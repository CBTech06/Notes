# ---- [ DICTIONNARIES ] ---- 
                                
    < [../index.md]

  * Only immutable(they can't modify) objects can be used as key to dictionnary
    Each element in a dictionnary is representd by a key:value pair

## DECLARE DICTIONNARIES
```python
      alien_0 = {'color': 'green', 'points': 5 }
      print("  Color:  " + alien_0['color'] + "  Points:  " +  
	      str(alien_0['points']))
     # or
     print(alien.get("color"))

```
  * GET function
```python
   fib={1:1, 2:1, 3:2, 4:3}
   print(fib.get(4,0) + fib.get(7,5))

    # The result = 8 the fourth value get by fib is 3
    # fib.get(7,5) the value 7 doesn't exist so return 5
    #  5 + 3 = 8

```
## REMOVE VALUE FROM DICTIONNARY 
```python
        del alien_0['points']

        favorite_langage = {
        'Paul' : 'Ruby', 'Henry' : 'Asm', 'Jen' : 'C++' 
        }
```

## LOOP IN DICTIONNARY 
```python
        for key,value in favorite_langage.items():
        print("Key: " + key + "\tValue: " + value)
```

## LOOP ONLY KEY 
```python
        for key in favorite_langage.keys():
        print(key)
```
## LOOP ONLY VALUE
```python
        for value in favorite_langage.values():
        print(value) 
```

## LOOP A DICTIONNARY IN ORDER
```python
        for l in sorted(favorite_langage.keys()):
        print(l + "\tThank you to taking the poll")
```

##  CREATE AN EMPTY LIST AND STORE VALUE
```python
        aliens = []


        ''' MAKE 30 GREEN ALIENS  '''
        for alien_number in range(30):
        new_alien = { 'color' : 'green', 'points' : '5', 'speed' : 'slow'}
        aliens.append(new_alien)

        '''  SHOW THE FIRST FIVE ALIEN '''
        for alien in aliens[:5]:
        print(alien)
        print("...")

        ''' SHOW HOW MANY ALIENS HAVE BEEN CREATED '''
        print("Total number of aliens: " + str(len(aliens)))
        ```
        
## LIST IN DICTIONNARY
``` python
        pizza = {
                'crust': 'thick',
                'toppings': ['musrooms','xtra cheese'],
                }

        print("You ordered " + pizza['crust'] + "-crust pizza " + " with the following toppings: ")
        for toppings in pizza['toppings']:
        print("\t" + toppings)
```

## DICTIONNARY IN DICTIONNARY
```python
        users = {
        'aeinstein': {
            'first': 'Albert',
            'last': 'Einstein',
            'location':'princeton',
            },

        'mcurie': {
            'first': 'Marie',
            'last': 'Curie',
            'location': 'Paris',
            },
        }

for username, user_info in users.items():
    print("\nUsername: " + username)
    full_name = user_info['first'] + " " + user_info['last'] 
    location = user_info['location']

    print("\tFullName: " + full_name.title())
    print("\tLocation: " + location.title())
```
## ORDERED DICTIONNARY
```python
from collections import OrderedDict

favorites_langage = OrderedDict()

favorite_langage['Jen'] = 'Python'
favorite_langage['Sarah'] = 'C'
favorite_langage['Edward'] = 'Ruby'
favorite_langage['Phil'] = 'Python'
favorite_langage['Sarah'] = 'c'

for name, langage in favorite_langage.items():
    print(name.title() + "'s favorite langage is " + langage.title() + ".")
```
