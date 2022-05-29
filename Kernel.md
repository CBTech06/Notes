# ---- [ KERNEL ] ---- 
                                        
                                        
     < [index>.md]
 
## TOOLS 
	lspci											pkg: pciutils
	lsmod
	lsusb
	
## BUILD KERNEL OPTION
			### MAKE HELP
						make help
			### GET CURRENT CONFIG WITH MODULES
						make localmodconfig
			### MAKE DEFAULT CONFIGURATION
						make defconfig
			### CONFIG WITHOUT MENU
						make config
			### CONFIG WITH SIMPLE MENU
						make nconfig
			### CONFIG WITH MENU
						make menuconfig
			### BUILD MODULES
						make modules
			### INSTALL MODULES
						make modules_install
			### CLEAN AND REMOVE .config
						make mrproper

# ZALMANN Z11

# SAMSUNG NC10
  Bridge: 		Intel 945GS
  SATA Controller: 	82801GBM/GHM
  PCI Bridge: 		Intel NM10/ICH7
  Audio: 		Intel NM10/ICH7  
  Network: 		
  			Qualcomm Atherox AR242x (WIFI)
  			  → Atheros 5424/2424

			Marvel 88E8040 PCI-E
			  * FreeBSD → device msk
  			  	→ Marvell Yukon 88E040
			  	→ Marvell 88E3016 10/100 (PHY)

  Graphic:		Intel 945GSE
  USB: 			NM10/ICH7 UHCI Controller 
  SMBUS: 		Intel NM10/ICH7

  Modules:

# SAMSUNG AIO 

## TIPS
* Show all modules installed 
	lsmod
* Show Listed sound modules 
	grep SND_HDA .config

* List soundcards
	cat /proc/asound/cards
	aplay -l

## INFOS: 
	CAN (Control Area Network) :  Serial Communication protocol used in Automotive and Marine
	RXRPC: These are used for AFC Kernel  filesystem and userspace utilities 
	INFINBAND: is a computer networking communication used in high-performance computing

* USERSPACE / KERNELSPACE
	The user space is a set of locations where normal user processes run(Everything
	other than the kernel). The role of the kernel is to manage applications running in this space.

	The Kernel space is location where the code of the kernel is stored, and excutes under

	Processes running under the user space have acces only to a limited part of memory, whereas
	the kernel has acces to all of the memory.

