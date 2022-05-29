# ---- [ OPENRC ] ---- #
                                        
              < [index]

## TOOLS:
	openrc	rc-status 	rc-update 	rc-service

## RUNLEVELS:
	`boot` 			Only service that deal with the mouting of filesystem 
	`sysinit`  	Mount /dev /proc and optionnaly /sys
	`single` 		Stop all service except those in sysinit level	
	`reboot`	  Reboot the host	
	`shutdown` 	Shutdown the host
				
## RC-UPDATE
* LIST STARTED SERVICES
 			rc-update show	

* DELETE SERVICE FROM DEFAULT RUNLEVEL
			rc-update delete sshd default
							
## RC-SERVICE
* LIST ALL  AVAILLABLE SERVICES
				rc-service -l
							
* COMMANDS
			stop / start / restart / describe / zap(Reseting to Stopped state)	

* START SERVICE
			rc-service elogind start
		or
			service elogind start

## RC-STATUS
	* LIST ALL PROCESS IN RUNLEVEL
			rc-status sysinit
