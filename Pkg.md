# ---- [ PACKAGES ] ----

   <[index.md]>

### ANT
   1. Export JAVA_HOME 			 export JAVA_HOME=/usr/lib/jvm/java-11-openjdk
   2. Build 				 ./build.sh
   3. Add and home to PATH		 export PATH=$PATH:/home/captainchris/Downloads/Github/ant/dist/bin


# ---- [ BUILDING ] ----

   * Add directory to PATH: export PATH=$PATH:$(pwd)

   Install library in opt
      ./configure --prefix=/opt --libdir=/opt/lib

## CMAKE
   * Build pkg using CMAKE
      1. Create build dir with mkdir Build and cd Build
      2. cmake ../

   * Second method (Building webkitfltk fifth browser)
      
        [X] make -C Source/bmalloc/bmalloc
        [X] make -C Source/WTF/wtf
        [X] make -C Source/JavaScriptCore gen
        [ ] make -C Source/JavaScriptCore
        [ ] make -C Source/WebCore
        [ ] make -C Source/WebKit/fltk

## PKG-CONFIG

   * MULTIPLE DEFINITIONS:
      pkgconfig --cflags gtk4 webkit2gtk-5.0 x11
   
   * Build PKG with Library not installed in /usr/lib
    1. Extract package / configure / make 
    2. Find the directory where the file .pc is 
    3. Add directory to PKG_CONFIG_PATH

   Example: `export PKG_CONFIG_PATH=$PKG_CONFIG_PATH:/home/captainchris/Downloads/Github
                                     /webkitgtk-2.4.9/libsecret-0.9/libsecret/`

   * Add Directory to pkg-config:
   Path to the .pc file
     `export PKG_CONFIG_PATH=~/Downloads/Github/webkitgtk-2.4.9/geoclue-2.5.7/
                               json-glib/build/meson-uninstalled/`

   Verify with `pkg-config --list-all | grep json-glib`

   * Add INCLUDE Directory:
      export C_INCLUDE_PATH=<directory>               For C
      export CPLUS_INCLUDE_PATH=<directory>           For C++
      example: 
         export C_INCLUDE_PATH=~/Downloads/Github/PHONEHACK/libplist/include/
      or make -I/directory/

   * Add LIBRARY Directory:
      export LD_LIBRARY_PATH=<directory>
      export LDFLAGS='-L/home/captainchris/download/dir'

   * Add Multiple Library Dir:
        ./configure LDFLAGS="-L/home/captainchris/Downloads/Github/fifth/urlmatch/ -L/home/captainchris/Downloads/Github/fifth/physfs/Build/"
        ./configure LIBS="-L/usr/lib/python-lib"
        export libplist_LIBS="~/Downloads/Github/PHONEHACK/libplist/src/"

## LD LINKER

## MESON BUILD
   1. Add Meson directory to PATH 
   2. Create Build dir to the package directory. Go to build directory 
   3. `meson.py ../`

   * Configure with meson
      meson configure --help 
  
   * EDIT  meson_options.txt file to configure option
	set true or false the correct options
   Or specify -Dimage-hpeg=false on the meson commandline

   meson build/ --prefix=/usr --libdir=/usr/lib --sysconfdir=/etc
   ninja -C build/
   su -c "ninja -C build/install"

* TROUBLESHOOTING
   Compiler cc  can not compile programs
     install libc6-dev

## AUTOCONF
				
   * aclocal manage m4 files
			
   > IF BUILDING FROM GIT
	autoreconf -fi
										
   * REBUILD WITH NO WARNING MSG
 	autoreconf -I --force -Wall,no-obsolete -I/usr/share/aclocal
				
   * AC_PROG_LIBTOOL ERROR
	Install pkg libtool
	Check if /usr/share/aclocal/libtool.m4 is present
										
## CONFIGURE ERROR 

   * syntax error: unexpected word (expecting ")")
					
   Change this: 	AX_PYTHON_MODULE(jinja2, needed, python3)
	to:		AX_PYTHON_MODULE='jinja2, needed, python3'

### XORG
	https://gitlab.freedesktop.org/xorg/lib/libxscrnsaver.git
								

### SHOW VAR INFORMATION	
   pkg-config --variable=datarootdir gnome-doc-utils

## GLIBC WITH MUSL LIBC
   * Avoir error with stdio.h
      copy stdio.h in glibc/include/

# ---- [USEFUL NOTES ] ---- 
 GConf: System used by the GNOME for storing configuration settings for the
 desktop and applications. It is similar to the Windows Registry.
 DEPRECATED since GNOME3. Remplacement GSettings/dconf

## ALSA-LIBS ALSA-UTILS
* BUILDING ALSA-LIBS
     ./configure --disable-ucm

* BUILDING ALSA-UTILS
   ./configure --disable-nls 
   To avoid undefined reference get_text libintl
   
 ## MPV
 ./waf configure  --disable-lua --disable-javascript --disable-android --disable-tvos \
    		  --disable-egl-android --disable-zimg --disable-libbluray \
		  --disable-uchardet --disable-rubberband --disable-vapoursynth \
		  --disable-libarchive
	
## JAVA 
   libswt http://sourceforge.net/projects/libswt
   JNI:

