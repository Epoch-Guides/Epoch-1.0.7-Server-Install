# Setting up Files, Database, and Getting the Server Running
The Folder Structure we demonstrate here is made so that you can follow along easier, and also obtain a better understanding of terminology. There is no single absolute way to set up your folders, so if you do it differently to the below, just make sure you change any file or path references where required :monocle_face:  

**NOTE: For the sake of this guide, we will be setting up a Chernarus Server**
## Server Folders
1. Open File Explorer and Navigate to a Memorable Directory. We will be using the Root Directory of the C Drive - `C:\`
2. Create a Folder called `Epoch Server`. All Files relevant to the Server will be contained here
3. Create 2 Folders within this Folder, Name them: `root` and `Vanilla Files`
4. Copy and Paste the Contents of the Epoch Server Files you downloaded earlier in to the `Vanilla Files`. This Folder will act as a redundant copy of Fresh Server Files if you are ever to need them again
5. Open your Arma 2 OA Install Directory (from Steam) and Copy and Paste the Contents into the `root` Folder of your Server
6. Open your Arma 2 (Base Game) Install Directory and Copy and Paste the `AddOns` folder in to the `root` Folder of your Server
7. Copy the `DZE_Server_Config` Folder from the `Vanilla Files` Folder in to the `Epoch Server Folder`. You should now have 3 Folders in the `Epoch Server` Folder: `DZE_Server_Config`, `root`, and `Vanilla Files`.
8. Copy and Paste all except `DZE_Server_Config`,`SQL`,`Tools` & `Visual Studio C++ Redistributables` in the the `root` Folder (where you copied Arma 2 OA in to previously)

You should now have a Folder called `Epoch Server`, containing 3 Subfolders: `DZE_Server_Config` (containing a `BattlEye` & `Users` Folder, as well as loads of `.cfg` & `.bat` Files), `root` (Containing Arma 2 OA, Arma 2 Addons, an `@DayZ_Epoch_Server` Folder, an `@DayZ_Epoch` Folder and other Files & Folders), and `Vanilla Files` (Containing an unedited copy of the Epoch Server Files you downloaded previously)


## Database Setup
1. Open up MySQL Workbench, click on `Local instance MySQL80` (enter the Password if need be), in the `Navigator` Pane on the Left Side, at the bottom click `Schemas`. You Should See a Schema called `sys`.
2. Right Click within the empty space in the Navigator (below the `sys` Schema) and Click `Create Schema`. Call the Schema `dayz_epoch` and click Apply. Double Click on the `dayz_epoch` Schema in the `Navigator` Pane, `dayz_epoch` should now be **bold** (this indicates it is selected)
3. Open a new Query Tab (Underneath `File` in the Top Left, the Icon looks like a Page, with `SQL` and a + on it. Drag and Drop the `epoch.sql` File from `Vanilla Files\SQL` in to the newly opened Query Tab. It should now be populated with SQL Code. Click the Icon that looks like a Lightning Bolt located just above the SQL Code to execute the SQL Script.
4. Drag and Drop the `add_recommended_mysql_events.sql` File from `Vanilla Files\SQL` in to the existing Query Window, and Execute it like the previous one.
5. In the Toolbar Menu at the Top Left, go to `Server` -> `Users and Priviledges`. Click `Add Account`, call it `dayz`, and give it a good Password (write it down!), confirm the Password. Go to the `Adminstrative Roles` Tab, and Check the `DBA` Box, and Click `Apply`

## Server Setup
1. Go to your `Epoch Server` Folder, and in to the `DayZ_Server_Config` Folder, open up `HiveExt.ini` with Notepad++ (or your favorite Text Editor). Find the Line that says `Password = ChangeMe`, change `ChangeMe` to the Password you set for the `dayz` Database User you created in the Previous Step. Save the File and Close it.
2. Still within the `DayZ_Server_Config` Folder, open the `11_chernarus.bat` File in Notepad++ (or your favorite Text Editor), Delete all Text from the File, and paste the below inside: 
```bat
@echo off
cd C:\Epoch Server\root\
start "arma2" /min /high arma2oaserver.exe -port=2302 "-config=C:\Epoch Server\DZE_Server_Config\11_chernarus.cfg" "-cfg=C:\Epoch Server\DZE_Server_Config\basic.cfg" "-profiles=C:\Epoch Server\DZE_Server_Config\" -name=server "-mod=@DayZ_Epoch;@DayZ_Epoch_Server;"
```
3. Open the `11_chernarus.cfg` File in Notepad++ (or your favorite Text Editor)
4. Set the `hostName` option to whatever you want to name your Server (IE what it shows up as in the Server List & DayZ Launcher). You may also set a Joining Password by changing the `password` option. (We recommend this while setting up & editing your Server to stop Randoms joining your Server and Messing you up. You may also want to set a random password for the `passwordAdmin` option too. There are multiple other Options for you to set here if you wish see the [BIKI](https://community.bistudio.com/wiki/Arma_2:_Server_Config_File) for more information, leave the `class Missions...` Section as it is.
5. When you are Ready, Launch up your Server via the `11_chernarus.bat` File (The Server is ready to join when the Server Console Window Opens.
6. To Join Your Server, Open up Arma 2 OA with the Epoch Mod Loaded, open the Multiplayer Menu, and Click `LAN`. Your Server will show up there with the name you set earlier in `11_chernarus.cfg`, and you can join with the Password you (may or may not have) set in `11_chernarus.cfg`

***Debugging: If you have any problems with the server -> go to `DZE_Server_Config` -> `arma2oaserver.RPT` is where your logs and errors will be 90% of the time. If you have problems on the Client side -> Open File Explorer -> At the top in the address bar and type `%userprofile%\AppData\Local\ArmA 2 OA` *** and hit Enter. Your Client Log (refered to as Client RPT) will be the file named `ArmA2OA.RPT`***

## Server Setup Complete
Your server should run and not have any problems now, if it does not start please refer to ++Debugging++.

[Click Here to Continue to Next Step](../main/EditingTheServer.md) or [Return Home](../main/README.md)
