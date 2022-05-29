# ---- [ FILE IN C] ----

	< [../index.md]

## C/CPPREFERENCE:
  The doc for file are located under CPP_Reference/en/c/io

## FILE [OPEN/READ/WRITE]
  * fopen(filename,mode) returns a FILE pointer 
     to file filenamme which is opened using mode 
       r: open for reading(file must exist)
       w: open for writting(file need not exist)
       a: open for append ( file need not exist)
       r+: Open for reading and writing from begining
       w+: Open for reading and writting, overwritting file
       a+: open for reading and writing, appending to file

* WRITE FILE USING FWRITE
	< [../../Snippet/C/File_BinaryWrite.c]

 * BINARY FORMAT:
     ab: Append (file need not exist)
     wb: Ecriture de fichier
     rb+: Open for reading and writing from begining
     wb+: Open for reading and writing,overwriting
     ab+: Open for reading and writing appending to file

* READ FILE USING FREAD
```c
	int x[10]
	FILE *fptr;

	fptr = fopen("datafile.bin","rb");
	fread(x,sizeof(

```
## READ BY STRINGS
 * fgets(buff,n,fp):
     read n-1 character from the file pointed by fp and stores the string in buff.
     A null character \0 is appended as the last character in buff.
```c
	FILE *fptr;
	char buffer[200];

	fptr = fopen("myfile.txt","r");
	fgets(buffer, 20, fptr)
	printf("%s\n",buffer);
```

* READ CHAR BY CHAR


