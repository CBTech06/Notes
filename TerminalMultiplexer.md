#---- [ MULTIPLEXER ]

      <[index.md]

## [ DVTM ]

   Mod = <Ctrl>g

   Mod-c                Create New shell window
   Mod-C                Similar using current dir
   Mod-x-x              Close Focused window
   Mod-l                Increase master area
   Mod-h                Decrease master area
   Mod-j/J              Focus Next/Below window
   Mod-k/K              Focus Prev/Above window
   Mod-H                Focus to the left
   Mod-L                Focus to the right
   
   Mod-m                Maximize current window

   Mod-PageUp           Scroll Up
   Mod-PageDown         Scroll Down

## [ TMUX ]

  <prefix> r             Reload configuration
  <prefix> ?             List all Keybindings 
  <prefix> ~             Show all messages 
      - 
## WINDOWS

    <prefix> c             Create new window
    <prefix> n             Change to next window
    <prefix> p             Change to previous window
    <prefix> %             Split Left/Right
    <prefix> "             Split Top/Bottom
    <prefix> &             Kill current session
    <prefix> x             Kill current pane
    <prefix> [             Enter in copy mode 

### SWAP WINDOW TO LEFT OR RIGHT 

   tmux swap-window -t:-1                         Swap window to Left
   tmux swap-window -t:+1                         Swap window to right

## PANE  

   ### DEFINE PANE NAME 

   ### DEFINE TITLE
       printf '\033]2;%s' 'TITLE'
       printf "\033]2;TITLE" 

   ### SHOW STATUS PANE
       set -g pane-border-status top

   <prefix>:swap-pane -t:+1         Move current pane to right window
   <prefix> z                       Current pane fullscreen 
   <prefix> o                       Select the next pane in the window
   <prefix> x                       Close pane
   <prefix> {                       Move current pane to the left 
   <prefix> }                       Move current pane to the right

 ### RESIZE PANE
      tmux resize-pane -LRUD 10

   ### BIND 
      <prefix>: bind 'h' select-pane -L
      tmux bind "h" select-pane -L

## BUFFER 
   ### SET BUFFER 
      tmux set-buffer $(xclip -selection c -o)
      tmux setb $(pwd)                                      Copy pwd output to tmux buffer
      tmux show-buffer -b buffer0                           Show Buffer 0
      tmux show-buffer -b buffer0 | xclip -selection -i     Copy buffer0 to XClip

##  COPY / PASTE  
   ### VI MODE 
      :setw -g mode-keys vi
      list-keys -t vi-copy


   ### INTO COPY MODE  
       h   Go Left
       l   Go Right   
       j   Go Up
       k   Go Down
       L   Go Bottom
       H   Go Top
       v   selection
       V   Select line
       y   Copy the selection

  1. Enter copy mode using <prefix> + [
  2. space  to begin selection
  3. ctrl-w  to copy or y (vi Copy mode enabled)
  4. <prefix>+]  to paste

  In copy mode type :100 to go to offscreen line 100 

  ### CAPTURE PANE CONTENT INTO BUFFER
      tmux capturep -b temp -S -

##  STATUSBAR 
   show bash command in status bar
       #(whoami)

## COMMAND
   tmux list-commands              List all TMUX commands
   tmux list-keys                  List all keybindings
   tmux list-buffers
   tmux paste-buffer                Paste Buffer


## SESSION
   tmux a                 Attach to session 
   <prefix> d             Deatch session 

   ### CREATE NEW SESSION WITH NAME
      tmux -new -s Mysession

   * Create session and detach it immediately
      tmux -new -s Mysession -d 

   ### LIST SESSION
       tmux ls   :or:   <prefix>:list-sessions

   ### SELECTING A SESSION
       <prefix>:choose-session 
       <prefix>(                               Move to next session
       <prefix>)                               Move to prev session

   ### RENAMING SESSION
       <prefix>$      :or: tmux rename-session -t {current-id} {new-id} 
