## Find player when right click
```lua
local clickedPlayer
for i, v in ipairs(worldObjects) do
  local movingObjects = v:getSquare():getMovingObjects()
  for i = 0, movingObjects:size() - 1 do
    local o = movingObjects:get(i)
    if instanceof(o, "IsoPlayer") then
      clickedPlayer = o
      break
    end
  end
end
```
