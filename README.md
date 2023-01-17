## Nintendont - libertyernie's build

Changes from upstream (https://github.com/FIX94/Nintendont) in this branch:

* You can load a base64-encoded nincfg.bin from the command line (for loading specific games directly from Homebrew Channel entries; also see [NinCFGEditor](https://github.com/libertyernie/NinCFGEditor))
* Controller shortcuts to swap buttons (Y/B vs. B/A) or exit Nintendont have been removed
* There are new default mappings for the Classic Controller, Classic Controller Pro, and Wii U GamePad:
    * Large left shoulder button: full L press
    * Small left shoulder button: half L press
    * Large right shoulder button: full R press
    * Small right shoulder button: half R press
    * Home: Start
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

For more information:

https://github.com/FIX94/Nintendont/blob/27606319cd9ab16231accd0968870ee67c0514d6/README.md  
