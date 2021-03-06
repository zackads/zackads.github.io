---
title: "Brian Harvey's CS61A course: getting OOP Scheme programs working in 2021"
date: 2021-03-06
categories:
  - blog
tags:
  - learning
header:
  teaser: /assets/images/advent_of_code.png
---

I've been working through Brian Harvey's CS61A course, as recommended by [teachyourselfcs.com](teachyourselfcs.com). It's mind-blowing, but it's also almost ten years old now and uses a [variant of Scheme](https://people.eecs.berkeley.edu/~bh/61a-pages/Scheme/) last updated in 2008. Naturally, the macOS binaries are 32-bit and so don't work on anything more recent than Catalina. Even worse, the [object-oriented syntactic sugar file](https://inst.eecs.berkeley.edu/~cs61a/sp09/library/obj.scm) provided by the UCB faculty was written in the year 2000!

The workaround for getting programs and homework assignments running in weeks 1 - 6 is to use DrRacket with the `simply-scheme` and `berkeley` packages, guide [here](https://github.com/theurere/berkeley_cs61a_spring-2011_archive#getting-started).

The week 1 - 6 workaround is great for getting you through recursion, higher-order functions and generics, but grinds to a hault when you move on to object-oriented programming in week 7. Even when you load `obj.scm` from the lib files, `define-class` does not work:

```scheme
define-class: unbound identifier in: define-class
```

Follow the steps below to get the OOP working so you can completed homework assignments and projects from week 7 onwards.

## How to get UCB's object-oriented `define-class` etc. lib file working in 2021

Pre-requisites:

- [Docker](www.docker.com)
- A clean working directory with an OOP scheme file, e.g. `oop-homework.scm` and a copy of `obj.scm` from the [CS61A lib folder](https://inst.eecs.berkeley.edu/~cs61a/sp09/library/obj.scm).

Steps

1.  Pull the `stklos` Docker image:

```bash
$ docker pull stklos/stklos:1.60
```

2.  Execute your `oop-homework.scm` file using the containerised `stklos` environment:

```bash
docker run -v$(pwd):/home -ti stklos/stklos:1.40 stklos -f random-generator.scm
```

(In contrast to using DrRacket for previous weeks, you'll need to use `(print <expression>)` to see the console output of your programs.)
