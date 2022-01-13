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

# Consumables
|Parameter Name	|Effect / Description	|Example|
|:--|---|:--|
|IsCookable|	Whether the item can be cooked.|	Boolean (false or true)|
|MinutesToCook|	How many in-game minutes the item must be in an oven for it to cook.|	50 (pot of soup)|
|MinutesToBurn|	Length of time the item must be in an oven for it to be burnt. Usually double the value of 'MinutesToCook'.|	150 (steak)|
|HungerChange|	Value applied to player's current hunger points. Positive increases hunger.	-20 (crisps)|
|DaysFresh|	How many days it takes for a food item to begin rotting.|	2 (steak)|
|DaysTotallyRotten|	How many days it takes for a food item to become entirely rotten.|	7 (carrots)|
|DangerousUncooked|	Whether the food item will negatively affect the player in an uncooked state.|	Boolean (false or true)|
|RequireInHandOrInventory	|Requires a specified item to be inside the player's inventory before the item may be used.|	CanOpener (canned soup)|
|Alcoholic|	Whether the item effects the player in a similar way to Whiskey Bottle.	|Boolean (false or true)|
|UseSelf	|Whether the item is consumed after use.	|Boolean (false or true)|

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
|MinimumSwingTime|	The time that takes between each swing.	|15 (baseball bat)|
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

# Clothing
|Parameter Name	|Effect / Description	|Example|
|:--|---|:--|
|Palettes|	Defines the clothing item's colors.	Trousers_Blue/Trousers_Brown/Trousers_Grey/Trousers_White (trousers)|
|PalettesStart|	Defines the clothing item's palette prefix.|	Shirt_ (sweater)|
|BodyLocation	|Where the clothing item is worn.	|Bottoms (trousers)|
|SpriteName|	Defines the sprite displayed on the player.|	Shoes1 (shoes)|

# Literature
|Parameter Name	|Effect / Description	|Example|
|:--|---|:--|
|StressChange	|Value applied to player's current stress points. Positive makes the player become more stressed.	|-10 (newspaper)|
|BoredomChange|	Value applied to player's current boredom points. Positive increases player's boredom.	|-50 (book)|
