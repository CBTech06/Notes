# ---- [GIT] ---- 

      <[index.md]

## CREATE REPOSITORY USING COMMAND LINE
	curl -u CBT06:token https://api.github.com/user/repos -d '{"name":"SDL"}'

## SCHEME
		 Repository		Commit		Branch
	CbTech06/Notes 			11122020	main	
		
## TIPS
	* GET RAW FILES
		curl -O https://raw.githubusercontent.com/lattera/glibc/master/debug/execinfo.h

	* GET WIKI: Repo → https://github.com/jarun/nnn
		git clone https://github.com/jarun/nnn.wiki.git

## BASIC USAGE
  * Get third party lib			  git submodule update initOD
  * Remove GIT to the current folder	  rm -rf .git
  * Identify to github			  git config user.email "you@github.com" / user.name "name"
  * Create new local repository:	  git init
  * Download from an existing repository: git clone url
  * List files not commited:		  git status
  * Show full change history:		  git log
	
## BRANCHES
	
  List all branches:		git branch -a
  List Remote branches:	        git branch -r
  Local branch only		git branch -l / git branch
  Delete branch			git branch -d [local branch]
  Swith to branch branch names:	git switch -c "branch-name"
  Merge branch-name to current branch:	git merge branch-name
  Add file to stagging environment,ready for commit	git add [file-name] / [folder] 
  Commit all stagged files to versionned history	git commit -m "Your message about the commit"
  Add remote repository URL				git remote add origin url
  Fetch latest changes from origin and merge		git pull origin branch-name
  Push local changes to the origin			git push origin branch-name


## STAGGING
	
  Remove single file from the stagging area	   git reset HEAD -- [file] / [directory] 
  Remove commit from local repository              git reset --soft HEAD^
  Rewrite reset index 				   git rm --cached -r .
  Remove every file from git's index  		   git reset --hard

   [DESC]
	Put your desc into README.md and add it to stagging
	Image ![Alt text](Sokoban.png?raw=true "Sokoban")
 	 
## PROCESS
### INIT
 
  1. git init 
  2. git status (Index files)
  3. git add <filename>
  4. git commit -m "Your message about the commit"

### BRANCHES(PENDING)

  4. Create new branch git checkout -b new-branch
  5. To merge branch: git merge new-branch

### UPLOAD TO REPOSITORY
  6. git remote add origin https://github.com/captainchris06210/config.git
  7. git push -u origin master

* NEW COMMIT ON THE SAME REPO
  1. Add file to the current directory(example file.md)
  2. git add file.md
  3. git commit "Added File file.md on repo"



## VOC

  Staging(index)
  Commit: is a record of what files you have changed since the last time


