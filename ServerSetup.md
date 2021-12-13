# Setting up Files and Getting the server Running
I'm having you name files and folders certain things only so you can follow along easier, you can name them whatever you please just remember when editing Directory names to change them to what you make them.

## Steps
* Step 1: Open File Explorer -> Make a folder anywhere call it `DayZ_Server`.
* 
* Step 2: Open Arma2:OA directory -> Copy everything in there into `DayZ_Server`. 
* 
* Step 3: Open Arma2 Directory -> Copy `AddOns` folder only to `DayZ_Server`.
* 
* Step 4: Open File Explorer -> Make another folder not in the same Drive called `DayZ_Server_Config`.
* 
* Step 5: Open Epoch Server Files -> Move the `DZE_Server_Config` into the `DayZ_Server_Config` folder you made.
* 
* Step 6: Move all other Epoch Server Files into the `DayZ_Server` folder we made. `arma2oaserver.exe` should be in this folder. 
* Step 7: Open HeidiSQL -> Make a new Session, call it `DayZServer`. 
* Sign into the 'root' with the password you made on MySQL 5.7 -> right click on `DayZServer` at the top -> Create new -> database ->name it like `dayz_db` -> for Collation find the one called `utf8_general_ci` -> Create. 
* Now a database named `dayz_db` should have popped up inside the drop down next to like `mysql` and `information_schema`. Click on it -> Over on the right side toward the top you'll see a blue button that says Query, click it -> a new empty window popped up -> Open `DayZ_Server`  folder -> find `SQL` folder -> open it, now drag `epoch.sql` into that area where the Query opened. Next to the Query tab it will say 'Database:dayz_db', ABOVE that there is a blue Play button, click it after putting the 'epoch.sql' file into the Query.
* Now a dialog should have popped up saying `produced 1 warning`, ignore it.Now that next to where that Query tab was -> Click on that little gray window with the little green plus sign -> This opens a new Query tab -> Drop the 'add_recommended_mysql_events.sql' in that one and run it as well.Now a dialog should have popped up saying `produced 7 warnings`, ignore it. 
* Click on ‘dayz_db’ while in Heidi, click on the people icon, now under User Management click the green Add button, it will prompt you to make a new user I would name it something like “newServer” or whatever you want, make a good password, then toward the bottom of that same dialog it says “Allow access to”, click the green ‘Add object’ button, click on ‘dayz_db’, then when it goes into the list below, click on the checkbox next to it, do not click on checkbox next to ‘global privileges’ only the one next to ‘dayz_db’. 
* Now navigate to the `HiveExt.ini` located in your `DZE_Server_Config` folder, go down to line 36, change the `database = ` to `database = dayz_db` then below that change `Username` equal to `newServer`, then below that change the password to the password you set.

* Step 8: Open Visual Studio Code -> Navigate to the top left -> blocks icon called 'Extensions' -> type `SQF` -> Install `SQF Language` by Vladislav and `SQFLint` by Skace.
* Open File Explorer -> Open `DayZ_Server` -> Open `@DayZ_Epoch_Server` -> addons -> Right click on `dayz_server.pbo` -> PBO Manager -> `Extract to dayz_server\`. 
* Now go back to the main server folder -> MPMissions ->  right click on `DayZ_Epoch_11.Chernarus` -> PBO Manager -> `Pack into DayZ_Epoch_11.Chernarus.pbo`. 
* Now drag the `DayZ_Epoch_11.Chernarus` folder into VS Code on left side under `Workspace` -> Trust -> Add folder to workspace. 
* Go back to the `@DayZ_Epoch_Server` again -> addons -> drag the `dayz_server` folder into the work space as well -> Trust -> Add to workspace. 
* Now find the `DayZ_Server_Config` you made -> open it -> drag the `DZE_Server_Config` folder into the workspace as well. 
* Now at the top click File -> Save Workspace As -> Name it something like `DayZ Code` -> Save it to your desktop. Now click File again and click on Auto Save. You are now done setting up the text editor. (remember to drag the `folders` not the `.pbo` files into VS code)

* Step 9: In VS Code -> In the worksapce -> click on `DZE_Server_Config` -> Click the arrow to open it -> go to '11_chernarus.bat' -> change the Directories to yours. (ie: '`-config=C:\DZE_Server_Config\11_chernarus.cfg`' will change to '`-config=YourDrive\DayZ_Server_Config\DZE_Server_Config\11_chernarus.cfg`'). Now open the `11_chernarus.cfg` -> change 'hostname = ;' to whatever you want to name it, this will be what pops up on the server list, below that you can also have a server password.

* Step 10: Open -> `DZE_Server_Config` -> put the 'start.bat' inside.Change the directories in the `Start.bat` before you start it. 
* In VS Code -> Top left click 'Terminal' -> New Terminal -> a drop down menu will pop up -> click on `DZE_Server_Config` -> the new terminal window will have opened up at the bottom -> type `start start`. 
* Your server should start up. If you make changes in VS Code while the server is up, once you are ready to restart -> close the server -> then click on the Terminal window toward the bottom -> You should be able to just hit the Up arrow key or type 'start start' again.

**Debugging: If you have any problems with the server -> go to `DZE_Server_Config` -> `arma2oaserver.RPT` is where your logs and errors will be 90% of the time. If you have problems on the Client side -> Open File Explorer -> At the top in the address bar type `%appdata%` -> Go back one folder and click 'Local' -> Arma 2 OA -> 'ArmA2OA.RPT'.
If it has an error that  says `Include file z\addons\dayz_code\gui\description.hpp not found` -> go to the '11_chernarus.cfg' and change the name to something like `TEST` -> then go to '11_chernarus.bat' then check all your spelling and directory changes, this error is typically due to the server not actually being directed to the Mission folder, the other possible problem is that you do no have a '$PREFIX$' file in your '@DayZ_Epoch_Server\addons\dayz_server' folder. After putting ‘TEST’ in the name, restart the server and see if the server name changes, if not, go to ‘11_chernarus.cfg` and check the line that says `template = “DayZ_Epoch_11.Chernarus”;’ and make sure it is directed to the correct folder.**

## Done
Your server should run and not have any problems now, if it does not start please refer to **Debugging**, if you are ready we will move on to editing your server, click below to return to the ReadMe.

[Click Here to Continue](../main/README.md)
