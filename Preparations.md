# Preparing to Make the Server
This is assuming you have administraitive rights on your computer, and that you have a basic understanding of how to navigate Windows and have Steam with Arma 2 and Arma 2: Operation Arrowhead in your library.
You will want to restart after finishing these.
## Preparing Arma & Epoch
* Download and install Arma 2 and Arma 2 Operation Arrowhead via Steam. After both games are installed, be sure to Verify Integrity of Game Files (Right Click on the Game(s) in your Library -> Properties -> Local Files -> Verify integrity of game files). Run Arma 2 until the main menu, then close it, and run OA till main menu then close it.

* Download and install [DayZ Launcher](http://app.dayzlauncher.com/updates/setup_dzlauncher.exe), After DayZ Launcher has installed, Launch it and Open the Settings Panel (Top Right). Set the `Mods/Downloads Path` to your Arma 2 OA Install Directory (Example. `C:\Program Files (x86)\Steam\steamapps\common\Arma 2 Operation Arrowhead`). And Set the `Arma 2 Path` to your Arma 2 (Base Game, NOT OA!) Install Directory (Example. `C:\Program Files (x86)\Steam\steamapps\common\Arma 2`).Scroll down and hit `Save` then close the Settings Panel, and Navigate to the `Mods` Tab in DayZ Launcher. Find `DayZ Epoch 1.0.7` In the Mods List, and Click Download. Once the Mod has finished downloading, be sure to Verify the Install by Clicking the Verify Button

* Download [Epoch 1.0.7 Server Files](https://drive.google.com/file/d/1jDn86sfTwcRae4NZgHK76k_CaY1jOUP2/view)


## Installing MySQL Server & Workbench (Database)
* Download [MySQL Server](https://dev.mysql.com/downloads/file/?id=508935). Download the one that has the smallest size, once it has downloaded, run the Installer. Select the `Server only` Setup Type, Click Next and then Execute, you might have to install some Redistributables during this process. Follow the Installer Process until you reach the `Product Configuration` Section, Press Next Once, and you should come to the `Type and Networking` Page.

* Installing MySQL Server & Workbench can be confusing to those with little to no experience, particularly this next Section, so please read carefully. 
The `Config Type` Option: If you are planning to Host this Server on a Home Machine, you can leave the Settings on this Page as they are and click Next. If you are Hosting from a (relatively decent) Dedicated Server Machine, select `Server Computer`, and leave the rest of the options as they are and click Next. `Authentication Method`: You *can* leave this Setting as it is for now, however this *might* cause problems further down the line; we can edit this option at any time by re-running the MySQL Server Installer.
`Accounts and Roles`: MySQL has a "root" User Account, which is a user that has full priviledges on the Server, so be sure to set the Root Password to be strong and secure, keep a note of it if you need to. You May Add & Configure MySQL Users on this Page if you wish to do so, for the sake of simplicity for this Guide, we will not run over this. Click Next. The `Windows Service` Page: Leave this Page as it is, and click Next, and Click Execute on the Next Page, the Finish the Installation.

* Download MySQL Workbench [here](https://dev.mysql.com/downloads/file/?id=507335) and run the Installer. Follow the Installer, select the `Complete` Setup Type, press Next, then Install, once the Install has Completed, Launch MySQL Workbench. Click on the `Local instance MySQL80` Box, enter your Root Account password you set earlier. You should now be presented with a fairly confusing looking screen, if that is the case, then you can Minimize MySQL Workbench for now, we will continue here in a little while.

* Download and Install [PBO Manager](https://drive.google.com/file/d/1V_ivuaVIkDJuqULvhwAfbEtlp45eOE-X/view?usp=sharing), to make sure your PBO Manager was installed correctly go to Windows Settings -> type "defaults" -> Default Apps -> Choose default apps by file type -> Scroll down to '.pbo' on the left and make sure PBO Manager is the application assigned to it. You should see the icon next to PBO files now.

* Download and install [WinRAR](https://www.win-rar.com/fileadmin/winrar-versions/winrar/th/winrar-x64-602.exe) or [7 Zip](https://www.7-zip.org/a/7z2106-x64.exe)

* Download and install [Visual Studio Code](https://code.visualstudio.com/docs/?dv=win) and [Notepad++](https://github.com/notepad-plus-plus/notepad-plus-plus/releases/download/v8.1.9.3/npp.8.1.9.3.Installer.x64.exe) we will be using both!

* Download the [Setup Guide Files folder](https://drive.google.com/drive/folders/1ln5BWdNLfw1AcWfyHHCORErb2O-bQwIo) from the google drive to follow along with.

## Done
We have done every we can up until this point. The Next Step is Setting up the Epoch Server!  
[Click Here to Continue to Next Step](../main/ServerSetup.md) Or [Return to ReadMe](../main/README.md)
