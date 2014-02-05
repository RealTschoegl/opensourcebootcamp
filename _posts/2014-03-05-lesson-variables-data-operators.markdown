---
layout: post
title: "Week 1 : Lesson 5 : Variables, Data Types, and Operators"
category: lesson
published: true
---

## Review

Review from [Week 1 : Lesson 4 : Heroku]({{ site.baseurl}}{% post_url 2014-03-04-lesson-heroku %}).  One (or more) pair will rehash the previous session's lesson by teaching the basic learnings to the group.  They will explain it to the others by drawing a diagram, using an analogy, telling a story or in some other way creatively communicating the idea without using code.

## Today's Project<a name="todays-project"></a>

Part of [Week 1 : Project 1 : BOS]({{ site.baseurl}}{% post_url 2014-03-07-project-bos %}).

## Variables, Data Types, and Operators

### _What Is It?_

One of the things that you will hear a lot about Ruby is how everything is an object.  It will take a little while before that really sinks in.  First, we're going to take a little bit of time to learn how to create an object, know what the object is, and then how to change it.  

A variable is ...

A data type is ...

Operators are ...

### _How Does It Work?_

Assigning a variable just means that you make the thing on the left equal to the thing on the right.  So, in the example below:

```ruby
apple = 2
```

_In your Ruby program, any time the variable **apple** is used, the program will treat it as if it is the value **2**.  Why bother?  Can't we just enter the value **2** and be done with it?  Yes!  Then why bother?_

_Well, we are going to do things to this apple.  Awful things.  But that means that we need to make sure that each part of our applications knows what this value is. However we received that input, we are probably not going to want to just keep asking for that input again and again, right?_

_Keep this in the back of your head as we proceed - often times we make things a little more complicated than they need to be in order to make them much simpler in the future._

Assignment is like putting something in a bucket.  Except first you the tip the bucket over and then put something in it.  Every time.  For example: 

```ruby
2.0.0-p247 :001 > orange = 2
 => 2 
2.0.0-p247 :002 > orange 
 => 2 
2.0.0-p247 :003 > orange = 4
 => 4 
2.0.0-p247 :004 > orange
 => 4
``` 

There are a few other assignment operators worth mentioning. If you have assigned a number 

Let's say that in the example above you had actually wanted to increase the value of orange by four, not reassign the value.  How could you do that?  Well, the easiest way is to incrememnt the value using: +=

```ruby
2.0.0-p247 :006 > orange = 2
 => 2 
2.0.0-p247 :007 > orange 
 => 2 
2.0.0-p247 :008 > orange += 4
 => 6 
2.0.0-p247 :009 > orange
 => 6
```

If you want to subtract from the value, that's not so hard either.  Use the decrement operator: -= 

```ruby
2.0.0p247 :001 > orange = 2
 => 2 
2.0.0p247 :002 > apple = 4
 => 4 
2.0.0p247 :003 > apple -= orange
 => 2 
```

Back to it...What is apple now?  It's an **Integer**.  Remember integers?  They're whole numbers.



```ruby
2.0.0-p247 :003 > apple = "Apple"
 => "Apple" 
2.0.0-p247 :004 > apple
 => "Apple"
```

Does it have to be an integer if it's a number?  No, it can also be a **Float**.  

```ruby
2.0.0-p247 :019 > quasimodo = 1.5
 => 1.5 
2.0.0-p247 :020 > quasimodo
 => 1.5 
```
     
What else can we do with apple?  Well, we can make it equal to a **String**.

```ruby
apple = "Apple"
```
    
And when we enter it into IRB, we get:
  
```ruby
2.0.0-p247 :003 > apple = "Apple"
 => "Apple" 
2.0.0-p247 :004 > apple
 => "Apple"
```
What else can it be? It can be a **Boolean**! Isn't that cool!!  What's a Boolean ... A Boolean is a datatype which can only have two values: True or False.  

```ruby
2.0.0-p247 :010 > platypus = true
 => true 
2.0.0-p247 :011 > platypus
 => true 
```
How do we check what type of value a variable is?  Well, everything in Ruby is an object and every object belongs to a class. So let's get its class.

```ruby
2.0.0-p247 :001 > platypus = true
 => true 
2.0.0-p247 :002 > platypus.class
 => TrueClass 
```

When we have assigned these various types of data, we can begin to perform operations on them.  Basically, having created an object, we can now do things with it. 

### Arithmetic Operators

These are about doing math on the object.  Below are some of the options:

#### Addition

```ruby
2.0.0-p247 :001 > apple = 2
 => 2 
2.0.0-p247 :002 > banana = 5
 => 5 
2.0.0-p247 :003 > apple + banana
 => 7
```

There is also a way that you can use addition plus assignment to change the value of the variable.  

```ruby
apple = 2
orange = 4
apple = apple + orange
```

#### Subtraction

```ruby
2.0.0-p247 :001 > apple = 2
 => 2 
2.0.0-p247 :002 > banana = 5
 => 5
2.0.0-p247 :003 > banana - apple
 => 3 
2.0.0-p247 :004 > apple - banana
 => -3 
```

#### Multiplication

```ruby
2.0.0-p247 :001 > apple = 2
 => 2 
2.0.0-p247 :002 > banana = 5
 => 5
2.0.0-p247 :003 > apple * banana
 => 10 
```

#### Division 

```ruby
2.0.0-p247 :001 > apple = 2
 => 2 
2.0.0-p247 :002 > banana = 5
 => 5
2.0.0-p247 :003 > banana / apple
 => 2
```

Wait, what?  Banana equals 5.  Apple equals 2.  I might not be a math whiz, but I know that equals 2.5?  Why is it giving me two?  

Because banana is an integer and apple is an integer.  The returned value, therefore, can only be an integer.  And the integer value of 2.5 is 2.  Computers, amirite?   If you want it to return a float value, you need to make one or both of those values a float.  

#### Modulo

My favorite operator, the modulo divides the number on the left by the number on the right and returns the remainder.  This may not sound particularly useful.  Until you need to get an even or odd number.  

```ruby
2.0.0-p247 :001 > kumquat = 6
 => 6 
2.0.0-p247 :002 > kumquat % 2
 => 0 
2.0.0-p247 :003 > kumquat % 4
 => 2 
```

#### Exponent 

Take the value on the left to the value of the power on the right.   

```ruby
2.0.0-p247 :004 > guava = 2
 => 2 
2.0.0-p247 :005 > guava ** 3
 => 8 
```

### Comparison Operators

These operators tell you how one value or variable compares to another value or variable.

#### ==

Does the value on the left equal the value on the right?

```ruby
2.0.0-p247 :006 > kiwi = 2
 => 2 
2.0.0-p247 :007 > apple = 2
 => 2 
2.0.0-p247 :008 > kiwi == apple
 => true 
```

#### !=

Does the value on the _left_ not equal the value on the right?

```ruby
2.0.0-p247 :001 > orange = 4.50
 => 4.5 
2.0.0-p247 :002 > apricot = 5.60
 => 5.6 
2.0.0-p247 :003 > orange != apricot
 => true 
```

#### >, >=, <, <=

```ruby
2.0.0p247 :001 > 5 > 4
 => true 
2.0.0p247 :002 > 5 >= 5
 => true 
2.0.0p247 :003 > 4 <= 5
 => true 
2.0.0p247 :004 > 4 < 5
 => true 
2.0.0p247 :005 > 7 < 6
 => false 
```

#### <=>

This operator might be a bit unusual, if not paradoxical, on first glance, but it shows up fairly frequent and can really come in handy.  Rather than returning a boolean value, this operand returns a numeric value that corresponds with the relationship between the left variable and the right one.  As so: 

```ruby
2.0.0p247 :001 > 3 <=> 3
 => 0 
2.0.0p247 :002 > 3 <=> 2
 => 1 
2.0.0p247 :003 > 3 <=> 4
 => -1
```

### _What Can I Do With It?_

Try building some logic.

```ruby
2.0.0-p247 :005 > lunch = "sandwich"
 => "sandwich" 
2.0.0-p247 :006 > drink = "coke"
 => "coke" 
2.0.0-p247 :007 > text = "I had a " + lunch + " and a " +  drink
 => "I had a sandwich and a coke"
2.0.0-p247 :008 > text
 => "I had a sandwich and a coke"
```

### Logical Operators

These are basic logical building blocks.

**&&** - if both are true, then it returns true 

```ruby
2.0.0p247 :001 > first_answer = true
 => true 
2.0.0p247 :002 > second_answer = false
 => false 
2.0.0p247 :003 > first_answer && second_answer
 => false 
```

**||**	- if either is true, then it returns true

```ruby
2.0.0p247 :001 > first_answer = true
 => true 
2.0.0p247 :002 > second_answer = false
 => false 
2.0.0p247 :003 > first_answer || second_answer
 => true 
```

**!** - if it is _not_ true, then it returns true

```ruby
2.0.0p247 :012 > answer = true
 => true 
2.0.0p247 :013 > !answer
 => false 
2.0.0p247 :014 > answer = false
 => false 
2.0.0p247 :015 > !answer
 => true
```

 
### _Why Do I Care?_

Ruby is an Object-Oriented programming language.  That means that you are always creating object and then changing those objects and then showing those objects to the user.  This lesson is all about making those objects, figuring out what they are, and then doing stuff to them.

## Exercise

Imagine your ideal partner.  Make a list of conditions that they would have to meet.  At least five.  If you don't get why the below works, find an instructor.

```ruby
2.0.0p247 :008 > partner = "breathing"
 => "breathing" 
2.0.0p247 :009 > partner == "breathing"
 => true
```

## Happiness Checkpoint

Find an instructor and be prepared to explain your code and your utterly unrealistic expecations for your partner.  

## Project Guidelines

Without taking user input, imagine the scenario and what the user would want.  Try to use as many conditionals as possible.  

## Solve

Create a menu with prices.

## Extensions

Take user input using [gets](http://www.ruby-doc.org/docs/Tutorial/part_02/user_input.html)

## Push Instructions

Push your Ruby doc to the Github repo you created yesterday.

## Further Readings

* [RubyBacon: Ruby Data Types](http://www.rubybacon.com/ruby-data-types/)
* [Tutorial on Ruby Operators](http://www.tutorialspoint.com/ruby/ruby_operators.htm)