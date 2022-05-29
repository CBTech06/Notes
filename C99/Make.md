# ---- [ MAKEFILE] ----

	<[index.md]
 * Look at SNIPPET/Build/Makefile for example

# MANAGE A DEFINE
 * Add -DOPTION
	CFLAGS= -D_GLFW_WAYLAND
```c
	if defined(_GLFW_COCOA)
		#include "blah.h"
	elif defined(_GLFW_WAYLAND)
```

## INSTALL DIRECTORY
 * MANPAGES: 
 	install 

install:
 	install ${EXE} ${DESTDIR}
	make install DESTDIR=/usr/bin
	
