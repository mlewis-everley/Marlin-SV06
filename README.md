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


## Join Sovol Community

- Sovol Facebook page: https://www.facebook.com/sovol3d/
- Sovol Youtube Channel: https://www.youtube.com/c/Sovol/videos
- Sovol Offcial User Group: https://www.facebook.com/groups/sovol3d
- Sovol Forum website: https://forum.sovol3d.com/

## Related tutorials 

- User Manual. [Click here](https://drive.google.com/drive/folders/10uJUe-J0IutQSNI4IS-Tbwym4Ch8Yw6x)

## Learn more & How to Buy it

- Sovol website: https://sovol3d.com
- SV06 Product Page: https://sovol3d.com/products/sovol-sv06-direct-drive-3d-printer

## Notice

This is a fork of the official source code for the Sovol SV06. 

The damage caused by modifying firmware also using the third party firmware will lose the 1 year warranty. If you need support, it’s recommended to reflash the stock firmware before contacting sovol.

Sovol doesn’t provide tech help for help users to modify source code, but if you need us to add more functions, you are welcome to send us your suggestions via Facebook Messenger or email 
info@sovol3d.com