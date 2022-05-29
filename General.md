# ---- [ GENERAL LINUX NOTES ] ----

      <[index.md]

## USEFUL COMMAND
   * ADD GROUP / REMOVE
   	groupadd / groupdel _seatd	

   * CONNECTION ROOT IMPOSSBILE
   	-rwxr-xr-x root root 	/bin/su
	chmod u+s /bin/su to change permission to s

   * INFORMATIONS ABOUT FILES
	stat /usr/bin/X 

   * PASTE FILE TO PASTEBIN
    cat file | nc termbin.com 9999

   * Show Directory and size
      	dh -h
        du -h --max-depth=1		  Just Directory without file
        du -h -s                Just size of current directory 
   
   * Count line in All *.c *.h files
      `wc -l *.[hc]`

   * Copy multiple files(.vimrc,.vim to dest
       cp .{vimrc,vim} dest
       mv {ende.py,flag.txt.en,pw.txt} dest/

   * List file 
       `ls test*`      List all file named test
       `ls test?`      List test2/test3/test4/test5
       `ls test???`    List test340/test564/test700
       `ls -lh`        List Files with Size Kb/Mb/Gb
       `ls *.[hc]`     List all .H .C files 

   * Markdown files to PDF using pandoc and texlive 
      `pandoc file.md -o file.pdf`

## DD
* INFORMATION ABOUT SECTOR WITH 
    fdisk -l /dev/sdd1
    500 GB = 500107862016 bytes / 976773168 sectors
             976773168 * 512(1 sector) = 500107862016
    USB3 → 16 MB/s = 2h00 → 116 GB 

* FILL DISK WITH RANDOM DATA
  dd if=/dev/urandom of=/dev/sdx status=progress

## BATTERY
  * PRINT BATTERY INFORMATION 
      * SHOW PERCENT
        cat /sys/class/power_supply/BAT<ID>/capacity
        acpi                      

  * PRINT USER CONNECTED 
                whoami

    * COPY STD OUTPUT TO FILE
                make localmodconfig 2>&1 | tee file

    * MOUNT USBSTICK WITH PERMISSIONS 
               sudo mount /dev/sdb1 /home/captainchris/mount/ -o umask=000

    * LIST ALL MAN PAGES
                man -k zathura

     ## XRANDR DEFAULT MODE 
                xrandr --output DVI-I-0 --mode 1280x1024

     ## TURN OFF THE MONITOR 
                xset dpms force off
    
     ## READ 8th MAN PAGES
                man 8 apk

# KEYMAP
  usage: `loadkeys fr`

  * All keymaps are located in `/usr/share/kbd/keymaps/i386/azerty`
   all keymaps are file.map.gz

  * To load specific key map: 
      `loadkeys/usr/share/kbd/keymaps/i386/azerty/fr.map`

# XCLIP CLIPBOARD
   * COPY USING XCLIP  
              xclip -selection c 
   * PASTE USING XCLIP 
              xclip -selection c -o
   * PASTE CONTENTS INTO FILE 
              xclip -o > output.txt

   * COPY  OUPUT COMMAND INTO XCLIP 
      `cat file | xclip 
       echo $(cat ~/.config/Scripts/bookmarks | fzf -e -e --reverse | sed 's/^.*|//') |
       xclip -selection c`

   * USE IN CMD LINE
              youtube-dl $(xclip -selection c -o)

## DATE        
 <usage>                            date +"%A"
    %a  Abbreviated weekday name.
    %A  Full weekday name.

  %b  Abbreviated month name.
  %B  Full month name.

  %c  Date and time representation. [Sun Aug 8 16:04:10 2021]
  %C  Century

  %d  Day of the month as a decimal number [01,31].
  %D  Date in the format mm/dd/yy.
 
  %e  Day of the month as a decimal number [1,31]
 
  %h  Similar to %b.
  %H  Hour (24-hour clock) as a decimal number [00,23].
 
  %I  Hour (12-hour clock) as a decimal number [01,12].
  %j  Day of the year as a decimal number [001,366].

  %m  Month as a decimal number [01,12].
  %M  Minute as a decimal number [00,59].
 
  %n  Newline
  %t  Tabulation
 
  %p  AM or PM.
  %r  12-hour clock time [01,12] using the AM/PM notation;
  %S  Seconds as a decimal number [00,60].
 
  %T  24-hour clock time [00,23] in the format HH:MM:SS.
 
  %u  Weekday as a decimal number [1,7] (1=Monday).
  %U  Week of the year      
 
## PERMISSIONS
## CHMOD
        
        -rwx r-x r-x 1 captainchris captainchris 8320 Apr 22 15:38 gui.cpp
         <u> <g> <o>
         
                 u:     USER /  g:     GROUP   /   o:     OTHER
         
         chown ugo+x | chown a+x :              Add execution for all users 
         chmod uo=rw  <file>
         
         ## Change permissions with octal number [421]
                - rw- r-- r-- =  chmod 644       - rwx --- --- = chmod 700 
                  420 400 400                      421 000 000
                   6   4   4     


         ## UMASK  

                umask look the bit off. He is working for creating all new file.
                rw 7-6 = 1        r 7-4 = 3    7-7=0
                
                - umask 000      rw- rw- rw-            umask 033       rw- r-- r--
                - umask 666      --- --- ---
                - umask 137      rw- r-- --- 

## GREP / PDFGREP
* SEARCH MULTIPLE OCCURENCE
  grep '[e|x]hci'

* ARGS
                -n              Show number lines
                -r              Recursive
                -i              Ignore sensitive case 
* EXTRACT ALL URL FROM file.html
    egrep -o 'https?://[^ ")]+' file.html

* PRINT ONLY THE THIRD LINE
     egrep -o 'https?://[^ "]+' file.html | sed -n '3p'

* SEARCH OCCURENCE IN PDF(RECURSIVE) 
                pdfgrep -nri 'emplace_back'
                
* SEARCH IN FILES 
                grep -nri "occurence" 

* SEARCH TWO DIFFERENT WORDS 
                egrep -w 'word|word2' <folder>

## FIND 
* SEARCH CASE SENSITIVE REGARDLESS 
            find /home/captainchris -iname file.txt

* SEARCH PATTERNS
            find /home/captainchris -name '*.mp3'
            
* SEND OUTPUT FROM COMMAND TO A FILE
        find /home/captainchirs -name *.mp3 > output.txt
            
* SEND RECURSIVELY FILE NAMED IndicatorApplet
                    find . -iname "IndicatorApplet*" -type f

* SEARCH OCCURENCE IN FILES
       find . -type f -print -exec grep -nri "wlr_layer_surface" {} \;   

## PATCH
        ## APPLY A PATCH 
                        `patch < dwm-systray.patch`

## ADD PERSISTENCE TO LIVE USB
      * Dependencies: 
             e2fsprogs-extra
             parted

      1. Transfert Image to USB
            `dd if=kali-linux...-live.amd64.iso of=/dev/sdd bs=4M`
      or
            `dd if=kali-linux...-live.amd64.iso of=/dev/sdd bs=4M status=progress`

      2. Run this folowing command in the term
            `end=7GiB
             read start _ < <(du -bcm kali-linux...-live.amd64.iso | tail -1); echo $start
             parted /dev/sdd mkpart primary ${start}MiB $end`

      * Or you can Create partition with fdisk
            fdisk /dev/sdd
                  Create New paritition   with n
                  Primary                 with p
                  <Return>                default: 3
                  <Return>                default:Next free sector
                  <Return>                default: last adressable sector
                  w                       Write and quit

      or simply with `fdisk /dev/sdd <<< $'n\np\n\n\n\nw'`

      3. Create Partition
           `mkfs.ext3 -L persistence /dev/sdd3
            e2label /dev/sdd3 persistence`

      4. Create configuration file
           `mkdir -p /mnt/
            mount /dev/sdd3 /mnt
            echo "/ union" > /mnt/persistence.conf
            umount /dev/sdd3`

## ADD USB PERSISTENCE WITH LUKS ENCRYPTION
  * Dependencies:
        cryptsetup

  1. Do step 1 and 2 

  2. Initialize the LUKS encryption 
       `cryptsetup --verbose --verify -passphrase luksFormat /dev/sdd3
        cryptsetup luksOpen /dev/sdd3 my_usb`

  3. Create the Partition 
        `mkfs.ext3 -L persistence /dev/mapper/my_usb
         e2label /dev/mapper/my_usb persistence`

  4. Create configuration File
        `mkdir -p /mnt/my_usb
         mount /dev/mapper/my_usb /mnt /my_usb
         echo "/ union" > /mnt/my_usb/persistence.conf
         umount /dev/mapper`

  5. Close encrypted channel
        `cryptsetup luksClose /dev/mapper/my_usb`

## DOXYGEN
  * GENERATE CONFIG FILE
    doxygen -g doxygen.conf

  * doxygen doxygen.conf 



