# ---- [ VIM ]

        <[index.md]

## ---- [USEFUL NOTES] ----
   st -e vim -c 'vert term /bin/bash'                    Start VIM with Term 
   :scriptnames					         List scripts installed
   q:                                                    Open Menu with history

* Man page using VIM
   MANPAGER="vim +MANPAGER" man cp                                    :WORK:
   MANPAGER="vim -m +MANPAGER --not-a-term -" man cp

* OPEN MANPAGE ON PROGRAMMING KEYBOARD
     put your cursor under keyword press shift+k

* XClip
   :!xclip -sel c -f      	 Copy to xclip  
   :r !xclip -sel c -o      	 Paste from xclip

* Digraph: 
    `:digraphs`               List All digraphs codes
    [INSERT] `<Ctrl>k  -!`    Insert ↑
             `<Ctrl>k  <-`    Insert ←
             `<Ctrl>k ->`     Insert →
             `<Ctrl>k -V`     Insert ↓
* OPEN VIM AT LINE 224
    vim +2244 file.cpp

### TERMINAL
  :term /bin/bash                      Open terminal
  :vert term /bin/bash                 Open vertical Terminal
  CTRL-W N                    Normal Mode
  i                           Insert Mode
  CTRL-W c                    Close Window 
  CTRL-W q                    Quit Window

### SEARCH USING VIMGREP
   * Go to the location of current edited file
      `:cd %:h`
   * Search sed occurrence in file and open occurence highlight 
      `vimgrep "sed" file.cpp | copen`
   * search sed recursively 
      `vimgrep "sed" **/*.md`
   * Search in the current filepath active buffer
   	vimgrep "lambda" %

### MACRO
   Press q<letter>                        Record macro letter
   <number>@<letter>                      Play <number> times macro
   @<letter>                              Execute macro
   @@                                     Execute macro again

### FILE EXPLORER NETWRIST
  :Sex                        Open Explore in split
  :Sex!                       Open Explore in Vertical Split
  :e%:h/filename              Edit file in current dir
  :w%:h/filename              Write file in current dir
  d                           Create Dir in explorer
  %                           Create File in explorer
  mb                          Mark Current directory
  gb                          Go to marked directory
  d                           Create directory in explorer
  %                           Create file in explorer
  i                           Change List view
### PRINTING
  1. Define Font and Print in ps
      set printfont=CodeNewRomandNerdFont:h12
      :ha > file.ps
 
  2. Transform file into PDF
      ps2pdf file.ps 

## ---- [KEYBINDING] ----
   CTRL-W + c              Close Windows
   CTRL-W + T              Tab to new Window

### ACTION
   xp                       Swap two characters
   g/text/                  Show All lines with text
   /pattern                 Search forward pattern 
   ?pattern                 Search backward pattern
   *                        Search words under the cursor
   [I                       Show lines with matching words
   noh                      Remove highlighting
   R / r                    ReplaceMode / Replace char
   > / <                    Indent / Unindent
   di(                      Delete everything between ()
   Ctrl+r + (insert mode)   Paste clipboard content
   Ctrl+v                   Visual Block
   3p                       Paste 3 Times
   ciw                      Change Inner word
   di(                      Delete everything () "" '' ...
   dw                       Del current pos to newt word
   d$                       Delete current pos to end of line
   d0                       Delete current pos to begin of line 
   Yiw                      Copy inner word
   :g/^#/d                  Remove all commented lines
   :g/^$/d                  Remove all blank lines
   c3l                      Replace 3 char

### NAVIGATION
   h                     Move left
   k                     Move Up 
   j                     Move Down
   l                     Move Right
   w                     Next word
   e                     End of word
   b / B                 Previous word / WORD
   0                     Start of line
   $                     End of line
   gg/ G                 Begin of file / End of file
   CTRL + ]              Jump to quickref help
   CTRL + O              Jump older location 
   :vert help            Help in vertical mode
   (                     Start of sentence
   )                     End of sentence 
   {                     Start of paragraph
   }                     End of paragraph 
   H/L/M                 Move to top/Bottom/Middle 
   %                     Next bracket
   :N                    Goto N line
   Ctrl + d/u            Go 1 Screen down / Go 1 Screen up
   zj / zk               Prev / Next fold 
   gf                    Go file under cursor

### TABS / WINDOWS
   :tabnew <file>        Opening file in a new tab
   :tabnext              Next Tab
   :tabprev              Previous Tab
   :tabe <filename>      Edit file in new file
   Ctrl+ww               Switch window
   gt/gT/#gt             Tab Next/Prev/Tab#

### SEARCH
   %s/pattern/foo        Change all pattern / foo
   %s/pattern/foo/c      Change all pattern / foo with conf
   %s/pattern/foo/g      Change all occurence
   n / N                 Next Search Match /Prev Search

### MARKS
   m[a-z]                 Create Mark
   '[a-z]                 Jump to Mark
   '[A-Z]                 Jump to mark over the files 

### FOLD
   setlocal foldmethod=expr  Fold(hide)  Expr:syntax/indent/...
   zf                        Define Fold
   zo                        Open fold
   zc                        Close fold
   zd                        Delete fold

### BUFFER
   :buffer <nb>              Switch to buffer <nb>
   :ls                       List all buffer
   :b <TAB>                  Switch between buffer with TAB
   :bd                       Delete Buffer 
   :bw                       Write buffer  and close

### OTHER
   :htp                     Show Runtimepath
   :ls                      List all Buffer
   :tab h helpgrep conceal  Summarize of conceal
   :!make -j8               execute Shell Command
   :set nornu               Disable relative number 

### HELP
   :tab h pattern        Open help in new tab
   :vert h pattern       Open help in vertical split  
   :tab h CTRL-W         View all CTRL-W Shortcuts

### NAVIGATE THROUGHT HELP(TAGS)
  Move cursor to the bar, then CTRL+] 
  to go to the selected selection

