---
layout: post
title: "Week 2 : Lesson 3 : Hashes"
category: lesson
published: true
---

## Review

Review from [Week 2 : Lesson 2 : Methods]({{ site.baseurl}}{% post_url 2014-03-11-lesson-methods %}).  One (or more) pair will rehash the previous session's lesson by teaching the basic learnings to the group.  They will explain it to the others by drawing a diagram, using an analogy, telling a story or in some other way creatively communicating the idea without using code.

## Today's Project<a name="todays-project"></a>

Part of [Week 2 : Project 2 : Movie Directory]({{ site.baseurl}}{% post_url 2014-03-14-project-movie-directory %}).

## Hashes

### _What Is It?_

Hashes are the most common data storage unit you're going to see.  Even when you aren't using hashes, you're probably using a type of data storage that looks an awful lot like a hash.  

### _How Does It Work?_

A hash is a data storage unit that is composed of what are called "keys" and "values".  Each key is connected to value.  Unlike an array, there is no order in which the key-value pair is added into hash, nor can the information be extracted by knowing the order in which the key-value pair was added.  If you know the key, you can find the value.  If you add a key, you also have to add a value.

So first, how do we create a hash? One option:

{% highlight irb linenos %}
irb(main):001:0> fruit = Hash.new
=> {}
irb(main):002:0> fruit
=> {}
{% endhighlight %}

Alternatively, you can just make it equal to the curly brackets:

{% highlight irb linenos %}
irb(main):001:0> fruit = {}
=> {}
irb(main):002:0> fruit
=> {}
{% endhighlight %}

What can be the key? Anything!  Here are some examples:



What can be the value?

How do you add something to a hash?



What if I want to get information out of a hash? If you know the key, it's pretty easy:





### _What Can I Do With It?_



### _Why Do I Care?_

## Exercise

## Happiness Checkpoint

## Project Guidelines

## Solve

## Extensions

## Push Instructions

## Further Readings

* [Ruby Documentation for Hashes](http://ruby-doc.org/core-2.1.0/Hash.html)
* [Ruby Hashes](http://www.tutorialspoint.com/ruby/ruby_hashes.htm)
* [Hashes in Ruby](http://zetcode.com/lang/rubytutorial/hashes/)