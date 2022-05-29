# ---- [ NETWORK ] ---- 

## CONFIGURE TWO COMPUTERS UNDER UNIX SYSTEM
	ip addr flush dev eth0
	ifconfig eth0 192.168.1.11 netmask 255.255.255.0 broadcast 192.168.1.255

* EDIT /etc/hosts
	add IPs of known host

## PERMANENT CONFIGURATION FOR INTERFACE
* DEBIAN / KALI / ...
	Edit /etc/network/interfaces
		allow-hotplug ethO
		iface eth0 inet static 
			address 192.168.2.10 
			netmask 255.255.255.0 
			broadcast 192.168.2.255
			gateway <IP_GATEWAY>


## SHOW INFORMATION  
* GET HELP
  qemu-system-x86_64 -device help | grep '[e|x]hci'

* SHOW IPV4 
   ip -4 addr

* SHOW IPV6
   ip -6 addr

* SHOW INFO ABOUT INTERFACES AND ROUTES
   ip link show
   ip route show
   ethtool -P wlp2s0

* SCAN ACCESSPOINT
     iw dev wlp2s0 scan
     iwlist wlp2s0 scan

## SET STATE & MODE 
     ip link set wlp2s0 [mode](mode) default
     ip link set wlp2s0 

## WPA_SUPPLICANT 
   -d Debug 

  ### WPA PASSPHRASE
    wpa_passphrase <SSID> <PASSPHRASE>  

  ### TERMINATE WPA
    wpa_cli -i wlp2s0 terminate

  ### LIST NETWORKS
    wpa_cli list_networks

  ### DELETE PROFILE
     wpa_cli remove_network <id>

## IW
* LIST WIFI INTERFACE
        iw dev

* LIST ALL SSID
        su -c "iw wlan0 scan " | grep ssid

* INFO ABOUT CONNECTED SSID
        iw wlan0 link

## USING DHCPCD

   ip link set dev wlp2s0 up
    wpa_supplicant -B -i wlp2s0 -c /etc/wpa_supplicant/wpa_supplicant.conf
    dhcpcd wlp2s0

## STATIC CONFIGURATION 

  ip addr add 192.168.0.10/24 broadcast 192.168.0.255 dev <interface>
      :/24: CIDR notation of 255.255.255.0(SUBMASK)

* EDIT /etc/resolv.conf TO ADD DNS 
     nameserver 194.158.122.10
     nameserver 194.158.122.15
     nameserver 192.168.1.254        Access the BBOX interface

     ip route add default via 192.168.1.254 dev <interface>

## UNDO & CLEAR CONNECTION
  ip addr flush dev enp4s0
  ip route flush dev enp4s0

* AND FINALLY DISABLE THE INTERFACE
       ip link set enp4s0 down

## CLOSING CONNECTION
   ip link set dev wlp2s0 down

WARNING Before disabling the interface, flush IP address and gateway:
   ip addr flush dev wlp2s0

## BRIDGE(TUN)
  modprobe tun

## CIDR NOTATION(Classless Inter-domain Routing)
    is a method for allocating IP adress and for IP routing

        www.shellhacks.com/cidr-notation-explained-examples/

