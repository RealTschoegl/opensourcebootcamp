---
layout: post
title: "Week 2 : Lesson 2 : Methods"
category: lesson
published: true
---

## Review

Review from [Week 2 : Lesson 1 : Arrays]({{ site.baseurl}}{% post_url 2014-03-10-lesson-arrays %}).  One (or more) pair will rehash the previous session's lesson by teaching the basic learnings to the group.  They will explain it to the others by drawing a diagram, using an analogy, telling a story or in some other way creatively communicating the idea without using code.

## Today's Project<a name="todays-project"></a>

Part of [Week 2 : Project 1 : Crime Blotter]({{ site.baseurl}}{% post_url 2014-03-11-project-crime-blotter %}).

## Methods

### _What Is It?_

Methods are objects that do things.  Isn't that cool?  Or, more precisely:

> A method in Ruby is a set of expressions that returns a value. With methods, one can organize their code into subroutines that can be easily invoked from other areas of their program. 

Basically, a method is a piece of code that, when called, does something.  Up until now, all of the code that we have written has run upon loading the file.  The method lets us run code only when we want to.  It's the difference between taking the bus and calling a taxi.  Taxis are nice.  

### _How Does It Work?_

We actually have already run somethings that are a lot like methods.  You should remember from our lessons on arrays and loops that we are able to loop through an array and print out each thing in the array

{% highlight irb linenos %}
irb(main):044:0> nums = [1, 2, 3, 4, 5]
=> [1, 2, 3, 4, 5]
irb(main):045:0> 
irb(main):046:0* nums.each do |num|
irb(main):047:1*     puts num
irb(main):048:1> end
1
2
3
4
5
=> [1, 2, 3, 4, 5]
{% endhighlight %}

We've also used **blocks**:

{% highlight irb linenos %}
irb(main):049:0> nums
=> [1, 2, 3, 4, 5]
irb(main):050:0> nums.each {|num| puts num}
1
2
3
4
5
=> [1, 2, 3, 4, 5]
{% endhighlight %}

How do these differ from methods?  Methods are _reusable_.  We can call a method from another part of our code rather than having it run automatically.  Here is what a method looks like:

{% highlight irb linenos %}
irb(main):080:0> def listy
irb(main):081:1> 	(0..5).each do |x|
irb(main):082:2* 		puts x
irb(main):083:2> 	end
irb(main):084:1> end
=> nil
irb(main):085:0> listy
0
1
2
3
4
5
=> 0..5
{% endhighlight %}

The method has a name, **listy**, and performs an action - in this case, putting each number in a range.  We then call the method after we have defined it, by simply typing **listy**. 

This method, though, only performs the action on a set range. What if we want it to perform the listing action, though, on a number that reflects user input?  In that case, we can have the method take a **parameter**.  A **parameter** is just a piece of input that the method expects and is ready to use (if you don't include anything for a parameter, it gets confused and upset).  

{% highlight irb linenos %}
irb(main):001:0> students = ["Tom", "Tao", "Thor"]
=> ["Tom", "Tao", "Thor"]
irb(main):002:0> def bootcamp(students)
irb(main):003:1> students.each {|student| puts student}
irb(main):004:1> end
=> nil
irb(main):005:0> bootcamp(students)
Tom
Tao
Thor
=> ["Tom", "Tao", "Thor"]
{% endhighlight %}

The method can actually take multiple parameters:

{% highlight irb linenos %}
irb(main):015:0> fruit = ["mango", "apple", "banana"]
=> ["mango", "apple", "banana"]
irb(main):016:0> veggie = ["cucumber", "carrot", "brussel sprout"]
=> ["cucumber", "carrot", "brussel sprout"]
irb(main):017:0> def shopping_list(one, two)
irb(main):018:1> puts one
irb(main):019:1> puts two
irb(main):020:1> end
=> nil
irb(main):021:0> shopping_list(fruit, veggie)
mango
apple
banana
cucumber
carrot
brussel sprout
{% endhighlight %}

Or even an unknown number of parameters

{% highlight irb linenos %}
irb(main):023:0> def shopping_list(*items)
irb(main):024:1> puts *items
irb(main):025:1> end
=> nil
irb(main):026:0> shopping_list(fruit,veggie)
mango
apple
banana
cucumber
carrot
brussel sprout
{% endhighlight %}

You can also call a method from inside of a method:

{% highlight irb linenos %}
irb(main):007:0> def one
irb(main):008:1> 	puts "One"
irb(main):009:1> end
=> nil
irb(main):010:0> def two
irb(main):011:1> 	one
irb(main):012:1> 	puts "Two"
irb(main):013:1> end
=> nil
irb(main):014:0> two
One
Two
{% endhighlight %}

### _What Can I Do With It?_

Let's build something by chaining some methods together.  We are going to put some methods together to make a dinner.  

puts "Are you allergic to gluten?(Y/N)"
allergy = gets.chomp
puts "Do you dig on swine?(Y/N)"
hallal = gets.chomp
puts "Are you lactose intolerant?(Y/N)"
vegetarian = gets.chomp

if allergy == "Y"
	appetizer("breadless")
else
	appetizer("breadful")
end

if hallal == "Y"
	main("pigless")
else
	main("pigful")
end

if vegetarian == "Y"
	dessert("dairyless")
else
	dessert("dairyful")
end

def appetizer(choice)
	choice == "breadless" ? puts ("Brussel Sprouts") : puts ("Garlic Bread")
end

def main(choice)
	choice == "pigless" ? puts ("Scallops" : puts ("Prosciutto")
end

def dessert(choice)
	choice == "dairyless" ? puts ("Strawberry Rhubarb Pie" : puts ("Banana Cream Pie")
end

### _Why Do I Care?_

## Exercise

## Happiness Checkpoint

## Project Guidelines

## Solve

## Extensions

## Push Instructions

## Further Readings

* [Ruby Documentation on Methods](http://www.ruby-doc.org/core-2.1.0/Method.html)
* [Ruby Methods](http://www.tutorialspoint.com/ruby/ruby_methods.htm)
* [Writing Own Ruby Methods](http://rubylearning.com/satishtalim/writing_own_ruby_methods.html)