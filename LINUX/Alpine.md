# ---- [ ALPINE LINUX ]  
                                        
         <[../index.md]

## INFOS 
	/etc/apk/world												All installed pkg

## PACKAGE MANAGER
			apk add / del				Add or Delete a pkg 
			apk list				List pkg matching pattern
			apk search <pkg>			Search pkg by name or description
			apk search -v <pkg>			Show description about pkg search
			apk update				Update repository index
			apk upgrade				Install upgrades available from repos
			apk fix					Fix / Reinstalls / Upgrade without changing world
			apk policy										
			apk -vv info | sort			Show installed packages with -vv for description about package

## PKG
	alpine-sdk			Build tools and libs
	mandoc					Man page viewer
	man-pages				Corelinux man page
	docs						Get man pages for everything
	syslog-ng				Normal logs in /var/log
	lang						locale files

## CONSOLE FONTS
	All confonts are located /usr/share/consolefonts/
	
	
	* CHANGE FONTS
	  - Install terminus-font for this font
	  setfont /usr/share/consolefonts/ter-v14n.psf.gz
	
	 * CHANGE FONT PERMANENTLY
	 echo 'FONT=ter-v14n' >> /etc/vconsole.conf 

## CREATING PACKAGE 
	* RESOURCES:
		https://pkgs.alpinelinux.org/packages?name=libplist&branch=edge
		Example: [../RESOURCES/APKBUILD]

		Download PKG
		1. Get the URL from clone button → Download as ZIP (archive/refs/ahead/master.zip)
		2. Get URL from Released → Bottom the page download archives

MANPAGE → man APKBUILD

1. INSTALL ABUILD
	apk add abuild abuild-doc (for man APKBUILD)

* SPAWN PRIVATE / PUBLIC KEY FOR ABUILD
	abuild-keygen -a 				by default Store the file in ~/.abuild/
	* COPY the key to /etc/apk/keys/

2. PREPARE THE LOCATION TO BUILD PKG
	mkdir -p /var/cache/distfiles 
	chmod a+w /var/cache/distfiles

3. newapkbuild packagename

* INFO
 apkbuild-cpan		 simplifies the creation of perl package from CPAN
 apkbuild-pypi		 simplifies the generation of APKBUILD file from PyPi

 If you are creating a daemon package which needs init script
 `newapkbuild -c pkgname`

SUBPACKAGES is used to split into multiple packages ($pkgname-$pkgver-dev,$pkgname-$pkgver-doc...)
prepare() is used to patch package. Make sure you have default_prepare declared

* if the package doesn't have a check phase.
	Add to APKBUILD `options="!check"`

* FILL INFORMATION ABOUT PKG
			(see manpage) → man APKBUILD

* GENERATE CHECKSUM
			abuild checksum

* BUILD PKG
			abuild -r
## EXTRACT COMPILED PKG
	apk fetch alsa-lib
	tar -xvf alsa.lib.apk

## MYSQL
	apk add mysql mysql-client mariadb-connector-c-dev
	mariadb-connector is necessary for mysql_config script 
	needed for flask_mysqldb
	
	* SETUP MARIADB 
	    /etc/init.d/mariadb setup
	
	* START THE SERVER
	    /etc/init.d/mariadb start

	* SECURE INSTALLATION
	    mysql_secure_installation
	    after that run:  rc-service mariadb restart

	* DEFINE USER
	    run mysql(root)
	      create user 'cbtech' identified by 'pass1234'
	    RUN AS ROOT
	      run mysql(root)
	      alter user 'root'@'localhost identified by 'pass1234'

	* RUN MYSQL (as simple user).
	   	 mysql -u cbtech -p
	  * OR
		mysql -u root -p

