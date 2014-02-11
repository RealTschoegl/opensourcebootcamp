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

{% highlight irb linenos %}
irb(main):006:0> grocery_list = {}
=> {}
irb(main):007:0> grocery_list["fruit"] = "mango"
=> "mango"
irb(main):008:0> grocery_list[:fruit] = "apple"
=> "apple"
irb(main):009:0> grocery_list[["fruit","salad"]] = "raspberry"
=> "raspberry"
irb(main):010:0> grocery_list[1] = "items"
=> "items"
irb(main):011:0> grocery_list[Object.new] = "Thing"
=> "Thing"
irb(main):012:0> grocery_list
=> {"fruit"=>"mango", :fruit => "apple", ["fruit", "salad"]=>"raspberry", 1=>"items", #<Object:0x007f8abd95ec10>=>"Thing"}
{% endhighlight %}

When using a symbol as a key, there is another notation that you can also use:

{% highlight irb linenos %}
irb(main):043:0> fruit = { pear: "anjou" }
=> {:pear=>"anjou"}
{% endhighlight %}

You can even use variables as keys and values in a hash - or at least the values from the variables:

{% highlight irb linenos %}
irb(main):034:0> your_hash = {}
=> {}
irb(main):035:0> hash_key = gets.chomp
S
=> "S"
irb(main):036:0> hash_value = gets.chomp
B
=> "B"
irb(main):037:0> your_hash[hash_key] = hash_value
=> "B"
irb(main):038:0> your_hash 
=> {"S"=>"B"}
{% endhighlight %}

What can be the value?  Pretty much anything that can be the key.

How do you add something to a hash?  One, you can add a value to hash on creation:

{% highlight irb linenos %}
irb(main):001:0> students = { "Thomas" => "John", "Robinson" => "Craig" }
=> {"Thomas"=>"John", "Robinson"=>"Craig"}
irb(main):002:0> students
=> {"Thomas"=>"John", "Robinson"=>"Craig"}
{% endhighlight %}

Once you have an existing hash, it is as easy as this:

{% highlight irb linenos %}
irb(main):003:0> students["Simpson"] = "Homer"
=> "Homer"
irb(main):004:0> students
=> {"Thomas"=>"John", "Robinson"=>"Craig", "Simpson"=>"Homer"}
{% endhighlight %}

Alternatively:

{% highlight irb linenos %}
irb(main):004:0> students
=> {"Thomas"=>"John", "Robinson"=>"Craig", "Simpson"=>"Homer"}
irb(main):005:0> students.store("Crusoe", "Robinson")
=> "Robinson"
irb(main):006:0> students
=> {"Thomas"=>"John", "Robinson"=>"Craig", "Simpson"=>"Homer", "Crusoe"=>"Robinson"}
{% endhighlight %}

Or you can merge an existing hash with your new hash to add to it:

{% highlight irb linenos %}
irb(main):010:0> a = {"Brewster" => "Punky"}
=> {"Brewster"=>"Punky"}
irb(main):011:0> students.merge!(a)
=> {"Thomas"=>"John", "Robinson"=>"Craig", "Simpson"=>"Homer", "Crusoe"=>"Robinson", "Brewster"=>"Punky"}
{% endhighlight %}

What if I want to get information out of a hash? There are a number of methods to do so, but none of them that work sequentially as with an array. 

If you know the key, it's pretty easy.  Just follow the name of the hash with the key that is associated with the value:

{% highlight irb linenos %}
irb(main):003:0> students
=> {"Thomas"=>"John", "Robinson"=>"Craig", "Simpson"=>"Homer", "Crusoe"=>"Robinson", "Brewster"=>"Punky"}
irb(main):004:0> students["Robinson"]
=> "Craig"
{% endhighlight %}

Does it work the other way?  

{% highlight irb linenos %}
irb(main):005:0> students["Robinson"]
=> "Craig"
irb(main):006:0> students["Craig"]
=> nil
{% endhighlight %}

No.

What if I want to get out all of the elements in a hash?  This is where the **each** method comes in handy:

{% highlight irb linenos %}
irb(main):009:0> students.each {|key,value| puts key }
Thomas
Robinson
Simpson
Crusoe
Brewster
=> {"Thomas"=>"John", "Robinson"=>"Craig", "Simpson"=>"Homer", "Crusoe"=>"Robinson", "Brewster"=>"Punky"}
{% endhighlight %}

What if I don't know if it has a key?

{% highlight irb linenos %}
irb(main):012:0> students.has_key?("Thomas")
=> true
irb(main):013:0> students
=> {"Thomas"=>"John", "Robinson"=>"Craig", "Simpson"=>"Homer", "Crusoe"=>"Robinson", "Brewster"=>"Punky"}
irb(main):014:0> students.has_key?("Thomasina")
=> false
{% endhighlight %}

What if you only want to get those elements from a hash that meet a certain criteria, say that either the key or value contain the name Robinson.  **Select** returns a new hash consisting of entries for which the block returns true:

{% highlight irb linenos %}
irb(main):001:0> students = {"Thomas"=>"John", "Robinson"=>"Craig", "Simpson"=>"Homer", "Crusoe"=>"Robinson", "Brewster"=>"Punky"}
=> {"Thomas"=>"John", "Robinson"=>"Craig", "Simpson"=>"Homer", "Crusoe"=>"Robinson", "Brewster"=>"Punky"}
irb(main):004:0> students.select {|key,value| key == "Robinson" || value == "Robinson"}
=> {"Robinson"=>"Craig", "Crusoe"=>"Robinson"}
irb(main):005:0> students
=> {"Thomas"=>"John", "Robinson"=>"Craig", "Simpson"=>"Homer", "Crusoe"=>"Robinson", "Brewster"=>"Punky"}
{% endhighlight %}

If we want to delete something in the hash, then just specify the key and use the **delete** method (you can also use **delete_if** when there is a logic behind which entries should be deleted):

{% highlight irb linenos %}
irb(main):005:0> students
=> {"Thomas"=>"John", "Robinson"=>"Craig", "Simpson"=>"Homer", "Crusoe"=>"Robinson", "Brewster"=>"Punky"}
irb(main):006:0> students.delete("Thomas")
=> "John"
irb(main):007:0> students
=> {"Robinson"=>"Craig", "Simpson"=>"Homer", "Crusoe"=>"Robinson", "Brewster"=>"Punky"}
irb(main):009:0> students.delete_if {|key| key == "Simpson" }
=> {"Robinson"=>"Craig", "Crusoe"=>"Robinson", "Brewster"=>"Punky"}
irb(main):010:0> students
=> {"Robinson"=>"Craig", "Crusoe"=>"Robinson", "Brewster"=>"Punky"}
{% endhighlight %}

Another useful method treats the case where we want to move data between a hash and an array: **flatten**.  

{% highlight irb linenos %}
irb(main):010:0> students
=> {"Robinson"=>"Craig", "Crusoe"=>"Robinson", "Brewster"=>"Punky"}
irb(main):011:0> students.flatten
=> ["Robinson", "Craig", "Crusoe", "Robinson", "Brewster", "Punky"]
{% endhighlight %}

This may not seem like a hugely valuable asset, but there are some methods or operations that are more easily performed with one type of data storage rather than the other.

### _What Can I Do With It?_

Let's say I want to create a playlist of artists and their songs.  So, we can seed it (add in some sample data):

{% highlight irb linenos %}
irb(main):002:0> playlist = { "Led Zeppelin" => "Kashmir", "Nena" => "99 Luft Ballons", "Nirvana" => "Where Did You Sleep Last Night", "Modest Mouse" => "Satin in a Coffin" } 
=> {"Led Zeppelin"=>"Kashmir", "Nena"=>"99 Luft Ballons", "Nirvana"=>"Where Did You Sleep Last Night", "Modest Mouse"=>"Satin in a Coffin"}
{% endhighlight %}

Now this is just data storage.  What if I want to print it out so the user can see it?  What can I do? Well, we can create a small method that takes each key-value pair form the hash and prints it in a format we like:

{% highlight irb linenos %}
irb(main):005:0> playlist.each {|key,value| puts "#{key}: #{value}."}
Led Zeppelin: Kashmir.
Nena: 99 Luft Ballons.
Nirvana: Where Did You Sleep Last Night.
Modest Mouse: Satin in a Coffin.
=> {"Led Zeppelin"=>"Kashmir", "Nena"=>"99 Luft Ballons", "Nirvana"=>"Where Did You Sleep Last Night", "Modest Mouse"=>"Satin in a Coffin"
{% endhighlight %}

But who really wants to just print out a playlist?  What is more likely is that you want to be able to search the data store and find some piece of data you want. In this case, we are going to search the database for an artist and print out any songs of their's.  

So first, we need to get the inputed artist and find out if there are any of his/her songs in the hash.  That can be done with an **include?** method:

{% highlight irb linenos %}
irb(main):013:0> singer = gets.chomp
Led Zeppelin
=> "Led Zeppelin"
irb(main):014:0> playlist.include?(singer)
=> true
{% endhighlight %}

So we know that the singer has a song in our playlist.  How do we do that?  Well, we can create a hash that only has the artist's songs and then print those:  

{% highlight irb linenos %}
irb(main):034:0> if playlist.include?(singer) 
irb(main):035:1> artist_list = playlist.select {|key,value| key == singer }
irb(main):036:1> artist_list.each {|key,value| puts "#{key}: #{value}" }
irb(main):037:1> else
irb(main):038:1* puts "Nothing found."
irb(main):039:1> end
{% endhighlight %}

And it works:

{% highlight irb linenos %}
Led Zeppelin: Kashmir
=> {"Led Zeppelin"=>"Kashmir"}
{% endhighlight %}

### _Why Do I Care?_

Hashes are a fundamental method of data storage in Ruby.  Hashes allow us to put data in a place where it can be easily retrieved.  

## Exercise

In the exercise above, where we created the playlist, the answer required at least six lines of code.  Can you make it shorter?  How many different ways do you have to do this?

## Happiness Checkpoint

Flag an instructor to verify.  Get ready to show the class your answer.  

## Project Guidelines

Create a hash directory for movies similar to IMDB.  Add as much or as little data as possible.  It should also be _partially_ searchable using user input.

## Solve

Start small.  

## Extensions

Add more search functionality along further parameters.

## Push Instructions

Create a new repo and push to that repo.

## Further Readings

* [Ruby Documentation for Hashes](http://ruby-doc.org/core-2.1.0/Hash.html)
* [Ruby Hashes](http://www.tutorialspoint.com/ruby/ruby_hashes.htm)
* [Hashes in Ruby](http://zetcode.com/lang/rubytutorial/hashes/)