# ---- [ VOIDLINUX ] ----


# [ XBPS MANAGER ]
   `xbps-install`       installs and update pkg
   `xbps-install -Su`   Update system

   `xbps-query`                 Searches for and display information about pkg
   `xbps-query  -Rs`            Search available repositories for pkg
   `xbps-query -o "*/gcc"`      List all gcc binary pkg
              -R                Search repositories 
               s                Search for locally-installed pkg
              -f                List files installed by pkg
              -l                List packages installed
              -o                List binary pkg

  * To get a list of all installed packages, without their version:
   `xbps-query -l | awk '{ print $2 }' | xargs -n1 xbps-uhelper getpkgname`

  `xbps-remove`                 Remove all installed pkg
  `xbps-reconfigure`            Run the configuration steps for installed pkg
  `xbps-reconfigure -fa`        Reconfigure All pakages

  `xbps-alternatives`  Lists or sets the alternatives provided by installed pkg
  `xbps-pkgdb`         Can report and fix issues in the package db 

* RECONFIGURE CERTIFCATES
    `xbps-reconfigure -f ca-certificates`

## DOWNGRADING 
   * Add the pkg version to your local repository:
      `xbps-rindex -a /var/cache/xbps/pkg-1.0_1.xbps`

   Then downgrade with xbps-install
      `xbps-install -R /var/cache/xbps -f pkg-1.0_1`

   The -f flag is necessary to force downgrade

## HOLDING A PKG 
   To prevent a pkg from being update during a system update
      `xbps-pkgdb -m hold <pkg>`

  The hold can be remove with:
      `xbps-pkgdb -m unhold <pkg>`

## REPOSITORY LOCKING PKG  
  * If you've used xbps-src to build and install a pkg from a customized
  template. You may wish to prevent system update for this pkg
      `xbps-pkgdb -m repolock <pkg>`

* To remove the repolock
      `xbps-pkgdb -m repounlock <pkg>`

## IGNORING PKG 
  Sometimes you may wish to remove a pkg whose functionality is being
  provided by another pkg.Example: You may wish to use doas instead sudo
  but will be unable to remove the sudo pkg due to its dependencies.
  To remove it, you will need to ignore the sudo pkg

## VIRTUAL PKG 
  Virtual pkg can be created with xbps.d virtual pkg entry.
  For example , to create linux virtual package which will resolve 
  to the linux-5.6 pkg, create and xbps.d configuration file
  with the contents
             `virtualpkg=linux:linux5.6`

## TROUBLESHOOTING

  [reposync] failed to fetch file https://alpha.de.repo.voidlinux.org/current/aarch64/aarch64-repodata': Operation not permitted
    * TIME AND DATE not configured
      enable chronyd service → ln -s /etc/sv/service /var/service
  
