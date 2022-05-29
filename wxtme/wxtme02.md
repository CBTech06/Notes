

   																												# ---- [ TILEMAP EDITOR PART2  ] ---- #
											

	

 Add Menubar and Add File/View menu:

				6Add to the class GUI private attributes in gui.hpp:
						
						```cpp
						wxMenuBar* menubar;
						wxMenu* file;
						wxMenu* view;
						```
				<t6Add the methods below:>
					
						```cpp
						void addMenubar();
						void createGUI();
						void OnQuit(wxCommandEvent&);
						void OnLoad(wxCommandEvent&);
						void OnSave(wxCommandEvent&);
						```

<t5 Implement Menubar like this:>
		
	<t0All icons can be found at: https://docs.wxwidgets.org/trunk/page_stockitems.html >
					
					```cpp
					void addMenuBar()
					{
							menubar = new wxMenuBar;
							file = new wxMenu;
							file->Append(wxID_NEW,wxT("&New Map"));
							file->Append(wxID_OPEN,wxT("&Open file"));
							file->Append(wxID_SAVEAS,wxT("&Save as"));
							file->Append(wxID_EXIT,wxT("&Quit"));
							menubar->Append(file,wxT("&File"));
							view = new wxMenu;
							view->Append(wxID_JUSTIFY_LEFT,wxT("&Show Grid"));
							menubar->Append(view,wxT("&View"));
							SetMenuBar(menubar);
							Bind(wxEVT_COMMAND_MENU_SELECTED,&GUI::OnQuit,this,wxID_EXIT);
					}
					```
        
       <t5 Bind function:>
       
                template<typename EventTag , typename Class , typename EventArg ,typename EventHandler >
                          void  Bind (const EventTag &eventType, void(Class::*method)
                                (EventArg &), EventHandler *handler, int id=wxID_ANY,
                                int lastId=wxID_ANY, wxObject *userData=NULL)
                                See the Bind<>(const EventTag&, Functor, int, int,
                                wxObject*) overload for more info. More...
                                
                       <t6Explanation> 
                       
                                        evenType-> wxEVT_COMMAND_MENU_SELECTED
                                        eventArg-> &GUI::OnQuit
                                        eventHandler-> this
                                        id-> Not specified
                                        lastid-> Not specified
                                        wxObject *userdata=NULL
                                
                
        Functors: 
                Functors are objects that can be treated as though they are a function or function pointer.				
                
<t5 Implement OnQuit method:>
						
					```cpp	
					void GUI::OnQuit(wxCommandEvent& WXUNUSED(event))
					{
						Close(true);
					}
					```
					

<t5  Add statusBar to our wxFrame in the GUI constructor>
					
					```cpp	
					statusbar = this->CreateStatusBar(1,wxSTB_DEFAULT_STYLE,wxID_ANY);
					```	
					
<t5 Create function createGUI and implement it like this:>
	
					```cpp
					void GUI::createGUI()
					{
						addMenubar();
						
						Centre(wxBOTH);
					}
					```

