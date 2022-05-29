   <t5                                                     TILEMAP EDITOR                                                                     >
											



<t5Schematics>

 	|---------------------------------------------------------------|
	|File	View				                    WXMENUBAR		|
	|---------------------------------------------------------------|
	| |----------------------------------------|  |---------------| |
	| |				                           |  |		          |	|
	| |					                       |  |               |	|
	| |                                        |  |    TILE       |	|
	| |                                        |  |   WXPANEL     |	|
	| |	         MAP EDITOR	                   |  |---------------|	|
	| |	    WXPANEL + GRIDSIZER	               |         			|
	| |				                           |  |---------------| |
	| |				                           |  |	  TILE INFO   |	|
	| |					                       |  |   TEXTLABEL   | |
	| |----------------------------------------|  |---------------| |
	|		 WXFRAME 					                            |
	|---------------------------------------------------------------|
	|Statusbar show information  		WXSTATUSBAR	            	|
	|---------------------------------------------------------------|


<t5Create a structure:> touch {main.cpp,main.hpp,gui.cpp,gui.hpp,file.cpp,file.hpp,event.cpp,event.hpp}

<t5Create Window>

		<t6GUI.HPP:>
		
					```cpp
					#ifndef GUI_HPP	
					#define GUI_HPP

					#include<iostream>
					#include<wx-3.0/wx/wx.h>

					class GUI: public wxFrame
					{
						private:
						public:
							GUI(const wxString&);
					};

					#endif
					```
					
		<t6GUI.CPP:>
		
					```cpp
					#include "gui.hpp"

					GUI::GUI(const wxString& title):
						wxFrame(NULL,wxID_ANY,title,wxDefaultPosition,wxSize(1024,600))
					{
						Centre();
					}
					```

		<t6MAIN.HPP:>

					```cpp
					#ifndef MAIN_HPP
					#define MAIN_HPP

					#include <wx-3.0/wx/wx.h>

					class wxMapEditor : public wxApp
					{
						public:
							virtual bool OnInit();
					};

					#endif
					```

		<t6MAIN.CPP:>

					```cpp
					#include "main.hpp"
					#include "gui.hpp"

					IMPLEMENT_APP(wxMapEditor)

					bool wxMapEditor::OnInit()
					{
						GUI *gui = new GUI(wxT("wxMapEditor"));
						gui->Show(true);

						return true;
					}
					```





<t5TODO>
- [ ] Drawing on Panel 
- [ ] Drawing my icon on panel
-







