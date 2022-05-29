   <t5                                         DOCUMENTATION                                                              >
   
   
                        [GO BACK](index.md) 
   
		1. <t0 When an application fails>
		
				Run it from the command line.
				
				The folowing command find the name of executable in package
				for f in `pacman -Ql packagename | grep "/bin/" | cut -d" " -f2`; do file $f 2>/dev/null | grep -q executable && basename $f; done
			
		2. <t0Segmentation faults>
				
				gdb appname
				r (wait for the segfault)
				bt full 
				Now pots the output to a Pastebin client and include the URL in your bug report
			
			
				Recompile the application in question with <t0 -g -O0 -fbuiltin> flags.Make sure "!strip" is in the options array 
				in the PKGBUILD, then install the package and run it again with gdb.
				
				This is what the options line can look like: 
						
						options=('!strip')
						
				Put these two lines at the very begining of the build() function of PKGBUILD:
				
						export CFLAGS="$CFLAGS -O0 -fbuiltin -g"
						export CXXFLAGS="$CXXFLAGS -O0 -fbuiltin -g"
						
				Use core file with GDB:
				
						gdb appname core
						bt full
					
		3. <t0Valgrind>															5. <t0Readelf>
										
				usage:	valgrind appname												If you get "no such file or directory when running App
						valgrind --tool=callgrind appname								
						
		4. <t0Strace>																				readelf -a /usr/bin/appname | grep interp
				
				For finding which files a program named appname tries to open			Get app information:
				
						strace -eopen appname														file appname
						
				If you wish to grep the output from strace:
				
						strace -o /dev/stdout appname | grep string
						
				
		
