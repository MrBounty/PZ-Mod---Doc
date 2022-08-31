# What is an event ?
One of the fundamental points of modding project zomboid are the events.  
An event is called upon a particular action. It's used to call code when something happens.  

You can find all events here : [Link](https://pzwiki.net/wiki/Modding:Lua_Events)  
For every events there is a description of when the event is trigger and parameters.

All you have to do is put the code I show you here in a .lua file in `media/lua/client`.

# Examples
## [onKeyPressed](https://pzwiki.net/wiki/Modding:Lua_Events/OnKeyPressed)  
```lua
local function onKeyPressed(key)
	-- Your code here
end

Events.OnKeyPressed.Add(onKeyPressed)
```

The `onKeyPressed` function gonna be call every time a key is press.
`key` is the value of the key press.  
Find all value here [Link](https://theindiestone.com/forums/index.php?/topic/9799-key-code-reference/)

## [everyTenMinutes](https://pzwiki.net/wiki/Modding:Lua_Events/EveryTenMinutes)  
```lua
local function everyTenMinutes()
	-- Your code here
end

Events.EveryTenMinutes.Add(everyTenMinutes)
```

The `everyTenMinutes` function gonna be call every 10 in game minute.
There is no parameters with this event.

# Full example
This is a full example, the player gonna say "Hello world" when press the Q key.  
```lua
local function onKeyPressed(key)
    if key == 16 then
        getPlayer():Say("Hello world")
    end
end

Events.OnKeyPressed.Add(onKeyPressed)
```
