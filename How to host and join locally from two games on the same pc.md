# Why do that ?
The reason is quite simple, to test the multiplayer functionality of your mod.

## How ?
I will assume you have the steam version of the game.  

-First start by going to the game files, the root folder. And found `ProjectZomboid64.bat` and `ProjectZomboid64.json`  

-Copy and paste then 2 time, rename then as you want. Like `noSteam Host` and `noSteam Client`  

-Go in the both .bat and change `-Dzomboid.steam=1` to `-Dzomboid.steam=0`. If you want a debug version, add `-debug` at the end of the line with `-Dzomboid.steam=`

-Go in the both .json and change `-Dzomboid.steam=1` to `-Dzomboid.steam=0`  

-Now start the both game by running the .bat  

-In one game, click on Host  

-Change the options of your server to add you mod and other, you don't have steam workshop anymore  

-Start the server  

-Join the local server from the other game with the IP `127.0.0.1` or `localhost`  

-To pass in admin use the commande `/setaccesslevel username admin`
