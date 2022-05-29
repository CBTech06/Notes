# ---- [ LIST ] ---- 

    < [../index.md]

## CREATION 
```python
     my_list = []            # Create empty list
     bicycles = [ 'Trek', 'Cannondale', 'Redline',
                    'Specialized' ]
```

## SHOW ELEMENT
```python
     print (bicycles[0])       # Show Trek
```

## SEARCH ELEMENT IN THE LIST
```python
        def search_double(list,element): 
            for i in range(len(list)):
                if list[i] == element:
                    return True
            return False

        def check_double(sum):
            print("SUM ADDED TO LIST: ", sum)
            if search_double(double, sum):
                print("ALREADY IN THE LIST")
            else: 
                double.append(sum)
                print("ADDDED")
```
## TO ACCESS AT THE LAST ELEMENT IN A LIST
```python
        print (bicycles[-1])
```

## CONCATENATION WITH STRING 
```python
    ''' title add caps to the first letter '''
    msg = "My first bike was a " + 
           bicycles[0].title() + "."
```

## CHANGING THE VALUE OF THE FIRST ELEMENT 
```python
        bicycles[0] = "Sunn"
```

## INSERTING A NEW ITEM TO THE END OF THE LIST
```python
        bicycles.append('YT')
```

## INSERTING ELEMENTS TO n POSITION 
```python
bicycles.insert(1,'Morewood')
```

## REMOVE THE LAST ITEM USING THE POP METHOD
```python
    popped_bicycle = bicycles.pop()
    print(popped_bicycle)

    bicycles.remove('Redline')
```

## SORT A LIST
```python
    bicycles.sort()
```

## SORT TEMPORARILY WITH SORTED FUNCTION
```python
    print(sorted(bicycles))
```

## LENGTH OF LIST
```python
    print(len(bicycles))
```

## LIST IN LOOP
```python
    for items in bicycles:
     print(items)
```

## CREATE NUMBER LIST  
```python
    numbers = list(range(0,10))
    # min / max / sum 
    print(sum(numbers))
```

##  SLICE LIST
```python
    print(numbers[0:3])
```
## LOOPING A SLICE
```python
    players =['charles', 'martina', 
              'michael', 'florence','eli']

    for player in players[:3]:
    print(player.title())
```

## COPYING A LIST 
```python
    newList = players[:]
```

