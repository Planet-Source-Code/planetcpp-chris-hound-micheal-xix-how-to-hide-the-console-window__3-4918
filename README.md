<div align="center">

## How to Hide the Console Window


</div>

### Description

Sometimes when your developing an application you come across the need or want to

use a console app to get part of the job done, or maybe you have a program where batch

files are performing certain actions you need. No matter what the reason, if there's

no output then theres no reason for your user to be subjected to a console window being

splashed on the screen for a moment, or worse, have it remain visible for a long time.

Face it, the console window is nothing pretty to look at, even in XP.

Here's a way for you to bypass the console window and shoot straight to main().

There's a function called mainCRTStartup thats sole purpose is to parse the command

line arguments and then call main while passing the arguments to main also.

In C++ you can set the entry point for you application and if you want to skip straight

to main or WinMain (In Windows applications) then you tell it to start at mainCRTStartup

or WinMainCRTStartup accordinglly.

Most of you will be using different compilers so it won't get into how you set the entry

point for every compiler there is, instead we'll use my favorite preprocessor directive

#pragma. You can set linking options among other things with this, and all you need to do

is add this line above your code:

#pragma comment( linker, "/subsystem:\"windows\" /entry:\"mainCRTStartup\"" )

Here is a small example, this program will play the system start sound 3 times then exit.
 
### More Info
 
do NOT take input with this from the console obviouslly.


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[PlanetCPP\-Chris\(Hound\)/Micheal\(xix\)](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/planetcpp-chris-hound-micheal-xix.md)
**Level**          |Intermediate
**User Rating**    |4.4 (31 globes from 7 users)
**Compatibility**  |C\+\+ \(general\), Microsoft Visual C\+\+, Borland C\+\+
**Category**       |[Miscellaneous](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/miscellaneous__3-1.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/planetcpp-chris-hound-micheal-xix-how-to-hide-the-console-window__3-4918/archive/master.zip)





### Source Code

```
#include <windows.h>
#include <mmsystem.h>
#pragma comment(lib,"winmm.lib")
#pragma comment( linker, "/subsystem:\"windows\" /entry:\"mainCRTStartup\"" )
int main(void)
{
	PlaySound("SystemStart",NULL, SND_ALIAS|SND_SYNC);
	Sleep(50);
	PlaySound("SystemStart",NULL, SND_ALIAS|SND_SYNC);
	Sleep(50);
	PlaySound("SystemStart",NULL, SND_ALIAS|SND_SYNC);
	Sleep(50);
	return 0;
}
```

