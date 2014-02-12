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

There are also a couple of other ways to invoke a method although they can only really be called on an explicit object.  In truth, all methods that we looked at above are called on an object - the Object class, to which we added them.  

So here, we create any old object and give it a method, fingers:

{% highlight irb linenos %}
irb(main):001:0> def fingers
irb(main):002:1>   (0...10).each {|x| puts x * 2 }
irb(main):003:1> end
=> nil
irb(main):004:0> fingers
0
2
4
6
8
10
12
14
16
18
=> 0...10
irb(main):005:0> hand = Object.new
=> #<Object:0x007fabae0904f0>
irb(main):006:0> hand.method(:fingers)
=> #<Method: Object#fingers>
{% endhighlight %}

We can then call this finger method in two different ways:

{% highlight irb linenos %}
hand.method(:fingers).call
hand.send(:fingers)
{% endhighlight %}

There is one other thing worth taking a look at.  See this piece of code:

{% highlight irb linenos %}
irb(main):019:0> m = 12.method(:+)
=> #<Method: Fixnum#+>
irb(main):020:0> m.call(4)
=> 16
{% endhighlight %}

Which can also be written a little more clearly this way:

{% highlight irb linenos %}
irb(main):025:0> 12.method(:+).call(4)
=> 16
{% endhighlight %}

So what are we looking at?  First of all, what is 12?  

{% highlight irb linenos %}
irb(main):037:0> 12.class
=> Fixnum
{% endhighlight %}

As we can se, 12 is just an object of the Fixnum class.  Next, we are calling a method on it.  What method?  The addition method - yes, addition is a method: 

{% highlight irb linenos %}
irb(main):039:0> Fixnum.public_instance_methods
=> [:to_s, :inspect, :-@, :+, :-, :*, :/, :div, :%, :modulo, :divmod, :fdiv, :**, :abs, :magnitude, :==, :===, :<=>, :>, :>=, :<, :<=, :~, :&, :|, :^, :[], :<<, :>>, :to_f, :size, :zero?, :odd?, :even?, :succ, :integer?, :upto, :downto, :times, :next, :pred, :chr, :ord, :to_i, :to_int, :floor, :ceil, :truncate, :round, :gcd, :lcm, :gcdlcm, :numerator, :denominator, :to_r, :rationalize, :singleton_method_added, :coerce, :i, :+@, :eql?, :quo, :remainder, :real?, :nonzero?, :step, :to_c, :real, :imaginary, :imag, :abs2, :arg, :angle, :phase, :rectangular, :rect, :polar, :conjugate, :conj, :between?, :nil?, :=~, :!~, :hash, :class, :singleton_class, :clone, :dup, :taint, :tainted?, :untaint, :untrust, :untrusted?, :trust, :freeze, :frozen?, :methods, :singleton_methods, :protected_methods, :private_methods, :public_methods, :instance_variables, :instance_variable_get, :instance_variable_set, :instance_variable_defined?, :remove_instance_variable, :instance_of?, :kind_of?, :is_a?, :tap, :send, :public_send, :respond_to?, :extend, :display, :method, :public_method, :define_singleton_method, :object_id, :to_enum, :enum_for, :equal?, :!, :!=, :instance_eval, :instance_exec, :__send__, :__id__]
{% endhighlight %}

Finally, we want to look at how we call it - does it take arguments and how many?  For that, we can use the **arity** method:

{% highlight irb linenos %}
irb(main):034:0> 12.method(:+).arity
=> 1
{% endhighlight %}

Let's do some looking.  The 12 is a Fixnum.  Does Fixnum have a plus method?  Yes, it does.  Can you really pass that method a parameter?  Yup.







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