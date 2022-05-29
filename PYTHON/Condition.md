# ----[ CONDITION - PYTHON] ---- 
                                
    < [index.md]

## SIMPLE CONDITION CHECK
```python
    cars =['Audi', 'BMW', 'Subaru', 'Toyota']

    for car in cars:
        if car == 'BMW':
            print(car.upper())

     ## CHECK INEQUALITY ##
      if cars != 'Nissan':
            print("No Toy")
```
 
## TEST MULTIPLE CONDITION
```python
    age = 16

    if (age > 0 and age >= 21):
        print("The age is in the range")
```

## CHECKING IN THE LIST
```python
    requested_toppings = ['mushrooms','onions',
                          'pineaple']

    if('mushrooms' in requested_toppings):
        print("They are mushrooms in recipe")
```

## CHECKING IF A VALUE IS NOT IN A LIST
```python
    if ('pepperoni' not in requested_toppings):
         print("No pepperoni in recipe")
```

## IF / ELSE CONDITION
```python
    age = 17

    if age >= 18:
       print("You are old enought to vote")
    else:
       print("Sorry, you are too young to vote")
```
     
## IF / ELIF / ELSE
```python
    age = 12

    if age < 4:
        print("Your admission cost is $0")
    elif age < 18:
        print("Your admission cost is $5")
    else:
        print("Your admission cost is $10")
```

## CHECKING IN THE LIST
```python
    requested_toppings = ['mushrooms',
                          'green_peppers',
                          'extra_cheese']
    for requested_toppings in requested_toppings:
            print("Adding  " + requested_toppings)

print ("Pizza Finished")
```

## USING MULTIPLE LISTS
```python
    available_toppings = ['mushrooms',
                          'green_peppers',
                          'extra_cheese']
    requested_toppings = ['mushrooms',
                          'french fries',
                          'extra_cheese']

    for requested_topping in requested_toppings:
      if requested_topping in available_toppings:
         print("Adding " + requested_topping + ".")
      else:
         print("Sorry,we don't have " +
               requested_topping + ".")

        print("\nFinished makiing your pizza")
```
