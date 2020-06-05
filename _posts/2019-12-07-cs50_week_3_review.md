---
title: "cs50 week 3: review"
date: 2019-12-07
categories:
  - blog
tags:
  - cs50
  - c
  - data structures
  - debugging
  - memory management
---

Harold Wilson said a week is a long time in politics. Well, he may have been speaking about Harvard University's [CS50 course](https://www.edx.org/course/cs50s-introduction-to-computer-science). My last post, completing week 2's psets, was made on 10th October. Well, here is week 3's write-up, almost two months later! This developer is not optimised for performance...

(There is also a joke to be made about multitasking here. The offline world has been soaking up most of my time with painting and decorating.)

<!--more-->

## CS50 week 3: memory, data structures and debugging tools

CS50 week 3 (actually the fourth week in human numbers) takes the stabilisers away. Up until now, the very kind team at Harvard had been leeting us use the training header file `cs50.h`. This simplified things and protected students from a world where a string isn't a string but an array of characters. Oh no, wait, it's a pointer to the address of the first character in a string.

So if you have what you think is a `string` with value `zack`, what you actually have is a `char *` with value of the address in memory where the `char` z is stored. `zack` is actually `my_name[5]` (four letters + terminating `\0` character). Something like this:

![string arrays](/assets/images/strings_with_addresses.png)

_It's a string Jim, but not as we know it..._

This is important to remember because it's very easy to stray in to memory that isn't yours using arrays and pointers, causing segmentation faults. Really helpfully, the command line gives you no idea whatsoever where segmentation faults occur, leaving you to a lengthy debug process.

I thought I understood this during the lecture, but it's a whole different ball game when the stabilisers are off trying to work out where pointer and memory allocation bugs occur when you're developing. I still find this difficult and can't wait to move on to higher level languages where you don't have to juggle memory allocation and wrap your head around pointers.

![mexican standoff](/assets/images/pointers.jpg)

_A Mexican standoff of pointers._

I understand this difficulty in managing memory in C (and C++) -- to the point of C not being considered a ['memory safe' language](https://en.wikipedia.org/wiki/Memory_safety) - is one of the contributing factors in its fading from mainstream use in many applications.

Here are my solutions for the week 3 psets.

## pset3: whodunit

Objective: edit the RGB values of a bitmap to make some hidden text visible, revealing the culprit of a heinous crime.

<script src="https://gist.github.com/zackads/02182475a17acadac52526d2cc01e408.js"></script>

## pset3: resize less

Objective: resize a .bmp by a factor of `f`, where `f` is an int between 0 and 100.

_NB - I started off on the "more" version of this, which requires you to allow floating points in `f`, e.g. resize to 5.6 as well as 5 or 6. A bridge too far for me...._

<script src="https://gist.github.com/zackads/da550fc0b87263f6dbf651e2ad17dfec.js"></script>

## pset3: recover

Objective: use file operations to recover .jpgs from a corrupted raw file.

<script src="https://gist.github.com/zackads/1e3b0e9f8dcc68af81d4f3db8cdd9e6f.js"></script>
