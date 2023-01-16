## Nintendont - libertyernie's build

Changes from upstream (https://github.com/FIX94/Nintendont) in this branch:

* You can load a base64-encoded nincfg.bin from the command line (for loading specific games directly from Homebrew Channel entries; also see [NinCFGEditor](https://github.com/libertyernie/NinCFGEditor))
* Controller shortcuts to swap buttons (Y/B vs. B/A) or exit Nintendont have been removed
* There are new default mappings for the Classic Controller, Classic Controller Pro, and Wii U GamePad:
    * Large left shoulder button: full L press
    * Small left shoulder button: half L press
    * Large right shoulder button: full R press
    * Small right shoulder button: half R press
    * Select / Minus: Z
* Special controller overrides for the Classic Controller, Classic Controller Pro, and Wii U GamePad:
    * **The Legend of Zelda: Four Swords Adventures**
	    * D-Pad => Left Stick
		* Select => D-Pad Down
    * Super Puzzle Bobble / Bust-A-Move 3000 / Bust-A-Move All-Stars
        * Both left shoulder buttons -> full L press
        * Both right shoulder buttons -> full R press
        * D-pad diagonals -> D-pad horizontals
        * Analog stick diagonals -> analog stick horizontals or verticals (whichever is closer)

To build on Windows, you might need to set the "windows" variable so the build process can find zip.exe:

    $ windows=1 make

You'll also want to make sure the devkitpro folder with libwinpthread-1.dll is in your PATH.

.dol files (if any) are in the Releases section on GitHub.

### Nintendont
A Wii Homebrew Project to play GC Games on Wii and vWii on Wii U

### HOWTO ###
* Connect your XBOX360 controller then start Nintendont-XBOX360. (Order is optional.)
* The XBOX360 LED 1 should now light up and the gamepad should react.<br>
  If you start a game the WiiMote LED says player 2.
* If your controller doesn't work try one of these options:
    1. Restart Nintendont-XBOX360 or your Wii.
    2. Replug your controller.
    3. Plug in your controller after you have started a game. 
    4. If it is still not working, try my USB gamepad tester [RetrodeTest](https://github.com/revvv/snes9xgx-retrode/releases/download/0.5/RetrodeTest-0.2.zip)
    to check if your Gamepad works at all.
    5. Set `EndpointOut=0` in`/controller/045e_028e.ini`. This will disable rumble and LED will flash.<br>
    Also use this settings if your Wii crashes. (Rare crashes are normal, though.)
  
### Turn on LED and rumble ###
* If the LED keeps flashing, this means that the LED cannot be set and also rumble will not work.
  Try to set `EndpointOut=2` in [/controller/045e_028e.ini](https://github.com/revvv/Nintendont-XBOX360/blob/master/controllerconfigs/045e_028e.ini).<br>
  The default is `EndpointOut=1` which is surprisingly correct for my controller ;-)<br>
  There are controllers which are not compatible with these settings. You could try the values 1-8.<br>
  Maybe check `lsusb -v -d 045e:028e` and grep for `OUT`. [Example output](https://gist.github.com/rombert/6902ab691e12ab478e31)

### Debugging ###
* Enable _Debugger_ and _Log_ in Nintendont-XBOX360 settings.
* Check log file `/ndebug.log`.
* The log file is not always written: Best practice is to start a game, then plug in your controller, then quit.

#### Download ###
* [Release](https://github.com/revvv/Nintendont-XBOX360/releases/)
* Unpack it to your SD card.
* Put games in folder `/games`
* *Optional:* Configure button layout in [/controller/045e_028e.ini](https://github.com/revvv/Nintendont-XBOX360/blob/master/controllerconfigs/045e_028e.ini).<br>
  __NEW:__ Fixed XBOX360 rumble for vWii<br>
  __NEW:__ Support 3rd party WiiMote + Nunchuk (labeled with "NEW2in1" and "Motion plus", distributed by Haiwai Consulting/Tiger-Zhou UG)
  
### Compile
Get these versions: devkitppc r29-1, devkitarm r47 and libogc 1.8.16 and execute _make_. 

### Disclaimer
This software comes without any warranty. I am not responsible for any damage to your devices. Please make backups!

### Compiling:
For compile Nintendont yourself, get the following versions of the toolchain compiling PPC tools:
* **devkitARM r53-1**
* **devkitPPC r35-2**
* **libOGC 1.8.23-1**

These versions can be downloaded here: https://www.mediafire.com/folder/j0juqb5vvd6z5/devkitPro_archives

On Windows, run the "Build.bat" batch script for build Nintendont.

On Unix, run the "Build.sh" script.

Please use these specific versions for compiling Nintendont, **because if you try to compile them on latest dkARM/dkPPC/libOGC, you'll get a lot of compiler warnings and your build will crash when attemping to return to Nintendont menu**, so be warned about that.

### Notes
* The Wii and Wii U SD card slot is known to be slow. If you're using an SD card and are having performance issues, consider either using a USB SD reader or a USB hard drive.
* USB flash drives are known to be problematic.
* Nintendont runs best with storage devices formatted with 32 KB clusters. (Use either FAT32 or exFAT.)
