# ---- [ PYTHON FUNCTIONS ] ---- 
                                
      <[../index.md]

## DEFINING A FUNCTION
```python
        def greet_user():
        print("Hello")
```
## LAMBDA FUNCTION

 * DEFINITION:
 	Lambda function in anonymous function used 
	inside another function

```python
# Multiply argument a with argument b and return the result
x = lambda a,b: a *b
print(x(5,6))
```

## DEFINING FUNCTION WITH DEFAULT VALUE
```python
    def describe_pet(pet_name,animal_type='dog'):
        print("Animal: " + animal_type,
              "\t Name: " + pet_name)

    describe_pet(pet_name='harry')
```

## RETURN A VALUE
```python
    def get_formatted_name(first_name, last_name):
        full_name = first_name + last_name
        return full_name.title()

    print(get_formatted_name('jimi ',' hendrix'))
```

## RETURN DICTIONNARY 
```python
    def build_person(first_name,last_name):
        person = {'first': first_name, 
                  'last': last_name}
        return person

    musician = build_person('jimi','hendrix')
    print(musician)
```

## FUNCTION IN A WHILE LOOP
```python
    while True:
        f_name = input("first Name: " )
        l_name = input("last_name: ")

        formated_name = get_formatted_name(f_name,
                                           l_name)
        print(formated_name)
        if f_name == 'q' or l_name =='q' :
           break
```

## PASSING A LIST TO A FUNCTION 
```python
    def greet_users(names):
        for name in names:
            msg = "Hello " + name.title() + "!"
            print (msg)

    usernames =['hannah','ty','margot']
    greet_users(usernames)
```

## SEND A COPY OF LIST 
```python
    function_name(list_name[:])
```

## PASSING AN ARBITRARY NUMBER OF ARGUMENT 
```python
 '''Create an empty tupple to store information '''
    def make_pizza(*toppings):
        for topping in toppings:
            print("- " + topping)

    make_pizza('peperoni')
    make_pizza('mushrooms','green peppers',
               'extra cheese')
```

## MIXING POSITIONAL AND ARBITRARY ARG
```python
    def make_pizza(size,*toppings):
        for topping in toppings:
            print("Pizza size : " + str(size) +
                  "\t Toppings: " + topping)

    make_pizza(12,'peperoni')
    make_pizza(16,'mushrooms','green peppers',
               'extra cheese')
```

## USING ARBITRARY KEYWORD ARG 
```python
    ''' Create a dictionary '''

    def build_profile(first,last,**user_info):
        profile = {}
        profile['first_name'] = first
        profile['last_name'] = last

        for key ,value in user_info.items():
            profile[key] = value

        return profile 

user_profile = build_profile('albert','einstein',
                              location='princeton',
                              field='physics')
print(user_profile)
```

## IMPORT FUNC FROM MODULE - PIZZA.PY
```python

    ''' FILE: pizza.py '''
    def make_pizza(size,*toppings):
        print("\nMaking a " + str(size) +
        " inch pizza with the following toppings:")
        for topping in toppings:
            print("- " + topping)

    # FILE: import pizza
    pizza.make_pizza(16,'peperroni')
```

## IMPORTING SPECIFIC FUNCTIONS
```python
    ''' Example: from module_name import func0,
                 func1, func2 '''

    from pizza import make_pizza
    make_pizza(16,'mushroom')
```

## IMPORT ALIAS FUNC 
```python
    from pizza import make_pizza as mp
    mp(16,'peperroni')
```
## ALIAS OF MODULE
```python
    import pizza as p
    p.make_pizza(16,'peperonni')
```

## IMPORT ALL FUNCTIONS FROM MODULE 
```python
    from pizza immport *
```
## PEP 8 RECOMENDATION 79 CHAR BY LINES 
```python
    def func_name (
        parameter 0, parameter 1, 
        parameter 3, parameter 4):
    func_body
```
