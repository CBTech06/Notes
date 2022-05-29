# ---- [ LINUX PARTITIONNING ] ----


# Primary / extended Partition
	Disc drive can contains 4 primary partition or 3 primary and 1 extended partition
	Only a single partition can be contained in a HD.Extended partition acts as a container
	for logical partition.

	Primary partition is a bootable partition and can contain OS.Extended partition is partition
	that is not bootable 

# PARTED
	<usage> parted /dev/sdax

* COMMAND
	help <cmd>				Show command help
	print					Show partition information
		free				Show free space information
	rm <PARTITION NB>			Delete partition
	mkpart fat32 primary 1049kB 550MB	Create Partition with 550mB
	set 1 boot on				Set Bootflag on for partition 1
	toggle 1 esp				Add esp flag to partition 1

* Create GPT Table	
	mklabel gpt 

* Creation EFI Partition Table
	mkpart primary fat32 1Mib 400MiB
	set 1 esp on	

* Creation of linux-swap
	1. mkpart / 2. primary / 3. linux-swap / 4.start: 419MiB /5. end: 1419MiB

# Partition Table Samsung AllInONE
	Number		start		end		size		type		fs	flag
	1		1049kb		419MB		418MB		Primary		fat32	esp	
	2		439MB		1488MB		1049MB		Primary		swap	
	3		1488MB		307GB		306GB		Primary		ext4	
	4		307GB		500GB		193GB		Primary		ext4	

# Swap File
	mkswap /dev/sdax	Format SWAP
	swapon /dev/sdax	Mount SWAP FS
	swapoff /dev/sdax	Unmount SWAP

# Mounting
  * MOUNT / and /HOME
	mount /dev/sda3 /mnt
	mount /dev/sda4 /mnt/home

  * MOUNT ESP ON /boot/efi
	mount /dev/sda1 /mnt/boot/efi/

