---
layout: post
title:      "I Never Thought I Could Do This, But I Just Built My First Web App!"
date:       2018-11-21 23:14:07 -0500
permalink:  i_never_thought_i_could_do_this_but_i_just_built_my_first_web_app
---


It was almost a year ago when I created an `index.html` file in my Atom editor, typed `"Hello, World!"` in it, fired up *httpserver*, and saw it rendered in my browser for the first time. From that moment until today, I've been spending my time learning Ruby, SQL, HTML, CSS, and JavaScript. I've failed more often than I've succeeded, but I've been happier than I've ever been. And, anyway, today makes up for those past failures, because (thanks to them) I just finished building my first full web app.

### CONCEPT

When I was trying to figure out what to build, I took to heart the wise words of Ben Greenberg who told me once to keep it simple, especially when building something for the first time. "Your goal is to learn," he said, "not impress; besides, simple projects done well are impressive for someone at your level."

Given that, I knew I only wanted my app to have a has_many/belongs_to relationship, nothing more. Two models, no join table, no problems. That meant that I would have a User model and something that belongs to User. So I thought a wine journal would lend itself particularly well to this. User `has_many` wines, and Wine `belongs_to` User. The user would input information about wines they like and store them for future reference. It was perfect!

However, I had a hard time getting excited about the idea, despite my commitment to keep it simple. The idea kept popping into my head to allow all users to view every wine entry, not just their own, and before long I had this concept of a wine-centric social media platform in my head. Once I had named it Vino, there was no turning back.


### DAY ONE: TESTS

I knew I wanted to build Vino in a test-driven way, which of course meant I would need to write tests first. The problem with that was I didn't know how to write tests. But I knew how to read tests, and I figured now was as good a time as any to learn how to write them.

I started by mapping out the basic structure of my project. I took out a piece of paper, scribbled out the seven RESTful routes, their corresponding views and what each would contain, and then I had a basic idea of how a user would interact with Vino from log in to log out.

As a former chef, I'm used to learning from people who have come before me. A chef, especially in the early stages of development, researches and uses recipes that they alter to fit their needs. With practice, they start to rely on the recipe less and less. This is similar to the way I decided to learn how to write tests. I searched through repos I had forked on GitHub until I found good examples of RSpec and Capybara tests. I copied them into my spec files, and went through them line by line, rewriting them to suit my expectations for the application. In the end, I had something like 67 tests in my test suite. They consisted of tests for both models, verifying they had the attributes I wanted them to, and the rest were application controller tests, covering everything from a user being able to log in, to not being able to hack a URL and modify another user's data. Writing the tests was a whole day's work, but I gained in-depth knowledge of how tests work and how to write them, and it made building Vino a much more efficient process.


### DAY TWO TO DAY THREE: RELATIONSHIPS

Once the tests were written, I felt more confident about building, because I was used to running tests and debugging. I started by running the model specs, defining my classes, and writing migrations for the User model and Wine model. Once that was done, it was time to run the application controller specs and define my routes. I really enjoy databases, but when you start defining your routes, that's when you really get to dig in and figure out the logic. That's the stuff I live for when programming, so I really enjoyed debugging my way to a working app.

Pry was my best friend. Since I was building this using Sinatra, I also heavily utilized a gem called Tux, which, when you run `bundle exec tux` in your console, opens up an interactive environment that's pretty much like the sexy lovechild of Pry and IRB.

Before long, all my tests were passing, and my data was behaving as it should. My app was working!

Unfortunately, it was also ugly as sin.


### DAY FOUR TO DAY SEVEN: ADVENTURES IN HTML

I wanted Vino to look nice. It was really important to me that even though I had kept it as basic as I could, that it was something I could be proud of. Something I could point to and say "I did that" without embarrassment. I came pretty damn close to succeeding.

My design skills are limited, and I still wanted to keep the app simple. So rather than writing all my HTML and CSS from scratch, I decided to Bootstrap it. This was advantageous for several reasons. It meant first of all that I could use a bare-bones Bootstrap template (I didn't use a theme), and write a ton of custom HTML and CSS without necessarily needing to worry about things like clearfix. All the pieces would just fit together nicely, as long as I paid attention to the grid and didn't screw up the size of my rows and columns. It meant I didn't have to worry about making the app responsive because it would be automatically. It also meant that I could give Vino some nice features using Bootstrap's javascripts that I normally wouldn't try to incorporate myself at this stage in my learning. For instance, I used a lot of modals for different features, and I could code those out in HTML, style them in CSS, and they would work.

To learn how to do this, I followed a tutorial on [w3schools.com](https://www.w3schools.com/) that walked me through adding BootstrapCDN scripts and building out a basic grid for a social media-style website. I altered the grid somewhat to suit my needs, and started styling. I thought it would be fun to make it look like Facebook, so I wrote the CSS to make it happen, Googling around whenever I ran into an issue.

![Peter Griffin frustrated](https://media.giphy.com/media/5pxnxdzdZfXFK/giphy.gif)

It may sound easy, but my first attempt was a miserable failure. Bugs were popping up like crazy as I tried to do things like create cards for each wine entry, and whenever I fixed one bug, another would pop up someplace else. It was like the worst game of Whack-A-Mole I had ever played. I was getting so far down the rabbit hole with my changes, I knew I needed to start over. So I ran `git checkout`, started a new branch, and began rebuilding the HTML. After a day or two of work, I had a layout that I liked, and that functioned properly.

`git checkout master`

`git merge revised-layout`

When I was as satisfied as I could be with every little detail, I started refactoring the code. I tried to make it as DRY as I could as I started cutting out lines of code that served a purpose in the beginning, but were unnecessary in the finished product. I tried hard not to repeat myself more than necessary. When I was building, all the HTML and CSS for each view was together in each `.erb` file. I moved all the CSS to a stylesheet and as much repeated HTML as I could to a layout. It could definitely be more DRY, but I did as much as my lack of experience would allow. With a sigh of relief, I arrived at the moment when I couldn't think of anything else I needed to do. At least for the time being.

`git add .`

`git commit -m "done."`

`git push`

With a smile, I opened a bottle of wine, poured myself a glass, and sat back ...

... then looked at the label, fired up `shotgun`, logged in, and put it in my app.


### NEXT STEPS

I'd like to add features like comments which would be a good way to incorporate a many to many, or a has_many through relationship. I would like stricter authentication, flash messages, log in with Facebook OAuth, the list goes on. The next thing I want to do is build a Rails app, so I may rebuild Vino in Rails and add these features.

Programming can sometimes be so frustrating I think about doing something else. And then I build something and remember how much I love it. I hope I always find a way to fall back in love with programming.

If you want, you can check out the [GitHub repo](https://github.com/JMSchuurmans/vino).
