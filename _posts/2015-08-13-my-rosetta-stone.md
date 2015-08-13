---
layout: post-hover
title: How to program the cosmos..
description: "..one api at a time (first blog from my coding adventures at Flatiron School)"
category: articles
tags: [cosmos, api, cli, flatironschool]
image:
  feature: "seahorse_nebula.jpg"
---

> If you want to build a ship teach people to yearn for the vast and endless sea
--Antoine de Saint-Exupery

### Some nature inspired curiosity

In our first day at [FlatironSchool](http://flatironschool.com) we were presented with this quote from Antoine de Saint-Exupery. The metaphor resonanted with me deeply as it crystalizes the way I approach every new project, challenge, learning and sharing opportunity.

This quote also made me think of Goldfish growth versus tank size. The growth of the fish is conditioned by the size of his tank size because of increasing ammonia levels.
![Goldfish in a bowl](/images/fish.jpg)
(ALERT: MYTH BUSTED) Goldfish don't grow only as large as their environment because their grow is determined by their genetic heritage however the size of their tank conditiones their growth indirectly due to the water quality. In other words the fish tanks have a [Garbage Collection](https://en.wikipedia.org/wiki/Garbage_collection_(computer_science)#Limited_environments) challenge just like the city of New-York and many of the programming languages:)

I take three major learnings from this nature instantiation of wisdom:
1.  beeing in an appropriate environment and changing the environment as we are evolving is key to our growth and development.
2. jumping to a larger bowl (as challenging as it may be at times) allows us to deal with our missconceptions waste and to constantly observe and assimilate new patterns.
3. people are very good at justifying their shortcommings (no Goldfish don't have a 3 seconds memory so you should really think twice before opting for that kitchen bowl).

### From fishtanks to spaceships :rocket:
So Goldfish are cool (and they never stop growing) but let's go back to Antoine de Saint Exubery who wrote a book that touched me as a child (and continues to do so today).
![Little Prince on Comet 67P/Churyumov–Gerasimenko](/images/Little_prince.png)

What beter motivation than dreaming about space for challenging our limits of understanding and curiosity?

A lot of my colleagues and our instructors have compared our learning curve to c a mountain climbing experience. For me it feels like going into space because I am learning how to get more and more perspective on things and climb the abstraction ladder.
![Abstraction gif](/images/abstraction.gif)

As a first "lightstone" in this journey to infinity and beyond I would like to invite you to Cosmos, the Ruby program I crafted together with my colleague [Drew](https://twitter.com/drewfromspace).  

As we both love space we decided to play with the Nasa Api for Apod (Nasa picture of the day). Our constraint was to make everything run in the command line and we had two days to do it (with some mediation workshop and lectures along the way).
![Nasa picture of the day last year for my birthday](/images/birthday_apod.jpg)

####This was our process:

1. Get the data from [Nasa Apod Api] (https://api.nasa.gov/api.html#apod)
2. Convert the image in ASCI [Ascii art gem] (https://rubygems.org/gems/asciiart)
3. Build the CLI program

###What we learned:

1. Run bash commands from ruby.We used two options System method and Backticks. There are actually six commands that enable you to run Shell commands in Ruby. More on that [here](http://tech.natemurray.com/2007/03/ruby-shell-commands.html)
2. Store api keys secretly by creating a .gitignore file.
3. Use meta-programming to set our own instance variables
4. Call a private method with and argument and a proc
5. Make our terminal talk to us
6. Search images by date
7. Make a gif in the terminal
8. Take pictures from the terminal with [ImageSnap package] (https://github.com/rharder/imagesnap)
9. Run commands in the backend
10. Rspec mock open-uri

### What we want to do next

- publish code as a gem (probably ready by the time you read this:)
- improve tests (of course)
- add option to see original picture in the browser
- include 8bit music for background
- create option to stop backend processes(music background) without interrupting the program.
- add download option for picture audio playback
- make a podcast with all our random generated terminal voice-over-ascii-picture.

### The slingshot of it all..

![Comet 67P/Churyumov–Gerasimenko from Rosetta](/images/comet.jpg)

Some of you space nerds might have noticed the "strange rock" the Little Prince was sitting on at the beginning of the post. It turns out it's a very special rock named Comet 67P/Churyumov–Gerasimenko and it took us 12 years to get there.. and we could only do that by using slingshot force.

[Example of Rosetta slingshot](https://youtu.be/ktrtvCvZb28 "Rosetta slingshot")

I believe programming just like space enables us to dream big and transform our dreams in reality. From a fish tank to the ocean the question remains of how we can best slingshot each other in our eternal quest for knowledge that is life.

![See you on the other side](/images/imagesnap_stef_ascii.png)
