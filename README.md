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

