# ---- [ BASH TIME PROGRAMMING ] ----

    <[../index.md] 

# COMPARE TWO TIME HH:MIN
```bash 
OLD=13:19
NEW=12:36

TIMER_START=$(date -u -d "$OLD" +"%s")
TIMER_END=$(date -u -d "$NEW" +"%s")
TIMER=$(date -u -d "0 $TIMER_START sec - $EXPTIME sec" +"%M:%S")
```

## DIFF BETWEEN TWO TIMES
* Usage:
   Number of days between 2 date
      dateDiff -s "2006-10-01" "2006-10-32"
   Number of seconds between two times
      dateDiff  -m "17:55" "23:15:07"
   Number of minutes between two times
   from now until the end of the year
      dateDiff -m "now" "2006-12-31 24:00:00 CEST"

```bash
date2stamp () {
    date --utc --date "$1" +%s
    }

stamp2date() {
 date --utc --date "1970-01-01 $1 sec" "+Y-%m-%d %T"

  datediff(){
    case $1 in 
      -s) sec=1;
      -m) sec=60;
      -h) sec=3600;
      -d) sec=86400;
      *)  sec=86400;;
    esac

    dte1=$(date2stamp $1)
    dte2=$(date2stamp $2)
    diffSec=$((dte2-dte1))
    if ((diffSec <0)); then abs=-1; else abs=1; fi
    echo $((diffsec/sec*abd))
    }
```

