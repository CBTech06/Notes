# ---- [ FFMPEG VIDEO EDITING ] ----

## ARGS 
    -f x11grab                      Record from screen
    -s 1280x1024                    Record Size
    -r 30                           Frame per second
    -f pulse/alsa                   Record audio from pulse or alsa
    -i default                      Uses delfault input device for recording
    -c:v libx264                    Setting Video Codec
    -c:a flac                       Setting Audio Codec
    -y                              Overwrite output file

## LIST CODECS 
   ffmpeg -codecs | grep mp3
   ffmpeg -encoders 
   ffmpeg -decoders 
   ffmpeg -formats 
   ffmpeg -h encoder=libx264         Show details about encoder

## TRANSFORM ALL MP4/M4A IN MP3 ##
```sh
     for f in *.mp4;
        do ffmpeg -i "$f" -q:a 0 -map a "Output/${f%.mp4}.mp3"
     done
```
```sh
    for f in *.mp4;
       do ffmpeg -i "$f"  -c:a libmp3lame "Output/${f%.m4a}.mp3"
    done

                
```
## RECORD A WEBCAM ##
                ffmpeg -y -i /dev/video0 output.mkv

## RECORD DESKTOP AND AUDIO AT THE SAME TIME 
```sh
                ffmpeg -y -f x11grab -s $(xdpyinfo | grep dimensions | awk '{print $2;}') \
                -i :0.0 \
                -f alsa -i default \
                -c:v libx264 -r 30 -c:a libmp3lame $filename 
```

