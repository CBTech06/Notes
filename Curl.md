# ---- [CURL HOW TO]
                                                
    <[index.md]                                             


# EXPLANATION

  * POST REQUEST
	POST is often used by WWW to send data to 
	the web server or when you upload a file.

  * GET REQUEST
	You can use this method only to retrieve data from
	the address bar in the browser

## RESOURCES 
  https://www.whiteoaksecurity.com/how-to-prepare-for-an-api-pentest-curl/
  http://jsonplaceholder.typicode.com/guide/
  http://httpbin.org
  http://httpbag.org
  https//reqbin.com
  https://github.com/iv-org/documentation/blob/master/docs/api.md

  List of userAgent: https://developers.whatismybrowser.com/useragents/explore/operating_system_name/macos/ 

  * TOOLS:
        html-xml-utils Pkg for webscrapping using CURL

  * TODO:
        Search youtube how to get width and height of each movies

## USERAGENT
    Mozilla/5.0(X11; Linux x86_64;rv:60.0) Gecko/20100 101 Firefox/81.0
    Mozilla/5.0(Macintosh; Intel Mac OS X 10_15_6) AppleWebKit/605.1.15(KHTML, like Gecko) Version/13.1.2 
    Safari/605.1.15

  - Example: curl -A "Mozilla/5.0(X11; Linux x86_64;rv:60.0) Gecko/20100 101 Firefox/81.0" \ 
                 https://www.yeah.com

## YOUTUBE SEARCH WITH CURL AND JSON
 
  curl https://www.youtube.com/results -s \
      -G --data-urlencode "search_query=cryptomonnaie" \
      -G --data-urlencode "sp=$sp"\
      -H 'Authority: www.youtube.com' \
      -H "User-Agent: $useragent" \
      -H 'Accept_language: en-US,en;q=0.9' \
      -L --compressed 

  * Minimal:
    curl https://www.youtube.com/results -G --data-urlencode "search_query=archlinux" 

  * See OPTION Section below to option signifaction

## ------------------------[ INVIDIOUS API ] --------------------------------
Hackersploit Curl Linux Movie Xy7fDxz39FM
HackerSploit ucid(User Channel ID): UC0ZTPkdxlAKf-V33tqXwi3Q

* GET ALL VIDEOS ABOUT CURL LINUX 
  curl https://yewtu.be/search?q=curl+Linux

* SEARCH USING PARAMETERS [../Snippet/CURL/curl_yewtubeSearch.json]
 curl -X GET -H "Content-type: application/json" -H "Accept: application/json"  "https://yt.artemislena.eu/api/v1/search?q=curl&duration=long&features=hd" >>

* OR USING --data-encode 
curl  -X GET -H "Content-type: application/json" -H "Accept: application/json" -G --data-urlencode "q=curl&duration=long&features=hd" "https://yt.artemislena.eu/api/v1/search"

* GET VIDEO INFORMATION (yewtube API) → [../Snippet/CURL/api_yewtube.json]
curl -X GET -H "Content-type: application/json" -H "Accept: application/json"   https://yt.artemislena.eu/api/v1/api/v1/videos/Xy7fDxz39FM >> api_yewtube.json

* GET PLAYLIST INFORMATION → [../Snippet/CURL/api_yewtube_playlist.json] 
curl -X GET -H "Content-type: application/json" -H "Accept: application/json"   https://yt.artemislena.eu/api/v1/channels/playlists/UC0ZTPkdxlAKf-V33tqXwi3Q >> api_yewtube_playlist.json

## POST REQUEST WITH JSON
```sh
	curl -X POST https://reqbin.com/echo/post/json -H "Accept: application/json" \
	     -H "Content-Type: application/json" --data-binary @- <<DATA
	{
 	 "Id": 78912,
  	"Customer": "Jason Sweet",
  	"Quantity": 1,
  	"Price": 18.00
	}
	DATA
```

## BASIC CMD
   * Make get request
     curl https://www.yeahhub.com/

   * Save file with default filename
      curl -O http://wwww.google.com/robots.txt

   * Save file with custom name
      curl -O http://wwww.google.com/robots.com file.txt

   *  Download multiple files
       curl url1 url2 url3

   * Download a range of files
        curl http://www.google.com/logo/logo[1-9].png

   * Upload a file 
        curl -T uploadFile http://upload.linuxhandbook.org/files

   * Avoid redirect 
        curl -L http://www.google.com

   * Authentication 
        curl -u username:pass http://seeni.linuxhandbook.org/

   * Ignore ssl certificates 
        curl -k https://url

   * Get header information 
        curl -i http://www.google.com/robots.txt

   * Change user agent 
        curl -A "Mozilla FireFox(42.0)" http://url.org

  * Post data to a server 
        curl -d "param1=value1&param2=value2" -H "Content-Type: 
                 application/x-www-form-urlencoded" -X POST 
                 http://localhost/data 

## BASIC OPTIONS(see manpage for more)
  --compressed
    Request a compressed response using one the algorithm
    and automatically decompress the content

  -G      --get
    This option will make all data specified -d 
    to be used in an HTTP GET request  

  -H      --header
    Extra header to include in the request when 
    sending HTTP to a server.

  -L      --location
     If the server reports that the requested 
     page has moved to a different location.
     CURL redo th request on the new place

## SHOW INFORMATION ABOUT CERTIFICATE EXCHANGE 
    curl -v https://postimages.org
