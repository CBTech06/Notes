# --- [ XORG ] ---

## AUTOLOGIN
  * EDIT /etc/inittab

  id:2345:respawn:/sbin/getty --autologin cbtech 38200 tty1

  * DISABLE PASS ON TTY
   * EDIT /etc/logindefs
    Add  NO_PASSWORD_CONSOLE

 * You can define TTY permissions in login.defs

 
## AUTOSTART
  x:2345:respawn:/home/cbtech/startweston

# PKG
	xf86-input-intel
	xf86-input-keyboard

# MOUSE TRACKPAD	
	xf86-input-mouse
	xf86-intpu-synaptics

# INTEL CONF ( 20-intel.conf )
```sh
	Section "Device"
		Identifier "Intel Graphics"
		Driver "intel"
	EndSection
```

# KEYBOARD CONF(00-keyboard.conf)
``` sh
	Section "InputClass"
		Identifier "system-keyboard"
		Option "XkbLayout" "fr"
		Option "XkbModel" "pc104"
	EndSection
```
