                                # ---- [ I3 BASH SCRIPTING ] ---- #
                                
                <[index.md]
                
## USEFUL TIPS  ##
        
        #!/bin/bash                              <- hashbang shebang
        
        USER="LEMAITRE Jack"
        
        ' does not allow substitution
                echo 'Hello $VAR '                        <- hello $VAR
                
        " Allow substitution
                echo "HELLO $VAR"                        <- hello BOURGEOIS Christophe                       
         
                
## PANGO MARKUP ##
        ### ATTRIBUTES ###
                foreground / background
                font='FontAwesome'
                
                font_size='xx-small/x-small/small/medium/large/x-large'
                font='12.5'
                
                font_weight='ultralight/light/normal/bold/ultrabold/heavy'
                underline='single/double/low/error/single-line/double-line'
                
               <span foreground='red' font='FontAwesome'></span>

               
## SCRIPT WITH DATE ##
        
        date "+%H"            Return Hours
        date "+%M"            Return Min
        date "+%S"            Return Seconds
                
