---
layout: post
title:      "The Virtue of Laziness"
date:       2018-07-16 19:03:33 -0400
permalink:  the_virtue_of_laziness
---



![](http://www.paulagordon.com/shows/wall/wall-photo.jpg)

Larry Wall, the creator of the PERL language,  famously said that one of the three main virtues of a programmer is laziness. What he means by this is that a great programmer strives to avoid redundancy and wordiness, among other bad practices. It's the idea of putting in a little extra work now, to save energy later. When programming, you don't want to repeat yourself, and you want your code to be as concise as possible. This is a key element in writing clean code, which is code that is elegant, programmer-friendly (easy to change when needed), and easy to understand. We should be constantly asking ourselves how we can get our programs working with as few lines of code as possible.

A key to this is refactoring. It might seem like more work sometimes, but if you can get your code working properly, and then go back and revise it to a clearer, more concise form, it means less future hassle for you and anyone else who might be working with your code. It's an investment in future laziness.

Let's say you're working on a music library program that imports song files, then organizes, lists, and plays them. You have a Song class in which you are storing all song instances as an array in a class variable `@@all`. You want to iterate over that array, and output a numbered list of songs. You could do it like this:

```
1 |  Song.all.sort_by{ |song| song.name }.each.with_index(1) do |song, index| 
2 |    puts "#{index}. #{song.artist.name} - #{song.name} - #{song.genre.name}" 
3 |  end
```

This method could be refactored to one line.

```
1|  Song.all.sort_by{ |song| song.name }.each.with_index(1) { |song, index| puts "#{index}. #{song.artist.name} - #{song.name} - #{song.genre.name}" 
```

Not bad, but it could be even more concise. Consider:

```
1 |  Song.all.sort_by(&:name).each.with_index(1){ |song, index| puts "#{}.  #{} - #{} - #{} etc ...
```

It's a small change, but we've been able to refactor our code into a less wordy form, an example of the virtue of laziness in programming. Every change, even small ones, can count for a lot. Style is all about the details.

Also check out the three virtues of a great programmer [here.](http://threevirtues.com)

And next time: impatience.

