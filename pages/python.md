---
title: Python
tags: language
filters: {}
---

-
  > Python is the most powerful language you can still read.
  > \
  > \- Paul Dubois
- **Workflow:**
	- [[Python Workflow]]
-
  collapsed:: false
  ---
- **Language**
  collapsed:: false
	- ^^Setup^^
	- ^^Resources^^
	  collapsed:: true
		- [Comprehensive Cheatsheet](https://github.com/gto76/python-cheatsheet)
		  todo:: 1620885582093
		- [[PEP's]] - [PEP's](https://www.python.org/dev/peps/)
		- [Dev Docs](https://devdocs.io/python~3.9/)
		- [Google's Dependency Management service](https://deps.dev/) **COMING SOON**
	- ^^Projects^^
	  collapsed:: true
		- [[FTP File Transfer Application]]
		- [[Make a Discord Bot]]
		- [Turn your Python Script into a 'Real' Program with Docker](https://python.plainenglish.io/turn-your-python-script-into-a-real-program-with-docker-c200e15d5265)
			- [Project Repo](https://github.com/adamcyber1/mypythondocker)
	- ^^Tools^^
	  collapsed:: true
		- [[Jupyter]]
		- [[Kite]]
		- [[VSCode]] Extensions
			- _General_
				- `ms-python.python` Python language support
				- `ms-python.vscode-pylance` Python language support
				- `brainfit.vscode-importmagic` Fix missing module imports
				- `formulahendry.code-runner` Code runner to run the language for output and not just python code
				- _AI Code Completion_
					- [Comparisons here](https://medium.com/swlh/kite-vs-tabnine-which-ai-code-autocomplete-should-you-choose-eb6eba85c3a6)
						- ❌️ `kiteco.kite` Kite
						- ✅️ `tabnine.tabnine-vscode` TabNine
				- `almenon.arepl` Coding REPL
			- _Documentation_
				- `njpwerner.autodocstring` Auto Generatre Doc Strings
			- _Formatting_
				- `kevinrose.vsc-python-indent` Correct Indentation
			- _Debugging_
				- `dongli.python-preview` Preview execution stack
			- _Unit Testing_
				- `littlefoxteam.vscode-python-test-adapter` Python Test explorer
			- _Static Typing_
				- `njqdev.vscode-python-typehint` Data type hint
				- `ms-pyright.pyright` for static type checking
			- _App Dev_
				- ❌️ `nikolapaunovic.tkinter-snippets` [[tkinter]] snippets
				- `njqdev.vscode-python-typehint` Data type hint
			- _Jupyter Notebooks_
				- `jithurjacob.nbpreviewer` Jupyter Notebook Support and Viewing
				- `ms-toolsai.jupyter` Jupyter Notebook Support and Viewing
		- [[black]] Code formatter
		- [[Python Poetry]]
	- ^^Libraries^^
	  collapsed:: false
		- ^^Build Tools^^
		  collapsed:: true
			- [Pants](https://www.pantsbuild.org/docs)
		- **Dependency Management** [[Python Poetry]] [[pydeps]]
		- **Linting & Style Checking:** [[black]], [[flake8]]
		- **Utils:** [[pyinstaller]], [[os]], [[glob]], [[sys]], [[shutil]], [[socket]]
			- **Logging:** [[logging]], [[rich]].logging, 💙[[loguru]]
			- **Virtual Environment:** [[venv]], 💙[[virtualenv]]
			- **Benchmarking:** [[clockpy]]
			- **Error Handling:** [[pretty-errors]]
		- **Documentation:** [[pydoc]], [[prettytable]], [[functools]], [[mkdocs]]
		- **Unit Testing:** 💙[[pytest]] [[unittest]]
		- **String Manipulation:** [[re]], [[parse]]
		- **Email:** [[smtplib]], [[email]]
		- **File System:**
			- **File System Monitoring:** [[watchdog]]
			- **File Manipulation:**
				- **PDF's** [[PyPDF2]]
				- **YAML** [[PyYaml]]
		- **CLI Apps:**
			- **Resources:** [this list](https://github.com/vinta/awesome-python#command-line-interface-development)
			- **Management:** [[click]], [[argparse]]
			- **Quality Of Life:** [[prompt_toolkit]]
			- **Visuals:** [[tqdm]], [[alive-progress]], [[rich]]
			- **TUI Apps:** [[textual]], [[blessed]], [[npyscreen]]
		- **GUI Apps:**
			- **Desktop**
				- **tkinter:** [[tkinter]], [[tkcalendar]], [[pyqt]], [[PySimpleGUI]]
			- **Web Apps**
				- [[pywebio]]
		- **Data Science:**
			- **Data Manipulation:** [[pandas]], [[pandasgui]], [[pandasql]] [[datetime]], [[tablib]], [[OpenPyXl]], [[mito]]
			- **Data Visualization:** [[matplotlib]], [[lux]], [[holoviz]], [[panel]], [[hvplot]]
			- **Data Management:** [[CSV]], [[JSON]]
			- **Data Pipelines:** [[prefect]]
		- **Databases:** [[sqlite3]], [[sql alchemy]]
		- **Parallelization:** [[ray]], [[asyncio]]
		- **URL Manipulation:** [[yarl]]
		- **API Requests:** [[requests]]
		- **Machine Leaning:** [[sklearn]]
		- **Password Managment:** [[getpass]]
	- ^^Syntax^^
		- ^^Conventions^^
		  collapsed:: true
			- Use uppercase initials for class names, lowercase for all others.
				- function names all in lowercase
				- `class.object.field` names should not be capitalized, and if multiple words used, then separate with underscores:
					- `user1.first_name` > `user1.firstName`
		- ^^Decorators^^
		  id:: 60be8411-7d36-4c4f-8f0f-56c733eb3294
		  collapsed:: true
			-
			  collapsed:: true
			  			  			  			  			  ```python
			  			  			  			  			  def hello_decorator(func):
			  			  			  			  			    def wrapper(*args, **kwargs):
			  			  			  			  			        result = func(*args, **kwargs)
			  			  			  			  			        return result
			  			  			  			  			    return wrapper
			  			  			  			  			  
			  			  			  			  			  @hello_decorator
			  			  			  			  			  def add(a, b):
			  			  			  			  			    return a + b 
			  			  			  			  			  
			  			  			  			  			  if __name__ == '__main__':
			  			  			  			  			    output = add(2, 2)
			  			  			  			  			    print(output)
			  			  			  			  			  ```
				- ![2021_06_03_image.png](https://cdn.logseq.com/%2F07ac90d5-a8a5-495c-84ae-a5c969228e3823d90a39-636b-484a-a9f0-247ff0a7a0bf2021_06_03_image.png?Expires=4776348240&Signature=aullpNqBIYr0X2A8xmDyEjDbWMqCgT812xTe9ViyKqyKBH64h7itp8Ore5U4XyKQ3pC6HbfhoDClIegiG-VaeWfqKnyXhBVZ1eFADMklEExEy0pV64NNrZ9ptrwfpupGTdg2IQHCtgnJppUa2eHuFlcgDAv99oAQf6e2l8UxXLoByhaWOqguYAICMXBkYtklhFSaCORRbZwrjdT9ZrEMrK6HnRrpnfTOY6rmk840A0UACaAeOjFg17ba-VTdL6wLUMcE9Dt0i73khlU5xjKlUqTE5ejBPk-dK8cDsASOCLMhWgMqiSSpZs6MjMSOtL9b3K1fBWiWP7sqt0hDpoVpcQ__&Key-Pair-Id=APKAJE5CCD6X7MP6PTEA)
			- [Python Decorators in 15 Minutes](https://youtu.be/r7Dtus7N4pI) | [Calm Code Decorators](https://calmcode.io/decorators/introduction.html) #star
			  done:: 1622747738306
			- [Decorators 101](https://sureshdsk.dev/python-decorators-101)
			  todo:: 1620835767488
			- [Decorators 201](https://sureshdsk.dev/python-decorators-201)
			  done:: 1621632285760
			  todo:: 1622738195818
				- To get the correct doc strings and indicate that wrapping has occurred on the given function we can use the [[functools]] module with the `wraps` function
			- [Decorators with params](https://sureshdsk.dev/python-decorators-with-parameters)
			  todo:: 1620835794488
				- Useful with using Classes so the extra param passing boiler plate can be avoided
		- ^^Data Types & Structs^^
		  collapsed:: true
			- **Data Types**
			  id:: 6100ca2b-21a1-4fbe-babf-ada8c983a200
				- _Strings_
					-
					  ```python
					  					  					  					  					  					  						  # This is an ordinary string
					  					  					  					  					  					  						  print("This is a string")
					  					  					  					  					  					  						  
					  					  					  					  					  					  						  # This is a function Doc string
					  					  					  					  					  					  						  def function(x):
					  					  					  					  					  					  						      """This is a doc string explaining
					  					  					  					  					  					  						      the inner workings of this function
					  					  					  					  					  					  						      """
					  					  					  					  					  					  						      y = x * 7
					  					  					  					  					  					  						      reutrn(y)
					  					  					  					  					  					  						  
					  					  					  					  					  					  						  x = 17
					  					  					  					  					  					  						  printer = "hewlet packard"
					  					  					  					  					  					  						  
					  					  					  					  					  					  						  # This is a template literal "F string"
					  					  					  					  					  					  						  print(f"I just printed {x} pages to the printer {printer}")
					  					  					  					  					  					  						  # or for less elegence
					  					  					  					  					  					  						  print("I just printed" + x + "pages to the printer" + printer)
					  					  					  					  					  					  						  ```
					- [Python 3's f-Strings: An Improved String Formatting Syntax (Guide)](https://realpython.com/python-f-strings/)
				- _Nubmers_
					-
					  ```python
					  					  					  					  					  					  						  # Integer whole numbers
					  					  					  					  					  					  						  a = 496
					  					  					  					  					  					  						  print(type(a)) # int for integer
					  					  					  					  					  					  						  
					  					  					  					  					  					  						  # Float for floating point number
					  					  					  					  					  					  						  a = 496
					  					  					  					  					  					  						  print(type(a)) # float
					  					  					  					  					  					  						  
					  					  					  					  					  					  						  # Complex Numbers (in math i is used for imaginary numbers, in programming and python it is 'j')
					  					  					  					  					  					  						  a = 496 - 6.1j #the j is the complex part
					  					  					  					  					  					  						  print(type(a)) # complex
					  					  					  					  					  					  						  print(a.real) # view the real part of the number
					  					  					  					  					  					  						  print(a.imag) # view the imaginary part of the number
					  					  					  					  					  					  						  ```
				- _Booleans_
					-
					  ```python
					  					  					  					  					  					  						  True & False # these ARE the operators
					  					  					  					  					  					  						  true & false # These are NOT the operators
					  					  					  					  					  					  						  TRUE & FALSE # These are NOT the operators
					  					  					  					  					  					  						  
					  					  					  					  					  					  						  bool(" ") # True
					  					  					  					  					  					  						  bool("")  # False
					  					  					  					  					  					  						  bool(1)   # True
					  					  					  					  					  					  						  bool(0)   # False
					  					  					  					  					  					  						  ```
			- **Data Strcutures**
				- _Set_
					-
					  ```python
					  					  					  					  					  					  						  # a set is like a hashtable, the order is not important and they are not ordered like an array
					  					  					  					  					  					  						  # sets cannot contain duplicate values
					  					  					  					  					  					  						  a = set([1,2,3,4])
					  					  					  					  					  					  						  a = (1, 2, 3, 4)
					  					  					  					  					  					  						  
					  					  					  					  					  					  						  # methods
					  					  					  					  					  					  						  a.add() # adds an item to the set
					  					  					  					  					  					  						  a.remove() # removes an existing item from the set
					  					  					  					  					  					  						  a.discard() # acts like remove but if item is not a part of the set, do nothing and throw no errors (remove quietly)
					  					  					  					  					  					  						  a.clear() # removes all items from the set and it becomes empty
					  					  					  					  					  					  						  len(a) # lets you see how many items are in the set
					  					  					  					  					  					  						  # faster way of making a set is to pass an `[]` array to the set() function
					  					  					  					  					  					  						  
					  					  					  					  					  					  						  a = set([1,3,5,7,9])
					  					  					  					  					  					  						  b = set([2,4,6,8,10])
					  					  					  					  					  					  						  c = set([2, 3, 5 ,7])
					  					  					  					  					  					  						  a.union(b) # = 1, 2, 3, 4, 5, 6, 7, 8, 9, 10
					  					  					  					  					  					  						  a.intersection(c) # = 3, 5, 7
					  					  					  					  					  					  						  
					  					  					  					  					  					  						  2 in b # result is True
					  					  					  					  					  					  						  9 not in a # Result is False 9 IS in the set of odd numbers
					  					  					  					  					  					  						  ```
					- _Frozen Set_
						-
						  ```python
						  						  						  						  						  						  							  # less methods than sets
						  						  						  						  						  						  							  # immutable
						  						  						  						  						  						  							  ```
				- _Tuple_
					-
					  ```python
					  					  					  					  					  					  						  # can be created just by assigning values encapsulated in parens
					  					  					  					  					  					  						  # or for a single value leaving a trailing comma
					  					  					  					  					  					  						  
					  					  					  					  					  					  						  a = (1, 2, 3, 4)
					  					  					  					  					  					  						  # or
					  					  					  					  					  					  						  b = ('a',)
					  					  					  					  					  					  						  # or
					  					  					  					  					  					  						  c = 1, 2, 3, 4,
					  					  					  					  					  					  						  
					  					  					  					  					  					  						  # tuples are immutable, they are smaller in memory than lists, have less methods available to them, and are faster that lists.
					  					  					  					  					  					  						  
					  					  					  					  					  					  						  survey = (27, "vietnam", True)
					  					  					  					  					  					  						  age, country, knows_python = survey # this works
					  					  					  					  					  					  						  print(age)
					  					  					  					  					  					  						  print(country)
					  					  					  					  					  					  						  print(knows_python)
					  					  					  					  					  					  						  ```
				- _Dictionary_
					-
					  ```python
					  					  					  					  					  					  						  # key value pairs, basically an object in javascript
					  					  					  					  					  					  						  my_dictionary = {"key":"my_key", "value":666}
					  					  					  					  					  					  						  my_dictionary.keys()
					  					  					  					  					  					  						  my_dictionary.values()
					  					  					  					  					  					  						  
					  					  					  					  					  					  						  # to add more key value pairs after initialization to the dictionary use object name and brackets around the key and set equal to the value:
					  					  					  					  					  					  						  my_dictionary["name"] = "Bryan Jenks"
					  					  					  					  					  					  						  # with bracket method the key needs quotes around it but in the constructor function you DONT need quotes on the key names:
					  					  					  					  					  					  						  dict(message="test", language="english")
					  					  					  					  					  					  						  
					  					  					  					  					  					  						  for key, value in my_dictionary.items():
					  					  					  					  					  					  						  	print(key, "=", value)
					  					  					  					  					  					  						  ```
				- _List_
					-
					  ```python
					  					  					  					  					  					  						  # basically an array as you understand them
					  					  					  					  					  					  						  
					  					  					  					  					  					  						  a = [1, 2, 3, 4, 5]
					  					  					  					  					  					  						  a.append(17) # adds a new item to the end of the list
					  					  					  					  					  					  						  a.append(19) # adds a new item to the end of the list
					  					  					  					  					  					  						  a = [1, 2, 3, 4, 5, 17, 19]
					  					  					  					  					  					  						  
					  					  					  					  					  					  						  a[-1] # shows the item at the end of the list by wrapping around
					  					  					  					  					  					  						  # you can only wrap around completely, once, otherwise you will get an error.
					  					  					  					  					  					  						  
					  					  					  					  					  					  						  a[2:5] # this slices out a smaller list. the starting index number element is included and the ending index number is not included so indexes returned will be 2, 3, 4 but not 5
					  					  					  					  					  					  						  
					  					  					  					  					  					  						  b = ['a', 'b', 'c']
					  					  					  					  					  					  						  a + b # = [1, 2, 3, 4, 5, 17, 19, 'a', 'b', 'c']
					  					  					  					  					  					  						  # adding lists together causes concatenation
					  					  					  					  					  					  						  ```
		- ^^Flow Control^^
		  collapsed:: true
			- **Loops**
			  collapsed:: true
				- _While Loop_
					-
					  ```python
					  					  					  					  					  					  							  i = 1
					  					  					  					  					  					  							  while i <= 10:
					  					  					  					  					  					  							      print(i)
					  					  					  					  					  					  							      i+=1
					  					  					  					  					  					  							  ```
				- _For Loop_
					-
					  ```python
					  					  					  					  					  					  							  for letter in "giraffe academy":
					  					  					  					  					  					  							      print(letter)
					  					  					  					  					  					  							  
					  					  					  					  					  					  							  friends = ["Jim", "Suzy", "Kevin"]
					  					  					  					  					  					  							  
					  					  					  					  					  					  							  for name in friends:
					  					  					  					  					  					  							      print(name)
					  					  					  					  					  					  							  
					  					  					  					  					  					  							  for index in range(10):
					  					  					  					  					  					  							      print(index) # prints 1-9 not including 10 so always increment upwards by 1
					  					  					  					  					  					  							  ```
			- **Exception Handling**
			  collapsed:: true
				-
				  ```python
				  				  				  				  				  try:
				  				  				  				  				      number = int(input("enter a number: "))
				  				  				  				  				      print(number/0) #divide by zero
				  				  				  				  				  except ZeroDivisionError as err:
				  				  				  				  				      print(err)
				  				  				  				  				      print("Divided By Zero")
				  				  				  				  				  except ValueError:
				  				  				  				  				      print("invalid input")
				  				  				  				  				  # OUTPUT:
				  				  				  				  				  ## ./test.py
				  				  				  				  				  ## enter a number: 1
				  				  				  				  				  ## integer division or modulo by zero
				  				  				  				  				  ## Divided By Zero
				  				  				  				  				  ```
			- **Ternary Operator**
			  collapsed:: true
				-
				  ```python
				  #You'll typically see:
				  reputation = 30
				  if reputation > 25:
				      name = "admin"
				  else:
				      name = "visitor"
				  print(name)
				  
				  reputation = 20
				  name = "admin" if reputation > 25 else "visitor"
				  print(name)
				  #>>> admin
				  #>>> visitor
				  ```
			- **Case Statement**
			  collapsed:: true
				- Python 3.10 added Match Case statements
				-
				  ```python
				  x = "hello" 
				  
				  match x:
				  	case "hello":
				      	print("hello")
				    	case "hi":
				     		print("hi")
				    	case _:
				      	print("default case")
				  ```
		- ^^Functions^^
		  collapsed:: true
			- **Functions**
				-
				  ```python
				  				  				  				  				  				  					  def pow(p):
				  				  				  				  				  				  					      """Calculate the power"""
				  				  				  				  				  				  					      return p*p
				  				  				  				  				  				  					  ```
			- **Map Filter Reduce**
				-
				  ```python
				  				  				  				  				  				  					  import math
				  				  				  				  				  				  					  
				  				  				  				  				  				  					  def area(r):
				  				  				  				  				  				  					      """Area of a circle with radius 'r'."""
				  				  				  				  				  				  					      return math.pi * (r**2)
				  				  				  				  				  				  					  
				  				  				  				  				  				  					  radii = [2, 5, 7.1, 0.3, 10]
				  				  				  				  				  				  					  # Method 1: Direct Method
				  				  				  				  				  				  					  areas = []
				  				  				  				  				  				  					  for r in radii:
				  				  				  				  				  				  					      a = area(r)
				  				  				  				  				  				  					      areas.append(a)
				  				  				  				  				  				  					  
				  				  				  				  				  				  					  print(areas)
				  				  				  				  				  				  					  radii = [2, 5, 7.1, 0.3, 10]
				  				  				  				  				  				  					  # map(<function>, <list, tuple, or other iterable object>)
				  				  				  				  				  				  					  list(map(area, radii))
				  				  				  				  				  				  					  print(list(map(area, radii)))
				  				  				  				  				  				  					  # Celcius to Farenheit with map and lambda
				  				  				  				  				  				  					  temps = [("Berlin",29), ("Cairo", 36), ("Buenos Aires", 19), ("Los Angelas", 26), ("Tokyo", 27), ("New York", 28), ("London", 22), ("Beijing", 32)]
				  				  				  				  				  				  					  
				  				  				  				  				  				  					  c_to_f = lambda data: (data[0], (9/5)*data[1] + 32)
				  				  				  				  				  				  					  
				  				  				  				  				  				  					  print(list(map(c_to_f, temps)))
				  				  				  				  				  				  					  
				  				  				  				  				  				  					  import statistics
				  				  				  				  				  				  					  
				  				  				  				  				  				  					  data = [1.3, 2.7, 0.8, 4.1, 4.3, -0.1]
				  				  				  				  				  				  					  avg = statistics.mean(data)
				  				  				  				  				  				  					  print(avg)
				  				  				  				  				  				  					  print(list(filter(lambda x: x > avg, data)))
				  				  				  				  				  				  					  # Remove Missing Data
				  				  				  				  				  				  					  countries = ["", "Argentina", "", "Brazil", "Chile", "", "Columbia", "", "Ecuador", "", "", "Venezuela"]
				  				  				  				  				  				  					  
				  				  				  				  				  				  					  print(list(filter(None, countries)))
				  				  				  				  				  				  					  # dont use reduce, just use an explicit for loop
				  				  				  				  				  				  					  ```
			- **The \_\_main\_\_ Function**
				-
				  ```python
				  				  				  				  				  import time
				  				  				  				  				  
				  				  				  				  				  def useful_function():
				  				  				  				  				    for i in range(5):
				  				  				  				  				      print("I sweat I'm useful: {}".format(i))
				  				  				  				  				      time.sleep(1.0)
				  				  				  				  				  
				  				  				  				  				  # This function call if un commented would make it so if the script was run
				  				  				  				  				  # on the CLI then it would execute the function code. However, if we want to 
				  				  				  				  				  # Re-use the code as a module import and not have it run immediately on import
				  				  				  				  				  # Then you need the following logical construct
				  				  				  				  				  # useful_function()
				  				  				  				  				  
				  				  				  				  				  # This code checks if the entry point to the current session is this file.
				  				  				  				  				  # i.e. did we run this file like a script? or are we importing from another 
				  				  				  				  				  # location that is actually "__main__" and we're a sub process declaring
				  				  				  				  				  # variables, functions, and classes? Anything under this construct is ran and 
				  				  				  				  				  # defined only if the script is executed as a stand alone script and not imported
				  				  				  				  				  if __name__ == "__main__":
				  				  				  				  				    useful_function()
				  				  				  				  				  ```
			- **Working with global scope variables from within functions**
				-
				  ```python
				  				  				  				  				  i = 0
				  				  				  				  				  def increment():
				  				  				  				  				      global i
				  				  				  				  				      i += 1
				  				  				  				  				  ```
			- **Functions Can Be Nested**
				-
				  ```python
				  				  				  				  				  def func1(a, b): 
				  				  				  				  				  def inner_func(x):
				  				  				  				  				        return x*x*x 
				  				  				  				  				  return inner_func(a) + inner_func(b)
				  				  				  				  				  ```
			-
		- ^^Object Oriented Programming^^
		  collapsed:: true
			-
			  ```python
			  			  			  			  			  			  				  import datetime
			  			  			  			  			  			  				  # init/initializer is basically a constructor, this code runs first every time a new instance of this class is created
			  			  			  			  			  			  				      # self is a reference to the newly created object instance
			  			  			  			  			  			  				      def __init__(self, full_name, birthday):
			  			  			  			  			  			  				          self.name = full_name # getter/setter
			  			  			  			  			  			  				          self.birthday = birthday
			  			  			  			  			  			  				  
			  			  			  			  			  			  				      # extract first and last names
			  			  			  			  			  			  				      name_pieces = full_name.split(" ")
			  			  			  			  			  			  				      self.first_name = name_pieces[0]
			  			  			  			  			  			  				      self.last_name = name_pieces[-1]
			  			  			  			  			  			  				  
			  			  			  			  			  			  				      def age(self):
			  			  			  			  			  			  				          """Return the age of the user in years"""
			  			  			  			  			  			  				          today = datetime.date(2001, 5, 12)
			  			  			  			  			  			  				          yyyy = int(self.birthday[0:4])
			  			  			  			  			  			  				          mm = int(self.birthday[4:6])
			  			  			  			  			  			  				          dd = int(self.birthday[6:8])
			  			  			  			  			  			  				          dob = datetime.date(yyyy, mm, dd) # date of birth
			  			  			  			  			  			  				          age_in_days = (today - dob).days
			  			  			  			  			  			  				          age_in_years = age_in_days / 365
			  			  			  			  			  			  				          return int(age_in_years)
			  			  			  			  			  			  				  
			  			  			  			  			  			  				  user1 = new User("john legend", 20191120)
			  			  			  			  			  			  				  user1.name # result: "john legend"
			  			  			  			  			  			  				  user1.first_name # result: "john"
			  			  			  			  			  			  				  user1.last_name # result: "legend"
			  			  			  			  			  			  				  user1.birthday # result: 20191120
			  			  			  			  			  			  				  ```
			-
			  ```python
			  class User1:
			      pass
			  # Conventions: Class names Proper case
			  # Method names lower case snake case
			  # variables lower case
			  user1 = User1()
			  user1.first_name = "Bryan"
			  user1.last_name = "Jenks"
			  user1.age = 27
			  print(user1.first_name)
			  print(user1.last_name)
			  
			  user2 = User1()
			  user2.first_name = "Frank"
			  user2.last_name = "Poole"
			  user2.favorite_book = "2001: A Space Odessey"
			  # CLASS BENEFITS:
			  ## Methods
			  ## Initialization
			  ## Help Text
			  import datetime
			  
			  class User:
			      """
			      A member of friendface. for now we only store name and birthday, but in the future we will store an uncomfortable amount of information of the user.
			      """
			      # __INIT__ is the initilization/constructor of the class instance
			      def __init__(self, full_name, birthday):
			          self.name = full_name
			          self.birthday = birthday
			  
			          # Extract First and Last Names
			          name_pieces = full_name.split(" ")
			          self.first_name = name_pieces[0]
			          self.last_name = name_pieces[-1]
			  
			      def age(self):
			          """Return The age of the user in years"""
			          today = datetime.date(2001, 5, 12)
			          yyyy = int(self.birthday[0:4])
			          mm = int(self.birthday[4:6])
			          dd = int(self.birthday[6:8])
			          dob = datetime.date(yyyy, mm, dd)
			          age_in_days = (today - dob).days
			          age_in_years = age_in_days / 365
			          return int(age_in_years)
			  
			  user = User("Bryan Jenks", "19920923")
			  print(user.name)
			  print(user.first_name)
			  print(user.last_name)
			  print(user.birthday)
			  print(user.age())
			  ```
			- [Operator Overloading](https://www.programiz.com/python-programming/operator-overloading)
			- **Underscore Names**
			  collapsed:: false
				- [What's the meaning of underscores (_ & __) in Python variable names?](https://youtu.be/ALZmCy2u0jQ)
					- Name a private identifier with a leading underscore ( `_username`)
					- Name a strongly private identifier with two leading underscores (`__password`)
					- Special identifiers in Python end with two leading underscores.
						- _A.K.A. Dunder methods (double under-score)_ `__main__`
		- ^^File Handling^^
		  collapsed:: true
			-
			  ```python
			  			  			  			  			  			  				  employee_file = open("employees.txt","r") # Filename, Mode (r:read a:append w:write)
			  			  			  			  			  			  				  print(employee_file.readable()) # returns T/F if we can read the file
			  			  			  			  			  			  				  print(employee_file.readline()) # reads the first line of the file
			  			  			  			  			  			  				  print(employee_file.readline()) # reads the next line (second) in the file
			  			  			  			  			  			  				  print(employee_file.readline()[2]) # reads the (third) in the file
			  			  			  			  			  			  				  
			  			  			  			  			  			  				  
			  			  			  			  			  			  				  # always close open files
			  			  			  			  			  			  				  employee_file.close()
			  			  			  			  			  			  				  ```
		- ^^Tips, Tricks, & Hacks^^
		  collapsed:: false
			- **Multi-Variable Assignment**
			  collapsed:: true
				-
				  ```python
				  				  				  				  				  				  					  x = 0
				  				  				  				  				  				  					  y = 0
				  				  				  				  				  				  					  
				  				  				  				  				  				  					  # can be:
				  				  				  				  				  				  					  x, y = 0, 0
				  				  				  				  				  				  					  ```
			- **Swap Variable Values**
			  collapsed:: true
				-
				  ```python
				  				  				  x, y = 1, 0
				  				  				  
				  				  				  ```
			- **Kwargs**
			  collapsed:: true
				-
				  ```python
				  				  				  				  				  				  					  # Python 3.5+ allows passing multiple sets
				  				  				  				  				  				  					  # of keyword arguments ("kwargs") to a
				  				  				  				  				  				  					  # function within a single call, using
				  				  				  				  				  				  					  # the "**" syntax:
				  				  				  				  				  				  					  
				  				  				  				  				  				  					  def process_data(a, b, c, d):
				  				  				  				  				  				  					     print(a, b, c, d)
				  				  				  				  				  				  					  
				  				  				  				  				  				  					  x = {'a': 1, 'b': 2}
				  				  				  				  				  				  					  y = {'c': 3, 'd': 4}
				  				  				  				  				  				  					  
				  				  				  				  				  				  					  process_data(**x, **y)
				  				  				  				  				  				  					  # >>> 1 2 3 4
				  				  				  				  				  				  					  
				  				  				  				  				  				  					  process_data(**x, c=23, d=42)
				  				  				  				  				  				  					  # >>> 1 2 23 42
				  				  				  				  				  				  					  ```
			- **Default Parameters**
			  collapsed:: true
				-
				  ```python
				  				  				  # In Python 3 you can use a bare "*" asterisk
				  				  				  # in function parameter lists to force the
				  				  				  # caller to use keyword arguments for certain
				  				  				  # parameters:
				  				  				  				  				  				  					  
				  				  				  def f(a, b, *, c='x', d='y', e='z'):
				  				  				      return 'Hello'
				  				  				  				  				  				  					  
				  				  				  # To pass the value for c, d, and e you
				  				  				  # will need to explicitly pass it as
				  				  				  # "key=value" named arguments:
				  				  				  f(1, 2, 'p', 'q', 'v')
				  				  				  # TypeError: "f() takes 2 positional arguments but 5 were given"
				  				  				  				  				  				  					  
				  				  				  f(1, 2, c='p', d='q',e='v')
				  				  				  'Hello'
				  				  				  ```
			- **The \_ in Python**
			  collapsed:: true
				- The `_` in python can hold the last value in an interactive shell session but can be used like the unnamed register in [[VIM]] and you can use it to avoid issues when unpacking tuples or just throwing something away:
					-
					  ```python
					  					  					  					  					  my_tuple = (1,2,3)
					  					  					  					  					  x, _, z = my_tuple # (1,2,3)
					  					  					  					  					  #> x = 1
					  					  					  					  					  #> _ = 2
					  					  					  					  					  #> z = 3
					  					  					  					  					  ```
			- **Named Tuples**
			  collapsed:: true
				-
				  ```python
				  from collections import namedtuple
				  
				  Coordinate = namedtuple("Coordinate", "longitude latitude")
				  location = Coordinate(90, 37.5)
				  print("location:", location) 
				  # accessing attributes with dot notation
				  print(location.longitude, location.latitude) 
				  # Output: 
				  # location: Coordinate(longitude=90, latitude=37.5) 
				  # (90, 37.5) 
				  ```
			- **For ... Else**
			  collapsed:: true
				-
				  ```python
				  #case 1
				  for letter in 'foo':
				      print(letter)
				  else:
				      print("All letters have been printed")
				  
				  #case 2
				  for letter in 'foo':
				      print(letter)
				      if letter == 'o':
				          break
				  else:
				      print("Letters have been printed")
				      
				  # Output:
				  # case 1
				  # f
				  # o
				  # o
				  # All letters have been printed
				  # case 2
				  # f
				  # o
				  ```
			- **enums with the [[enum]] module**
			  collapsed:: true
				-
				  ```python
				  from enum import Enum
				  Season = Enum('Season', 'winter summer spring autumn')
				  print(Season.summer.name)
				  print(Season.summer.value)
				  
				  #using class
				  class Season(Enum):
				      winter = 1
				      summer = 2
				      spring = 3
				      autumn = 4
				  print(Season.winter.name)
				  print(Season.winter.value)
				  
				  # Output:
				  # summer
				  # 2
				  # winter
				  # 1
				  ```
			- **Replace len() with enumerate()**
			  collapsed:: true
				- Before:
					-
					  ```python
					  # Define a collection, such as list:
					  names = ['Nik', 'Jane', 'Katie', 'Jim', 'Luke']
					  
					  # Using the range(len(collection)) method, you'd write:
					  for i in range(len(names)):
					      print(i, names[i])
					  
					  # Using enumerate, you can define this by writing:
					  for idx, name in enumerate(names):
					      print(idx, name)
					      
					  # Both ways of doing this return:
					  # 0 Nik
					  # 1 Jane
					  # 2 Katie
					  # 3 Jim
					  # 4 Luke
					  ```
				- After:
					-
					  ```python
					  # Define a collection, such as list:
					  names = ['Nik', 'Jane', 'Katie', 'Jim', 'Luke']
					  
					  # Using enumerate, you can define this by writing:
					  for idx, name in enumerate(names, start=1):
					      print(idx, name)
					      
					  # This returns:
					  # 1 Nik
					  # 2 Jane
					  # 3 Katie
					  # 4 Jim
					  # 5 Luke
					  ```
			- **Stop Using Square Brackets To Get Dictionary Items — Use .get()**
			  collapsed:: true
				- Before:
					-
					  ```python
					  nik = {
					    'age':32,
					    'gender':'male',
					    'employed':True,
					  }
					  
					  print(nik['location'])
					  
					  # Returns:
					  # KeyError: 'location'
					  ```
				- After:
					-
					  ```python
					  nik = {
					    'age':32,
					    'gender':'male',
					    'employed':True,
					  }
					  
					  print(nik.get('location'))
					  
					  # Returns:
					  # None
					  ```
			- **Simplify Iterating Over Multiple Lists With Zip()**
			  collapsed:: true
				- Before:
					-
					  ```python
					  
					  names = ['Nik', 'Jane', 'Melissa', 'Doug']
					  ages = [32, 28, 37, 53]
					  gender = ['Male', 'Female', 'Female', 'Male']
					  
					  # Old boring way:
					  for_looped = []
					  for i in range(len(names)):
					      for_looped.append((names[i], ages[i], gender[i]))
					  
					  print(for_looped)
					  
					  # Returns:
					  # [('Nik', 32, 'Male'), ('Jane', 28, 'Female'), ('Melissa', 37, 'Female'), ('Doug', 53, 'Male')]
					  ```
				- After:
					-
					  ```python
					  
					  names = ['Nik', 'Jane', 'Melissa', 'Doug']
					  ages = [32, 28, 37, 53]
					  gender = ['Male', 'Female', 'Female', 'Male']
					  
					  # Zipping through lists with zip()
					  zipped = zip(names, ages, gender)
					  zipped_list = list(zipped)
					  
					  print(zipped_list)
					  
					  # Returns:
					  # [('Nik', 32, 'Male'), ('Jane', 28, 'Female'), ('Melissa', 37, 'Female'), ('Doug', 53, 'Male')]
					  ```
		- ^^Dunders^^
		  collapsed:: true
			- `__init__.py`
				- Determines what happens when the directory it's in is imported as a package
	- ^^PEP's^^
	  collapsed:: false
		- {{embed [[PEP's]] }}
	- ^^Version Changes^^
	  collapsed:: true
		- **3.10**
			- _Structural Pattern Matching_
				- From:
					-
					  ```python
					  name = input() 
					  match name: 
					      case "Misha": 
					          return "Hello Misha" 
					      case "John": 
					          return "Hello John" 
					      case _: 
					          return "Go away"
					  ```
				- To:
					-
					  ```python
					  match name: 
					      case "Misha" | "John": 
					          return f"Hello {name}" 
					      case "Michelle": 
					          return "Long time no see, Michelle" 
					      case _: 
					          return "Go away"
					  ```
				- Add Additional Conditions on matches with `if`
					-
					  ```python
					  
					  def get_car_price(make, is_turbocharged): 
					      match make: 
					          case "Subaru" if is_turbocharged: 
					              return 10000 
					          case "Toyota" if not is_turbocharged: 
					              return 7500 
					          case _: 
					              return 2300
					  ```
					- [Video on Pattern Matching](https://youtu.be/-79HGfWmH_w)
			- _Union Operator for Type Hints_
				-
				  ```python
				  def add(x: int | float, y: int | float):
				    return x + y
				  ```
			- _Parenthesized Context Managers_
				-
				  ```python
				  with (open('file1.txt', 'r') as fin, 
				       open('file2.txt', 'w') as fout):
				      fout.write(fin.read())
				  # In essence: cat file1.txt > file2.txt 
				  # if file2 were in append mode 'a' then it would be like:
				  # cat file1.txt >> file2.txt
				  ```
			-
-
  ---
- **Machine Learning**
	- [perceptilabs](https://www.perceptilabs.com/papers)
	- Model Building Steps:
		-
		  1. _Define_: What type of model will it be? A decision tree? Some other type of model? Some other parameters of the model type are specified too.
		  2. _Fit_: Capture patterns from provided data. This is the heart of modeling.
		  3. _Predict_: Just what it sounds like
		  4. _Evaluate_: Determine how accurate the model's predictions are.
	-
-
  ---
- **Security:**
  collapsed:: false
	- [10 common security gotchas in Python and how to avoid them](https://hackernoon.com/10-common-security-gotchas-in-python-and-how-to-avoid-them-e19fbe265e03)
	- [SQL injection Cheat Sheet](https://www.netsparker.com/blog/web-security/sql-injection-cheat-sheet/)
-
  ---
- **Package Development**
  collapsed:: true
	- ^^Resources^^
		- [Calm Code Setup](https://calmcode.io/setup/introduction.html)
	- ^^Workflow^^
		- Setup Git Repo and clone
		- {{embed ((60be8411-e645-4f47-bcc5-98ede67aeaed)) }}
		- Make directory and `*.py` file for your project name
			- In that directory add an `__init__.py` file and in that file add code to import your desired objects from your package
			- like "Install module but also add to working session these objects"
		- in the root set up a `setup.py` file
			- This file lets the local files be installed by pip as a proper package
		- Live iteration through [[Jupyter]] lab with magics:
			-
			  ```bash
			  python -m pip install jupyterlab
			  python -m jupyter lab
			  ```
			-
			  ```
			  %load_ext autoreload
			  %autoreload 2
			  ```
		- Upload package to PyPi (Python Package Index)
			-
			  ```
			  python -m pip install twine wheel
			  
			  ```
	- ^^Documentation^^
		- Create Documentation automatically. [Example config file](https://github.com/koaning/clumper/blob/main/mkdocs.yml) | [Explanation](https://calmcode.io/docs/mkdocs.yml.html)
		  id:: 60c243a4-c18d-4110-9912-ea846f2a342e
		- also [[sphinx]] and [[Restructured Text]]
- **Python & [[Docker]]**
	- [scaffoldy](https://scaffoldy.io/) service to make the generation of docker template files easier
-