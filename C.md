# ---- [ C99 PROGRAMMING LANGAGE] ----

	<[index.md]

## C99 GLOSSARY
    C99/Glossary.md
    C99/Make.md
    [C99/Pointers.md]
    [C99/Memory_Allocation.md](Malloc/calloc/realoc)
    [C99/File.md](fread)
    [C99/Bitwize.md](Bit Operation)

## PASS OPTION TO COMMANDLINE
   cc -shared -fPIC *.c -DBM_VERSION="command"

## MULTIPLE EXAMPLES IN SAME FILE
```c
	#if defined(EXAMPLE_1)
		printf("Example 1\n");
	#elif defined(EXAMPLE_2)
		printf("Example2\n");
	#endif
```	
	* BUILD: cc -g -Wall -w -DEXAMPLE_1 -o EXE

## CREATE LIBRARY
  * CREATE FILE .o
    gcc -c add.c
    gcc -c sub.c
  
  * CREATE LIB
  	c:create r: for replace s:for index
    ar crs libbasic add.o sub.o

## SYMBOLIC CONSTANTS
  #define LOWER 0

## PRINTF
 printf("%d", value)

 %d 		→ 	decimal integer
 %6d 		→	decimal integer , 6 character wide
 %f 		→	floating point
 %6f		→ 	floating , - char wide
 %.2f		→ 	floating point,2 char decimal point
 %6.2f		→	floating, 6 char wide and 2 after decimal point
 %o/%x/%c/%s	→ 	Octal,Hexdecimal,Character,String

## FOR LOOP
```c
	for (int i=0; i<= max; i++) {}
```
## READ FOR KEYBOARD INPUT 
```c
int c;

while (( c = getchar()) != EOF) {
	putchar(c);
	}
```

* MAP KEY
  #define CTRL_KEY(k) ((k) & 0x1f)
  if (c == CTRL_KEY('q')) break;

## POINTERS
```c
	char str_a[20];
	char *pointer;
	char pointer2

	strcpy(str_a,"Hello World!\n");
	pointer = str_a;
	printf(pointer);		// Hello World!
	pointer2 = pointer + 2
	printf(pointer2)		//llo World!
```

## TROUBLESHOOTING
	* Cannot find lssp-nonshared
		
	  gcc -v 2>&1 | grep -- '--disable-libssp'
	  gcc is build with --disable-ssp-nonshared.Recompile gcc or install clang

