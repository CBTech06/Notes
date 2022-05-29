# ---- [ DRACUT ] ----
	
					< [index.md]

# [ DRACUT ] 
 MANPAGES
 ---------       
   dracut 
   dracut.cmdline        ->      All Kernel command line option
   dracut.conf(5)

## FILES

   All modules are listed in /usr/lib/dracut/dracut.conf.d/

   /var/log/dracut.log             Logfile of initramfs image creation
   /etc/dracut.conf                Configuration file for dracut 

   /etc/conf.d                     Any files found in /etc/conf.d will be sources in the initramfs to set initial values
   /etc/cmdline                    Can contain additional command line options[DEPRECTAED]
   /etc/cmdline.d/*.conf           Can contain additional command line options

## USAGE

   dracut   <image> <kernel version>      If no kernel version is specified dracut use current kernel image
        --force                        use if the image is already created.
        --hostonly or -H               Create image only with dracut module kernel module and filesystems

   dracut foo.img 2.6.4-1                  Create custom img for specific kernel
   dracut --kver 2.6.4                     Specify kernel version
   dracut --modules "module1 modul2"       list of modules to build initramfs
   * All modules are listed in /usr/lib/dracut/modules.d

   dracut --drivers "kmodule1 kmodule2"    Add list of kernel modules 
   dracut --omit-drivers   "kmodule1 kmodule2"     List to kernel module not to add to the initramfs
   dracut --host-only                              Install only what is needed for booting the local host
   dracut --fstab                                  Use /etc/fstab instead /proc/mountinfo
   dracut --mount "<device> <mountpoint> <filesystem type>  Mount device in initramfs
   dracut --install "/bin/foo /sbin/bar"           Install files in initramfs
   dracut --stdlog <level>                         Specify log level 

   Level: [0-6]:
     0. suppress any messages
     1. only fatal errors
     2. all errors
     3. warnings
     4. info
     5. debug info
     6. trace info

    dracut --regenarate-all                          Regenerate all initramfs imagewith kernel versions found on the systems.
    dracut --loginstall <dir>                        Log all files installed to <dir>

## LIST DRACUT IMAGE CONTENT
        `lsinitrd | less`                         To see the content created by dracut

## ADDING MODULE
        `dracut --add bootchart initramfs-bootchart.img`
         dracut --list-modules                   To list all modules
## ADDING KERNEL MODULE
        `dracut --add-drivers mymod initramfs-with-my-mod.img`

## OMITING DRACUT MODULE
        `dracut -o "multipath lvm" no-multipath-lvm.img`

  Or add to :/etc/dracut.conf:
        `omit_dracutmodules="lvm raid ... " `

## SPECIFYING ROOT DEVICE
   Add this to :/etc/dracut.conf:
        `root=rd.driver.blacklist=r8169`

   Print informations:
        `dracut --print-cmdline`

## TROUBLESHOOTING
   1. Remove rhgb and quiet from the kernel command line
   2. Add rd.shell rd.debug log_buf_len=1M  to the kernel command line
   3. The file /run/initramfs/rdsosreport.txt contains all the logs 
      To save that ouput mount an USB Stick and copy taht file.
# [ DRACUT CONF ] 
## INFO:
   .conf files are read from /usr/lib/dracut/dracut.conf.d and /etc/dracut.conf.d
   `WARNING:` To override default filename the filename in /etc/dracut/conf.d 
    must have the same name

## ADD LIST TO DRACUT MODULES 
   add_dracutmodules+="<modules>"
   or
   dracutmodules+="<modules>"      This option forces dracut to only include 
                                   specified dracut modules.In most cases the
                                   add_dracutmudles option is what you want to use

   All modules are located in /usr/lib/dracut/modules.d

## OMIT DRACUT MODULES 
                omit_dracutmodules+="<modules>"

##  KERNEL MODULES 
   `driver+="<kernel module>"`          List of kernel modules to exclusively
                                        include in the initramfs.


   `add_drivers+="<kernel_modules>"`    List of kernel modules to add to 
                                        the initramfs

   `force_drivers+="<list of kernel modules>"`          same as add_driver but in this case
                                                        the driver is loaded early via modprobe

   `hostonly="{yes|no}"`                 Install only what is needed for booting 
                                         the local host instead of a generic host 
                                         and generate host-specific

   `use_fstab="{yes|no}"`                Use /etc/fstab instead of 
                                         /proc/self/mountinfo

   `ro_mnt="{yes|no"}"`                  Mount / and /usr read only 
   `kernel_cmdline="parameters"`         Specify default kernel cmd line parameters
   `stdloglvl="{0-6}"`                   Set logging to std error level
   `sysloglvl="{0-6}"`                   Set logging to syslog lvl
   `fileloglvl="{0-6}"`                  Set logging to file level

   `show_modules="{yes|no}"`             Print the name of the included modules to 
                                         std output during the build
