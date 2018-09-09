---
layout: post
title:      "Ruby Method Spotlight: Slice"
date:       2018-08-24 22:28:19 -0400
permalink:  ruby_method_spotlight_slice
---



![sliced orange](https://i.imgur.com/r0i4Gu5.png)





Just a quick note before we begin: this post assumes a basic knowledge of Ruby data structures, since I can't really think of a reason why you would want to read about this otherwise. Specifically, you should know what arrays and strings are, and you should probably have some understanding of return value.

### WHAT DOES IT DO?

`#slice` is a method that operates on arrays, strings, and (since Ruby 2.5.0) hashes. We'll just focus on arrays for now, since the logic is basically the same regardless, but keep in mind that you can call `#slice` on strings and hashes as well. `#slice` allows you to cut into an array and select specific elements.

### HOW DOES IT WORK?

Let's say you have an array of fruits:

`fruit = ["apple", "banana", "orange", "grapefruit", "tomato"]`

You can call `#slice` on the array, pass it a specific index, and it will return the object at that index. Calling `fruit.slice` with an argument of `(2)` will return the string object `"orange"` because `"orange"` is at index 2 of the `fruit` array (note that array elements are indexed starting at 0, so `"apple"` is at index 0, `"banana"` is at index 1, etc). Let's drop into IRB and check it out:

<pre>
<code>
2.5.1 :001 > fruit = ["apple", "banana", "orange", "grapefruit", "tomato"]
 => ["apple", "banana", "orange", "grapefruit", "tomato"]
2.5.1 :002 > fruit.slice(2)
 => "orange"
</code>
</pre>

If you want the banana, the orange, and the grapefruit, you can call `#slice` with a _starting index_ and a _length of elements_ and it will return those objects in an array.

<pre>
<code>
2.5.1 :001 > fruit = ["apple", "banana", "orange", "grapefruit", "tomato"]
 => ["apple", "banana", "orange", "grapefruit", "tomato"]
2.5.1 :002 > fruit.slice(1,3)
 => ["banana", "orange", "grapefruit"]
</code>
</pre>

This selects all elements starting with index 1 and ending with index 3. 

Similarly, we can use a range:

<pre>
<code>
2.5.1 :002 > fruit.slice(1..3)
 => ["banana", "orange", "grapefruit"]
</code>
</pre>

Another way to utilize this method is to call the array, and then simply select the elements you want, like so:

`fruit[2]`, which returns
`=> "orange"`

This is useful if you need to work with specific parts of a specific element. If your baby really wants a "nana", for instance, not a "BAnana", you can select the `"banana"` at index 1 by calling `fruit[1]`, and chain `[2,5]` onto it, which will select the string object at index 1 of the array, and then select the letters at indices 2 through 5 of the string object itself. Like this:

<pre>
<code>
2.5.1 :001 > fruit = ["apple", "banana", "orange", "grapefruit", "tomato"]
 => ["apple", "banana", "orange", "grapefruit", "tomato"]
2.5.1 :002 > fruit[1][2,5]
 => "nana"
</code>
</pre>

I hope you're starting to see how powerful this method is. You can do so much with it, especially when you use it with regular expressions, or other methods.
With a chef knife you can take food and change it in so many ways, and the same goes for the `#slice` method, but without the risk of cutting yourself. Drop into IRB, play around for awhile, and see for yourself what it can do. Ruby is designed to make programmers happy, and so with Ruby,

![happiness is a piece of cake](https://thepracticaldev.s3.amazonaws.com/i/lombsqm6son61so6nf78.jpg)

`#slice` of cake?

A quick note on hashes: like I said above, you can use `#slice` on hashes, but only in the newest Ruby versions. You use it like so:

<pre>
<code>
2.5.1 :003 > basket = {fruit: "apples, bananas",  vegetables: "carrots, onions, celery", grains: "rice, cornmeal, quinoa"}
 => {:fruit=>"apples, bananas", :vegetables=>"carrots, onions, celery", :grains=>"rice, cornmeal, quinoa"}
2.5.1 :004 > basket.slice(:vegetables)
 => {:vegetables=>"carrots, onions, celery"}
2.5.1 :005 > basket.slice(:vegetables, :grains)
 => {:vegetables=>"carrots, onions, celery", :grains=>"rice, cornmeal, quinoa"}
</code>
</pre>

For more on `#slice`, see the [ruby docs](https://ruby-doc.org/core-2.2.0/Array.html#method-i-slice), particularly look at concepts we didn't cover, like what situations cause `#slice` to return `[]` or `nil`, and what `#slice!` does.

For more on using `#slice` with strings, click [here](https://ruby-doc.org/core-2.2.0/String.html#method-i-slice)

For more on using `#slice` with hashes, click [here](https://docs.ruby-lang.org/en/2.5.0/Hash.html#method-i-slice)

If you have any questions or comments, just drop me an email.

Until next time, happy coding!
