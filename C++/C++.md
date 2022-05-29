# ---- [C99 - C++ - MODERN C++] 

               <[../index.md]

	[Template.md] (Template C++ Programming)
	[Pointers.md] (Pointers/Smart Pointers Programming)
	[Lambda.md] 	(Lambda func Programming)
	[Thread.md]		(Thread programming)

## REF:
		* CppReference :
				reinterpret_cast is located at language/reinterpret_cast

## BUILDING 
	* Build std::filesystem::path not defined use -std=gnu++17 -fpermissive
			`g++ -std=c++17 -fpermissive boxpicture2.cxx -lfltk 
			-lfltk_images -lpng $(fltk-config --ldflags) -o BoxPicture2`

## SOME USEFUL TIPS
	* TO FIND AN INDEX IN MATRICE :> y * nElem + x
				`int *data <- MyMap`

```cpp
	for( int y = 0; y < NB_TILE_HEIGHT; y++)
		for(int x =0; x < NB_TILE_WIDTH;x++) {
				x * nElem + y							// LOOP 0 32 64 96 128 ...
				data[y*NB_TILE_WIDTH+x]		// LOOP ALL VALUES IN DATA	
		}
```
	
## OTHER EXAMPLES 
```cpp
		int someArray[10] = { 3,6,9,12,15,18,21,24,27,30};
						
		int *pLocation0 =&SomeArray[0];
		for(int i=0; i < 10; i++)
			{
			//std::cout << someArray + i << "=" << *(someArray + i) << std::endl;
				std::cout << pLocation0 << " = " << *pLocation0 << std::endl;
				pLocation0++;
			}
```

## ALLOCATION 
```cpp
	struct sSomeObject
			{
				int x = 0xA3A2A1A0;
				int y = 0xB3B2B1B0;
										
				sSomeObject() // constructor
				{
						x = 0xC3C2C1C0;
						y = 0xD3D2D1D0;  
				}
			}
```
		
Stack Allocation(COMPILATION TIME): `sSomeObject pSomeObject[10];`
Heap(RUNTINE):			`sSomeObject *pSomeObject = new sSomeObject[10]`
then delete		      `delete sSomeObject;`
								
* Pointers of array pointers
						
	Heap(RUNTIME) :			`sSomeObject **pSomeObject = new sSomeObject*[10] { 0 };`
		then delete		    `delete[] pSomeObject;`
						
## TRANSFORMATION
				
 * This code above 
```cpp
		if (bkey[0]) {
				if( DoesPieceFit(nCurrentPiece,nCurrentRotation,nCurrentX + 1, nCurrentY)) {
 					  nCurrentX = nCurrentX +1
							}
	//  Become:
 	 if bkey[0] is pushed and DoesPieceFit return 1 or return 0 if it is false
	  nCurrentX += (bKey[0] && (DoesPieceFit(nCurrentPiece,nCurrentRotation,nCurrentX + 1, nCurrentY)) ? 1 : 0

	 // Avoid If loop
		 	Example:    bGameOver = !(DoesPieceFit(nCurrentPiece,nCurrentRotation,nCurrentX + 1, nCurrentY))
```

## FILESTREAM
```cpp
    static_cast<new type(expression)

   size_t is unsigned interger type
   static_cast<size_t>length               // Convert length to size_t
```
   * Example:
    ```cpp
       const size_t N=100
       int numbers[N]
       for(size_t ndx=0; ndx < N;++ndx)
    ```

   * Flags 
     std::ios::app       Append content to an existing file. Otherwise the content will be deleted 
     std::ios:ate        Open file with position indicator to the end

