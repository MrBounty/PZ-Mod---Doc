# Intro
This is how I manage data transfer for the multiplayer functionality of my mod The Only Cure.  It's not necessarily the best way, but it works well.

 I'm going to show you two things:
 - From client, send a command to a player
 - From client, request data from another client

# Understand commands
The two main functions are:
 - `sendClientCommand(module, command, arg)` To send a command from client to the server
 - `sendServerCommand(player, module, command, arg)` To send a command from the server to players. Note: if player is empty, send to all player.

`module` is a string which is used to categorize commands. I recommend using the same everywhere for your mod, using your mod ID is a good idea. I use "TOC" for my mod.  
`command` is a string too. This is what will allow you to choose what to run.  
`arg` is what you want to send. Usually a table with all the informations to send. All objects are not available, like player or square. Use only strings, ints or floats. So if you want to send a square for exemple, you need to send the position and then use it to get the square.

# Make and init files
First you need to make one file in `media/lua/client`
```lua
local Commands = {}
local moduleName = "myModule"

-- Event
local onServerCommand = function(module, command, args)
    if module == moduleName and Commands[command] then
        args = args or {}
        Commands[command](args)
    end
end

Events.OnServerCommand.Add(onServerCommand)
```

Then one file in `media/lua/server`
```lua
---Server side
local Commands = {}
local moduleName = "myModule"

Commands["SendServer"] = function(player, arg)
    local otherPlayer = getPlayerByOnlineID(arg["To"])
    sendServerCommand(otherPlayer, "TOC", arg["command"], arg)
end

local onClientCommand = function(module, command, player, args)
    if module == 'TOC' and Commands[command] then
        args = args or {}
        Commands[command](_, args)
    end
end
Events.OnClientCommand.Add(onClientCommand)
```

# From client, send a command to a player
Ok so first you make a function to call to send the data. For that, add this function in the client file.
```lua
function SendMyFunction(player, arg1, arg2, arg3)
    local arg = {};
    arg["From"] = getPlayer():getOnlineID();
    arg["To"] = player:getOnlineID();
    arg["command"] = "myFunction";
    arg["toSend"] = {arg1, arg2, arg3};
    sendClientCommand(moduleName, "SendServer", arg);
end
```

Then add that, it's what is call to the receiver.
```lua
Commands["myFunction"] = function(arg)
    local arg = arg["toSend"];
    -- Code here
end
```

And use it like that:  
```lua
SendMyFunction(playerObj, "arg1", 100, {"arg2", 3, 88})
```

Note: You can use this as an example for send to server.

# From client, request data from another client
It's the same as above but twice.
Add this to the client file:
```lua
function AskMyFunction(player, arg1)
    local arg = {};
    arg["From"] = getPlayer():getOnlineID();
    arg["To"] = player:getOnlineID();
    arg["command"] = "askMyFunction";
    arg["toSend"] = arg1;
    sendClientCommand(moduleName, "SendServer", arg);
end

Commands["askMyFunction"] = function(arg)
    local arg1 = arg["toSend"];
    
    arg["To"] = arg["From"];
    arg["From"] = getPlayer():getOnlineID();
    arg["command"] = "responseMyFunction";
    arg["toSend"] = {arg1, arg2, arg3};
    sendClientCommand(moduleName, "SendServer", arg);
end

Commands["responseMyFunction"] = function(arg)
    local response = arg["toSend"]
    -- Code here
end
```
