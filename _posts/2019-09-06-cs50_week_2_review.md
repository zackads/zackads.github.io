---
title: "cs50 week 2: review"
date: 2019-09-06
categories:
  - Blog
tags:
  - cs50
  - c
header:
  teaser: /assets/images/expectedbehaviour.jpg
---

Another week of CS50 and another classic computer science problem solved. This time, the Caesar cipher: how to encrypt your top secret military messages by shifting each letter `x` times up/down the alphabet so the germanic hordes can't tell what you're up to, even if they could read.

<!--more-->

I didn't find this too mentally taxing once I'd grokked the use of the modulo (%) operator, but it took me a while to get there. My own rudimentary pen-and-paper based tests of expected vs actual behaviour were also eye-opening. It definitely helped to get the pen and paper out and do a mini-whiteboarding session with myself when I realised I was just hitting compile and hoping for the best.

This passed with 11/11 for working code and 1.0 for style on the second attempt. I had to Google the maths for using the modulo operator to iterate through `key_length` whilst also iterating through `argv[1]`. Key lessons were:

- As well as the loop within a loop, the maths of the modulo operator was the hardest part for me. This course is making me think of going for A-Level Maths as an extra curricular thing, bandwidth dependent.
- Writing the expected variable values for each loop iteration on a piece of paper and then checking them using the CS50 IDE's debugging tool really, really helped. If only I'd done this before submitting the first attempt!
- Same for testing. I tested with `abc` as the key and HELLO as the plaintext, as in the pset's problem description. I got this working and thought 'hey presto'. It was only after doing `submit50` (`check50` is not available for this pset) that I discovered my code didn't work for all other user inputs! Lesson from this was to plan and test extreme cases of user input thoroughly before submission.

Overrall a really interesting, intellectually challenging pset that has got me thinking about loops, arrays and functions in a different way.

## How I did it (eventually)

CS50 helpfully guides you through the steps of writing the parts of the code.

## Validate user input

I didn't find the validation of user input that challenging once I had the realisation (/remembered David's lecture...) that `argv[1][i]` is a character (`[i]`) within a string (`argv[1]`) within an array (`argv`). This builds on the validate user input part of mario.c.

## Error messages

I had the idea to define a global error message. In the lecture material David underlines the importance of not copying and pasting code, so if there were more than one reason for a `USAGE_ERROR` I could use the variable. Other error messages could be included here. Capitalised because it's a global variable.

## Rotate `plaintext` by k to get `ciphertext`

Here's where it got complicated for me. I think of myself as a numerative person, but this again tied me up in knots. The main sticking points were:

1.  **How to repeatedly work through the length of `key` for each character in `argv[1]`???** I worked through several versions of the final code below:

```c
 // Rotate plaintext by k to get ciphertext;
        int plaintext_length = strlen(plaintext);

        string ciphertext = plaintext;

        for (int i = 0, j = 0; i < plaintext_length; i++)
        {
            int k = shift(argv[1][j]);

            // If character is uppercase
            if (ciphertext[i] >= 65 && ciphertext[i] <= 90)
            {
                ciphertext[i] = (ciphertext[i] - 65 + k) % 26 + 65;
                j = (j + 1) % key_length; // This has to be inside the 'if' statement so that it does not operate for non-alpha characters
            }

            // If character is lowercase
            if (ciphertext[i] >= 97 && ciphertext[i] <= 122)
            {
                ciphertext[i] = (ciphertext[i] - 97 + k) % 26 + 97;
                j = (j + 1) % key_length;
            }
        }
```

It felt like I just couldn't get it right. I could iterate through `key` once OK, but getting that to go back to the first character just wouldn't work.

I played with having `j++` in the 'execute after' section of the `for()` line after `i++`. I tried to do two `for` loops: one outer for iterating through `ciphertext`, another for iterating through `key`. I played around a bit with mixing in `while` loops, didn't work.

## Debugging... properly

Remembering my lesson to myself from a previous pset, I abandoned the old trial and error approach. I knew what I wanted to get from my code, so I mapped out expected behaviour using pen and paper:

![Any old scrap paper will do!](/assets/images/expectedbehaviour.jpg)

Using the test plaintext and key from the CS50 marking scheme (Which you only get to see after your first submission), I then used the [CS50 IDE debugger](https://www.youtube.com/watch?v=VtkMZjvvKaU) to iterate through my loop and work out where the values of `i` and `k` were becoming what I didn't want them to be:

![Iterating through a loop and watching the variables change, until they do something you don't want them to do!](/assets/images/debugging1.png)

Using [Wolfram Alpha](https://www.wolframalpha.com) to plug actual numbers in to a formula with the modulo operator helped me work out what I expected to see.

With a bit of fiddling (and Googling the mathematics behind the modulo operator, thanks go to [Khan Academy](https://www.khanacademy.org/computing/computer-science/cryptography/ciphers/a/shift-cipher) on that one), I'd got it sort-of working.

A final tweak of putting `j = (j + 1) % key_length;` inside the `if` statements so that the key shift only advanced for alaphabetic characters (i.e. not spaces or symbols) and the job was done.

## Here's what I learned

Here's what I'm taking away from this problem:

- Methodologically debugging by mapping expected behaviour to actual behaviour and using a proper debugger == substantially better than bone headed trial and error.
- Proper testing to make sure the code works for all possible user inputs before submission is essential.
- Watch the CS50 shorts! They're actually full of new material and insights that David doesn't include in the main lectures.

Thanks for reading!

### Viginere solution

<script src="https://gist.github.com/zackads/5a35be961d98b1ca29bb2285e58e3972.js"></script>

### Caesar solution:

<script src="https://gist.github.com/zackads/4529878f5be2219a3359cf2f3f5fc1d4.js"></script>
