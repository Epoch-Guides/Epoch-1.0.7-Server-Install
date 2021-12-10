# Making Battle Eye Exceptions
BattleEye reads `.txt` files from the folder, it then reads everything after the function name, for example in `DZE_Server_Config\BattleEye\scripts.txt` line 40 says `1 execVM` , 1 being the filter style and `execVM` being the function, everything after are the Exceptions. Exceptions allow someone to execute that function in a certain way without being kicked by BattleEye. Please read the [Battle Eye Filters Guide](https://github.com/AsYetUntitled/Framework/wiki/BattlEye-Filters) to get a better understanding then come back.

## Generating Restrictions
If you followed the 'Making Edits' in [this](../writeup/EditingTheServer.md) then you should have all of your filters inside the `DZE_Server_Config\BattleEye\scripts.txt`set to `1`'s, we are now going to launch the game and join the server and when you get in, press F2 and do everything the admin menu allows you to. This will generate the restrictions(kicks) that would normally happen. Once you are done testing every admin tool available, close the server. If you navigate to `DZE_Server_Config\Battle` you will notice a new file called `scripts.log` , this is filled with all the restrictions we've just generated. When a mod tries to call one of the Functions but does not have an Exception for it, BattleEye will kick the user. It will then note this in `scripts.log` with the exact code that tried to call the function in quotes, along with the filter number.

## Generating Exceptions for Restrictions
First let's open the Setup Guide Files folder we downloaded -> copy the `BE_AEG.exe` and the `with console debug.bat` into your BattleEye folder.
Now, we need to generate Exceptions for the restrictions that were created by the Admin Tools (because flying and teleporting ect, do not have exceptions by default). But when we look at `scripts.log` we only need to look at the Restrictions that contain a random line(variable) of letters and numbers, for example 
```sql 
#79 "] call BQ1vBKUInpSNuc;
			};
		};

		if (-1 > -1) then {setViewDistance -1};
		if (25 > -1) then {setTerrainGrid 25};
		if (true"
```
with `BQ1vBKUInpSNuc` being the random variable and `setViewDistance` being the function.
The reason we are only looking at and making exceptions for them is because the Admin Tools generates new variables every time the server starts again, so we have to add manual exceptions that will cover the code around them. All of the other restrictions should be fixed when we run the `BE_AEG.exe` by double clicking the `with console debug.bat` file. In order to fix this we need to make an exception that gets as much of the code as possible but also removing the variable. If you followed the [Battle Eye Filters Guide](https://github.com/AsYetUntitled/Framework/wiki/BattlEye-Filters) you know we need to break this down do let's do it.
``` sql
 "] call BQ1vBKUInpSNuc;
 ```
 Contains the problem variable. So let's start making the exception after it. Like this:
 ``` sql
  !"};\n		};\n\n		if (-1 > -1) then {setViewDistance -1};\n		if (25 > -1) then {setTerrainGrid 25};\n		if (true"
```
So we head to `scripts.txt` and find line 79, we then go up two to line 81 because the filters don't start on line 1, it says `//new2` and the first filter `1 addAction` is 0, in programming numbers don't start at 1, they start at 0. So now line 81 says `1 setViewDistance` and since that is the Function being called in the code, we know we are right, click on the line, hit the End key on your keyboard, and copy the exception to the end of the line. Now we know how to make exceptions for the Admin Tools random variable restrictions. Please continue to find as many as you can with the random variables and fix them. Once you are done fixing them, navigate to your Battle Eye folder and double click on `with console debug.bat` and it will then auto generate the exceptions needed for all of the other restrictions.

## Done
Restart your game and Server and rejoin, then leave, and check `scripts.log`, if it is not there, you are done. Please click continute below.

[Continue](../writeup/README.md)
