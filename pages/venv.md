---
title: venv
tags: library
---

- **Python Virtual Environments**
	- **What are they**
		- a place to install packages that are specific to a certain project
			- also like [[packrat]] for [[R]] where you want to use a specific older version of a package in a snapshot
	- **How to use them**
		- A good module to use for this is the [[venv]] module
		- `python3 -m venv project_env`
			- make a new project in a virtual environment
		- `python3 -m venv projects/env_name`
			- Makes multiple environments for different projects but all in a single overarching directory
		- `source project_env/bin/activate`
			- activates it
			- if on windows in power shell its `& project_env/scripts/activate.ps1`
		- `which python`
			- confirms usage by
		- `pip list`
			- in the venv if you this command it will show you all the installed packages (only pip and setup tools) installed packages will now be stored here
		- `pip freeze`
			- Gets a list of the packages to send for reproducible analysis
			- and the output can go to _requirements.txt_
		- `deactivate`
			- to deactivate the venv
		- `pip install -r requrirements.txt`
			- To take a new virtual environment and install a list of requirements that we exported above
	- **Package Management**
		- `python3 -m venv venv --system-site-packages`
			- Create a venv with access to the system global packages for python from within a virtual environment
			- the difference is that now you copied your system packages to the venv but new installs will only go into the venv until you remove it
		- `pip list --local`
			- to see packages that are only installed in the venv and not the system
		- `pip freeze --local`
			- same logic as above
	- **Information**
		-
		  #+BEGIN_TIP
		  You can put your virtual environment into the project folder but you dont want to put your project files into the venv as the venv is just the place where execution is taking place, your working files should be in your project directory.
		  
		  the venv's are meant to be disposable and easy to throw away so no project files in them.
		  #+END_TIP
		-
		  #+BEGIN_WARNING
		  Never commit your venv's to source control, put them in gitignore
		  #+END_WARNING
		- but what you would commit to source control is the _requirements.txt_ doc
-