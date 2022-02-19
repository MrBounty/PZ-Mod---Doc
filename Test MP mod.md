## Local
This is the method that uses the host button from the main menu. It's like a server but without the console server. I recommend using the other method with the dedicated server to have it because server-side errors are displayed in it and it facilitates/accelerates disconnection/reconnection.  
I will assume you have the steam version of the game.  

-First start by going to the game files, the root folder. And found `ProjectZomboid64.bat` and `ProjectZomboid64.json`  

-Copy and paste then 2 time, rename then as you want. Like `noSteam Host` and `noSteam Client`  

-Go in the both .bat and change `-Dzomboid.steam=1` to `-Dzomboid.steam=0`. If you want a debug version, add `-debug` at the end of the line with `-Dzomboid.steam=`

-Go in the both .json and change `-Dzomboid.steam=1` to `-Dzomboid.steam=0`  

-Now start the both game by running the .bat  

-In one game, click on Host  

-Change the options of your server to add you mod and other, you don't have steam workshop anymore so you need to put your mod in `C:\Users\User\Zomboid\mods`  

-Start the server  

-Join the local server from the other game with the IP `127.0.0.1` or `localhost`  

-To pass in admin use the commande `/setaccesslevel username admin`

## Server
You can also do it using a nosteam dedicated server. Follow [this guide](https://pzwiki.net/wiki/Dedicated_Server) to make a server.  
After the server is launched, you can connect the same way, using `localhost` and two nosteam game.  
You can add you username as admin from the server console.
