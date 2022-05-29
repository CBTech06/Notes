# ---- [PYGAME HOWTO) 
                         
                         
       <[../index.md]

## REF:  
  PYGAME C FILES : /usr/include/python3.9/pygame
  PYGAME: /usr/lib/python3.9/site-package/pygame 
  All events are listed in /usr/lib/python3.9/
                site-package/pygame/locals.py  

## LOAD IMAGE
```python
    def load_image(self,filename):
        return pygame.image.load(filename).convert()

        # CODE IN MAIN
        background = game.load_image('resources/Asset.png')
        screen.blit(background_img,screen_rect)
```
## CLEAR SCREEN WITH BLITSURFACE
    screen.fill(pygame.Color("black"),(0,0,10,10)
## DEFINE COLORKEY
```python
        # Black is now transparent 
        img.set_colorkey((0,0,0)
```
## KEYBOARD
```python
def event_manager(self):
    for event in pygame.event.get():
        if event.type == pygame.KEYDOWN:
            if event.key == pygame.K_ESCAPE:
                sys.exit()
            if event.key == pygame.K_LEFT:
                self.move("left")
```

## MOUSE 
    * GET POSITION 
```python
     #event.pos[0] = X event.pos[1] = Y
      if event.type == MOUSEMOTION:
          print (event.pos[0])
        if event.type == MOUSEBUTTONDOWN:
            printf("BTN CLICKED")
```

## LOAD SPRITESHEET         
```python 
     # imgRect is coordinate of picture in the spritesheet 
     imgRect=Rect(0,0,220,165)
     # initial.x/y is position x and y in the game
     screen.blit(img,(self.initial.x, self.initial.y),imgRect)

```
## SPRITE GROUP 
```python
                # CLASS MUST INHERIT TO SPRITE
                class Ship(Sprite):
                    def __init(self,ai_settings,screen):

                    """ INITIALIZE THE SHIP AT STARTING POSITION """
                    super(Ship,self).__init__()

                # CODE TO CREATE GROUP
                self.ships = Group()    # Create empty group
                for ship_number in range(self.stats.ships_left):
                    # CONSTRUCTOR CALL
                    ship = Ship(self.ai_settings, self.screen)

                    # POSITIONNING THE SHIP  
                    ship.rect.x = 10 + ship_number * ship.rect.width
                    ship.rect.y = 10

                    self.ships.add(ship) ### Add new ship to the group
```
