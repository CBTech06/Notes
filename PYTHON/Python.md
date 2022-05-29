# ---- [ GENERAL PYTHON PROGRAMMING ] ---- 

 
## INDEX
 [Func.md](Func / Lambda ...)
 [File.md](File)
 [Input-loops.md](user Input and loops)
 [Class.md](Class)
 [Condition.md](If then else)
 [Exceptions.md](Exceptions Python Programming)
 [String.md](Python string)
 [Json.md](JSON Python Programming)
 [Advanced.md](__init__/__add__/]

* Containers:
 [Dict.md](Dictionnaries)
 [List.md](Python list)
 [Tupples.md](Python tupples)
 [Thread.md](Thread Python)

## CONVERT HEX COLOR TO DECIMAL
	FFC200 → 255,194,0
	print (int('FF',16)) → 255
	print (int('C2',16)) → 194
	print (int('00',16)) → 0

## MODULE DIRECTORY 
```python
        # randomNumber is located to Resources/randomNumber
        from Resources.randomNumber import Calc
        # If the file is located ../Test/
        ..Test/
```

2. EXAMPLE: DIRECTORY Resources/binance/file.py
  Client in /Work/Python/BINANCE/client_1.py
  from Resources.binance.client import Client

  * Change in  __init__.py   
``` python
  change:         from binance.client import Client 
      to:         from Resources.binance.client import Client
```

3. EXAMPLE: file → Resources/binance/client.py ask file
                   Resources/aiohttp/aiohttp

  change:  import aiohttp
      to:  import Resources.aiohttp.aiohttp

# [ TIPS - SCRIPTS ] 
 * HOW TO SEE THE TYPE OF ATTRIBUTS
```python         
	print(type(dimension))                  # Type Dict
	print(type(dimention[0))                # Type int
```

## DOC 
        pydoc                   for Python2
        pydoc3.9                for Python3

## DEBUG PDB 
``` python
      import pdb
      pdb.set_trace()                    # INVOKE PDB

      where 				 # Show stack trace (where function is called)
```

    list(ll)					List current func
    print value       Show information about value
    display value       "        "          "
    break             Put a breakpoint
    continue          Go to see the next step 

* EXAMPLE 
	print (self.card_result[0])

## KWARGS
   * If the number of keyword args is unknown 
     add a double ** before the parameter
     `Example` def my_function(**kwargs)

##  PIP 
  * INSTALL DEPENDENCIES
        pip install -r requirements.txt

  * UPGRADE PIP
        python -m pip install --upgrade

  * REMOVE PACKAGE
        pip uninstall matplotlib

## COMMAND LINE ARGUMENT
        ```python
        import sys

        print("NB ARGS: ", len(sys.argv))
        print("VALUE:" , str(sys.argv))
        ```
## VIRTUAL ENV
   A virtual environment is a place on your 
   system where you can install packages and 
   isolate them from all other python packages
   
   1.Install py38-virtualenv(under FREEBSD)
   
   *  CREATE ENV 
         python -m venv llenv 

   * ACTIVATE ENV 
         source ll_env /bin/activate
         
   * STOP ENV 
         deactivate

   If you have more than 1 python version 
   python3 -m venv CRYPTO
   virtualenv  --python=/usr/bin/python3.9 <path-to-virtualenv> 
