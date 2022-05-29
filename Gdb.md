# [GDB HOW TO]

		<[index.md]

## RUN WITH COMMANDLINE ARGS
	cgdb wofi
		r --show run

 * DEBUG RUNNING PROCESS(DAEMON/SERVER)
    ps ax | grep ydotoold	→ Returns 567 as PID
    cgdb -p 567 or 
    cgdb → attach 567 
	
 - ptrace operation not permited
     Solve this temporary, do the command below:
      echo 0 > /proc/sys/kernel/yama/ptrace_scope

     Solve permanenly, edit /etc/sysctl.d/10-ptrace.conf
      kernel.yama.ptrace_scope=0

      or simply run cgdb as root user
    
      
## SFML DEBUG
			
* 	Put a BP on sf::Keyboard::isKeyPressed(sf::Keyboard::Up)
			if sf::Keyboard::isKeyPressed(sf::Keyboard:Up)
				
* 	TODO:
		Didn't find mov DWORD PTR [esp] to show hello world ... P35
		Try to repere in ASCII CODE  Hello word 
		
	[Asm.md](Assembler code SRC)

## TOOLS COMMAND 
	objdump -D a.out | grep -A20 main.
	strings ./executable																			List all strings in executable

## GDB COMMANDS
* 	Set intel instruction. Put set disassembly intel in .gdbinit
  		disassemble main																			List ASM instruction	
  		list main 																						Show main function
			x																											Display the memoru contents
  		info register																					Shwo all Register informations
			info register edi(i r edi)														Show informations about edi

* 	SHOW INFORMATION ABOUT
         x/o 	   Octal information
	 x/u	   unsigned information
	 x/t	   Binary information
	 x/i $rip  Show instruction pointed by eip
			x/3i 																									Show 3 instructions
	
*		Unity Size	
			/b																										Octet
			/h																										Half Word (2 octets)
			/w																										Four Words (4 octets)
			/g																										DWORD(8 octets)
 
*  	Tips:
  		echo $((0x15a))
 			printf '%d\n' 0x15a																	Show binary value(346)
		
*  TUI
 		layout asm																						Show ASM code
		layout src																						Show SRC code

## REGISTERS (Internal processor var)
*		General register
			RAX,RCX,RDX,RBX				
* 	Index / Pointers
			RSP,RBP,RSI,RDI	
*		Instruction Pointer
			RIP										
*		32 Bits register version	
			ebp,eip,esp						32bits register
*		64 Bits 
			rbp,rip,rsp 					64bits register version

## ASM INSTRUCTIONS 

	$RIP					contains the value in RIP

* 	For loop in x86
			mov DWORD PTR[ebp-4], 0x0																Copy 0 in ebp-4
			cmp DWORD PTR [epb-4], 0x9															Compare ebp-4 to 9
			jle 0x00.......																					Jump if less or equal
			jmp																											Else jump to this addr

## CHECK POINTER WITH GDB
	char *pointer = str_a

*	 View pointer Information
	 		x/xw pointer										0x7fffffffe5f0: 0x6c6c6548 string is located at 0x7fffffffe5f0
			x/xw &pointer										0x7fffffffe5e0: 0xffffe5f0 
			x/s	pointer											Show string `Hello World`
			print &pointer									$1 = (char **) 0x7fffffffe5e0
			print *pointer

# ---- [ HOW TO DEBUG PROCESS ] ---- 

## WHEN AN APPLICATION FAILS
	   Run it from the command line.
	   The folowing command find the name of executable in package
 
 		for f in `pacman -Ql packagename | grep "/bin/" | cut -d" " -f2`; 

 		 		do file $f 2>/dev/null | grep -q executable && basename $f; 
 		done
		
## SEGMENTATION FAULTS 
	gdb appname
		`r` (wait for the segfault)
		`bt full` 
		Now pots the output to a Pastebin client and include the URL in your bug report
		Recompile the application in question with <t0 -g -O0 -fbuiltin> flags.Make sure "!strip" is in the options array 
		in the PKGBUILD, then install the package and run it again with gdb.
		This is what the options line can look like: 
						`	options=('!strip')`
		
Put these two lines at the very begining of the build() function of PKGBUILD:
		`export CFLAGS="$CFLAGS -O0 -fbuiltin -g"`
		`export CXXFLAGS="$CXXFLAGS -O0 -fbuiltin -g"`
						
Use core file with GDB:
		`gdb appname core`
		`bt full`
					
## VALGRIND 														
   usage:	`valgrind appname`					
	      	`valgrind --tool=callgrind appname`								
						
## STRACE 																			
	* For finding which files a program named appname tries to open			
				`strace -eopen appname`													
						
	* If you wish to grep the output from strace:
				`strace -o /dev/stdout appname | grep string`

## READELF ##
    * If you get "no such file or directory when running app
				`readelf -a /usr/bin/appname | grep interp`
		
 
