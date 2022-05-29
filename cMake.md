# ---- [ CMAKE TUTORIAL ] ---- 
                                                
    < [index.md]

## SIMPLE HELLO WORLD 
1. Create CMakeLists.txt file	
	  cmake_minimum_required(VERSION 3.10)
		  set(CMAKE_CXX_STANDARD 17)
		  set(CMAKE_CXX_STANDARD_REQUIRED ON)
		
	  project(hello VERSION 1.0)
	  add_executable(hello main.cpp)
	
2. Running CMake 
		cmake . && make && ./hello
	
## USING BUILD DIRECTORY 
	mkdir build
	cmake ../

## ADDING HEADER FILE
	set(ZLIB_INCLUDE_DIR /usr/include)
	target_include_directories(hello PUBLIC ${CMAKE_CURRENT_SOURCE_DIR}/include ${ZLIB_INCLUDE_DIR})

## MULTIPLE SOURCE FILE 
	file(GLOB_RECURSE SRC_FILES src/ù.cpp)
	add_executable(hello ${SRC_FILES})
			
## CREATE A LIB FROM SOURCE FILES:
1. replace add_executable with add_library
		add_library(mylib STATIC lib/blah.cpp)
		target_link_libraries(hello PUBLIC mylib)
		
## DEPENDING ON EXTERNAL LIBRARY WITH FIND_PACKAGE
	find_package(SFML 2 REQUIRED network audio graphics window system)
	find_library(ZLIB libz.a REQUIRED PATHS /usr/lib/libz.a)
1. include and link it simply
	target_include_directories(hello PUBLIC ${SFML_INCLUDE_DIR})
	target_link_libraries(hello PUBLIC ${SFML_LIBRARIES} {SFML_DEPENCIES} ${ZLIB})
					
## CMAKE DEPENCIES MANAGEMENT(CPM)

