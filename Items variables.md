# Group of variables used during object creation

## General
|Parameter Name	|Effect / Description	|Example|
|:--|---|:--|
|Type	|Item-type, describes how the item behaves. Includes 'Food', 'Weapon', 'Drainable', 'Literature', 'Clothing' and 'Normal'.|	Food (steak)|
|Display Name|	The item's name as it appears displayed to the player.	|Axe (axe)|
|Icon	|The item's icon as it appears displayed to the player. This parameter looks inside "media/texturepacks/ui.txt" and will call any sprite with the prefix "Item_".|	Molotov (molotov cocktail)|
|Weight|	Item's weight, used for encumbrance.|	0.1 (painkillers)|
|OtherHandRequire	|Requires a specified item to be held by the player in their second quick-slot before the item may be used.|	Lighter (molotov cocktail)|
|CanBarricade|	Whether the item may be used like the hammer to barricade doors and windows.|	Boolean (false or true)|
|Count	|The number of items which may ever be used in the game world.|	8 (Ripped Sheets)|
|UseWhileEquipped|	Whether the item is used over time while it is equipped.	|Boolean (false or true)|
|UseDelta|	Numerical value associated with how quickly the item drains.|	0.0009 (torch)|
|ReplaceOnUse|	Name of the item which replaces the current item after use.	|Pot (pot of soup)|
|CanStoreWater| If the item can store water.| TRUE (Saucepan)|
|Medical| If it's use for medical thing| TRUE (Needle)|
|SurvivalGear| Need more research|TRUE (Needle)|
|CanBandage|Can be use as bandage.| TRUE (RippedSheets)|

# Weapons
|Parameter Name	|Effect / Description	|Example|
|:--|---|:--|
|MinAngle	|The angle that the weapon attacks, a value aprox. to 1 is going to need more accuracy with mouse than one nearer to -1.	|0.88 (shotgun)|
|MinDamage	|Minimum damage the weapon will inflict.|	0.7 (baseball bat)|
|MaxDamage|	Maximum damage the weapon may ever inflict.	|1.0 (baseball bat)|
|MaxRange|	Maximum range the weapon is effective.	|1.5 (spiked baseball bat)|
|MaxHitCount|	Maximum amount of enemies the weapon will hit at one time.|	1 (hammer)|
|PhysicsObject|	Physics object used as a projectile.|	MolotovCocktail (molotov cocktail)|
|SwingAnim|	Name of animation which is ran when the weapon is fired/swung.	|Bat (baseball bat)|
|WeaponSprite|	Name of sprite, the image used to display the weapon.	|axe (axe)|
|DoorDamage	|Damage inflicted by the item on doors.|	10 (spiked baseball bat)|
|TreeDamage| Damage inflicted by the item on tree. | 0 ( SpearMachete)|
|MinimumSwingTime|	The time that takes between each swing.	|15 (baseball bat)|
|TwoHandWeapon| If you need to use it with two hand| TRUE (SpearMachete)|
|KnockdownMod||0 (SpearHuntingKnife)|
|SwingAmountBeforeImpact|	Requires more research.	|0.2 (spiked baseball bat)|
|PushBackMod|	Distance that enemies are pushed back.	|4.5 (wood planks)|
|KnockBackOnNoDeath|	Whether enemies are pushed back if they are not killed.	|Boolean (false or true)|
|SplatNumber|	Blood effects used when an enemy is injured by the weapon.	|5 (shotgun)|
|SplatBloodOnNoDeath|	Whether an enemy injured by the weapon will bleed if they are not killed	|Boolean (false or true)|
|ImpactSound|	Name of sound used on impact.	|splat1 (axe)|
|SwingSound|	Name of sound used when firing/swinging weapon.	|shotgun (shotgun)|
|SoundVolume|	Defines the volume of a chosen sound.|	40 (shotgun)|
|SoundRadius|	Radius in which the sound may be heard in the game world from it's point of origin.|	50 (shotgun)|
|ToHitModifier|	Requires more research.|	1.5 (shotgun)|
|NPCSoundBoost|	Amount that a sound is boosted when the weapon is fired by an NPC (Not player).|	1.5 (shotgun)|
|RangeFalloff|	Requires more research.	|Boolean (false or true)|
|UseEndurance|	Whether the weapon causes exhaustion.|	Boolean (false or true)|
|ShareDamage|	Requires more research.	|Boolean (false or true)|
|AmmoType	|Item required to fire the weapon.	|ShotgunShells (shotgun)|
|DamageCategory| | Slash (SpearMachete)|
|DamageMakeHole| If attack damage clothes | TRUE (SpearMachete)|
|RunAnim| Animation when running with the weapon in hand | Run_Weapon2 (SpearMachete)|
|IdleAnim| Animation when doing nothing with the weapon in hand | Idle_Weapon2 (SpearMachete)|
|DamageCategory|Category of attack | Slash (SpearMachete)|
|CriticalChance| Chance item to do a critical attack| 30 (SpearMachete)|
|CritDmgMultiplier| Damage multiplier of critical attack| 10 (SpearMachete)|
|BaseSpeed|Attack speed. |0.9 (SpearMachete)|
|WeaponLength |Need more research.|0.2 (DumbBell)|
|attachmenttype|Need more research. |Shovel (SpearMachete), Rifle (AssaultRifle2)|
|ProjectileCount|Need more research|1 (AssaltRifle2)|
|ConditionLowerChanceOneIn|Need more research.| 60 (AssaultRifle2)|
|ConditionMax	|Need more research. | 10 (AssaltRifle2)|
|IsAimedFirearm	|For gun, need more research.|TRUE (AssaultRifle2)|
|AimingPerkCritModifier	|For gun, need more research.|0 (AssaultRifle2)|
|HitChance	|For gun, chance to hit.|50 (AssaultRifle2)|
|AimingPerkMinAngleModifier	|For gun, need more research.|0.01 (AssaultRifle2)|
|AimingPerkHitChanceModifier	|For gun, need more research.|5 (AssaultRifle2)|
|AimingPerkRangeModifier 	|For gun, need more research.|3 (AssaultRifle2)|
|RecoilDelay	|Delay between attack, for gun.|0 (AssaultRifle2)|
|ReloadTime 	|Delay to reload, for gun.|25 (AssaultRifle2)|
|AimingTime 	|Delay to aim, for gun.|25 (AssaultRifle2)|
|MaxAmmo  |For gun, need more research.|20 (AssaultRifle2)|
|AmmoBox  |For gun, need more research.|308Box (AssaultRifle2)|
|FireMode |For gun, need more research.|Single (AssaultRifle2)|
|WeaponReloadType  |For gun, need more research.|boltaction (AssaultRifle2)|

# Clothing
|Parameter Name	|Effect / Description	|Example|
|:--|---|:--|
|Palettes|	Defines the clothing item's colors.	Trousers_Blue/Trousers_Brown/Trousers_Grey/Trousers_White (trousers)|
|PalettesStart|	Defines the clothing item's palette prefix.|	Shirt_ (sweater)|
|BodyLocation	|Where the clothing item is worn.	|Bottoms (trousers)|
|SpriteName|	Defines the sprite displayed on the player.|	Shoes1 (shoes)|
|Wet|Cloth can be wet|TRUE (DishClothWet)|
|WetCooldown| Time to dry.|8000 (DishClothWet)|
|ItemWhenDry| Replace the item when dry.|Base.DishCloth (DishClothWet)|

# Literature
|Parameter Name	|Effect / Description	|Example|
|:--|---|:--|
|StressChange	|Value applied to player's current stress points. Positive makes the player become more stressed.	|-10 (newspaper)|
|BoredomChange|	Value applied to player's current boredom points. Positive increases player's boredom.	|-50 (book)|
|UnhappyChange|	Value applied to player's current unhappy points. Positive increases it.	|-20 (ComicBook)|
|TeachedRecipes| Teach a recipe when read| Make Fishing Rod;Fix Fishing Rod (FishingMag1)|
|NumberOfPages | The time it take to read the book.| 220 (BookTrapping1)|
|SkillTrained | The skill that train that book.| Trapping (BookTrapping1)|
|LvlSkillTrained | The first level train by the book.| 1 (BookTrapping1)|
|NumLevelsTrained | Number of level that train that book.| 2 (BookTrapping1)|
|CanBeWrite | If the book can be write in | true (Notebook|
|PageToWrite| Number of page available to write| 10 (Notebook)|

# Food
|Parameter Name	|Effect / Description	|Example|
|:--|---|:--|
|StressChange	|Value applied to player's current stress points. Positive makes the player become more stressed.	|-10 (newspaper)|
|BoredomChange|Value applied to player's current boredom points. Positive increases player's boredom.	|-50 (book)|
|UnhappyChange|Value applied to player's current unhappy points. Positive increases it.	|-20 (ComicBook)|
|HungerChange	|Value applied to player's current hunger points. Positive makes the player become more hungry.| -30 (DogFoodOpen)|
|ThirstChange	|Value applied to player's current thirst points.| -20 (Wine)|
|FatigueChange|Value applied to player's current fatigue points.| 0 (ColdCuppa)|
|DaysFresh	|Number of day before rotten.	|5 (DogfoodOpen)|
|DaysTotallyRotten	|Need infos.	|7 (DogfoodOpen)|
|Carbohydrates	|Nutritional value.	|77.56 (DogfoodOpen)|
|Proteins 	|Nutritional value.	|16.04 (DogfoodOpen)|
|Lipids 	|Nutritional value.	|12.58 (DogfoodOpen)|
|Calories 	|Nutritional value.	|498 (DogfoodOpen)|
|Packaged 	|If you can read the nutritional value on the box.	|TRUE (DogfoodOpen)|
|ReplaceOnUse 	|Item to remplace with after use it.	|TinCanEmpty (DogfoodOpen)|
|EatType	|Type of food.	|can (DogfoodOpen)|
|FoodType| The type of food.| Vegetables (TofyFried) Meat (CannedCornedBeefOpen)|
|CannedFood| If it's a canned food| TRUE (DogFood)|
|EvolvedRecipe| Recipe you can use with.| Stew:15;Stir fry Griddle Pan:15;Stir fry:15;Sandwich:10 (CannedCornedBeefOpen)|
|DangerousUncooked| If the fodd can make you sick if uncook| TRUE (DeadRat)|
|IsCookable| If you can cook the food| TRUE (DeadRat)|
|ReplaceOnCooked|Replace the item when cook.| Base.EggPoached (EggBoiled)|
|MinutesToCook| Number of minute to cook the food| 6 (DeadRat)|
|MinutesToBurn| Number of minute before burning the food| 60 (DeadRat)|
|BadInMicrowave| Need an oven to cook it | true (Steak)|
|FishingLure| If you can use it to fish| true (BaitFish)|
|GoodHot| If better hot, need more research| true (Steak)|
|BadCold| If bad cold, need more research| true (Steak)|
|RemoveUnhappinessWhenCooked| Need more research| true (BaitFish)|
|CantBeFrozen| The food can't be frozen| TRUE (Wine)
|Alcoholic| If it make you drunk| TRUE (Wine)|
|CustomContextMenu| Add a context menu option for use the item| Drink (Wine)|
|CustomEatSound|Sound to play when eat the item.| DrinkingFromBottleGlass (Wine)|
|Poison|If it can kill you.| true (Bleach)|
|PoisonDetectionLevel|Need more research.| 7 (Bleach)|
|PoisonPower |Power of the poison (100 kill you)| 120 (Bleach)|
|UseForPoison |Need more research.| true (Bleach)|
|Spice| If it's a spice.| true (SugarBrown)|
|CantEat| Can't be eat (for intermediate recipe)|TRUE (BakingTray_Muffin)|
|UseSelf	|Whether the item is consumed after use.	|Boolean (false or true)|
|RequireInHandOrInventory	|Requires a specified item to be inside the player's inventory before the item may be used.|	CanOpener (canned soup)|
