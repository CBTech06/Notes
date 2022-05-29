# ---- [ ALSA CONFIGURATION ] -----
                                        
                                        
   	<[index.md]
 
## LIST SOUNDCARDS
	aplay -L
							
## .ASOUNDRC
	 
  pcm.!default {
    type hw
    card 0
  }
													
  ctl.!default {
    type hw
    card 0
  }
					
## LIST ALL MODULES THAT USES SOUND
  fuser -v /dev/snd/*

  * If no sound in Kali, it its probably that pipewire
    and fluidsynth use sound

## START JACK 
   jackd -R -dalsa -D  -Chw:Adapter -Phw:MID
