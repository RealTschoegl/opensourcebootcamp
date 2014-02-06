---
layout: post
title: "Week 1 : Lesson 2 : The Terminal"
category: lesson
published: true
---

## Review

Review from [Week 1 : Lesson 1 : Ice Breakers]({{ site.baseurl}}{% post_url 2014-03-03-lesson-ice-breakers %}).  One (or more) pair will rehash the previous session's lesson by teaching the basic learnings to the group.  They will explain it to the others by drawing a diagram, using an analogy, telling a story or in some other way creatively communicating the idea without using code.

## Today's Project<a name="todays-project"></a>

Part of [Week 1 : Project 1 : BOS]({{ site.baseurl}}{% post_url 2014-03-07-project-bos %}).

## The Terminal

### _What Is It?_

The terminal is the means by which you can interact with your computer's files.  As a web developer, it is also how you will interact with the files on a web server (which is really just a computer that other people can also access). 

### _How Does It Work?_

By using commands.  By entering commands you can find files, make files, delete files, copy files, and a whole bunch else (much of which we will not cover here).  These are a few of the basics that you will need:

* **pwd** 					[Print Working Directory]
* **ls** 					[List]
* **ls** -a 				[List all]
* **cd**  					[Change Directory]
* **cd ..** 				[Change Directory by moving up one folder]
* **mkdir** 				[Create new folder]
* **mv** 					[Move or rename files or directories]
* **cp** 					[Copy one or more files to another location]
* **rm** 					[Remove files]
* **rm -rf** 				[Force remove directories and their contents recursively]

The easiest way to think about file directories, at least for me, is in terms of rooms in a huge house.  **pwd** tells you what room you are in. **ls** tells you what else is in the room.  **ls -a** tells you what is in the room, even if it is hidden (think of it as opening the cupboards).  **cd** is to enter another room.  **cd -** is to enter the previous room while **cd ..** is to go to the room which provides the entry to your current room. **mkdir** is to create a new room.  **mv** is to bring an object from one room to another room and **cp** is to copy it from one room to another (both can also be used for files, aka rooms, but that is a bit confusing in this analogy).  **rm** destroys something in a room, while **rm -rf** destroys a room and everything in it.  If that later one sounds especially scary, that is because it is. Although not as scary as **rm * ** which is to delete everything.  Ask [Pixar about that one](http://www.techdirt.com/articles/20120514/17243918918/how-toy-story-2-almost-got-deleted-except-that-one-person-made-home-backup.shtml). 

### _What Can I Do With It?_

Let's run you through a couple of exercises.  First click on iTerm, which has been helpfully installed already on your computer.  This is what you will see:

```
➜  ~
```
Okay.  So...where are we?  Easy enough to find, simply type in this command:

```
➜  ~ pwd
```
and we get the following

```
➜  ~ pwd
/Users/matthewtschoegl
```
This is the directory we are currently sitting in.  So now we want to know what else is in this file.  So we type in the following:

{% highlight ksh %}
➜  ~ ls
{% endhighlight %}

and get ...

```
➜  ~  ls
Code      Desktop   Documents Downloads Dropbox   Library   Movies    Music
Pictures  Public    SkyDrive  asciiart  bin       src       subl
```

These are all of the files that are in this file.  Let's say that we want to look in one of the files.  There are two ways to do that.  The first is simply to list the contents of that file, like so:

```
➜  ~ ls Code
```

The other is to actually enter the file and take a look around.  Let's do that:

```
➜  ~ cd Code
```

And now it changes to 

```
➜  Code 
```

Our terminal helpfully tells us what file we are in.  It doesn't give the whole pathway, although it can be configured to do so.  Kind of a matter of personal preference.  

Now that we are in the file, I want to see what is there.  What do we type? Of course

{% highlight ksh %}
➜  Code  ls
DevChamps       GolaZone        HoffmannJozsef  RandomStuff     StockApp
bedeadly        commitcoffee    maximum-awesome
{% endhighlight %}

Here we can see a bunch of files of various code projects that I have or am working on.  Cool.  Let's do some of the stuff mentioned above.  First we can create a new folder named Stuff.  

```
➜  Code mkdir Stuff
➜  Code
```

Did anything happen?  Well, let's see if it's there:

```
➜  Code ls
DevChamps       GolaZone        HoffmannJozsef  RandomStuff     StockApp        Stuff
bedeadly        commitcoffee    maximum-awesome
```

It is!  Let's enter this folder.

```
➜  Code cd Stuff
➜  Stuff
```

Again, we look around a little bit.

```
➜  Stuff ls
➜  Stuff
```

Nothing there.  Here is a helpful command if we want to create a file.  Let's make an index.html file, to start with (when we get more into html, you'll see why this file type is so important).

```
➜  Stuff touch index.html
➜  Stuff ls
➜  Stuff
index.html
```

Now we are going to create another file in our folder.

```bash
➜  Stuff  mkdir Cabinet
➜  Stuff  ls
Cabinet    index.html
```

And into that cabinet, let's copy the index file.  

```bash
➜  Stuff  cp index.html Cabinet
➜  Stuff  ls
Cabinet    index.html
➜  Stuff  ls Cabinet
index.html
```

Now we want to create another file in the Cabinet.

```bash
➜  Stuff  touch style.css
➜  Stuff  ls
Cabinet    index.html style.css
```

Dagnabit!  We didn't look at our file pathway beforehand and forgot to create the file in the right directory.  Let's move it to the right one.

```bash
➜  Stuff  mv style.css Cabinet
➜  Stuff  ls
Cabinet    index.html
➜  Stuff  ls Cabinet 
index.html style.css
```

Now that I think about it, I don't really need that file at all.  Let's get rid of it.

```bash
➜  Stuff  cd Cabinet
➜  Cabinet  ls
index.html style.css
➜  Cabinet  rm style.css 
➜  Cabinet  ls
index.html
```

Finally, I want to get rid of the Cabinet and everything in it.

```bash
➜  Cabinet  cd ..
➜  Stuff  ls
Cabinet    index.html
➜  Stuff  rm -rf Cabinet
➜  Stuff  ls
index.html
```

### _Why Do I Care?_

For a lot of experienced developers, pretty much everything they do is done in the terminal.  Creating servers, putting files on those servers, changing the files on those servers - all of it can be done fastest and easiest through the command line.  At this point, we will just be using it for basic file management, but as the course progresses, you will use it more and more.  

## Exercise

Create a file structure for a year, with months, weeks, and days.  It does not have to be complete.  

## Happiness Checkpoint

What does your structure look like?

<pre>
.
└── January
    └── Week1
        ├── Friday
        ├── Monday
        ├── Saturday
        ├── Sunday
        ├── Thursday
        ├── Tuesday
        └── Wednesday
</pre>

## Project Guidelines

In your code folder, create a folder titled BOS.  Create a file called bos.rb.  

## Solve

Flag an instructor when you are done.  

## Extensions

Fool around with some of the other commands that are available to you [listed here](http://ss64.com/bash/).

## Push Instructions

We'll get to this bit tomorrow.  

## Further Readings

* [List of Bash Commands](http://ss64.com/bash/)
* [Treehouse: Console Foundations](http://teamtreehouse.com/library/console-foundations-2)
* [The Command Line Crash Course](http://cli.learncodethehardway.org/book/)

## Week's Badges

This week, the following badges are up for grabs:

* **Teach One** for [Moodle Blog](http://realtschoegl.github.io/devchamps/mini-lesson/2014/01/01/mini-moodle.html) 
* **Teach One** for [Ranges](http://realtschoegl.github.io/devchamps/mini-lesson/2014/01/01/mini-ranges.html)

Let your instructor know at lunch if you would like to earn one of these badges.