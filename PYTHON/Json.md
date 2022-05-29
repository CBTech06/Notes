# ---- [ JSON - PYTHON ] ----

	<[../index.md]

import json

## SAVE DATA IN FILES 
```python
	numbers = [2,3,5,7,11,13]
	filename = 'file.json'

	with open(filename,'w') as f_obj:
	    json.dump(numbers,f_obj)
```

## LOAD JSON FILE
```python
	with open(filename) as file_obj:
	    n = json.load(file_obj)

	print(n)
```

## SAVING AND READING USERINPUT DATA
```python
	username = input("What is your name: ")
	filename = 'file.json'

	with open(filename,'w') as file_obj:
	json.dump(username,file_obj)
	print('Well remember you when you come back ' + username)
```
## READ DATA SAVED BEFORE
```python
with open(filename) as file_obj:
    user = json.load(file_obj)
    print('Welcome back: ' + user)
```

