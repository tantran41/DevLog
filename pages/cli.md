---
tags: 
alias: command line, command line interface
---

- ^^Resources^^
	- [Command Line Interface Guidelines](https://clig.dev/) #star
- ^^Related^^
	- [[Bash]]
	- [[C++]]
	- [[Clang]]
- ^^Philosophy^^
  collapsed:: true
	- **Human-first design**
	- **Simple parts that work together**
	- **Consistency across programs**
	- **Saying (just) enough**
	- **Ease of discovery**
	- **Conversation as the norm**
	- **Robustness**
	- **Empathy**
	- **Chaos**
- ^^Guidelines^^
	- **The Basics**
	  collapsed:: true
		- _Use a command-line argument parsing library where you can._
			- Go: Cobra, cli
			  Java: picocli
			  Node: oclif
			  PHP: console
			  Python: [[click]], Typer, [[argparse]]
			  Ruby: TTY
			  Rust: clap, structopt
			  Swift: swift-argument-parser
		- *Return zero exit code on success, non-zero on failure*
		- _Send output to stdout._
		- _Send messaging to stderr._
	- **Help**
	  collapsed:: true
		- _Display help text when passed no options, the -h flag, or the --help flag._
		- _Display a concise help text by default._
		- _Show full help when -h and --help is passed._
		- _Provide a support path for feedback and issues._
		- _In help text, link to the web version of the documentation._
		- _Lead with examples._
		- _If you’ve got loads of examples, put them somewhere else_
		- _Display the most common flags and commands at the start of the help text._
		- _Use formatting in your help text._
		- _If the user did something wrong and you can guess what they meant, suggest it._
		- _If your command is expecting to have something piped to it and stdin is an interactive terminal, display help immediately and quit._
	- **Documentation**
	  collapsed:: true
		- _Provide web-based documentation._
		- _Provide terminal-based documentation._
		- _Consider providing man pages._
	- **Output**
	  collapsed:: true
		- _Human-readable output is paramount._
		- _Have machine-readable output where it does not impact usability_
		- _If human-readable output breaks machine-readable output, use --plain to display output in plain, tabular text format for integration with tools like [[grep]] or [[awk]]._
		- _Display output as formatted [[JSON]] if --json is passed._
		- _Display output on success, but keep it brief._
		- _If you change state, tell the user._
		- _Make it easy to see the current state of the system._
		- _Suggest commands the user should run._
		- _Actions crossing the boundary of the program’s internal world should usually be explicit._
		- _Increase information density—with ASCII art!_
		- _Use color with intention._
		- _Disable color if your program is not in a terminal or the user requested it._
			- `stdout` or `stderr` is not an interactive terminal (a TTY). It’s best to individually check—if you’re piping `stdout` to another program, it’s still useful to get colors on stderr.
			  The `NO_COLOR` environment variable is set.
			  The `TERM` environment variable has the value `dumb`.
			  The user passes the option `--no-color`.
			  You may also want to add a `MYAPP_NO_COLOR` environment variable in case users want to disable color specifically for your program.
		- _If stdout is not an interactive terminal, don’t display any animations._
		- _Use symbols and emoji where it makes things clearer._
		- _By default, don’t output information that’s only understandable by the creators of the software._
		- _Don’t treat `stderr` like a log file, at least not by default._
		- _Use a pager (e.g. `less`) if you are outputting a lot of text._
			- [[pypager]] in [[python]]
	- **Errors**
	  collapsed:: true
		- _Catch errors and rewrite them for humans._
		- _Signal-to-noise ratio is crucial._
		- _Consider where the user will look first._
		- _If there is an unexpected or unexplainable error, provide debug and traceback information, and instructions on how to submit a bug._
		- _Make it effortless to submit bug reports._
	- **Arguments and flags**
	  collapsed:: true
		- _Prefer flags to args._
		- _Have full-length versions of all flags._
		- _Only use one-letter flags for commonly used flags_
		- _Multiple arguments are fine for simple actions against multiple files._
		- _If you’ve got two or more arguments for different things, you’re probably doing something wrong._
		- _Use standard names for flags, if there is a standard._
			- `-a`, `--all`: All. For example, `ps`, `fetchmail`.
			  `-d`, `--debug`: Show debugging output.
			  `-f`, `--force`: Force. For example, `rm -f` will force the removal of files, even if it thinks it does not have permission to do it. This is also useful for commands which are doing something destructive that usually require user confirmation, but you want to force it to do that destructive action in a script.
			  `--json`: Display JSON output. See the output section.
			  `-h`, `--help`: Help. This should only mean help. See the help section.
			  `--no-input`: See the interactivity section.
			  `-o`, `--output`: Output file. For example, `sort`, `gcc`.
			  `-p`, `--port`: Port. For example, `psql`, `ssh`.
			  `-q`, `--quiet`: Quiet. Display less output. This is particularly useful when displaying output for humans that you might want to hide when running in a script.
			  `-u`, `--user`: User. For example, `ps`, `ssh`.
			  `--version`: Version.
			  `-v`: This can often mean either verbose or version. You might want to use -d for verbose and this for version, or for nothing to avoid confusion.
		- _Make the default the right thing for most users._
		- _Prompt for user input._
		- _Never require a prompt._
		- _Confirm before doing anything dangerous._
		- _If input or output is a file, support `-` to read from `stdin` or write to `stdout`._
			-
			  ```bash
			  curl https://example.com/something.tar.gz | tar xvf -
			  ```
		- _If a flag can accept an optional value, allow a special word like "none."_
		- _If possible, make arguments, flags and subcommands order-independent._
		- ❗ _Do not read secrets directly from flags._
	- **Interactivity**
	  collapsed:: true
		- _Only use prompts or interactive elements if stdin is an interactive terminal (a TTY)._
		- _If `--no-input` is passed, don’t prompt or do anything interactive._
		- _If you’re prompting for a password, don’t print it as the user types._
		- _Let the user escape._
	- **Subcommands**
	  collapsed:: true
		- _Be consistent across subcommands._
		- _Use consistent names for multiple levels of subcommand._
		- _Don’t have ambiguous or similarly-named commands._
	- **Robustness**
	  collapsed:: true
		- _Validate user input._
		- _Responsive is more important than fast._
		- _Show progress if something takes a long time._
		- _Do stuff in parallel where you can, but be thoughtful about it._
		- _Make things time out._
		- _Make it idempotent._
		- _Make it crash-only._
		- _People are going to misuse your program._
	- **Future-proofing**
	  collapsed:: true
		- _Keep changes additive where you can._
		- _Warn before you make a non-additive change._
		- _Changing output for humans is usually OK._
		- _Don’t have a catch-all subcommand._
		- _Don’t allow arbitrary abbreviations of subcommands._
		- _Don’t create a "time bomb."_
	- **Signals and control characters**
	  collapsed:: true
		- _If a user hits Ctrl-C (the INT signal), exit as soon as possible._
		- _If a user hits Ctrl-C during clean-up operations that might take a long time, skip them._
	- **Configuration**
	  collapsed:: true
		- Command-line tools have lots of different types of configuration, and lots of different ways to supply it (flags, environment variables, project-level config files). The best way to supply each piece of configuration depends on a few factors, chief among them specificity, stability and complexity.
			- Configuration generally falls into a few categories:
				- **Likely to vary from one invocation of the command to the next.**
					- Examples:
						- Setting the level of debugging output
						  Enabling a safe mode or dry run of a program
						-
						  > Recommendation: Use flags. Environment variables may or may not be useful as well.
				- **Generally stable from one invocation to the next, but not always. Might vary between projects. Definitely varies between different users working on the same project.**
					- This type of configuration is often specific to an individual computer.
					- Examples:
						- Providing a non-default path to items needed for a program to start
						  Specifying how or whether color should appear in output
						  Specifying an HTTP proxy server to route all requests through
						-
						  > Recommendation: Use flags and probably environment variables too. Users may want to set the variables in their shell profile so they apply globally, or in .env for a particular project.
						- If this configuration is sufficiently complex, it may warrant a configuration file of its own, but environment variables are usually good enough.
				- **Stable within a project, for all users.**
					- This is the type of configuration that belongs in version control. Files like Makefile, package.json and docker-compose.yml are all examples of this.
					-
					  > Recommendation: Use a command-specific, version-controlled file.
		- _Follow the XDG-spec._
		- _If you automatically modify configuration that is not your program’s, ask the user for consent and tell them exactly what you’re doing._
		- _Apply configuration parameters in order of precedence._
			- Here is the precedence for config parameters, from highest to lowest:
				- Flags
				  The running shell’s environment variables
				  Project-level configuration (eg. `.env`)
				  User-level configuration
				  System wide configuration
	- **Environment variables**
	  collapsed:: true
		- _Environment variables are for behavior that varies with the context in which a command is run._
		- _For maximum portability, environment variable names must only contain uppercase letters, numbers, and underscores (and mustn’t start with a number)._
		- _Aim for single-line environment variable values._
		- _Avoid commandeering widely used names._
			- https://pubs.opengroup.org/onlinepubs/009695399/basedefs/xbd_chap08.html
		- _Check general-purpose environment variables for configuration values when possible:_
			- `NO_COLOR`, to disable color (see Output)
			  `DEBUG`, to enable more verbose output
			  `EDITOR`, if you need to prompt the user to edit a file or input more than a single line
			  `HTTP_PROXY`, `HTTPS_PROXY`, `ALL_PROXY` and `NO_PROXY`, if you’re going to perform network operations (The HTTP library you’re using might already check for these.)
			  `SHELL`, if you need to open up an interactive session of the user’s preferred shell (If you need to execute a shell script, use a specific interpreter like `/bin/sh`)
			  `TERM`, `TERMINFO` and `TERMCAP`, if you’re going to use terminal-specific escape sequences
			  `TMPDIR`, if you’re going to create temporary files
			  `HOME`, for locating configuration files
			  `PAGER`, if you want to automatically page output
			  `LINES` and `COLUMNS`, for output that’s dependent on screen size (e.g. tables)
		- _Read environment variables from .env where appropriate._
		- _Don’t use .env as a substitute for a proper configuration file._
			- A `.env` file is not commonly stored in source control
			  (Therefore, any configuration stored in it has no history)
			  It has only one data type: string
			  It lends itself to being poorly organized
			  It makes encoding issues easy to introduce
			  It often contains sensitive credentials & key material that would be better stored more securely
		- _Do not read secrets from environment variables._
			- While environment variables may be convenient for storing secrets, they have proven too prone to leakage:
			- Exported environment variables are sent to every process, and from there can easily leak into logs or be exfiltrated
			  Shell substitions like `curl -H "Authorization: Bearer $BEARER_TOKEN"` will leak into globally-readable process state. (cURL offers the `-H @filename` alternative for reading sensitive headers from a file.)
			  [[Docker]] container environment variables can be viewed by anyone with Docker daemon access via docker inspect
			  Environment variables in [[systemd]] units are globally readable via `systemctl show`
			  Secrets should only be accepted via credential files, pipes, `AF_UNIX` sockets, secret management services, or another IPC mechanism.
	- **Naming**
	  collapsed:: true
		- _Make it a simple, memorable word._
		- _Use only lowercase letters, and dashes if you really need to_
		- _Keep it short._
		- _Make it easy to type._
	- **Distribution**
	  collapsed:: true
		- _If possible, distribute as a single binary._
		- _Make it easy to uninstall._
	- **Analytics**
	  collapsed:: true
		- _Do not phone home usage or crash data without consent._