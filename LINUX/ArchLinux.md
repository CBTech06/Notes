# ---- [ ARCHLINUX ] ---- #

               < [index.md]
                
## PACMAN 
        ## INSTALL OFFLINE DOC ##
                pacman -S arch-wiki-docs
                
   ## LIST FILES OF INSTALLED PACKAGES ##
                pacman -Ql <pkg>
                
  ## LIST ALL INSTALLED PACKAGES ##
                pacman -Qqe 
        
  ## SHOW PACKAGE INFORMATIONS ##
                pacman -Si <pkg>
                
  ## REMOVE PACKAGE WITH HIS DEPENCENCIES ##
                pacman -Rns <pkg>
        
  ## INSTALL PACKAGE FROM FILES ##
                pacman -U pkg.tar.xz
                
  ## LIST MANUALLY INSTALLED ##
                pacman -Qm
                
        ## DOWNLOAD PACKAGE WITHOUT INSTALL ##
                pacman -Sw <pkg>
        
        ## CLEAR CACHE ##
                pacman -Scc
                
        ## SEE FILE OWNED BY PACKAGE ##
                pacman -Qo /usr/lib/libGLX.so 
        
        ## INSTALL DKMS MODULE ##
                dkms install nvidia/340.106 -k 4.4.46-lts
                
                * Change version number of nvidia and kernel 
                
# -- [ NOUVEAU VIDEO DRIVER] -- #

        ## INSTALL DRIVER AND DEPENDANCIES ##
                sudo pacman -S xf86-video-nouveau 
                               libglvnd linux-firmware mesa
                               mesa-vdpau
                               libvdpau-va-gl
                               vdpauinfo ( For informations)
                
## VERIFY INSTALLATION #
     
     glxgears                   pkg: mesademos
     DRI_PRIME=1 to run application on the nvidia-gpu
     mpv --gpu-context=help                         Show different context
     mpv --gpu-api=help                             Show different API

     ffmpeg -hwaccels                               Show different hardware acceleration methods           glxgears 
               
        ## URLS ##
                
                https://wiki.archlinux.org/index.php/Hardware_video_acceleration
                
# -- [ SYSTEM LOG] -- #
        
        ## CLEAN JOURNAL FILES ##
                journal --vacuum-size=100M
                
        ## SHOW ALL MSG FROM THIS BOOT ##
                journalctl -b                           :current:
                journlactl -b1                          :previous:
                
        ## SHOW ALL MSG BY UNIT ##
                journal -u vlc
                
        ## SHOW ONLY CRITICAL / ALERT MSG ##
                journalctl -p err..alert
        
# -- [SYSTEM SERVICES] -- #

        ## LIST ALL SERVICES ##
                systemctl list-unit-files
                
# -- [ PKGBUILD ] -- #
                
        ## PROTOTYPE ## 
                /usr/share/pacman/PKGBUILD.proto 
                
                epoch:		Used to force the package seend as newer than any previous version with a lower epoch.

                * Example:		1:5.13-2
                pkgver=5.13
                pkgrel=2
                epoch=1

## KEY MANAGEMENT
* ARTIX EXTRA REPO
        pacman -S artix-archlinux-support
        pacman-key --populate archlinux

