# ---- [ FREEBSD ] ----

    <[index.md]

## PKG
* SEARCH PKG
      pkg search suversion 

* LIST INSTALLED PKG
      pkg info 

* QUERY THE LOCAL VERSION
      whereis lsof

* UPDATE PKG
      pkg update -f 
      pkg upgrade
* UPDATE SYSTEM
      freebsd-update fetch
      freebsd-update install

## KEYBOARD
  * CHANGE KEYBOARD → kbdmap 

## SERVICES
  * All services are located to /etc/rc.d

  * START SERVICE 
      service ipfw start
  or  service ipfw onestart
  or  `firewall_enable="YES"` in /etc/rc.conf
       sysrc pf_enable="YES"
  * STOP SERVICE
      service pf stop

## NETWORK CARD(FREEBSD p.222)
1. EDIT /etc/rc.conf
	    `ifconfig_msk0="inet 192.168.1.11 netmask 255.255.255.0"`
2. EDIT /etc/hosts to add the names and IP adresses of the host

3. RESTART  NETWORK SERVICE
	`service netif restart`

## NETWORK 
* SET INTERFACE UP/DOWN
      ifconfig wlan0 up/down

* SHOW IP AND MAC ADRESS
       arp -an

## CREATE BRIDGE
	ifconfig bridge create
 	ifconfig bridge0 addm wlan0 addm msk0 up						Bridge over ethernet
	ifconfig bridge0 inet 192.168.1.0/24

### SETTING WIFI WITH ROUTE
	wpa_supplicant -B -i wlan0 -c /etc/wpa_supplicant.conf
	ifconfig wlan0 inet 192.168.1.49/24
	route change default -iface wlan0
	route change default 192.168.1.254
	route del 192.168.1.0/24
	route add 192.168.1.0/24 -interface wlan0

### WIRELESS

* RESTART NETWORK SERVICE
	service netif restart

* SCAN NETWORK
	ifconfig wlan0 up scan

* LIST KNOWN NETWORKS
	ifconfig wlan0 list scan

### ROUTE	
* See ROUTAGE table  
   netstat -rn

* ADD ROUTAGE  
      route add default 192.168.1.254

* CHANGE INTERFACE
      route change default -iface wlan0
      route change default 192.168.1.1

* DELETE ROUTE
      `route delete default`

* ADD DEFAULT ROUTER TO /etc/rc.conf
      defaultrouter="192.168.1.254" 

* FREEBSD AS DEFAULT GATEWAY
      1. Edit /etc/rc.conf to enable GW and NAT
            `gateway_enable="YES"`
       or unable routing with:
            `sysctl -w net.inet.ip.forwarding=1`
            `natd_enable="YES"`
            `natd_interface="wlan0"`
            `natd_flags=`

      2. Enable FIREWALL AND SET RULES
            see FIREWALL section below

      - STOP ROUTING
            `systcl -w net.inet.ip.forwarding=1`

* RESTART SERVICE
      `service routing restart`

## FIREWALL
      * EDIT /etc/rc.conf
          pf_enable="YES"
          pf_rules="/etc/pf.conf"
          pf_flags=""
          pflog_enable="YES"
          pflog_logsfiles="/var/log/pflog"
          pflog_flags=""
          pflogd_enable="YES"
          pfsync_enable="YES"

      * RELOAD THE RULES
            pfctl -nf /etc/pf.conf
## PORTS
 * All ports are located in /usr/port/graphics/
 * FETCH PORTS
 	portsnap fetch extract

 * VIEW MAKE OPTIONS FOR PKG
 	make showconfig

 1. BUILD

 make extract
 make && make install

## CONSOLE VIDEO MODE
 info: 	webpage newcons
 	syscons(4) / vt(4)

  1. Install drm-fbsd13-kmod
  2. kldload i915kms or add it to /etc.rc.conf kld_list="i915kms"


## KERNEL
 git clone --branch releng/13.0 https://git.Freebsd.org/src.git
 git clone --branch stable/13 https://git.Freebsd.org/src.git
 
 cd /src/sys/<arch>/conf/

 cp GENERIC CUSTOM 
 and change in CUSTOM line 22 ident GENERIC to ident CUSTOM

 * RETURN TO SRC PARENT DIRECTORY AND BUILD KERNEL
 make buildkernel KERNCONF=CUSTOM
 make installkernel KERNCONF=CUSTOM

 * REBOOT
### MAKE OPTION 

## HARDWARE INFORMATION
	pciconf -lv | grep vga

## GROUPS (PW / ID)
* CREATE USER GROUP
    pw groupadd cbtech

* CHANGE USER INITIAL GROUP
  pw usermod cbtech -g cbtech -G video,wheel,messagebus

* ADD USER TO GROUP VIDEO WHEEL
      pw groupmod video -m captainchris || pw groupmod video -m captainchris

* REMOVE USER FROM GROUP 
      pw groupmod del cbtech wheel

* SHOW USER INFORMATIONS
  id cbtech
  pw user show cbtech

* SHOW GROUP INFOS
  pw group show wheel

