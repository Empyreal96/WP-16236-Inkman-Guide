# WP-16236-Inkman-Guide
Guide on installing an early leaked WCOS build on a production Lumia 950

- download these OSData files
- Flash FFU (optional but recommended)
- Unlock Bootloader
- Enter Mass Storage Mode
- Enable Developer Menu (add link with permission)
- replace mobilestartup.efi and bootarm.efi
- Format MainOS, Data
- use DISM to apply MainOS.wim and Data.wim to respective partitions
- shrink Data by 512MB, create a partition OSData
- link up DPP, EFIESP, OSData and Data to MainOS folders
- extract the OSData files to the OSData partitions
- enable test signing and flight signing on efiesp bcd
- boot and hope for the best
