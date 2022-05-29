                                        # ---- [ FZF / RIPGREP ] ---- #
                                        
                                        
                [<GO Back](index)
                
## OPTIONS ##
        
        -A                      Show num lines after each match
        -e / --regexp           Search for regexp
        -s                      Case sensitive 
        -c                      Count line number and disable the output similar close to -l but show the line number
        -l                      Only print the path of the filename useful when you use it in the command $()
        --color WHEN            This flag controls when to use colors [never,auto,always,ansi)
        --colors COLOR_SPEC     colors matches rg --colors 'matches:fg:yellow' ip -> color all IP in expression  
        --vimgrep
        -t                      specify the filetype rg -t md <expression>
        -f                      Files flag
        -w                      Only show matches surrounded by word boundaries 
        --hidden                Force ripgrep to search in hidden [dir](dir)
        --engine                Use rust or PCRE2 search engine  
        
        'regexp                 Search exact term
## USAGE ##
        
         Search files in /mnt/Notes and open it in neovim
          ```sh
            1.     nvim $(find /mnt/Notes/ | fzf -e -i --reverse --preview 'rg "$1" {} | head -500')
          ``` 
                

        
 
