# LulzBot Retro Marlin firmware

This is clone of Lulzbot's Marlin repo.  Most things should look very familiar.

The source on this repository can compile firmware for the TAZ 6 using an Einsy Retro board.  The build directory contains firmware images for the Einsy and many of the new tool heads for the Taz 6 (including the default hexagon based hotend).

# Safety and warnings:

**This repository may contain untested software.** It has not been extensively tested and may damage your printer and present other hazards. Use at your own risk. Do not operate your printer while unattended and be sure to power it off when leaving the room. Please consult the documentation that came with your printer for additional safety and warning information.

# Compilation from the command line on Linux using "avr-gcc"

Run the "build-lulzbot-firmware.sh" from the top level directory. This will build the ".hex" files for every combination of the Taz 6 and supported toolheads . The ".hex" files will be saved in the "build" subdirectory.

Images built here will have the following naming convention...
```
build/Marlin_Oliveoil_TAZ6_Retro_Tilapia_SingleExtruder_1.1.9.29.2_aee71de48.hex
                                                        ^^^^^^^^^^
                                                        Note the version
                                                        Marlin FW: 1.1.9
                                                        Lulzbot Version: 29
                                                        Retro Version: 2                                     
```

# Compilation using Arduino IDE

To select what firmware to build, modify the lines starting with "//#define" towards the bottom of the "Marlin/Configuration_LulzBot.h" file. Remove the leading "//" and modify the text after "LULZBOT_" and "TOOLHEAD_" so that it specifies the desired printer model or the desired toolhead, as listed in the top of the file.

To compile for a TAZ using a standard toolhead, modify the lines such that they read:
```
  #define LULZBOT_Oliveoil_TAZ6_Retro
  #define TOOLHEAD_Tilapia_SingleExtruder
```
Then, open the "Marlin.ino" file from the "Marlin" subdirectory in the Arduino IDE. Select the board "Arduino/Genuino Mega or Mega 2560" from the "Board" submenu menu of the "Tools" menu and the port to which your printer is connected from the "Port" submenu from the "Tools" menu.

To compile and upload the firmware to your printer, select "Upload" from the "Sketch" menu.
