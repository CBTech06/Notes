# ----[ PYTHON I3 SCRIPTING ] ---- 
                                
     < [../index.md]

## BUTTONS ##
```python
   import os
   if os.environ.get('BLOCK_BUTTON'):
       if (os.environ['BLOCK_BUTTON'] == '1'):
          btn = "BTN1"
       if (os.environ['BLOCK_BUTTON'] == '2'):
          btn = "BTN2"
       if (os.environ['BLOCK_BUTTON'] == '3'):
          btn = "BTN3"
       if (os.environ['BLOCK_BUTTON'] == '4'):
          btn = "BTN4"
       if (os.environ['BLOCK_BUTTON'] == '5'):
          btn = "BTN5"
```
