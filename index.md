# git

> You’re about to spend several hours of your life reading about Git. - Pro Git

## Learin git project

**Next Action:** Read first 10 pages of Git book

**List of actions:**

* [ ] Read git book
* [x] learn to install git
* [x] learn to creat a git repo
* [ ] Manage folders
* [ ] manage text files
* [ ] learn basic linux terminal utility
* [x] migrate reddit dayly jurnal project to txt fills
* [ ] find my old git lab accont
* [ ] create a git hub accont
* [ ] make git hub mirror git lab ??? or the other way arround.
* [ ] create a git workflow metaphor
* [ ] Do git interactive turorial at "https://learngitbranching.js.org/"
* [ ] Practice

## Pro Git

Some of the chapters of this book are beyond the scope of my needs. Chapters 1, 2 and 3 are must reads. Chapters 4 and 6 are optional but interesting reads.

 I will read the first chapter to have some understanding of what came before. Chapter 2 and 3 are the bread and butter. Chapter 5 and 6 will be read to make me proficient in the current trends on how to use the platforms.

### chapters to read:

* [x] Chapter 1 - context and background history
* [x] Chapter 2 - The basic
* [x] Chapter 3 - the defining feature
* [ ] Chapter 5 - git workflow
* [ ] Chapter 6 - GitHub

**Start Time**: 5/08/2020

**End Time**: 17/08/2020

**Description:** Success is to be able to deploy web site folder, manage folders in git and do simple pull, push, clone requests from the terminal.
Also undestand most of the "Gui" even if I can do some of the tasks in terminal I want to undestand the workflow.

## resources

several git hosts -https://www.git-tower.com/blog/git-hosting-services-compared/

* #github or #git channel on [https://freenode](https://freenode.net)
* https://www.reddit.com/r/git/
* https://www.reddit.com/r/github/
* https://github.community/
* https://about.gitlab.com/community

## My previus knowladge of Git

Git is a version controle technology, it's purpose is to prevent data loss during the several fases of developlment of a project, it's particulary useful when working with other people as one can manage, view, edit, comment and decide which changes are integrated to the project and which changes are discarded.

Git also allows for an individual to clone a project, so store a version add changes. Later the platforms that implemnts git repositoris or git repos for sorth also add feature relevant to softwere development such as bug repports.

Git repos are primarly used to work with text files but can also support other formats. The hosting of projects from the platform that implements free git solutions makes it so many users use git as storage and/or sync solution.

git seem to be the gold standard for softwere development version controll and is also used by writers.

## table of contents

* what is Git ?
* (installing git)[#installing-git]
* (git config)[]
* git branching
* (List of all commands)[]

## what is Git ?

## installing git

* Using a linux package manager
* installing on Linux from source
* installing on Windows

### Linux

> `sudo apt install git-all`

Instaling git in linux using the package manager is a simple process just run the above command for "APT" package manager on debian based distributions on other distribution you can find them by "distribution name install git"

### source code

* latest version of git (not true in modern times)
* if your package manager dos not have git

This is a more labor intensive approach, use in the **rare ocassion** where git is not on your package manager. It used to be that installing from source code would give you the most recent version of git, this seems to be irrelevant nowadays

debian based source instalation :

1. install all the dependacies
2. install documentation formats
3. install `install-info` package
4. grab the latest tagged release tarball
5. compile and install the tarball

```
1.
sudo apt-get install dh-autoreconf libcurl4-gnutls-dev libexpat1-dev \
gettext libz-dev libssl-dev

2.
$ sudo apt-get install asciidoc xmlto docbook2x

3.
sudo apt-get install install-info

4.
from kernar.org or from github.com
"https://www.kernel.org/pub/software/scm/git"
"https://github.com/git/git/releases"

5.
$ tar -zxf git-2.8.0.tar.gz
$ cd git-2.8.0
$ make configure
$ ./configure --prefix=/usr
$ make all doc info
$ sudo make install install-doc install-html install-info
```

### Windows

There are also a few ways to install Git on Windows:

* The most official build is available for download on the Git website note that this is a project called **Git for Windows**, which is separate from Git itself.
* You can also use the **Git Chocolatey package** but keep in mind this packed is community maintained.
* Another easy way to get Git installed is by installing **GitHub Desktop**. The installer includes a command line version of Git as well as the GUI.

## Git Config

Git comes with a tool called git config that lets you get and set configuration variables that control all aspects of how Git looks and operates. These variables can be stored in three different places:

* [path]/etc/gitconfig --> --system --> applies to the system
* ~/.config/git/config --> --global --> applies to the user
* config file in the Git directory --> --local --> applies to the folder

The more specific the config setting the higher priority it has, thus allowing overriding of previous levels. Folder config in action then user then system. // cascading

### Quick first time config

When you first install git on your machine theres a few recomened confics you should do the the global (user) config file

* config your identity

* config default editor

* see current settings

* conficg any directory specifc files

### Checking Your Settings

You can view all of your settings and where they are coming from using: `$ git config --list --show-origin`

You may see keys more than once, because Git reads the same key from different files ([path]/etc/gitconfig and ~/.gitconfig, for example). In this case, Git uses the last value for each unique key it sees.

You can also check what Git thinks a specific key’s value is by typing `git config <key>`

Since Git might reads the same configuration variable value from more than one
file, it’s possible that you have an **unexpected value** for one of these values and you don’t know why. In cases like that, **you can query Git as to the origin for that value***, and it will tell you which configuration file had the final say in setting that value:

`$ git config --show-origin <key>`

### Your Identity

The first thing you should do when you install Git is to set your username and email address. This is important because every Git commit uses this information, and it’s immutably baked into the commits you start creating:

```
$ git config --global user.name "John Doe"
$ git config --global user.email johndoe@example.com
```

### Your Editor

Now that your identity is set up, you can configure the default text editor that will be used when Git needs you to type in a message. If not configured, Git uses your system’s default editor.

If you want to use a different text editor, such as Emacs, you can do the following: `$ git config --global core.editor emacs`

On a Windows system, if you want to use a different text editor, you must specify the full path to its executable file. This can be different depending on how your editor is packaged.

In the case of Notepad++, a popular programming editor, you are likely to want to use the 32-bit version, since at the time of writing the 64-bit version doesn’t support all plug-ins. If you are on a 32-bit Windows system, or you have a 64-bit editor on a 64-bit system, you’ll type something like
this:

```
$ git config --global core.editor "'C:/Program Files/Notepad++/notepad++.exe' -multiInst -notabbar -nosession -noPlugin"
```

Vim, Emacs and Notepad++ are popular text editors often used by developers on
Unix-based systems like Linux and macOS or a Windows system. If you are using another editor, or a 32-bit version, please find specific instructions for how to set up your favorite editor with Git at [git config core.editor commands](https://www.git-scm.com/book/en/v2/Appendix-C%3A-Git-Commands-Setup-and-Config)

### Your default branch name

By default Git will create a branch called master when you create a new repository with git init. From Git version 2.28 onwards, you can set a different name for the initial branch. To set main as the default branch name do: `$ git config --global init.defaultBranch main`

### Getting Help

If you ever need help while using Git, there are three equivalent ways to get the comprehensive
manual page (manpage) help for any of the Git commands:

```
$ git help <verb>
$ git <verb> --help
$ man git-<verb>

pravtical exmple:
$ git help config
```

you can also use `$ git add -h` for a sort usefull commands list

other resurces:

* #github or #git channel on [https://freenode](https://freenode.net)
* https://www.reddit.com/r/git/
* https://www.reddit.com/r/github/
* https://github.community/
* https://about.gitlab.com/community/

# Git the basics

*

* ## Getting a Git Repository

* turn a local directory into git repository

* clone an existing git repository

### Initializing a Repository in an Existing Directory

 and type comand `git init`

```
 Move to the directory where you want to inicialise the repo:
cd /home/user/my_project

Type the command:
$ git init
```

### clone an existing git repository

```
You clone a repository with `git clone <url>`:
git clone https://github.com/Zettlr/zettlr-docs
```

theres other protocols such as ssh (user@server:path/to/repo.git) or git:// protocol

## Recoring changes

![git-file-stage.png](D:\000-activeprojects\git\git-file-stage.png)

* untraked - `git add <filename>`

* unmodified `git stage <filename>`

* modified - eddit a file to make modified

* staged - `git add <filename>`

* commit - `git commit <filename>`.

* Reset - `git reset HEAD <file>`

* remove - `git rm <filename>`

## File comparison

* `git diff <filename>` - will show the **difference** between the staged and modified version of a file.

* `git diff --staged` -  will show the **difference** between the staged and unmodified (commited) version of a file.

  ## Commit history

To see what commits you have made as well as to with branch to they belong and in witch branch your located you can use the `git log`.

## working with romote repositorys

> what is a remote repository ?

A remote repository is another git repository that not the one your working currently. For exmple When we clone a repo we create a copy of the repo on our system, the original version of the repo is to us a remote repository.

remote repositories are important because when working with multiple people, each person will create there own repos as to make it easier to debug and prevent two people simultaneously modify the same file.

Theres 2 major action to do to remote repos:

* fetch - `git fetch <remote>`

* push - `git push <remote> <branch>`

* Pull -

on top of this you need to be able to see what remotes you have, and new remote repositories, renaming.

* see current remote repos - `git remote show`
* see remote repo detail - `git remote show <remote>`
* add remote repo - `git add remote <remote>`
* delete remote repo - `git remote rm <remote>`
* rename remote repos (on your system) -

### Add, remove and rename remotes

The `git clone <url>` command **implicitly adds the origin remote** for you. To add a new remote Git run: `git remote add <shortname> <url>`.

To remove a remote run the command `git remote remove <shortname>. Once you delete the reference to a remote this way, all remote-tracking branches and configuration settings associated with that remote are also deleted.

To change the shortname you can us the comand `git remote rename <oldname> <newname>`

### Inspecting a remote

To see more information about a particular remote, you can use the `git remote show <remote>` command

## Tags

Git has the ability to tag specific points in a repository’s history as being important. typically, people use this functionality to mark release points (v1.0, v2.0 and so on).

### See tags

you can list your tags using `git tag` and to serch for a specific tag pattern use `git tag --list "v1.8.5*"`.

You can see the tag data along with the commit that was tagged by using the git show command `git show <tag>`

### Create tags

Git supports two types of tags:

* lightweight
* annotated

A **lightweight** tag it’s just a pointer to a specific commit.

**Annotated tags are stored as full objects in the Git database**. They’re checksummed; contain the tagger name, email, and date; have a tagging message; and can be signed and verified with GNU Privacy Guard (GPG).

It’s generally recommended that you create annotated tags so you can have all this information; but if you want a temporary tag or for some reason don’t want to keep the other information, lightweight tags are available too.

You can create annotation with `git tag -a <tagname>` git will open you deafoult so you can write the tag message. You can also use `git tag -a <tagname> -m "message"`.

To create a lightweight tag dont provide any of the flags, just use `git tag <tagname>`.
                                                                              You can also **tag commits after you’ve moved past them**. To tag that commit, you specify the commit checksum (or part of it) at the end of the command. To get the commit checksum use the `git log` command

## Deleting Tags

To delete a tag on your local repository, you can use `git tag -d <tagname>`

Note that this does not remove the tag from any remote servers. There are two common variations
for deleting a tag from a remote server.

* `git push origin --delete <tagname>` // use this one is simpler
* `git push <remote> :refs/tags/<tagname>:

## Sharing Tags

by default, the git push command doesn’t transfer tags to remote servers. You will have to explicitly push tags to a shared server after you have created them.

* Run `git push <remote> <tagname>` to push a single tag
* `git push <remote> --tags` to push all your tags
* `git push <remote> --follow-tags` will push only annotation tag
* theres currently no option to push only lightweight tags ( pro git Version 2.1.259, 2020-08-28)

## Checking out Tags

> I dont undestand this, do at your own risk!

If you want to view the versions of files a tag is pointing to, you can do a git checkout of that tag, although this puts your repository in “detached HEAD” state, which has some ill side effects:

In “detached HEAD” state, if you make changes and then create a commit, the tag will stay the same, but your new commit won’t belong to any branch and will be unreachable, except by the exact commit hash. Thus, if you need to make changes — say you’re fixing a bug  on an older version, for instance — you will generally want to create a branch:

```
$ git checkout -b version2 v2.0.0
Switched to a new branch 'version2'.
```

If you do this and make a commit, your version2 branch will be slightly different than your v2.0.0 tag since it will move forward with your new changes, so do be careful.

## Git Aliases

Git doesn’t automatically infer your command if you type it in partially. If you don’t want to type the entire text of each of the Git commands, you can easily set up an alias for each command using git config. Here are a couple of examples you may want to set up:

```
$ git config --global alias.co checkout
$ git config --global alias.st status
$ git config --global alias.ci commit
```

This means that, for example, instead of typing git commit, you just need to type git ci. This technique can also be very useful in creating commands that you think should exist.

## Git Branching

![git-branch.png](D:\000-activeprojects\git\git-branch.png)

* create branch - `git branch <filename>`
* switch branch - `git checkout <branch name>`
* merge branch - `git merge <brach name>` will merge the current branch with the `<branch name>`
* delete branch - `git branch -d <branch_name>`
* check merge history - `git log`
