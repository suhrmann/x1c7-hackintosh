# macOS on Thinkpad X1 Carbon 7th Generation, Model 20QE\*
 
<h2 align="center"> ‼️ Forked from Tyler Nguyen's repo <a href="https://github.com/tylernguyen/x1c6-hackintosh">x1c6-hackintosh</a> ‼️</h3>
<p align="center">
    If this helped you. Please consider donating to <a href="https://github.com/tylernguyen">@tylernguyen / x1c6-hackintosh </a>. <br>
    <a href="https://tylerspaper.com/support">❤️ Sponsor Tyler Nguyen</a>
</p> 

**Note:** I did not update most of the docs (for X1C7 / X1 Carbon 7th Gen) _yet_ 🙄

-----

[![macOS](https://img.shields.io/badge/macOS-Catalina-yellow.svg)](https://github.com/996icu/996.ICU/blob/master/LICENSE)
[![version](https://img.shields.io/badge/10.15.5-yellow)](https://github.com/996icu/996.ICU/blob/master/LICENSE)
[![BIOS](https://img.shields.io/badge/BIOS-1.45-blue)](https://github.com/996icu/996.ICU/blob/master/LICENSE)
[![MODEL](https://img.shields.io/badge/Model-20QE*-blue)](https://github.com/996icu/996.ICU/blob/master/LICENSE)
[![OpenCore](https://img.shields.io/badge/OpenCore-0.5.9-green)](https://github.com/996icu/996.ICU/blob/master/LICENSE)
[![LICENSE](https://img.shields.io/badge/license-MIT-green.svg)](https://github.com/996icu/996.ICU/blob/master/LICENSE)

<img align="right" src="https://i.imgur.com/I3yUS4Q.png" alt="Critter" width="300">

### Check out Tyler's blog [tylerspaper.com](https://tylerspaper.com/)

#### READ THE ENTIRE README.MD BEFORE YOU START.

#### I am not responsible for any damages you may cause.

### Should you find an error, or improve anything, be it in the config itself or in the my documentation, please consider opening an issue or a pull request to contribute.

`I AM A ONE MAN TEAM, AND A FULL TIME STUDENT. SO, I MIGHT NOT BE ABLE TO RESPOND OR HELP YOU IN A TIMELY MANNER. BUT, I PROMISE I WILL GET TO YOU EVENTUALLY. PLEASE UNDERSTAND.`

`Lastly, if my work here helped you. Please consider donating to Tyler.` <br>
[❤️ Sponsor Tyler Nguyen](https://tylerspaper.com/support)

> ## Update

##### Recent | [Changelog Archive](https://github.com/tylernguyen/x1c6-hackintosh/blob/master/docs/CHANGELOG.md)

> ### 2020-6-1

#### Changed

- OpenCore to 0.5.9
- Upgraded various Acidanthera kexts.
- Recompiled various SSDT with new iasl libraries.
- Replaced `SSDT-EXT3` with `SSDT-LED`
- Change SSDT OEM ID to `tyler` to somewhat track distributions and usage across various projects

> ## SUMMARY:

**`In short, x1c7-hackintosh is very stable and is currently my daily driver. I fully recommend this project to anyone looking for a MacBook alternative.`**

| working | Device / Step                             | Comment            |
|:-------:|:------------------------------------------|:-------------------|
| ☑️ | **Basic Setup**                                 | Working base config in ``EFI-install_USB``, see release [EFI-install_USB](https://github.com/suhrmann/x1c7-hackintosh/releases/tag/EFI-install_USB) |
| ✅ | Booting Clover Bootloader                      |                    |
| ✅ | Booting macOS installer                        |                    |
| ✅ | Installed to HD                                |                    |
| ➖ | <p> **Post-Install** <p>                       |                    |
| ✅ | Graphics                                       | Working in ``EFI-install_USB`` <br> ⚠️ ToDo: Fix HiDPI (I have 1080p display, so for me low prio) |
| ✅ | Touchpad                                       | Requires ``VoodooI2C`` with ``XOSI`` ACPI patch|
| ✅ | Trackpoint                                     | Requires ``VoodooPS2`` |
| ✅ | Keyboard                                       | Requires ``VoodooPS2`` |
| ✅ | Keyboard-Multimedia Fn keys                    | need [ThinkpadAssistant](https://github.com/MSzturc/ThinkpadAssistant) |
| ❌ | WiFi                                           | ❗️Intel WiFi has no Kext yet (at 2020-06-15) - hoping for the awesome [@zxystd/itlwm](https://github.com/zxystd/itlwm) |
| ❌ | Bluetooth                                      | Integrated in Intel WiFi/BT - currently (2020-06-15) unsupported  |
| ❌ | WWAN                                           | DISABLED at BIOS |
| ❓ | Ethernet                                       | IntelMausi (?) |
| ❓ | Hibernation                                    |           |
| ❓ | HDMI output                                    |           |
| ❓ | USB A / USB C                                  |           |
| ❓ | Thunderbolt 3                                  | ⚠️ See [@tylernguyen/x1c6-hackintosh, Issue #24](https://github.com/tylernguyen/x1c6-hackintosh/issues/24#issuecomment-603183002)         |
| ❓ | Webcam                                         |           |
| ✅ | Audio                                          | ✅ _Internal Speaker_ and _Headphones_ / _Line in_ <br> ⚠️ _Internal Microphone_ not working <br> Realtek ALC285, layout 11, 21, 31 (all seem to work except Internal Microphone) ➡️ ``boot-args: alcid=11`` |
| ❓ | iCloud (App Store, iMessage, FaceTime, etc)    |           |
| ❓ | HiDPI, Handoff, Sidecar                        |           |
| ❌ | Fingerprint Reader                             | DISABLED at BIOS; If enabled in BIOS Touchpad does not work in MacOS |
| ❓ | Power Management Optimizations                 | ⚠️ Like [@tylernguyen/x1c6-hackintosh, Issue #28](https://github.com/tylernguyen/x1c6-hackintosh/issues/28) |

> ✅ Fully functional; ❓Untested, might work; ❌ Non-functional

**For more information regarding certain features, please refer to [`docs/3_README-POSTinstallation.md`](https://github.com/tylernguyen/x1c6-hackintosh/blob/master/docs/3_README-POSTinstallation.md)**

> ## NEEDED:

A macOS machine would be VERY useful: to create install drives, and for when your ThinkPad cannot boot. Though it is not completely necessary.  
Flash drive, 16GB or more.  
Xcode works fine for editing plist files, but I prefer [PlistEdit Pro](https://www.fatcatsoftware.com/plisteditpro/).  
[MaciASL](https://github.com/acidanthera/MaciASL), for patching ACPI tables.  
[IOJones](https://github.com/acidanthera/IOJones), for diagnosis.  
[Hackintool](https://www.insanelymac.com/forum/topic/335018-hackintool-v286/), for diagnosis.

> ## WHERE TO START:

Explore links included this README, especially those in references and other x1c6-hackintosh repos.

Once you are ready, follow the series of README files included `docs/`.  
[**1_README-HARDWAREandBIOS**](https://github.com/tylernguyen/x1c6-hackintosh/blob/master/docs/1_README-HARDWAREandBIOS.md): Requirements before starting.  
[**2_README-installMEDIA**](https://github.com/tylernguyen/x1c6-hackintosh/blob/master/docs/2_README-installMEDIA.md): Creating the macOS install drive.  
[**3_README-POSTinstallation**](https://github.com/tylernguyen/x1c6-hackintosh/blob/master/docs/3_README-POSTinstallation.md): Settings and tweaks post installation.  
[**4_README-ACPIpatching**](https://github.com/tylernguyen/x1c6-hackintosh/blob/master/docs/4_README-ACPIpatching.md): The hardest and most time consuming part, patching the system ACPI table for battery status, brightness, sleep, thunderbolt, thunderbolt hotplugging, etc...  
[**5_README-other.md**](https://github.com/tylernguyen/x1c6-hackintosh/blob/master/docs/5_README-other.md): for other notices

- While you can plug-and-play most of my hotpatches if you have an x1c6, I still suggest that you dump and disassemble your own DSDT. This is imprortant as your DSDT maybe different from mine. And furthermore, you get to learn more about what's actually going on.

> ## MY SPECIFICATIONS:

**Again: This are my hardware specs of `20QES01L00`:**
Refer to [ThinkPad_X1_Carbon_7th_Gen_Spec.PDF](https://github.com/suhrmann/x1c7-hackintosh/blob/master/docs/references/ThinkPad_X1_Carbon_7th_Gen_Spec.PDF) for possible stock ThinkPad X1 7th Gen configurations. <br>
Source: [Lenovo Product Specification Reference (PSREF) [psref.lenovo.com]](https://psref.lenovo.com/Product/ThinkPad/ThinkPad_X1_Carbon_7th_Gen)

| Processor Number                                                                                                                   | Code Name    | # of Cores | # of Threads | Base Frequency | Max Turbo Frequency | Cache | Memory Types | Graphics      |
| :--------------------------------------------------------------------------------------------------------------------------------- | :----------- | :--------- | :----------- | :------------- | :------------------ | :---- | :----------- | :------------ |
| [i7-8565U](https://ark.intel.com/content/www/us/en/ark/products/149091/intel-core-i7-8565u-processor-8m-cache-up-to-4-60-ghz.html) | Whiskey Lake <br>(based on Coffee Lake) | 4          | 8            | 1.8 GHz        | 4.6 GHz             | 8 MB  | LPDDR3-2133  | Intel UHD 620 |

|                  |                 |
| :--------------- | :-------------- |
| **Ports**        | 2x USB 3.1 Gen 1 (Right USB Always On) |
|                  | 2x USB 3.1 Type-C Gen 2 / Thunderbolt 3 (Power Delivery and DisplayPort) [Max 5120x2880 @60Hz] |
|                  | HDMI 1.4b (Max 4096x2160 @24Hz) |                 |
| **Ethernet**     | via ThinkPad Ethernet Extension Adapter Gen 2: I219-LM Ethernet (vPro) |
| **WLAN + BT**    | Intel Wireless-AC 9560, Wi-Fi 2x2 802.11ac + Bluetooth 5.0 |
| **WWAN(optional)** | - |
| **Display**      | 14.0" (355mm) HDR HD (1920 x 1080) |
| **Camera**       | IR and HD720p camera with ThinkShutte |
| **Audio**        | Realtek ALC3286 codec <br> Linux: ``Realtek ALC285``, layout 11, 21, 31 ; [@acidanthera/AppleALC > Supported codecs [Github]](https://github.com/acidanthera/AppleALC/wiki/Supported-codecs) |
| **Fingerprint reader** | ✔️ |
| **NFC (optional)** | ✔️ |

**Further Specs:**
 - TrackPoint: PS/2
 - TrackPad: PS/2
 - **Thunderbolt:**  Intel JHL6540 (Alpine Ridge 4C) Thunderbolt 3 Bridge (?)

 **NOTE:** The WWAN M.2 slot does **NOT** support SSDs. "If you do manage to fit something in there, you'll be presented with this whitelist error when you try and power the laptop on" [source and photos by @acoutts [Github]](https://github.com/acoutts/x1c7-hackintosh#edit-jan-2-2020)

> ## Read These (References):

- [dortania Hackintosh guides](https://github.com/dortania)
- [The Vanilla Laptop Guide](https://fewtarius.gitbook.io/laptopguide/)
- Daliansky's [Hackintool tutorial](https://translate.google.com/translate?js=n&sl=auto&tl=en&u=https://blog.daliansky.net/Intel-FB-Patcher-tutorial-and-insertion-pose.html).
- [Getting Started with ACPI](https://khronokernel.github.io/Getting-Started-With-ACPI/)
- [WhateverGreen Intel HD Manual](https://github.com/acidanthera/WhateverGreen/blob/master/Manual/FAQ.IntelHD.en.md)

> ## OTHER x1c7-hackintosh REPOSITORIES:

[acoutts / x1c7-hackintosh](https://github.com/acoutts/x1c7-hackintosh) who brought me on this project.  
[jaehxx0925 / X1C7-Hackintosh](https://github.com/jaehxx0925/X1C7-Hackintosh) Working Clover for Catalina

**x1c6-hackintosh** <br>
[zhtengw/EFI-for-X1C6-hackintosh](https://github.com/zhtengw/EFI-for-X1C6-hackintosh)  
[Colton-Ko/macOS-ThinkPad-X1C6](https://github.com/Colton-Ko/macOS-ThinkPad-X1C6)  
Create a pull request if you like to be added, final decision at my discreation.

> ## CONTACT:

https://tylerspaper.com/contact  
Signal: (202)-644-9951 \*This is a Signal ONLY number. You will not get a reply of you text me at this number.

> ## DONATE AND SUPPORT:

[https://tylerspaper.com/support](https://tylerspaper.com/support/)

> ## Credits and Thank You:

### Tyler Nguyen [@tylernguyen](https://github.com/tylernguyen)


[@Colton-Ko](https://github.com/Colton-Ko/macOS-ThinkPad-X1C6) for the great features template.  
[@stevezhengshiqi](https://github.com/stevezhengshiqi) for the one-key-cpufriend script.  
[@corpnewt](https://github.com/corpnewt) for CPUFriendFriend.  
[@Sniki](https://github.com/Sniki) and [@goodwin](https://github.com/goodwin) for ALCPlugFix.  
[@xzhih](https://github.com/xzhih) for one-key-hidpi.  
[@daliansky](https://github.com/daliansky) for all the hotpatches.  
[@velaar](https://github.com/velaar) for your continual support and contributions.

The greatest thank you and appreciation to [@Acidanthera](https://github.com/acidanthera), without whom's work, none of this would be possible.

And to everyone else who supports and uses my project.

Please let me know if I missed you.
