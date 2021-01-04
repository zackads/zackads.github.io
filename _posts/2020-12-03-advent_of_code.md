---
title: "Advent of Code 2020"
date: 2020-12-03
categories:
  - blog
tags:
  - learning
header:
  teaser: /assets/images/advent_of_code.png
---

This was my first year of [Advent of Code](https://www.adventofcode.com). Sucked in by the fun but achievable challenges of the first week, I made a commitment to a couple of people that I would achieve all 25 days this year. My solutions are on [GitHub](https://github.com/zackads/advent_of_code) (spoiler alert: there aren't 25 of them).

![My Advent of Code 2020 score](/assets/images/advent_of_code.png)

I didn't know it at the time, but this commitment was a bit ambitious: in 2019 101,009 people completed day 1 but only 3,112 finished day 25, suggesting a completion rate in the region of 3% [1].

[Mike Zamanksy](https://cestlaz.github.io/post/advent-2020-final-thoughts/), the computer science teacher and blogger whose posts I leaned on quite heavily towards the end, completed all 25 days with his 30 years of experience teaching CS. Mike's blog posts about his solutions show an understanding I can only aspire to, and 2020 is the first year _he_ has completed all 25 days. Thank you for sharing this fact with us Mike, it's definitely me feel better!

So: after being trapped in debugging hell for a couple of days on day 20's puzzle (and knowing that my eventual solution, if it came, would be neither elegant nor performant), I decided to call it a day.

What did I learn?

### Algorithms and data structures++

So I actually thought I was kind of good at algorithms and data structures. I'd read [Algorithms To Live By](https://www.waterstones.com/book/algorithms-to-live-by/brian-christian/tom-griffiths/9780007547999), had heard of merge sort and, bruh, I've got [5kyu on Code Wars](https://www.codewars.com/users/zackads).

How humbled I was by Advent of Code.

Here's a few new things I learned about algorithms and data structures:

- Graph algorithms: how much of the world can be reduced to a directed acyclic graph; depth-first and breadth-first traversal; adjacency lists. I spent 2020 cycling around the countryside and job hunting, so AoC's graph/network problems really resonated with me.
- Set operations. I used iteration for a lot of the puzzles where I later learned I could have succinctly/performantly/elegantly used [set operations](<https://en.wikipedia.org/wiki/Set_(mathematics)>). More to learn here before reaching for a `for` loop.
- Space and time complexity. For some time I've subscribed to the view that "premature optimization is the root of all evil". I still think it is, but Advent of Code structured many of its problems in such a way that solutions in exponential time simply wouldn't work without a supercomputer. I think in the past I'd leaned a little too heavily on this view on premature optimization as an excuse not to learn algorithms in depth, perhaps because it's easier to iterate over an array many times than it is to think about the problem on a mathematical level. More to work on here.

### Domain-driven design

Writing solution code using the language of the problem domain. I've been exposed to a little [Domain Driven Design](https://en.wikipedia.org/wiki/Domain-driven_design) at work, though AoC with its explanation of the problem in real-life terminology (e.g. "ferry", "passenger", "passport) hammered home the value of this to me more than some katas I'd done in the past that used code-level language (e.g. "array", "string", "number").This really got me in the practice of thinking "yes, I'm writing a binary to decimal converter but what problem is this solving in the problem domain?".

### Test-driven development

Lulled into the false sense of security by the ease of early problems, I thought I'd give myself a break from writing tests (hey, it was coming up to Christmas...). This turned out to be short-sighted pretty quickly and I was back in the arms of my favourite JavaScript test framework before you could say "red, green, refactor".

I honestly don't think I'd have got to day 20 without the clarity and structure TDD brought me. I know what my new year's resolution is going to be now.

## Summary

Well, it was a hell of a ride. I'm looking at developing my core computer science knowledge now, as Advent of Code has really sparked in me a desire to learn more of the theory that underpins what I now do day-to-day.

After deciding to call it a day, I sought forgiveness from my wife for the sheer amount of time I'd spent on Advent of Code problems over Christmas. I was really encouraged for her to tell me that she's confident I'll be able to do all 25 days and spend less time on it next year after everything I'll learn in 2021! I hope she's right...

---

[1] [https://adventofcode.com/2019/stats](https://adventofcode.com/2019/stats). The puzzles are released daily regardless of whether or not the user has completed previous puzzles, so comparing day 1 and day 25 gives an approximate completion rate assuming _most_ people attempt to complete Advent of Code sequentially from days 1 to 25.
