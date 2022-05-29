# ---- [ PRINTERS ] ---- #
                                
                [ < GO Back](index.md)
                

        Use lpadmin and lpinfo in commandline to manage printers
        All PPD files are located to : /usr/share/ppd/HP/
        
## LPINFO 
        
                ### LIST ALL DEVICE  
                        lpinfo -v 
                
                ### LIST ALL DRIVERS 
                        lpinfo -m    
                
                ### LIST ALL DRIVERS FOR HP DESKJET   
                        lpinfo -m | grep -i" hp deskjet 2600"
        
## LPOPTIONS 

                ### LIST ALL OPTIONS 
                        lpoptions -l
                        
                ### PRINT LANDSCAPE FORMAT  
                        lp -o landscape gui.cpp -d dest
                        
                ### FIT TO PAGE SIZE 
                        lp -o fit-to-page <file> -d dest
                        
                        
## ADD A NETWORK PRINTER USING LPADMIN
        
        
        :WARNING: -m option are depercated.don't use it
        
                lpadmin -p HP_DeskJet2600 -E -v socket://192.168.1.84 -m file.ppd
                
                ### LIST ALL DRIVERS USING DESKJET 2600 
                        lpinfo --make-and-model "deskjet" -m | grep "2600"
                
                ### SHOW DEFAULT DESTINATION 
                        lpstat -d
                        
                ### SHOW PROCESSING STATE OF DESTINATIONS  
                        lpstat -p
                        
## ADD USB PRINTER USING LPADMIN 
                
                lpadmin -p HP_DeskJet2600_USB -E -v "usb://HP/DeskJet%202600%20series?serial=CN9AC9718H06MD" -m file.ppd
                
                ### PRINT USING LP 
                        lp gui.cpp -d HP_DeskJet_2600_Series
                
                ### MANAGE JOBS USING LPSTAT 
        
                ### REMOVE PRINTER 
                      lpadmin -x HP_DeskJet_2600_series
        
## SCANNER
       
                ### LIST ALL DEVICES 
                        scanimage -L
                        
                ### SCAN IMAGE 
                        scanimage -d hpaio:/usb/DeskJet_2600_series?serial=CN9AC9718H06MD -o file.pn
                
                

