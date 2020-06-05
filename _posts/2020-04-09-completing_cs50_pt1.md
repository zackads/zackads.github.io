---
title: "cs50: weeks 3 - 6 (bitwise image manipulation, hashtables, html/css and PYTHON!)"
date: 2020-04-09
categories:
  - blog
tags:
  - cs50
  - learning
---

Wow, what a journey. CS50 complete and certificate issued! And, I am ashamed to say, not much in the ship's log past the fourth week. I've put together this post to summarise what I did on the remaining problem sets and reflect on cs50, a course that is easily in my top five learning experiences.

## The remaining problem sets

### pset3: recover (bitwise image manipulation)

Week 4 began with a great sendup of CSI and all those TV programmes that 'zoom' and 'enhance' images to catch the bad guy.

![Zoom, enhance](/assets/images/enhance.jpg)

pset4 required you to use C file operations to pull a set of JPEGs from a single corrupted file. This was a great intro to how images are stored and displayed digitally (clue: not like how CSI portrays).

I knew about how pixels work, but I didn't know that a JPEG is still a bitmap, even though it's not a .bmp. This problem gets you thinking about image manipulation on a bit-by-bit level, and ultimately requires you to create an algorithm to edit the image files line by line, looking for the bytes that signify the end of an image file and exporting each individual image programatically. Good fun.

### pset3: resize (more bitwise image manipulation)

Another bit-by-bit image manipulation problem, this time requiring you to create an algorithm to resize images by adding and subtracting pixels. Sounds simple, but what what about images that are 3 x 3 pixels and resizing by a floating number rather than an int? And how do you choose which pixels to delete when making an image smaller? Really good head-scratching stuff, also in C.

### pset4: speller (hash tables and tries)

This week was all about efficiency in searching, sorting and other algorithms. C can be a very fast language in execution, and the advanced memory management features can allow the developer to be very deliberate in the way memory is allocated. CS50 touched on optimising for x, a concept in computer science (and life!) that many decisions will be trade-offs between competing priorities.

This gave me a wry smile: it's the same in project management (time, cost or quality?) and in cycling (“Strong, light, cheap. Pick two." -- Keith Bontrager on the subject of bike components).

!["Strong, light, cheap.  Pick two." -- Keith Bontrager](/assets/images/stronglightcheap.jpg)
_"Strong, light, cheap. Pick two." -- Keith Bontrager\*_

Computer science teaches you ways to manage trade-offs and encourages you to confront them, which I love. Too often I've seen teams unwilling to talk rationally about trade-offs with their stakeholders, to the detriment of the project. But I degress.

Speller is a spell checker implemented in C using a hash table. Hash tables allow you to store and retrieve information quickly by breaking down large sets of information into buckets of smaller, mostly uniquely identified sets. Some more trade-offs here: the number of buckets and how likely the hash table is to generate conflicts (where different values end up in the same bucket) are design problems the engineer must tackle.

To solve the pset you must create your own hash table in C by taking a `dictionary.txt` of English words, hashing each line and storing in a suitable data structure. The user must then be able to input words to be spell-checked and your solution must then search through the hashtable looking for a match. It helps to be performant as this can take some time if not!

The more adventurous in this pset were able to solve this by using a [trie](https://en.wikipedia.org/wiki/Trie), another data structure. I was not that adventurous, but I certainly learned a lot about hash tables. And later learned to love the obfuscated complexity and elegant abstraction of the Python programming language...

### pset5: homepage (html and css)

Blinking in the harsh daylight, we emerge this week from the dungeon of C and cast off the yoke of abstract computer science concepts and bitwise operations and fell into the welcoming arms of HTML and CSS.

I jest, but this week did feel a little like that. HTML and CSS certainly felt very accessible after previous weeks, and being able to see the results immediately in a web browser (with very little debugging...) certainly improved the time-to-reward metric.

Homepage requires the student to submit a basic HTML and CSS homepage. This is a good intro to markup languages, if a little copy-and-pasty (if you want a navbar/footer or other repeatable features on your homepage, at this stage in the programme you're not given the tools to do it via automatic templating, for example). Good, simple, home-grown HTML and CSS like grandma used to make.

### pset6: bleep (python: file operations, string manipulation)

Oh my word, Python! Where have you been all my life? All the memory anxiety, segmentation faults, boilerplate code and endless debugging of C disappears and you're left with simple, elegent, almost human-like code that just does what it says it's going to do.

The way David Malan introduces you to Python in the 2-hour video lecture this week is bordering on vindictive. It's as if he's saying "Look, here's how easy we could have had you do all those problems we made you do in C. But we didn't. How do you feel about that?"

Bleep is a simple Python program to take user input and replace banned words (`darn`, `drat` and `fiddlesticks` feature on the list). I solved it in 40 lines of code with two `for` loops and a handfull of `if/else` statements. By jove that was too easy...

### pset6: mario, credit, caesar (rapid development with python)

And just like that, you're completing problems in Python that in the C weeks took you days of headscratching to the point of questioning your fitness to operate in modern society. Flaming nelly CS50 why didn't you tell us programming was like this beforehand?

This is very much deliberate: you really get an appreciation for the built-in methods that Python gives you. String operations are a dream. Want to convert between types? Python has a function for that. New data structures like dictionary and lists just do what they're supposed to do: no rolling your own hash table or linked list here.

Many introductory courses start off with basics (i.e. easy-to-understand) stuff first and either skip over things like memory allocation in a low-level language like C or come to them much later. Perhaps they choose to do this because they're reliant on eyeballs (advertising) or continued subscription (e.g. CodeAcademy) and so don't want to put students off if things are too challenging too early.

I think CS50 took the right approach here. With a brand like Harvard University you don't need to worry so much about discouraging people with the tough stuff. They signed up for a challenge, after all.

As a result of learning the 'hard way' first, I now feel like my comprehension of how software works is deeper than it would have been if I'd started off with an 'Intro to HTML' course or similar. From binary up, I feel in some ways like I 'get it' much better than I would otherwise have, whilst also appreciating just how much there is left to learn.

Thanks CS50. I think...

That's it for today. Check back soon for my reflections on the final problem sets of CS50 and where I'm going next.

---

\*incidentally, another of my favourite cycling truisms that translates well to software engineering is 'it doesn't get any easier, you just go faster'. A software engineer can be intellectually challenged just as much at the beginning trying to understand for vs while loops as 10 years in and working on AI. It doesn't get any easier, you just get better at it.
