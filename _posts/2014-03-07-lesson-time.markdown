---
layout: post
title: "Week 1 : Lesson 7 : Time"
category: lesson
published: true
---

## Review

Review from [Week 1 : Lesson 6 : Conditionals]({{ site.baseurl}}{% post_url 2014-03-06-lesson-conditionals %}).  One (or more) pair will rehash the previous session's lesson by teaching the basic learnings to the group.  They will explain it to the others by drawing a diagram, using an analogy, telling a story or in some other way creatively communicating the idea without using code.

## Today's Project<a name="todays-project"></a>

Part of [Week 1 : Project 1 : BOS]({{ site.baseurl}}{% post_url 2014-03-07-project-bos %}).

## Time

### _What Is It?_

Ruby isn't just about logic, it's also about getting and using real-life data.  The Time library, what we're going to be working with today, is one library that allows you to get data and transform it.

### _How Does It Work?_

Here are some ways that you can use the Time library.

First, you can find out what time it is right now:

```ruby
2.0.0p247 :088 > Time.now
 => 2014-01-31 12:19:34 -0600
```
Notice the format for the time that it gives.  This is called ISO 8601, which is [an international standard](http://en.wikipedia.org/wiki/ISO_8601) for representing date and time. It is worth mentioning that this time is the local time.  If you would like to use a standard time that is universally recognized, then you can also get it in UTC (Coordinated Universal Time - it's a French acronym).  

```ruby
2.0.0p247 :122 > Time.now.utc
 => 2014-01-31 19:18:24 UTC 
```

You can also get a specific time if you enter some date parameters.  

```ruby
2.0.0p247 :089 > Time.new(2002)  
 => 2002-01-01 00:00:00 -0600 
2.0.0p247 :090 > Time.new(2002,5,1)  
 => 2002-05-01 00:00:00 -0500
```

Alternatively, you can use Time.at to also get a specific time, but in seconds from the UNIX Epoch:

```ruby
2.0.0p247 :094 > Time.at(0)
 => 1969-12-31 18:00:00 -0600 
2.0.0p247 :093 > Time.at(60*60*24*365)
 => 1970-12-31 18:00:00 -0600
```

UNIX Epoch?  As far as Ruby is concerned, time started on January 1st, 1970.  More on this [here](http://stackoverflow.com/questions/1090869/why-is-1-1-1970-the-epoch-time).

Time also responds to some logic as well.  You can create a Time object and query that object as so:

```ruby
2.0.0p247 :095 > t = Time.now
 => 2014-01-31 13:02:26 -0600 
2.0.0p247 :096 > t.monday?
 => false 
2.0.0p247 :097 > t.tuesday?
 => false 
2.0.0p247 :098 > t.wednesday?
 => false 
2.0.0p247 :099 > t.thursday?
 => false 
2.0.0p247 :100 > t.friday?
 => true 
2.0.0p247 :101 > t.saturday?
 => false 
2.0.0p247 :102 > t.sunday?
 => false 
2.0.0p247 :103 > t.wday
 => 5 
2.0.0p247 :104 > t.year
 => 2014 
2.0.0p247 :105 > t.month
 => 1 
2.0.0p247 :106 > t.hour
 => 13 
2.0.0p247 :107 > t.dst?
 => false
```
What do you think the last one is?

If we don't want to print out a time in the somewhat unwieldy ISO 8601 format, we can use a method (remember that word) called strftime to format the time based on our specifications.

```ruby
2.0.0p247 :123 > t = Time.now
 => 2014-01-31 13:38:04 -0600 
2.0.0p247 :124 > t.strftime("Printed on %m/%d/%Y")
 => "Printed on 01/31/2014" 
```

You can find more on what symbols to use for what times in strftime in the Time library's documentation.


### _What Can I Do With It?_

Let's make a basic conditional using Time.  

### _Why Do I Care?_

Because things happen in time. 

## Exercise

Make a conditional statement that tells what a cooler version of you would do every night of the week.

## Happiness Checkpoint

Flag down an instructor and show them what you did.

## Project Guidelines

Imagine that your BOS now has daily specials and lunch specials.  Implement that business logic in your model.

## Solve

Flag an instructor when you are done.  Be prepared to present yours in front of the class.

## Extensions

If you really want to get tricky, implement pricing.  Even harder, implement pricing based on time of day.  

## Push Instructions

Push to your BOS repo.  You are officially done this project, so feel free to play the push music.

## Further Readings

* [Ruby Documentation on Time](http://www.ruby-doc.org/core-2.1.0/Time.html)
* [Date and Time in Ruby](http://www.tutorialspoint.com/ruby/ruby_date_time.htm)

## Blogging

Each weekend, you will be expected to write a blog entry as homework.  The blog entry must be submitted to your Moodle blog, but can also be published on an external blog (publishing publicly is our recommendation, but not a requirement).  Feel free to write about something you have learned, a challenge you solved, a particularly interesting technology, or a challenging problem.  You are also welcome to write about your personal experiences of the program and or learning Ruby on Rails.  What we are hoping is that you can begin getting comfortable with publishing your thoughts online and contributing to the Ruby community.