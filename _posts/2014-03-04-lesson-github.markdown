---
layout: post
title: "Week 1 : Lesson 3 : Github"
category: lesson
published: true
---

## Review

Review from [Week 1 : Lesson 2 : The Terminal]({{ site.baseurl}}{% post_url 2014-03-03-lesson-the-terminal %}).  One (or more) pair will rehash the previous session's lesson by teaching the basic learnings to the group.  They will explain it to the others by drawing a diagram, using an analogy, telling a story or in some other way creatively communicating the idea without using code.

## Today's Project<a name="todays-project"></a>

Part of [Week 1 : Project 1 : BOS]({{ site.baseurl}}{% post_url 2014-03-07-project-bos %}).

## Github

### _What Is It?_

Designed to help developers work together on open-source projects, Github has become the place where coders put their stuff. Although it can serve as a library, the real heart of the thing is as a way for multiple programmers to be able to work together without breaking their programs.  

Sometimes you will hear Github described as a VCS or Version Control System.  The biggest problem with having multiple coders working on a project is that they are all making changes to a code base that is itself changing.  These shifting sands would be impossible to navigate unless there was a way to stop that at certain points and get everyone on the same page. 

### _How Does It Work?_

So this is the best way to understand how the process flow works: imagine a supermarket.

First, you grab a shopping cart.  Then you grab things off the shelf or out of a freezer, and add it to your shopping cart.  You have decided to go with your friend.  To make the task easier, you have sent them off to pick up dairy products.  They grab a small basket and run off to get that stuff.  Eventually they come back and you take a look at what they brought.  If the stuff they have is what you wanted and not anything you have already got, they put it in there.  When you've gotten what you want, you head to the cashier.  Once you have finished paying, the stuff is yours.  You go home and put it in your pantry/cupboard/fridge.  

This is how git works.  Your shopping cart is your local repository.  Adding an item to the cart is like adding an item to the repository.  When you send your friend off to get something, it is like creating a branch.  When they get back, it is like merging the branch.  When you checkout, that is similar to committing your changes.  And putting it in your cupboard is like pushing it to the remote repo.

### _What Can I Do With It?_

**git init**  [Initializes a git repository – creates the initial ‘.git’ directory in a new or in an existing project.]
**git clone** [Makes a Git repository copy from a remote source. Also adds the original location as a remote so you can fetch from it again and push to it if you have permissions.]
**git add** [Adds files changes in your working directory to your index.]
**git status** [Shows you the status of files in the index versus the working directory. It will list out files that are untracked (only in your working directory), modified (tracked but not yet updated in your index), and staged (added to your index and ready for committing).]
**git diff** [Generates patch files or statistics of differences between paths or files in your git repository, or your index or your working directory]
**git checkout** [Checks out a different branch – switches branches by updating the index, working tree, and HEAD to reflect the chosen branch.]
**git merge** [Merges one or more branches into your current branch and automatically creates a new commit if there are no conflicts.]
**git rm** [Removes files from your index and your working directory so they will not be tracked.]
**git commit** [Takes all of the changes written in the index, creates a new commit object pointing to it and sets the branch to point to that new commit.]
**git log** [Shows a listing of commits on a branch including the corresponding details.]
**git remote** [Shows all the remote versions of your repository.]
**git push** [Pushes all the modified local objects to the remote repository and advances its branches.]

Let's take a few of these for a whirl.

```bash
➜  Githippopotamus  git init
Initialized empty Git repository in /Users/matthewtschoegl/Code/Githippopotamus/.git/
➜  Githippopotamus git:(master) 
```

So here I have initialized a Git repository.  If we look into the file, here's what we'll see:

```bash
➜  Githippopotamus git:(master) ls -a
.    ..   .git
➜  Githippopotamus git:(master) ls
➜  Githippopotamus git:(master) 
```
So there is a git file that is tracking our changes and what our repository does and nothing else.  Let's change that and add a file.

```bash
➜  Githippopotamus git:(master) touch index.html
➜  Githippopotamus git:(master) ✗ git status
# On branch master
#
# Initial commit
#
# Untracked files:
#   (use "git add <file>..." to include in what will be committed)
#
#	index.html
nothing added to commit but untracked files present (use "git add" to track)
➜  Githippopotamus git:(master) ✗ ls
index.html
```
So here we created a file, index.html, and we can see at the bottom that it has indeed been created.  What is the rest of the message telling us?  It's saying that we have an untracked file.  An untracked file is one that git does not currently know about.  To use our earlier analogy, it is something that we are holding in our hand, but have not put in our shopping cart.  To put it in our shopping cart, we have to add it. 

```bash
➜  Githippopotamus git:(master) ✗ git add index.html
➜  Githippopotamus git:(master) ✗ git status
# On branch master
#
# Initial commit
#
# Changes to be committed:
#   (use "git rm --cached <file>..." to unstage)
#
#	new file:   index.html
#
```
Now it's been added to git.  Let's head to checkout now - i.e. commit our code.  

```bash
➜  Githippopotamus git:(master) ✗ git commit -m "Added an index.html file."
[master (root-commit) 1f02005] Added an index.html file.
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 index.html
```

Here we committed the code and included a message.  The message is important, as it tells the other people who are working on the code (including your future self) what this code that you committed actually did.  

But this repo is only found locally and only works if someone is using the same file directory as me.  If we want to use Github and have a code repository which we can all use and which is hosted in the cloud, there are a few more steps.  Let's give that a try now.

First, you have to create a repository in your Github account (name it, describe it, and give it a README):   

![](http://realtschoegl.github.io/devchamps/images/githubrepo1.png)

Then it takes you to this screen. 

![](http://realtschoegl.github.io/devchamps/images/githubrepo2.png)

Here you have two options.  The second is to simply push the repo that you configured locally to the repo using those two commands.  It's that easy!  The first is slightly more complicated.  

What it has you do is to:

1. Create a README file (totally optional, but always recommended) locally
2. Initialize a local git repo 
3. Add your README
4. Commit the README you just made
5. Add the remote - this is to tell your local repo what cloud repo you are going to be pushing your code to.
6. Push.

And that's it.  Now you have both a local repo and a remote repo.  When you want to get the latest version of that codebase, you use the command **git pull** to update your local repo. If you don't have a local repo and a repo already exists online, you can make it even easier on yourself by using the **git clone** command along with the location of the remote repo (in the second picture that can be found in the Quick Setup section text box). 

```bash
➜  Code  git clone https://github.com/RealTschoegl/Githippopotamus.git
```
Versioning doesn't only exist so that you and your coworkers can each work on the same codebase without sabotaging each others' work.  It also exists so that you can experiment locally with your own codebase, but without having to worry about compromising your codebase.  

How does it do this?  Through the use of branches.  A branch is like a temporary version of your codebase where you can make changes (this is the friend's shopping basket in the grand analogy).  Eventually it is intended to be merged with the major codebase, but that is not always the case (think of your friend paying for what they have in their codebase separately).

First, create a branch:

```bash
➜  Githippopotamus git:(master) git checkout -b basket
Switched to a new branch 'basket'
➜  Githippopotamus git:(basket) 
```

As you can see from the command line we are now in a different branch.  I am going to now create another file, add that to the git repo, and commit the change (normal git procedures apply in a branch as well).  

```bash
➜  Githippopotamus git:(basket) touch style.css
➜  Githippopotamus git:(basket) ✗ ls
images     index.html style.css
➜  Githippopotamus git:(basket) ✗ git add .
➜  Githippopotamus git:(basket) ✗ git status
# On branch basket
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#	new file:   style.css
#
➜  Githippopotamus git:(basket) ✗ git commit -m "Added a style.css file."
[basket 6883b15] Added a style.css file.
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 style.css
```

Now let's say we have finished making our changes and we are happy with them.  First, we switch back to the master.

```bash
➜  Githippopotamus git:(basket) git checkout master
Switched to branch 'master'
➜  Githippopotamus git:(master) ls
images     index.html
```

Notice that the style.css file that we created is not there.  No problem!  Now we just merge the changes from our branch into our master so we can include all of that good stuff.

```bash
➜  Githippopotamus git:(master) git merge basket
Updating 5192834..6883b15
Fast-forward
 style.css | 0
 1 file changed, 0 insertions(+), 0 deletions(-)
 create mode 100644 style.css
➜  Githippopotamus git:(master) ls
images     index.html style.css
```

And there it is - our change has been included.  This all seems pretty easy and it certainly can be.  The hard part comes with remembering to execute each step at the proper time and in the proper way.  Much of the complaints you hear from developers about git has to do with the difficulty of undoing mistakes that have been made.

The easiest way to avoid these frustrations is to know what your current git situation is and what you therefore have to do.  If at any time you want to check what is going on with your git, there are three commands you can use.  

**Git diff** will show you what exact lines of code have changed since your last commit.  Here I added some html tags to an index.html file:

```bash
diff --git a/index.html b/index.html
index e69de29..97645c2 100644
--- a/index.html
+++ b/index.html
@@ -0,0 +1,4 @@
+<head>
+</head>
+<body>
+</body>
(END) 
```

**Git status** shows what files have changed since my last commit.  It is less informative than **git diff**, but much easier to read and therefore more frequently used:

```bash
# On branch master
# Changes not staged for commit:
#   (use "git add <file>..." to update what will be committed)
#   (use "git checkout -- <file>..." to discard changes in working directory)
#
#	modified:   index.html
#
no changes added to commit (use "git add" and/or "git commit -a")
```
And if you want to know what commit it is that your current work is being compared against,** git log** will show you a list of previous commits:

```bash
commit 1f0200507d6c8d085f4faecb79284c5b693d1726
Author: RealTschoegl <Matt.Tschoegl@gmail.com>
Date:   Tue Jan 28 01:10:07 2014 -0600

    Added an index.html file.
(END)
```

### _Why Do I Care?_

You're going to be doing this a lot.  

## Exercise

1) Create a git repo locally.  Add a file to that repo.  Commit the changes. 

2) Create a repo on Git.  Clone that repo down.  Add a file to that repo.  Commit the changes.

## Happiness Checkpoint

Did you do both of the above successfully?

## Project Guidelines

Remember the file from yesterday?  Commit that to a Github repository.  

## Solve

Flag an instructor when you are done.  Be prepared to tell them what you did and how you did it (process is as important as result in this exercise).  

## Extensions

Figure out how to go back to a previous commit.

## Push Instructions

Kinda the project above.

## Further Readings 

* [Git Cheatsheet](http://www.ndpsoftware.com/git-cheatsheet.html)
* ["Try Git" Tutorial](http://try.github.io/levels/1/challenges/1)
* ["Git Real 1" Tutorial](https://www.codeschool.com/courses/git-real)
* ["Git Real 2" Tutorial](https://www.codeschool.com/courses/git-real-2)