# ---- [ SYSTEMCTL ] ----

## COMMANDS 
* lIST ALL SERVICES RUNNING
	systemctl list-units --type=service --state=runninig
	or pstree	

* ENABLE/DISABLE SERVICE
	systemctl enable/disable openvpn.service

* START/STOP SERVICE
	systemctl start/stop openvpn.service

* SHOW STATUS ABOUT UNITS
	systemctl status polkit.service

* LIST DEPENDENCIES
	systemctl list-dependencies polkit.service 

## SERVICES
	wpa_supplicant
	networking
	NetworkManager
