---
title: pywebio
---

- `pip install -U pywebio`
- **Input Output Functions**
	- https://pywebio.readthedocs.io/en/latest/output.html#functions-list
	-
	  |Function name|Description| 
	  |input|Text input| 
	  |textarea|Multi-line text input| 
	  |select|Drop-down selection| 
	  |checkbox|Checkbox| 
	  |radio|Radio| 
	  |actions|Actions selection| 
	  |file_upload|File uploading| 
	  |input_group|Input group|
- **Basic Input Functions**
	-
	  ```python
	  # Text Input
	  name = input('What is your Name?', type=TEXT)
	  # Number Input
	  name = input('How old are you?', type=TEXT)
	  # Single choice
	  answer = radio("Which Continent?", options=['Africa', 'Asia', 'Australia', 'Europe', 'North America', 'South America'])
	  # Checkbox
	  agree = checkbox("User Term", options=['I agree to terms and conditions'])
	  ```
- **Input Groups**
	-
	  ```python
	  #!/usr/bin/env python
	  
	  from pywebio.input import *
	  from pywebio.output import *
	  
	  data = input_group(
	      "User data",
	      [
	          input("What is your Name?", name="name", type=TEXT),
	          input("Input your age", name="age", type=NUMBER),
	          radio(
	              "Which Continent?",
	              name="continent",
	              options=[
	                  "Africa",
	                  "Asia",
	                  "Australia",
	                  "Europe",
	                  "North America",
	                  "South America",
	              ],
	          ),
	          checkbox(
	              "User Term", name="agreement", options=["I agree to terms and conditions"]
	          ),
	      ],
	  )
	  
	  # Output functions
	  
	  put_text("The output in a table:")
	  
	  put_table(
	      [
	          ["Name", data["name"]],
	          ["Age", data["age"]],
	          ["Continent", data["continent"]],
	          ["Agreement", data["agreement"]],
	      ]
	  )
	  ```
-