# RG36 “Open Source” Handheld – Technical Analysis

## Summary
This repository documents an investigation into a handheld console
marketed as an “open source” device. The goal was to determine whether
custom firmware or third-party Android apps (RetroArch, YouTube) could
be installed.

Conclusion: the device is cryptographically locked and cannot be
modified by the end user.

## Device Information
- Product: HEXING6592_WET_L
- SoC: MediaTek MT6592
- Bootloader: MediaTek LK
- Android: 32-bit, appliance build

## Initial Claims
- “Open source console”
- Dual SD card slots
- Android-based

## Investigation Steps
- Explored stock UI and hidden menus
- Tested ADB in normal boot
- Tested recovery ADB sideload
- Installed Google USB driver
- Entered fastboot mode
- Queried bootloader variables

## Bootloader Output
(bootloader)    max-download-size: 0x8000000
(bootloader)    partition-size:bmtpool: 1500000
(bootloader)    partition-type:bmtpool: raw data
(bootloader)    partition-size:userdata: 32000000
(bootloader)    partition-type:userdata: ext4
(bootloader)    partition-size:cache: 1a800000
(bootloader)    partition-type:cache: ext4
(bootloader)    partition-size:system: 60000000
(bootloader)    partition-type:system: ext4
(bootloader)    partition-size:expdb: e60000
(bootloader)    partition-type:expdb: raw data
(bootloader)    partition-size:frp: 100000
(bootloader)    partition-type:frp: raw data
(bootloader)    partition-size:ebr2: 80000
(bootloader)    partition-type:ebr2: raw data
(bootloader)    partition-size:logo: 800000
(bootloader)    partition-type:logo: raw data
(bootloader)    partition-size:misc: 80000
(bootloader)    partition-type:misc: raw data
(bootloader)    partition-size:sec_ro: 600000
(bootloader)    partition-type:sec_ro: ext4
(bootloader)    partition-size:recovery: a00000
(bootloader)    partition-type:recovery: raw data
(bootloader)    partition-size:boot: a00000
(bootloader)    partition-type:boot: raw data
(bootloader)    partition-size:uboot: 60000
(bootloader)    partition-type:uboot: raw data
(bootloader)    partition-size:seccfg: 40000
(bootloader)    partition-type:seccfg: raw data
(bootloader)    partition-size:protect_s: a00000
(bootloader)    partition-type:protect_s: ext4
(bootloader)    partition-size:protect_f: a00000
(bootloader)    partition-type:protect_f: ext4
(bootloader)    partition-size:nvram: 500000
(bootloader)    partition-type:nvram: raw data
(bootloader)    partition-size:pro_info: 300000
(bootloader)    partition-type:pro_info: raw data
(bootloader)    partition-size:ebr1: 80000
(bootloader)    partition-type:ebr1: raw data
(bootloader)    partition-size:mbr: 80000
(bootloader)    partition-type:mbr: raw data
(bootloader)    partition-size:preloader: 40000
(bootloader)    partition-type:preloader: raw data
(bootloader)    off-mode-charge: 1
(bootloader)    warranty: yes
(bootloader)    unlocked: no
(bootloader)    secure: yes
(bootloader)    kernel: lk
(bootloader)    product: HEXING6592_WET_L
(bootloader)    version: 0.5
all: Done!!
Finished. Total time: 0.039s

## Security Findings
- Bootloader locked
- Secure boot enabled
- Signed images enforced
- No OEM unlock path
- No ADB install vectors

## Why Custom OS / Apps Are Impossible
- Private signing key not present on device
- Verified boot enforced by LK
- No exploit paths available
- No SD boot support

## Conclusion
Despite marketing claims, this device is a sealed Android appliance.
Modification without OEM keys or hardware exploits is not possible.

## Lessons Learned
- “Open source” ≠ user-modifiable
- SD slots do not imply SD boot
- MediaTek LK + secure boot is a hard stop
