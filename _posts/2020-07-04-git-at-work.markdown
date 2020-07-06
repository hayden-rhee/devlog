---
layout: post
title:  "Git at Work!"
categories: [ Git, Sticky ]
author: hyeon
image: assets/images/alphameme.jpg
---
> The title of this page *is* a parody of ["Cells at Work!"](https://en.wikipedia.org/wiki/Cells_at_Work!).

![GitHub top language](https://img.shields.io/github/languages/top/hyeondnl/git-work) ![GitHub repo size](https://img.shields.io/github/repo-size/hyeondnl/git-work) ![GitHub last commit (branch)](https://img.shields.io/github/last-commit/hyeondnl/git-work/master) ![GitHub](https://img.shields.io/github/license/hyeondnl/git-work)

[<img style="align: middle" src="https://github.githubassets.com/images/modules/logos_page/Octocat.png" alt="octocat" width="250" />](https://github.com)

Oops! Our cute octocat is playing hooky right now. We should give him some works to do. Maybe he can help my git commits!

### Introduction
`work` will start *working* with basic stuffs on the current branch by this statement.
```bash
git work
```
The command pulls changes from the remote repos, commit the changes with a timestamp, and pushes back to the remote repo.
You can select the works that `work` will automatically perform, using options.
```bash
git work -c #commit only!
```

### Calling the branch
#### `work in progress`
At-mark `@` will *call* the branch.
Once the branch is called, `work` will start to *work*; pull, commit, and push.
**Make sure that the branch is not only checkouted, but also performs things in default, if there are no options.**
```
git work @branch @done
```
`@done` command could be omitted, and its optional; actually it just sends you back to the branch you first started.  
It is not like `end` from Pascal or `fi` from bash.
```bash
#working in master branch
git work @hotfix <something> @develop <something>         #stays in develop branch
git work @hotfix <something> @develop <something> @done   #returns to master branch
```

For example, the following command first pushes the changes you made to `develop` branch. Then it pulls the changes from `hotfix` branch to `release` branch, and compares `release` branch with your working branch (`develop`).
```bash
#working in develop branch
git work
git work @release -f @hotfix @. -d
```

`@.` is a short name for the current branch at the moment you call it; in this case, `release` branch. It is also the default value when the branch name is not mentioned.

### Calling the remote repository
#### `work in progress`

Sharp, or a hashtag `#` will *call* the remote repository.
```
git work @release -f #johndoe
```
The default value is `#.`, if you don't specify the remote. This points to the remote origin.

### Example
This code make sense based on the syntax, but it looks terrifying and hard to read.
```
git work @feature -f #johndoe @develop -f #myboss @feature @. @done
```
This looks way better; I recommend you to use this.
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

#### Auto-complete
#### `work in progress`
`work` supports auto-complete in bash. Tapping tab key after `@` and `#` will each show you available branch and remote names.

### Installation
Giving the `git-work` script file a power will wake our octocat up! 
```bash
chmod +x $DOWNLOAD_PATH/git-work
```

### Documentation
For more help, `git work --help` provides more details.
