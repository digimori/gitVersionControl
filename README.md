# Self-Study notes for Git, Github and Version Control

## Version Control using Git and the Command Line:

### Working Directory

- In the command line:

```
cd rootFolder // Or whatever you have called your equivalent
mkdir folderName // Make Directory
cd folderName // Change Directory into the previously named folder
ls // Check for other directories or files
touch fileName // Create file
open -a fileName // Opens file
git init // Initialises an empty Git repository

```

- If you CD into the folder, then run the ls command again with a -a flag, it will show your created file and .git file on the command line
- This is used to track your changes in order to perform version control.

### Staging Area:

- This is where you choose which files in your working directory that you want to commit
- To check what files are currently in your staging area or what files are being tracked:

```
git status
```

- This will give the branch information, whether there are any commits or staged files.
- Untracked files will be in red.
- To stage, we use the following commands:

```
git add <filename> // You can simply use . if you want to commit everything in the current working directory
```

- To check if it has been staged successfully, use git status again and the file will now be in green
- The next part of this process is the commit stage.

```
git commit -m"Message goes here"
```

- the -m flag is to provide a message to the commit to give context of what has been changed between versions
- Present tense with messages is most common convention, avoid past.

- To check which commits have been made:

```
git log
```

- This will give the hash (unique identifier for the commit), author of the commit and the date/time that it was committed along with the files.

- Revert changes in the local directory:

```
git diff <filename> // Shows changes
git checkout <filename> // This will revert to the previous committed version (Not pushed! This is different!)
```

## Git Remote Repositories:

- Create Repository on Github
- Copy the URL of the Repo that you want to use remotely
- Use the command line:

```
git remote add origin <url>
git push -u origin main // Links up local and remote repositories and pushes local commits to it
```

- The main branch is your main branch of commits, which are like save points.

## Gitignore:

- Choose which files that you do not want tracked
- This is especially useful to not commit big, unnecessary folders (like node modules), or secret keys(API, passwords etc)
- .DS_Store files often end up committed from locals and they're not necessary here and so can be ignored.

Create the gitignore file:

```
touch .gitignore
```

- Inside gitignore, name the files and folders that you want ignored and not pushed. eg:

```
.DS_Store
.env // This is usually where secret keys are kept
secrets.txt
*.log // * This wildcard means that everything with this file extension will be ignored, ie: filename.log, file2.log
```

- If you do accidentally commit (not push) a file, this can be removed before it makes it to github:

```
git rm --cached -r . // This will remove everything from the staging area
```

## Git Cloning

- Cloning a remote repository to use as a local repository on your desktop:

```
git clone <url>
```

- This will pull all commits and branches from the repo
- Often used to build on existing code (Using a copy)

- This will need to be installed in order to also use the dependencies needed:

```
cd repoRootFolder
npm install
```

- If using someone elses open source, there will usually be documentation on the steps that follow this (ie if you need to add scripts or echos, also the commands to open the server)

## Pull Requests, branching and merging:

- Branches are offshoots from the main branch. They can be used, for example, for experimentation without committing to the main.

```
git branch name-of-branch
```

- You'll usually be working on branches in a dev environment, and then when you've completed the code in the background, can perform a merge request, like so:

```
git checkout main // Takes you back to the main branch
git merge name-of-branch
:q! // Save and quit
git push origin main -u // Push the changes upto the main
```

- The previous branch will still exist, but the changes will now be absorbed from the branch to the main
- Prevents breaking of the main branch whilst experimenting with other features

## Forking and Pull Requests:

Forking:

- Copying a remote repository to work on it yourself to your own github account, not the same as cloning where it is cloned to a local repository
- Once there is a remote copy, this can then be cloned to your local repository in order to work on it yourself

Pull Request:

- If someone forks a repository, makes changes and then wants to add them back to the original repo, they can make a pull request
- These are like suggested changes where the original owner can decide if they want the changes made by the person who forked the repo merged into their work
- So, in essence, you "pull" those changes over to the original code and can merge the repos
