# ---- [BASH SCRIPTING] ----

	<[../index.md]

* DEBUG				bash -x script
## CONFIGURATION

* LOAD BASHRC AUTOMATICALLY
	edit .bash_profile
```sh
	if [ -r ~/.bashrc ]; then
		source ~/.bashrc 
	fi
```

## VAR
* DECLARE VAR
	`declare -x nLine=1`

* INCREMENT VAR
```sh
	var=$((var+1))
	((var=var+1))
	((var+=1))
	((var++))

	let "var=var+1"
	let "var+=1"
	let "var++"
```

## ECHO & PRINTF
* PRINT VAR 
```sh
	var="10"
	echo "$var"
	printf "%s" "$var"	
```
 * ECHO ON MULTIPLES LINES 
```sh
	echo "full_text":"  $full_text",\
             "status_symbol":"$status_symbol",\
	     "time":"$time",\
	     "initial_time":"$initial_time",\
	     "incr":"$incr",\
	     "running":"$running"}
									```
 * PRINT CALCUL
```bash
	now () { date --utc +%s; }
	$((60 * 25 )) or $(($(now) + 60 * 25))
```

## FOR 
```bash 
			for i in $(cmd); do
				command
				done 
```
* FOR EACH LINE IN FILE
```bash
	for i in $(cat file.txt); do
		printf "%s\n" $i
	done
```
		
## WHILE

# ---- CONDITION ----

## IF / ELSE 
		-ge 			Greater or equal
		-le 			Less or equal
```bash
				var=1
				if [ "$var" == "1" ]; then 
			 		echo "blop"
				fi
```
* Else 
```bash
		if [ ${user_input} -ge 10 ] && [ ${user_input} -le 20 ]
		then
				echo "Great! The number is 
                      what we were looking for"
		else 
				echo "WRONG"
		fi
		```

## CASE
```bash
	 case "$BLOCK_BUTTON" in
			5) decrease ;;
			4) increase ;;
			3) stop ;;
			1) start ;;
			2) pause ;;
	  esac 
```
## INCREMENT / DECREMENT 
				((var++))

## FILE
	* Check if file exist 
```bash
	FILE="file.txt"
	if test -f "$FILE"; then
		echo "$FILE exists."
	fi
```

#  ---- ARRAYS ----
`array=(Hello World)`

`array[0]=Hello`							
`array[1]=world`

`${array[*]}`										All of the items in the array
`${!array[*]}`									All of the indexes in the array
`${#array[*]}`									Number of the items in the array
`${#array[0]}`									Length of item zero


## ADD AN ELEMENT TO THE BEGINING OF ARRAY
```bash
array=("new_element" "${array[@]}") 					
array=("new_element1" "new_element2" "..." "new_elementN" "${array[@]}")
```

## ADD AN ELEMENT TO THE END OF ARRAY 
```bash
array=( "${array[@]}" "new_element" )
array+=( "new_element" )

array=( "${array[@]}" "new_element1" "new_element2" "..." "new_elementN") 
array+=( "new_element1" "new_element2" "..." "new_elementN" )
```

##  ADD AN ELEMENT TO THE SPECIFIC INDEX 
```bash
array=( "${array[@]:0:2}" "new_element" "${array[@]:2}" )
```

## REMOVE AN ELEMENT FROM ARRAY 
arr=( "${arr[@]:0:2}" "${arr[@]:3}" )

* Explanation: Remove the element #3.
		 ${arr[@]:0:2} will get two elements arr[0] and arr[1] starts from the beginning of the array.
		 ${arr[@]:3} will get all elements from index3 arr[3] to the last.
							 

# ---- ESCAPE SEQUENCES ----

## COLORS
Black       0;30     Dark Gray     1;30
Blue        0;34     Light Blue    1;34
Green       0;32     Light Green   1;32
Cyan        0;36     Light Cyan    1;36
Red         0;31     Light Red     1;31
Purple      0;35     Light Purple  1;35
Brown       0;33     Yellow        1;33
Light Gray  0;37     White         1;37

## MOVEMENT	
* Position the Cursor(Cursor at line L 
   and column C): 											\033[<L>;<C>H or \033[<L>;<C>f 

* Move the cursor up N lines:		\033[<N>A
• Move the cursor down N lines:		\033[<N>B
• Move the cursor forward N columns:	\033[<N>C
• Move the cursor backward N columns:	\033[<N>D
 Clear the screen, move to (0,0):	\033[2J
• Erase to end of line:			\033[K
• Save cursor position:			\033[s
• Restore cursor position:		\033[u
																																		
ESC Code Sequence    Description
\033[H                moves cursor to home position (0, 0)
\033[{line};{column}H moves cursor to line #, column #
\033[{line};{column}f
\033[#A               moves cursor up # lines
\033[#B               moves cursor down # lines
\033[#C               moves cursor right # columns
\033[#D               moves cursor left # columns
\033[#E               moves cursor to beginning of next line, # lines down
\033[#F               moves cursor to beginning of previous line, # lines up
\033[#G               moves cursor to column #
\033[6n               request cursor position (reports as 033[#;#R)
\0337                 save cursor position (DEC)
\0338                 restores the cursor to the last saved position (DEC)
\033[s                save cursor position (SCO)
\033[u                restores the cursor to the last saved position (SCO)
			
# --- [ EXAMPLES] ---
## READ FILE LINE BY LINE AND STORE INTO ARRAY
```bassh
			 file="voc.txt"
			 while read -r line;do
			 l+=( "$line" )
			done < "$file"
 ```

## CMUS SCRIPTING
```bash
	INFO_CMUS=$(cmus-remote -Q 2>/dev/null)
	if [[ $? -eq 0 ]]; then
	INFO_TITLE=$(echo "${INFO_CMUS}" | 
            sed -n -e 's/^.*title//p' | head -n 1)
	INFO_ALBUM=$(echo "${INFO_CMUS}" | 
            sed -n -e 's/^.*album//p' | head -n 1)
	INFO_ARTIST=$(echo "${INFO_CMUS}" |
            sed -n -e 's/^.*artist//p' | head -n 1)
	else
		 exit
	fi

	if [[ "${INFO_ARTIST}" ]] && 
        [[ "${INFO_TITLE}" ]]; then
	
    OUT_TEXT="${INFO_ARTIST} - ${INFO_TITLE}"
	 elif [[ "${INFO_TITLE}" ]]; then
	 OUT_TEXT="${INFO_TITLE}"
	fi

	echo "${OUT_TEXT}"
	echo "${OUT_TEXT}"
	exit
												```
	
