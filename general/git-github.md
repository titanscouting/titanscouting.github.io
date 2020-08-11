---
permalink: /general/git-github
title: Setting Up Git and Github
---

### Download and Install [Git](https://git-scm.com/downloads)
* Keep everything as default in the installer (if you don’t like Vim as the default editor you can set it to Nano; it will only show up when you resolve merge conflicts in the terminal)   
* You MUST restart Visual Studio Code (VSCode) after installing Git in order for its Git integrations to work

### Create a [GitHub Account](https://github.com/join) 
* (it's free of charge)    
* If you're a student, the [GitHub Student Developer Pack](https://education.github.com/pack) is a good way to get free things   
  
### Set GitHub Credentials in Git
* Go to the Terminal (on Windows this is either GitBash or Powershell, on Mac or Linux it's Terminal)
* once you're there run the following commands:   
  * `git config --global user.name <your GitHub username>`   
  * `git config --global user.email <the email you signed up to GitHub with>`   
* You can confirm these commands worked by typing `git config --global user.name` (user.email for email)

You would repeat this process (aside from git init and creating a new GitHub repo) whenever FTC releases an official update to their repo   
To remove a remote, use `git remote rm <remote-name>` so you can repeat the process again without naming conflicts.  
You could also skip creating new remotes altogether but it could get confusing (especially when FTC inevitably moves repos)  

### Cloning an existing Repository
A repository (repo) is the remote storage space for your code   
Cloning a repo downloads the repo onto your computer and sets up its configuration for use with git   
#### Steps:
* Open VSCode and press "Ctrl-Shift-G" to open the source control panel.
* Select "Clone Repository".
* Paste the URL of the repo you would like to clone/.
* Choose an empty folder to clone into for "Directory".
* Click "Clone".
* Once it finishes, click "Open" on the dialog in the bottom-right corner. 

### Git Usage
Run Git commands through the Git/Github extension in VSCode. 
Make sure you’re on the right branch as well as under the right folder

* To retrieve code from GitHub's remote repositories, use `git pull`
  * it fetches all of the code from the remote repository (i.e. the code stored on GitHub), and merges it into your local repo (i.e. the folder on your computer) 
  * this is how you pull changes that other people have made onto your computer
  * you don't have to do this when you first download a repo - it is downloaded up to date.
* To push your changes from your local computer to GitHub:
  * First use `git add <file path>` - this will prepare the file in question to be committed as a definite change
    * if you want to add every file currently changed, use `git add *`
  * Next use `git commit -am <commit name>` - this will make the changes on your local repository official.
  * Lastly use `git push` to transfer your local changes to the remote GitHub repository.
    * you can push more than one git commit at a time; git will maintain the order accordingly.
    
### Branching
Branches allow multiple versions of the code to coexist at once, making team development more streamlined. For example, I can have the master branch for the official code, and another branch called a new API route for `new-api-1`
* To switch to an existing branch, run: `git checkout <branch_name>`. You may need to pull after switching
* To create a new branch (from the current branch) and switch to it, run: `git checkout -b <branch_name>`
* The master branch is usually restricted from direct changes, as it is meant for code that is tested and absolutely works. For this reason, changes are made to master through merging into it from other branches.

### Merging
GitHub has its own built-in feature to make merging branches team-friendly - Pull Requests.
* Pull Requests allow us to view changes and request reviews before going through with a merge
* You should always have a trusted administrator review your Pull Request and merge it
* All your code should pass automated code checks and be free of linting errors.

#### What happens if I forgot to push my changes but want to pull in new changes? (there are changes to both pull and push)
* First, once your changes are complete, commit them (don’t push)
* Then run a special pull: `git pull --rebase`
  * Reorders the commits to avoid merging
* Sometimes merging is unavoidable.
  * If Git is able to automatically merge, then we’re good
  * Otherwise, if there are conflicts, VSCode may be able to help you resolve them. If not, contact an admin to get help resolving them - [this page](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/resolving-a-merge-conflict-using-the-command-line) has information about resolving merge conflicts

### Attribution
Large parts of this article were sourced from [High Oak Robotics](https://highoakrobotics.github.io/FTC-Control-Docs/).
