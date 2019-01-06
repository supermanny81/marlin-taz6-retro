# LulzBot Retro

This mod is both a firmware and hardware modification.  It's easy to do if you have a little basic experience with electronics, particular the Arduino platform.  You will have to upload a new version of firmware to your retro in order for your printer to work.

## What you will need to do this modification

A drill, a soldering iron, set of drill bits, and a set of allen keys are some of the basic tools you will need to do this mod.  In additon, you will need to purchase the following.

| Item                                                   | Qty |
| ------------------------------------------------------ | --- |
| [Einsy Retro](1) **Buy the kit**                       |   1 |
| [M3 Heat Set Insert for Plastics](2)                   |   4 |
| [M3 x 0.5mm Thread, 8mm Long Screws](3)                |   4 |
| M3 washers                                             |   4 |
| [10P 5x2 IDC Flat Ribbon Data Cable 2.54mm](4) _maybe_ |   2 |

**Note: the flat ribbon cables are only necessary if you are upgrading from a Rambo 1.3L.  Taz 6 units with a RAMBO 1.4 already have the correct cable.**

And then print out these items.
| Item                                           | Qty |
| ---------------------------------------------- | --- |
| [Einsy Mount](stl-1)                           |   1 |
| [Reset Button Jig](stl-2) _optional_           |   1 |

## Installing the Einsy Retro board

The Einsy boards dimensions differ from the Rambos.  To use one in a Taz 6 case you will need to print out a new mount.  I recommend printing enough perimiters to makes the posts solid material.  Printing with 3 shells should suffice and 20% infill should work.  It's not a long print and you'll appreciate the extra plastic.  The STL for the mount is located here  [/stl/taz6-einsy-mount.stl](stl-1).

#### Lets get started...

Begin by unplugging your Taz unit, opening the back case and verifying that you have the correct ribbon cables needed for the upgrade.  If your board is a RAMBO 1.3L, you will need to purchase the ribbon cables if you haven't already done so.

Next remove the cables for Extruder 2.  I remove the whole thing since multiple extruders won't be option for me anymore unless I go down the MMU or Palette path.
![Rambo without Extruder 2](img-1)

![Mount with inserts](img-2)

![Mount in Taz](img-3)

![Reset Button Jig](img-4)

## LulzBot Retro Marlin firmware

This is clone of Lulzbot's Marlin repo.  Most things should look very familiar, just some macros and settings were changed where applicable, some stls were added along with these instructions.

The source on this repository can compile firmware for the TAZ 6 using an Einsy Retro board.  The build directory contains firmware images for the Einsy and many of the new tool heads for the Taz 6 (including the default hexagon based hotend).  

Using Cura connect to your upgraded printer and upload a custom firmware.

#### Safety and warnings:

**This repository probably has stuff that hasn't been tested.**  The same message that the Marlin and Lulzbot folks give you applies here.

#### Compilation from the command line on Linux using "avr-gcc"

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

#### Compilation using Arduino IDE

To select what firmware to build, modify the lines starting with "//#define" towards the bottom of the "Marlin/Configuration_LulzBot.h" file. Remove the leading "//" and modify the text after "LULZBOT_" and "TOOLHEAD_" so that it specifies the desired printer model or the desired toolhead, as listed in the top of the file.

To compile for a TAZ using a standard toolhead, modify the lines such that they read:
```
  #define LULZBOT_Oliveoil_TAZ6_Retro
  #define TOOLHEAD_Tilapia_SingleExtruder
```
Then, open the "Marlin.ino" file from the "Marlin" subdirectory in the Arduino IDE. Select the board "Arduino/Genuino Mega or Mega 2560" from the "Board" submenu menu of the "Tools" menu and the port to which your printer is connected from the "Port" submenu from the "Tools" menu.

To compile and upload the firmware to your printer, select "Upload" from the "Sketch" menu.


[1]: https://ultimachine.com/products/einsy-retro
[2]: https://www.mcmaster.com/catalog/124/3395
[3]: https://www.mcmaster.com/94500a222
[4]: https://www.amazon.com/gp/product/B07FZXKN4K/ref=oh_aui_detailpage_o01_s00?ie=UTF8&psc=1

[stl-1]: https://github.com/supermanny81/marlin-taz6-retro/blob/master/stl/taz6-einsy-mount.stl
[stl-2]: https://github.com/supermanny81/marlin-taz6-retro/blob/master/stl/reset-button-jig.stl

[img-1]: https://raw.githubusercontent.com/supermanny81/marlin-taz6-retro/master/media/taz6-rambo-1.3L.jpg
[img-2]: https://raw.githubusercontent.com/supermanny81/marlin-taz6-retro/master/media/mount-with-inserts.jpg
[img-3]: https://raw.githubusercontent.com/supermanny81/marlin-taz6-retro/master/media/mount-in-taz.jpg
[img-4]: https://raw.githubusercontent.com/supermanny81/marlin-taz6-retro/master/media/mount-in-taz.jpg
