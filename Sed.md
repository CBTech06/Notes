# -----[ SED ] -----
                                                
              <[index.md]

## OPTIONS
	-n Quiet 
	-e script expression 
	-f script file 
	-s consider file as separate rather 
	-i edit file in place
	
## SUBSTITION
		sed 's/First/Second/' < oldFile > newFile
	  ### SED ON ECHO COMMAND
		
		echo "BOURGEOIS" | sed 's/BOURGEOIS/CACAPROUT/'

## USEFUL SED COMMANDS
* INSERT AT FIRST LINE IN FILE INT FILE YDOTOOL.c
	sed -i '1i\cland ydotoolc -o ydotool\n' ydotool.c

* Change simple occurence in file called startweston
  sed -i 's/weston/sway/' startweston

* Change all `plist` in ../../libplist/include/plist in all h files
  `find . -type f -name "*.[hc]" -exec sed -i 's#include <plist#include 
                                   <../../libplist/include/plist#' {} \;`

* Change without find
	`sed -i 's#include <curl#include <../../curl/include/curl' 
	         Source/WebCore/platform/network/ResourceError.h`

* Show all .h files
				`find . -type f -name "*.h" -print`
* Show All line containing #include in all .h files
				`sed -n '/#include/p' $(find . -type f  -name "*.h")`	
* Comment line number 88 with #define
				`sed -i '88 s*^*//*` dir/dir/file.h 

* Uncomment 
	 			`sed -i '88 s*//**` dir/dir/file.h

* COMMENT LINE CONTAINING SPECIFIC STRING 
				`sed -i '/<pattern>/s/^/#/g' file`

* UNCOMMENT IT:
				`sed -i '/<pattern>/s/^#//g' file`

## REPLACEMENT WITH SED 

* Change all <C> TO $cmd  AND ALL <T> in  ${text} in string:
		`sed -e "s/<C>/${cmd}/g;s/<T>/${text}/g;`

* Remove keywords in string:
		`sed -i 's/bad//g' ${string}`
			
