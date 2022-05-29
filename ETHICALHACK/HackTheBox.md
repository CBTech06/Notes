# ---- [ HACK THE BOX GUIDELINE ] ----

##  MEAOW First Chalenge
   Select VPN US Starting Point / US Starting point 1
   Download the file ovpn → pack.ovpn
   Start openvpn   openvpn pack.ovpn

   * Create interface tun0 :
      `ip link show`      tun0 appears
      `ip addr show`      show ip addr of tun0

   telnet 10.129.131.182
   login:root
   cat flag.txt

## FAWN Second Chalenge

## DANCING (SMB)
 * TASK 
      1. Server Message Block
      2. Port 445
      3. client-server model
      4. microsoft-ds
      5. smbclient
      6. flag -L
      
         smbclient -L `target_ip`     List all host
            ADMIN$   Allows system administrators.These shares may be disabled
            C$       This is where the operating system is hosted
            IPC$     The interprocess communication shared. It is not a part of system
            Workshares     Custom share

      7. smbclient \\\\target\\Workshares
      8. get (ls and get files)


