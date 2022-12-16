# 1. Git to SVN :(

Some useful information can be found at [svnbook.red-bean.com](http://svnbook.red-bean.com)

## 1.1 Create A Local Working Copy
```bash
$ svn checkout BRANCH FOLDER_NAME
```

### 1.1.1 Example:
```bash
# Checks out repo/trunk in a folder called trunk
$ svn checkout https://code.example.com/repo/trunk

# Checks out repo/trunk in a folder called repo
$ svn checkout https://code.example.com/repo/trunk repo
```

### 1.1.2 Git Equivalent
```bash
$ git clone REPO
```

## 1.2 Create A New Branch
```bash
$ svn copy CURRENT_BRANCH NEW_BRANCH -m “MESSAGE”
```

### 1.2.1 Example:

```bash
$ svn copy https://code.example.com/repo/trunk \
    https://code.example.com/repo/features/feature_branch \
    -m "Creating a private branch of /repo/trunk."
```

### 1.2.2 Git Equivalent
```bash
$ git checkout -b BRANCH
```

## 1.3 Switch To a Different Branch
```bash
$ svn switch BRANCH
```

### 1.3.1 Example:

```bash
$ svn switch https://code.example.com/repo/features/feature_branch
```
### 1.3.2 Git Equivalent

```bash
$ git checkout BRANCH 
```

## 1.4 Keep The Branch In Sync

```bash
$ svn update 
```

### 1.4.1 Example:

```bash
$ svn switch https://code.example.com/repo/trunk
$ svn update
$ svn switch https://code.example.com/repo/features/feature_branch
$ svn merge https://code.example.com/repo/trunk
& svn ci -m "Merge branch trunk into feature_branch" 
```

### 1.4.2 Git Equivalent

```bash
$ git pull 
```

## 1.5 Merge to Trunk

```bash
$ svn merge BRANCH 
```

### 1.5.1 Example:

```bash
$ svn switch https://code.example.com/repo/trunk
$ svn update
$ svn merge --reintegrate https://code.example.com/repo/features/my_feature
$ svn update
$ svn commit -m "Merge branch my_feature into trunk" 
```

### 1.5.2 Git Equivalent

```bash
$ git merge BRANCH 
```

## 1.6 Status

```bash
$ svn status 
```


### 1.6.1 Git Equivalent

```bash
$ git status 
```

## 1.7 Committing

```bash
$ svn commit -m “MESSAGE” 
```

### 1.7.1 Example:

```bash
$ svn update
$ svn status
$ svn add PATH/TO/NEW/FILES
$ svn commit -m “Added an awesome feature” 
```

### 1.7.2 Git Equivalent

```bash
$ git commit -m “Added an awesome feature” && git push 
```

## 1.8 Commit A Single File

```bash
$ svn commit FILE -m "MESSAGE" 
```

### 1.8.1 Example:

```bash
$ svn commit app/models/awesome.rb -m "Adding some awesome" 
```


## 1.9 View Repository Structure

```bash
$ svn ls REPO 
```

### 1.9.1 Example:

```bash
$ svn ls https://code.example.com/repo
branches/
features/
tags/
trunk/

$ svn ls https://code.example.com/repo/features
sprint_17/
sprint_18/
sprint_19/ 
```


### 1.9.2 Git Equivalent

```bash
$ git branch -a 
```

## 1.10 View Repository Details

```bash
$ svn info 
```

## 1.11 Revert Changes

```bash
 $ svn revert 
```


### 1.11.1 Example:

```bash
$ svn revert . -R
$ svn revert /PATH/TO/FILE 
```

### 1.11.2 Git Equivalent

```bash
$ git checkout /PATH/TO/FILE 
```


## 1.12 List latest revision

```bash
$ svn log 
```
### 1.12.1 Example:

```bash
$ svn log /PATH/TO/FILE -v -l3 
```

### 1.12.2 Git Equivalent

```bash
$ git log -n 3 
```

## 1.13 View diff of a commit

```bash
$ svn log --diff 
```

### 1.13.1 Example:

```bash
$ svn log -r 42256 --diff 
```

### 1.13.2 Git Equivalent

```bash
$ git diff 29461219405dcdee17194d0e3112f160e1345d49 
```

## 1.14 Merge Conflicts

Accept whatever the current directory structure is at this time


## 1.15 The “Git Way”

##### 1.15.1.1.1 Clone Trunk:

```bash
$ svn checkout https://code.example.com/repo/trunk repo 
```

##### 1.15.1.1.2 Create Feature Branch:

```bash
$ svn copy https://code.example.com/repo/trunk \
    https://code.example.com/repo/features/feature_branch \
    -m "Creating a private branch of /repo/trunk." 
```

##### 1.15.1.1.3 Switch:

```bash
$ svn switch https://code.example.com/repo/features/feature_branch 
```

##### 1.15.1.1.4 Make Changes:

```bash
$ rm *.php
$ rails new awesome_app 
```

##### 1.15.1.1.5 Add New Files:

```bash
$ svn status
$ svn add . --force 
```

##### 1.15.1.1.6 Commit New Files:

```bash
$ svn commit -m “Made some awesome” 
```

##### 1.15.1.1.7 Switch to Trunk:

```bash
$ svn switch https://code.example.com/repo/trunk 
```

##### 1.15.1.1.8 Update From Upstream:

```bash
$ svn update 
```

##### 1.15.1.1.9 Merge New Feature:

```bash
$ svn merge --reintegrate https://code.example.com/repo/features/feature_branch 
```

##### 1.15.1.1.10 Commit Merge:

```bash
$ svn commit -m “Merge branch feature_branch into trunk” 
```

