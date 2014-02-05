---
layout: post
title: "Week 1 : Lesson 4 : Heroku"
category: lesson
published: true
---

## Review

Review from [Week 1 : Lesson 3 : Github]({{ site.baseurl}}{% post_url 2014-03-04-lesson-github %}).  One (or more) pair will rehash the previous session's lesson by teaching the basic learnings to the group.  They will explain it to the others by drawing a diagram, using an analogy, telling a story or in some other way creatively communicating the idea without using code.

## Today's Project<a name="todays-project"></a>

Part of [Week 1 : Project 1 : BOS]({{ site.baseurl}}{% post_url 2014-03-07-project-bos %}).

## Heroku

### _What Is It?_

Once you have made something, you want other people to be able to see and use it.  This means getting it to a server online as opposed to your own local server.  Heroku is a service that uses git to make it a cinch to get your local project online.  Using the command line, you upload your code to their file.  Then it fires up a server and database on your behalf. And for free! 

It really falls under the category of a managed hosting solution.  You don't have unlimited access to the server and it only really supports some languages/platforms/frameworks/etc.   But what it does really well, and was in fact designed to, was to work with Ruby on Rails and other Ruby-based servers. 

### _How Does It Work?_

So let's say that you have an app that you want to push to production (production means "live", weirdly) - how do you go about getting it up on Heroku?

Well first, you have to have a git repository with a commit already performed.  Heroku finds it really hard to launch apps when you don't have any code to push :/  So the initial step is to have code that you are ready to push.  In this case, we are going to create a basic rails app in one line of code.  

```bash
➜  Githippopotamus git:(master) ✗ rails new blog
      create 
      ( ... whole bunch of code)
Your bundle is complete!
Use `bundle show [gemname]` to see where a bundled gem is installed.
```

We have an app!  Let's commit this.

```bash
➜  Githippopotamus git:(master) ✗ git add .
➜  Githippopotamus git:(master) ✗ git status
# On branch master
# Changes to be committed:
#   (use "git reset HEAD <file>..." to unstage)
#
#	new file:   blog/.gitignore
(.... whole bunch of code)
➜  Githippopotamus git:(master) ✗ git commit -m "Launching test app."
[master 3de6a50] Launching test app.
(.... whole bunch of code)
```

Now, you are ready to initialize some Heroku. Let's use the Githippopotamus repo from a previous lesson and push that to Heroku. 

```bash
➜  Githippopotamus git:(master) heroku create
Creating vast-stream-4070... done, stack is cedar
http://vast-stream-4070.herokuapp.com/ | git@heroku.com:vast-stream-4070.git
```

The heroku create command creates a new application on Heroku – along with a git remote that must be used to receive your application source.

And let's verify that that remote exists.

```bash
➜  Githippopotamus git:(master) git remote -v
heroku	git@heroku.com:secure-lake-7773.git (fetch)
heroku	git@heroku.com:secure-lake-7773.git (push)
```

Then you push.

```bash
➜  Githippopotamus git:(master) git push heroku master
```

You'll see something like this.  

```bash
➜  blog git:(master) git push heroku master
Initializing repository, done.
Counting objects: 63, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (49/49), done.
Writing objects: 100% (63/63), 25.94 KiB | 0 bytes/s, done.
Total 63 (delta 2), reused 0 (delta 0)

-----> Launching... done, v4
       http://secure-lake-7773.herokuapp.com deployed to Heroku
```

Now all you have to do is to run the following commands.

```bash
➜  blog git:(master) heroku run rake db:migrate
```

This will migrate your app's database. And...

```bash
➜  blog git:(master) heroku restart
```
This isn't strictly speaking necessary, but it's a good habit to get into.  When you restart Heroku, the changes you have made come into effect.  I have made the mistake inthe past of wondering why my changes didn't take, only to realize that I never restarted it.

And finally.

```bash
➜  blog git:(master) heroku open
```
Which will open your application in a new window.

One last thing...Rails out of the box uses SQLite for a database.  Heroku only supports Postgres.  Right now, that doesn't mean all that much to you, but in the future it will.  That does mean, though, in the present, that you have to make one change to any normal rails app.  Change the following in the Gemfile:

```bash
gem 'sqlite3'
```

to

```bash
group :development do
  gem 'sqlite3'
end
group :production do
  gem 'pg'
end
```

Then run 

```bash
bundle install
```

### _What Can I Do With It?_

Launch apps.

### _Why Do I Care?_

Although there are other options for hosting, this is the only one which is completely free and super user-friendly.  Well, maybe not completely free...When you want it to do pretty much anything extra, it costs you.  A lot.  For our purposes right now, and for most of the apps you will make in the near future, that makes it a great solution.  Down the line, as you create apps with greater demands, you might find that other hosting solutions begin to make more sense.  

## Exercise

Launch this [sample app](https://github.com/railstutorial/sample_app) on your own Github account. 

## Happiness Checkpoint

Show the instructor your functioning rails app on Heroku.  Alternatively, flag an instructor so we can see 

## Project Guidelines

Should probably push an existing app or two.

## Solve

Is it working?

## Extensions

Look at the some of the [add-on products](https://addons.heroku.com/) they offer.  Research what a couple of those are and what they do.

## Push Instructions

I mean, the whole thing is kind of a push instruction.

## Further Readings

* [What Is Heroku: Video Guide](https://www.codeschool.com/code_tv/heroku)
* [Deploying with Git](https://devcenter.heroku.com/articles/git)
* [Getting Started with Rails 4.x](https://devcenter.heroku.com/articles/getting-started-with-rails4)