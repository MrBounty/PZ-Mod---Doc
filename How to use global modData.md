# Global ModData

## What is it ?
Registers moddata tables with a given String key.
When Global Moddata is initialised during world loading it triggers the event "OnInitGlobalModData" with parameter: boolean isNewGame.

## Functions
```lua
LuaTable  ModData.create(String key)              --creates and returns the table with given key, returns null if the table already exists.
String    ModData.create()                        --creates a table with a random UUID key, note: returns the string key.
LuaTable  ModData.getOrCreate(String key)         --gets or creates the table with given key.
LuaTable  ModData.get(String key)                 --returns the table with given key or null.
boolean   ModData.exists(String key)              --return true if table with given key exists.
LuaTable  ModData.remove(String key)              --removes the table with given key if exists and returns it or null.
void      ModData.add(String key, LuaTable table) --store the table with given key (overrides any existing table).
ArrayList getTableNames()                         --returns a list of all registered tables.
```

## Networking
Global ModData is not synced between server and client as depending on what the moddata is being used for this may not be required or even unwanted.
Syncing of data where needed is up to coder/author. There are however two methods for networking:

`void ModData.transmit(String key)` - this will attempt to transmit the table with given key, when called on server this is send to all clients, when called on client send to server. (see note on receiving moddata below)

`void ModData.request(String key)` - client only, this sends a request to server to send back the table with given key to this client.

When the server or the client receives a moddata packet it is not automatically added to the local register.
Instead the packet is read and the event `OnReceiveGlobalModData` is triggered, the String key and LuaTable table are passed as arguments.
NOTE: the table argument can be 'false' when moddata packet replied to a ModData.request.
The coder/author can then decide to parse, register or keep it as temporary lua table only etc.

Link: https://theindiestone.com/forums/index.php?/topic/38241-iwbums-4151-released/
