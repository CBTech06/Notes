# ---- [ BASH KEYBINDINGS ]

        <[../index.md]

## SHORTCUTS
   cd ~ or ~            Home directory
   cd -                 Last Directory

   pushd $(pwd)         Mark directory
   popd                 Go to Last Directory 
                        in the stack

## EXPANSIONS         
* SET TERMINAL NAME
      printf "\033]2;TITLE\007" 

   cat ~/.config/Scripts/bookmark | fzf -e -i 
       --reverse | sed 's/^.*|//'

* SHOW PREVIOUS COMMAND
   !!
   EXAMPLE: cat ~/.config/Scripts/bookmark | 
            fzf -e -i --reverse | sed 's/^.*|//'

* PREVIOUS ARG
    !*            
        RESULT:  ~/.config/Scripts/bookmark | 
                 fzf -e -i --reverse | 
                 sed 's/^.*|//'
    !-1     Previous CMD
    !-2     Prev Prev command
    !$      Previous last command arg 
        RESULT: 's/^.*|//'
    !:1     First ARGS         
        RESULT: ~/.config/Scripts/bookmarks 
   !:2-3   Second to third arguments
   !:2-$   Second to last arguments
   !:2*    Second to last arguments
   !:2-    Second to next to last arguments
   !:0     The command

   Command: df
   !$ -du                    Add -du to the end of
                             the previous command
   !:s/addr/route            Change addr to route

* CHANGE COMMAND IN HISTORY WITH SED 
   535 git clone https://github.com/libimobiledevice/libplist
   
   I want to change libplist with libimobiledevice-glue
      !535:s/libplist/libimobiledevice-glue

## SUBSTITIONS 
   echo Bonjour Christophe

* CHANGE HELLO TO GOODBYE
   !:s/Hello/GoodBye    
* CAHNGE ALL HELLO OCCURENCE
   !:gs/Hello/Bye

## KEYBINDINGS 
   bind -P         List all keybindings
   \e              ALT
   \c              CTRL

    ALT+~        Complete user
    ALT+$        Complete var
    ALT+/        Compplete filenmae 
    ALT+<        Begining history
    ALT+*        Completion( search program)
    ALT+l        Downcase word
    ALT+c        Capitalize word
    ALT+d        Delete word under cursor
    ALT+t        Transpose word

    CTRL+x+CTRL+v    SHow BASH Version
    CTRL+l           Clear Screen
    CTRL+e           End of Line
    CTRL+f           forward-char
    CTRL+t           Switch char with previous 
    CTRL+ r          Reverse search history

### CREATING A NEW KEYBINDING 
     bind '"\c-u":"Hello"'

### LIST ALL CUSTOM KEYBINDINGS
      bind -X

### REMOVING EXISTING KEYBINDING
        bind -r "\C-u"
