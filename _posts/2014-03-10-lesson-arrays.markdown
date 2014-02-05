---
layout: post
title: "Week 2 : Lesson 1 : Arrays"
category: lesson
published: true
---

## Review

Review from [Week 1 : Lesson 7 : Time]({{ site.baseurl}}{% post_url 2014-03-07-lesson-time %}).  One (or more) pair will rehash the previous session's lesson by teaching the basic learnings to the group.  They will explain it to the others by drawing a diagram, using an analogy, telling a story or in some other way creatively communicating the idea without using code.

## Today's Project<a name="todays-project"></a>

Part of [Week 2 : Project 1 : Crime Blotter]({{ site.baseurl}}{% post_url 2014-03-11-project-crime-blotter %}).

## Arrays

### _What Is It?_

Whereas a variable can hold only one piece of data at time, an array is a type of data storage that can be used to hold multiple pieces of data in a list-like form.

### _How Does It Work?_

As an analogy, an array is a little like a backpack. You put things in one at a time.  Stuff on the bottom can only be found by remembering that its on the bottom.  Otherwise, you gotta root around.  

First of all, this is what an array looks like:

```ruby
["apple", "orange", "mango"]
```
There are two ways to create an array.  What is called a "literal constructor" works as follows: 

```ruby
2.0.0p247 :001 > fruit = ["apple", "orange", "mango"]
 => ["apple", "orange", "mango"] 
2.0.0p247 :002 > fruit
 => ["apple", "orange", "mango"] 
```

There is also the "object constructor":

```ruby
2.0.0p247 :007 > fruit = Array.new
 => [] 
2.0.0p247 :008 > fruit[0] = "apple"
 => "apple" 
2.0.0p247 :009 > fruit[1] = "orange"
 => "orange" 
2.0.0p247 :010 > fruit[2] = "mango"
 => "mango" 
2.0.0p247 :011 > fruit
 => ["apple", "orange", "mango"]
```

This one is a bit more complicated.  We first create an empty array.  Then we assign a value to each position in the array.  It's worth noting that an array's first position is [0] not [1].  This is a convention that came about as a way to save precious bytes in earlier days of computing.

To get an element from an array, you need to know the position of the element.  So, if we are looking for orange, we have to know that orange is the second element which is in the [1] position.

```ruby
2.0.0p247 :016 > fruit
 => ["apple", "orange", "mango", "kiwi"] 
2.0.0p247 :017 > fruit[1]
 => "orange" 
```
There are a couple more ways of doing the above as well.  

To create an array using a literal constructor:

```ruby
2.0.0p247 :019 > fruit = %w(apple orange mango kiwi)
 => ["apple", "orange", "mango", "kiwi"] 
```

To push something to an array:

```ruby
2.0.0p247 :001 > fruit = []
 => [] 
2.0.0p247 :002 > fruit << "apple"
 => ["apple"] 
2.0.0p247 :003 > fruit << "orange"
 => ["apple", "orange"] 
```

What kinds of things can we put in an array?  

```ruby
various = [1, -1, "big", 3.4, Empty.new, nums, :two]
```

So integers, both positive and negative, strings, floats, custom objects, variables, and even symbols can be entered into an array.  What's more, you can also put an array in an array:

```ruby
2.0.0p247 :001 > fruit = ["apple", "orange", "mango"]
 => ["apple", "orange", "mango"] 
2.0.0p247 :002 > groceries = [fruit]
 => [["apple", "orange", "mango"]] 
2.0.0p247 :003 > veggies = ["carrot", "broccoli", "onion"]
 => ["carrot", "broccoli", "onion"] 
2.0.0p247 :004 > groceries << veggies
 => [["apple", "orange", "mango"], ["carrot", "broccoli", "onion"]] 
2.0.0p247 :005 > groceries
 => [["apple", "orange", "mango"], ["carrot", "broccoli", "onion"]] 
```

In addition to these basic functions, arrays also have a number of built in methods that replicate or expand on these basic functions of putting stuff in arrays and then getting it out.

#### Push

If you want to add something to the array and don't know what the last position was, then you can use the **push** method:

```ruby
2.0.0p247 :014 > fruit
 => ["apple", "orange", "mango"] 
2.0.0p247 :015 > fruit.push "kiwi"
 => ["apple", "orange", "mango", "kiwi"] 
```

#### Insert

If you want to add a element to your array at a specific position, you can use the **insert** method.  Just specify the position and the element you want to add:

```ruby
2.0.0p247 :006 > fruit
 => ["apple", "orange", "mango"] 
2.0.0p247 :007 > fruit.insert(1, "kumquat")
 => ["apple", "kumquat", "orange", "mango"] 
```

#### Pop

The **pop** method deletes the last item in an array:

```ruby
2.0.0p247 :009 > fruit
 => ["apple", "kumquat", "orange", "mango"] 
2.0.0p247 :010 > fruit.pop
 => "mango" 
2.0.0p247 :011 > fruit
 => ["apple", "kumquat", "orange"] 
```

#### Shift

The **shift** method returns the first item in an array and deletes it:

```ruby
2.0.0p247 :012 > fruit
 => ["apple", "kumquat", "orange"] 
2.0.0p247 :013 > fruit.shift
 => "apple" 
2.0.0p247 :014 > fruit
 => ["kumquat", "orange"] 
```

#### Delete_at

Delete an element at a particular index:

```ruby
2.0.0p247 :017 > fruit
 => ["kumquat", "orange", "apple", "peach"] 
2.0.0p247 :018 > fruit.delete_at(1)
 => "orange" 
2.0.0p247 :019 > fruit
 => ["kumquat", "apple", "peach"] 
```

#### Delete

Delete a particular element anywhere in an array:

```ruby
2.0.0p247 :022 > fruit
 => ["kumquat", "apple", "peach", "orange", "apple"] 
2.0.0p247 :023 > fruit.delete("apple")
 => "apple" 
2.0.0p247 :024 > fruit
 => ["kumquat", "peach", "orange"] 
```

#### Length

The **length** method gives you the number of items in an array:

```ruby
2.0.0p247 :024 > fruit
 => ["kumquat", "peach", "orange"] 
2.0.0p247 :025 > fruit.length
 => 3 
```

#### Each

The **each** method takes each element in an array and then does something to it:

{% highlight irb linenos %}
irb(main):003:0> fruit
=> ["kumquat salad", "peach salad", "orange salad"]
irb(main):004:0> fruit.each {|x| puts x }
kumquat salad
peach salad
orange salad
=> ["kumquat salad", "peach salad", "orange salad"]
{% endhighlight %}

In this case, the syntax could also be read as, "go through the array 'fruit' and for reach each element, x, perform the puts actions."

#### Map

There are two variants of the **map** method. The first method, without an **!**, is a little like **each** in that it takes each element of the array, applies the transformation that you want, and leaves the original array unchanged. The difference is that the **map** method returns an array with your transformation:

```ruby
2.0.0p247 :026 > fruit
 => ["kumquat", "peach", "orange"] 
2.0.0p247 :027 > fruit.map {|x| x + " salad"}
 => ["kumquat salad", "peach salad", "orange salad"] 
2.0.0p247 :028 > fruit
 => ["kumquat", "peach", "orange"] 
```
In the other variant of the **map** method, the one with the **!**, the array that you are "mapping" is returned with the transformation _and_ the original is also transformed.  That is often the case when the **!** is used:

{% highlight irb linenos %}
irb(main):001:0> fruit = ["kumquat", "peach", "orange"] 
=> ["kumquat", "peach", "orange"]
irb(main):002:0> fruit.map! {|x| x + " salad"}
=> ["kumquat salad", "peach salad", "orange salad"]
irb(main):003:0> fruit
=> ["kumquat salad", "peach salad", "orange salad"]
{% endhighlight %}

#### Include?

So what do you do if you want to find something in an array?  The **include?** method comes in handy.  It returns true if the given object is present in the array; otherwise it returns false:

{% highlight irb linenos %}
irb(main):006:0> fruit
=> ["kumquat salad", "peach salad", "orange salad"]
irb(main):007:0> fruit.include?("peach salad")
=> true
irb(main):008:0> fruit.include?("tomato salad")
=> false
{% endhighlight %}

#### Reverse 

This method is only so handy, but for some reason it is frequently referenced in quizzes.  It returns a reversed version of the given array, but does not change or transform the array:

{% highlight irb linenos %}
irb(main):009:0> fruit
=> ["kumquat salad", "peach salad", "orange salad"]
irb(main):010:0> fruit.reverse
=> ["orange salad", "peach salad", "kumquat salad"]
irb(main):011:0> fruit
=> ["kumquat salad", "peach salad", "orange salad"]
{% endhighlight %}

#### One Last Tip

What do you do if you want to get the last element in an array?  Easy:

{% highlight irb linenos %}
irb(main):011:0> fruit
=> ["kumquat salad", "peach salad", "orange salad"]
irb(main):012:0> fruit[-1]
=> "orange salad"
{% endhighlight %}

### _What Can I Do With It?_

Store data that you receive as inputs. Let's use this script for, example:

{% highlight ruby linenos %}
puts "What is your favorite fruit?"
fruit = gets.chomp
grocery_list = []
grocery_list << fruit

puts "What is your favorite veggie?"
veggie = gets.chomp
grocery_list << veggie

puts "Your Grocery List:"
puts "=================="
puts grocery_list

print grocery_list

{% endhighlight %}

Which gives us the following output (with my inputs given to the questions):

{% highlight irb linenos %}
What is your favorite fruit?
Melon
What is your favorite veggie?
Cauliflower
Your Grocery List:
==================
Melon
Cauliflower
["Melon", "Cauliflower"]=> true
{% endhighlight %}

### _Why Do I Care?_

## Exercise

## Happiness Checkpoint

## Project Guidelines

## Solve

## Extensions

## Push Instructions

## Further Readings

* [Ruby Documentation on Arrays](http://www.ruby-doc.org/core-2.1.0/Array.html)
* [Arrays in Ruby](http://zetcode.com/lang/rubytutorial/arrays/)
* [Ruby Arrays](http://www.tutorialspoint.com/ruby/ruby_arrays.htm)

## Week's Badges

This week, the following badges are up for grabs:

* 

Let your instructor know at lunch if you would like to earn one of these badges.