---
title: Git
tags: tools
---

- ^^Resources^^
	- [Official Git Docs command shorthand](https://git-scm.com/docs)
	- [GREAT graphical walkthrough tool for learning git](https://learngitbranching.js.org/)
	- [Git Alias Tips](https://www.atlassian.com/blog/git/advanced-git-aliases)
	- [.gitignore Templates](https://github.com/github/gitignore)
	- [Git Cheatsheet](https://ndpsoftware.com/git-cheatsheet.html)
	- [Git Book](https://git-scm.com/docs)
- ^^Commands^^
	- `git log`
		- Pretty Log Output (_PLOG_)
			-
			  ```bash
			  			  git config --global  alias.plog "log --graph --format='%Cgreen%h %Cred%aN%Cblue%d%Creset %s %C(yellow)(%cr)%Creset'"
			  			  ```
	- `git stash`
		-
		  ```bash
		  		  git stash push 
		  		  ```
			- like an array method this will create a _Box_ and put all your changes inside of it and shove that _box_ in the corner of the room and give you a clean working tree.
			- The _box_ is now portable and you can switch to another branch and open the _box_ there and take out all of the changes.
		-
		  ```bash
		  		  git stash pop
		  		  ```
			- This opens the _box_ and applies all those stashed changes to the current working tree.
			- This is very useful for the situations where maybe you made a bunch of changes and you forgot to make a new branch and you're still on `master`/`main` and you want to move all those changes to the actual feature branch.
	- `git worktree`
		-
		  ```bash
		  		  git worktree add master
		  		  ```
			- Create a bare repo and start making new worktrees ((609ad591-5d2d-4a35-bfea-bc8a279b8ec6))
				- This means that a copy of the repo files is made for each worktree at the source commit that the bare repo was made from
				- Worktrees make it easier to open multiple repo branches at once under a unified workspace for easy switching of work between multiple features
				- Doesn't lend itself to easy updating.
				  collapsed:: true
					- The bare repo doesn't `git pull` itself but the worktrees after creation can use `git pull` but this is not ideal. The bare repo is basically frozen at a single commit for all new worktrees made.
- ^^Configuration^^
	- Great bash config for using git from [this thoughtbot article](https://thoughtbot.com/upcase/videos/git-customizing)
		-
		  ```bash
		  		  # No arguments: `git status`
		  		  # With arguments: acts like `git`
		  		  g() {
		  		    if [[ $# > 0 ]]; then
		  		      git $@
		  		    else
		  		      git status
		  		    fi
		  		  }
		  		  
		  		  # Complete g like git
		  		  compdef g=git
		  		  ```
	- A great tip to update your master branch return to the original branch you left and then merge changes. this is made as a git alias.
		- `!git checkout master && git pull && git fetch --prune && git checkout - && git merge master`
		- Aliased as `mup` for _"Master Up"_
		- The `!` is running it as a shell command as git aliases can only run 1 command. So this way we're still chaining commands
	- BARE Repos
	  id:: 609ad591-5d2d-4a35-bfea-bc8a279b8ec6
		- `git clone --bare <url>` or `git init --bare`
- ^^Troubleshooting^^
	- Removing a file from git history from [this SO article](https://stackoverflow.com/questions/307828/how-do-you-fix-a-bad-merge-and-replay-your-good-commits-onto-a-fixed-merge/15729420#15729420)
- ^^General Info^^
	- The `git checkout` command was replaced by `git switch` in git v2.23 as `git checkout` was apparently too overloaded.
	- **Rebasing:** essentially takes a set of commits, "copies" them, and plops them down somewhere else.
		- if you have 2 parallel branches and you rebase 1 onto the other it essentially looks for their common origin point (commit), takes the "base" of that branch and places the base at the end and right on top of branch you're Rebasing.
		- Then the branch that was the recipient of the rebasing needs to be updated so you rebase that onto the branch that was just rebased. This just moves the pointer to the tip of the merged branches
		- Interactive Rebasing with `git rebase -i <commit hash>` make it a more interactive way to move around and reorder commits
	- **HEAD** is simply the name of the currently checked out commit hash
		- each commit is a pointer to the repo at a point in time
			- each branch is a named pointer to a particular commit
	- **Relative References** using `^` and `~` to traverse commits in the `git log` so that you don't need to type even the minimum 6 characters of the commit hash.
		- `^` when given the name of a commit hash/branch name it will refer to the parent commit: `main^`
			- These can be stacked too so you can refer to grandparent commit with `main^^`
			- can also use with **HEAD** to traverse from current point: `git checkout HEAD^`
		- `~` will let you specify a number of commits to travel back instead of `git checkout HEAD^^^^` you can use `git checkout HEAD~4` to traverse 4 commits backward
	- **Forcing Branches** You can move what commit a branch is referencing with something like:
		- `git branch -f myBranch locationToMoveItTo`
	- **Reversing Commits** There are at least 2 ways to do this `git reset` and `git revert`
		- `git reset` move the branch backwards in time
		- `git revert` move the branch backwards in time and acts like the commit never even happened
	- `git cherry-pick <commit hash> <commmit hash> ...`
		- ![2021_04_27_image.png](https://cdn.logseq.com/%2F07ac90d5-a8a5-495c-84ae-a5c969228e383e15d4ae-be18-4a8f-acb1-c3e3cc45cbaf2021_04_27_image.png?Expires=4773158404&Signature=Tz~VjOeuALHDo~htM6IzYhAjMY6xItAyynFz4MnJhk1JuwNeQqhMgDmARACUARHT1pgrWRWvtdRuxTBPBVCZGtGwqJMN~yyT2xn12PKBGixRgjMdf4R~Q8m9wsm58~mjXNoL4M5bVb-WbGmV1m9RCOMw9UwiFb0nqN7ms7mroIC3MSZmlvDrbz8LpJPWkp~KlacU9ZeF6knUV2doFho0cckWfW9LsXiJ3y3goCEEleYOjC9WWDwNBDciRKukUXQZEeH87pkLGlr2NB2ZhYat4NhwlfNbdgRye~iTD7WMMX-p5hOYzuuFCxt0-7H8-5wboemZCELbhveVxvwsP70vSQ__&Key-Pair-Id=APKAJE5CCD6X7MP6PTEA)
		- `git cherry-pick c2 c4`
		- ![2021_04_27_image.png](https://cdn.logseq.com/%2F07ac90d5-a8a5-495c-84ae-a5c969228e382d520a7f-8f7e-4611-8688-f577103228a12021_04_27_image.png?Expires=4773158436&Signature=OVIU3Ae4tfpm0qsdn6a7~pHwIgTHuqNKtnIO7zb46Q2ccC~mLbV8RHgXErVUjRLjeYX3Ya80cR6sHTwqsFx~IW9ejEilesi1YNAr2UNeWN4uw8G8n7PxNHO-v30ZCMEsPfU36liohp6RoGfdpl5v-DfRrlREtKy7jUIofPrG0s0bs7QTIywuW-bB85LxFlI4BO7cavXXqlJhf5SRVVDKg7DSnmxJ4K4v-oxZGfzuBhAfsvU7Vh60JS1CjDI~zX-S7tZ8d5t~5dDl8FR0~J1L2eskouayjFNAIFtSpJ5cIuPH3gHIMXPgXF4UuFl6hv8BTu1vrPiXN5uG~X3Ck3YCyQ__&Key-Pair-Id=APKAJE5CCD6X7MP6PTEA)
	- **Tagging** To tag commits as a project milestone or something the commands are very simple
		- `git tag v1 <commit hash>` will tag what ever referenced commit hash with the tag _"v1"_
		- `git tag v1` will tag what ever commit hash **HEAD** is on with the tag _"v1"_
	- `git describe <ref>` If no ref is provided it will just look at wherever HEAD is. This can, however, be used on Tags.
		- If you have a tag on the first commit of the repo such as `0.1` with a message of `initialized repository` and then ran the command `git describe` all it would tell you is something like:
			- _"0.1-62-g07f34f4"_
				- _0.1_ for the tag
				- _62_ for the commits since that tag
				- _g07f34f4_ is the hash being described (your current one that hasn't been committed yet)
		- ![2021_04_27_image.png](https://cdn.logseq.com/%2F07ac90d5-a8a5-495c-84ae-a5c969228e38150b5d0a-c5e6-401b-b6ee-39fb4031aabe2021_04_27_image.png?Expires=4773160079&Signature=E6p6WMlzNrJ7yVeIR0bADUCYsOUg2QaJAYBnlyHNxG7fAK2XqQete8ZYAQ9yf7rxztozxD8Ya2DDk9GsITJuMpDHRvSaQePFgNkGYhAeflkD-ZDqntqPVNWsyD-TkxdX5Z1WfAhGcR1L6ixWbwAXnOgGa1YRFeqsyCwJOdBSWJfGHbJAJMmAgjQyS4~1-NI7K2ZXX-WYu-hg0GoN4QZ2BiNt4JdrWUN2~flky49CNhFNdZplz1eBLSr~m19CTHNIX3x8kPjHNMO0qzRXaTz6ersk5I2vPpzwcqT8MXoI77suIXgH9nsdFEu4fkxUu5Ac2nEeg8CbcOe91C18Hdi7oQ__&Key-Pair-Id=APKAJE5CCD6X7MP6PTEA){:height 256, :width 543}
# Obsidian notes
	- ## Working With Repositories
	- ### Making a Repository
	- #### Start Repository from existing directory then push to GitHub
	  
	  ```bash
	  git init
	  git add .
	  git commit -m 'message'
	  git remote add origin <url.git>
	  git push -u origin master
	  ```
	- ##### Set Global Configs
	  
	  ```bash
	  git config --global user.name "John Doe"
	  git config --global user.email johndoe@example.com
	  ```
	- ### Going Back in Time
	- #### Open a cloned repository from a particular commit
	- [SO](https://stackoverflow.com/questions/3555107/git-clone-particular-version-of-remote-repository)
	  
	  ```bash
	  git clone [remote_address_here] my_repo
	  cd my_repo
	  git reset --hard [ENTER HERE THE COMMIT HASH YOU WANT]
	  ```
	- ### Branching
	- #### Making work-trees
	- [ThePrimeagen](https://youtu.be/2uEqYw-N8uE)
	  
	  ```bash
	  git clone --bare <repo url.git> <name of the folder to create>
	  # ex:
	  git clone --bare git@github.com:tallguyjenks/CV.git CV
	  
	  
	  # makes a bare repo of my resume
	  # there's nothing in it, none of the files from the repo just git stuff
	  # THEN
	  
	  git worktree add master
	  git worktree add test
	  git worktree add feature
	  
	  # it takes the current commit at the HEAD of the repo (git pull at you're at the most recent) and this way # you're working with 3 folders basically 3 branches of the same repo but simultaneously. NO SWITCHING BACK & AND FORTH ?????????????????????
	  ```
	- ## Git Stash
	- ### Saving and moving changes
	  
	  ```bash
	  # say you're on master, and you have changes to docs and you're about to make a commit, but you realize "oh crap, I'm still on master, I needed to put this on a feature branch!" 
	  # you can run 
	  git stash push 
	  # to basically package up all those uncommitted changes into a "box" and shove it into a corner returning to a master branch that is a mirror of remote master (CLEAN!) 
	  # then make your branch, switch to it and run 
	  git stash pop 
	  # to grab your changes and put them onto the current working branch. 
	  ```