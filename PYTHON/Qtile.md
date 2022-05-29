# ---- [ QTILE ] ---- 
                                        
      <[../index.md]

VOC:
    layout = window agency
    groups = workspace 

## LOG 
    ~/local/share/qtile.log

### CREATE SCREEN

```python
     main_screen = Screen(bottom=main_bar)
     screens = [main_screen,secondary_screen]
```

### CREATE BAR
```python       
    main_bar = bar.Bar(
    [
        widget.GroupBox(),
        widget.Prompt(),
        widget.WindowName(),
        widget.Chord(
            chords_colors={
                'launch': ("#ff0000", "#ffffff"),
            },
           name_transform=lambda name: name.upper(),
        ),
        widget.Systray(),
        widget.Clock(format='%Y-%m-%d %a %I:%M %p'),
        widget.QuickExit(),
        widget.CurrentLayout(),
    ], 24, background="#282C34",foreground="#999999")
```

