#  FLTK PROGRAMMING 

    <[index.md]

## BUILD
  g++ -g -fpermissive Adjuster.cpp -lfltk -o Adjuster
  fltk-config --compile --cflags --cxxflags --ldflags Adjuster

  * Build Fl_PNG_Image ;)
  g++ -g -Wall  PNG.cxx  -lfltk -lfltk_images -lpng $(fltk-config --ldflags) -o Fl_PNG
  g++ -std=c++17 -fpermissive boxpicture2.cxx -lfltk -lfltk_images -lpng $(fltk-config --ldflags) -o BoxPicture2

## WIDGET
  Fl_Group widget class         Base container class to group the widgets
  Fl_Double_Window              A double-buffered window on the screen
  Fl_Gl_Window                  An OpenGL Window on the screen
  Fl_Pack                       A collection of widgets that are packed into the group
  Fl_Scroll                     A Scrolled Window area
  Fl_Tabs                       Display child widgets as tabs
  Fl_Tile                       A tiled window
  Fl_Window                     Window on the screen

  * You cange change size / position by using position(), resize(), size()

## COLORS [P.103]
  FL_BLACK / FL_RED / FL_ GREEN / FL_YELLOW/ FL_BLUE / FL_MAGENTA
  FL_CYAN / FL_WHITE 

  FL_FOREGROUND_COLOR FL_BACKGROUND_COLOR / FL_INACTIVE_COLOR / 
  FL_SELECTION_COLOR 

  Fl_Color c = fl_rgb_color(85,170,255);          // RGB to Fl_Color
  Fl::get_color(c,r,g,b);                         // Fl_Color to RGB

 ## CHANGING WINDOW BACKGROUND THEME
  Values are located instead 0(FL_BLACK) to 255(FL_WHITE) 
  Fl::background(100,100,100);
 
 ## TYPES [P.104]
  All box types is an enumeration defined in Enumerations.H
  Fl_Boxtype fl_down(Fl.Boxtype b)               returns "pressed" or "down version of the box.
  "      fl_frame(Fl.Boxtype b)
 
## CALLBACKS [P.109]
  A Callbacks are functions that are called when the value of a widget changes.
```cpp     
        // Callbacks takes fl_widgets* and void *data
        button1.callback([] (Fl_Widget* sender, void* window) {
```
