# Git to SVN :(

Some useful information can be found at [svnbook.red-bean.com](http://svnbook.red-bean.com)

## Create A Local Working Copy

    $ svn checkout BRANCH FOLDER_NAME

### Example:

    # Checks out repo/trunk in a folder called trunk
    $ svn checkout https://code.example.com/repo/trunk

    # Checks out repo/trunk in a folder called repo
    $ svn checkout https://code.example.com/repo/trunk repo

### Git Equivalent

    $ git clone REPO

## Create A New Branch

    $ svn copy CURRENT_BRANCH NEW_BRANCH -m “MESSAGE”

### Example:

    $ svn copy https://code.example.com/repo/trunk \
        https://code.example.com/repo/features/feature_branch \
        -m "Creating a private branch of /repo/trunk."

### Git Equivalent

    $ git checkout -b BRANCH

## Switch To a Different Branch

    $ svn switch BRANCH

### Example:

    $ svn switch https://code.example.com/repo/features/feature_branch

### Git Equivalent

    $ git checkout BRANCH

## Keep The Branch In Sync

    $ svn update

### Example:

    $ svn switch https://code.example.com/repo/trunk
    $ svn update
    $ svn switch https://code.example.com/repo/features/feature_branch
    $ svn merge https://code.example.com/repo/trunk
    & svn ci -m "Merge branch trunk into feature_branch"

### Git Equivalent

    $ git pull

## Merge to Trunk

    $ svn merge BRANCH

### Example:

    $ svn switch https://code.example.com/repo/trunk
    $ svn update
    $ svn merge --reintegrate https://code.example.com/repo/features/my_feature
    $ svn update
    $ svn commit -m "Merge branch my_feature into trunk"

### Git Equivalent

    $ git merge BRANCH

## Status

    $ svn status

### Git Equivalent

    $ git status

## Committing

    $ svn commit -m “MESSAGE”

### Example:

    $ svn update
    $ svn status
    $ svn add PATH/TO/NEW/FILES
    $ svn commit -m “Added an awesome feature”

### Git Equivalent

    $ git commit -m “Added an awesome feature” && git push

## Commit A Single File

    $ svn commit FILE -m "MESSAGE"

### Example:

    $ svn commit app/models/awesome.rb -m "Adding some awesome"

## View Repository Structure

    $ svn ls REPO

### Example:

    $ svn ls https://code.example.com/repo
    branches/
    features/
    tags/
    trunk/

    $ svn ls https://code.example.com/repo/features
    sprint_17/
    sprint_18/
    sprint_19/

### Git Equivalent

    $ git branch -a

## View Repository Details

    $ svn info

## Revert Changes

    $ svn revert

### Example:

    $ svn revert . -R

## Merge Conflicts

Accept whatever the current directory structure is at this time

    $ svn resolve --accept working . -R

## The “Git Way”

##### Clone Trunk:

    $ svn checkout https://code.example.com/repo/trunk repo

##### Create Feature Branch:

    $ svn copy https://code.example.com/repo/trunk \
        https://code.example.com/repo/features/feature_branch \
        -m "Creating a private branch of /repo/trunk."

##### Switch:

    $ svn switch https://code.example.com/repo/features/feature_branch

##### Make Changes:

    $ rm *.php
    $ rails new awesome_app

##### Add New Files:

    $ svn status
    $ svn add . --force

##### Commit New Files:

    $ svn commit -m “Made some awesome”

##### Switch to Trunk:

    $ svn switch https://code.example.com/repo/trunk

##### Update From Upstream:

    $ svn update

##### Merge New Feature:

    $ svn merge --reintegrate https://code.example.com/repo/features/feature_branch

##### Commit Merge:

    $ svn commit -m “Merge branch feature_branch into trunk”