------Understanding Git/Github--------

git --> software
github --> service 
version control system --> tracks files for changes

1) Repository(Repo)
Git on system v/s tracking Repo
If you have git on system it does not mean it is tracking all the folders/Repos, you have to mention to it 
what all folders to track.

# git --version / git --v -> to check the version of git installed
# git status -> to check if any folder is tracked by git or not, if no folder is tracked it gives error message
# git init -> (only to initialize one time per project) to initialize the tracking of the folder 

.git -> a hidden folder to keep history of all files and sub-folders

2) Commit --> check points
write-> Add -> Commit
working directory -> git add -> Staging Area -> git commit -> Repo -> git push -> github

3) Stage 
To add the file in the staging area use the 'git add' command

# git add <file> -> adds the file to the staging area, we can add single file or multiple files with space in between
# git add . -> used to add all the files present in the directory to the staging area

-To Unstage the file use
# git rm --chached <file> || git restore --staged <file> 

Now to commit file use the 'git commit' command
# git commit -m "message to be given" -> git commit is a bit tricky, so always add a message to the commit command, 
                                         just running git commit is not enough, we have to type git commit -m to give a message.
If we do not give a message while commiting, git opens the default set code editor, and tells to add a message.
The default code editor of git is VIM editor, you can change it while downloading git to any code editor of your choice.

TO ESCAPE FROM VIM EDITOR --> esc + : + q / q + ! 

4)---Staging Area & Commits---(summary)
# git init
creat file or files
# git add <file1> <file2> || git add .
# git status
# git commit -m "good describing message"
# git status
# git log (log of commits with commit hash)

# git log --> gives information about all the commits done with the commit id, etc.
# git log --oneline -> does the same works but in short 

5) Atomic commits
Keep commits centric to one feature, one component or one fix. Focused on one thing.
--> Present or Past commit message
    Depends(present tense, imperative)

6) Git Configuration file
# git config --global 
# git config --global user.name "Aditya Dawale" -> sets the user nameof the user
# git config --global user.email "adityadawale64@gmail.com" -> sets the email of the user
# git config --global core.editor "code --wait" -> to change the default code editor of git to prefered one.

@ if you want to check the 'git config' file just go to the root of directory, and type "cat .gitconfig" , you will see all the blocks

7) Git ignore
# touch .gitignore -> this file holds all the sensitive information, which we want to keep safe. 
therefore git ignores the information in this file. Eg. node_modules, API keys, etc.
just add the folder in the .gitignore and the folder will be ignored by git.
- can get templet online, .gitignore generator

8) Commit Behind the scene
- in the ecosystem of git every commit is dependent on the previous commit, except the first commit
(Hash, Parent->null, info) <-- (Hash, Parent, info) <-- (Hash, Parent, info)
                                second commit depends       third commit depends 
                                on the first commit         on the second commit, points towars the second parent.

9) Git Branches
like an alternative timeline
- head -> master ; head points to where a branch id currently at
# git branch -> to check on which branch we are currently working on; initially head points to the master/main branch
# git branch <branchname> -> to create a new branch 
# git checkout <branchname> -> to move to the branch created; head now points to the newly created branch

- commit befor switching to another branch
- go to .git folder & checkout head file

---Branch Summary---
# git branch
# git branch <branchname>
# git switch <branchname> || git checkout <branchname>
# git switch -c <branchname>    --> (creates a branch and moves there)
# git checkout -b <branchname>  --> (creates a branch and moves there)

10) Merge the Branches
Go to the branch in which you want to merge the other branch,
In this case, I wanted to merge the 'nav-bar' branch in the 'master' branch, so I went to the master 
branch and merged the both branches.

# git merge <branchname> --> wrote the command in the master branch
# git branch -d nav-bar -> -d stands for delete the branch, the branch is deleted but the history remain.

- CONFLICTS arrive during merging, keep whatever you want, remove markers and save 
- can be resolved in the code editor, this is what conflict looks like
        >>>>>Head 
        line 1  --> code in the master branch
        line 2
        ========
        line 3  --> code in footer branch
        <<<<<footer

11) Git Diff 
# git diff - (informative command, Compare working with staging)

-> HOW to read diff
- a -> file1    &   b -> file2  (file1 and file2 are the same file over time, means they are the same file form two different times)
 --- file1 -> indicate changes in the file (do not indicate content deleted or added)
 +++ file2 

# git diff --staged -> shows the differences between the same file before staging and after staging
                        bascially we made some changes in file, then added the file using 'git add' 
                        and now we are comparing both the files using 'git diff'

# git diff <uniqueid> <uniqueid> -> this can also be used to compare 
# git diff <uniqueid>..<uniqueid> 

12) Git Stashing
- Create a repo, work on it and commit it on the main
- Switch to another branch and work
- Conflicting changes do not allow to switch branch, without commit
- Let's say we are working on a branch and we want to switch to another branch to fix some bugs but we have not yet 
  commited the changes in the working branch, we can stash those changes and move to the other branch. 
  It's just like stshing those changes on a shelf and then bringing them back on returing to the working branch. 

# git stash -> (you can switch branch)
# git stash pop -> (bring back those changes)
# git stash apply -> (apply chamges and keep them in stash)

---More Commands---
# git checkout <hash>   -> (Detach Head) :new branch
# git switch main       -> (re-attach head)
# git checkout HEAD ~2  -> (look at 2 commits prior)
# git restore filename  -> (get back to last commit version)

13) Git Rebase - NEVER RUN THIS COMMAND FROM THE MAIN/MASTER BRANCH
- It is an alternative to merging
- clean up tool (clean up commits) 

# git init -> work and commit on main branch
# git switch -c footer -> work and add footer in the feature branch
# git commit -am "add footer text"
# git switch main -> work and add hero section on main branch
# git switch footer 
# git merge main -> work and add more info in footer; if there is more work on main, do more merge
 --> get on footer branch and Rebase
# git rebase main -> work and add more on main branch, more to footer branch
# git rebase main

    --> NEVER Rebase commits that you have shared, pushed to Github

)------GITHUB------( Go through the git documentation to access your git hub through Git, SSH documentation
- Git is a software and github is a service tohost git online.
- Github -> Collaboration + Backup + Open Source
- Gitlab or Bitbucket

# git clone <Url>
# git config --global user.name "Aditya Dawale"
# git config --global user.email "dawaleaditya08@gmail.com"

- Setup SSH keys to connect with Github, Github uses SSH to allow you to push code. 
  Passoword based code push is not allowed.
  Check Instructions for your OS on github website, as that's beat & updated resourse.

# git remote -v
# git remote add name url
# git remote add origin(default name given by github) https://github.com/Artsyadi/Learn-git
# git remote rename oldname newname
# git remote remove name

# git push <remote> <branch>
# git push origin main
# git push <remote> localBranch : remoteBranch

# git push -u origin main
    -u setup an upstream that allow you to run future command 
# git push 
    and it push the code directly to github


