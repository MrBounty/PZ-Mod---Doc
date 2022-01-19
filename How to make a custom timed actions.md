# What a timed actions ?
It is an action which will take time in the game. Almost all of the actions the player does is derived from timedActions.

The source code for the timedAction is here: `media\lua\shared\TimedActions\ISBaseTimedAction.lua`  
All the others are here: `media\lua\client\TimedActions`  
After reading this, I recommend look at a timedActions that looks like what you want to do and learn from it.

## Call a timedAction
To call a timedAction in your code: `ISTimedActionQueue.add(MyTimedAction:new(player))`  
Also work with vanilla timedAction like `ISTimedActionQueue.add(ISAddFuel:new(character, generator, petrolCan, time))`  


## Make a custom timedAction
Make a file `MyTimedAction.lua` in `media\lua\client\TimedActions`.  
This is the most basic example of how to do a timed action:
```lua
require "TimedActions/ISBaseTimedAction"

MyTimedAction = ISBaseTimedAction:derive("MyTimedAction");

function MyTimedAction:isValid() -- Check if the action can be done
    return true;
end

function MyTimedAction:update() -- Trigger every game update when the action is perform
    print("Action is update");
end

function TOC_CutArm:waitToStart() -- Wait until return false
    return false;
end

function MyTimedAction:start() -- Trigger when the action start
    print("Action start");
end

function MyTimedAction:stop() -- Trigger if the action is cancel
    print("Action stop");
    ISBaseTimedAction.stop(self);
end

function MyTimedAction:perform() -- Trigger when the action is complete
    print("Action perform");
    ISBaseTimedAction.perform(self);
end

function MyTimedAction:new(character) -- What to call in you code
    local o = {};
    setmetatable(o, self);
    self.__index = self;
    o.character = character;
    o.maxTime = 30; -- Time take by the action
    if o.character:isTimedActionInstant() then o.maxTime = 1; end
    return o;
end
```


## Exemples of functions to call

### MyTimedAction:new()
| Description  | Functions |
| ------------- | ------------- |
| Prevents doing the action while running  | `o.stopOnWalk = true` |
| Prevents doing the action while walking  | `o.stopOnRun = true`  |
| Ignore added time if hand is injured | `o.ignoreHandsWounds = false` |
| Force progress bar | `o.forceProgressBar = true` |
| Disable hotbar:update() | `o.fromHotbar = true` |


### MyTimedAction:start()
| Description  | Functions |
| ------------- | ------------- |
| Add an animation  | `self:setActionAnim("MedicalCheck")` |
| Add a cloth animation [see](https://github.com/MrBounty/PZ-Mod---Doc/blob/main/Animation%20list.md)  | `self:setActionAnim("WearClothing"); self:setAnimVariable("WearClothingLocation", "Jacket")`  |
| Play a sound | `self.character:getEmitter():playSound("My_sound")` |
| Make a character face something | `self.character:faceThisObject(self.generator)` |
| Trigger event | `self.character:reportEvent("EventLootItem")` |
| Force complete | `self:forceComplete()` |


### MyTimedAction:perform()
| Description  | Functions |
| ------------- | ------------- |
| Add item to inventory | `self.character:getInventory():addItem("Base.YourItem")` |
| Remove item from inventory | `self.surgeon:getInventory():Remove(self.item)` |
| Trigger event | `self.character:reportEvent("EventLootItem")` |


### MyTimedAction:update()
| Description  | Functions |
| ------------- | ------------- |
| Make a character face something | `self.character:faceThisObject(self.generator)` |


### MyTimedAction:isValid()
| Description  | Functions |
| ------------- | ------------- |
| Check if an item is on inventory | `return self.surgeon:getInventory():FindAndReturn('Pills')` |


### MyTimedAction:waitToStart()
| Description  | Functions |
| ------------- | ------------- |
| Wait until character face something | `self.character:faceThisObject(self.generator); return self.character:shouldBeTurning()` |
