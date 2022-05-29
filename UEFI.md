# ---- [ Unified Extensible Firmware Interface] ----

## REF:

	http://Rodbooks.com

	- [X] Managing EFI BootLoaders for linux - Basic Principle
	- [X] Managing EFI BootLoaders for Linux - EFI Boot Loader Installation
	- [ ] Dealing with Secure Boot
	- [ ] Controling Secure Boot
	- [X] Using a fallback Filename

## TOOLS
	efibootmgr

## EFIBOOTMGR
  * Add new boot option usgin EFIBOOTMGR
	If you want to add a boot option for `boot/efi/EFI/refind/refind_x64.efi`
	where /boot/efi is the mount mount point of the ESP
		
	`findmnt /boot/efi`

	TARGET 			SOURCE 			FSTYPE			OPTIONS
	/boot/efi		/dev/sda1		vfat				rw,flush,tz=UTC

	efibootmgr --create --disk /dev/sda --part 1 --loader /EFI/refind/refind_x64.efi 
						--label"rEFIn BootMGR"

  * Remove entry from EFI
	- Remove entry number: 0000
        	efibootmgr -b 0000 -B
			
## KERNEL CONFIG FOR UEFI
	CONFIG_RELOCATABLE=y
	CONFIG_EFI=y
	CONFIG_EFI_STUB=y
	CONFIG_FB_EFI=y
	CONFIG_FRAMEBUFFER_CONSOLE=y
	CONFIG_EFIVAR_FS=y					* Kernel 3.10

* check for existence of /sys/firmware/efi/efivars/dump-* files. 
	if they exists remove them.

## INSTALLATION
* For EFI, Add /etc/fstab entry
	/dev/sda1	/boot/efi		vfat		defaults		0		1
or		UUID=####-####

* REGISTERING BOOT LOADER WITH EFI
		`efibootmgr -c -d /dev/sda -p 1 -l \\EFI\\newloader\\loadername.efi -L NewLoader`
	This example adds /boot/efi/EFI/newloader/loadername.efi on /dev/sda1 to the EFI's
	internal menu of boot options.

* Options: -d specify the disc device -p 1 partition number loadername → bootx64.efi
	
# TROUBLESHOOTING
	EFI var are not supported on this system
		modprobe -t efivars
	If the modules doesn't exist , you have to build kernel to enable feature.
	
# ---- [ INFORMATIONS ] ----
	UEFI = EFI version 2.x 					EFI = EFI 1.X

## DIFFERENCE BETWEEN UEFI AND LEGACY MODE
   Firmware is piece of software that acts as an interface between 
   the hardware and the operating system.`LEGACY MODE` reffers to
   BIOS Firmware. BIOS us unable to provide advance features of moden hardware.

   `Unified Extensible firmware`
      Is the successor to BIOS. UEFI uses the GUID Partition Table(GPT)
      whereas `BIOS` uses the Master Boot Record(MBR)

   * Difference between GPT and MBR:
       Max partition size in `MBR`: ~2 TB UEFI:~9 ZetaBytes
       `MBR`: can have max 4 Primary partition `GPT`: can have 128

       `MBR` can store only one bootloader whereas `GPT` has a 
       separate dedicated `EFI System` for storing multiple bootloaders.

       `UEFI` offers secure boot which can prevent boot-time viruses for
       loading.

## GUID Partition Table(GPT) (BOOT DISK)
	* Create GPT under Linux
			1. Use libparted-based tool such as parted or GParted
				 in parted, you can do this by typing mklabel gpt.
				 in Gparted, Select Device → Create Partition Table 
						expand the Advance item, select gpt as the partition table type
						click apply to create a new partition table.
			2. Use GPT fdisk(gdisk,cgdisk,sgdisk), These tools can convert an existing
				 MBR disk to GPT format.
			3. Use a recent version of fdisk,cfdisk,sfdisk.The version in util-linux 2.27 
				 doest the job, but no util-linux2.20

## EFI SYSTEM PARTITION(ESP) 
	Create an ESP at least 550Mib in size.
	Should only FAT32 Filesystem 
	Fdisk type code for ESP is EF00. You should not set the "boot flag" on any OS
	partition under GPT, just on the ESP.

* Location EFI 	
	Ubuntu place its EFI boot loader files in EFI/ubuntu,
	Once linux is installed the ESP is typically mounted at /boo/efi
	so for ubuntu: /boot/efi/EFI/ubuntu

		bootx64.efi		Default bootloader file
		bootia32.efi	IA-32(X86)
		bootaa64.efi	ARM computers

* Install bootloader independently
	EFI/refind for rEFInd

* EFI Boot Process
		List of boot options are in NVRAM.

* CSM(Compatibility Support Module (BIOS Compatibility)
	
GRUB is Boot loader and BOOT manager.
ELILO/SYSLINUX/EFI Stub load is only boot loader.

## BIOS [BASIC INPUT /OUTPUT SYSTEM]
	It was written using 16-bit Code.Boot process load only 512 bytes of data
	the contents of the first sector if th boot disk and executing it.
	

# FALLBACK IMAGE
	bootx64.efi is the fallback filename


  • You're preparing a bootable removable disk, such as a USB flash drive or CD-R, 
		especially if it's supposed to be used on multiple computers. This is the case 
		for which the fallback filename was designed, after all.
	• You're forced to install the boot loader in BIOS/CSM/legacy mode. In this case, using the fallback
    filename should make the computer bootable once you switch to EFI-mode booting, provided no other
    boot entries take precedence. (Even in that case, you may find a boot manager entry to boot using the
    fallback filename, but it likely won't be the default entry.)
  • You must install the boot loader on one computer, then transfer the disk to another one. In this
    case, the disk should be bootable, just as a USB flash drive would be, provided there are no other
    boot loaders on the disk that were bootable on the target system prior to the disk being juggled.
  • You want to install an emergency backup boot loader in addition to the regular boot loader. This can
    be a prudent step to take, but it's best considered a backup to the regular boot loader
    distributions will try to manage their boot loaders using the standard locations, so you might miss
    out on important security updates if you try to boot on a regular basis using the fallback filename.
  • Your computer has a badly buggy EFI that "forgets" its boot entries or boot order or that fails to
    honor its boot order. In this case, obtaining a fixed EFI is the ideal solution; but few such fixes
    actually exist, so you may be stuck with using the fallback boot loader until you replace the
    computer.

Broadly speaking, there are two alternative names that are most useful:

  • EFI/BOOT/bootarch.efi—This name is the official EFI fallback filename. It's most commonly used on
    bootable removable disks, but it can be used on hard disks. It's typically used only if no NVRAM
    entry points to a valid boot loader. Note that arch is an architecture code, such as x64 for x86-64/
    AMD64 or ia32 for x86/IA32. Thus, the most common fallback filename is bootx64.efi
  • EFI/Microsoft/Boot/bootmgfw.efi—This filename has no official special standing in the EFI
    specification, but as a practical matter, many EFI implementations use it as a fallback boot loader
	
