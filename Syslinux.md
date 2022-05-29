# ---- [ SYSLINUX ] ---- #
                                        
                                        
                [<GO Back](index)
 
 
## INFORMATIONS 
				
				syslinux is used for FAT
				extlinux is used for EXT

				:CONFIGUREATION_FILES: extlinux.conf
				
## CREATE BOOTABLE MEDIA WITH EXTLINUX

			### INSTALL ON A PARITION MOUNTED IN MNT 
		              extlinux --install /mnt
									
		 
## CREATE BOOTABLE MEDIA WITH SYSLINUX

				syslinux install /dev/<device>
## UEFI 
   For UEFI systems, the bootloader file is called syslinux.efi
		
		efi32/syslinux.efi
		efi64/efi/syslinux.efi
	
  EFI_SYSTEM_PARTITION/EFI/BOOT/BOOTX64.EFI
		
