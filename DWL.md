# ---- [ DWL ] ----
  
  <[ Wayland.md ]>
## BUILDING
	* PKG NEEDED:	wlroots-dev libinput-dev
	
	Modification with new wlroots version:
		dwl.c:554 implicit declaration `wlr_layer_surface_v1_close`
							change `wlr_layer_surface_v1_close` with `wlr_layer_surface_v1_destroy`
		dwl.c:778 change `wlr_xdg_surface->configure_next_serial` to
							`wlr_xdg_surface->scheduled_serial`
		dwl.c:929/935:change `wlr_layer_surface_v1->client_pending` to
						  `wlr_layer_surface_v1->pending`

## STRUCT
  Arg:
  Button:
  
  Monitor:
  MonitorRule:
  Rule:

  render_date: Used to move all of data necessary to render a surface from the top-level

  Client:
  Decoration:
  Key:
  Keyboard:
  LayerSurface
  Edge:
  Layout:

## MACRO
```c
    MAX(A, B) ((A) > (B) ? (A) : (B))     //RETURN THE BIGGEST VALUE
        if A > B return A else return B
    MIN(A, B) ((A) < (B) ? (A) : (B))    // RETURN THE SMALLEST VALUE
        if A <  B return A else return B
    LENGTH(X) ( sizeof X / sizeof X[0])
    TAGSMASK ((1 << LENGTH(tags)) - 1)
```
## FUNCS
  - applybounds(Client *c, struct wlr_box *bbox)
      Adapt X / Y of client

  - cleanup(void)
       Destroy All surface to quit the programn. Free resources

  - cleanupKeyboard(struct wl_listener *listener, void *data)
        Free Keyboard struct.

  - cleanupmon(struct wl_listener * listener, void *data)
        Free Monitor struct.

  - createmon(struct wl_listener *listener, void *data)

  - setup(void)
        Create WAYLAND display server 
        Create renderer
        Create a cursor

  - spawn (const Arg *arg)
        Launch application in config.h(termcmd/dmenucmd...)  

  - tag(const Arg *agr)
        
