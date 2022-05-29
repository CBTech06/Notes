                                # ---- [ XDOTOOL ] ---- #
                                
                [ < GO Back](index.md)

## YDOTOOL
	* CREATE RUNSCRIPT (example VOID Linux)
	  1. Create a directory → /etc/sv/ydotoold
	  2. Create run file 
	         #!/bin/sh
		 exec /usr/local/bin/ydotoold --socket-path=/tmp/100-runtime-dir --socket-perm=0677
								
	* COPY MANPAGE
	   - Go to manpage folder
	       cp ydotoold.8.scd /usr/share/man/man8/ydotoold.8
	       cp ydotool.1.scd /usr/share/man/man1/ydotoold.1
	
	* SOCKET AUTHORISATION
	   - Change group
	       chown root:input .ydotool_socket
	       chmod 0607 .ydotool_socket
	
* COMMANDS
  
  * MOVE MOUSE
      ydotool movemouse 100 600

 * PRESS KEY
   All keys are listed in /usr/include/linux/input-event-codes.h

   ydotool key 28:1	Press Return
   ydotool key 28:0	Release Return

 * TYPE TEXT IN TERMINAL / BROWSER
      ydotool type Hello 	→ Type Hello in the terminal


# WEV (WAYLAND EVENT)
	export WAYLAND_DISPLAY=/tmp/1000-runtime-dir/wayland-1
	
## EXAMPLES:

	xdotool exec thunar						
	xdotool key F2	                    	Send F2 keystroke
            key Page_Down                   Scroll Page_down 
            key plus                        Zoom +
            key minus                       Zoom -
	xdotool Aacute		                    Send a with accent 
	xdotool search --name gdb key ctrl+c	Send ctrl+c to all windows matching gdb

	xdotool windowmove 100 y    			Moves to 100,y
	xdotool getactivewindow					Ouput active window
	xdotool getactivewindow getwindowpid	Get PID of current window 
	xdotool getwindowname $(xdotool getactivewindow)		Get name of the current window
 	
	xdotool getactivewindow windowsize 640 100		Resize Windows
	
	
	xdotool search --name ROXTerm				List all windows with ROXTerm Name
	xdotool search windowfocus 8327665			Focus windows
	xdotool getactivewindow window move 0 0		Move window

	xdotool get_desktop							Get current desktop
	xdotool set_desktop 1						Change Desktop to 1


	Windows organisation Dual screen
		
* SIZE:
		Halfscreen: xdotool getactivewindow windowsize 630 990
		Tile(4-1):  xdotool getactivewindow windowsize 630 450 
	
* POSITION
	1. xdotool getactivewindow windowmove 5 5
	2. xdotool getactivewindow windowmove 640 5
	3. xdotool getactivewindow windowmove 1285 5
	4. xdotool getactivewindow windowmove 1920 5


		|----------------------|----------------------|
		|	   |	       |           |          |
		|	   |	       |           |          |
		|   1	   |	 2     |    3      |    4     |
		|	   |	       |           |          |
		|	   |	       |           |          |
		|----------------------|----------------------|
		|	   |	       |           |          |
		|	   |	       |           |          |
		|	   |	       |           |  4-1     |
		|	   |	       |           |          |
		|	   |	       |           |          |
		|---------------------------------------------|
