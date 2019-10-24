# Pantri

TODO: super short project description, some sample screenshots or mockups that you keep up-to-date.

## Architecture
[<img src="https://docs.google.com/drawings/d/e/2PACX-1vRoPN0yBtnrPnrU0m25f1EqlxoNF3XG4B0rmVfVPnELtxN5OAdUKHyjqEkI8GzrEhgoiVCSDRUjnDfd/pub?w=1350&amp;h=700">](https://docs.google.com/drawings/d/1fx1nooEFF1EThIcaz7oLuxJ-Xyhhrd2AMjO_ypzqe7U/edit?usp=sharing)

## Setup

1. Clone this repo
2. Setup submodules (see below)
3. TODO

TODO: how to get the project dev environment up and running, npm install etc, all necessary commands needed, environment variables etc

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
git pull
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
Just git add, commit, and push it. (The submodule path can be found in .gitmodules)
```
git add <SUBMODULE_PATH>
git commit -m "submodule <SUBMODULE_PATH> updated"
git push
```

## Deployment

TODO: how to deploy the project

## Authors

 - Stephen Crowe
 - Madison Hazard
 - Max Lata
 - Raphael Preston
 - Mike Zhu

## Acknowledgments

- [Initial git submodule article](https://gist.github.com/gitaarik/8735255)
- [Detailed git submodule usage](https://medium.com/fiverr-engineering/working-with-git-submodules-ec6210801e07)
