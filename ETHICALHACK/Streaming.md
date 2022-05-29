# ---- [ STREAMING HACKZ ] ----


# HACKING YOOWOOSH
1. Get index page
      https://yoowootch.com/the-walking-dead/10

2. Extract links(in data-src) on embed video for season 10
 ` sed -n '/data-src/p' 10 | cut -f16 d='"' > embedS10`

3. Download each link for each episode
```sh
   declare -i nLine=1
   for i in $(cat embedS10); do
      curl $i -o S10e$nLine
      (($nline++))
   done
```

## DOWNLOAD MOVIE ON OPENLOAD

   1. Open devtool on QUTEBROWSER( SHORTCUT: wi)
   2. Go to Network section -> Media.
   3. Play the movie and copy the link in media 
   4. Download it with wget link

## IDENTIFY THE REQUEST
   1. Open WebInspector
   2. Go to Network

## DAFTSEX HACK
   * URL SERVER:  https://psv119-1.daxab.com/videos/<id>/<id2>/<res>.mp4
      Example     https://psv119-1.daxab.com/videos/-118334847/456239220/720.mp4

   1. Grab html responce from request
       curl  "https://daftsex.com/video/phoenix marie" >> output

       * Get second page:
       curl --request POST -d 'hd=0&sort=0&longer=0&page=2'
                  "https://daftsex.com/video/korra del rio" 

   2. Extract Video title from output:
        cat output | grep -i 'video-title' | cut -d ">" -f2 | tr -d "</div"
        
        TODO:
         curl request_payload hd=0&sort=0&longer=0&page=3
 
