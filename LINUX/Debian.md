# ---- [ DEBIAN / DEBIAN BASED DISTRO ] ----

## KALI LINUX ROOT PASSWORD
	1. sudo su
		Enter USER password(not admin password)
	2. passwd root
		Enter ROOT password  

## APT PACKAGE MANAGER
	apt update 			Update Package 
	apt list --upgradable		View pkg list need to be upgradable
	apt upgrade			Upgrade all package

 * DOWNGRADE PKG

# ANTIX
## INSTALLATION CORE
	login / pass : root
	loadkeys fr 
	cli-installer 
	
	partion HD 
		SWAP Ram (20% of RAM)
		primary partition ext4
## ANTIX MIRROR LIST
 	/etc/apt/sources.list.d/antix.list

* SET FR KEYBOARD (TTY)
 	* EDIT /etc/default/console-setup
		FONTFACE="TerminusBold"
		FONTSIZE="20x10"
		KEYMAP="fr"
	
	* EDIT /etc/default/keyboard
		XKBMODEL="pc105"
		XKBLAYOUT="fr"
		XKBVARIANT=""

* INXI	
	* LIST ALL REPOSITORY
		pt inxi -r


## NETWORKING
* LIST INTERFACES
		ls /sys/class/net

* EDIT /etc/network/interface
		auto eth0
		iface eth0 inet static 
			adress 192.168.1.63/24
			gateway 192.168.1.254

## DPKG-RECONFIGURE
	Config files are located /var/lib/dpkg/info

## SERVICE
	service networking <start/stop/restart/reload>

## WAYLAND INSTALLATION
	libpam-elogind
	libinput-bin
	libinput-dev
	libseat1 seatd
