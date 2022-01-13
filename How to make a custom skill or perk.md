# What a skill/perk ?
Skill and perk are the same thing.  
Skills are abilities a character has learned, with their proficiency at that skill quantified by its skill level. The skill level can be increased by gaining a sufficient amount of experience points (XP).

Skills are grouped into categories. There are currently five main skill categories: agility, combat, crafting, firearm, and survivalist. Each of these contains multiple skills. There is also a passive category, containing the fitness and strength skills.


## Create and init the file
The first thing to do is to create an `perks.txt` file in `\media`  
Then start by writing: `VERSION = 1,`  


## Add a custom categories
To add a category, you must then enter this code:
```
perk MyPerkCat
{
	parent = None,
	translation = MyPerkCatName,
	passive = false,
	xp1 = 0,
	xp2 = 0,
	xp3 = 0,
	xp4 = 0,
	xp5 = 0,
	xp6 = 0,
	xp7 = 0,
	xp8 = 0,
	xp9 = 0,
	xp10 = 0,
}
```
The name of the category goes in `media\lua\shared\translate\EN\IG_UI_EN.txt`  
Like that: `IGUI_perks_MyPerkCatName = "This is the name of my perk cat",`


## Add a custom skill
It's very similar to above:
```
perk MyPerk
{
	parent = MyPerkCat,
	name = MyPerk,
	translation = MyPerkName,
	passive = false,
	xp1 = 50,
	xp2 = 100,
	xp3 = 200,
	xp4 = 500,
	xp5 = 1000,
	xp6 = 2500,
	xp7 = 4000,
	xp8 = 5000,
	xp9 = 7000,
	xp10 = 9000,
}
```  
Parent is the category. Here we use a custom category but an already existing category like crafting can be use


## Add xp to the skill
In your lua code, just use that: `player:getXp():AddXP(Perks.Doctor, 4)`  
Or for the custom perk: `player:getXp():AddXP(Perks.MyPerk, 4)`  
The second argument is the value of xp added. 1 add 0.25xp, so here 4 add a point of xp


## Get xp and level of perk
Get the level of a perk: `player:getPerkLevel(Perks.Doctor)`  
Get the xp of a perk: `player:getXp():getXP(Perks.Doctor)`

## Exemple of my mod
This is the files I am using for my mod "The only cure" as exemple.
The `perks.txt`:
```
VERSION = 1,

perk Protheses
{
	parent = None,
	translation = Protheses,
	passive = false,
	xp1 = 0,
	xp2 = 0,
	xp3 = 0,
	xp4 = 0,
	xp5 = 0,
	xp6 = 0,
	xp7 = 0,
	xp8 = 0,
	xp9 = 0,
	xp10 = 0,
}

perk LeftHand
{
	parent = Protheses,
	name = LeftHand,
	translation = LeftHand,
	passive = false,
	xp1 = 50,
	xp2 = 100,
	xp3 = 200,
	xp4 = 500,
	xp5 = 1000,
	xp6 = 2500,
	xp7 = 4000,
	xp8 = 5000,
	xp9 = 7000,
	xp10 = 9000,
}

perk RightHand
{
	parent = Protheses,
	name = RightHand,
	translation = RightHand,
	passive = false,
	xp1 = 50,
	xp2 = 100,
	xp3 = 200,
	xp4 = 500,
	xp5 = 1000,
	xp6 = 2500,
	xp7 = 4000,
	xp8 = 6000,
	xp9 = 7000,
	xp10 = 9000,
}
```
And the `IG_UI_EN.txt`:
```
IGUI_EN = {
    IGUI_perks_RightHand = "Right hand",
    IGUI_perks_LeftHand = "Left hand",
    IGUI_perks_Protheses = "Protheses skills",
}
```
