# ---- [ POINTERS / SMART POINTERS ] ----

        < [../index.md]

* USAGE:
 		`int a = 5;`								
		`int *b = &a;`							b contains address of a
		`int c = *b;`								c contains value of b(5)
	
# SMART POINTERS 

## EXAMPLE STD::UNIQUE_PTR<T> OF STRUCT 
```cpp
        // DECLARATION IN HEADER FILE 
        struct Tile
        {
                sf::Vector2f src;
                sf::Vector2 dst;
        };
        class Map
        {
                private:
                std::unique_ptr<Tile[] tile;
        }
        
        // DECLARATION IN CPP FILE
                tile.reset(new Tile[itemsPerLine * nLines]);
                tile[y*itemPerLine + x].dst.X = x * TILESIZE;
        
```

## EXAMPLE STD::UNIQUE_PTR<T> OF OBJECT
```cpp
        // DECLARATION IN FILE.HPP (CLASS)
        std::unique_ptr<Blocks> pBlock; 
        
        // INSTANTIATION IN FILE.CPP
        pBlock = std::make_unique<Blocks>(nbBlock,
                 sf::Vector2f(blockPos[i].x,blockPos[i].y));
```

## EXAMPLE STD::SHARED_PTR<T> 
        ```cpp
        // DECLARATION IN FILE.HPP(CLASS)
        std::shared_ptr<Blocks> pBlock;
 
        std::vector<std::shared_ptr<Blocks>> blockContainer;

        // INSTANTIATION IN FILE.CPP
        
        // blockPos is a vector who contains all position 
        // of my blocks.
        pBlock = std::make_shared<Blocks>(nbBlock,
                 sf::Vector2f(blockPos[i].x,blockPos[i].y));
        blockContainer.push_back(pBlock);
        
        // DRAW CONTAINERS
        for( int n = 0; n <= nbBlock;n++) {
                window.draw(*blockContainer[n]);
        }
```
# POINTERS

## CLASS OBJECT AS POINTERS 
```cpp
	class Tilemap: public sf::Drawable, public sf::Transformable
		{
			class snippet
					}
```
 * CREATE OBJECT
```cpp
		Tilemap *t = new Tilemap;
		t->loadfile("resources/map1.xml");
```

## ACCESS POINTER TO STD::VECTOR 
        ```cpp
        blockpos is std::vector<sf::Vector2i>
        storedPos is std::vector<sf::Vector2i>*
        
        storedPos = &blockpos
        // Acces to storedPos data
        for(int i=0; i < storedPosition->size();i++)
                (*storedPosition)[i].x;
                // BETTER BELOW 
                std::cout << storedPosition->at(i).y <<"\n";
                std::cout << storedPosition->at(i).x <<"\n";
        ```
