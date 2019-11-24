# Pantri

Pantri is an app which enables users to easily keep track of the items in their pantry and fridge, so when they shop, they know exactly how much to buy.
TODO: sample screenshots

## Architecture
[<img src="https://docs.google.com/drawings/d/e/2PACX-1vRoPN0yBtnrPnrU0m25f1EqlxoNF3XG4B0rmVfVPnELtxN5OAdUKHyjqEkI8GzrEhgoiVCSDRUjnDfd/pub?w=1350&amp;h=700">](https://docs.google.com/drawings/d/1fx1nooEFF1EThIcaz7oLuxJ-Xyhhrd2AMjO_ypzqe7U/edit?usp=sharing)

## Setup

1. Clone this repo
2. Setup submodules (see below)

For additional setup please see the submodule READMEs, as there is specific information for setting up each repository.

### Working with git submodules
Why submodules? As per this [article](https://gist.github.com/gitaarik/8735255), a submodule "is basically a repository embedded in your __main__ repository." Specifically, submodules point to commits on a separate repository, and the commit versions need to be managed. The following sections will outline how this flow works. (All commands below should be run in the __main__ repository)

#### Submodule setup
If a new submodule is created by one person, first retrieve the submodule information with a normal `git pull`. Then, initiate the submodules:
```
git submodule update --init --remote --rebase
```
Next, since the submodules are initially set in a detached HEAD state, run:
```
git submodule foreach git checkout master
```
Great! Your submodules should be perfectly setup now.


#### Submodule updating
Use case: A teammate updated a repository, and your local should be up to date.
```
git pull --rebase
git submodule update --remote --rebase
```
This rewinds your local head back on each submodule and applies each commit sequentially in the order they were committed.

#### Updating a submodule commit
Use case: You updated the master of a submodule and the main repository needs to point to the new commit. Specifically, `git status` gives you:
```
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   SUBMODULE_PATH (new commits)
```
Just git add, commit, and push it (the submodule path can be found in .gitmodules). Anyone who has updated their submodules according to the instructions above can do this. In the grand scheme of themes the main repo's pointers being out of date doesn't actually affect anything.
```
git add <SUBMODULE_PATH>
git commit -m "submodule <SUBMODULE_PATH> updated"
git push
```

#### Creating a new submodule
First, create the new repository with all the appropriate settings, permissions, etc.
Then, in the __main__ repository:
```
git submodule add -b master <REPOSITORY_URL> <PATH>
git submodule update --remote --rebase
```
Make sure the new repo is not in a _detached HEAD_ state.

## Deployment

At the moment we are not deploying the app. In the future we would like to publish on the Apple App store and Google Play store. For now, we are exclusivly demoing locally.

## User-Configurable Settings
- Range for item to be considered "expiring soon"
- Disable specific auto-tagging

## Authors

 - Stephen Crowe
 - Madison Hazard
 - Max Lata
 - Raphael Preston
 - Mike Zhu

## Acknowledgments

- [Initial git submodule article](https://gist.github.com/gitaarik/8735255)
- [Detailed git submodule usage](https://medium.com/fiverr-engineering/working-with-git-submodules-ec6210801e07)
