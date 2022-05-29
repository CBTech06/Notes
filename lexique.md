# ---- [ LEXIQUE ] ----

# ---- [ C PROGRAMMING ] ----
  ## ASSERT
    CPPRef: C/error.html

    The macro assert depends of NDEBUG macro
    which is not define in C library. 
    If NDEBUG is not defined then assert check its args
    compares equal à zero. if true assert output implementation
    sepcific to stdout and call abort.


# ---- [ WAYLAND ] ----
## INTERFACES
  When you run an XML file throught wayland-scanner
  it generates interface (which are analogous 
  to listener), and glue code for sending events.
  
  Interface are listed in wayland.xml
   EXAMPLE:
   	<interface name= "wl_surface" version="4">
	<request name="damage">
		<arg name="x" type="int">
	</request>

## SEAT
  A Seat is a collection of input devices that act independently of 
  other.

## LISTENER
  The server-side code for interfaces and listeners is identical, but reverse.
  It generate listeners for request and glue code for events.

## WL_REGISTRY
	The registry is used to allocate other objects

## WL_PROXY / WL_RESOURCES (Used for abstraction)
   An object is entity wich known to both the client and 
   the server.
	On the client side, libwayland refers to these objtecs 
	throught the `wl_proxy interface`.

	On the server, objects are abstracted throught wl_resouce.
	which is similar, but have an extra degree of complexity.
	The server has to track which object belongs to which client.

	Each wl_resource is owned by a signral client.

## GLOBALS 
	GlobalS are objects that provide information 
	and functionnality.They're used  to broker(negocier)
	additionnal objects to fulfill various purposes.
	
* BINDING TO GLOBAL:
  This process of taking a known object and assigining it 
  an ID is called binding the object

* REGISTERING GLOBALS:
  Registering globals with libwayland-server is done somewhat 
  differently

	
	
## SHELL (XDG-SHELLS)
	- Surface is a rectangular box of pixels sent from the client
		to the compositor.
	- Shells are how surfaces in Wayland are given.
	- XDG-SHELL encapsule every feature of a typical
	 	graphical desktop session in a single protocol.

### POPUP INTERFACE 
	is used to show "popup" window, which can be used for
	a variety of purposes(right click menus,tooltips)
  xdg_positionner (provided by xdg-shell) adjust
  the position and size of xdg_popup surfaces.
	
### LAYER SHELL
	The purpose of this shell is to provide an interface
	for desktops components like panels, lock screen, wallpapers
	on-screen keyboards, notifications to display on your compositor

## WLROOTS
WLROOTS is a module that provide backends 
	that abstract the underlying display and input 
	hardware, including KMS/DRM,libinput,Wayland,X11.
	
### SUBSURFACE(SUBCOMPOSITOR)
	The subsurface state describe the sub-surface relationship
	with its parents
### LIBSEAT
	Seat management take care of mediating access to shared device(Graphics/Input)
	without requiring the application needing access to be root
	
## INFOS:
	Unlike Xorg, Wayland implementation combine 
	the display server,
	WM and compositor in single application

### KMS (Kernel Mode Setting)
	KMS is a method for setting display resolution 
	and depth in the kernel space.

* intel/nouveau/ati/amdgpu enable KMS automatically
	KMS is initialized after the initramfs,
	to enable before add your videodriver to the 
	initramfs:

* video drivers:
	amdgpu,ati (for the old gen card), i915(intel)

* Edit /etc/mkinitcpio.conf
	MODULES=( ... i915 ...)

	For intel users, you need to add intel-agp before
	i915 to suppress ACPI error.

### DRM (DIRECT RENDERING MANAGER)
	 Kernel module that give direct hardware access
	 to dri client.It provides synchronized access
	 to the graphic hardware

### DRI(DIRECT RENDERING INFRASTRUCTURE)
	DRI modules reside 
		`/lib/modules/.../kernel/drivers/gpu/drm`

It must be compiled each time the kernel change.
DRI is a framework(context,frame,structure). 
for allowing direct access to
the hardware.

### EGL
	EGL is an interface between Khronos rendering API
	(Like openGL ES or openVG) and the underlying 
	platform window system.
	It handles graphics context management, 
	surface/buffer binding, and rendering 
	synchronization.

## HTTP HANDLES SESSIONS

	Http is stateless protocol.

	A stateless protocol operates under the client-server model.
	Where the client sends request and the server responds to requests

	Stateless protocols do not retain or store client sessions
	and as a result, the client is responsible for storing session information
	for future requests.

	This ultimately means that clients must include their session 
	information in requests made to the server for authentication and
	validation.

* COOKIES
    Cookies are used to store session information and other data
		sent from the server on the client side.

		Cookies are typically used to uniquely identify clients interacting
		with server.

		Cookies are stored in a temporary directory on the client browser.

		Cookies are typically used for state management as they can contains:
		     .Session IDs
				 .Other cookie attributes.

				When communicating with a Web server, the server will send a cookie 
				to the client with the "Set-Cookie" header

* COOKIE ATTRIBUTES
	Session ID:   Random string that is used for session management
		Session ID are unique identifiers that are used to
		identify useser their respective sessions

		Session ID can be stored into: Cookie or URL
		Session ID Guidelines :
			- Must be random and unique
			- They need to be sent securely
			- They should be lengthy
			- Should never be reused

	Expires   :		Specifies and expiration date for the cookie
	Domain    :   Specifies the domain where this cookie can be used
	Path      :   Resource or path where the cookie is valid.
	HttpOnly  :   If enabled, this prevents the cookies from being
	 				        accessed via JS on the client side.
	Secure 	  :   If enabledn the cookie will only be sent over https.




