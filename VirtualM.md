# ---- [ VIRTUAL MACHINE ] ----

## DOCKER
  * INSTALL DOCKER ON KALI LINUX 
    apt install -y docker.io
    systemctl enable docker --now
    usermod -aG docker $USER
    docker

### DOCKER COMMANDS
    docker  info			Informations about docker
    docker stop ubuntu			Stop Ubuntu container
    docker rm ubuntu			Remove Ubuntu

 * GET SPECIFIC DISTRIBUTION (https://hub.docker.com/search?q=linux)
    docker pull ubuntu			Get Ubuntu
    docker run -it ubuntu 		Run ubuntu container 
    docker ps -a			List all containers

 * BUILD IMAGE(Dockerfile)
   docker build -t <name> .

## INSTALLATION
* KALI LINUX 
	apt install qemu-kvm libvirt-clients libvirt-daemon-system bridge-utils

* ALPINE LINUX
	apk add qemu-system-x86_64
	apk add qemu-ui-gtk
	apk add qemu-ui-spice-core
	apk add qemu-hw-usb-host
	apk add qemu-hw-display-qxl

* ADD USER TO GROUP
	adduser <username> libvirt
	adduser <username> kvm

## QEMU
* CREATE NEW IMAGE SIZE 4G:
			qemu-img create -f raw <img_file> <size>

* RESIZE IMAGE
			qemu-img resize <disk_image> +10G
* INFO IMAGE	
			qemu-img info void_linux-*.iso

* RUN MACHINE
			qemu-system-x86_64 <img_file>

* INSTALLING OPERATING SYSTEM
	qemu-system-x86_64 -enable-kvm -nographic -m 2G -cdrom <iso_image> -boot order=d 
		           -drive file=<img_file>,format=raw
	
* EXIT NOGRAPHIC MODE
	ctrl+a then c
	retypr to return in virtual machine

## KEYBINDINGS
	Ctrl+Alt+m									Enable/Disable Menubar
	Alt+Shift+LeftClick					Full machine keyboard
	CTRL+ALT+G									Out of machine
	CTRL+ALT+F									FullScreen

## USB
	qemu -usb -device qemu-xhci

## GRAPHICS CARD
	1. INSTALL qemu-hw-display-qxl

## KVM(Kernel-base Virtual Machine)
	Qemu use CPU extension(HVM) instead KVM
	
 * HARDWARE SUPPORT
	1) Enable Virtualization in BIOS
	2) LC_ALL=C lscpu | grep Virtualization
	 or grep -E --color=auto 'vmx/svm/0xC0F' /proc/cpuinfo

 * KERNEL SUPPORT
		grep CONFIG_KVM /boot/config<version>

		lsmod | grep kvm
			kvm_intel		u_type1
			kvmgt				kvm
			mdev				irqbypass (/lib/modules/<kernel>/virt/lib)
			vfio
		
* TO CHECK IF KVM IS OKAY
	kvm-ok


## MONITOR(COMMAND)
* ADD USB TO GUEST OS
	device_add usb-ehci,id=ehci

* SHOW INFO ABOUT VM
	info usb 
	info network
	info kvm ...
## CONFIG OPTIONS
* KERNEL vhost-net Kernel 5.7 and later
		`Device Drivers  --->
			[*] VHOST drivers  --->
			<*>   Host kernel accelerator for virtio net`

* KERNEL	Optional advanced networking support
			`Device Drivers  --->
			  [*] Network device support  --->
	      		  [*]   Network core driver support
			  <*>   Universal TUN/TAP device driver support`

* KERNEL Enabling 802.1d Ethernet Bridging support
			`[*] Networking support  --->
        			Networking options  --->
			           <*> The IPv6 protocol
				   <*> 802.1d Ethernet Bridging`

## TROUBLESHOOTING
	Cannot setup guest memory 'pc.ram'
		This is due to -m<x>G option.reduce xG





