I will give you two ways to store data.  

### Json
The first is with the Json.lua. [File](https://discord.com/channels/136501320340209664/232196827577974784/940523841027964948)  
Like that:
```lua
local Json = require("Json");

local theTable = {};

local function Save()
    local fileWriterObj = getFileWriter("file_theTable.json", true, false);
    local json = Json.Encode(theTable);
    fileWriterObj:write(json);
    fileWriterObj:close();
end

local function Load()
    local fileReaderObj = getFileReader("file_theTable.json", true);
    local json = "";
    local line = fileReaderObj:readLine();
    while line ~= nil do
        json = json .. line;
        line = fileReaderObj:readLine()
    end
    fileReaderObj:close();

    if json and json ~= "" then
        theTable = Json.Decode(json);
    end
end
```

### Custom
Otherwise I made a small function to save a table with a .txt number, boolean and text:  
```lua
-- name is a path with the name of the file and the extension. Like that: name = "MyFile.txt"
-- File in C:\Users\User\Zomboid\Lua

local function encodeTable(t)
    local toReturn = "";
    for k, v in pairs(t) do
        toReturn = toReturn .. k .. "=" .. tostring(v) .. ",\n";
    end
    return toReturn
end

local function decodeTable(txt)
    local toReturn = {}
    for k, v in string.gmatch(txt, "(%w+)=(%d+)") do -- If number
        toReturn[k] = tonumber(v);
    end
    for k, v in string.gmatch(txt, "(%w+)=(%d+.%d+)") do -- If decimal number
        toReturn[k] = tonumber(v);
    end
    for k, v in string.gmatch(txt, "(%w+)=([%a%s]+)") do -- If string
        if v == "true" then toReturn[k] = true -- If string is a boolean
        elseif v == "false" then toReturn[k] = false -- If string is a boolean
        else toReturn[k] = v;
        end
    end
    return toReturn
end

function SaveFile(t, name)
    local fileWriterObj = getFileWriter(name, true, false);
    local text = encodeLayout(t);
    fileWriterObj:write(text);
    fileWriterObj:close();
end

function LoadFile(name)
    local fileReaderObj = getFileReader(name, true);
    local text = "";
    local line = fileReaderObj:readLine();
    while line ~= nil do
        text = text .. line;
        line = fileReaderObj:readLine()
    end
    fileReaderObj:close();

    if text and text ~= "" then
        return decodeTable(text);
    end
end
```
