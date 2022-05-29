# ---- [ FULL INSTALLATION WITH ENCRYPTION  ] ----

## RESOURCES 
  https://www.howtogeek.com/427982/how-to-encrypt-and-decrypt-files-with-gpg-on-linux/
  https//whhone.com/posts/arch-linux-full-disk-encryption

## ENCRYPT FILE USING gpg
  * GENERATE KEY FOR ENCRYPTION
    gpg --full-generate-key
  
  create file (example token) and copy informations into it 
  
  * ENCRYPT
  gpg --cipher-algo AES256 --symmetric token

  * You can now remove original file and keep only token.gpg
  
  DECRYPT:
    gpg --output token.gpg --decrypt token.gpg

## PKG NEEDED
	gptfdisk cryptsetup lvm2 
	e2fsprogs util-linux dosfstools

## BASIC METHOD
  1. FORMAT HD
	dd if=/dev/urandom of=/dev/sdX bs=1M	

  2. RUN CRYPTSETUP
	cryptsetup --verbose --verify-passphrase luksFormat /dev/sdx

  3. OPEN THE ENCRYPTED PARTITION
	cryptsetup luksOpen /dev/sdx sdx

  4. CHECK WHERE THE PARTITION IS MAPPED
	fdisk -l → /dev/mapper/sdx

  5. CREATE NEW FILESYSTEM
	mkfs.ext4 /dev/mapper/sdx

  6. REMOVE RESERVED SPACE
	tune2fs -m 0 /dev/mapper/sdx

  7. CLOSE ENCRYPTED DEVICE
	umount /dev/mapper/sdx			if sdx is mounted
	cryptsetup luksClose /dev/mapper/sdx

### MOUNT ENCRYPTED PARTITION
	1. OPEN ENCRYPTED PARTITION(STEP 3)
	2. mount /dev/mapper/sdx /media/eHD
	3. umount /media/eHD
	4. CLOSE ENCRYPTED DEVICE(STEP 7)
	
## INFORMATION ABOUT ENCRYPTED DEVICES
	cryptsetup luksDump /dev/sde

* INFORMATIONS ABOUT CRYPTO PROTOCOLS
	cat /proc/crypto

## FORMAT OLD PARTITION 
   PARTITION DISC USING GPTFDISK(ESP) FDISK

## ENCRYPT PARTITION(SPECIFIC ENCRYPTION) 
	cryptsetup luksFormat --type luksl 
	-c aes-xts-plain64 -s 512 --iter-time 
 	5000 --hash sha512 /dev/<sdb1>

	cryptsetup luksOpen /dev/<sdb1> enc_root

	pvcreate /dev/mapper/enc_root
	vgcreate /dev/mapper/enc_root

## CREATE TWO LOGICAL VOLUMES 16GB(SWAP)
         OTHER EXT4 PARTITION
       `If you don't use the same disc 
       it is not necessary to use LVM`

	lvcreate -L 16G lvm -n swap
	lvcreate -l 100%FREE lvm -n root

	mkswap /dev/lvm/swap
	mkfs.ext4 /dev/lvm/root

## MOUNT PARTITIONS
	mount /dev/sd<b2> /mnt -t ext4
	mkdir /mnt/boot/efi -p
	mount /dev/sd<b1> /mnt/boot/efi/

* TAKE NOTE OF THE UUID, IT WILL BE
   NEEDED FOR GRUB 
	blkid -s UUID -o value /dev/sd<b2>

## INSTALL SYSTEM
	ifconfig eth0 up
	udhcpc eth0
	setup-apkrepos
	setup-disk -m sys /mnt

## CHROOT ENVIRONMENT
	mount -t proc /proc /mnt/proc
	mount --rbind /dev /mnt/dev
	mount --make-rslave /mnt/dev
	mount --rbind /sys /mnt/sys
	
	chroot /mnt /bin/bash
	source /etc/profile
	
## INSTALL BOOTLOADER
	apk add grub-efi efibootmgr
	apk del syslinux

* EDIT /etc/default/grub 
```bash
     GRUB_DISTRIBUTOR="Alpine"
     GRUB_TIMEOUT=2
     GRUB_DISABLE_SUBMENU=y
     GRUB_DISABLE_RECOVERY=true
     GRUB_ENABLE_CRYPTODISK=Y
     GRUB_CMDLINE_LINUX_DEFAULT="cryptroot=
   	UUID=<blkid value> cryptdm=lvmcrypt 
	cryptkey"
    # cryptroot specifies which device to unlock
    # cryptkey indicates that a key exist 
    # at /crypto_keyfile.bin
    # cryptdm indicates the name of the 
    # encrypted disk mapping
     GRUB_PRELOAD_MODULES="luks cryptodisk 
        		      part_gpt lvm" 	
```

## GENERATE A RANDOM KEY AND ADDED IT 
       TO MY ENCRYPTED VOLUME
   dd bs=512 count=4 if=/dev/urandom 
	    of=/crypto_keyfile.bin
   chmod 000 /crypto_keyfile.bin
   cryptsetup luksAddKey /dev/sd<b2> 
                 /crypto_keyfile.bin

## SETUP INITIAL RAMDISK
 * EDIT /etc/mkinitfs/mkinitfs.conf
     features="ata base ide scsi usb 
              virtio ext4 lvm cryptsetup cryptkey"
	
 * CREATE INITRAMFS 
     mkinitfs -c /etc/mkinitfs/mkinitfs.conf 
     	$(ls /lib/modules/)

      grub-install --target=x86_64-efi 
      	  --efi-directory=/boot/efi	
      grub-mkconfig -o /boot/grub/grub.cfg

## SET PASSWORD (passwd)
## REBOOT THAT'S DONE
