---
layout: post
title:  "Git at Work!"
categories: [ Git ]
author: hyeon
image: assets/images/alphameme.jpg
tags: [ featured ]
---
> The title of this page is a spoof on ["Cells at Work!"](https://en.wikipedia.org/wiki/Cells_at_Work!).

Commit messages on Git is extremely important, especially if the project gets bigger. It helps you figure out the changes made to the file, without asking your colleagues in detail. However, writing commit messages is sometimes very annoying. If you are running a project on your own, and if you know what's going on in your project, maybe specific comments are not needed. If you don't want to write brief commit messages in the project that nobody might see, let's throw it away!

### Let's get started
`work` will start *working* on basic kinds of stuff on the current branch by calling it using this statement.
```bash
git work
```
It will do three different things; pull changes going on the remote repositories, commit the changes with a timestamp, and pushes back to the remote repository.

You can select a specific work that `work` will perform, using options.
```bash
git work -c #commit only!
```

### Calling the branch
At-mark `@` *calls* the branch to the program; it means that the branch is checkouted.
Once the branch is called, `work` will start to *work*; pull, commit, and push on the specified branch. If there is no such branch in both local and remote, it automatically branches out to a new branch.
**Check out that the command not only moves the working branch to the mentioned branch but also performs things in default if there are no options.**
```
git work @branch @done
```
`@done` command can be omitted, and it is optional; actually, it just sends you back to the branch where the program first started. 

```bash
#working in master branch
git work @hotfix <something>         #stays in hotfix branch
git work @hotfix <something> @done   #returns to master branch
```

Calling the branch could be chained. For example, the following command first pushes the changes you made to `develop` branch. Then it pulls the changes from the `hotfix` branch to the `release` branch and compares the merged `release` branch with the `develop` branch.
```bash
#working in develop branch
git work
git work @release -f @hotfix @. -d
```
`@.` is a short name for the current branch at the moment you call it; in this case, `release` branch. It is also the default value of the branch when nothing else is mentioned.

### Calling the remote repository

Sharp, or a hashtag `#` will *call* the remote repository.
```
git work @release -f #johndoe
```
The default value is `#.` if you don't specify the remote. This is another name for the `origin` remote.

#### Caution
Based on the syntax defined, the following code will work, but it looks terrifying. Note that writing too long chain will decrease the readability.
```
git work @feature -f #johndoe @develop -f #myboss @feature @. @done
```

Instead, use shorter separate chains. Avoid using more than one `@done` calls.
```
git work @feature -f #johndoe @done
git work @develop -f #myboss @feature @. @done
```

This code will perform the same thing.
```bash
git pull johndoe feature         # @feature -f #johndoe
git checkout develop             # 
git pull myboss feature          # @develop -f #myboss @feature
git add .                        #
git commit                       #
git push origin develop          # @.
git checkout master              # @done
```
Above all things, just use the simplist `git work`; this is what I first intended.

#### Auto-complete
`work` supports auto-complete in bash. Tab key after writing `@` and `#` will each show you available branch and remote names.

### Installation
![GitHub top language](https://img.shields.io/github/languages/top/hyeondnl/git-work) ![GitHub repo size](https://img.shields.io/github/repo-size/hyeondnl/git-work) ![GitHub last commit (branch)](https://img.shields.io/github/last-commit/hyeondnl/git-work/master) ![GitHub](https://img.shields.io/github/license/hyeondnl/git-work)


[Find me on Github!](https://github.com/hyeondnl/git-work) [GitHub forks](https://img.shields.io/github/forks/hyeondnl/git-work?style=social)
Giving the `git-work` script file a power will wake our octocat up! 
```bash
chmod +x $DOWNLOAD_PATH/git-work
```

### Documentation
For more help, `git work --help` provides more details.
