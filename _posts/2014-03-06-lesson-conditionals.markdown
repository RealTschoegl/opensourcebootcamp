---
layout: post
title: "Week 1 : Lesson 6 : Conditionals"
category: lesson
published: true
---

## Review

Review from [Week 1 : Lesson 5 : Variables, Data Types, and Operators]({{ site.baseurl}}{% post_url 2014-03-05-lesson-variables-data-operators %}).  One (or more) pair will rehash the previous session's lesson by teaching the basic learnings to the group.  They will explain it to the others by drawing a diagram, using an analogy, telling a story or in some other way creatively communicating the idea without using code.

## Today's Project<a name="todays-project"></a>

Part of [Week 1 : Project 1 : BOS]({{ site.baseurl}}{% post_url 2014-03-07-project-bos %}).

## Conditionals

### _What Is It?_

Things change.  When things change, other things change.  Conditionals let you decide what changes when something else changes.  Managing the logic of these changes is a fundamental part of building code and, paradoxically, debugging (things changing that shouldn't or not changing when they should).

### _How Does It Work?_

All of these conditionals do or do not do something until a condition is met.  Here are some examples of different types of conditionals.  

#### If, Else, Elsif

One thing to note: it stops at the first correct thing.

```ruby
x=1
if x > 2
   puts "x is greater than 2"
elsif x <= 2 and x!=0
   puts "x is 1"
else
   puts "I can't guess the number"
end
```

#### Unless

The opposite of If.

```ruby
x=1
unless x>2
   puts "x is less than 2"
 else
  puts "x is greater than 2"
end
```

#### While Loops

```ruby
days_left = 7;  
  
while days_left != 0  
    puts "there are still #{days_left} in the week"  
    days_left -= 1  
end 
```

#### Until

The opposite of while. 

```ruby
days_left = 7;  
  
until days_left == 0  
    puts "there are still #{days_left} in the week"  
    days_left -= 1  
end 
```

#### Case Statements

```ruby
age =  5
case age
when 0 .. 2
    puts "baby"
when 3 .. 6
    puts "little child"
when 7 .. 12
    puts "child"
when 13 .. 18
    puts "youth"
else
    puts "adult"
end
```

#### Ternary Operators

The ternary operator looks terribly complicated but is really kind of straightforward once you get used to it.  

Here is an example of a ternary operator in action:

```ruby
2.0.0p247 :006 > orange = 3
 => 3 
2.0.0p247 :007 > apple = 5
 => 5 
2.0.0p247 :010 > apple > orange ?  (puts "yes") : (puts "no")
yes
```
So how does this work?  It says that if the statement on the left (apple > orange) is true, then print "yes" in the terminal, but if not, then print "no".  This a very concise form of conditional statement that you will see more of later on. 

### _What Can I Do With It?_

Conditionals allow you to build logic into your applications. Putting these conditionals together, you can create logic that will make sure that your users give the information you want and you can give them the response that they want/need.   

### _Why Do I Care?_

All but the smallest applications have options.  Conditionals allow you to manage options.  They also all have inputs and outputs and conditionals help you to manage those as well.  

## Exercise

Order a cup of coffee using conditionals.
 
## Happiness Checkpoint

Share your implementation with the class.  

## Project Guidelines

Yesterday you made a menu using variables.  Now imagine a user going through that menu and make sure that they give you the inputs you want and they get the outputs they need to make decisions.

## Solve

Make the application.  Then have someone in the pair next to your pair try it out.  

## Extensions

Try to use all of the different conditionals in your application if you haven't already.  

## Push Instructions

Push this code to your BOS repo.

## Further Readings

* [Ruby If/Else Tutorial](http://www.tutorialspoint.com/ruby/ruby_if_else.htm)
* [Ruby for Newbies Conditional Statements and Loops](http://net.tutsplus.com/tutorials/ruby/ruby-for-newbies-conditional-statements-and-loops/)