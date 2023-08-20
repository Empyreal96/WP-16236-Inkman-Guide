# WP-16236-Inkman-Guide
Guide on installing an early leaked WCOS build on a production Lumia 950

- Download these msv*.dll files
- download these OSData files
- copy qc*.mbn files from 15254 on a 950
- Flash FFU (optional but recommended)
- Unlock Bootloader
- Enter Mass Storage Mode
- Enable Developer Menu (add link with permission)
- replace mobilestartup.efi and bootarm.efi
- Format MainOS, Data
- use DISM to apply MainOS.wim and Data.wim to respective partitions
- shrink Data by 512MB, create a partition OSData
- link up DPP, EFIESP, OSData and Data to MainOS folders
- take ownership of all qc*.mbn files in Windows\System32, rename to qc*.mbn.bak (or delete)
- insert the .mbn files from 15254
- copy msv*.dll files to System32, don't replace any
- extract the OSData files to the OSData partitions
- enable test signing and flight signing on efiesp bcd
- boot and hope for the best
