# -----[ SSH HOW TO ]---- 

       <[index.md]

## SSH  
   If your private keys is encrypted with a passphrade, this passphrase
   must be entered every time you attempt to connect to an SSH Server using 
   public key.
                  
    ssh-agent:      is a program which cachees your decrypted private 
                    keys and provide them to SSH client
                
    ~/.ssh/id_rsa         ->          Private Key 
    ~/.ssh/id_rsa.pub     ->          Public key

  * public key goes into server "autorized_keys" file

## SSHD: SSH DAEMON ##

  Start server using /usr/sbin/sshd -h~/.ssh/id_rsa -d

  Allow user to accessing port 22:
  setcap CAP_NET_BIND_SERVICE=+eip /usr/sbin/sshd
                    
      -4                Forces sshd to use IPV4
      -6                Force sshd to use IPV6
      -c                Specifies a path to certifcation file to identify sshd during
                           key exchange.The certificate file must match a host key file 
                           specified using the -h option.
      -d                debug mode
      -D                SSHD will not detach and does not become a daemon
      -E                Append debugs logs to log_file instead of system log
      -e                write debug logs to std error 
      -f                Specifies a configuration file :DEFAULT: /etc/ssh/sshd_config
      -h                Specifies a file from which host key is read. This option
                             is for non root user
                             
                              :DEFAULT: 
                               * /etc/ssh/ssh_host_ecdsa_key 
                               * /etc/ssh/ssh_host_ed25519_key
                               * /etc/ssh/ssh_host_rsa_key

      -p port                 Specifies the port on wich the server 
      -t                      Test mode. Only check the validity of the configuration
                                        and sanity of the keys

## CONNECTION BETWEEN TWO LINUX COMPUTER WITH SSH AND ETHERNET
  1. INSTALL openssh-server 
  2. INSTALL openssh-client 

  3. SPAWN public/private key
  4. CONNECT via SSH with ssh user@ip_address
  5. MANIPULE windows on DWM client with xdotool

## SSH_KEYGEN ##

   ssh-keygen -b 4096                              Generate stronger RSA Key Pair
   ssh-keygen -f ~/.ssh/id_rsa -p                  Changing passphrase without changing the key

   ssh-copy-id username@ip
   ssh-copy-id -i ~/.ssh/id_rsa.pub username@ip    Specifies the location of the public key

   scp ~/.ssh/id_rsa.pub username@ip               Manual method

   * On the remote server:
        mkdir ~/.ssh
        chmod 700 ~/.ssh
        cat id_rsa.pub >> ~/.ssh/authorized_keys
        rm id_rsa.pub 
        chmod 600 ~/.ssh/autorized_keys


## SSH KEYS ## 
        
   challenge is an encrypted message. ssh-keygen
   generate by default a 2048bit RSA

      * RSA(Rivest-Shamir-Adleman)
      * DSA(Digital Signature Algorithm) 
      * ECDSA(Elliptic Curve Digital Signature Algorythm)
      * Ed25519 (Curve25519)
                        
      DSA are deprecated since openSSH 7. 
      RSA Keys provide the greatest portability.
      While ED25519 give you the best security but 
      require recent verions of client/server
               
      The PRIVATE key as the same name as PUBLIC key 
      but PUBLIC key as .pub extention

## COPY FILES
   NC10 RETRIEVE FILE FORM SERVER(HOST FROM SERVER)
      scp captainchris@192.168.1.53:~/.tmux.conf .

* SEND FILE TO HOST(SERVER TO HOST)
    scp -r folder cbtech@192.168.2.10:~

## TROUBLESHOOTING ##

   * Connection with X autologin
	edit /etc/ssh/ssh_config
		Add ForwardX11 yes


   Key ignored by the server
   * If it appears that the SSH server is ignoring your keys,
     ensure that you have the proper permissions
                    set on all relevant files.

   For the local machine:
     $ chmod 700 ~/ ~/.ssh
     $ chmod 600 ~/.ssh/id_ecdsa

   For the remote machine:
     $ chmod 700 ~/ ~/.ssh
     $ chmod 600 ~/.ssh/authorized_keys

  If that does not solve the problem you may try 
  temporarily setting StrictModes to no in sshd_config.
  If authentication with StrictModes off is successful, 
  it is likely an issue with file permissions persists.

  Make sure keys in ~/.ssh/authorized_keys are entered 
  correctly and only use one single line.
  Make sure the remote machine supports the type of keys 
  you are using: some servers do not support
  ECDSA keys, try using RSA or DSA keys instead


## SSH KEY FOR GITHUB

   ssh-keygen -t rsa 

   Save the file as id_rsa_github

   copy the id_rsa_github.pub and:
        1. Go to github account page
        2. SSH/GPG section and copy the public key
        3. Run sshd
        4. eval `ssh-agent -s` 
        5. ssh-add /home/captainchris/.ssh/id_rsa_github
        6. git clone your repository


