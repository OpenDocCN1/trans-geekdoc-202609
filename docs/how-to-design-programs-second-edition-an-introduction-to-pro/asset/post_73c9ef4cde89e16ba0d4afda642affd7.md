
```scheme
; constants
(define WIDTH 100)
(define HEIGHT 60)
(define MTSCN (empty-scene WIDTH HEIGHT))
🚀
(define ROCKET
🚀
(define ROCKET-CENTER-TO-TOP
 (- HEIGHT (/ (image-height ROCKET) 2)))
; functions
(define (picture-of-rocket.v5 h)
 (cond
  [(<= h ROCKET-CENTER-TO-TOP)
   (place-image ROCKET 50 h MTSCN)]
  [(> h ROCKET-CENTER-TO-TOP)
   (place-image ROCKET 50 ROCKET-CENTER-TO-TOP MTSCN)]))
```

## Figure 8: Landing a rocket (version 5)

Before you read on, ponder the following changes to your program:

- How would you change the program to create a 200-by-400 scene?
- How would you change the program so that it depicts the landing of a green UFO (unidentified flying object)? Drawing the UFO is easy:
  (overlay (circle 10 "solid" "green")
  (rectangle 40 4 "solid" "green"))
- How would you change the program so that the background is always blue?
- How would you change the program so that the rocket lands on a flat rock bed that is 10 pixels higher than the bottom of the scene? Don't forget to change the scenery, too.

Better than pondering is doing. It's the only way to learn. So don't let us stop you. Just do it.

**Magic Numbers** Take another look at picture-of-rocket.v5. Because we eliminated all repeated expressions, all but one number disappeared from this function definition. In the world of programming, these numbers are called _magic numbers_, and nobody likes them. Before you know it, you forget what role the number plays and what changes are legitimate. It is best to name such numbers in a definition.

Here we actually know that 50 is our choice for an x-coordinate for the rocket. Even though 50 doesn't look like much of an expression, it really is a repeated expression, too. Thus, we have two reasons to eliminate 50 from the function definition, and we leave it to you to do so.

## One More Definition

Recall that animate actually applies its functions to the number of clock ticks that have passed since it was first called. That is, the argument to picture-of-rocket isn't a height but a time. Our previous definitions of picture-of-rocket use the wrong name for the argument of the function; instead of h—short for height—it ought to use t for time:

```scheme
(define (picture-of-rocket t)
 (cond
  [(<= t ROCKET-CENTER-TO-TOP)
   (place-image ROCKET 50 t MTSCN)]
  [(> t ROCKET-CENTER-TO-TOP)
   (place-image ROCKET
    50 ROCKET-CENTER-TO-TOP
    MTSCN) ]))
```

And this small change to the definition immediately clarifies that this program uses time as if it were a distance. What a bad idea.

> Danger ahead! This section introduces one piece of knowledge from physics. If physics scares you, skip it on a first reading; programming doesn't require physics knowledge.

Even if you have never taken a physics course, you know that a time is not a distance. So somehow our program worked by accident. Don't worry, though; it is all easy to fix. All you need to know is a bit of rocket science, which people like us call physics.

Physics?! Well, perhaps you have already forgotten what you learned in that course. Or perhaps you have never taken a course on physics because you are way too young or gentle. No worries. This happens to the best programmers all the time because they need to help people with problems in music, economics, photography, nursing, and all kinds of other disciplines. Obviously, not even programmers know everything. So they look up what they need to know. Or they talk to the right kind of people. And if you talk to a physicist, you will find out that the distance traveled is proportional to the time:

$d = v \cdot t$

That is, if the velocity of an object is v, then the object travels d miles (or meters or pixels or whatever) in t seconds.

Of course, a teacher ought to show you a proper function definition:

$d(t) = v \cdot t$

because this tells everyone immediately that the computation of d depends on t and that v is a constant. A programmer goes even further and uses meaningful names for these one-letter abbreviations:

```scheme
(define v 3)
(define (distance t)
  (* v t))
```

This program fragment consists of two definitions: a function distance that computes the distance traveled by an object traveling at a constant velocity, and a constant v that describes the velocity.

You might wonder why v is 3 here. There is no special reason. We consider 3 pixels per clock tick a good velocity. You may not. Play with this number and see what happens with the animation.

Now we can fix picture-of-rocket again. Instead of comparing t with a height, the function can use (distance t) to calculate how far down the rocket is. The final program is displayed in figure 9. It consists of two function definitions: picture-of-rocket.v6 and distance. The remaining constant definitions make the function definitions readable and modifiable. As always, you can run this program with animate:

```scheme
> (animate picture-of-rocket.v6)
```

```scheme
; properties of the "world" and the descending rocket
(define WIDTH 100)
(define HEIGHT 60)
(define V 3)
(define X 50)

; graphical constants
(define MTSN (empty-scene WIDTH HEIGHT))

(define ROCKET )
(define ROCKET-CENTER-TO-TOP
 (- HEIGHT (/ (image-height ROCKET) 2)))

; functions
(define (picture-of-rocket.v6 t)
 (cond
  [(<= (distance t) ROCKET-CENTER-TO-TOP)
   (place-image ROCKET X (distance t) MTSN)]
  [(> (distance t) ROCKET-CENTER-TO-TOP)
   (place-image ROCKET X ROCKET-CENTER-TO-TOP MTSN)]))

(define (distance t)
 (* V t))
```

## Figure 9: Landing a rocket (version 6)

In comparison to the previous versions of picture-of-rocket, this one shows that a program may consist of several function definitions that refer to each other. Then again, even the first version used + and /—it’s just that you think of those as built into BSL.

As you become a true-blue programmer, you will find out that programs consist of many function definitions and many constant definitions. You will also see that functions refer to each other all the time. What you really need to practice is to organize them so that you can read them easily, even months after completion. After all, an older version of you—or someone else—will want to make changes to these programs; and if you cannot understand the program’s organization, you will have a difficult time with even the smallest task. Otherwise, you mostly know what there is to know.

## You Are a Programmer Now

The claim that you are a programmer may have come as a surprise to you at the end of the preceding section, but it is true. You know all the mechanics that there are to know about BSL. You know that programming uses the arithmetic of numbers, strings, images, and whatever other data your chosen programming languages support. You know that programs consist of function and constant definitions. You know, because we have told you, that in the end, it’s all about organizing these definitions properly. Last but not least, you know that DrRacket and the teachpacks support lots of other functions and that DrRacket’s HelpDesk explains what these functions do.

You might think that you still don’t know enough to write programs that react to keystrokes, mouse clicks, and so on. As it turns out, you do. In addition to the animate function, the 2htdp/universe library provides other functions that hook up your programs to the keyboard, the mouse, the clock, and other moving parts in your computer. Indeed, it even supports writing programs that connect your computer with anybody else’s computer around the world. So this isn’t really a problem.

In short, you have seen almost all the mechanics of putting together programs. If you read up on all the functions that are available, you can write programs that play interesting computer games, run simulations, or keep track of business accounts. The question is whether this really means you are a programmer. Are you?

Stop! Don’t turn the page yet. Think!

## Not!

When you look at the “programming” bookshelves in a random bookstore, you will see loads of books that promise to turn you into a programmer on the spot. Now that you have worked your way through some first examples, however, you probably realize that this cannot possibly happen.

Acquiring the mechanical skills of programming—learning to write expressions that the computer understands, getting to know which functions and libraries are available, and similar activities—isn’t helping you all that much with **real** programming. If it were, you could equally well learn a foreign language by memorizing a thousand words from the dictionary and a few rules from a grammar book.

Good programming is far more than the mechanics of acquiring a language. Most importantly, it is about keeping in mind that programmers create programs for other people to read them in the future. A good program reflects the problem statements and its important concepts. It comes with a concise self-description. Examples illustrate this description and relate it back to the problem. The examples make sure that the future reader knows why and how your code works. In short, good programming is about solving problems systematically and conveying the system within the code. Best of all, this approach to programming actually makes programming accessible to everyone—so it serves two masters at once.

The rest of this book is all about these things; very little of the book’s content is actually about the mechanics of DrRacket, BSL, or libraries. The book shows you how good programmers think about problems. And, you will even learn that this way of solving problems applies to other situations in life, such as the work of doctors, journalists, lawyers, and engineers.

Oh, and by the way, the rest of the book uses a tone that is more appropriate for a serious text than this Prologue. Enjoy!

**Note on What This Book Is Not About** Introductory books on programming tend to contain lots of material about the authors’ favorite application discipline: puzzles, mathematics, physics, music, and so on. Such material is natural because programming is obviously useful in all these areas, but it also distracts from the essential elements of programming. Hence, we have made every attempt to minimize the use of knowledge from other areas so that
