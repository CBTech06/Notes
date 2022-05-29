# ---- [ FIREWALL ] ---- 
 	
	< [index.md]
               
## CREATE GATEWAY NAT WITH FIREWALL USING FREEBSD
	NAT :  Allow multiple devices to acces the internet throught 
	       a single public adress

	All ports are liste in /etc/services	

* ENABLE FIREWALL
	* EXAMPLE OF CONFIGURATION FILE ARE LISTER IN /usr/share/example/pf/
		sysrc pf_enable=yes
	
	. Add rule in /etc/rc.conf
		pf_rules = "/etc/pf.conf
		sysrc pflog__enable="yes"
		pflog_logfiles="/var/log/pflog"
		gateway_enable="YES"
	

## PROTOCOL
        
        WHOIS : Is a query response protocol that is widely used for querying database
                that store the registered users or assignees of an internet resources,
                such as a domain name, an IP adress...
                
        GOPHER: Is a communication protocol designed for distributing, searching 
                and retrieving documents on Internet Protocol network.
                It is presented an alternative to the HTTP in early stage.
               
        KERBEROS: Is a computer-network authentication protocol that works on the basis 
                  of tickets to allow nodes communicating over a non secure network to 
                  prove their identity to one another in a secure manner.
                  
        TLS/SSL: Transport Layer Security and its now predecessor, SSL (Secure Socket Layer)
                 are cryptographic protocols designed to provide security over a computer 
                 network.Website can use TLS to secure all communications between their server
                 and web browser.
                 
        SOCKS:  Is an internet protocol that exchanges network packets between client and server 
                through proxy server . SOCKS5 provides authentication so only authorized users 
                may access a server 
        
        TCP:    
        
         
## IPTABLES 

    
    [IPV4] / [IPV6] table contains :CHAIN: .CHAIN is a list of rules. Rules specifies criteria for packet and target.
    
    ### SPECIAL VALUES 
        
        ACCEPT: means let the packet throught
        DROP: means to drop the packet on the floor
        RETURN: Stop traversing this chain and resuume at the next rule in the previous chain
    
    ### TABLES 
        
        By default there are 5 tables. 
            
            1. filter (default) : INPUT: for packets destined to local socks.  FORWARD: for packets being routed throught the box  OUTPUT: for locally generated packets
            2. nat :
            3. mangle :
            4. raw :
            5. security : 
        
        
## MODEL OSI

               * Communication model *
                
                7 - APPLICATION LAYER
                        
                        An application layer is an abstraction, layer that specifies the shared
                        communications protocol and interface methods used by hosts in a 
                        communication
                        
                        NNTP / SIP / SSI / DNS / FTP / GOPHER / HTTP / NFS / NTP / SMPP
                        SMTP / SNMP / TELNET / DHCP 
                        
                6 - PRESENTATION LAYER
                        
                        The presentation layer is responsible for the formatting and delivery 
                        of information to the application layer for further processing and 
                        display
                       
                        MIME : (Multipurpose Internel Mail Extensions) 
                                Attachements of audio,videos, images in Mail.
                                
                        XDR: (External Data Representation)
                                Is a standard data serialization format, It allows data to be 
                                transferred between different kinds of computer systems.
                        
                        ASN.1: (Abstract Syntax Notation One) 
                                Is a standard interface description langiage for defining data 
                                structures that can be serialized and deserialized in a cross
                                platform way.
                                
                        ASCII: (American Standard Code for Information Interchange)
                                Is a chacrater encoding.
                                
                        PGP:    (Pretty Good Privacy)
                                Is an encryption program that provides cryptographic privacy
                                and authentication for data communication.PGP is used for 
                                signing,encrypting and decrypting texts, emails, files, dir
                                

