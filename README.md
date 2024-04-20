# Marlin 2.1.x SV06 Edition

The Sovol SV06 is a budget printer with some great features and makes use of a linear rod based motion system and an all metal hotend with orbital direct geared extruder.

The original firmware was a fork of Marlin released by [Sovol](https://github.com/Sovol3d/Sv06-Source-Code).

This was later rebased onto stock Marlin by [blastrock](https://github.com/blastrock/Marlin-sv06/tree/rebase-sovol-2.1.2-xtwist)

This version is a fork of the blastrock version with additional tuning and quality of life features.

## Additions to SV06 Marlin

This build of Marlin includes the following features:

* Input shaping enabled (with menu) and some initial config, based on the [Patshead website](https://blog.patshead.com/2023/10/marlin-input-shaping-on-the-sovol-sv06-three-months-later.html)
* Increased feedrates on Z for homing and gantry alignment (the stock speeds are SLLLOOOOOOOOWWWWWWWWWWW)
* Increased feedrates for XYZ on bed probing (not second probe)
* Additional "host" menu items (for tighter integration with octoprint)
* Cancel objects support
* Increased print accelerations and voltages
* 1/64 Microstepping on X and Y (for smoother operation at higher speeds)
* Move z-safe home location to front left (easier if you need to try and recover a print)
* Improved stock temperature profiles and addition of "PETG"

## How to install

If you have never flashed your firmware before, the process is fairly simple:

1. Download the latest built binary from: https://github.com/mlewis-everley/Marlin-SV06/releases
2. Transfer this binary to an empty SD card (formatted to FAT32)
3. Turn off the printer and insert the SD card with the firmware
4. Turn the printer back on.
5. If the printer has seen the firmware, then you should see the plain blue bootup screen for about 5 - 10 seconds before the latest firmware loads.

### Firmware not recognised

If point 5 the above does not happen, the printer may have not recognised the firmware (this happens sometimes).

Rename the firmware binary file to something new (keep the .bin extension) and also ensure the new file name is a different character length (Eg: `firmware.bin` > `firmware-new.bin`).

If this does not take again, try renaming the file until the printer recognises the file (it will eventually).

### EEPROM Error

After flashing, you may get an  `EEPROM Error` on the screen. This is normal, just choose "reset".

You may also get the message a second time (after you reset it once), again, this is normal, just choose "reset" again.

## Next Steps

After instalation, perform some additional setup steps:

### 1. Initialise EEPROM

This will reset the printers ROM with new firmware defaults, to do this:

1. While on the info screen, click the scroll wheel.
2. From this menu, go to Configuration.
3. From the Configuration menu, go to Advanced Settings.
4. Choose `Initialise EEPROM`.

### 2. Load firmware defaults

This may not be necessary, but via testing, the new firmware default settings didn't always seem to load. To do this you need to:

1. While on the info screen, click the scroll wheel.
2. From this menu, go to Configuration.
3. From the Configuration Menu, select Load Defaults.

### 3. Update/Calibrate ESTEPS

The default ESTEPS in the firmware are set a little higher than standard. Via testing 3 out of 4 machines had ESTEPS of slightly more than 700.

If you have never calibrated your ESTEPS, there is a great guide on [Teaching Tech's website](https://teachingtechyt.github.io/calibration.html#esteps) (you can change the ESTEPS via the Configuration menu).

To update your ESTEPS with a new value, you need to:

1. Get your new calculated ESTEPS
2. While on the info screen, click the scroll wheel.
3. From this menu, go to Configuration.
4. From the Configuration menu, go to Advanced Settings.
5. Go to Edit steps/mm
6. Select Extruder Steps

### 4. Z Probe Offset

Z-Probe offset can be calibrated via a wizard, you can do this by:.

1. While on the info screen, click the scroll wheel.
2. From this menu, go to Motion.
3. Select Z-Probe Wizard
4. Use a piece of paper or gauge (around 0.05mm seems to work OK), use the screen to move the nozzle down until it is just touching the paper/gauge.

### 5. Save your changes

Once you have done the above steps, you have to save these changes to:

1. While on the info screen, click the scroll wheel.
2. From this menu, go to Configuration.
3. From the Configuration menu, select Save Settings.

### 6. Run a gantry leveling

To ensure the X gantry is aligned, you need to run an auto align, to do this:

1. While on the info screen, click the scroll wheel.
2. From this menu, go to Motion.
3. From the Motion menu, select Auto Z-Align.

### 7. Level the bed using a probe

By default, the SV06 was set to auto heat the hotend to 120 and the bed to 60. This was a little problematic and meant that when running host prints, if you had `G29` in your start GCODE then the firmware would reset the temperatures.

This version of the firmware disables that features, but if you plan on using a saved mesh, you will need to preheat the hotend and bed manually (for the best result).

To do this:

1. While on the info screen, click the scroll wheel.
2. From this menu, go to Tempurature.
3. Select Preheat PLA/ABS/PETG.
4. Wait for the bed to heat
5. Go to the Motion menu
6. Select level bed

Once the leveling is complete, the mesh will be stored automatically.

#### Level before each print

If you want to level the bed prior to each print, simply add:

    G29

To your start GCODE in your slicer of choice.

#### Recall a saved mesh before each print

If you want to recall a saved mesh instead of leveling at the start of each print, you will need instead to add:

    M420 S1

This rectores the mesh saved in slot 1 (default) and activates it.

### Reset leveling after home

By default, Marlin will clear a saved mesh after homing `G28`.

The Sovol stock firmware (and this fork) disables this features, so the last saved mesh is retained agter homing.


# Additional Information

## Join Sovol Community

- Sovol Facebook page: https://www.facebook.com/sovol3d/
- Sovol Youtube Channel: https://www.youtube.com/c/Sovol/videos
- Sovol Offcial User Group: https://www.facebook.com/groups/sovol3d
- Sovol Forum website: https://forum.sovol3d.com/

## Related tutorials 

- [User Manual](https://drive.google.com/drive/folders/10uJUe-J0IutQSNI4IS-Tbwym4Ch8Yw6x)
- [Further calibration help from Teaching Tech](https://teachingtechyt.github.io/calibration.html)

## Learn more & How to Buy it

- Sovol website: https://sovol3d.com
- SV06 Product Page: https://sovol3d.com/products/sovol-sv06-direct-drive-3d-printer

## Notice

This is a fork of the official source code for the Sovol SV06. 

The damage caused by modifying firmware also using the third party firmware will lose the 1 year warranty. If you need support, it’s recommended to reflash the stock firmware before contacting sovol.

Sovol doesn’t provide tech help for help users to modify source code, but if you need us to add more functions, you are welcome to send us your suggestions via Facebook Messenger or email 
info@sovol3d.com