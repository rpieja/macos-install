# MacOS High Sierra AMD Ryzen Install Guide

Based on XLNC macOS images and instructions from AMD-OSX forum.

Disclaimer:
This is only an installation log for mine future use, feel free to use it, but I won't provide any support. This works for me, but that doesn't guarantee it will work for you even if you have exactly the same setup.

Hardware Setup:
* CPU: AMD Ryzen 7 1700
* MOBO: Gigabyte X370 Gaming 5
* GPU: Gigabyte Radeon RX460 4GB
* RAM: G.Skill Trident z RGB 16GB 2400 MHz


#### Installation
1. Image: AMDHS_Installer v2 clover edition 
2. Restore image to at least 8GB usb stick with TransMac
3. BIOS Settngs (skip the ones that you dont have):
```
HPET                        = Enabled
Sata Mode                   = AHCI
IOMMU                       = Disabled
APU / Integrated Graphics   = Disabled 
GPU / Graphics Priority     = PEG/PCI
Serial Port                 = Disabled
Parallel Port               = Disabled
Legacy USB Support          = Enabled
AS Media 3.1/3.0 controller = Enabled 
EHCI Handoff                = Enabled
XHCI Handoff                = Enabled
SECURE BOOT                 = Disabled / Other OS
CSM Support                 = Disabled
```
4. Plug usb stick to USB 3.0 (3.1 gen 1) port and boot in UEFI mode
5. Boot into installer
6. Disk utility: format drive with GUID scheme and MacOS Extended Journaled fs
7. Exit diskutil and install OS to previously formatted drive

#### Post-installation
8. After reboot boot once again into installer
9. Open terminal and run `xlnc` command
10. Select `1.Bronya`
11. Then select `2.Post Install`
12. Enter name of macos disk name (disk name entered in diskutil)
13. Answer `Y` to all questions asked
14. Reboot
15. Boot again into USB but now choose to boot from your partition, not the installer

#### Clover installation

16. Download Clover bootloader (I've used version v2.4k_r4497)
17. Install on boot drive with settings:
```
- Install for UEFI booting only
- Install Clover in the ESP
- Install Clover Preference Panel
- OsxAptioFixDrv-64
- PartitionDxe-64
- UsbKbDxe-64
```
18. Copy config.plist to `EFI/CLOVER/` (Replace file)
19. Copy contents of kexts folder into `EFI/CLOVER/kexts/Other/`
20. Remove USB
21. Reboot

Known bugs:
HDMI output image is distorted, looks like compressed JPEG.