---
title: "Brian Harvey's CS61A course: getting OOP Scheme programs working in 2021"
date: 2021-03-06
categories:
  - blog
tags:
  - learning
header:
  teaser: /assets/images/sicp_cover.jpeg
---

I've been working through Brian Harvey's CS61A course, as recommended by [teachyourselfcs.com](teachyourselfcs.com). It's mind-blowing, but it's also almost ten years old now and uses a [variant of Scheme](https://people.eecs.berkeley.edu/~bh/61a-pages/Scheme/) last updated in 2008.

Naturally, the macOS binaries are 32-bit and so don't work on anything more recent than Catalina. Even worse, the [object-oriented syntactic sugar file](https://inst.eecs.berkeley.edu/~cs61a/sp09/library/obj.scm) provided by the UCB faculty was written in the year 2000!

The workaround for getting programs and homework assignments running in weeks 1 - 6 is to use DrRacket with the `simply-scheme` and `berkeley` packages, guide [here](https://github.com/theurere/berkeley_cs61a_spring-2011_archive#getting-started).

The week 1 - 6 workaround is great for getting you through recursion, higher-order functions and generics, but grinds to a hault when you move on to object-oriented programming in week 7. Even when you load `obj.scm` from the lib files, `define-class` does not work:

```scheme
define-class: unbound identifier in: define-class
```

Follow the steps below to get the OOP working so you can complete homework assignments and projects from week 7 onwards.

## How to get UCB's object-oriented `define-class` etc. lib file working in 2021

I'll use a basic example `oop-homework.scm` file taken from the course lecture notes:

```scheme
(load "obj.scm")

(define-class (complex real-part imag-part)
 (method (magnitude)
         (sqrt (+ (* real-part real-part)
                  (* imag-part imag-part))))
 (method (angle)
         (atan (/ imag-part real-part))) )

(define c (instantiate complex 3 4))
(print (ask c 'magnitude))
(print (ask c 'real-part))
```

Pre-requisites:

- [Docker](www.docker.com)
- A clean working directory with the Scheme file (I'm using `oop-homework.scm` above) and a copy of `obj.scm` from the [CS61A lib folder](https://inst.eecs.berkeley.edu/~cs61a/sp09/library/obj.scm).

Steps:

1.  Pull the `stklos` Docker image:

```bash
$ docker pull stklos/stklos:1.60
```

2.  Execute your `oop-homework.scm` file using the containerised `stklos` environment:

```bash
$ docker run -v$(pwd):/home -ti stklos/stklos:1.40 stklos -f oop-homework.scm
```

Three things to note:

- In contrast to using DrRacket for previous weeks, you'll need to use `(print <expression>)` to see the console output of your programs. If you don't, nothing will show on your screen.
- You no longer need `#lang racket` and `(require berkeley)` at the start of your `.scm` files.
- You _do_ need to `(load "obj.scm")` to access the OOP syntactic sugar (`define-class` et al.).

Happy Scheming!

--- EDIT 13 March ---

Unfortunately, stklos doesn't seem to be able to get round some of the dependencies the Spring 2011 version of CS61A has on STk. The version of `obj.scm` required for Project 3, the adventure game, includes a couple of extra methods that depend on STk modules. This `object?` procedure is the offender that's causing me headaches:

```scheme
; An object is a compound procedure with a single argument.
; (Really, an object is a dispatch procedure, but we can't look inside
; the definition to make sure it always returns a procedure or
; a NO-METHOD marker.)
; We use the STk-specific WITH-MODULE to make sure we get the built-in
; version of PROCEDURE-BODY (also an STkism), rather than an override.
(define (object? obj)
  (and (procedure? obj)
        (let ((lambda-exp ((with-module scheme procedure-body) obj)))
	 (and lambda-exp
	      (let ((args (cadr lambda-exp)))
		(and (list? args)
		     (= 1 (length args)) ))))))
```

Gives me:

```
**** Error while executing file "game.scm"
	 Where: in object?
	Reason: variable `Scheme' unbound

  - <<let/call>>
  - <<let/call>>
  - <<let/call>>
  - object?
  - ask
  - instantiate
  - %execute
  - #[closure 7f55aaf6feb0]
  - call-with-values
  - dynamic-wind
  - ...
Set shell variable STKLOS_FRAMES to set visible frames
EXIT
```

Various alternatives to `with-module scheme` (including `Scheme`, `STklos`, `stklos` etc.). Nothing's coming up on Google either. It looks like the passage of time has killed this one.

I'm sadly now going to skip the OOP goodness of Project 3. If you're reading this and feeling some FOMO at the prospect of not doing Project 3, try checking out the [similar project in the Python version of CS61A](https://inst.eecs.berkeley.edu/~cs61a/fa15/lab/lab06/). It might scratch that itch.

Have you got this working? Please do get in touch using the details on the sidebar.
