# ---- [ WRITE WM TILLING MANAGER ] ----                                        

                < [index.md]

## SWAY WM

	mod + Enter 		New Terminal
	mod + f			Fullscreen
	mod + Shift + q		Quit programm
	mod + shift + e		Exit sway
	mod + shift + c		Reload sway
	mod + shift + -		Move to scratchpad
	mod + -			Show scratchpad

	mod 0-9			Change current workspace
	mod + Shit + 0-9	Move to desk 0-9
	mod + b 		Horizontol layout
	mod + v 		Vertical layout
	mod + s			Stacking layout
	mod + e			Toggle split layout
	mod + a			Focus on parent container
	mod + space		Swap focus between tiling and floating
	mod + shift + Space	Toggle floating mode
	mod + tab		Next workspace
	mod + L/R/U/D		Move focus of the window
	mod + Shift + L/R/U/D	Move the focused window in the workspace

## SWAYBAR 
	add command 
		status_command 

## SWAYMSG
 - Use SWAY config to search command and use it with swaymsg

 * LAUNCH APP USING SWAYMSG
 	swaymsg exec thunar
	swaymasg exec foot 'man libinput'
	swaymsg exec 'foot -e vim ~/.config/sway/config'
 
 * TOGGLE FULLSCREEN CURRENT WINDOW
	swaymsg fullscreen
 
 * TOGGLE FLOATING
   	swaymsg floating toggle

 * CREATE NEW WORKSPACE
	swaymsg workspace 3
 
 * RENAME WORKSPACE
 	swaymsg rename workspace 3 to NUKLEAR

 * SWITCH BETWEEN WORKSPACE 
 	swaymsg workspace next / prev

 * MOVE FOCUS 
 	swaymsg focus left/right/up/down
 
 * MOVE CURRENT WINDOW
	swaymsg move left/right/up/down

 * MOVE TO WORKSPACE 3
 	swaymsg move to workspace 3

 * KILL CURRENT WINDOWS
 	swaymsg kill

 * USE SWAYMSG OVER SSH USING SOCKET
     socket is locted under /tmp/100-runtime-dir
     `swaymsg -s /tmp/1000-runtime-dir/sway-ipc.1000*.sock'
 
 * USING SWAY_SOCK
     export SWAYSOCK=/tmp/1000-untime-dir/sway-ipc.1000.*.sock
     swaymsg --socket $(sway --get-socketpath) -t get_workspaces

 * GET TREE
  sway -t get_tree

## WRITING WM

 Original Post: `https://jichu4n.com/posts/how-x-window-managers-work-and-how-to-write-one-part-i/` 

 Window manager is a client of X server.

## SCHEMATICS
                                 APP                 APP
                                 ↓ ↑                 ↓ ↑
        WINDOW MANAGER          GUI FRAMEWORK   GUI FRAMEWORK
          ↓   ↑                  ↓  ↑                ↓ ↑
         ----------------- XSERVER ----------------------
          ↓   ↑                      ↑         ↑
        VIDEO CARD                  MOUSE   KEYBOARD 

  In modern GUI we use term widget or control, 
  In term application we use container instead widget.

  In windows is any rectangular area that is unit of user interaction

  The mechanism that allows a window manager to intercept such requests is called
  substructure redirection 

  Redirection means that an event is sent to the client selecting redirection (WM)

  * Schema 2:
               APP              WM
                ↓               ↓ ↑
                ↓               ↓ ↑
                ↓               ↓ ↑
                ↓               ↓ ↑
               ------ XSERVER ------

  1. App sends request to Xserver
  2. Xserver routes request to window manager (XSERVER UP TO WM)
  3. Window Manager grants,modifies,or denies request(DOWN TO XSERVER)

   Buttons minimizing maximizing and closing window are not 
   create by the application but by the window manager
   via a process known as reparenting of framing 

## WM CREATION

   1. Create a Root window
   2. When a top level window W is mapped (first shown),
        The window manager is notified by substructure redirection on the root
        and the toplevel window is a direct child of the root windows
   3. The root window creates a frame F and reparent W to F.

   XCB is asynchron. The advantage is we have 5 windows at once. 
   In XCB we can fire of all 5 requests to X server and then wait 
   for all of them to return.

  XLIB is synchron. we have send one request at a time

## MAPPING(SHOW) A WINDOW

   1. Recall that Create a frame window f
   2. Register for substructure redirect on f with XSelectInput().
       Recall that substructure redirect only applies to direct 
       child windows, so after reparenting, the substructure 
       redirect previously registered on the root window would no 
       longer apply to w, hence this step.
   3. Make w a child of f with XReparentWindow().
   4. Render f and w with XMapWindow().
   5. Register for mouse or keyboard shortcuts on w and/or f.
        Make w a child of f with XReparentWindow().
