---
title: pydoc
tags: library,documentation
---

- [Socratica Video](https://www.youtube.com/watch?v=URBSvqib0xw&ab_channel=Socratica)
- using the [[pydoc]] module you can review documentation
- This command ( `python -m pydoc <++>` ) searches for the following:
	- modules ( `math` )
	- classes ( `tuple` )
	- functions ( `pow` )
- [[pydoc]] commands:
	- `pydoc -b`
		- Start an HTTP server with the given hostname (default: localhost).
		- Start an HTTP server on the given port on the local machine. Port number 0 can be used to get an arbitrary unused port.
		- Write out the HTML documentation for a module to a file in the current directory. If <name> contains a '' it is treated as a filename; if it names a directory, documentation is written for all the contents.
	- `pydoc -k <keyword>`
		- Search for a keyword in the synopsis lines of all available modules.
		- Start an HTTP server on an arbitrary unused port and open a Web browser to interactively browse documentation. This option can be used in combination with -n and/or - p
	- `pydoc -n <hostname>`
		- Start an HTTP server with the given hostname (default: localhost).
	- `pydoc -p <port>` #star #documentation
		- Start an HTTP server on the given port on the local machine. Port number 0 can be used to get an arbitrary unused port.
	- `pydoc -b`
		- Start an HTTP server on an arbitrary unused port and open a Web browser to interactively browse documentation. This option can be used in combination with -n and/or - p•
	- `pydoc -W <name> ...`
		- Write out the HTML documentation for a module to a file in the current directory. If <name> contains a '' it is treated as a filename; if it names a directory, documentation is written for all the contents.