# Git

## Introduction to Git

* Working directory: Stores the code we are currently writing (after the new version development is completed, we can submit the new version)
* Staging area: Temporarily saves the content to be submitted (After the new version is submitted, it will be stored in the local repository)
* Local repository: A version control repository located on our computer (It stores the addition and deletion information of each version of the current project)
* Remote repository: A version control repository located on the server (The version information on the server can be pushed up to the local repository or retrieved from the server to the local repository)

***

**It is a distributed control system. Therefore, in general, each of our computers has a local repository, and all of us jointly push the version update information to the remote repository.**

## The operations of Git

### After installation, the subsequent operations

* After the installation is completed, you need to set a username and email address to distinguish different users:

  ```
  git config --global user.name "Your Name"
  git config --global user.email "email@example.com"
  ```

### Create a local repository

* After inputting, a .git directory will be automatically generated. Note that this directory is a hidden one, and the current directory is our working directory

  * ```
    git init
    ```

* After the creation is successful, we can check the current status.

  * ```
    git status
    ```

### Operations after modifying and adding the local repository

* If the work directory changes, it will prompt **"Untracked files"**

* We add the changed files to the staging area, and then they will automatically become **tracked**.

  * ```git
    git add hello.txt
    
    # or another operation tp add all contents in the directory at one timeAdd all the files in the directory at one time
    
    git add.
    ```

### Add the files in the staging area to the local repository

* ```
  git commit -m -a 'Hello world'
  ```

* The quotation marks following the -m parameter are the description of the submitted content. -a is to place the modified files that are not in the staging area into the staging area and then perform the submission operation.

### View submission history

* ```
  git log #Submission Record
  git log --graph #Graphical presentation of submission records
  git show [You can also add the commit ID to view the specified commit record]#View the detailed information of the most recent change
  git log --all --graph
  ```

### .gitignore

* We can create a .gitignore file to define a list of files to be ignored. If a file in the ignore list exists and is not in the tracked state, then Git will not perform any checks on it.

* ```git
  # This way, it won't match all files that end with ".txt" 
  
  *.txt
  
  # Although all files ending with ".txt" have been excluded above, this does not mean that they are all excluded. 
  
  ! 666.txt
  
  # You can also directly specify a folder. All the files in that folder will be completely ignored.
  
  test/
  
  # All files in the directory with the extension "txt", but excluding subdirectories.
  
  xxx/*.txt
  
  # All files with the extension "txt" in the directory, including those in subdirectories.
  
  xxx/**/*.txt
  
  ```

### Roll-back

* When we want to revert to an earlier version, we can perform the rollback operation. After execution, the content of the workspace can be restored to the state of the specified commit.

  * ```
    git reset --hard commitID
    ```

* View the operation records of all branches

  * ```
    git reflog
    ```

* This way, you can find the previous commit ID and simply reset it again.

### Branch

* We can view the existing branches in the current repository by using the following command.

  * ```
    git branch
    ```

* We found that by default, there is a "master" branch, and we are using the "master" branch as well. Generally, the "master" branch contains updates for the official version, while other branches are updated more frequently during development. Next, let's create a new branch based on the current branch:

  * ```
    git branch test #A new branch named "test" has been created.
    ```

* Delete branch "test"

  * ```
    git branch -d test
    ```

#### Switch branches

* Switch to the "test" branch

  * ```
    git checkout test
    ```

#### Merging branches

* Now, switch the branch to the master branch.

  * ```
    git checkout master
    ```

* Use the merge branch command

  * ```
    git merge test
    ```

* If there is a "conflict" indicated

  * ```
    git diff
    ```

  * View the conflict

  * **Solution: Roll back the version of the master branch to before the modification of hello.txt, or directly modify it to the latest version's content. This way, there will be no conflicts. Then, perform the merge operation again. Now, the two branches have successfully merged into a single branch.**

#### Branching base change

* Apart from directly merging branches, we can also perform a rebasing operation. This is different from merging. Merging is the process where a branch returns to the main trunk, while rebasing directly modifies the starting point of the branch. For example, if we want to rebase line 'test' onto 'master', then 'test' will move the branch's starting point to the position of the **last commit on 'master'**:

  * ```
    git rebase master
    ```

#### Cherry pick

* We can also choose to apply the commits from another branch to the current branch. This operation is called "cherry pick".

* ```
  git cherry-pick <commit id> # Merge a single commit separately
  ```

* Here, we create a new file on the master branch, commit this update, and then apply this update to the test branch using the cherry-pick method.

## Remote

The remote repository is actually a repository located on the server. It can store our version history remotely and enable multiple people to collaborate on the project simultaneously. Everyone can synchronize others' versions and view others' version submissions, which is equivalent to hosting our code on the server for management.



### Remote account authentication and push notifications

* After creating the repository, we can push the contents in the local repository to the remote repository by using the push function.

  * ```
    git remote add [name] [remote repository address] 
    git push [remote repository name] [local branch name[:remote branch name]]
    ```

  * If the local branch and the remote branch have the same name, no further processing is required.

### A once-and-for-all connection method

* We can generate an RSA public key locally.

  * ```
    ssh-keygen -t rsa
    cat ~/.ssh/github.pub
    ```

  * Next, we need to upload our public key to GitHub. When we visit GitHub again, it will automatically verify and we won't need to log in. Later, in the Linux section, we will explain in detail the principle of SSH.

### We can link the remote and local branches. After the linking process, there is no need to specify the branch names anymore.

* ```
  git push --set-upstream origin master:master
  git push origin
  ```

### Complete process of pushing remote repository (local files have been modified)

* ```
  git commit -a -m 'Modify files'
  git log --all --oneline --graph
  git push origin master 
  git log --all --oneline --graph
  ```

### Clone Project

* ```
  git clone [Remote repository address]
  ```

### Grabbing, pulling and conflict resolution

* When there are multiple local repositories corresponding to one remote repository, for example, in a team, N people are all using the same remote repository, but each of them is only responsible for writing and pushing the code of their own business part, which is what we commonly call collaborative work. In this case, coordination is necessary. 
  For example, if programmer A has completed his module, then he can submit the code and push it to the remote repository. At this point, programmer B also needs to start writing code. Since the remote repository has the submission records of other programmers, the local repository of programmer B is not consistent with the remote repository. At this time, a pull operation needs to be performed first to obtain the latest submission in the remote repository.

* ```
  git fetch [remote repository] # Fetch: Only retrieve without merging the remote branches. We need to manually merge them later before committing.
  git pull [remote repository] # Pull: Retrieve + Merge
  ```

