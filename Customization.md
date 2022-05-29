# ----[COLORSCHEME]---- 
                        
            < [index]

## DMENU
 * USAGE
  dmenu -nf '#404613' -nb '#ffffff' -sf '#404613' -sb '#988800'

	nf: Font color
	nb: Background color
	sf: Highlight text
	sb: Highlight background

## PROMPT
  USER:  ┌─[\[\e[0;36m\]\u\[\e[0m\]]-[\w] \n└─▪
  ROOT:  ┌─[\[\e[0;31m\]\u\[\e[0m\]]-[\w]\n└─▪

## DWM
	* Nerd font Cheatsheet 
		https://www.nerdfonts.com/cheat-sheet?set=nf-mdi-
	1.  create theme in themes/default.h
	2.	Define all colors in default.h
	```c
	static const char normal_bg[]   = "#1e222a";
	static const char normal_fg[]		= "#2e323a";
	static const char normal_bd[]   = "#545862";
	static const char select_fg[]   = "#0074C4";
	static const char select_bg[]   = "#61afef";  
	static const char select_bd[]   = "#61afef";  
	static const char font_color[]  = "#282828";  
	```
	3.  Include Theme in config.h #include "theme/one.h"

## TTY COLORS
```sh
if [ "$TERM" = "linux" ]; then
  echo -en "\e]P0111111"        # Black
  echo -en "\e]P8222222"        # Dark Grey
  echo -en "\e]P1803232"        # Dark Red
  echo -en "\e]P9982B2B"        # Red
  echo -en "\e]P25B762F"        # Dark Green
  echo -en "\e]PA89B83F"        # Green
  echo -en "\e]P3AA9943"        # Brown
  echo -en "\e]PBEFEF60"        # Yellow
  echo -en "\e]P4324C80"        # Dark Blue
  echo -en "\e]PC2B4F98"        # Blue
  echo -en "\e]P5706C9A"        # Dark Magenta
  echo -en "\e]PD826ABL"        # Magenta
  echo -en "\e]P692BL9E"        # Dark Cyan
  echo -en "\e]PEALCDCD"        # Cyan 
  echo -en "\e]P7FFFFFF"        # Light Grey
  echo -en "\e]PFDEDEDE"        # White
  clear                         # For background artifacting
fi
```

## TERMINAL
	* SET TERMINAL NAME
      printf "\033]2;TITLE\007" 
  CTRL + + Zoom IN
  CTRL + - Zoom OUT

  NORMAL : BRIGHT
  C0 : C8   -> BLACK 
  C1 : C9   -> RED
  C2 : C10  -> GREEN 
  C3 : C11  -> YELLOW
  C4 : C12  -> BLUE
  C5 : C13  -> MAGENTA
  C6 : C14  -> CYAN
  C7 : C15  -> WHITE
