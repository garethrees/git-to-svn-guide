# Git to SVN :(

Some useful information can be found at [svnbook.red-bean.com](http://svnbook.red-bean.com)

## Create A Local Working Copy
```bash
$ svn checkout BRANCH FOLDER_NAME
```

### Example:
```bash
# Checks out repo/trunk in a folder called trunk
$ svn checkout https://code.example.com/repo/trunk

# Checks out repo/trunk in a folder called repo
$ svn checkout https://code.example.com/repo/trunk repo
```

### Git Equivalent
```bash
$ git clone REPO
```

## Create A New Branch
```bash
$ svn copy CURRENT_BRANCH NEW_BRANCH -m “MESSAGE”
```

### Example:

```bash
$ svn copy https://code.example.com/repo/trunk \
    https://code.example.com/repo/features/feature_branch \
    -m "Creating a private branch of /repo/trunk."
```

### Git Equivalent
```bash
$ git checkout -b BRANCH
```

## Switch To a Different Branch
```bash
$ svn switch BRANCH
```

### Example:

```bash
$ svn switch https://code.example.com/repo/features/feature_branch
```
### Git Equivalent

```bash
$ git checkout BRANCH 
```

## Keep The Branch In Sync

```bash
$ svn update 
```

### Example:

```bash
$ svn switch https://code.example.com/repo/trunk
$ svn update
$ svn switch https://code.example.com/repo/features/feature_branch
$ svn merge https://code.example.com/repo/trunk
& svn ci -m "Merge branch trunk into feature_branch" 
```

### Git Equivalent

```bash
$ git pull 
```

## Merge to Trunk

```bash
$ svn merge BRANCH 
```

### Example:

```bash
$ svn switch https://code.example.com/repo/trunk
$ svn update
$ svn merge --reintegrate https://code.example.com/repo/features/my_feature
$ svn update
$ svn commit -m "Merge branch my_feature into trunk" 
```

### Git Equivalent

```bash
$ git merge BRANCH 
```

## Status

```bash
$ svn status 
```


### Git Equivalent

```bash
$ git status 
```

## Committing

```bash
$ svn commit -m “MESSAGE” 
```

### Example:

```bash
$ svn update
$ svn status
$ svn add PATH/TO/NEW/FILES
$ svn commit -m “Added an awesome feature” 
```

### Git Equivalent

```bash
$ git commit -m “Added an awesome feature” && git push 
```

## Commit A Single File

```bash
$ svn commit FILE -m "MESSAGE" 
```

### Example:

```bash
$ svn commit app/models/awesome.rb -m "Adding some awesome" 
```


## View Repository Structure

```bash
$ svn ls REPO 
```

### Example:

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


### Git Equivalent

```bash
$ git branch -a 
```

## View Repository Details

```bash
$ svn info 
```

## Revert Changes

```bash
 $ svn revert 
```
 

### Example:

```bash
$ svn revert . -R
$ svn revert /PATH/TO/FILE 
```

### Git Equivalent

```bash
$ git checkout /PATH/TO/FILE 
```


## List latest revision

```bash
$ svn log 
```
### Example:

```bash
$ svn log /PATH/TO/FILE -v -l3 
```

### Git Equivalent

```bash
$ git log -n 3 
```

## View diff of a commit

```bash
$ svn log --diff 
```

### Example:

```bash
$ svn log -r 42256 --diff 
```

### Git Equivalent

```bash
$ git diff 29461219405dcdee17194d0e3112f160e1345d49 
```

## Merge Conflicts

Accept whatever the current directory structure is at this time:

```bash
$ svn resolve --accept working . -R 
```

## The “Git Way”

##### Clone Trunk:

```bash
$ svn checkout https://code.example.com/repo/trunk repo 
```

##### Create Feature Branch:

```bash
$ svn copy https://code.example.com/repo/trunk \
    https://code.example.com/repo/features/feature_branch \
    -m "Creating a private branch of /repo/trunk." 
```

##### Switch:

```bash
$ svn switch https://code.example.com/repo/features/feature_branch 
```

##### Make Changes:

```bash
$ rm *.php
$ rails new awesome_app 
```

##### Add New Files:

```bash
$ svn status
$ svn add . --force 
```

##### Commit New Files:

```bash
$ svn commit -m “Made some awesome” 
```

##### Switch to Trunk:

```bash
$ svn switch https://code.example.com/repo/trunk 
```

##### Update From Upstream:

```bash
$ svn update 
```

##### Merge New Feature:

```bash
$ svn merge --reintegrate https://code.example.com/repo/features/feature_branch 
```

##### Commit Merge:

```bash
$ svn commit -m “Merge branch feature_branch into trunk” 
```
