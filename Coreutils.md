# ---- [ COREUTILS TOOLS ] ----#
	
	< [index.md]


   [Sed.md](Sed) 

## SEARCH TOOLS LOCATION
  `whereis` ls or `type ls`

## GET THE HASH OF MD5
* WITH CUT
  md5sum libplist-2.2.0.tar.bz2 | cut -d ' ' -f1 
* WITH AWK
  md5sum libplist-2.2.0.tar;bz2 | awk '{print $1}'

## CAT
 * WRITE MULTIPLE TEXT IN FILE
```bash
	cat << 'EOF' > fruit.txt
	banana		# ADD ENTRY
	papaya
	mango
	EOF  		# TO QUIT AND WRITE FILE
```
 * CAT WITH STDIN DATA
```bash
	echo 'apple bannana cheery' | cat
```
    
  * OPTIONS:    
    -b (with cat -n)  SHOW ONLY NON EMPTY LINES    
    -T                SHOW ALL TABS
    -E                SHOW ALL CR
    
  * UUOC (Useless Use Of Cut)
    * PREFER REDIRECTION
        cat greetings.txt | tr 'a-z' 'A-Z' 
        <greetings.txt tr 'a-z' 'A-Z

    * MATCH LINE CONTAINING '0' 'o'
        cat <file> | grep -n '[o0]'
        grep -n '[o0]' file1.txt file2.txt ...

   
## TR 
 * CONVERTS LOWERCASE TO UPPERCASE
```bash 
	tr 'a-z' 'A-Z' << 'end' > op.txt
	hi there
	have a nice day
	end
```

## CUT
* extract data src in <div class> line
   sed -n '/data-src/p' <file.html> | cut -f16 d='"'

```css
    <div class="episode"><div class="c-title"><h3>episode 1
        </h3></div>
    <div class="player"><iframe data-loader="iframe" 
    style="position:absolute; top:0; left: 0" width="100%" 
    height="100%" 
    data-src="https://uqload.com/embed-58lhvul8mgxy.html"
```

* FIELD AND DELIMITER
      - delimiter = " 
          cut -f1 -d'"' → <div class
              -f2       →  episode
              -f3       → ><div class=
              ...
