                                # ---- [C++ STD VECTOR] ---- #
                                

                [<GO Back](C++)
                                                                
# EXAMPLE WITH STD::VECTOR #
              
              ```cpp  
              // Instantiation class (inherit sf::Drawable sf::Transformable)  
              Blocks block;
              
              std::vector<Blocks> blockContainer;
              
              // Reserve place for our vector
              blockContainer.reserve(number);
              blockContainer.emplace_back(Blocks(sf::Vector2f(blockPos[i].x,blockPos[i].y)));
          
              // Draw all blocks with for ranger loop 
              for (auto& objectToDraw: blockContainer)
                        win.draw(blockContainer);
              ```
        
## EXAMPLE WITH STD::LIST ##

```cpp
        std::list<Blocks> bcontainer;

        // INITIALISATION WITH CONSTRUCTOR
        bContainer.emplace_back(sf::Vector2f(blockPos[i].x,blockPos[i].y));

        // DRAW LIST
        for(auto & blockToDraw : bContainer) {
        window.draw(blockToDraw);
        }
```
 
