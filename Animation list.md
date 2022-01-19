# setActionAnim
This is a non-exhaustive list of animation names to use with this function `self:setActionAnim(Name)` in a timed action.[See this link](https://github.com/MrBounty/PZ-Mod---Doc/blob/main/How%20to%20make%20a%20custom%20timed%20actions.md)  
Line with a * have options below, don't forget to check it !  

## Equip:
```
- "WearClothing" *
- "DetachItem"
- "UnequipItem"
- "AttachItem"
```

## Craft:
```
- "Craft"
- "Build"
- "RemoveCurtain"
- "RemoveBarricade"
- "RipSheets"
- "BlowTorch"
- "SawLog"
- "Forage"
- CharacterActionAnims.Paint
- CharacterActionAnims.Craft
- CharacterActionAnims.Disassemble
- CharacterActionAnims.Build
- CharacterActionAnims.BuildLow
- CharacterActionAnims.Destroy
```

## Vehicle:
```
- "refuelgascan"
- "VehicleTrailer"
- "VehicleWorkOnTire"
- "VehicleWorkOnMid"
- "ExamineVehicle"
- "TakeGasFromVehicle"
- "VehicleWash"
- "refuelgascan"
```

## Grass, bush, tree & dig:
```
- "Rake"
- "RemoveGrass"
- "RemoveBush"
- "RemoveBushKnife"
- "RemoveBushLongBlade"
- "RemoveBushAxe"
- CharacterActionAnims.Chop_tree
- CharacterActionAnims.Dig
- CharacterActionAnims.DigShovel
- CharacterActionAnims.DigHoe
- CharacterActionAnims.DigPickAxe
- CharacterActionAnims.DigTrowel
```

## Eat & drink:
```
- CharacterActionAnims.Drink *
- CharacterActionAnims.Eat *
```

## Weapon:
```
- CharacterActionAnims.Reload
- CharacterActionAnims.InsertBullets
- CharacterActionAnims.RemoveBullets
```

## Medical:
```
- "MedicalCheck"
- CharacterActionAnims.Bandage
```

## Other:
```
- "Loot"
- "Forage"
- "fill_container_tap"
- "drink_tap"
- "WashFace"
- "Pour"
- CharacterActionAnims.Pour
- CharacterActionAnims.Read
- CharacterActionAnims.TakePills
- CharacterActionAnims.Shave
```

# setAnimVariable
This is a non-exhaustive list of animation names to use with this function `self:setAnimVariable(arg1, arg2)` in a timed action. 
To an example of using spoon and fork, check `ProjectZomboid\media\lua\client\TimedActions\ISEatFoodAction.lua`, line 40.  
[See this link](https://github.com/MrBounty/PZ-Mod---Doc/blob/main/How%20to%20make%20a%20custom%20timed%20actions.md)  

## Cloth:  
| arg1 | arg2 |
| ---- | ---- |
| "WearClothingLocation" | "Waist" |
| "WearClothingLocation" | "Legs" |
| "WearClothingLocation" | "Face" |
| "WearClothingLocation" | "Jacket" |
| "WearClothingLocation" | "Feet" |
| "WearClothingLocation" | "Pullover" |

## Food: 
| arg1 | arg2 |
| ---- | ---- |
| "FoodType" | item:getEatType() |
| "FoodType" | "Kettle" |
| "FoodType" | "bottle" |
| "FoodType" | "2handbowl" |
| "FoodType" | "drink" |
| "FoodType" | "plate" |
| "FoodType" | "can" |
| "FoodType" | "2hand" |

## Bandage:  
| arg1 | arg2 |
| ---- | ---- |
| "BandageType" | "Head" |
| "BandageType" | "LowerBody" |
| "BandageType" | "UpperBody" |
| "BandageType" | "LeftArm" |
| "BandageType" | "RightArm" |
| "BandageType" | "LeftLeg" |
| "BandageType" | "RightLeg" |

## Weapon:  
| arg1 | arg2 |
| ---- | ---- |
| "WeaponReloadType" | gun:getWeaponReloadType() |
| "isLoading" | true |
| "isUnloading" | true |
| "isRacking" | true |
| "RackAiming" | character:isAiming() |

## Other:  
| arg1 | arg2 |
| ---- | ---- |
| "LootPosition" | "Low" |
| "LootPosition" | "" |
| "ReadType" | "newspaper" |
| "ReadType" | "book" |
| "RemoveBarricade" | "CrowbarHigh" |
| "RemoveBarricade" | "CrowbarMid" |

# Example
- In `ProjectZomboid\media\lua\client\TimedActions\ISEjectMagazine.lua`:
```
self:setAnimVariable("WeaponReloadType", self.gun:getWeaponReloadType())
self:setAnimVariable("isUnloading", true)
```
[TODO] Add examples.
