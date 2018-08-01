---
layout: post
title:      "TooHotToHandel"
date:       2018-07-22 01:19:04 -0400
permalink:  toohottohandel
---


Sometimes in life, you have to pause, take a step back, and appreciate the fact that you have accomplished something worthwhile. For me, today is one of those days. A few months ago, I had no idea what a programming language was. I had never heard of Ruby. I didn't know what a command line was, or what a text editor did ("um ... I guess it edits text?"). Concepts like recursion, iteration, truthy, and falsey were like a foreign language. Data structures like hashes and arrays were simply not a part of my daily life. Well ... that has certainly changed.

![](https://i.imgur.com/woj4NLd.gif)


Today I built an application that I never would have thought possible only a few months ago. Everybody meet my new baby: TooHotToHandel.

TooHotToHandel is a command line interface that scrapes the New York Times for the latest news and reviews in the world of classical music (get it ... TooHotTo*Handel*?) It was a challenging program to build, and I'm very happy with how it turned out.

One of the greatest things about building an application like this is the way in which starting from an empty file, and building a functioning program, step by step, solidifies in your mind the concepts you've learned but maybe haven't quite put together. Much like that super long run-on sentence I just wrote. Let me illustrate with a simple example, since I've been programming all day, and thus am now beat. Somebody bring me pizza and beer, please.

The primary function of my program is to scrape the New York Times website for classical music articles, and display them in the form of a numbered list on the user's command line. It displays number, title, and description, and allows the user to select an article and read it. I accomplished this by defining a ClassicalReview class, and saving new instances of ClassicalReview in a class variable(`@@all`) which I then iterated over using `#each` and puts-ed out the data in the form of a numbered list (shout-out to our old friend `#each_with_index`).

The particular use-case that I came up with involves the user simply entering a command to display the list of articles, selecting a specific article to read, and then re-entering the initial command to display the list again so as to be able to select yet more articles. When I tried this, however, my simple one to ten list would multiply. The second time around it would be an 11 to 21 list, and so on. This just wouldn't do.

The solution was blessedly simple. I remembered how in previous projects where we would create arrays and store them in class variables, we would generally have a method that cleared that array.

```
1. def self.destroy_all
2.   @@all.clear
3. end
```

Look familiar? The purpose of this method had never really dawned on me before, until I faced my iteration problem and thought, is it possible that I could create this method in my ClassicalReview class, call it after I iterate through my  array and display the articles, so that it clears the array and starts over again next time the command is entered?

```
1. reviews = TooHotToHandel::ClassicalReview.all
2. 
3.   reviews.each.with_index(1) do |review, index|
4.     puts "#{index} - #{review.title.blue}"
5.     puts ""
6.     puts "#{review.description}"
7.     puts ""
8.   end
9.     
10. view_content
11.     
12. TooHotToHandel::ClassicalReview.destroy_all
```

It was absolutely the solution I needed. This is only part of a larger method, but what this code does is assign all of the review instances to a reviews variable, iterates over them and outputs my numbered list. Then it calls a `#view_content` method which is responsible for allowing the user to select and view the text of a particular article, and then clears the array, so that next time this method is called, it starts with an empty array, which means that my list is numbered 1-10 every time. The simplest solution is usually the right one.

I was also able to make the program open a specific article in a web browser. The solution to that was also simple and very cool, but I'll save that for later.

Happy coding!

