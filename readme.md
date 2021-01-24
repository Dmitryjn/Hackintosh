# Hackintosh on Asrock H370 pro4 via [OpenCore][OC]

![About this mac][System Info]

*macOS Supported:* **10.14+**

This is light configuration to run macOS smoothly. I didn't get any [kernel panics][uptime] science after macOS install. This config is base on [OpenCore Vanilla Desktop Guide][Guide].

## Hardware configuration

* Intel Core i5 8400  UHD630 (Geekbench 5: [CPU][GB_CPU]/[OpenCL][GB_OCL]/[Metal][GB_MTL])
* Asrock H370 pro4
* 2×8GB Adata XPG 2666MHz
* M.2 NVME ADATA SX6000NP 120GB
* ST2000DM001-1ER164 (FusioDrive)
* Atheros 9380 WIFI
* Bluetooth Roketek 4.1

## Before you start make sure you have

* Working hardware
* Actual [OpenCore][OC] `= 0.6.4`
* Populated `PlatformInfo > Generic` section in `config.plist`, can be easyly done with `macserial` tool from [OpenCore][OC] utilities.

# Installation

## BIOS Settings

* *Exit* → Load Optimized Defaults [Yes]
* *Advanced* → System Agent (SA) Configuration → VT-d [**Disable**]
* *Advanced* → System Agent (SA) Configuration → Primary Display [**IGPU**]
* *Advanced* → System Agent (SA) Configuration → DVMT Pre-Allocated [**64M**]
* *Advanced* → USB Configuration → Legacy USB Support [**Disabled**]
* *Advanced* → CPU Configuration → Intel Virtualization Technology [**Enabled**]
* *Boot* → Fast Boot [**Disabled**]
* *Boot* → CSM (Compatibility Support Module) → Launch CSM [**Disabled**]

## What's behind the scenes

You must download all not bundled kexts and drivers from repositories by yourself.

### Kexts

* [IntelMausi.kext][IntelMausi] - Another intel driver for Ethernet
* [AppleALC.kext][AppleALC] - Getting audio to work as easy-peasy
* [Lilu.kext][Lilu] - Dependency of `VirtualSMC.kext` and `WhateverGreen.kext`
* [VirtualSMC.kext][VirtualSMC] - A advanced replacement of FakeSMC, almost like native mac SMC.
* [WhateverGreen.kext][WG] - Need for GPU support (even for disabling discrete GPU)
* [IO80211HighSierra][WI] Needed for Wi-Fi support on Catalina.
* [USBInjectALL][USB] USB Support
* [OS-X-USB-Inject-All][USBS] Needed for USB Support on Asrock board.


### EFI drivers

* ~VirtualSMC.efi~ - only needed if you use File Vault 2 or [authrestart][FV2].

## Issues


## USB ports mapping


## Chnagelog
###### 01/23/2021
* The initial push to GitHub

[AppleALC]: https://github.com/acidanthera/AppleALC
[FV2]: https://lifehacker.com/bypass-a-filevault-password-at-startup-by-rebooting-fro-1686770324
[GB_CPU]: https://browser.geekbench.com/v5/cpu/6076431
[GB_MTL]: https://browser.geekbench.com/v5/compute/2289808
[GB_OCL]: https://browser.geekbench.com/v5/compute/2289810
[Guide]: https://dortania.github.io/OpenCore-Install-Guide/
[IntelMausi]: https://github.com/acidanthera/IntelMausi
[Lilu]: https://github.com/acidanthera/Lilu
[OC]: https://github.com/acidanthera/OpenCorePkg
[System Info]: https://eljnavas.files.wordpress.com/2021/01/info.png
[uptime]: https://eljnavas.files.wordpress.com/2021/01/uptime.png
[VirtualSMC]: https://github.com/acidanthera/VirtualSMC
[WG]: https://github.com/acidanthera/WhateverGreen
[WI]: https://github.com/khronokernel/IO80211-Patches/blob/main/10.13.6-High-Sierra-Kexts/IO80211HighSierra.kext.zip
[USB]: https://bitbucket.org/RehabMan/os-x-usb-inject-all/downloads/
[USBS]: https://github.com/RehabMan/OS-X-USB-Inject-All
