   <t5                                                     TILEMAP EDITOR PART3                                                                     >
											



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


<t1Create a structure:> touch {main.cpp,main.hpp,gui.cpp,gui.hpp,file.cpp,file.hpp,event.cpp,event.hpp}

		<t4 * drawPanel Tutorial part1 * >
		
						```cpp
						class drawPanel: public wxScrolledWindow
						{
								private:
										
								public:
								drawPanel(wxWindow* parent);
								void setSize(wxSize);
								void OnPaint(wxPaintEvent& event);

						};
						```
		 * No difficulties just create simple class drawPanel
		
			And in GUI Class Declare drawPanel* mainpanel
			and implement in the GUI constructor:
			
						```cpp
						mainPanel = new drawPanel(borderPanel);
						mainPanel->SetBackgroundColour(wxColour(wxT("#888888")));
						```
					
		    Add it to createGUI:
			
						```cpp
						hbox->Add(mainPanel,3,wxEXPAND|wxALL,10);
						```
		<t4 * Implement MAP in Panel * >						
		     Load Map by file -> Open 
			 			```cpp
						
						      void GUI::OnLoad(wxCommandEvent& WXUNUSED(event))
						      {
							  wxString s_dir,s_file;
							  wxFileDialog dialog(this,"Open a file",wxEmptyString,
								      wxEmptyString,wxString::Format("All files (*.*)|*.*|Text Files (*.txt)|*.txt|XML files (*.xml)|*.xml"));

							  dialog.ShowModal();

							  wxString filename = dialog.GetPath();

							  m.loadXML(filename);
							  mainPanel->showMap(); 
						      }
						   ```												      
	    
		      Same as load map see in the previous tutorial, load and show map in panel like this 
		      
		      Add 3 int to drawPanel srcIDX sX and sY
		      
						   ```cpp 	      
						      void drawPanel::showMap()
						      {
							      Bind(wxEVT_PAINT,&drawPanel::OnPaint,this);
						      }

						      void drawPanel::OnPaint(wxPaintEvent& WXUNUSED(event))
						      {
							  if(!init) {
							      m.loadXML("resources/map1.xml");
							      init = !init;
							      }
						       
							      wxBitmap tileset("resources/levelgridless.png");
							      wxBitmap r01;
							      wxPaintDC dc(this);
							 
							      for(int x=0; x < NB_TILE_WIDTH; x++)
								  for(int y=0; y < NB_TILE_HEIGHT ;y++)
								  {
								      srcIDX = m.getData(y * NB_TILE_WIDTH + x);
								      
								      sX = srcIDX % (tileset.GetWidth() / TILESIZE) * TILESIZE;
								      sY = srcIDX / (tileset.GetHeight() / TILESIZE) * TILESIZE;
								  
								      r01 = tileset.GetSubBitmap(wxRect( sX, sY, TILESIZE, TILESIZE));
								      dc.DrawBitmap(r01,wxPoint(x * TILESIZE,y * TILESIZE));
								  }
						      }
						      ```cpp 

		      
		
		
						








