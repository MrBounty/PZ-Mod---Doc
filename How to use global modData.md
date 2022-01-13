# Global ModData

## What is it ?
Registers moddata tables with a given String key.
When Global Moddata is initialised during world loading it triggers the event "OnInitGlobalModData" with parameter: boolean isNewGame.

## Functions
| Return | Function | Description |
| :---      | :---                                      | :---          |
| LuaTable  | `ModData.create(String key)`              | Creates and returns the table with given key, returns null if the table<br> already exists. |
| String    | `ModData.create()`                        | Creates a table with a random UUID key, note: returns the string key. |
| LuaTable  | `ModData.getOrCreate(String key)`         | Gets or creates the table with given key. |
| LuaTable  | `ModData.get(String key)`                 | Returns the table with given key or null. |
| boolean   | `ModData.exists(String key)`              | Return true if table with given key exists. |
| LuaTable  | `ModData.remove(String key)`              | Removes the table with given key if exists and returns it or null. |
| void      | `ModData.add(String key, LuaTable table)` | Store the table with given key (overrides any existing table). |
| ArrayList | `getTableNames()`                         | Returns a list of all registered tables. |

## Networking
Global ModData is not synced between server and client as depending on what the moddata is being used for this may not be required or even unwanted.
Syncing of data where needed is up to coder/author. There are however two methods for networking:

| Return | Function | Description |
| :---  | :---------------------------------------- | :---          |
| void  | `ModData.transmit(String key)`            | This will attempt to transmit the table with given key, when called on server this is <br>send to all clients, when called on client send to server. |
| void  | `ModData.request(String key)`             | Client only, this sends a request to server to send back the table with given key to <br>this client. |


When the server or the client receives a moddata packet it is not automatically added to the local register.
Instead the packet is read and the event `OnReceiveGlobalModData` is triggered, the String key and LuaTable table are passed as arguments.
NOTE: the table argument can be 'false' when moddata packet replied to a ModData.request.
The coder/author can then decide to parse, register or keep it as temporary lua table only etc.

Link: https://theindiestone.com/forums/index.php?/topic/38241-iwbums-4151-released/
