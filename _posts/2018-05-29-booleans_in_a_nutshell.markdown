---
layout: post
title:      "BOOLEANS IN A NUTSHELL"
date:       2018-05-29 00:11:09 -0400
permalink:  booleans_in_a_nutshell
---


Whether we realize it or not, our lives are controlled by certain circumstances. We get hungry, we eat. We get tired, we sleep. Each of these actions are predicated on whether or not a certain condition is true for us. If we’re hungry, we eat. Unless we are not tired, we sleep. The conditions that are true or false for us control the flow of our daily lives.
	
The same is true for computer programs, except we control the flow. We can set specific conditions and tell our program to execute specific actions as a result. 
	
This works because of booleans. Booleans represent either true values, or false values. This is an essential concept to understand, because if we don’t understand how flow control works, we’ll never understand our programs. And if we don’t get to the point where we can take a problem, and think logically through the steps the program needs to take to reach the solution, our lives will be much harder.

The most basic tools we have in our programming arsenal to implement flow control are if, elsif (else if), and else statements, and the three logical operators && (and), || (or), and !(not). We can also utilize case statements, while and until loops, and many others, depending on the conditions we’re dealing with.
	
A perfect example of how booleans and conditional operators work is the classic FizzBuzz Problem. **Spoiler alert: the FizzBuzz code is below, so if you want to solve it yourself, stop reading and come back later.**

```
def fizzbuzz(int)
  if int % 3 == 0 && int % 5 == 0
    "FizzBuzz"
  elsif int % 3 == 0
    "Fizz"
  elsif int % 5 == 0
    "Buzz"
  end
end
```

	
This is a beautiful example of flow control. It can be read like this: *if it is true that an integer is divisible by three and five, return “FizzBuzz”. Else if the integer is divisible by three, return “Fizz”. Else if the integer is dvisible by 5, return “Buzz”.* (People are often confused about the double-equals in the if statement. Why is ```int % 3 == 0```? The modulo operator (%) divides and returns the remainder, so a divisibility check will need the return value of  ```int % 3``` to equal 0.
	
We need to get this kind of logic wired into our brains, so that we can think like our program thinks. That way, when we sit down to tackle a problem, we can start by what we want our program to do, and work our way back step by step until we have beautiful, elegant, functional code that makes us and our users happy.
	
Because, after all, that’s one of the greatest things about programming, that our software can make people happy.

There is so much more that could be said about control structures in Ruby. I hope this post will at least help you appreciate the beauty of conditional logic.

Happy coding!

	
**Lifehack**: The next time you need a bit of motivation, say, to get our of bed for an early morning coding session, try implementing some flow control in your life. Take a piece of paper and write something like, “if alarm goes off, get out of bed” and put it on your phone. You’d be surprised how motivational it can be. Code making the world a better place once again.
