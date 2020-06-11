---
title: "cs50: pset 7 (more Python, Flask, managing user input and responsive design)"
date: 2020-04-12
categories:
  - blog
tags:
  - cs50
  - learning
header:
  teaser: /assets/images/fuel_table.png
---

Part 2 of my summary of [CS50](https://online-learning.harvard.edu/course/cs50-introduction-computer-science) and problem sets 7, 8 and the final project. This is where it gets really cool. If you'd told me at the start I would be coding a database-driven stock trading app with user authentication at the end of this course I wouldn't have believed you.

It felt really gratifying to go from the core concepts of computer science in the early weeks to creating something I could actually show my friends at the end. But enough about my feelings, on to the problem sets!

<!--more-->

## pset7: similarities (Python in a web app: Flask)

`pset7: similarities` requires you to build out on the scaffolding the CS50 team provide you with by completing some helper functions and creating a web form. This will give you a web app that allows the user to compare two documents, highlighting similarities between them.

![The similarities user interface](/assets/images/similarities.png)

This is a gentle dipping of the toe into web frameworks. It's still vanilla HTML on the frontend for the form. The major design decisions about what backend functions to create, and what their parameters and return values will be, have already been made by CS50. The student is left to fill in a few `# TODO`s under already defined functions.

This snippet, a 'compare `a` with `b` and add to list' `for` loop I created as part of one of the scaffolded helper functions, made me chuckle in retrospect:

```python
# Iterate through a and b and identify common values
# (must be a more Pythonic way to do this?)
for line_a in a:
    for line_b in b:
        if line_a == line_b:
            common.append(line_a)
```

I hadn't discovered Uncle Bob's [thoughts on code comments](https://twitter.com/unclebobmartin/status/870311898545258497?s=20) at this point. There definitely is a more Pythonic way to do this in a list comprehension.

```python
common = [line_a for line_a in a if line_a in [line_b for line_b in b]]
```

Or even better, using Python's built in methods and the data type `set` (similar to a `list` in many ways, but containing only unique values).

```python
common = list(set(a).intersection(b))
```

Here, Python's built in `intersection()` method operates on the return value of `set(a)` with the parameter `b`, returning the mathematical intersection (common values) of `a` and `b`. The `list()` function simply turns the returned set into a list. Python is good like that.

There are three different ways of comparing two lists and deriving common values there. Which is the right one? It depends what you're optimising for. For absolute beginners, the nested `for` loops might be easiest to read, comprehend and maintain. There's something pleasing about the logical progression, the indents, the almost natural language.

The list comprehension has this too, if a little bit more confused. You have to _get_ list comprehensions to be able to grok the second example.

Same with the third example, using Python's `set` data type and `intersection()` method. This requires a little depth of knowledge about Python's in-built tools, but there's no reason to suppose that if you're in a professional dev team working on a Python code base that anyone wouldn't know this syntax.

And you wouldn't to err on the side of basic, verbose code (and not take advantage of built in methods/classes) for the benefit of the lowest common denominator, would you? I'm undecided on which is the better option in which scenario.

Back to code commenting.

![Uncle Bob](/assets/images/uncle_bob.jpg)
_Uncle Bob: Godfather of Clean Code_

[Uncle Bob](https://www.amazon.co.uk/Clean-Code-Handbook-Software-Craftsmanship/dp/0132350882/) doesn't like code that doesn't express itself, but as a learning tool I found commenting my code very useful. It helped me code deliberately by setting out what I wanted to achieve with the next few lines. Looking back now, clearly my nested `for` loop iterated through `a` and `b` and appended a value to `common` if that value was in both lists. But writing out what I wanted to achieve first kept me focussed ([selection and maintenance of the aim](/blog/perfect_enemy_of_good/)).

Looking back, commenting every few lines of code isn't something I'd do now. Putting a high quality docstring into a function that describes its parameters and return values is something I'm in the habit of doing instead. But when I learn a new concept or use a new library I will be using comments to help me along the way.

## pset7: survey (user input -> HTML form -> csv on the server -> displaying on an HTML table

I really enjoyed this. I didn't think I would. I don't excel at making things pretty, getting the colours right, styling them divs. But I liked making this web form that had to take user input, save it to a CSV and then display it back to the user using the [DataTables JQuery plugin](https://datatables.net/).

I think it's because I encounter such truly terrible user interfaces every. single. day. that having the opportunity to create my own allowed me to, in a small way, put my money where my mouth was. It _can_ be done better.

I chose to do a fuel order form. It had some carry over to something I was working on at work, so I had the data inputs already in my head ready to go.

Biggest thing I learned from this was responsiveness: making a website useable no matter what size screen the user accesses it from. This is huge - ginormous - as in [Q4 2019 52.6% of web traffic was to/from a mobile device](https://www.statista.com/statistics/277125/share-of-website-traffic-coming-from-mobile-devices/).

Best thing for making responsive websites? Bootstrap, grid, flexbox? All fantastic. But limited in utility unless you can test it from your laptop while developing. Step in browser dev tools!

![Browser dev tools: making a 13" Surface laptop look like an iPhone 6](/assets/images/fuel_request_form.png)

All the major ones have this. It was a revalation for me to be able to see what my website would look like on a phone whilst I was building it.

I can thoroughly recommend Firefox Developer Edition. Not because it's better than Chrome or Safari.

But because you get 'Developer Edition' in the title and a different colour logo:

![Firefox for Developers](/assets/images/firefox_developer_ed.png)

If that doesn't make any budding full-stack engineer feel warm and fuzzy then I don't know what will.

DataTables is also a really nice way of making a HTML form look nice and be much more useful to the user (searching, pagination). I haven't explored JQuery in too much depth, other than reading 'Is JQuery dead?' articles and listening to podcasts about how React/Vue/Angular etc. have 'finally killed JQuery'. But it seemed OK to me, especially for such a simple use case. Going down the React route via npm would have been overkill, I think.

This fuel order was submitted by my wife. She's from Mars.

![Image of the datatable showing existing fuel demands](/assets/images/fuel_table.png)

That's it for pset7. One more constrained problem set and then an open-ended final project of the student's choice to go.

Until next time...
