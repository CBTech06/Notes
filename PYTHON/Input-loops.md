# ---- [ INPUT / LOOP ] ---- 
                                                                
         <[../index.md]

## INPUT FUNC
```python
        ''' python2.7 raw_input("Tell me something:  ") '''
        message = input("Tell me Something:  ")
        print(message)
```

## MULITLINE PROMPT
```python
        prompt = "If you tell me us who you are"
        prompt += "\nWhat is you first name:  " 

        name = input(prompt)
```

## NUMERICAL
```python
        age = input("Enter your age:  ")
        print(int(age))
```

## WHILE LOOP
```python
        current = 1
        while(current <= 5):
            print(current)
            current += 1
```

## QUIT ON A WHILE LOOP
```python
        prompt = "Tell me something.  "
        prompt += "Enter quit to Quit :) :  "

        message = " " 
        while(message != "quit"):
            message = input(prompt)
            print(message)
```

## QUIT WITHOUT BOOLEAN 
```python
        while True:
            city = input("Tell me your favorite city: ")

            if city == 'quit':
                break;
            else: print("I love " + city)
```

## CONTINUE IN WHILE LOOP 1-3-5-7-9
```python
        current = 0

        while current < 10:
            current += 1
            if current %2 == 0:
                continue

            print (current)
```

## WHILE LOOP WITH DICTIONNARY AND LIST 
```python
        unconfirmed_users = ['alice','brian','candice']
        confirmed_users = []

        while unconfirmed_users:
            current_user = unconfirmed_users.pop()
            print("Verifying user: " + current_user)
            confirmed_users.append(current_user)

        print("\nThe following user has been confirmed: ")
        for confirmed_user in confirmed_users:
            print(confirmed_user.title())
```

## REMOVE ALL INSTANCES OF SPECIFIC VALUE
```python
        pets = ['dog','cat','goldfish','cat','rabbit','cat']

        while 'cat' in pets:
            pets.remove('cat')

        print(pets)
```
## FILLING THE DICTIONNARY WITH USER INPUT
```python
        responses = {}

        """ Set a flag to indicate that polling is active """
        polling_active = True

        while polling_active:
                name = input("Name: ")
                response = input("Last Name: " )

                responses[name] = response
                repeat = input("let another person respond(Yes/No) ")
                if repeat == 'no':
                     polling_active = False

        """ Polling is complete. Show the result """ 
        print(" --- Polling Result ---")
        for name,response in responses.items():
             print(name + "\tLast_Name: " + response)
```
