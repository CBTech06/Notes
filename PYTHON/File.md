# ---- [ FILES ] ---- 
                                
    < [../index.md]

## OPEN WITH ABSOLUTE PATH
```python
        filepath = '/home/captainchris/Work/Python/Learning/py_digits.txt'

        with open(filepath) as file_object:
         content = file_object.read()
        filepath.close
```

## RSTRIP() REMOVE SPACE AFTER STRING AND NEWLINE CHARACTER \n
```python
        print(content.rstrip())
```

## OPEN DIRECTLY
```python
        with open('py_digits.txt') as file_object:
        content = file_object.read()
        print(content)
```

## READ LINE BY LINE 
```python
        i = 0

        with open('py_digits.txt') as file_object:
        for line in file_object:
        print(str(i) + ":" + line.rstrip())
        i += 1
```

## READ FILE AND SEARCH
```python
  def read_line_by_line(filename):
   with open(filename) as file_object:
        lines = file_object.readlines()
        contents = ' '
        for line in lines:
	    contents += line.rstrip()
	    print (contents)                                  """ Show entire file """
	    print (contents[0])  | (line[0])                  """ Show character by character """
	    print (lines[0])                                  """ Show entire line 0 """ 

	   if "<map_info>" in contents:                       """ Search occurence in contents """
	        print ("FOUND")
	   else: 
	        print("NOT FOUND")
```

## MAKING A LIST OF LINES FROM FILE 
``` python
        filename = 'py_digits.txt'

        with open(filename) as file_object:
        lines = file_object.readlines()

        pi_string = ' '

        for line in lines:
        pi_string = line.rstrip()
```

## IS YOUR BIRTHDAY CONTAINED IN PI STRING
```python
        filename = 'pi_million_digits.txt'

        with open(filename) as fileobject:
        lines = fileobject.readlines()

        pi_string = ' '

        for line in lines:
        pi_string += line.rstrip()

        birthday = input("Enter you birthday[mmddyy]: ")

        if birthday in pi_string:
                print("Your birthday appears in pi million digits")
        else:
                print("Your birthday does not appear in pi million digits")
        ```

## WRITE INTO FILE 
```python
        file = 'programming_langage.txt'

        ''' w(write)|a(append)  '''
        with open(file, 'a') as file_object:
        file_object.write("I Love Programming")
        file_object.write("I Love Computer")
```


