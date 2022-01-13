# What a trait ? 
Traits are modifiers, positive and negative, available to the player. Some traits can be chosen during character creation (indicated by a points value) and others may be given with their choice of occupation, also known as hobbies. Multiple presets can be made to save a combination of a profession and multiple other traits which makes it useful for players that want to quickly jump right into the apocalypse.

## Create the trait
To start, you have to create a function in a new .lua file in `media\lua\client` which will be triggered when the game starts.  
Add these lines of code to the file:
```lua
local function initMyTraits()

end

Events.OnGameBoot.Add(initMyTraits);
```

Now all that is needed to create the traits will be in the initMyTraits function.  

To add a trait:  
```lua
local MyTrait = 
TraitFactory.addTrait("MyTrait",                          -- Incode name to refere that trait
                      getText("UI_trait_MyTrait"),        -- Trait name in game
                      -8,                                 -- Cost of the trait, can be positive or negative
                      getText("UI_trait_MyTraitdesc"),    -- Description of the trait
                      false,                              -- No idea
                      false)                              -- I guess it's if the trait is related to a profession
 ```
 
## Main usable functions
| Description  | Function |
| ------------- | ------------- |
| Add 4 level in the first aids skill  | `MyTrait:addXPBoost(Perks.Doctor, 4)`  |
| Add a recipe | `MyTrait:getFreeRecipes():add("Make Small Metal Sheet")` |
| Prevent having two trait at the same time | `TraitFactory.setMutualExclusive("MyTrait", "MyTrait2");` |
| Check if player have a trait | `player:HasTrait("MyTrait")` |
| Add a trait to a player | `player:getTraits():add("MyTrait")` |
| Remove a trait to a player | `player:getTraits():remove("MyTrait")` |

## Exemple of my mod
```lua
local function initTOCTraits()
    local amp1 = TraitFactory.addTrait("amputee1", getText("UI_trait_Amputee1"), -8, getText("UI_trait_Amputee1desc"), false, false);
    amp1:addXPBoost(Perks.LeftHand, 4)
    local amp2 = TraitFactory.addTrait("amputee2", getText("UI_trait_Amputee2"), -10, getText("UI_trait_Amputee2desc"), false, false);
    amp2:addXPBoost(Perks.LeftHand, 4)
    local amp3 = TraitFactory.addTrait("amputee3", getText("UI_trait_Amputee3"), -20, getText("UI_trait_Amputee3desc"), false, false);
    amp3:addXPBoost(Perks.LeftHand, 4)
    TraitFactory.addTrait("Insensitive", getText("UI_trait_Insensitive"), 6, getText("UI_trait_Insensitivedesc"), false, false);
    TraitFactory.setMutualExclusive("amputee1", "amputee2");
    TraitFactory.setMutualExclusive("amputee1", "amputee3");
    TraitFactory.setMutualExclusive("amputee2", "amputee3");
end

Events.OnGameBoot.Add(initTOCTraits);
```
