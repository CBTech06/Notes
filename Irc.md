# ---- [ IRC ]  ----
                                
    <[index.md]
 
## IRSSI 
  /quit /exit									Quit Application
	/part /leave 								Quit channel 
	Alt + LRUD 									Window Left/Right/Up/Down
	/connect										Connect to new server / CTRL+ Shift +x to switch between server
	/window new split 					Split Win H
	/wc													Close current window

## CONNECTING USING SSL
  /SERVER ADD -auto -ssl -ssl_verify -ssl_capath /etc/ssl/certs -network freenode -port 6697 irc.freenode.net
	/NETWORK ADD -sasl_mechanism plain -sasl_username <username> -sasl_password <password> freenode

## AUTOCONNECT
  /server add -auto -network freenode chat.freenode.net
  /channel add -auto #archlinux freenode

## ADD SERVER MANUALLY
* EDIT .irssi/config FILE
	- add server like this
```bash
	{
		adress = "irc.libera.chat";
		chatnet = "libera";
		port = "6697";
		use_tls = "yes";
		tls_verify = "yes";
		autoconnect = "no";
	},
```
* CONNECT: /connect libera
		
## SERVERS
	/connect irc.libera.chat 6697




