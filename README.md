# Guide to install the "Inkman" build on a Lumia 950

*Please note, this build is not a replacement for W10M, it's **very** barebones and only contains the Reference Composer and Diagnostic Composer. I have been unsuccessful in installing third party apps to this build*

*This requires manually modifying partitions on your device, if you are not comfortable with Windows Disk Manager and managing partitions leave now. **I will not be responsible if you brick your phone!** *

- Download the [EFIESP.zip](https://github.com/Empyreal96/WP-16236-Inkman-Guide/releases/download/0.1/EFIESP.zip) and [OSData.zip](https://github.com/Empyreal96/WP-16236-Inkman-Guide/releases/download/0.1/OSData.zip) packages for later
- Flash FFU (optional as all data will be wiped anyway)
- Unlock Bootloader
- Enter Mass Storage Mode with WPInternals
- Install [Developer Menu](https://github.com/Empyreal96/WP-16236-Inkman-Guide/releases/download/0.1/Developer_Menu_Installer_V2.zip) (Credit for this script goes to [Fadil Fadz](https://github.com/fadilfadz01) )
- Replace `mobilestartup.efi` and `bootarm.efi` from the [EFIESP.zip](https://github.com/Empyreal96/WP-16236-Inkman-Guide/releases/download/0.1/EFIESP.zip) archive, and copy any other files to the respective folders (I recommend renaming the originals with the .bak extention instead of physically replacing)
- Format ONLY `MainOS` and `Data` Partitions as NTFS.
- Use `DISM` to apply MainOS.wim and Data.wim to respective partitions
```
// D:\ is my example for the MainOS Drive, Highly suggested to save the .wim files somewhere easy like `C:\Inkman` //

dism /Apply-Image /ImageFile:C:\Inkman\MainOS.wim /Index:1 /ApplyDir:D:\

// E:\ is my example for the Data drive //

dism /Apply-Image /ImageFile:C:\Inkman\Data.wim /Index:1 /ApplyDir:E:\
```
- Using Disk Management, shrink `Data` partition by 512MB, create a partition `OSData`
- Using Disk Management, Mount `DPP`, `EFIESP`, `OSData` and `Data` to the empty MainOS folders with the same names. (*Note DPP is the small 8MB FAT partition*)
- Extract the OSData files to the newly mounted OSData folder
- Enable test signing and flight signing on efiesp bcd:
```
// I'm still using D:\ as MainOS in this example //

bcdedit /store "D:\EFIESP\EFI\Microsoft\Boot\BCD" /set {default} testsigning on
bcdedit /store "D:\EFIESP\EFI\Microsoft\Boot\BCD" /set {default} flightsigning on

```
- Boot and hope for the best
