# ---- [ AUTOLOGIN ] ----

## AUTOLOGIN WITH GETTY(TTY)
	1. ADD USER TO GROUP TTY
	2. CREATE / EDIT  /etc/login.defs and uncomment
		NO_PASSWORD_CONSOLE 	tty1:tty2:tty3:tty4:tty5:tty6
	3. EDIT /etc/inittab
	Change line 1:2345:respawn:/sbin/getty 38400 tty1
	to 1:2345:respawn:/sbin/agetty --autologin cbtech 38200 tty1

### VOID LINUX AUTOLOGIN 
 * EDIT /var/service/agetty-tty1/conf
 	* Add:
		GETTY_ARGS="--autologin cbtech --noclear"

## AUTOLOGIN (RUN STARTX AUTOMATICALLY)
* EDIT .profile
	if [ -z "$DISPLAY" ] && [ "$(fgconsole)" -eq 1 ]; then
		exec startx
	fi
