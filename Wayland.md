# ---- [ WAYLAND - DISPLAY SERVER PROTOCOL ] ----


	<[index.md]

## Wlroots Programming 
    Wlroots.md 
    DWL.md
    TinyWL.md

## CREATE CLIENT 
	[int main]
		1. Create display using wl_display_connect
		2. Create registry and get information 
		   with wl_display_get_registry
		3. Add reigistry listener with 
		   wl_registry_add_listener 
		     3.1 handle global to bind all interface to and ID
		     3.2 handle_global_remove to release all interface
		4. Create SHM Pool for buffer


## BUILDING FROM SRC
	* DEPENDENCIES:
		- gcc / g++ / libc-dev / meson / pkgconfig / cmake 
		- expat-dev / graphivz-dev / libffi-dev / doxygen /libtool / gperf
		- xmlto / libdrm / libpciaccess / mesa / libxkbcommon / libseat / mtdev

1. Build Wayland → https://gitlab.freedesktop.org/wayland/wayland.git
	meson build/ --prefix=/usr --libdir=/usr/lib --sysconfdir=/etc
	ninja -C build/
	su -c "ninja -C build/ install"
		`repeat step 1`

3. Build libdrm → https://gitlab.freedesktop.org/mesa/drm.git
	 Build  autoconf /automake/ eudev → https://github.com/eudev-project/eudev
	 libxkbcommon / libseat / mtdev / libevdev / libwacom/ gtk+-3.0-dev / checkdev / libinput
	 xwayland-dev / xcb-util-renderutil-dev xcb-util-wm-dev  
	 libxcb-errors → https://gitlab.freedesktop.org/xorg/lib/libxcb-errors
	 
4. Build WLRoots → https://gitlab.freedesktop.org/wlroots/wlroots

## WAYLAND-SCANNER 
  Wayland-scanner generate C/H(header code) from xml file.

* GENERATE HEADER FOR SERVER / CLIENT
    wayland-scanner server-header < protocol.xml > protocol.h
    wayland-scanner client-header < protocol.xml > protocol.h

* GENERATE C CODE
    wayland-scanner private-code < protocol.xml > protocol.c

* EXAMPLE WITH WAYLAND-PROTOCOL UNDER FREEBSD
    wayland-scanner server-header </usr/local/share/protocols/stable/xdg-shell/ \
            xdg-shell.xml > xdg-shell-protocol.h
  

## CONFIGURE INPUT USING SWAY-INPUT        
  * GET LIST OF INPUT
    swaymsg -t get_inputs | grep -i wacom

    and configure it in the sway config file.
    input "1670:8197:Dell_dell_usb_keYBOARD" {
    	xkb_layout "us,us"
	xkb_variant "dvorak,"
	# configoption
    }

 type:<input_types>

* USING LIBINPUT
	swaymsg input '1386:178:Wacom_Intuos3_9x12_Pad' button[1]	
e
EXAMPLE:	 
	swaymsg input '9580:110:HUION_420_Pen' map_to_region(slurp -a 400:223|tr',x' ' ')

* USING SEAT (Simulate Click Left Mouse)
  * LIST SEAT
      swaymsg -t get_seats
	
  * Attach to device
	swaymsg seat seat_wacom attach "1386:178:Wacom_Intuos3_9x12_Pad"
	
  * SIMULATE MOUSE CLICK LEFT
	swaymsg seat 'seat0' 'cursor press BTN_LEFT'
	* OR
	swaymsg seat - 'cursor press BTN_LEFT'

	* Place Mouse cursor to position X/Y

	swaymsg seat 'seat0' 'cursor set 100 100'


 input_types:   touchpad / pointer / keyboard / touch / 
 		tablet_tool / tablet_pad /switch

	
## USAGE
* LIST ALL RECONIZED DEVICE 
	libinput list-devices

* DEBUG EVENTS	
	libinput debug-events
	
	Push buttons to see the code and the vars 
	of each button

* START UDEV
		/etc/init.d/udev start
		udevadm trigger

## XDG_RUNTIME
	* CREATE XDG_RUNTIME_DIR
```sh
	#!/bin/bash
	# Set the var, you could hardcore to 1000
	XDG_RUNTIME_DIR=/run/user/$(id -u)
	# Create directory, you need root
	mkdir -p $XDG_RUNTIME_DIR
	mount -t tmpfs-o size=100m tmpfs $XDG_RUNTIME_DIR
```
	* CREATE /etc/profile.d/xdg.sh
or 
```sh 
	#!/bin/bash
	if [ ! -d /tmp/runtime-$USER ]; then 
		mkdir -p /tmp/runtime-$USER
	fi
	if [ -d /tmp/runtime-$USER ]; then
		export XDG_RUNTIME_DIR=/tmp/runtime-$USER
	fi
```

* CONFIGURATION UNDER FREEBSD
    export XDG_RUNTIME_DIR=/tmp/$(id -u)
    test -d "$XDG_RUNTIME_DIR" || { mkdir "$XDG_RUNTIME_DIR"; chmod 700 "$XDG_RUNTIME_DIR"; }

## LIBSEAT
	* Could no connect to socket /run/seat-sock
		1. Install seatd seatd-openrc
		2. add user to `_seatd group`
		3. rc-service seatd start


