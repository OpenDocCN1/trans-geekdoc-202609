![](resources/title_page.png)

![Thinking Functionally in PHP](resources/title_page.png)

## Thinking Functionally in PHP

 

#### Larry Garfield

 

This book is for sale at [http://leanpub.com/thinking-functionally-in-php](http://leanpub.com/thinking-functionally-in-php)

This version was published on 2021-04-25

![publisher's logo](resources/leanpub-logo.png)

\*   \*   \*   \*   \*

This is a [Leanpub](http://leanpub.com) book. Leanpub empowers authors and publishers with the Lean Publishing process. [Lean Publishing](http://leanpub.com/manifesto) is the act of publishing an in-progress ebook using lightweight tools and many iterations to get reader feedback, pivot until you have the right book and build traction once you do.

\*   \*   \*   \*   \*

© 2020 - 2021 Larry Garfield 

## Table of Contents

1.    
    1.  [Preface](#chap00.xhtml#leanpub-auto-preface)
    2.  [Introduction](#chap01.xhtml#leanpub-auto-introduction) 
        1.  [Functional vs. Procedural](#chap01.xhtml#leanpub-auto-functional-vs-procedural)
        2.  [Object-Oriented Code](#chap01.xhtml#leanpub-auto-object-oriented-code)
        3.  [Functional Style? Functional Language?](#chap01.xhtml#leanpub-auto-functional-style-functional-language)
        4.  [Type Systems](#chap01.xhtml#leanpub-auto-type-systems)
        5.  [What to Expect](#chap01.xhtml#leanpub-auto-what-to-expect)
2.  [Part One](#chap02.xhtml#leanpub-auto-part-one) 
    1.  [Pure Functions](#chap03.xhtml#leanpub-auto-pure-functions) 
        1.  [Define “Pure”](#chap03.xhtml#leanpub-auto-define-pure)
        2.  [Composing Functions](#chap03.xhtml#leanpub-auto-composing-functions)
        3.  [Binary Functions](#chap03.xhtml#leanpub-auto-binary-functions)
    2.  [First Class Functions](#chap04.xhtml#leanpub-auto-first-class-functions) 
        1.  [Anonymous Functions](#chap04.xhtml#leanpub-auto-anonymous-functions)
        2.  [Closure Objects](#chap04.xhtml#leanpub-auto-closure-objects)
        3.  [Short Lambdas](#chap04.xhtml#leanpub-auto-short-lambdas)
        4.  [Object Binding](#chap04.xhtml#leanpub-auto-object-binding)
    3.  [Memoization](#chap05.xhtml#leanpub-auto-memoization)
    4.  [Currying](#chap06.xhtml#leanpub-auto-currying)
    5.  [Mapping](#chap07.xhtml#leanpub-auto-mapping)
    6.  [Filter](#chap08.xhtml#leanpub-auto-filter)
    7.  [Reducing](#chap09.xhtml#leanpub-auto-reducing)
    8.  [Concatenation](#chap10.xhtml#leanpub-auto-concatenation)
    9.  [Recursion](#chap11.xhtml#leanpub-auto-recursion) 
        1.  [Recursion](#chap11.xhtml#leanpub-auto-recursion-1)
    10.  [Immutable Value Objects](#chap12.xhtml#leanpub-auto-immutable-value-objects) 
         1.  [What PHP Does](#chap12.xhtml#leanpub-auto-what-php-does)
         2.  [Making It Immutable](#chap12.xhtml#leanpub-auto-making-it-immutable)
         3.  [Objects, Functionally](#chap12.xhtml#leanpub-auto-objects-functionally)
         4.  [Evolvable Objects](#chap12.xhtml#leanpub-auto-evolvable-objects)
         5.  [Dependencies](#chap12.xhtml#leanpub-auto-dependencies)
         6.  [Entity Objects](#chap12.xhtml#leanpub-auto-entity-objects)
         7.  [Intra-Function Immutability](#chap12.xhtml#leanpub-auto-intra-function-immutability)
3.  [Part Two](#chap13.xhtml#leanpub-auto-part-two) 
    1.  [Category Theory](#chap14.xhtml#leanpub-auto-category-theory) 
        1.  [What Is a Category?](#chap14.xhtml#leanpub-auto-what-is-a-category)
        2.  [Objects](#chap14.xhtml#leanpub-auto-objects)
        3.  [Some Definitions](#chap14.xhtml#leanpub-auto-some-definitions)
        4.  [Structure](#chap14.xhtml#leanpub-auto-structure)
        5.  [Let’s Get Meta](#chap14.xhtml#leanpub-auto-lets-get-meta)
        6.  [Isomorphism](#chap14.xhtml#leanpub-auto-isomorphism)
        7.  [Monoids](#chap14.xhtml#leanpub-auto-monoids)
    2.  [Categories in Code](#chap15.xhtml#leanpub-auto-categories-in-code) 
        1.  [Converting Structure](#chap15.xhtml#leanpub-auto-converting-structure)
        2.  [Function Objects](#chap15.xhtml#leanpub-auto-function-objects)
    3.  [Fun With Functors](#chap16.xhtml#leanpub-auto-fun-with-functors) 
        1.  [Combining Functors](#chap16.xhtml#leanpub-auto-combining-functors)
        2.  [Monads in Programming](#chap16.xhtml#leanpub-auto-monads-in-programming)
        3.  [Anatomy of a PHP Monad](#chap16.xhtml#leanpub-auto-anatomy-of-a-php-monad)
    4.  [Algebraic Data Types](#chap17.xhtml#leanpub-auto-algebraic-data-types) 
        1.  [Products](#chap17.xhtml#leanpub-auto-products)
        2.  [Product Types in PHP](#chap17.xhtml#leanpub-auto-product-types-in-php)
        3.  [Coproducts](#chap17.xhtml#leanpub-auto-coproducts)
        4.  [Coproducts in PHP](#chap17.xhtml#leanpub-auto-coproducts-in-php)
4.  [Part Three](#chap18.xhtml#leanpub-auto-part-three) 
    1.  [Handling Null](#chap19.xhtml#leanpub-auto-handling-null) 
        1.  [The Problem](#chap19.xhtml#leanpub-auto-the-problem)
        2.  [The Example](#chap19.xhtml#leanpub-auto-the-example)
        3.  [The Category Theory Solution](#chap19.xhtml#leanpub-auto-the-category-theory-solution)
        4.  [The Programming Solution](#chap19.xhtml#leanpub-auto-the-programming-solution)
        5.  [An Alternate Implementation](#chap19.xhtml#leanpub-auto-an-alternate-implementation)
        6.  [A Note on Types](#chap19.xhtml#leanpub-auto-a-note-on-types)
    2.  [Either/Or and Error Handling](#chap20.xhtml#leanpub-auto-eitheror-and-error-handling) 
        1.  [The Problem](#chap20.xhtml#leanpub-auto-the-problem-1)
        2.  [The Example](#chap20.xhtml#leanpub-auto-the-example-1)
        3.  [The Category Theory Solution](#chap20.xhtml#leanpub-auto-the-category-theory-solution-1)
        4.  [The Programming Solution](#chap20.xhtml#leanpub-auto-the-programming-solution-1)
        5.  [Either Either?](#chap20.xhtml#leanpub-auto-either-either)
    3.  [Tracking Data](#chap21.xhtml#leanpub-auto-tracking-data) 
        1.  [The Problem](#chap21.xhtml#leanpub-auto-the-problem-2)
        2.  [The Example](#chap21.xhtml#leanpub-auto-the-example-2)
        3.  [The Category Theory Solution](#chap21.xhtml#leanpub-auto-the-category-theory-solution-2)
        4.  [The Programming Solution](#chap21.xhtml#leanpub-auto-the-programming-solution-2)
    4.  [Combining Monadic Behavior](#chap22.xhtml#leanpub-auto-combining-monadic-behavior) 
        1.  [The Example](#chap22.xhtml#leanpub-auto-the-example-3)
        2.  [The General Approach](#chap22.xhtml#leanpub-auto-the-general-approach)
        3.  [Binding](#chap22.xhtml#leanpub-auto-binding)
        4.  [The Lexers](#chap22.xhtml#leanpub-auto-the-lexers)
        5.  [Testing](#chap22.xhtml#leanpub-auto-testing)
        6.  [Analysis](#chap22.xhtml#leanpub-auto-analysis)
        7.  [Being Lazy](#chap22.xhtml#leanpub-auto-being-lazy)
5.  [Part Four](#chap23.xhtml#leanpub-auto-part-four) 
    1.  [Features of Functional Languages](#chap24.xhtml#leanpub-auto-features-of-functional-languages) 
        1.  [Auto-Currying](#chap24.xhtml#leanpub-auto-auto-currying)
        2.  [Recursion Optimization](#chap24.xhtml#leanpub-auto-recursion-optimization)
        3.  [Isomorphic Optimization](#chap24.xhtml#leanpub-auto-isomorphic-optimization)
        4.  [Function Composition](#chap24.xhtml#leanpub-auto-function-composition)
        5.  [Function Naming](#chap24.xhtml#leanpub-auto-function-naming)
        6.  [Generics](#chap24.xhtml#leanpub-auto-generics)
        7.  [Callable Types](#chap24.xhtml#leanpub-auto-callable-types)
        8.  [Comprehensions](#chap24.xhtml#leanpub-auto-comprehensions)
        9.  [Integrated Optionals](#chap24.xhtml#leanpub-auto-integrated-optionals)
        10.  [Optional Chaining](#chap24.xhtml#leanpub-auto-optional-chaining)
        11.  [A Native Bind Operator](#chap24.xhtml#leanpub-auto-a-native-bind-operator)
        12.  [Enumerated Types](#chap24.xhtml#leanpub-auto-enumerated-types)
    2.  [When to Go Functional](#chap25.xhtml#leanpub-auto-when-to-go-functional) 
        1.  [Avoid Global State](#chap25.xhtml#leanpub-auto-avoid-global-state)
        2.  [Make Pure Functions](#chap25.xhtml#leanpub-auto-make-pure-functions)
        3.  [Isolate IO](#chap25.xhtml#leanpub-auto-isolate-io)
        4.  [List Application](#chap25.xhtml#leanpub-auto-list-application)
        5.  [Embrace Value Objects](#chap25.xhtml#leanpub-auto-embrace-value-objects)
        6.  [Embrace Functions as Values](#chap25.xhtml#leanpub-auto-embrace-functions-as-values)
        7.  [Make Single-Method Callable Services](#chap25.xhtml#leanpub-auto-make-single-method-callable-services)
        8.  [Think in Terms of Pipelines and Data Flow](#chap25.xhtml#leanpub-auto-think-in-terms-of-pipelines-and-data-flow)
        9.  [Use Maybe and Either for Error Handling](#chap25.xhtml#leanpub-auto-use-maybe-and-either-for-error-handling)
        10.  [Don’t Overdo It](#chap25.xhtml#leanpub-auto-dont-overdo-it)
    3.  [Further Resources](#chap26.xhtml#leanpub-auto-further-resources) 
        1.  [Books](#chap26.xhtml#leanpub-auto-books)
        2.  [Videos](#chap26.xhtml#leanpub-auto-videos)
        3.  [Papers](#chap26.xhtml#leanpub-auto-papers)

## Guide

1.  [Begin Reading](#chap00.xhtml)

# Preface

Functional programming has been an interest of mine for years. That’s not to say I’ve been an expert in it, or that I’ve done much work in strictly functional languages, just that I’ve been interested in the topic.

Sadly, I’ve long found the available documentation and tutorials on the web to be lack-luster. Most of them either cover the very basics and then stop, or assume you’re already an expert in Haskell and so explain advanced topics in the most convoluted and Haskell-centric way possible. Neither of these did I find useful.

I have also found that the Curse of Monads seems to be true, as nearly every explanation I found about that mythical concept was obtuse, assumed you had three years of advanced mathematical training, or so dumbed-down as to be actively harmful to understanding.

> “Once you understand monads, you immediately become incapable of explaining them to anyone else.”
> 
> –Gilad Bracha

Combined with PHP’s overall clunky syntax for doing functional-esque code, I generally didn’t go further than “pure functions are your friend,” either in my own code or what I explained to others.

That is, until PHP 7.4.

PHP 7.4’s introduction of short lambdas is, as we’ll see in this book, a game-changer. While it doesn’t make anything new *possible*, it makes a lot of things suddenly *practical*. That makes all the difference, so I decided it was time to buckle down and really dig into functional programming. And what better way to learn than to force yourself to teach it to others?

I don’t mean that sarcastically; in fact, that’s been my history with functional programming from the beginning. I submitted a talk to a conference back in 2012 on functional programming before I really knew what I was doing, because that gave me a reason to learn it well enough to be able to explain it. I went on to give it 10 times. This book has had the same effect.

I knew when I started out that I was going to have to actually learn, finally, what all this category theory fuss was about. I did not expect it to be as hard as it was; apparently the Curse of Monads applies to most of category theory. A large part of the issue seems to be that no one can agree on how to call anything; it took reading a dozen tutorials in a half dozen languages to realize just how much the terminology varied, and just how much of a problem that causes for people trying to learn functional programming, category theory, or anything else.

I never would have thought that software engineering could be held up as an example of having consistent terminology, but I suppose all things are relative.

The central crux of this book is Part Two, in which I tackle the hard, academic, theoretical bits. It seems to be a trope that any time someone thinks they have understood monads they write an online tutorial about it, and I suppose I am no different. It is my hope that by writing that section, and rewriting it multiple times, while learning the material itself I was able to straddle the threshold between this world and the next (the one in which one does not understand monads, and the one in which one cannot explain them) long enough to capture a reasonable explanation of them. Should you find that I was successful, I would love to hear about it.

I am indebted to a number of people for their help in making this book happen.

*   Nash van Gool, who provided early validation that my early efforts were not entirely incomprehensible.
*   Nash and my colleague Chad Carlson, who served as beta testers for the first draft of the manuscript.
*   Shayna Steinberg, for reviewing the category theory section and validating it is comprehensible even for non-programmers/mathematicians.
*   Bartosz Milewski, whose book and website “[Category Theory for Programmers](https://bartoszmilewski.com/2014/10/28/category-theory-for-programmers-the-preface/)” is the best tome on the subject to date. He also was kind enough to answer my random validation questions on online forums, even though he had no idea why I was asking.
*   My editor, [Kara Ferguson](http://www.karaferguson.net/), without whom it’s quite possible there would be not a single comma in the right place in this entire book.
*   [Rebekah Simensen](https://ninjagrl.com/), who provided the delightful cover art you have probably already enjoyed. (Assuming you looked at the cover before opening this book, anyway, which seems likely.)

And of course to you, dear reader, as a book that is not read may as well not exist. It is my sincere hope that you find this volume educational, entertaining, and eye-opening. Or at least that it serves you as more than a monitor stand.

May your life be as pure as your code. I wish you well.

–Larry Garfield, @Crell

 begin mainmatter  

# Introduction

In recent years, functional programming has become increasingly popular as a concept. Even in “non-functional” programming languages, the concepts and practices of functional programming have become more mainstream.

Why is that? Are they actually useful, or is functional programming in a language other than Haskell just trying to fit a square peg into a round hole? What even is functional programming, and does it make sense in PHP?

This book aims to answer those questions. (Spoiler alert: The answer is yes.) While writing PHP as if it were Haskell, ML, or LISP is not going to produce a good result, the underlying principles behind functional programming offer many advantages, even in PHP. Other parts, however, do not, and that’s okay.

The aim of this book is not to convince you to write all PHP code in a strictly and rigidly functional fashion. Rather, the aim is to encourage you to approach problems from a functional mindset and apply the underlying principles of functional programming… most of the time. Many of them, in fact, you have no doubt encountered before in other contexts talking about “good code” under different names, such as the SOLID principles. That’s a good sign the concepts involved are a good idea.

## Functional vs. Procedural

There are many different paradigms for conceptualizing computation and programming, but the two oldest and most widely applicable are *procedural programming* and *functional programming*. Both were developed in the 1930s very close together, and have been shown to be equivalent; that is, there is no programming problem that can be solved in a procedural approach that cannot also be solved in a functional approach, and vice versa. One paradigm may be easier to write, or easier to read, or easier to think about, or more performant, or require fewer lines of code. Which one has the “edge” varies widely from one situation to another, but if it’s possible to solve in one, then it’s possible to solve in the other.

One could argue that since both are equally capable, a programmer needs to learn only one to solve any solvable problem. That would be a short-sighted view. By that logic, one would need to learn only a single Turing-complete language and be done with it, since all Turing-complete languages are, by definition, equally capable.

While it’s trite to fall back on cliches like “use the right tool for the job,” it’s a cliche because it’s true. But being able to determine the right tool for the job requires being at least competent in multiple tools. In the case of programming, that means being at least competent in multiple programming languages as well as multiple programming paradigms, if only to know when to *not* use a particular one.

Most programming resources, however, are geared toward a procedural mindset. That’s not surprising. It is the approach easiest to explain to a new developer, and at the end of the day, nearly all computer hardware in existence is procedural; anything else is simply syntactic sugar on top of assembly. That is unfortunate, though, as procedural is also the paradigm that scales least-well to large-scale systems, concurrency, and the ugly complex mess that is 21st-century computing.

What functional programming and procedural programming share, at least in their modern forms, is the division of programs into separate logical chunks that can be mixed and matched and reused. Even if the syntax is often similar or identical, however, functional programming goes a step further and makes those logical chunks first-class citizens that can be dynamically created, modified, passed around, even stored and reused. We’ll see concrete examples of that in Part One.

## Object-Oriented Code

The dominant programming paradigm today is neither functional nor procedural, but *object-oriented programming* (OOP)—at least, that’s the conventional wisdom. One issue with said conventional wisdom is OOP is a very loosey-goosey paradigm, with several sub-paradigms that actually get used. Far and away, the most common is what I term “Classic OOP,” as in, OOP that’s based in classes. C++, Java, C#, and PHP are all in this family, and with the introduction of explicit classes in ECMAScript 6 JavaScript sort of is.

There are other variants of OOP, however, some of which do not even include the quintessential “inheritance” concept. In practice, most OOP code in the wild is what I would term “procedural OOP,” that is, procedural thinking wrapped up in OOP style. That is not necessarily a bad thing; it is the dominant model today, so it must be doing something right. However, it is not fully message-centric OOP (a la Smalltalk). It also means there really is such a thing as “functional OOP,” or “object-functional” code.

Contrary to the Reddit consensus, OOP and functional programming are not adversaries that force you to choose One True Code Paradigm. Rather, we can and should leverage the lessons of both to produce the best solution to the problem.

## Functional Style? Functional Language?

One difficulty in understanding functional programming is that, much like object-oriented programming, there is no one clear definition of functional programming. On one level, it’s simply “programming with functions the way math does,” which is a nice and uninteresting definition. However, doing so quickly leads down a rabbit hole of category theory, monoids, endofunctors, generic type systems, pathological recursion, and other weird sounding words and phrases that are prone to turn off even the most receptive audience. In many cases it ends up looking like an unintentional [Mott-and-Bailey fallacy](https://rationalwiki.org/wiki/Motte_and_bailey), an [informal logical fallacy](https://en.wikipedia.org/wiki/List_of_fallacies#Informal_fallacies) where one argues two related points at the same time, one controversial and one not, and switches between the two depending on which is more advantageous in the moment.

There is, really, no universal definition of functional programming, nor of a functional programming language. If “functional programming language” means “a language in which one can do functional programming,” then nearly all modern languages are functional; this is not a helpful definition.

A better definition is to distinguish *functional-style programming* from a *functional language*.

*   *Functional-style programming* is a particular way of approaching a logical problem in code. It includes a couple of fairly simple core concepts, plus a huge array of concepts that naturally flow from those. Most of those are not all-or-nothing, making it possible to write “functional-ish” code in almost any modern language even if the syntax may end up a bit clunky.
*   A *functional language* is a language whose syntax and semantics are geared toward making functional-style programming easier and more natural, often (though not always) at the expense of other paradigms. Often those functional concepts are baked-in assumptions in the language, and if you are not aware of those assumptions, you’re likely to get bitten.
*   A *strictly functional language* is one whose syntax and semantics are geared toward writing in a functional style only, period. These languages go all the way down the rabbit hole and make thinking about a problem any other way frequently impossible. They also have a reputation for being impenetrable, precisely because they only support functional models.

PHP, in particular, is a language optimized for procedural OOP; it supports classic OOP, and that is the code style most widely used, but the single-threaded, shared-nothing architecture is intrinsically procedural. Since PHP 5.3, however, it has had syntactic support for functional-style programming. PHP 7.4’s introduction of short-lambdas further simplifies it far enough that functional-style code is now entirely viable.

That said, would I advocate writing 100% purely functional code in PHP? Not really. Many of functional code’s advantages do not actually apply in a single-threaded, shared-nothing environment, and others will work but collide with other limitations of the language to make them less friendly to work with.

## Type Systems

Type systems are a tricky topic in functional programming. On the one hand, type systems are entirely orthogonal and unrelated to functional programming. Some functional languages have extremely robust type systems (e.g., Haskell), while others have seemingly none at all (LISP). Yet, they’re often talked about in the context of functional programming. Why?

The answer lies in the previous observation that functional languages tend to have either no type system or a very robust one. Rarely have I seen a mediocre functional type system. While functional programming itself does not in any way require having an explicit type system, in practice functional code encourages and requires a very robust type system. A weak type system often cannot handle the complexity that a functional code base necessitates.

PHP is unusual in this case in that it has a relatively weak type system (compared to what languages like Rust or Haskell or even modern Java offer), but it’s all opt-in. As we’ll see, the result is that taking a fully functional approach will, in some cases, lose us some explicit typing ability. I don’t see that as a fatal problem, but rather as an indication of what sort of type system improvements PHP should prioritize in the future.

We’ll cover some typing concepts along the way, as necessary, but this is not primarily a book about typing.

## What to Expect

This book is divided into four parts:

*   In Part One, we will examine the fundamental principles of functional programming as a concept, using PHP as the example language. The results will not always be syntactically pretty, but that’s not the goal; understanding the value of the principles is, and we’ll use concrete PHP examples to go a little way down the rabbit hole.
*   In Part Two, we’ll step back and look at the theory that underpins much functional programming, specifically category theory. This is not a book on category theory, but a cursory understanding of the basics will greatly help to explain how functional programming and other formalisms really do make for more robust code.
*   In Part Three, we’ll bring the theory and practice together to demonstrate some more advanced techniques that make the theory concrete and make for more robust code at the same time.
*   In part Four, we’ll step back and consider the broader picture of what else functional programming could be, and where it should sit in your toolbox.

# Part One

# Pure Functions

The first and most crucial aspect of functional programming is the idea of a “pure function.” What makes a function pure? The fact that it’s an actual function and not something else.

If that seems circular, let’s back up a moment. One of the key challenges in discussing functional programming is software engineering and computer science are, in fact, two separate fields that have evolved in parallel with each other. They interact frequently, but not consistently. As a result, a great many concepts have a different name in software engineering than they do in computer science, and many others have the same word in both disciplines that mean different things. In order to establish a common vocabulary, therefore, let’s start at the very beginning.

In nearly all programming languages, there is an idea of a block of code that is reusable over and over again in multiple places, often with slight variation. The term for such a block is a *procedure*, or *sub-routine*. A procedure is any syntactically reusable block of code that can be referenced and, optionally, passed some parameters or arguments.

In mathematics, a *function* is a black box that is given inputs and reliably returns an output. How it does so is irrelevant; it could do some computation, or it could simply have a giant internal lookup table. However, the key term there is “reliably”; the same inputs will always produce the same outputs, guaranteed, and nothing else will change about the state of the universe except that a value is returned. Two inputs may result in the same output, but the same input can never, ever produce different output.

A function in mathematics is not a thing that happens but a *relationship* that defines the map from some input to some output.

In almost every mainstream modern language, the concept of a procedure and a function are folded together into a single concept termed “function.” In PHP-speak, both of the following are “functions”:

```
 1 function output(string $message): void
 2 {
 3     static $n = 1;
 4     global $preamble;
 5     echo "The {$n}th message is: {$preamble} {$message}". PHP_EOL;
 6     $n++;
 7 }
 8 
 9 function add(int $a, int $b): int
10 {
11     return $a + $b;
12 }
```

Both are procedures; however, only the second is a “function” as mathematicians would define it. The `output()` function takes a stealth input (a global variable), it produces a stealth output (it prints a message), and it has a different effect if called a second time with the same input (because it retains internal state via a static variable). All of those attributes violate what we expect of a “function” in the mathematical sense.

Of course, modern languages confuse things by using the term “function” willy nilly. Therefore, what mathematics calls a “function” programming instead calls a “pure function.”

## Define “Pure”

What makes a function pure? A procedure is a pure function if it follows two restrictions:

1.  It is *idempotent*. That is, the same explicit inputs are guaranteed to always produce the same outputs.
2.  It has no side-effects. That is, there is no effect on any value or data stream other than the return value being returned.

These rules are very simple and usually easy to achieve, but very powerful. By restricting ourselves in this way, we buy a number of assumptions.

1.  A pure function is incredibly easy to unit test. There is essentially no set up and no mocking necessary; just call it with known parameters and see if the result is what you expect.
2.  It has *referential transparency*. That is the fancy way of saying a function is equivalent to its return value. As long as `add()` is pure, then replacing all instances of `add(5, 5)` with `10` is guaranteed to not change the result of the program.
3.  Because we know that the same inputs produce the same output and because it’s referentially transparent, it is trivially easy to cache. Caching is, in essence, replacing subsequent function calls with a previously computed value.
4.  Conversely, while calling a pure function multiple times with the same input may be wasteful, it cannot be a source of bugs. That’s assuming you meant to call it with the same value multiple times; if not, the bug is in your parameters, not the function.

As we’ll see in the next chapter, those assumptions allow us to do a great deal more once we are dealing with higher-order functions. Stay tuned!

## Composing Functions

Another important attribute is that composing pure functions always produces a pure function, but calling an impure function from a pure function makes the pure function impure. That is:

```
 1 function add(int $a, int $b): int
 2 {
 3     return $a + $b;
 4 }
 5 
 6 function subtract(int $a, int $b): int
 7 {
 8     return $a - $b;
 9 }
10 
11 function compute(int $a, int $b, int $c): int
12 {
13     return subtract(add($a, $b), $c);
14 }
15 
16 function output(string $message): void
17 {
18     echo "The message is: {$message}". PHP_EOL;
19 }
20 
21 function run()
22 {
23     $val = compute(30, 10, 8);
24     output("The result is: $val");
25 }
```

`add()` and `subtract()` are pure functions, because they obey the two rules of pure functions. This means `compute()` is also a pure function, because it obeys the same rules and only calls other pure functions. However, `output()` is not a pure function because it has a side effect of producing output. `run()` calls both a pure and an impure function, and is thus impure. We cannot make any such assumptions about it.

Functional programming is built on pure functions. In strictly functional languages, writing a not-pure function is hard and requires extra syntax to remind you that you’re doing something dirty. PHP is not a strictly functional language, so it’s on us as developers to self-check and ensure our functions are pure whenever possible.

In practice, ensuring you have pure functions is straightforward:

1.  Avoid global values. Always. Period.
2.  Avoid static values in functions. Pretend they do not exist.
3.  Avoid passing or returning values by reference. In practice, there are extremely few use cases for that anyway in PHP, as PHP automatically supports copy-on-write making passing large, read-only parameters very memory efficient. This becomes a bit trickier when passing around objects, but there are ways to handle that which we will see later.
4.  If you need to do IO (read from a database, print to a screen, make an HTTP request, etc.), have a function (procedure) that does just that and nothing else, and returns its value. That function is impure, as is its caller, but other functions called by its caller need not be.

For example, this function reads a value from a database and then does some processing on it:

```
 1 function get_user(Connection $db, int $id): array
 2 {
 3     $result = $db->query("SELECT * FROM users WHERE uid=:uid", [':uid' => $id]);
 4     $row = $result->fetchRow();
 5 
 6     if ($row == 'false') {
 7         return [];
 8     }
 9     if ($row['expired'] == 1) {
10       return [];
11     }
12 
13     return $row;
14 }
```

Whereas a more robust approach would split the non-fetch functionality off to its own routine:

```
 1 function fetch_user(Connection $db, int $id): array
 2 {
 3     $result = $db->query("SELECT * FROM users WHERE uid=:uid", [':uid' => $id]);
 4     return $result->fetchRow();
 5 }
 6 
 7 function validate_result($row): bool {
 8     if ($row == false) {
 9         return false;
10     }
11     if ($row['expired'] == 1) {
12       return false;
13     }
14     return true;
15 }
16 
17 function get_user(int $id)
18 {
19     // ...
20     $user = fetch_user($db, $id);
21     if (validate_result($user)) {
22       return $user;
23     }
24     else {
25         // Some kind of error handling.
26     }
27 }
```

`validate_result()` is now a pure function, and thus far more predictable and easier to test.

Because most of functional programming is based on pure functions, for the rest of this book, whenever we talk about “functions” assume we mean pure functions unless explicitly stated otherwise.

## Binary Functions

A particular subset of functions are *binary functions*. Binary functions are functions which take two parameters of the same type and return an item of that type. That is, the following is a binary function:

```
1 function multiply(int $a, int $b): int
2 {
3     return $a * $b;
4 }
```

But this is not, because it does not return the same type:

```
1 function greater_than(int $a, int $b): bool
2 {
3     return $a > $b;
4 }
```

So far, that’s not all that interesting. However, there’s another subset of binary functions that are; specifically, binary functions can be *associative* and have an *identity element*.

A binary function is associative if the order of grouping doesn’t matter when chaining multiple calls together. Let’s look at multiplication again, this time with more traditional syntax.

```
1 $a * $b * $c * $d
```

Multiplying `$a` by `$b`, then by `$c`, then by `$d` produces the same result as multiplying `$a` by `$b`, `$c` by `$d`, and then those results together. Or, more visually:

```
1 $a * $b * $c * $d == ($a * $b) * ($c * $d)
```

An identity element is also known as a neutral element and is essentially the “no op” value. For multiplication over integers, the no-op value is 1. That is:

```
1 $a * 1 == $a
```

For every possible integer value of `$a`.

It turns out this combination of properties is rather useful in general. So useful that it has a fancy name: a *monoid*.

A “monoid” refers to a function that:

*   Is pure
*   Is a binary function (takes two parameters and returns one value, all of the same type)
*   Is associative
*   Has an identity value

More formally, we can say that multiplication is a monoid over integers. Stated more precisely, there is a monoid **<ℤ, multiply, 1>**: a set of values (integers), a binary operation (multiply), and an identity value (1). Multiplication may or may not be a monoid over other types of values, and for some types of values (e.g., turnips, employees, or shopping carts), it doesn’t even make sense.

While multiplication is fairly basic, the concept of a monoid applies to all sorts of types and operations. Consider list concatenation, for instance:

```
1 function concat(array $a, array $b): array {}
```

Is that a monoid? Let’s check the rules:

*   Is it pure? Check.
*   Is it binary? Check.
*   Is there an identity value? Yes, an empty array.
*   Is it associative?

We could go through a formal proof of associativity, or write tests to demonstrate it, but for now, let’s just logic it through. Given lists `[1, 3]`, `[5, 7]`, and `[9, 11]`, is the following true?

```
1 concat(concat([1, 3], [5, 7]), [9, 11])) == concat([1, 3], concat([5, 7], [9, 11]))
```

Yep, it is. Both give the same result, `[1, 3, 5, 7, 9, 11]`. For now we’ll go with that intuition and conclude it is associative (spoiler alert: It really is.), so we can conclude concatenation is a monoid over lists; or, more formally, **<lists, concat, \[\]>** is a monoid.

This concept will become more important later when we discuss value objects.

# First Class Functions

The second core attribute of functional programming is actually two closely related concepts: *first-class functions* and *higher-order functions*. In practice, the one tends to imply the other in almost any modern language, so we’ll consider them as a matched set.

Put simply, a first-class function is a function that can be assigned to a variable and passed around like any other variable, just as easily as an integer, string, or `Cat` object. A higher-order function is a function that either takes a function as a parameter or returns a function.

First-class/higher-order functions are a critical component of functional programming, as it requires, well, programming with functions as if they were any other value.

## Anonymous Functions

PHP has kinda-sorta had first-class functions for two decades, as you can specify a function name as a “callable” string. That doesn’t really qualify, frankly. Since PHP 5.3, however, PHP has supported anonymous functions that can be passed around as a normal function. They are implemented as an object under the hood, but the net result is “close enough for government work” to say PHP supports higher-order functions. PHP 7.4 introduced an even nicer syntax that makes many functional tricks vastly easier.

The basic anonymous function looks like this:

```
1 $factor = 6;
2 $multiply = function(int $a) use ($factor): int {
3     return $a * $factor;
4 };
5 print $multiply(9); // Prints 54
```

The variable `$multiply` is a function, just as the variable `$factor` is an integer. Specifically, it is a function that takes a single integer parameter and returns an integer. It also has that odd `use` clause in it. The `use` clause tells the function it can access `$factor` variable, even after it has gone out of scope. The function has an extra handle on it that keeps that variable existing for as long as `$multiply` exists, even if `$multiply` gets passed to some other function later. In computer science parlance, `$multiply` “closes over” `$factor`, that is, it is a *closure*. Strictly speaking, a closure is the process of a function incorporating part of its context into itself, but in common practice, “closure” and “anonymous function” get used more or less interchangeably (rightly or wrongly).

The more formal name for an anonymous function is a *lambda*. The name comes from “Lambda calculus”, which got its name because Alonzo Church, the inventor of it, got tired of writing the word “function” and so started using the greek letter lambda instead.

By default, all closures in PHP are by value—changing `$factor` after `$multiply` is created doesn’t change `$multiply`.

```
1 $factor = 6;
2 $multiply = function(int $a) use ($factor): int {
3     return $a * $factor;
4 };
5 $factor = 5
6 print $multiply(9); // Still prints 54
```

However, PHP also allows you to create a closure by reference, using an `&`:

```
1 $factor = 6;
2 $multiplyByRef = function(int $a) use (&$factor): int {
3     return $a * $factor;
4 };
5 $factor = 5
6 print $multiplyByRef(9); // Prints 45
```

Look carefully at the behavior of those two versions. Are they pure functions?

In the first case, yes. The behavior of `$multiply` depends exclusively on the value passed to it. However, in the second case where the closure is by reference, `$multiplyByRef`’s behavior is dependent on some external value, `$factor`, and thus subsequent calls to it may not produce the same value. So `$multiplyByRef` is **not** a pure function, and we lose all of our predictability about it.

We’ll find this is a nearly universal rule: A function that closes over a value by reference, or takes a parameter by reference, is not a pure function. It is merely a procedure, and thus its behavior is unpredictable.

## Closure Objects

If you have a hard time wrapping your head around a function-as-a-value, PHP has an alternate syntax that may be more familiar. Any object may implement a magic `__invoke()` method, which will get called if the object is invoked as if it were a function.

```
 1 class Multiply
 2 {
 3     private int $factor;
 4 
 5     public function __construct(int $factor)
 6     {
 7         $this->factor = $factor;
 8     }
 9 
10     public function __invoke(int $a): int
11     {
12         return $a * $this->factor;
13     }
14 }
15 
16 $factor = 6;
17 $multiplyObject = new Multiply($factor);
18 print $multiplyObject(9); //prints 54
```

The `Multiply` class does the exact same thing as the anonymous function above, just with more syntax. You can think of a closure as a single-method object where the variables closed over are passed to the constructor.

In fact, in PHP, you can do more than just think of it that way. In the engine, that is exactly what happens. The `$multiply` anonymous function gets converted into an object of class `\Closure`, the closed-over variables are assigned to private object properties, and it then passes around like any other object. You can even test that yourself; the following code will dutifully print “yes.”

```
1 $factor = 6;
2 $multiply = function(int $a) use ($factor): int {
3     return $a * $factor;
4 };
5 
6 print $multiply instanceof \Closure ? 'yes' : 'no';
```

The `Closure` class has a few other features, too. The interesting ones relate to how `$this` is handled. By default, if an anonymous function is created inside an object, it will implicitly close over `$this`, that is, the object inside which it is created. For example:

```
 1 class Table
 2 {
 3     private int $numForks = 3;
 4     private int $numSpoons = 4;
 5 
 6     public function cutleryCounter(): callable
 7     {
 8         return function() {
 9             return $this->numForks + $this->numSpoons;
10         };
11     }
12 }
13 
14 $t = new Table();
15 $counter = $t->cutleryCounter();
16 print $counter(); // prints 7
```

That is sometimes desirable, sometimes not. Once created, though, the value of `$this` can be swapped out:

```
1 $t2 = new Table();
2 $counter = $t->cutleryCounter();
3 $newCounter = \Closure::bind($counter, $t2);
4 // $newCounter's $this is now $t2, not $t.
```

In practice, this trick is rarely useful. However, let’s check: Does it make `$counter` impure?

It does! Whether rebound to a new object or not, the object to which it is bound could itself change; imagine if `Table` had methods that let you change the number of spoons, for instance. Then `$counter` cannot be relied upon to be idempotent (always return the same value).

Those side effects can be sneaky in a language that doesn’t help you avoid them.

There is one caveat to that observation, though; if Table can be shown to be a value object, then `$counter` again becomes a pure function. We’ll see more on value objects in a later chapter.

## Short Lambdas

PHP 7.4 introduced yet another syntax for anonymous functions, called variously “short lambdas” (because they’re shorter to write) or “arrow functions” (because they include the `=>` symbol, which looks like an arrow). Our previous multiplication example could now be written like this:

```
1 $factor = 6;
2 $multi = fn(int $a): int => $a * $factor;
3 print $multi(9); // Still prints 54
```

This code is exactly the same as the code we saw before, but shorter. Short lambdas have a function body that can be only a single expression, and the result of that expression is returned. They also support “auto-capture,” meaning you don’t need to specify the variables to close over explicitly. The engine can see we’re using `$factor` and fills in that information for us, always closing by value. Just like normal functions, they can take any number of parameters and be typed or untyped, and the return can be typed or untyped.

Short lambdas do not offer any more functionality over traditional anonymous functions. In fact, they are strictly less capable than the traditional version. What they offer is succinctness. The short lambda syntax makes it very easy to casually write a pure function as if it were any other literal value. What they really enable is the ability to “think in functions” without running into a wall of fugly syntax. That makes working in a functional way in PHP vastly easier than it ever was before, simply from a friction standpoint.

If you’re not used to short lambdas yet, some of the code in the rest of this book may take a little time to wrap your head around. I try to offer both a short and long version in many cases to help improve familiarity.

## Object Binding

By default, when you create a lambda within an object, the lambda gets auto-bound to the current object. `$this` is accessible and refers to the object the lambda is defined in. Occasionally that is useful; however, as with closures over references, it has the potential to make the function impure, unless the object is immutable. If the object goes out of scope, moreover, it may not get garbage collected if the closure is still alive.

```
 1 class Calendar
 2 {
 3     protected \DateTimeImmutable $startDate;
 4 
 5     public function getNextHoliday(int $days): callable
 6     {
 7         return function() use ($days) {
 8             return $this->startDate->add("$days days);
 9         }
10     }
11 }
```

To avoid automatic binding, you can declare the function `static`, which skips over the object binding.

Using static lambdas any time you’re inside an object is recommended; if you need some value off of the object from within the lambda, it’s straightforward to assign to a temporary variable instead:

```
 1 class Calendar
 2 {
 3     protected \DateTimeImmutable $startDate;
 4 
 5     public function getNextHoliday(int $days): callable
 6     {
 7         $start = $this->startDate;
 8         return static function() use ($days, $start) {
 9             return $start->add("$days days);
10         }
11     }
12 }
```

# Memoization

Now that we have a concept of first-class functions, and we have pure functions, what can we do with them? Quite a bit, in fact. One of the easiest next steps is to use them to help with performance.

Most PHP developers have at some point in their careers written code that looks something like this:

```
 1 function expensiveThing($key)
 2 {
 3     static $cache = [];
 4 
 5     if (!isset($cache[$key]) {
 6         // Do something really expensive to populate $cache[$key];
 7     }
 8 
 9     return $cache[$key];
10 }
```

It’s a fairly simple technique, but effective. Or, rather, mostly effective. It does aid performance, but it also makes testing substantially harder because later tests that hit that function get the cached version, not the original version. This includes tests of `expensiveThing()` itself. If the body of `expensiveThing()` is a pure function then that probably won’t hurt anything… but the most common behavior that gets wrapped there is some sort of IO call (to a database, file system, or web service), so that’s out the window. Moreover, it means `expensiveThing()` is itself not a pure function because it maintains internal state.

What we really want to do instead is separate the logic itself from the cache. A first pass at improvement may look like this:

```
 1 function expensiveThing($key)
 2 {
 3     static $cache = [];
 4 
 5     if (!isset($cache[$key])) {
 6         $cache[$key] = expensiveThingBody($key);
 7     }
 8 
 9     return $cache[$key];
10 }
11 
12 function expensiveThingBody($key)
13 {
14     $value = // some expensive thing;
15     return $value;
16 }
```

Now we’re able to test `expensiveThingBody()` in relative isolation without worrying about caching, but we also have two functions to keep track of, and all functions calling `expensiveThing()` still have the caching going on. That may or may not be a problem.

What if we could solve this problem generically, however? We know any pure function is idempotent, by definition, which means any pure function should be cacheable in this way. It may not always be useful, but it’s always possible.

As long as we’re okay with a function being a value, not a static string, a generic solution is fairly straightforward.

```
 1 function memoize(callable $fn): callable
 2 {
 3     return function(...$args) use ($fn) {
 4         static $cache = [];
 5         $key = serialize($args);
 6         if (!isset($cache[$key])) {
 7             $cache[$key] = $fn(...$args);
 8         }
 9         return $cache[$key];
10     };
11 }
```

The fancy computer-science name for this sort of caching is *memoization*, as in “write yourself a memo about what the return value was last time.” That “memo pad” is the `$cache` variable. `memoize()` takes a function as a parameter, and returns an anonymous function. Therefore, `memoize()` is a higher-order function.

The function it returns has the same cache logic we saw before, but for arbitrary arguments. It has a closure over the original function that was passed in, `$fn`, so it has it available to pass its arguments on to it when it’s called.

Let’s see it in action:

```
1 function multiply(int $a, int $b): int {
2     return $a * $b;
3 }
4 
5 $multiplier = memoize('multiply');
6 
7 print $multiplier(3, 5); // Prints 15
8 print $multiplier(4, 6); // Prints 24
9 print $multiplier(3, 5); // Prints 15
```

The output of each of those calls is the same as if we called `multiply()` directly. However, the second call to `$multiplier(3, 5)` won’t actually invoke `multiply()`. The result is already cached in the anonymous function that is `$multiplier`. This approach works for any pure function whose parameters are serializable.

What if we’re working with an impure function? Mathematically we cannot say it’s safe to cache; with an impure function, we’re outside of our ability to predict behavior reliably. However, we’ve still gained an advantage this way; resetting the cache is simply a matter of reassigning `$multiplier` to a new call to `memoize()`, or we could even have multiple cached versions with their own cache by calling `memoize()` multiple times.

Even if we’re dealing with a function that talks to the database, separating the caching logic out from the function itself in a flexible and generic way gives us a benefit in testability and debugability.

# Currying

The ability to work with functions as first-class values allows us to take advantage of another property of pure functions: Currying.

Despite the name, currying has nothing to do with Indian food (tasty as that may be). It is named after the logician Haskell Curry, after whom both the technique and the programming language are named. Currying is a process of converting a multi-parameter function into a single-parameter function, also fancily known as a “unary function.” In fact, almost any function can be converted into a single parameter function! (There are a few examples in mathematics of functions that cannot be curried, but the odds of running into them in routine PHP are quite small.)

To demonstrate, let’s consider this example:

```
1 function volume(float $x, float $y, float $z): float
2 {
3     return $x * $y * $z;
4 }
```

This mundane function computes the volume of a three-dimensional box. (We’ll assume the units match up for now.) It’s a pure function. What if we know the `x` value or want to compute a bunch of volumes, all with the same `x` value? We can create a new function that has `$x` preloaded, in a sense, like so:

```
1 $x = 5;
2 $volumeWithX = function(float $y, float $z) use ($x): float
3 {
4     return volume($x, $y, $z);
5 }
```

Or more succinctly:

```
1 $x = 5;
2 $volumeWithX = fn(float $y, float $z): float => volume($x, $y, $z);
```

Now we can call `$volumeWithX(4, 8)`, which will give us the exact same result, guaranteed, as calling `volume(5, 4, 8)`, because that’s exactly what happens. The value of `5` is saved into a new function, as a closure, to give us a 2 parameter function.

The same technique can be applied a second time to produce a single parameter function:

```
1 $volumeWithXY = fn(float $z): float => $volumeWithX(4, $z);
```

We can do the same thing over and over again for as many parameters as the function has, eventually producing a function that takes a single parameter.

Alternatively, a single function could self-curry if we wanted to get really fancy:

```
1 function curried_volume(float $x)
2 {
3     return function ($y) use ($x) {
4         return function ($z) use ($x, $y) {
5             return $x * $y * $z;
6         };
7     };
8 }
```

That’s kind of a mouthful, though, especially with all of that `use`-ing. Fortunately, short lambdas give us a much more condensed syntax that does the exact same thing:

```
1 function curried_volume(float $x)
2 {
3     return fn($y) => fn($z) => $x * $y * $z;
4 }
```

Both of those versions are identical; In both cases, `curried_volume()` takes one parameter (`$x`), then returns another function that takes one parameter (`$y`), which then returns a function that takes one parameter (`$z`), which then finally does the computation on all three collected inputs and returns a value. It returns the same value as the original `volume()` function.

```
1 volume(5, 4, 8) === curried_volume(5)(4)(8);
```

While in this case, we’ve shown currying one step at a time, there’s nothing which precludes closing over multiple parameters at once. In fact, it’s possible to write a generic “partial application” function like so:

```
1 function partial(callable $fn, ...$firstArgs): callable
2 {
3     return function(...$secondArgs) use ($firstArgs) {
4         return $fn(...[...$firstArgs, ..$secondArgs]);
5     };
6 }
```

Or, more succinctly:

```
1 function partial(callable $fn, ...$firstArgs): callable
2 {
3     return fn(...$secondArgs) => $fn(...[...$firstArgs, ..$secondArgs]);
4 }
```

Side note: If you’re confused by all of those ellipses, there are three different uses of them in the above function:

1.  In a function definition: `...$firstArgs` means “and all remaining parameters, as an array”. It replaces `func_get_args()`.
2.  In a function call: `$fn(...[])` means “take this array and spread it out as if I called the function with each parameter individually”; it replaces `call_user_func_array()`.
3.  Within a function literal: `[...$firstArgs, ...$secondArgs]` means “all of the values from `$firstArgs`, followed by all the values in `$secondArgs`, giving us one long flattened array.” It is a far simpler alternative to `array_merge()` and is new in PHP 7.4.

`partial()`, therefore, takes a function and an arbitrary number of parameters, as an array named `$firstArgs`. It returns a function that closes over that array and the callable and takes an arbitrary number of parameters `$secondArgs`, which in turn concatenates all of the parameters together and calls the original, saved function.

Now, using that new tool we can do this:

```
1 $partial_volume = partial('volume', 5, 4);
2 print $partial_volume(8);   // Prints 160
```

`partial()` as implemented here only allows pre-filling the values at the beginning of the parameter list. With short lambdas in PHP 7.4, I am not convinced it is even necessary as the following syntax does the same thing with less work, and it supports replacing any parameters we want, and lets us provide type information to boot:

```
1 $volumeForLength = fn(float $y): float => volume(5, $y, 8);
```

The astute reader may recall that when we introduced closures, we noted they were effectively the same thing as an object constructor but with less syntax. Currying takes that idea to its logical conclusion: A method call of an object can, in concept, be represented by a single function that takes all of the constructor arguments followed by its own arguments. The constructor simply creates a highly verbose curry of the method that is shared by the other methods.

Our last example could be rewritten with this equivalent, if horribly verbose, code:

```
 1 class YVolumizer
 2 {
 3     private float $x;
 4     private float $z;
 5 
 6     public function __construct(float $x, float $z)
 7     {
 8         $this->x = $x;
 9         $this->z = $z;
10     }
11 
12     public function __invoke(float $y): float
13     {
14         return $this->x * $y * $this->z;
15     }
16 }
17 
18 $volumizerForLength = new YVolumizer(5, 8);
19 print $volumizerForLength(4);
```

It should be obvious which one I’d rather spend time typing.

Currying is cool and all, but is it useful in practice aside from avoiding some typing? It turns out it is, because in practice nearly any function can be rewritten as a single-parameter function, almost trivially thanks to short lambdas. And single-parameter functions allow us to do some very cool things, as we’ll see in later sections.

The key takeaway from the chapter is this simple but incredibly powerful line:

```
1 $volumeForLength = fn(float $y): float => volume(5, $y, 8);
```

The ease with which new functions can be defined that turn an arbitrary pure function into a single-parameter function opens up a host of possibilities that haven’t existed in PHP before now, and in many ways form the basis for the rest of this book.

# Mapping

Beyond the basics of “doing things with functions,” functional programming tends to have a number of additional primitives that get used to structure an algorithm rather than typical procedural patterns. Most of them have to do with the handling of lists.

For example, in typical procedural code, it’s common to write a snippet like this:

```
 1 $list = [ /* Some set of data */]
 2 
 3 $result = [];
 4 foreach ($list as $value) {
 5     if ($value % 2 == 0) {
 6         $result[] = $value * 2;
 7     }
 8     else {
 9         $result[] = $value;
10     }
11 }
```

(Yes, this is a rather silly thing to do but bear with me. It’s just an example.)

In this very common procedural idiom, we’re iterating over one list to build another list. From a functional perspective, though, there are a couple of problems with it.

1.  The operation that is applied to each value is comingled with the act of iteration itself, meaning you cannot test it independently.
2.  That, in turn, makes it harder to read and understand. We’re iterating over the list, sure, but it’s not obvious at-a-glance that we’re applying the same logic to each item. It’s also not immediately obvious the computation applied to each element is independent of the other elements. (It is, but you have to actually read the code to find out.)
3.  It involves mutable variables. We’ll cover a bit later why functional programming frowns on that.

The more functional way to think about this task is to consider the iteration and operation separately. Instead of conceptualizing the problem as “I want to go through a list of integers one by one and do something with each value,” conceptualize it as “I have an operation that takes an integer and returns another integer, and I want to apply that operation to every value in this list.”

That naturally breaks down into two parts. First is the (pure) function we want to apply to a value. In our trivial example, that function looks like this:

```
 1 $operation = function(int $val): int {
 2     if ($value % 2) {
 3         // Odd numbers.
 4         return $value;
 5     }
 6     else {
 7         // Even numbers.
 8         return $value * 2;
 9     }
10 };
11 
12 // Or, more succinctly:
13 
14 $operation = fn(int $val): int => $value % 2 ? $value : $value * 2;
```

That function can now be examined, tested, and understood independently of the concept of lists.

The second part is applying that function to not one integer, but a list of integers. Such an action is called a *map*. (Actually, the word “map” gets reused slightly differently in a number of different functional languages, but this usage is reasonably universal, so let’s just roll with it.) You’ve most likely run across PHP’s `array_map()` function at some point in your life, which is exactly what we’re talking about. For practice, though, let’s go ahead and implement our own version:

```
1 function map(iterable $it, callable $fn): iterable
2 {
3     foreach ($it as $key => $val) {
4         yield $key => $fn($val, $key);
5     }
6 }
```

A few things to note in this version:

1.  It works on any `iterable`, not just an array. That is the number one complaint about PHP’s `array_map()` function, which shouldn’t be surprising since it predates PHP having iterables.
2.  It uses `yield` to produce a generator. That is, it operates lazily regardless of the size of the list.
3.  Because PHP `iterable`s can always be keyed, it also passes the key into the function being applied and preserves the keys when yielding values back. Strictly speaking, this is not a proper list map, but since PHP doesn’t have a true list structure (PHP arrays are hash maps or dictionaries), we’ll work with the language rather than against it.
4.  You may notice the parameter order is backward from `array_map()`, which takes the callable first. That’s because `array_map()` can act on multiple arrays at once, which is occasionally useful but requires putting the list of arrays at the end of the argument list. In practice, with a single list, it is easier to read if the more complex argument goes at the end, so I’ve put the list first and callable second.

In practice, this implementation is just abstracting out the `foreach()` loop from our previous code. (There are other implementations as we’ll see in a moment.) That still gets us a new, more functional-style way to write our previous code:

```
1 $operation = fn(int $val): int => $value % 2 ? $value : $value * 2;
2 $result = map($list, $operation);
3 
4 // Or simply:
5 $result = map($list, fn(int $val): int => $value % 2 ? $value : $value * 2);
```

That is “more functional,” but I would argue also objectively better in a few ways:

1.  If the operation is less trivial than this, we can test it on its own in isolation from the question of iteration.
2.  We can tell at-a-glance that each transformation is independent of the others because it’s a `map`. That’s intrinsic in the definition of a map.
3.  Because `int` involves a function boundary, we can enforce type checks in the applied operation. This is largely a PHP-specific benefit, but a benefit nonetheless.
4.  The null case is handled more gracefully. We don’t need to pre-create an empty `$result`, because if `$list` is empty, we get an empty `$result` naturally. Less edge case handling is always a benefit.
5.  It’s no help in PHP, but in a multi-threaded or multi-process language the independence of each transformation means they can be split across multiple threads, process, processors, or computers transparently, without changing the program logic at all, just changing the internal implementation of `map()`. Or it could be done manually by writing a new `map()`-like routine that uses a queue service of some kind, since the actual operation itself is now separately defined.

Finally, it allows code to be more declarative; the code describes what you want (a mapping of a function to a list) rather than how to do it (iterating and populating an array). The “how to do it” is still defined somewhere, but it’s separated out from the main flow of control of the application.

# Filter

Consider for a moment this procedural code:

```
1 foreach ($users as $user) {
2     if ($user->lastPaidDate() < date('-1 month')) {
3         send_email($user->email(), "Overdue bill", "Pay up, slacker!");
4     }
5 }
```

There are at least five different concerns, all being folded together.

1.  Iteration
2.  Determining if a user is overdue
3.  Filtering out users who are not overdue
4.  Defining an email to send
5.  Sending the email

It would be much nicer to separate all of those out instead, which makes the code both more readable and more testable.

We already have the tools to do most of those steps; we’re just missing the third step, filtering out users we shouldn’t be yelling at for being overdue. As with `map()`, PHP has a native array-only way to do that (`array_filter()`), but we’ll make our own `iterable` version for practice.

```
1 function filter(iterable $it, callable $ifTrue = null): iterable
2 {
3     $ifTrue ??= fn($val): bool => (bool)$val;
4     foreach ($it as $key => $value) {
5         if ($ifTrue($value)) {
6             yield $key => $value;
7         }
8     }
9 }
```

As with `map()`, our `filter()` function is lazy and works on any iterable, preserving keys. We’re also defining a default filter function just like `array_filter()` that skips values that are false-y. The `??=` operator is new in PHP 7.4 and is the “null assignment operator.” That is, it assigns the right side value to the variable on the left, if and only if the variable on the left is null. If it’s not null, then it does nothing.

Now, let’s rewrite our earlier procedural mess to separate out all of the concerns:

```
 1 $isUnpaid = fn(User $user): bool
 2     => $user->lastPaidDate() < date('-1 month');
 3 
 4 $mail = fn($email): void
 5     => send_email($email, "Overdue bill", "Pay up, slacker!");
 6 
 7 $mailUser = fn($user) => $mail($user->email());
 8 
 9 $unpaid = filter($users, $isUnpaid);
10 $action = map($unpaid, $mailUser);
11 
12 iterator_to_array($action);
```

Here, we’ve defined three utility functions upfront:

*   `$isUnpaid` determines if a user owes us money
*   `$mail` sends a message to an email address telling them to pay up
*   `$mailUser` extracts the email address from a user and calls `$mail` on it, further separating the concept of a user from the concept of “sending email.”

Those can be read, tested, or reused and recomposed all on their own. (And could just as easily be named functions or methods of an object if we were so inclined; any callable will do.) Next, we take our user list and filter out the ones we don’t care about, then apply the “send harassing email” function to the remaining list with `map()`.

One caveat, though, is that `map()` is a generator function, which means it… hasn’t actually done anything yet. We need to actually iterate it explicitly in order to make it do anything. There are a couple of ways of doing that, but the most straightforward is to call `iterator_to_array()` and discard the result. That iterates over every value in `$unpaid` and applies `$action` to it. `$unpaid` is also a generator, so it iterates through `$users` and returns just those that pass `$isUnpaid`.

So far, this may not seem like a great benefit, just a different way to get to the same result. It gets more beneficial when we want to compose more logic, or change selected parts. Consider if we also want to avoid sending emails to admins and to users flagged as partners, meaning they get stuff for free. In that case, we need only compose in some more primitives:

```
 1 $isAdmin = fn(User $user) $user): bool
 2     => $user->role == 'admin';
 3 
 4 $isPartner = function (User $user): bool {
 5     // Some horribly complex logic because
 6     // the concepts of partners was hacked
 7     // into your data model after the fact
 8     // because someone from sales promised it
 9     // to a particular partner and then
10     // told you about it after the fact...
11     // (Entirely fictional, of course...)
12 };
13 
14 $unpaid = filter($users, fn($user)
15     => !$isAdmin($user) && !$isPartner($user) && $isUnpaid);
```

And nothing else changes.

We’ll see some even nicer ways to structure this code in a later section when we start to cover logic flow.

# Reducing

Perhaps the most important functional operation, though, is “reducing.” Reducing is an operation that, from a procedural background, seems of extremely little use. PHP has an array reducing function, aptly named `array_reduce()`, but it’s not often used. When writing in a functional style, though, reduction comes up quite often, usually as an underlying implementation detail of other operations.

The basics of reducing are to take a list of values and “reduce” them to a single value by repeatedly applying a function to them. Unlike `map()`, `reduce()` is not intrinsically parallel because the value from one iteration is fed into the next.

As before, we can write our own `reduce()` implementation that works on any iterable:

```
1 function reduce(iterable $it, callable $fn, $collect = 0)
2 {
3     foreach ($it as $key => $val) {
4         $collect = $fn($collect, $val, $key);
5     }
6     return $collect;
7 }
```

Once again, we’re handling `iterable` keys, because PHP. The operation function `$fn` gets applied to the first element, along with an initial value, `$collect`. Then the result is fed back into the operation function as the new initial value, and so on until it runs out of values.

That’s a bit abstract but makes more sense with an example. The canonical trivial example for reduce is summing an array:

```
1 function sum(iterable $list): int
2 {
3     return reduce($list, fn($collect, $val) => $collect + $val, 0);
4 }
```

Note that we’re ignoring the key here as it’s irrelevant. PHP lets us do that. If we now call `sum([1, 3, 5, 7, 9])`, then the reducing function is called like so:

1.  (0, 1) ⇒ returns 1
2.  (1, 3) ⇒ returns 4
3.  (4, 5) ⇒ returns 9
4.  (9, 7) ⇒ returns 16
5.  (16, 9) ⇒ returns 25

And so we get the correct result of 25.

In normal PHP, you’d never do this, not when there’s a nice `array_sum()` method already implemented in C for you to use. However, it does illustrate several key aspects of functional-style programming.

*   The logic is built by composing trivially simple functions together.
*   Every function is a pure function.
*   Functions are being freely used as values, just as freely as the integers are.

More importantly, it demonstrates a pattern that can be used repeatedly in more complex cases where PHP doesn’t have an existing utility, or when the reducing function is complex enough that it warrants being separated out and tested in isolation.

Just for fun, let’s take `sum()` and see what else we can do with it, given all of the above:

```
1 $sum = fn(iterable $list) 
2     => reduce($list, memoize(fn($collect, $val) => $collect + $val), 0);
```

Now, `$sum` is still a function; it takes a list and reduces that list the same way as before. This time, though, since it’s a single line function returning a value, we rewrite it using short lambda syntax. We can also memoize the reducing function, as it’s a pure function. In this specific example it doesn’t buy us anything, but if we’re computing a lot of sums over time (or using a more expensive operation than just addition) then dropping a `memoize()` in there can be a very cheap speedup. We could also memoize all of `$sum` just as easily if we wanted to; which place is optimal to memoize, if either, depends heavily on your use case.

One of the interesting facts about `reduce()` is that it can be used as the basis of many, if not most other functional operations. For instance, there is no rule that the single value returned from `reduce()` cannot itself be a list. A list is still a value!

That means we could rewrite `map()` in terms of reduction:

```
1 function map_r(iterable $it, callable $fn): iterable
2 {
3     return reduce(
4         $it,
5         fn($result, $val, $key) => $result + [$key => $fn($val)],
6         []);
7 }
```

Consider what this function does. The reduction starts with an empty list `[]`, and then concatenates that empty list with the result of calling `$fn` on the first value in `$it`, preserving the key. That returns a new array with one key/value pair in it. That array is then concatenated with the key/value pair from calling `$fn` on the second value in the list, and so on until the whole new list is returned.

In practice, the `foreach()` version is more performant in PHP because iteration is cheaper than a function call in the PHP engine, albeit not as dramatically cheaper as it once was. (That may or may not be true in other programming languages.) It’s still nice to demonstrate you can do iteration over a list without actually iterating.

What about `filter()`? Can that be implemented as a reducer? It can indeed.

```
 1 function filter_r(iterable $it, callable $ifTrue = null): iterable
 2 {
 3     $ifTrue ??= fn($val): bool => (bool)$val;
 4 
 5     $reducer = function($result, $val, $key) use ($ifTrue) {
 6         if ($ifTrue($val)) {
 7             return $result + [$key => $value];
 8         }
 9         else {
10             return $result;
11         }
12     }
13 
14     return reduce($it, $reducer, []);
15 }
16 
17 // Or
18 
19 function filter_r(iterable $it, callable $ifTrue = null): iterable
20 {
21     $ifTrue ??= fn($val): bool => (bool)$val;
22 
23     $reducer = fn($result, $val $key) => $ifTrue($val)
24         ? $result + [$key => $value]
25         : $result;
26 
27     return reduce($it, $reducer, []);
28 }
```

I’ve shown the reducer here using both the long-form syntax and the short lambda syntax. You would use only one, naturally; which one you find easier to read is somewhat subjective, but I tend to prefer the short lambda version as it feels more declarative. The reducer logic is very similar to the one for `map_r()`. For each invocation, it returns the current `$result` untouched if the item should be filtered out and returns `$result` concatenated with the current value if it should be included.

# Concatenation

It is extremely common in procedural code to want to write a line that looks like the following:

```
1 getPromotions(mostExpensiveItem(getShoppingList(getCurrentUser(), 'wishlist'), [
2     'exclude' => 'onSale'
3 ]), $holiday);
```

That is, take the current user, get that user’s “wishlist” shopping list, find the most expensive item but skipping those that are already on sale, and then find any promotions available on that most expensive item for whatever the current holiday is. Then you can show those promotions to the user.

Such code is, as you may agree, horribly ugly and hard to read. It’s kind of inside out, it’s not obvious which parameters are part of which function, and adding an extra step to it is going to be an exercise in guessing at the right parentheses.

Usually the recommendation is to introduce a whole bunch of intermediate variables:

```
1 $user = getCurrentUser();
2 $shoppingList = getShoppingList($user, 'wishlist');
3 $mostExpensiveItem = mostExpensiveItem($shoppingList, [
4     'exclude' => 'onSale'
5 ]);
6 $promotions = getPromotions($mostExpensiveItem, $holiday);
```

That’s better but still not great, and we have to think of names for all of those intermediate variables. Proponents of object-oriented code often use method chaining, sometimes called a “fluent interface,” to allow you to write it this way:

```
1 $promotions = getCurrentUser()
2    ->getShoppingList('wishlist')
3    ->mostExpensiveItem(['exclude' => 'onSale'])
4    ->getPromotions($holiday);
```

That is easier to read but only works if those methods exist on the objects returned from each of those methods. Does it really make sense for an `Item` object in your store to have a `getPromotions()` method on it, which likely needs to hit the database? Not really. What if you want to offer promotions not for the most expensive item but for the items whose manufacturer is sponsoring a coupon? Does that mean adding that method to the `ShoppingList` class just so you can chain it? That violates most recommendations around object cohesion.

Stepping back, what we really want is a way to chain a series of steps together. The output of one step is the input to the next step, plus some other step-specific stuff. That “other step-specific stuff” is part of what makes it hard, because we can’t guarantee the parameter order of arbitrary functions.

Or can we?

Recall from the section on currying that it’s possible to convert any function into a single-parameter function, and in PHP 7.4 we can do so easily thanks to short lambdas. We can rewrite the functions in our chain like so:

```
1 $holiday = "Lincoln's Birthday";
2 $wishList = fn(User $user): ShoppingList
3     => getShoppingList($user, 'wishlist');
4 $item = fn(ShoppingList $list): Item
5     => mostExpensiveItem($list, ['exclude' => 'onSale']);
6 $promo = fn(Item $item): Promotions
7     => getPromotions($item, $holiday);
```

The types are, as always, optional; I included them here for completeness and to demonstrate the new functions are still type compatible with each other. Now we have a list of unary (single-parameter) functions that we want to use in order.

“List of functions” should be a hint. It’s an array of values, and what can we do with an array of values? Iterate them!

We’ll build a utility that essentially automates all of those intermediate variables so we don’t have to waste brain cells coming up with names for them:

```
 1 function compose(callable ...$fns): callable
 2 {
 3     return function($x) use ($fns) {
 4         $ret = is_object($x) ?  clone($x) : $x;
 5         foreach ($fns as $fn) {
 6             $ret = $fn($ret);
 7         }
 8         return $ret;
 9     };
10 }
```

`compose()` returns a new function (of course), which closes over the list of functions we pass in. That new function starts with some initial value, then passes it to the first function in the list and captures the result. Then that result gets passed to the second function, and its result captured and passed to the third, and so on. We also clone the input first if it’s an object to avoid modifying the original passed-in value.

The result is that we can chain together, or concatenate, or pipe, or compose (all of which are different terms for the same thing) any number of arbitrary unary functions, as long as they are type compatible. Sadly, we cannot catch type incompatibility at design time, but we’ll still get an error at runtime on the actual underlying functions (assuming those have types specified, which they absolutely should). The net result is we can do this:

```
1 $holiday = "Lincoln's Birthday";
2 $findPromotionsFor = compose(
3     fn($x) => getShoppingList($x, 'wishlist'),
4     fn($x) => mostExpensiveItem($x, ['exclude' => 'onSale']),
5     fn($x) => getPromotions($x, $holiday),
6 );
```

I’ve omitted the types this time to make it shorter, and because, as noted, the named functions still fail type checks at runtime if there’s an issue. But we can now see our “chain” of functions very clearly, with minimal overhead. Adding a new step is easy; just add a new unary short-lambda wrapper in the middle of the list, or swap one out, etc. As long as the types are still compatible from one function to the next, we’re good. And now we can use the `$findPromotionsFor(getCurrentUser())` function to find the promotions we should show.

Moreover, since `$findPromotionsFor()` is “just” a function, it could be further composed/concatenated/piped with still other functions (such as a chain that results in finding a user object). It’s piped functions all the way down!

If this concept feels familiar somehow, that’s because it’s the exact same principle behind the Unix command line. Small, single-purpose functions are “piped” together with the `|` character, where the input and output of each function is a stream of text. The principle here is exactly the same, but because we have a more robust programming language available, we can use richer data structures than just text strings. Please do so.

Let’s look back at that `compose()` function again, though. It should also look eerily familiar. It’s iterating over a list and feeding the result of one iteration into the next iteration. Doesn’t that look an awful lot like the `reduce()` function we described before? In fact, it is exactly the same.

In practice it is more performant to reimplement the looping logic in `compose()`, but for completeness’s sake let’s rewrite it as a reduction:

```
 1 function compose(callable ...$fns): callable
 2 {
 3     return function ($x) use ($fns) {
 4         return reduce($fns, function($collect, $fn) {
 5             return $fn($collect);
 6         }, $x);
 7     };
 8 }
 9 
10 // Or
11 
12 function compose(callable ...$fns): callable
13 {
14     return fn($x) => reduce($fns, fn($collect, $fn) => $fn($collect), $x);
15 }
```

Again, I’ve shown both the verbose and simpler versions. They are identical. In either case, `compose()` is still returning a new function, but this time that function has only a single statement: calling `reduce()` across the list of functions (which are, recall, “just” variables like any other) with a reducing function that is just “call the function with the current value” (aka `$fn($collect)`).

This is a perfect example of where `reduce()` can be useful for things other than addition, and serves to demonstrate the power of being able to treat functions as values. `compose()` is now a single-line function we can use to chain together arbitrary functions, by wrapping each arbitrary function into a unary function. If a function is already unary, it can be passed as-is although PHP has a sadly weak syntax for doing so.

And because the result is a function, it can be further chained as much as we want. What’s more, the call stack never goes much deeper than `compose()` itself (depending on what the underlying functions do, of course), so no matter how many functions we have chained together, we never risk blowing out the stack.

Let’s double-check, though. Is `compose()` a pure function?

*   Does `compose()` have any side effects? No. It’s taking input and returning output, no globals or state changes. Check.
*   Is `compose()` idempotent? Yes, passing in the same set of functions a second time gives back the same function afterward. Check.
*   Does it call any functions that are impure? Nope. Check.

So `compose()` is a pure function. Score. What about the function it returns?

*   Does it have any side effects? No. Check.
*   Is it idempotent? Yes. Check.
*   Does it call any functions that are impure? Maybe.

Unfortunately, there’s no way for us to know if the functions passed to `compose()` are pure or not. If they are, then the new function returns are also pure. If even one of them is not, however, it is not a pure function.

That’s a problem, but a somewhat small one. An impure function effectively “taints” any function that calls it, and is thus above it in the call stack. But we said a moment ago that chaining functions in this way does not have a deep call stack. So by keeping our call stack shallow, we limit the scope of the impure “taint.”

# Recursion

Much of functional programming in practice revolves around manipulating lists. That’s because lists are an extremely simple data structure, but deceptively powerful. It also works well as a primitive by which to build up larger algorithms.

We’ve already seen several list operations: `map()`, `filter()`, and `reduce()`. There are two more basic list operations to consider: `head()` and `tail()`.

In some older or more rigid languages, these operations are known as `car()` and `cons()`, respectively. That is mostly a legacy of LISP, in which they stood for “**c**ontent of **a**ddress **r**egister” and “**Cons**tructor.” You may run into tutorials using that terminology, even though it is really just an implementation detail of LISP. `head()` and `tail()` are far more descriptive, so that is what we are using here.

Given any list, `head()` returns the first value of the list. `tail()` returns everything but the first value without modifying the list itself. That’s all there is to it.

A user-space PHP implementation is straightforward:

```
1 function head(array $list)
2 {
3     return count($list) ? array_slice($list, 0, 1)[0] : null;
4 }
5 
6 function tail(array $list): array
7 {
8     return count($list) ? array_slice($list, 1): [];
9 }
```

Note the edge case handling for an empty list: In the case of `head()`, we return null, while for `tail()`, we return an empty list. That’s because the cardinality of the return must be maintained. Also note that the parameter here is `array`, not `iterable`. That’s because `iterable`s frequently do not support peeking at the first value without removing it, which we have to do in this case. There are ways around that, but that’s a tangent we won’t follow for now.

So far, so good, but what good are these functions, exactly? They are rarely used themselves but are very useful in constructing other operations using recursion rather than iteration.

## Recursion

Recursion is one of the most misunderstood and over-hyped concepts in computer science. It is made out to be highly complex and mind-bending, and somehow incredibly special that it can be used at all. I suspect much of that is simply history. In very early programming languages, functions had specific places in memory that they lived. There was no call stack per se; each function had its own memory, and that was that. Of course, that meant a function calling itself would be impossible without seriously tricky memory handling (which some languages did have, and it was seriously tricky). Later languages introduced dynamic function memory on a call stack, which made that complication go away.

The other reason recursion has a bad rap is performance. This critique is very language-specific, as different languages handle function calls differently. In languages that have a simple linear call stack, recursion can indeed lead to a very deep call stack that blows out your memory. In languages that are a little smarter, the engine can detect certain types of recursion, known as tail recursion, and internally convert the recursive function into an iterative one. In even more robust languages, including many strictly functional languages, there is no call stack as most procedural programmers are used to thinking of it, so the problem doesn’t appear in the first place.

PHP is, unfortunately, one of the simple languages in which recursion does pose a serious threat to memory usage as it does no optimization at all. That means while recursion can be used, it should be used judiciously as it can easily cause memory issues when working with even slightly large lists. As our goal isn’t to describe how one should always write PHP code but to explain the concepts of functional programming using a familiar language, we are ignoring that problem for the remainder of this section. In production code, you wouldn’t want to use it as readily as we are here; you have been warned!

The main advantage that recursion has is that it can result in very elegant algorithmic code. A recursive algorithm naturally follows the definition of a particular problem, just written in code. It also very naturally avoids mutating variables, which is a functional programming no-no.

For example, let’s reconsider `map()`. Instead of using a `foreach()` loop, we could write it as a recursive function instead.

```
 1 function recursive_map(array $list, callable $fn): iterable
 2 {
 3     if (count($list)) {
 4         return [$fn(head($list))], ...recursive_map(tail($list), $fn)];
 5     }
 6 
 7     return [];
 8 }
 9 
10 // Or as a one-liner:
11 function recursive_map(array $list, callable $fn): iterable
12 {
13     return count($list)
14         ? [$fn(head($list)], ...recursive_map(tail($list), $fn)]
15         : [];
16 }
```

In this case, `recursive_map()` is defined as a list consisting of applying `$fn` to the first element in the list, concatenated with calling `recursive_map()` on the rest of the list. If the list is empty, it simply returns an empty list. The result is a long line of `array_merge()` calls to concatenate together a long series of single-element lists.

Functional languages with better list support tend to have a nicer syntax for list concatenation, too.

Or, to take a more traditional example, consider the (in)famous Fibonacci sequence: Each element in a list is defined as the sum of the two previous values, or 1 if it’s the first two values. Recursively, the code looks exactly like its definition:

```
 1 function fibonacci(int $nth): int
 2 {
 3     if ($nth == 0) {
 4         return 1;
 5     }
 6     if ($nth == 1) {
 7         return 1;
 8     }
 9     return fibonacci($nth - 1) + fibonacci($nth -2);
10 }
```

Never write this code in PHP. It is horribly inefficient, both in terms of function calls and redundant calls to the same number. It can be much more efficiently written, in PHP, as an iterative loop:

```
 1 function fibonacci_iterative(int $n): int
 2 {
 3     $previous = 1;
 4     $current = 1;
 5     $next = 1;
 6     for ($i = 3; $i <= $n; ++i) {
 7         $next = $current + $previous;
 8         $previous = $current;
 9         $current = $next;
10     }
11     return $next;
12 }
```

In PHP, that is substantially faster and more memory efficient. However, it doesn’t really explain what the algorithm is. It’s very concerned with implementation detail, which often hides the algorithm itself. The recursive, functional version is much more self-explanatory.

That’s one of the areas that a functional language has significant benefit. A properly functional language (as opposed to one that just supports functional style code) can take steps in the language semantics to make recursive-looking algorithms more efficient. For instance, Haskell supports automatic memoization, meaning that the many redundant calls to `fibonacci()` with the same input are optimized away automatically. It can do that because all functions are guaranteed pure, and thus memoizeable. It also doesn’t use a call stack the same way PHP does. The result is that the first, easier to read version is faster than the iterative version, in addition to being more self-documenting.

# Immutable Value Objects

So far, we’ve been talking mostly about simple variables: ints, strings, and the occasional array. It’s a sorry language (and codebase) that can’t handle anything more robust, though. Complex data structures are what make modern software possible, but like most other features, they may have language-specific caveats. In a functional mindset, we need our values to behave in a certain way. Specifically, we want them to be unchanging.

The third core pillar of functional programming, after pure functions and first-class functions, is immutable variables. Superficially that term may sound contradictory: How can something be both variable (subject to change) and immutable (non-mutating, non-changing)?

It’s fine for a variable to represent “something to be determined at runtime,” but to only ever represent one thing. In fact, it’s critically important at times.

We already established that for functional programming to work, we need to be working with pure functions; pure functions have no implicit or side-band dependencies on any values outside of their parameters, nor any implicit effect on any value or state beyond its return value. That includes changing its parameters.

## What PHP Does

Consider the following snippet:

```
 1 function nextSunday(\DateTime $date): DateTime
 2 {
 3     $oneDay = \DateInterval::createFromDateString('1 day');
 4     while ($date->format('l') !== 'Sunday') {
 5         $date->add($oneDay);
 6     }
 7 
 8     return $date;
 9 }
10 
11 $today = new \DateTime('2019-12-25');
12 
13 $sunday = nextSunday($today);
14 
15 printf('Today is %s and the following Sunday is %s', 
16     $today->format('Y-m-d'), $sunday->format('Y-m-d')
17 );
```

We would expect it to print the date for Christmas 2019 and the Sunday after it (29 December). That’s what makes the most sense in context, but it’s not what happens. Instead, we get

```
1 Today is 2019-12-29 and the following Sunday is 2019-12-29
```

To make it even weirder, if we refactor away the `$sunday` variable, we get different output:

```
1 $today = new \DateTime('2019-12-25');
2 
3 printf('Today is %s and the following Sunday is %s', 
4     $today->format('Y-m-d'), nextSunday($today)->format('Y-m-d')
5 );
6 
7 // Today is 2019-12-25 and the following Sunday is 2019-12-29
```

Our code should not change results because of the order in which we call dependent functions! Here lies subtle and evil bugs, of the sort that neither a robust type system nor testing can fix for you. Testing may catch it after the fact, if your test coverage is really robust, but it would be much nicer if the code made such bugs impossible in the first place.

The problem is that `$date` inside `nextSunday()` is the same value as `$today`. They’re different variables, but they both refer to the same value in memory. That means when you change the value of one variable, you are changing it for both, creating a sort of “spooky action at a distance” (to quote Albert Einstein). “Spooky” is never a term you want applied to your code.

That problem doesn’t happen with integers, strings, or even arrays. The difference is in the way PHP variable passing works, and there’s some subtlety to it, largely inherited from other languages on which PHP is based.

Variables in PHP pass by value; that is, when you pass a variable to a function, the value gets duplicated, so inside the function, you’re dealing with an entirely different variable. However, you can also force it to pass by reference by placing an `&` in the function signature for that parameter: `function roundUpTo10(int &$num) {}`. In that case, PHP doesn’t duplicate the value but duplicates the reference to it, so there are now two variables pointing to the same value in memory. If you change one variable, you change the value behind it, thus impacting both variables. As we’ve seen, that’s bad.

Objects are a little weirder; objects already come with a separation between the value of the object in memory and its handle. When you pass an object to a function, you’re passing the handle by value. So the variable name you see is bound to the handle, and the handle then points to the object in memory. Duplicating the handle when you pass an object to a function still means it’s pointing to the same underlying value. That makes objects behave almost like they’re passing by reference, even though they aren’t.

There’s one important caveat to that, however: PHP doesn’t actually duplicate values when you pass them around. PHP’s engine uses “copy on write;” the implementation details are a bit intricate but not relevant for our purposes. The upshot, though, is that even though logically you can think of the following code having two 20 element arrays, there’s only one array in memory:

```
1 $one = range(1, 20);
2 $two = $one;
```

If you then change `$two` in some way, only then does PHP create a new copy of the array and modify that new copy, leaving `$one` untouched. That means we can semantically think of them as separate variables, but the memory usage is, generally, that of only a single variable. That makes our lives a lot easier when implementing immutable variables.

## Making It Immutable

Avoiding spooky action at a distance, which is a form of impurity, is vital for a functional system, and is a good idea even if you’re not trying to write functional code. Some strictly functional languages like Haskell only support immutable variables; changing a value after it’s set is impossible. In others, like Rust, variables by default are immutable; you must set a flag on a variable when it’s defined to make it mutable, which then triggers all sorts of extra compiler behavior to make sure you don’t screw up. PHP has neither of those safety belts, so we’ll have to do it ourselves.

For primitive values (integers, strings, booleans, etc.), it’s fairly easy. They already pass by value, which blocks spooky action at a distance. Don’t use pass by reference, ever.

For arrays, they also pass by value (with copy-on-write), so the same applies. Don’t use pass by reference.

For objects, it’s a bit more work. The key is to conceptualize an object not as a mutable collection of values, but as a value unto itself. You would not think of redefining what “5” means (I hope), just adding “1” to it to get a new value. That’s how you should approach objects as well.

To return to our previous example, the easy fix is to rewrite the `nextSunday()` function like so:

```
1 function nextSunday(\DateTimeImmutable $date): DateTime
2 {
3     $oneDay = \DateInterval::createFromDateString('1 day');
4     while ($date->format('l') !== 'Sunday') {
5         $date = $date->add($oneDay);
6     }
7 
8     return $date;
9 }
```

The `\DateTimeImmutable` class, available since PHP 5.5, has the same interface as `\DateTime`, but instead of modifying itself, it returns a new object that differs by whatever the change was. In this case, it returns a series of new `\DateTimeImmutable` objects that are reassigned to `$date`, and then the final reassigned `$date` gets returned. The value passed in never changes; the variable that points at it changes to point at something else. Because of PHP’s copy-on-write behavior, this is surprisingly efficient, so there’s almost no measurable performance difference. Now we can refactor the calling code whenever we want, safe in the knowledge that `nextSunday()` won’t be doing anything spooky.

## Objects, Functionally

When designing your own classes, your model should be `\DateTimeImmutable`, not `\DateTime`. Or rather, that’s the case for value objects. If you’re coming from an OOP background (as most modern developers are), then we need to first differentiate between different kinds of objects because the functional mindset is very different.

In classical OOP, as it usually gets taught, objects in code model real-world things, and have methods on them that make them do something. That something could be retrieving a value, updating a value, pushing data to a database, printing to the screen, or anything else, and it may even have knock-on effects to other objects. In fact, that’s precisely the point of that sort of design. This is often called the “Fat Object” approach, as domain objects tend to be large and persistent.

The idea behind that approach is that state is ugly and hard, so you encapsulate it within an object with explicit actions (methods) that can change it and nothing else. But you still have state, and state is still ugly and hard.

A functional approach, by contrast, strives to eliminate state entirely; or, rather, state exists only as the call parameters to functions. That means a hard, explicit split between data values and code that operates on values. In OOP speak, that means splitting classes into two flavors: *value objects* and *service objects*.

### Service Objects

Service objects are stateless, and are, in practice, just a more complex syntax for functions with closures. Consider this class:

```
 1 class ThemeRenderer
 2 {
 3     private $config;
 4   
 5     public function __construct(SysConfiguration $config)
 6     {
 7         $this->config = $config;
 8     }
 9   
10     public function renderUser(User $user): string
11     {
12         // ...
13     }
14 
15     public function renderProduct(Product $product): string
16     {
17         // ...
18     }
19 }
```

That is, in the end, really no different from:

```
 1 function renderUser(SysConfiguration $config, User $u): string {...}
 2 function renderProduct(SysConfiguration $config, Product $p): string {...}
 3 
 4 $config = getConfigFromWherever();
 5 
 6 $userRenderer = fn(User $u): string
 7     => renderUser($config, $u);
 8 
 9 $productRenderer = fn(Product $p): string
10     => renderProduct($config, $p);
```

Those two code snippets give us the same thing, in the end: Two operations we can pass around and invoke, with logic that require both a `SysConfiguration` value and `User` or `Product` value. Neither version contains any “state,” only immutable values that are closed over once at creation.

### Value Objects

In contrast, a value object represents a thing; “thing” in this case might correspond to a real-world object, but that’s mostly coincidental. Value objects are a noun, a value, a unique concept within your domain model. And they do nothing other than… be that thing. But just as “5” and “7” are different things, and Christmas 2019 and the following Sunday of 2019 are different things, if you change a part of a value, it becomes a new value and should be treated as such.

Let’s consider an object that represents distance:

```
 1 class Distance
 2 {
 3     private float $length;
 4     private string $units = 'meters';
 5 
 6     public function __construct(float $length, string $units = 'meters')
 7     { 
 8         $this->length = $length;
 9         $this->units = $units;
10     }
11 
12     public function length(): float
13     {
14         return $this->length;
15     }
16 
17     public function format(): string
18     {
19         return "$this->length $this->units";
20     }
21 }
```

Just as a timestamp with no timezone is incomplete and mostly useless information, a distance with no unit is incomplete. Both rely on implicit knowledge of the system that future developers may not have, so in both cases, we build a domain-specific object which encodes that information. In particular, note that `Distance` has no mutator methods; once the constructor is done, `$length` and `$units` cannot be modified. This gives us the immutability we want; we can pass a `Distance` object to another function and safely keep using it ourselves, confident we have not created any avenues for spooky action at a distance.

However, it’s not all that useful if we want to operate on the distance value. For instance, sometimes we want meters, sometimes kilometers, sometimes miles. But 5 kilometers is not the same value as 5000 meters; if we try to use an object expecting it to be one and get the other, we’ll have an off-by-1000 error. That means we need to convert from one unit to another. But telling the object to switch from “kilometer mode” to “meter mode” by modifying it directly introduces that spooky action problem.

Instead, just like with `DateTimeImmutable` we allow the object to create a new object.

```
 1 class Distance
 2 {
 3     // ...
 4 
 5     private array $factors = [
 6         'kilometers' => [
 7             'meters' => 1000,
 8             'kilometers' => 1,
 9         ],
10         'meters' => [
11             'meters' => 1,
12             'kilometers' => .001,
13         ],
14     ];
15 
16     public function as(string $units): self
17     {
18         return ($this->units == $units)
19             ? $this
20             : new static(
21                 $this->length * $this->factors[$this->units][$units],
22                 $units
23             );
24     }
25 }
```

The conversion factor between different units is well-known and fixed, so we can just bake that into the class. (Adding more possible units is left as an exercise to the reader; more robust approaches are also possible to avoid precision loss when using floats, but that’s off-topic for now.) The `as` method returns a new `Distance` object, with the requested units and the length expressed in that new unit. As an optimization, if the object is already in the right unit, then we can just return it as is because semantically 500 meters is 500 meters. The immutability of `Distance` is preserved, as we now get a new object in the format we want.

Now, say we want to combine two `Distance` values in order to know how far it is to traverse both of them. If they were bare, boring floats, then we could just use `+`, but since they’re not, we have to do it ourselves. Fortunately, it’s reasonably straightforward:

```
 1 class Distance
 2 {
 3     // ...
 4   
 5     public function add(Distance $add): self
 6     {
 7         return new static(
 8             $add->as($this->units)->length() + $this->length,
 9             $this->units
10         );
11     }
12 }
```

Once again, rather than modifying the value in place, we create another new `Distance` object. This one has the units of the object being invoked, and its length is the simple sum of its length and the length of the other object after converting them to the same units.

Similarly, we could have an `equals()` method that compares both the length and units of two `Distance` objects and returns true only if both match. Such a method is left as an exercise for the reader.

## Evolvable Objects

Probably the most famous value object in the PHP ecosystem is the PSR-7 HTTP Message Interfaces published by the PHP Framework Interoperability Group (PHP-FIG). In concept, it is just like the `Distance` class above, but for HTTP `RequestInterface` and `ReponseInterface` messages. (Observe that these are message objects that do not correspond to any real-world object.) It contains a number of values internally, but you cannot change them; you can only spawn a new request or response object from an existing one, with some change. In PSR-7’s case, rather than come up with custom names for each “spawn new” method, they were all prefixed with `with`. Here’s a sample of it, with PHP 7 types added for clarity.

```
 1 interface MessageInterface
 2 {
 3     public function getProtocolVersion(): string;
 4 
 5     public function withProtocolVersion(string $version): self;
 6 
 7     public function getHeaders(): array;
 8 
 9     public function hasHeader($name): bool;
10 
11     public function getHeader(string $name): array;
12 
13     public function getHeaderLine($name): string;
14 
15     public function withHeader(string $name, string $value): self;
16 
17     public function withAddedHeader(string $name, string $value): self;
18 
19     public function withoutHeader(string $name): self;
20 
21    // ...
22 }
```

There’s more, but it follows the same pattern:

*   A `getX` method to return the current value of a part of the HTTP message;
*   A `withX` method to create a new message object that is identical except for new data added;
*   A `withoutX` method to create a new message object that is identical except for some data removed.

In practice it is usually built up with chained method calls like so:

```
1 $response = (new Response())
2     ->withProtocolVersion('2.0')
3     ->withHeader('content-type', 'application/json')
4     ->withAddedHeader('cache-control', 'no-cache')
5 ;
```

That code actually creates four different `Response` objects, the first three of which are discarded and garbage collected along the way. While that may seem wasteful, in practice benchmarks have shown PHP’s copy-on-write behavior makes it impressively fast and efficient, to the point that, most of the time, you can write such code and not worry about the performance impact unless it’s inside a tight loop.

While there is no universal convention for describing this pattern, the PHP community has informally settled on calling them “evolvable” interfaces, because the object “evolves” from one object to another with each generation (method call). In practice, if you can use more purpose-built method names than `withX` that is better, but if the domain space doesn’t lend itself to that, then the `withX` convention is widely recognized within PHP, so is worth following.

## Dependencies

A common question when dealing with evolvable objects is, “But what about dependencies?” Developers used to an OOP world have to worry about ensuring objects don’t duplicate unexpectedly, because that could do weird things to their dependencies, and those dependencies may have transitive dependencies on something that should not get duplicated, like a database connection. And serializing an object is always fraught with challenges as you can’t serialize a database connection, or you may end up inadvertently serializing 15 layers of dependencies you don’t need, but will need to reconnect to after serialization.

A functional approach to data modeling provides an easy answer to that problem: It’s not a problem.

Service objects have those problems. That’s why service objects should never have state, making it pointless to even try serializing them. Cloning them is rarely necessary. Service objects form the pipeline through which data in your system flows.

Value objects, by contrast, are “just” data. They don’t have dependencies. They may have sub-objects, but those are also value objects. That means they don’t necessarily need to be dependency injected the way a service object is.

Consider a `Person` object, which has an `Address` object as one of its properties. A serialized `Person` includes a serialized `Address`, in its entirety. Which means when deserializing a `Person`, the object can reconstruct its own `Address` object. It doesn’t have to be injected. Even if it’s highly complex and needs a temporary builder object, that’s okay, and the builder can be created, used, and disposed of entirely within `Person`.

Value objects are the chunks of data that flow through your pipeline.

That “pipeline” analogy is not an accident. While OOP encourages you to visualize your system as a series of objects with lines between them, like neurons whose firing may trigger something else to fire, functional programming is better visualized with plumbing. Each function is a pipe that takes input and passes it on to some other pipe. The pipe may change size to adapt to the next pipe, the pipes may branch, the pipes may recombine, they may connect to a (data) sink, but they never leak. Functional data modeling is all about avoiding leaky pipes.

If your object design is such that you need to worry about long dependencies chains getting serialized, or not re-initialized properly, or that cloning may clone a database connection, it means that your object design is bad to begin with. Use that concern as a driver to refactor your system in a more functional way, with clearly separated service objects and immutable value objects, until that concern disappears.

As an aside, that sort of service/value object differentiation is directly contrary to the design of the “Active Record” pattern, where an object pulled from a database has a reference to its data source service so that it can put itself back. Active Record is inherently non-functional.

## Entity Objects

One caveat to value objects is the special case of entity objects. Entity objects are value objects with a unique identifier in some other system; that could be a persistent database, or a remote service, or something else where “the values are different now so it must be a different thing” no longer holds. If you want to change the price on a `Product`, your `Product` object is going to have some ID so you can save it back to the database with the updated price. That can’t be immutable, can it?

There are a few ways of addressing that problem. I’ll touch on each just briefly.

### Ignore It

Ignore it and break the rules for entities. That’s what the “Active Record” pattern does, as record objects (entities) have a direct connection back to their service so they can mutate and get resaved. While it seems tempting, don’t do that. It means everything your active `Product` object touches is no longer functionally reliable:

*   It’s no longer “the same value” being passed to a function, because who knows what state the database is in or if the object has been modified.
*   You’re susceptible to spooky action at a distance, even if your other functions are properly pure.
*   You cannot manipulate the object without concern for side effects, because it’s built to have side effects.
*   If you duplicate the object, the behavior of any changes you make is undefined.

This is a bad strategy. Even in OOP-modeled code, Active Record has a large number of problems. If you’re trying to leverage functional thinking, Active Record and similar approaches should be viewed as anti-patterns.

### Mutation Instructions

The second option is to split your reading and writing into separate pipelines and make the reading part a clean value object. If that sounds a lot like CQRS (Command Query Request Separation), that’s because it is. Under normal circumstances, read operations are far more common than write operations in most systems PHP gets used for, so having a read-only version of an entity that lacks mutator or evolving methods means most code is dealing with immutable objects.

For the pathways where an entity needs to be updated, use instead a dedicated changeset command. It could look a lot like the read entity or not, but it should be a separate, ideally incompatible interface. That way, code that expects to be reading an entity cannot get accidentally passed a mutable object, and the few parts of the code that are explicitly part of the mutation path know it, and you as a developer know to be extra careful with those parts.

For example, if there is a `Product` object that represents a product in an online store, that is read-only. There is a twin `ProductUpdate` object with the same getters, but also setters. Updating a product then would look something like this:

```
 1 class ProductUpdate
 2 {
 3     private Product $product;
 4 
 5     private array $changes = [];
 6 
 7     public function product(): Product
 8     {
 9         return $this->product;
10     }
11 
12     public function setDescription(string $desc): self
13     {
14         $this->changes['description'] = $desc;
15         return $this;
16     }
17 
18     public function getChanges(): array
19     {
20         return $this->changes;
21     }
22 }
23 
24 $prodUpdate = $repository->getProductForUpdate($id);
25 $prodUpdate->setDescription('A book about functional programming.');
26 $repository->persist($prodUpdate);
```

The result isn’t purely functional, but it’s 95% functional, which in PHP is already a pretty impressive feat.

### Event Sourcing

Taking that approach a step further, you could go full-on Event Sourcing. Other books have been written on Event Sourcing, so I won’t go into too much detail, but the general idea is that what is saved is not entity objects, but “events” that may impact the state of the data. Any “read model” is simply a denormalization of that event stream, which can be rebuilt at any time. To use the previous product description example:

```
 1 class ProductDescriptionUpdate
 2 {
 3     private string $description;
 4 
 5     public function __construct(string $description)
 6     {
 7         $this->description = $description;
 8     }
 9 
10     public function getNewDescription(): string
11     {
12         return $this->description;
13     }
14 }
15 
16 $stream->addEvent(
17     new ProductDescriptionUpdate('A book about functional programming.')
18 );
```

`ProductDescriptionUpdate` can be an immutable value object, with evolver methods, because it’s not the actual `Product`. The load routine, elsewhere, pieces the various changes back together to produce the read-only version of a `Product` at a given point in time, which could exist separately from a `Product` built from a different point in time.

Event Sourcing is a complex topic, so I won’t go further into how to implement that, but suffice to say it fits nicely with a “mostly functional” mindset.

### Functional State Management

Functional programming has its own idioms for handling state, which we’ll cover in later chapters. There are some other concepts we have to cover first in Part Two. For now, I’ll only say they involve the Scary Word^(tm), which isn’t really that scary; we just make it scary to keep children up at night.

## Intra-Function Immutability

So far, we’ve been focusing mainly on immutability at the function or object boundary, but there’s also immutability of individual variables within a function. In a strictly functional language that is also a no-no, for all the same reasons as between function calls. Strictly immutable variables also encourage you to write smaller functions that leverage recursion to process larger data structures like lists or trees. For instance, our `nextSunday()` routine above still has a mutable variable in it: `$date` still changes, even if that has no impact outside of the function. A strictly functional version of that function would look more like this:

```
1 function nextSunday(\DateTimeImmutable $date): DateTime
2 {
3     $oneDay = \DateInterval::createFromDateString('1 day')
4     return $date->format('l') == 'Sunday'
5         ? $date
6         : nextSunday($date->add($oneDay);
7 }
```

If the date is already a Sunday, just return it. Otherwise, call `nextSunday()` recursively with tomorrow and return its results. In this case, it builds up a call stack of `nextSunday()` calls, the final of which returns a date object that gets returned all the way down the stack as the last step. This is an example of “tail recursion,” and as discussed in the last chapter more robust languages have the ability to detect this kind of recursion and transparently convert it to the non-recursive version, which runs faster. Unfortunately, PHP is not such a language.

In practice, is it worth going strictly immutable in PHP? I would frankly argue no. Immutability at the boundary is mandatory to avoid spooky action at a distance, so always build and use immutable value objects and maintain strict separation between value objects and service objects/functions. Within a function, though, try to avoid mutating variables, but if the result would be too convoluted or slow, don’t sweat it. Focus instead on readability of the code. What makes the function easiest to reason about, read, and understand? Do that. If that means mutating an array or reusing a variable for a builder object, so be it. As long as the immutable boundaries are maintained, the function is still pure as viewed from the outside.

If your function is long or complex enough that it is hard to keep track of a variable that may change over the course of a function, it means your function is too long and complex and should get broken up anyway.

# Part Two

# Category Theory

Before we go further, we need to veer off of code for a little bit into the realm of category theory.

Stop, please don’t skip this chapter! I promise to be gentle.

Category theory is the realm of mathematics concerned with, well, categories. Categories are an abstraction much the way that type systems in programming are an abstraction, only cranked up to 11. Twice. In essence, it takes many of the concepts from programming and abstracts them away from programming entirely, to the point that they can apply to all sorts of concepts, as long as you can squeeze them into certain mathematical rules. At that high level of abstraction, it’s possible to prove general statements that, when reapplied back down to a lower level, allow you to reason about a problem in more robust ways.

Provided certain conditions are met, the point of category theory is to abstract well beyond mere programming and derive rules at a more generic level. Then, as long as those conditions are met back in a specific example, those rules are still true, which means you can make assumptions based on them being true.

Much of that process is valuable for proving things about programming that may seem intuitively true to an experienced programmer, but category theory provides a way to establish them firmly and reliably.

To make life more difficult, category theory also uses a completely different set of terminology from programming, except for where it uses the same words but for a slightly different concept. For good measure, it also does the same to set theory. For example, “object” in category theory has very little to do with what programmers would think of as an “object.” Many concepts also go by multiple names, further complicating matters. What programmers would call a “function” gets called variously “arrow” or “morphism” depending on your mood.

As if that weren’t enough, the programming language Haskell is frequently taken to be the definitive terminology on functional programming and category theory, even though it’s technically just one especially tailored implementation of it. (That’s not an exaggeration. Haskell was originally developed as a shared syntax for mathematicians to write logic and type proofs in, which for convenience was made executable. Later on, some very silly people discovered that it was possible to write actual programs in it and proceeded to do so.)

Functional programming technically evolved separately from category theory, but in practice, a great deal of the benefit of functional programming comes from being able to assume those rules are in place by ensuring you meet those conditions. For instance, “as long as it’s a pure function you can always cache the result” is a case where ensuring a certain condition holds (that the function is pure) means you can rely on certain assumptions (it’s always cacheable). By extension, certain types of functions can always be thought of as lookup tables rather than operations. Whether that lookup table ends up being more or less efficient than an operation is “just” an optimization problem. For that reason, understanding the more advanced parts of functional programming requires at least a little category theory.

Another aspect of category theory is that much of it is a matter of viewing the problem from the right angle. If you can take a problem and turn it sideways so it looks like another problem you’ve already solved, then you have solved the new problem, too. Much of what we’ll be doing here is taking a problem and turning it sideways so that it looks familiar to something we already know. (Category theory has rigorous mechanisms for such sideways looks, but for brevity, I’ll be doing that informally.)

This is not a book on category theory. This is an informal, intuitive-based summary of those parts of category theory that are relevant to us as programmers working in a fundamentally non-functional language (PHP).

## What Is a Category?

A “category” is a collection of:

*   Zero or more *Objects*
*   Some number of *Arrows* from one object to another object, which could be the same object

If you drew them on paper, you would have a series of dots (objects) and lines (arrows) connecting them. Arrows often go by the alternate name *morphism*: “morph” being Greek for “form” and “ism” meaning “study of.” Or, to use more colloquial English, “morph” as in “change” and “ism” meaning “thingie”. (I find the colloquial version a much more descriptive way of understanding morphisms as applied to programming.)

For a collection of dots and lines to qualify as a category, there are a few rules that it must follow:

*   There is an “identity morphism” for each object; that is, an arrow that points back to itself
*   Morphisms are composable; that is, they can be chained together
*   The composition of morphisms are associative; that is, when stringing multiple morphisms together, the grouping doesn’t matter
*   Morphisms are structure-preserving—more on that in a bit

![A simple two object category](resources/basic-category.png)

A simple two object category

Morphisms are usually written with arrows, like so: *f: A → B* means “f is the morphism from object A to object B”. There can be infinitely many morphisms from A to B, depending on the category. The source object of a morphism is known as its *domain*. Its destination object is known as its *codomain*. That pattern of “thingie” and its other end “cothingie” is consistent throughout category theory.

Composition of morphisms is usually denoted with *∘*. If there is a morphism from X to Y called f (*f: X → Y*), and a morphism from Y to Z called g (*g: Y → Z*) then we can concatenate the two together to produce a morphism called *g ∘ f*, that maps from X to Z. (Yes, it’s read right to left. Sorry. I didn’t invent it.)

![Composing a morphism from X to Z](resources/basic-composition.png)

Composing a morphism from X to Z

That’s a mouthful, but it should sound familiar. A few sections back, we talked about composing functions, where we pass the return value of one function into another function to “concatenate” them together. That’s the exact same concatenation we’re talking about here. The *∘* symbol is the mathematical way of writing the `compose()` function we wrote earlier. So if we’re talking about PHP functions `f(X $x): Y` and `g(Y $y): Z`, it means that:

`g(f($x))` == `compose('f', 'g')($x)` == a function that takes X and returns Z.

As long as there is a path from one object to another, you can represent that path as a new morphism that is the concatenation of the morphisms along that path.

The identity morphism is an arrow from an object to itself: *f: A → A*, generally called `id`. The identity morphism must be commutative. That is, *id ∘ f* == *f ∘ id* == *f*. There may be infinitely many other arrows from an object to itself, but only one is the identity morphism. Morphisms where the domain and codomain are the same, are called *endomorphisms*, “endo” being the Greek prefix for “within.” (“Endomorphism” thus means “within the same form thingie.”) It’s the same “no-op” pattern we’ve seen before, like 0 for addition and 1 for multiplication, except this time `id` is the “no op function,” i.e., no-op value in the function of composing two functions.

When viewing programming through the lens of category theory, a morphism is any single-parameter structure-preserving pure function, and objects usually represent types.

The idea of composition is core to both category theory and functional programming. In a sense, it is simply the age-old idea of “divide and conquer” applied to logic; if you break down your problem into small, easily digestible, almost trivial pieces (functions) with a clear and safe way to put those trivial pieces together, you can solve your overall problem by simply plugging those trivial pieces together in ways that follow the rules, and you are (almost) guaranteed to have a working answer at the end.

Think of it like LEGO blocks; by establishing a very clear standard size for blocks and the bumps on them, you can safely construct an infinite number of sculptures from the same basic blocks. Functions are those blocks.

The identity morphism in programming is, conveniently, trivially simple in almost all cases:

```
1 function id($x) {
2     return $x;
3 }
```

It should be self-evident that it is commutative.

## Objects

Objects are… thingies. They do not necessarily have any bearing on objects from object-oriented programming, which are “instantiations of a defined class of data properties and methods.” An object could be:

*   An integer, in a category that consists of all integers
*   A string, in a category that consists of ASCII strings less than 10 characters long
*   A set, in a category where each object is a set of something (“set” in the mathematical sense, meaning a unique list of values, which could themselves be sets)
*   A data type, in a category where each object is a data type representable by a programming language
*   A law, in a category where each object is a paragraph of the legal code

A category, therefore, may consist of a small, finite number of objects, a huge but finite number of objects, or a conceptually infinite number of objects (as in the case of “all integers”). A category may also have zero arrows other than the identity morphisms, or there may be multiple arrows from one object to another object.

A category that has only identity morphisms is called a “discrete category” and is generally described as “boring.”

## Some Definitions

Before we continue, let’s establish a few more definitions and notations to make the following sections easier.

*   Integers are any whole number, positive or negative, including zero. The set of all integers is denoted ℤ. It is an infinite list in concept, although in PHP it is limited to `PHP_INT_MIN` to `PHP_INT_MAX`.
*   Natural numbers refer to positive integers plus zero. The set of all natural numbers is denoted ℕ. (Programmers sometimes refer to these as “unsigned ints.”) It is an infinite list.
*   Positive integers without zero is denoted ℕ+.
*   Real numbers refer to any number, including fractional or decimal numbers. The set of all real numbers is denoted ℝ. Programmers tend to call these “floating point” numbers, aka `float`.
*   A *total function* is one that is valid for all permutations of its input (domain). A function may be total in one domain but not in another, similar domain.
*   A *partial function* is a function that is only valid for some input values in its domain. (Do not confuse “partial function” with “partial function application,” which we talked about earlier.)

All functions are exclusively either total or partial.

Morphisms must be total functions. That is, they must be valid for all permutations of their input, the source object. For example, the morphism “absolute value” (`abs`) is a total function for all real numbers ℝ, because it can handle any ℝ as an input. Square root, however, is only a partial function over ℝ because it fails for negative numbers. Square root is, however, a total function over non-zero natural numbers, ℕ+.

## Structure

We said above that morphisms need to be “structure preserving.” While we’re not allowed to peer inside an object to see if it has internal structure, it may have internal structure. Morphisms must respect that. For example, consider a category which has an object that is the set ℝ (real numbers) and another object that is the set ℤ (integers). Both sets are ordered; that is, 4.5 >= 2.3 in ℝ. If we have a morphism `floor` from ℝ to ℤ, then that ordering must be preserved. If we apply `floor` to 4.3, we get 4. If we apply `floor` to 2.3, we get 2. 4 >= 2. So yes, the order is preserved. More formally, *`floor`: ℝ → ℤ*. The function *`ceil`: ℝ → ℤ* also maps from ℝ to ℕ, is still order/structure preserving, but maps to different values.

![Structure preserving morphisms among numbers](resources/numbers.png)

Structure preserving morphisms among numbers

That is a trivial example, but it becomes more important when we look at morphisms between categories themselves.

Speaking of…

## Let’s Get Meta

Bear with me here for a moment, because we’re going to look at the world from a few angles. We’ve said that categories are a collection of objects and arrows; we’ve informally discussed sets, which are a collection of objects. And it is usually trivial to define arrows within a set; “is larger than” from the previous example, for instance, is an arrow. Does that mean a set meets the definition of a category?

In fact, sets are the most interesting (for us) kind of category. ℤ, the set of all integers, is a category of integers. ℕ is the set of natural numbers, and thus the category of natural numbers. Types in programming are themselves a special case of sets; Booleans are a set with two values: `true` and `false`. `int` is the type that is the set ℤ. And so forth.

But since we can have a category of sets, and sets are themselves categories, that means we can have a category of categories. In fact, there is a category that is the category of all categories, except itself.

If you can have a category of categories, then it follows there must be arrows between categories. There are. Those arrows get another fancy name: *functors*, which is a combination of “function” and “factor.” “Factor,” in this case, derives from Latin and means “doer, maker, or performer.” So “functor” literally translates as “function that does a thing,” but in Latin, whereas the rest of mathematics primarily uses Greek. (I presume mathematicians are just indecisive.)

A functor is a morphism between categories; or, put another way, it’s a way of transforming one category (`A`) into another (`B`) in a structure-preserving way. In this case, “structure preserving” means all the objects in category `A` translate (or “map”, or “convert”) to one and only one object in category `B` (but multiple of them could map to the same object in category `B`), and all the arrows in `A` also translate to arrows in `B` (but again, multiple arrows in `A` can map to the same arrow in `B`).

![A functor between two categories](resources/functor.png)

A functor between two categories

If we look at ℤ from one angle, it’s a set. If we look at it from another angle, it’s a category. It is both. We can use whichever perspective is most convenient for us at any given time. The same is true for ℝ. That means we can view `floor` as a functor from ℝ to ℤ. It applies for all values in ℝ (it’s a total function), and the ordering relationship is preserved.

As we can have morphisms from an object to itself, we can have functors that point back to their original category. For example, `squared` is a mapping from ℝ to ℝ. The domain and codomain are the same, although it will only map to positive values; that’s entirely fine, as long as it works for all inputs.

Functors that map from a category to itself are called *endofunctors*, which is a weird amalgam of Greek and Latin for “within the same category function doer thingie.” (It really does sound more impressive in Greek.)

## Isomorphism

Another important concept in category theory is equality. Equality is tricky at best in programming; 1 == 1, but does one product object “equal” another product object? What matters: their ID in the database, all of their internal properties, or their memory location? As usual, the unhelpful answer is “it depends.”

Category theory has the same problem. However, there is a specific flavor of equality that is especially useful. If you have an object `A` with an arrow to `B`, and another arrow from `B` back to `A`, then those morphisms are inverses of each other. It’s always possible to transition from one to another and back again. Those two objects are then said to be “equal up to isomorphism,” or simply *isomorphic*: in Greek, “equal form thingies.”

![An isomorphism from A to B and back again](resources/isomorphism.png)

An isomorphism from A to B and back again

Objects can be isomorphic, but so can entire structures of objects if they are fully parallel; they are not equal in the arithmetic sense, but if two objects or structures are isomorphic, it means in practice that one can be represented in terms of the other. Or, in programming speak, if two structures are isomorphic, then it’s completely safe to *refactor* code from one to another. The performance implications may be entirely different between two different structures, at an implementation level; that is actually a really good justification for converting code from one approach to another if you can guarantee the two approaches are isomorphic.

## Monoids

A few chapters back, we discussed a special case of functions called “monoids.” To refresh, a “monoid” refers to a function that:

*   Is pure
*   Is a binary function (takes two parameters and returns one value, all of the same type)
*   Is associative
*   Has an identity value

That should look very familiar at this point. The idea of associativity and an identity is pervasive in category theory, as it is what allows us to compose almost anything as long as the types are compatible; that is, the codomain of one morphism is the domain of the next. A monoid isn’t quite a morphism yet, though, because morphisms are unary functions.

However! Recall also that any multi-parameter function can be converted to a single parameter function; a process called “currying.” Consider a category with only a single object. Every monoid is a binary function that has been curried on that object. For example, in the category whose only object is the set of integers, ℤ, there is a monoid “add 1” from ℤ to ℤ, another monoid “add 5” from ℤ to ℤ, another monoid “add 397,” and so forth. There are an infinite number of morphisms from ℤ to ℤ because there are an infinite number of values of ℤ. There is even an identity morphism over addition, “add 0.”

A monoidal category, also sometimes called a monoid, is:

*   a single object category
*   where all the morphisms therefore necessarily point back to the same object (they are “endomorphisms”)
*   and one of them is the identity morphism

![A monoid category “A”](resources/monoid.png)

A monoid category “A”

That is, in fact, where the name “monoid” comes from. “Mono” meaning “one” or “single,” it roughly translates as “single thingie”; a single category object. All of its morphisms are, in essence, curried functions on itself.

Or, programmatically:

```
 1 function add(int $x, int $y): int
 2 {
 3     return $x + $y;
 4 }
 5 ==
 6 function add(int $x): int
 7 {
 8     return fn(int $y): int => $x + $y;
 9 }
10 
11 $add5 = add(5);
```

One could even say that those two add definitions are isomorphic.

# Categories in Code

All of that arithmetic is well and good, but how does that help us with code? For a more applicable example, let’s define a category consisting of all of the data types supported by a functional (or functional-enough-for-our-purposes) language. In PHP, that would include:

*   `int`
*   `float`
*   `bool`
*   `string`
*   `array`
*   `object`
*   `resource`
*   `callable`

`resource` is boring and weird, so we are going to ignore it. We could view the remaining types in a few different ways:

1.  As sets, each of which has either a finite (`bool`) or infinite (`string`) number of values.
2.  A bunch of discrete categories, one for each type.
3.  A category of sets, where each object is the set of a given type.

The third way is the most interesting perspective, so let’s use that. Let’s call this category **PHPType**.

What morphisms exist in our category **PHPType**? Technically an infinite number could, but here are some interesting examples:

*   We already saw `floor()` and `ceil()`, which are morphisms from `float` to `int`.
*   There’s an implicit morphism “truthiness” from `int` to `bool`; 0 maps to `false`, anything else maps to `true`.
*   `float` and `string` have their own “truthiness” morphism to `bool`.
*   There is an implicit “cast” morphism from `int` to float that can be invoked automatically except with extremely large values. (That’s why PHP’s strict mode can safely accept an `int` to a `float` parameter.)
*   `strlen()` is a morphism from `string` to `int`.
*   `count()` is a morphism from `array` to `int`.
*   The function “string concatenate,” which in PHP has a dedicated operator `.`, is an endomorphism from `string` to `string`.
*   The random utility function `soundex()` converts a string into a soundex key, which is itself a string. That makes it an endomorphism from `string` to `string`.
*   The language construct `array()` (or simply `[]` in most code today) is a morphism from `int` to `array`; `[5]` takes the `int` value 5 and maps it to a single-element array. There is a parallel morphism for every other type to `array`, using the same syntax.
*   The magic method `__toString()` lets you define a morphism from a certain object to a string.

An awful lot of functions you’re used to working with are morphisms or endomorphisms… but not all of them. They’re only a morphism if they are composable unary total pure functions: single parameter, work for any input of the source type, are idempotent, and can be safely composed.

![The PHPType category, visually](resources/php-type.png)

The PHPType category, visually

In a strictly functional language, all functions are morphisms. In PHP, it’s on us to make sure we only write morphism functions most of the time.

## Converting Structure

The types of a given language form a category, in our case **PHPType**. However, there are other kinds of categories in programming we can conceptualize. For instance, let’s consider a category called **\[PHPType\]**, whose objects are lists (arrays) of **PHPType** objects.

Note: For all of this to work, we’re talking about typed true-arrays: indexed, non-associative arrays where all values are of the same type. If that’s not the case, then all bets are off. That is, incidentally, why you always want that to be the case.

Because they’re both categories, we can define a functor that can convert both objects (values) and morphisms (functions) from one to the other. That is, we want to “lift” values and operations from the less-structured world of **PHPType** to the more-structured world of **\[PHPType\]**.

This ends up being an extremely powerful concept, especially later when we can get more creative in what we define as a category. Usually, in PHP, we have to do a bit of manual work for such a lifting functor. In PHP, though, this one is actually built-in.

There are two parts to the functor we want. The first part converts values from the world of **PHPType** to **\[PHPType\]**. The second part converts arrows, aka morphisms, aka functions.

Lifting values, in this case, is trivial because PHP has it built in: `array()` (or just `[]` in PHP 5.4 and later).

Lifting functions is a bit more interesting. Remember that, strictly speaking, we can only lift morphisms, aka unary functions. However, because of currying, we know a multi-parameter function can be converted into a unary function (that is, it’s isomorphic), so we can work with a multi-parameter function or a unary function, whichever is easier.

In concept, our goal is to turn any function like `foo(int $a): int` into `foo(int[] $a): int[]`. (Yes, that line is not valid PHP as PHP lacks typed arrays, but hopefully you get the idea.) One way to do so for a unary function is like this:

```
 1 function func_to_array_func(callable $fn): callable
 2 {
 3     return function(array $arr) use ($fn): array {
 4         $res = [];
 5         foreach ($arr as $val) {
 6             $res[] = $fn($val);
 7         }
 8         return $res;
 9     };
10 }
```

That is, we have a new function that takes an array and returns an array, after applying the original function to each element. That should look very familiar by now: It is the definition of `map()` we saw earlier! That means we can easily rewrite the lifting functor for arrays to simply:

```
1 function func_to_array_func(callable $fn): callable
2 {
3     return fn(array $arr): array 
4         => iterator_to_array(map($arr, $fn));
5 }
```

We’re not quite done. We still need to prove we’ve done it right. That means proving two constraints still hold, called the “functor laws.”

They should look familiar as they’re inherited from morphisms:

*   The identity (no-op) function from **PHPType** maps to the identity function in **\[PHPType\]**.
*   The lifted function (what `func_to_array_func()` returns) is still associative.

Let’s try it on the identity function:

```
1 $arr = [1, 2, 3];
2 $lifted = func_to_array_func('id');
3 $result = $lifted($arr);
4 print_r($result);
```

```
1 Array
2 (
3     [0] => 1
4     [1] => 2
5     [2] => 3
6 )
```

Yep, that works. Is it associative? A full formal proof will be difficult and time-consuming, but we can at least demonstrate the principle with an example.

Take these two functions:

```
1 $length = fn(string $x): int => strlen($x);
2 $times2 = fn(int $x): int => $x * 2;
```

Functor associativity means that mapping `$length` and `$times2` separately and then composing them should give the same result as composing them and then mapping the new function. Here’s composing them first:

```
1 $list = ["Hello", "PHP"];
2 
3 $composed1 = fn(string $s): int => $times2($length($s));
4 
5 $lifted1 = func_to_array_func($composed1);
6 print_r($lifted1($list));
```

And here’s lifting them first:

```
1 $list = ["Hello", "PHP"];
2 
3 $list_length = func_to_array_func($length);
4 $list_times2 = func_to_array_func($times2);
5 
6 $composed2 = fn(array $l): array => $list_times2($list_length($l));
7 
8 print_r($composed2($list));
```

Both snippets print the exact same output:

```
1 Array
2 (
3     [0] => 10
4     [1] => 6
5 )
```

Thus, `func_to_array_func()` is associative.

An important note on naming: `func_to_array_func()` may be self-descriptive, but it’s extremely not generic. This sort of “lifting” function is so common that it would be better to give it a common name we can recognize. The great thing about standards is there are so many to choose from, of course, and the terminology varies between languages. In Haskell, the name for this lifting function is `fmap`, as in “map this function into another category.” That’s the name we’ll use throughout the rest of the book as we discuss more types of functor.

Of course, we can’t use the same exact name for every functor; PHP doesn’t support multiple function definitions. Instead, we have to namespace it somehow. There are conceptually any number of ways of doing so, but for consistency we will use a static class method. On what class, you ask? On the one that is a functor for the value. Stay tuned.

## Function Objects

Finally, another terminology note. The word “functor” has meant “mapping between categories” in category theory for some time. However, the term also got adopted by some people on the software engineering side to mean something *completely different*: function objects. At least C++ uses this terminology, and I’ve seen it referenced in PHP once or twice. A “function object” is just a closure object, like we saw all the way back when talking about first class functions:

```
1 class Add1
2 {
3     public function __invoke(int $a): int
4     {
5         return $a + 1;
6     }
7 }
```

This double meaning of the word “functor” is an unfortunate side effect of computer scientists and software engineers rarely talking to each other, and leads to quite a bit of confusion when Duck Duck Go-ing.

The category theory usage is, as far as I can tell, far older. I, therefore, conclude that the software engineers who started using it to mean function object are responsible for the confusion, and so I reject their definition. In this book, “functor” always has the category theory meaning of “mapping between categories,” and I recommend using that nomenclature exclusively yourself. Just be aware the other definition may come up at times. Now at least you can confidently tell people that they’re wrong.

# Fun With Functors

## Combining Functors

Let’s review a number of things we’ve learned and their implications.

1.  A category can be of basically anything, as long as certain rules are met. That includes language types, but also many other things.
2.  A functor is a translation or mapping of both objects and arrows to another category. In programming, we can view that as “lifting,” or “enhancing,” or “decorating,” or “wrapping,” or various other verbs all meaning the same thing in this context.
3.  A functor to its own category is called an endofunctor.
4.  It follows, therefore, that you can have a category of endofunctors.

Also, consider:

1.  A monoid is a function that takes two parameters of the same type, and produces a value of that type, and does so associatively.
2.  A function’s “type” is the type of its return value, because that’s how you can plug it into the input of another function.
3.  A functor is represented as a function when we’re talking about programming.
4.  You can have a monoid for functors of the same type: It takes two functors that produce a given type and returns a value of that same type.
5.  “Functors of the same type” means we’re talking about endofunctors.

So if we have two functors from `C` → `Enhanced C`, called `F` and `G`, then we can write a monoid that combines them to produce an `Enhanced C`: `monoid(F, G)` → `Enhanced C`.

This monoid is highly useful. So useful in fact, that it gets is own special name: *monad*.

You may have heard the joking phrase “A monad is just a monoid in the category of endofunctors. What’s the problem?” Now we see what that phrase actually means, in category theory. Translating all of those fancy-sounding words back down to terminology we’re more used to:

*   A monad is just a monoid in the category of endofunctors.
*   A monad is an associative binary function in the category of endofunctors.
*   A monad is an associative binary function that takes two endofunctors and produces an enhanced value.
*   A monad is an associative binary function that takes two functions that return an “enhanced” and produces an enhanced value.
*   A monad is a function that takes two functions that return an “enhanced” and produces an enhanced value.
*   A monad is a function that lets you compose two functions that return “enhanced” values.

All of those fancy words to get back to “a monad is a fancy kind of composition.” Because really, once we get back down to programming that’s all it means.

## Monads in Programming

So why are monads so infamously scary and complicated? There’s a couple of reasons.

One, because they’ve developed a mystique about them that is really unearned, due mostly to the funky sounding name. It’s also because Haskell supposedly uses them everywhere, yet there’s nothing in Haskell syntax that a programmer from a more common imperative language would recognize. That is, they’re famously confusing because they’re famous for being confusing.

Two, because composition is so core to effective functional programming, and “enhanced” can mean pretty much anything, monads are extremely flexible. Or, rather, monads should be viewed as a design pattern (enhancing variables and then composing functions that work on them), and like any good design pattern they can crop up in an infinite number of places. While there are a few very common examples of monads, monad patterns can appear in ways that do not look at all like those common examples.

Three, because most tutorials on them are terrible and confuse the matter with unnecessary analogies before jumping straight to category theory without any slow-build up. It is my hope that this book has provided sufficient slow build up that by now all of these fancy words make sense.

Four, because the implementation of the monad pattern in most non-functional languages ends up looking nothing like its description above, and is implemented using classes. That’s not a bad way of doing it (we’re going to do exactly that in the following chapters), but it makes lining up the typical sample code with the theory difficult because it doesn’t actually map precisely. To make matters worse, every different library or tutorial uses a different set of nouns, some of which are borrowed from category theory, some from Haskell, and some from “it reads better for the actual code in this specific circumstance, so let’s go with that.” If you read three monad tutorials, you are going to get four sets of terminology.

This is why we can’t have nice things.

Over the next several chapters, we’re going to see different examples of “the monad pattern” in action. There are many common elements, but also elements that are highly specific to that particular use case.

## Anatomy of a PHP Monad

In practice, to implement what in programming would be called a monad pattern, there are a few moving parts:

First, you need a way to lift or enhance a value. Canonically, in category theory, this is called `unit`. In Haskell, it’s a special function called `return`. We can’t use `return` as a function name in PHP, of course. In practice, this is almost always the constructor of a class, because the natural way to enhance or decorate a value in PHP (and most similar languages) is to stick it in an object. It’s common (though not absolutely necessary) to provide a static method call as well to make the code read cleaner.

Second, you need a way to enhance a function. That’s the `fmap` we saw before, which takes a function `f(int $x: int)` and turns it into `f(EnhancedInt $x): EnhancedInt`.

These first two points are… not a monad. They constitute a *functor*, not a monad.

Third, you need a way to take a function that expects an unenhanced value and returns an enhanced value, and then pass it an enhanced value. That is, if you have a PHP function `$G = f(int $x): EnhancedInt` you want a function `h(EnhancedInt $x, $G): EnhancedInt`. In Haskell, this operation is generically called `bind`. In other languages, it gets called `flatMap`. Because `EnhancedInt $x` can come from another function, including a previous call to `bind`, this is effectively combining two `$G` functions together: It’s a monoid, where the first function has already been invoked. That means, if you want to get pedantic, `bind` is the actual monad.

Fourth, what happens if we try to combine `fmap` and `bind`? We end up with a function that takes `EnhancedInt` and returns `EnhancedEnhancedInt`, which is too meta to be useful. Instead, we need a function that takes an `fmap`ed function and `bind`s it, then sorts out the extra wrapping. The common name for this function is `join`, but you may also run across `chain`. It’s the same thing.

Fifth, another common operation that is not technically part of the core definition is to `fmap` and apply a function in a single action. That commonly goes by the name `map`. If you think back to `map` on arrays, you can see that’s what it’s doing: It’s taking a function that operates on a single value, converting it to act on a list of values, passing it a list of values, and getting back a list of values.

If you want to be really really pedantic, it’s possible to implement `bind` in terms of `join` and `fmap`. So in practice, depending on your specific use case, you may not need all five bits. The only required parts for the monad pattern are:

1.  An enhance/wrap/decorate/lift operation for a value; in practice this is almost always an object constructor.
2.  Some way to apply functions to that lifted value that continue to produce lifted values. This is some combination of `fmap`, `bind`, `join`, or `map`, which may go by different names in different use cases. (And, depending on the tutorial you read, some may be omitted entirely just to keep you on your toes.)
3.  It follows the “monad laws.”

The monad laws essentially boil down to “it’s still a monoid”:

1.  `unit` is a left identity for `bind`. That is, `bind`ing a function to a wrapped value produces a wrapped value that is the same as applying the function to the unwrapped value. Put another way, the lift/wrap/enhance is a no-op with respect to the value being lifted/wrapped/enhanced.
2.  `unit` is a right identity for `bind`. That is, `bind`ing a no-op function is a no-op.
3.  `bind` is associative.

By this point, you should be seeing a pattern in all of these laws: There’s a no-op, and it’s associative. Those two rules, expressed in various ways, are what makes composition safe and reliable. If composition is not safe and reliable, then weird bugs will spontaneously appear at random.

# Algebraic Data Types

## Products

Much of category theory is an abstraction from set theory. We already said types in programming languages are, or can be viewed as, discrete sets. That means there are “set like things” we should be able to do with them.

For example, one thing you can do with sets is take a “Cartesian product.” That is, pair every permutation in the first set with every permutation in the second set. If you have two finite sets `A` and `B`, their Cartesian product is the set `AxB`, whose values are pairs of some value from `A` and some value from `B`, written `(a, b)`. The number of possible values in `AxB` is the number of possible values in type `A` multiplied by the number of possible values in type `B`. So if `A` is Booleans (two values), and `B` is even numbers under 15 (seven values) then the number of values in `AxB` is 2 * 7 = 14.

You can think of a product in Boolean terms as “an `A` AND a `B`”.

The programming language name for this is a *pair*, as in, a pair of values. Pairs, however, can be easily combined, because one of the types involved can itself be a pair. So given basic types (or sets, or objects, all the same thing depending on your perspective) `A`, `B`, and `C`, we can create `(a, (b, c))`, as well as `((a, b), c)`.

`(a, b)` and `(b, a)` are not equal. A function (or morphism) that expects one will break if it gets the other. However, it’s trivially simple to convert between the two losslessly with a swap function. Since there’s a function from one to the other and back again, that means they are “equal up to isomorphism,” or isomorphic.

Similarly, `(a, (b, c))` and `((a, b), c)` are not equal in the sense that we can just ignore the parentheses. That is, they are not associative. However, it’s trivially simple to convert between the two losslessly. That makes them “associative up to isomorphism.” More importantly for us, they’re also both isomorphic to `(a, b, c)`.

An ordered fixed list of different types is called in programming lingo a *tuple*. A 2-tuple is a pair. You can also have a 3-tuple, 30-tuple, or more generically an n-tuple.

Usefully, there is also a type that can be incorporated into a Cartesian product that is isomorphic to not doing so; that is, it’s a no-op. That type is the `unit` type, which is the set with only one value (think `null`). A product of a set `A` with a single-element set has the same number of elements as `A`; no actual information has been added. If product types are equivalent to multiplication, then `unit` here is 1.

That is, we have a category (sets), we have a binary way of operating on it, and we have a no-op value. Hey, look, a monoid! **<Set, product, unit>** constitutes a monoidal category.

## Product Types in PHP

Many languages have native support for tuples. PHP does not. The closest it has are arrays, but arrays are untyped, so we cannot enforce that `[1, "hello"]` is valid and `["hello", 1]` just makes no sense. That’s fine, though, because frankly tuples are a painful data structure to work with much of the time because there’s no built-in way to refer to each element other than by position, which is just as bug-risky as untyped arrays.

What’s more useful in practice are named tuples; that is, tuples where each element has a name by which it can be accessed so that the order becomes irrelevant. Technically the order is still there, but because it’s isomorphic to reorder them it doesn’t impact us in practice. Different languages have different terminology for named tuples, but in PHP and most similar languages you’re already intimately familiar with them: classes.

The OOP perspective on classes is that they create a new type unto themselves, whose internal details are entirely opaque. The category theory or functional perspective on classes is that they are *product types*, a combination of two other types (categorical objects) to form a new type (categorical object). Neither of these perspectives is right or wrong; the language syntax supports either mindset.

As we discussed back in the chapter on value objects, it’s important to differentiate between service objects and data objects. Service objects are closed-over functions with funny syntax. Value objects are dumb nouns in their own right. Now, we can also think of them as product types built from other types (which could themselves be product types). Or nouns built by composing other nouns. (German speakers should be right at home here.)

Even classes have a category theory basis, if you look at them the right way.

## Coproducts

Most things in category theory have an inverse. Morphisms have a domain and codomain for their opposite ends, for instance. Product types also have an inverse, conveniently called a *coproduct*.

Without going into too much mathematical detail, if a product is “an `A` AND a `B`” then a coproduct is “an `A` OR a `B`”. Or said the other way around, if a product is “build an `AxB` out of an `A` and a `B`” then a coproduct is “break up an `AxB` and take either an `A` or a `B`”. Or more formally `Coproduct AxB = A | B`.

Where the number of possible values of a product type mirrors multiplication, the number of possible values of a coproduct type mirrors addition. `Coproduct(AxB)`’s possible values are the number of possible `A` values plus the number of possible `B` values. In our previous example, that would be 2 + 7 = 9. Hence they are also known more commonly as “sum types.”

Coproducts, like products, are associative up to isomorphism. That is, `A | (B | C)` and `(A | B) | C` are both isomorphic to `A | B | C`. Just as a product type may contain any number of composed types, a sum type may break down to any number of sub-types.

Are sum types a monoid? They’re associative up to isomorphism, so that’s half the answer. Is there an identity value? There is. Generically it is called `void`, and in sets means the empty set, `{}` (not to be confused with `null`, which is a set with only a single object). `A | B | void` is exactly the same as `A | B`. Think of it as 0 for addition. So yes, **<Set, sum, {}>** is a monoid.

## Coproducts in PHP

Most non-strictly-functional languages don’t have native sum type support. Some languages have *enumerations*, or “enums”, which are a sort of junior version. The sum type `color` can be a `Red` OR a `Green` OR a `Blue`, but never multiple of those at the same time. That’s not quite the same, though, as enums don’t support “this could be any integer OR any float” (but not, say, a string).

PHP doesn’t have native enum support, either. The closest approximation it has for sum types or enums is interfaces. The functional/categorical way of viewing an interface is that of a sum type of unbounded possible values. Or in code:

```
1 interface LoginSystem {}
2 
3 class Local implements LoginSystem {}
4 
5 class OAuth implements LoginSystem {}
6 
7 class LDAP implements LoginSystem {}
8 
9 function login(LoginSystem $sys, User $user) { }
```

Here, the `login()` method requires the sum type `LoginSystem`, whose possible values are `Local`, `OAuth`, and `LDAP`.

This is not a perfect match, however, since nothing prevents users from implementing their own class that matches that interface. There’s no in-language way to bound the legal values the way an enum of sum type would. However, it still gives us a “good enough most of the time” way to model sum type behavior.

In practice, “sum type behavior” ends up meaning… essentially polymorphism. Not necessarily the kind of polymorphism you’re used to talking about with methods, however (although that, too). We can use sum types to create different logical pathways or different contexts in which to allow other code to run. We’ll see some examples of that in the next few chapters.

# Part Three

# Handling Null

## The Problem

Recall from the chapter on concatenating or composing functions that we really want to be able to pipe functions together. That’s a very low-impact way of building up a large solution out of little solutions in a controlled and pure way. There’s one important caveat to it, though. That assumes all of the functions involved are total functions. If any function involved has no defined output for a given input, all bets are off because it has nothing meaningful to return. It’s no longer a morphism. Commonly, the answer here is to have that function return `null`, which is the programming equivalent of a shrug emoji.

That creates a problem because the next function then needs to be able to know how to handle a shrug emoji (`null`). Most likely, all it can do is respond with its own shrug emoji, and then it’s shrug emoji all the way down.

Error handling via shrugging is generally a bad idea.

As an aside, sometimes PHP functions return `false` instead of `null` to indicate error conditions. That is even worse, as it’s not just unhandleable, but also not type safe. Plus, because `false` silently casts to legal `int` and `string` values, it can be even harder to detect. That makes it really easy for a shrug emoji to hide in your code and produce all sorts of completely incorrect results.

In short, any function that returns `false` for an error condition (unless it’s return type really is `boolean`) is wrong, is a design flaw, and there are no exceptions to that rule. That includes every PHP standard library function that makes that mistake. Never do that.

## The Example

Let’s consider the same example as the previous chapter on composition. Here it is again in its procedural form:

```
1 $user = getCurrentUser();
2 $shoppingList = getShoppingList($user, 'wishlist');
3 $mostExpensiveItem = mostExpensiveItem($shoppingList, [
4     'exclude' => 'onSale'
5 ]);
6 $promotions = getPromotions($mostExpensiveItem, $holiday);
```

*   `getCurrentUser()` could fail if there is no one logged in.
*   `getShoppingList()` could fail if the user doesn’t exist, or if that user has no shopping list.
*   `mostExpensiveItem()` could fail if the user’s shopping list is empty.
*   `getPromotions()` could fail if there are no promotions for that item for the given holiday.

If any of those functions return null, the next function cannot work. The naive, procedural way of addressing it would be to wrap a bunch of `is_null()` calls around everything:

```
 1 $user = getCurrentUser();
 2 if (!is_null($user)) {
 3     $shoppingList = getShoppingList($user, 'wishlist');
 4     if (!is_null($shoppingList)) {
 5         $mostExpensiveItem = mostExpensiveItem($shoppingList, [
 6             'exclude' => 'onSale'
 7         ]);
 8         if (!is_null($mostExpensiveItem)) {
 9             $promotions = getPromotions($mostExpensiveItem, $holiday);
10         }
11     }
12 }
13 if (!is_null($promotions)) {
14    // Display promotions or something.
15 }
```

We can do better.

## The Category Theory Solution

From a category theory perspective, what we need to do is lift all of those functions to accept `null` and return `null` in addition to what they’re already doing. That is, they need to be enhanced so that their domain (input) and codomain (output) include null, thus making them total functions over the space of “the thing you’re expecting, plus null.”

That results in:

*   `getCurrentUser()` has a codomain of “User objects or `null`.”
*   `getShoppingList()` has a domain of “User objects or `null`” and codomain of “ShoppingList objects or `null`.”
*   `mostExpensiveItem()` has a domain of “ShoppingList objects or `null`” and a codomain of “Product objects or `null`.”
*   `getPromotions()` has a domain of “Product objects or `null`” and a codomain of “PromotionList objects or `null`.”

Now they’re all total functions and can be concatenated, in the category of “**PHPType But With Null**.”

## The Programming Solution

Programmatically, what we want to do is factor out all of those `is_null` checks that handle the flow control.

This problem space is the classic first example of monads in action, and as a believer in tradition, I’m starting here as well. Different languages use a different name and often different techniques to arrive at a `null`-handling monad. In Haskell, it’s called `Maybe`. In C++’s standard library it’s called `optional`. In Rust, it’s called `Option`. They’re all the same thing.

### Unit

The first step is to define a way to lift a value to “the same thing but with `null`.” That’s pretty straightforward in PHP:

```
 1 class Optional
 2 {
 3     private $value = null;
 4 
 5     private function __construct($value = null)
 6     {
 7         $this->value = $value;
 8     }
 9 
10     // Alias of "pack", "lift", "unit", "return", all the same thing.
11     public static function of($value): self
12     {
13         return new static($value);
14     }
15 
16     public static function none(): self
17     {
18         return new static();
19     }
20 }
```

In this case, I’ve included both a constructor and a static method. I find the static method easier to use, so for consistency I’ve made the constructor private. I’ve also included a dedicated static method for constructing the `null` case. Your mileage may vary.

### Bind

Second, we need to modify each of the functions we’re using to return an `Optional` that may or may not contain a value. For simplicity, I am showing only one; the rest are left as an exercise for the reader.

```
1 function getShoppingList(User $user, string $listName = 'main'): Optional
2 {
3     isset($user->lists[$listName]) 
4         ? Optional::of($user->lists[$listName])
5         : Optional::none();
6 }
```

As an aside, couldn’t `getShoppingList()` be a method on the `User` object directly? If you want to, sure. In that case, the “function” you’re working with is the callable `fn($user) => ([$user, 'getShoppingList'])('wishlist')`. The syntax looks a little different, but the logic is the same.

Third, we need a way to call one of those modified functions with an `Optional`. That’s exactly what the `bind` operation is:

```
 1 class Optional
 2 {
 3     private $value = null;
 4 
 5     // ...
 6 
 7     public function bind(callable $fn): self
 8     {
 9         if (!is_null($this->value)) {
10             return $fn($this->value);
11         }
12         return $this;
13     }
14 }
```

`bind` here is the same `is_null()` dance we saw before but factored out to a method. It does what `bind` claims to do, however: It takes a wrapped value (`$this`) and a function that returns a wrapped value (`$fn`) and sticks them together (`$fn($this->value)`).

We can now rewrite our code to look like this:

```
1 $holiday = "Lincoln's Birthday";
2 
3 $promotions = Optional::of(getCurrentUser())
4     ->bind(fn($x) => getShoppingList($x, 'wishlist'))
5     ->bind(fn($x) => mostExpensiveItem($x, ['exclude' => 'onSale']))
6     ->bind(fn($x) => getPromotions($x, $holiday))
7 ;
```

Or wrap it into a function to make it reusable:

```
1 $promotionFinder = fn($userFinder, $holiday) => Optional::of($userFinder)
2     ->bind(fn($x) => getShoppingList($x, 'wishlist'))
3     ->bind(fn($x) => mostExpensiveItem($x, ['exclude' => 'onSale']))
4     ->bind(fn($x) => getPromotions($x, $holiday))
5 ;
6 
7 $promotions = $promotionFinder('getCurrentUser', "Lincoln's Birthday");
```

In either case, `$promotions` is now an `Optional`, which may or may not contain a list of promotions. While this code isn’t quite as clean looking as the version that used `compose()`, it doesn’t have the `null` bugginess of that version, and it’s way cleaner than the deeply nested mess above.

Look carefully at the methods we’ve written. Every one is a pure function. Assuming no `null`s happen, a new `Optional` object is returned each time. They really are just piped together in a pure, functional way.

We could make one optimization and statically cache an instance of `Optional` with a null value to return from the `none()` static method. That would, strictly speaking, make it not a truly pure function. However, the net effect externally is still the same, and it means over the course of a program you need only a single “null instance,” which you could compare with `===`. Whether that’s worth it or not I leave up to personal preference.

### Getting Back Out

We could continue working with `Optional`s as long as we want. For instance, we could pass (`bind`) `$promotions` to a theming function that returns rendered HTML-or-`null`. Some purists argue that once lifted to an enhanced variable, you should never come back down. I find that to be practical only some of the time. Generally speaking, once lifted you should stay there “as long as possible but no longer.” That means there needs to be some way to “unlift”/”unwrap”/”unwhatever” the value. There’s zero standardization for what to name that operation. In Rust it’s `unwrap()`. `value()` is also a completely viable option. I’ve also seen `extract()` and `unpack()`.

Of course, that means you need to know if there is something there to unwrap. If you try to unwrap a `null`, you want to, well, not get a `null`. Different languages have different ways of handling that. Since PHP has none of them, the most straightforward is to just add a manual method check:

```
 1 class Optional
 2 {
 3     private $value = null;
 4 
 5     // ...
 6 
 7     public function valid(): bool
 8     {
 9         return !is_null($this->value);
10     }
11 
12     public function value()
13     {
14         return $this->valid() 
15             ? $this->value 
16             : throw new \RuntimeException("The cat is dead, Schrodinger");
17     }
18 }
```

The upshot here is any function that returns an `Optional` forces you to think about whether the return value is invalid. If you call `getCurrentUser()` and just start using it, assuming it has a value, it works fine in the happy path… but then fails miserably on the unhappy path. By making it return an `Optional` the question of, “Wait, is this a real value?” gets thrown in your face, and you’re less likely to forget to check the unhappy path. (You could still be lazy, but now you have no excuse.)

Other libraries and languages have other additional utilities here. For instance, Java’s `Optional` class has some nice default-handling utility methods instead. Translated to PHP, they’d be:

```
 1 class Optional
 2 {
 3     private $value = null;
 4 
 5     // ...
 6 
 7     public function orElse($default)
 8     {
 9         return !is_null($this->value) ? $this->value : $default;
10     }
11 
12     public function orElseGet(callable $default): bool
13     {
14         return !is_null($this->value) ? $this->value : $default();
15     }
16 }
```

In this approach, you’re forced to provide a default value when extracting the wrapped value, just in case. If deriving the default is potentially expensive, you can provide a function that only gets called if needed.

There’s a lot more you can do here if you want and still qualify as a “Maybe Monad.”

## An Alternate Implementation

Just for fun, let’s see if we can get rid of those conditionals in the `Optional` class, too. In both Haskell and Rust, the Maybe Monad is implemented with type classes. In Haskell, `Maybe` is defined as one of `Just` or `Nothing`. In Rust, `Option` is defined as one of `Some` or `None`. PHP doesn’t have type classes, but we can approximate them using subclasses. (That is, this is an example of the “sum types” we discussed earlier.) Here’s an alternate way to implement our `Optional` monad:

```
 1 interface Optional
 2 {
 3     public function bind(callable $fn): self;
 4 
 5     public function valid(): bool;
 6 
 7     public function value();
 8 
 9     public function orElse($default);
10 }
11 
12 class None implements Optional
13 {
14     public static function none(): self
15     {
16         return new static();
17     }
18 
19     public function bind(callable $fn): self
20     {
21         return $this;
22     }
23 
24     public function valid(): bool
25     {
26         return false;
27     }
28 
29     public function value()
30     {
31         throw new \RuntimeException('Sorry, Schrodinger');
32     }
33 
34     public function orElse($default)
35     {
36         return $default;
37     }
38 }
39 
40 class Some implements Optional
41 {
42     protected $value;
43 
44     private function __construct($value)
45     {
46         $this->value = $value;
47     }
48 
49     // Alias "of", "pack", "lift", "unit", "return", all the same thing.
50     public static function of($value): self
51     {
52         return new static($value);
53     }
54 
55     public function bind(callable $fn): self
56     {
57         return $fn($this->value);
58     }
59 
60     public function valid(): bool
61     {
62         return true;
63     }
64 
65     public function value()
66     {
67         return $this->value;
68     }
69 
70     public function orElse($default)
71     {
72         return $this->value;
73     }
74 }
75 
76 function getShoppingList(User $user, string $listName = 'main'): Optional
77 {
78     isset($user->lists[$listName]) 
79         ? Some::of($user->lists[$listName])
80         : None::none();
81 }
```

I prefer the second version, but you’re free to disagree. It’s only verbose because of PHP’s limited syntax and the extra newlines required by PSR-12 (the PHP-FIG code formatting standards).

## A Note on Types

You may note that this chapter omits types on most method calls. Given how useful types are for functional programming that may seem odd.

That’s because PHP’s type system is still relatively weak compared to many other languages. In particular, it lacks “generics.” With generics, one can define a type in terms of another type, such as “an `Optional` that contains a `string`” or “an `Optional` that contains a `User` object.”

We discuss generics in more detail in Part Four.

In general, to do functional programming well requires either a type system robust enough it can do generics or weak enough that types can be omitted entirely. The stronger alternative with generics is, I would argue, superior, for all the same reasons that typed code generally is superior. It allows the language syntax and compiler to do most of the debugging work for you, and ensure you are never trying to connect a square peg to a round hole. It would be even nicer with type inference, which allows you to omit types when the language is able to derive the type from context.

That is not PHP, however, which means we have to fall back to the untyped, implicit version and lose some type safety. That is a legitimate argument against functional programming in PHP, although there are enough other benefits that it is frequently worth the trade-off.

If you ever see someone lamenting the lack of generics in the language, or wishing it had them, this is why.

# Either/Or and Error Handling

## The Problem

The “Maybe Monad” is a nice and simple example, but only if you don’t care why a given value is missing. If you want to indicate what the error was, then you need something more robust than just `null`. We want the same general outline as `Optional`, though, with an error triggering a “fall through” that skips the rest of the composed functions.

If you squint, that may look a lot like an exception. It is certainly similar, but with some important differences:

1.  We want to use errors for control flow, whereas exceptions are supposed to be for “really exceptional” cases like “the database is missing,” not “there are no sales happening for that product.”
2.  In PHP, exceptions are very expensive to create. Largely that’s due to the need to build the backtrace, which is there even if you don’t use it or even throw it, but either way, it means using exceptions for common cases is extremely inefficient. (That’s not necessarily true in other languages, such as Python, but this is a PHP book.)
3.  It’s easy to throw an exception and assume it will be “someone else’s problem,” when it really should be the caller’s problem. The temptation to write just the happy path and throw exceptions where things fail and then forget to handle the unhappy path is quite high. As with `Optional`, we want the code to force us to care about the unhappy path, preferably before a user finds themselves on it and falls off the cliff at the end.
4.  Exceptions violate purity; a function that throws an exception affects the state of the world in a way other than its return value, potentially by unrolling the program’s entire call stack and crashing. A function that can arbitrarily cause your program to crash, depending on what try-catch blocks are placed outside of it, is decidedly impure.

What we really want is to allow a function to return *either* a value or an error. In fact, that’s the standard name for it: *Either*.

## The Example

Let’s look at the case of validating input. Say a user is signing up for an account, and we want to validate that the username is allowed. For it to be legal, it has to be:

*   Not already in use
*   Start with a letter
*   Be at least three characters long
*   Not contain non-alphanumeric characters

Ignore for a moment whether or not this is a good set of criteria; it gives us something to work with.

We want to have either a value or error message back at the end.

## The Category Theory Solution

That one of the possible values is an error is incidental. From a category theory perspective, what we’re looking at is taking two types and `OR`-ing them together, that is, taking the coproduct. Our `Either` type is one of two possibilities, usually denoted `Left` and `Right` to be extra generic. `Left` and `Right`, in turn, are parameterized by some other value.

That is, we’re lifting the type `Int` to `Int Or This Other Thing`, where “this other thing” in our example is an error. Or more abstractly, if `Optional` is lifting to “type or `null`”, `Either` is lifting to “this type or that type.”

## The Programming Solution

In the most minimalist sense, `Either` looks a lot like the `Optional` structure from the last chapter. In fact, the version of `Optional` that had a separate `Some` and `None` subclass is an `Either`. It’s “either” a desired value or `null`, where the handling for the `null` pathway is “just keep doing nothing forever.”

Different use cases of the `Either` pattern have different logic in the `Left` and `Right` pathways. In the simple case of exception-esque error handling, the `Left` pathway is essentially the same as the `None` pathway from before, but other cases might look entirely different. (Remember, monads are *design patterns*, not precise naming from an ivory tower.) To emphasize that this is just a specific implementation of the `Either` pattern (and because as a lefty I am offended by the idea that Left is the “unhappy path”), we’ll use a more purpose-built set of names.

We’ll implement `Either` in multiple ways, just to show that there’s no one true way. First let’s mimic the `Optional` approach, as it is the more generic.

We first need to establish our data wrappers. Specifically, we have two paths: Success and Failure. Both are legitimate Results from our input validators. Let’s use exactly those terms:

```
 1 abstract class Result
 2 {
 3     protected $value;
 4 
 5     public function __construct($value)
 6     {
 7         $this->value = $value;
 8     }
 9 
10     public function value()
11     {
12         return $this->value;
13     }
14 
15     public static function of($value): self
16     {
17         return new static($value);
18     }
19 
20     abstract public function bind(callable $fn);
21 }
22 
23 class Success extends Result
24 {
25     public function bind(callable $fn)
26     {
27         return $fn($this->value);
28     }
29 }
30 
31 class Failure extends Result
32 {
33     public function bind(callable $fn)
34     {
35         return $this;
36     }
37 }
```

`Success` wraps our happy path and carries a value from one validation step to the next. `Failure` wraps the unhappy path and carries the error that was returned by a validation step. Each has their own version of `bind`, which handles control flow. The value being carried for the Success path is the input string being validated. The value being carried for the Failure path is some kind of error message; rather than making that another string, let’s make a custom type for that:

```
 1 class ValidationError
 2 {
 3     private $message;
 4 
 5     public function __construct(string $message)
 6     {
 7         $this->message = $message;
 8     }
 9 
10     public function getMessage(): string
11     {
12         return $this->message;
13     }
14 }
```

Now we can write our validation routines:

```
 1 function lengthCheck(string $s): Result
 2 {
 3     return strlen($s) >= 3
 4         ? Success::of($s)
 5         : Failure::of(new ValidationError('String too short'));
 6 }
 7 
 8 function existsCheck(string $s): Result
 9 {
10     return in_array($s, ['aaa', 'bbb', 'ccc'])
11         ? Failure::of(new ValidationError('Username in use'))
12         : Success::of($s);
13 }
14 
15 function characterCheck(string $regex, string $s): Result
16 {
17     return preg_match($regex, $s)
18         ? Success::of($s)
19         : Failure::of(new ValidationError('Invalid characters found'));
20 }
21 
22 function startsWithLetter(string $s): Result
23 {
24     return ctype_alpha($s[0])
25         ? Success::of($s)
26         : Failure::of(new ValidationError('Must start with a letter'));
27 }
```

Note that most of them are just free-standing functions that take a string and return a `Result`, which is “either” a `Success` or `Failure`. There’s one that’s slightly different; `characterCheck` takes a regex and a string to test. I did that mostly to show it’s simple to still use that function in our pipeline.

We can now build an `Either` pipeline to validate a username:

```
1 $result = Success::of('abc123')
2     ->bind('lengthCheck')
3     ->bind('existsCheck')
4     ->bind(fn(string $s): Result => characterCheck('/^[a-zA-Z0-9]*$/', $s))
5     ->bind('startsWithLetter');
```

Note here that we’re inlining the `characterCheck` call with a regex to filter on that limits the values to alphanumeric characters. It could just as easily be done as a single “isAlphaNumeric” function if we wanted. However, then the function name would have to change if we decide to allow underscores in usernames, or if we decide to be polite to users from Ireland (whose names often have apostrophes), or to users from non-English speaking countries. There are many ways to skin this cat that aren’t related to functional programming per se, so take your pick.

Either way (pun intended), we now have a `$result` that is a `Success` or `Failure`. There are a few ways we can handle it. One is to type check it with `instanceof` and either continue or display the enclosed error message.

Alternatively, we could add an `either()` method to `Result` that takes two callables, one that only runs on Success and one that runs only on Failure. Each class’s implementation would simply run one callable and ignore the other.

As another option, we could offer a separate `success()` and `failure()` method that takes a callable, runs on the appropriate class, and is a no-op on the other one.

### Railway Programming

This style of flow control via `Either` is sometimes called “railway oriented programming,” a term coined by Scott Wlaschin to discuss how to handle errors in F#. The metaphor is that you have two train “rail lines,” and can “switch” from the happy track to the unhappy track but not back again.

It takes a bit less typing in F# due to its stronger type system, but the concept is largely the same as shown here. I highly recommend watching the video and slides he has on his website on railway oriented programming: [https://fsharpforfunandprofit.com/rop/](https://fsharpforfunandprofit.com/rop/).

### More Pathways

There’s a lot more we can do with this path. For instance, suppose we want to insist that all usernames are lowercase to avoid confusion between users “Larry” and “larry.” We could add another validator, or we could just lowercase them ourselves and be done with it. The latter case doesn’t have an error condition, however. Does that matter?

Not really. PHP already has a function that forces a string to lowercase: `strtolower`. We just need to convert it to work in our `Result` world. Fortunately, we’ve already discussed how to “lift” a function from `string` to `string` into a function from wrapped string to wrapped string: `fmap`. But since we want to go ahead and call it immediately, we want the `map` variant. `map` in this case is fairly simple since we don’t need to worry about changing tracks:

```
1 class Result
2 {
3     // ...
4 
5     public function map(callable $fn): self
6     {
7         return static::of($fn($this->value));
8     }
9 }
```

Now we can insert that into the pipeline at the beginning, and the string that gets passed on is in all lowercase.

```
1 $result = Success::of('ABC123')
2     ->map('strtolower')
3     ->bind('lengthCheck')
4     ->bind('existsCheck')
5     ->bind(fn(string $s): Result => characterCheck('/^[a-zA-Z0-9]*$/', $s))
6     ->bind('startsWithLetter');
```

Now even in the success case, `$result` contains the now-modified string, and we can continue to use that.

### Collapse the Types

The code above shows the generic approach to an `Either`, where every value gets wrapped. However, it has two problems:

1.  The `Failure` wrapper is kind of pointless since it only ever contains a `ValidationError`.
2.  `ValidationError` is kind of pointless, since it only ever wraps an opaque string.

We can solve both problems in this particular case by shifting the class structure while retaining the monad-like behavior.

```
 1 class Result { ... }
 2 
 3 class Success extends Result { ... }
 4 
 5 class ValidationError extends Result { ... }
 6 
 7 class StringTooShort extends ValidationError {}
 8 class UsernameExists extends ValidationError {}
 9 class InvalidCharacters extends ValidationError {}
10 class DoesNotStartWithLetter extends ValidationError {}
```

Now, the validators need only return one of `Success` or a subclass of `ValidationError`. For example:

```
1 function lengthCheck(string $s): Result
2 {
3     return strlen($s) >= 3
4         ? Success::of($s)
5         : new StringTooShort();
6 }
```

That makes the code simpler and easier to read, and provides more robust error handling potential through the type system. We can now programmatically differentiate between a username that’s too short and one that doesn’t start with a letter, for example, which makes displaying useful error messages to the user easier. It also gives us a complete list of the possible error conditions: it’s all the subclasses of `ValidationError`.

Whether the error classes themselves contain further error display logic or that’s handed off to some other routine is, from this chapter’s point of view, a matter of personal preference.

### Alternate Approach

This is a relatively simple case. For this simple case, it seems like an awful lot of ceremony. Can we do better?

We can, in fact. Let’s start with the same validators we’ve just seen (now returning type-specific error objects), and strip `map` and `bind` out of the wrapper classes. That means `ValidationError` can just be an interface, with any number of implementing error classes. `Success` is just a boring wrapper around a value.

```
 1 interface Result {}
 2 
 3 class Success implements Result
 4 {
 5     protected $value;
 6 
 7     public function __construct($value)
 8     {
 9         $this->value = $value;
10     }
11 
12     public function value()
13     {
14         return $this->value;
15     }
16 
17     public static function of($value): self
18     {
19         return new static($value);
20     }
21 }
22 
23 interface ValidationError extends Result {}
24 
25 class StringTooShort implements ValidationError {}
26 class UsernameExists implements ValidationError {}
27 class InvalidCharacters implements ValidationError {}
28 class DoesNotStartWithLetter implements ValidationError {}
```

Next, we still need to `bind` our validator functions so they can handle a `Result` object. In this case, there are only two possible things it can do, so we can just stick that into a single function with an `if` statement:

```
 1 function railway_bind(callable $fn): callable
 2 {
 3     return function ($param) use ($fn) {
 4         if ($param instanceof ValidationError) {
 5             return $param;
 6         }
 7         return $fn($param->value);
 8     };
 9 }
10 
11 // Or the even shorter version:
12 
13 function railway_bind(callable $fn): callable
14 {
15     return fn($param): Result
16         => $param instanceof ValidationError
17             ? $param
18             : $fn($param->value);
19 }
```

`railway_bind` (named in honor of Scott Wlaschin’s example) takes a callable we assume returns a `Result`, and turns it into one that takes a `Result` and returns a `Result`; specifically, the `Error` track falls through while the happy path calls the original callable and returns its `Result`. The `fmap` for converting `strtolower` is also straightforward (note here that we’re using `fmap` rather than `map`, because it’s not being immediately invoked).

```
1 function railway_fmap(callable $fn): callable
2 {
3     return fn($result): Result => Success::of($fn($param->result));
4 }
```

Now that we have a series of functions that take `Result`s and return `Result`s, we can pipe them together the old fashioned way:

```
1 $validator = compose(
2     railway_fmap('strtolower'),
3     railway_bind('existsCheck'),
4     railway_bind((fn(string $s): Result
5         => characterCheck('/^[a-zA-Z0-9]*$/', $s)),
6     railway_bind('startsWithLetter'),
7 );
8 
9 $result = $validator(Success::of('Larry'));
```

And now we can call `$validator` and get back either a `Success` wrapped around a username or a `ValidationError` of some kind.

This approach is entirely valid, and still constitutes an `Either` monad. We have a `bind` that is associative, we have an `fmap`, and we have a unit (the constructor of `Success`). `unit` is both a left identity and right identity of `bind`. It checks out.

Why aren’t more monads implemented in this more minimalist fashion? In purely functional languages, they usually are. In traditionally OOP languages (such as PHP), the extra ceremony of classes stands in for the lack of type classes and/or generics that more functional languages offer. They also account for the common lack of type inference and function overloading; note that we had to specify which kind of bind we were working with (the name `railway_bind`), because PHP won’t let us just define multiple `bind` functions and figure out which one we mean from context.

Though that would be kind of cool.

## Either Either?

An important observation is that `Either` is, as we said before, a coproduct type. That is, it’s an `OR` of two types. `OR` is, helpfully, associative. That means `Either A | B` and `Either B | C` can combine into `Either A | B | C`.

This means the technique shown here for two possible values (`Success` and `Failure`/`ValidationError`) still works just as well for three, four, or even more possible values. The upper limit here is not the math, just our human ability to reason about our code. We’ll see an example of multi-path `Either` in future chapters, but don’t get carried away. A 20-path `Either` would still likely qualify as spaghetti code, even if it’s still nominally functional.

# Tracking Data

## The Problem

So far, we’ve discussed two different approaches to error handling, but there’s far more the monad pattern can offer. For example, while functions in a functional system cannot retain state, they can pass values on to other functions that contain state. In essence, the call stack is the place state lives.

How then do we allow functions to record data about their action, beyond their simple return value, without having a global mutable value? How can we let functions have side effects without them having side effects?

## The Example

Suppose we want to do some sort of textual analysis. Say, we want to take a long piece of text and determine its word count, line count, reading level, what human languages it has, and so forth. As part of that process, we may want to do some normalization, so we can’t just call operations on the string independently of each other if we want to avoid mutable variables.

What we want is a composed pipeline of analysis functions that can modify the string as they go, but also record side-band data about the string. What we want at the other end is that side-band data.

## The Category Theory Solution

It may seem like a stretch to think of this as a new category of data, but in some sense it is. We’re lifting our analysis functions from “string” to “string and a log.” That’s no more of a stretch than “type or `null`.”

What’s different in this case is that we’re not changing the flow of control based on the enhanced type. Rather, the enhanced type is a product type of a string and a log. When the log gets added to, it is now a new value. (Remember the whole chapter on value objects.)

Where the Either monad lifts types to “type OR type”, this monad pattern lifts types to “type AND type.” Because it allows functions to write to a log, it’s common name is the *Writer* monad.

## The Programming Solution

In the interest of flexibility, let’s assume the list of stats to collect is unbounded; it’s just a key/value pair of strings, which we can model as an associative array.

That makes it tempting to have our analysis functions just return a three element array: `[string, label, stat]`. While that is technically possible, it fails in a number of ways.

*   “Tuple arrays” (mixed-type compound variables where the position is important) are notoriously not self-documenting.
*   We could switch to an associative array to give it labels, but associative arrays are still strictly less documenting than a proper data type (class).
*   We don’t want to lift our string to an array! That’s the wrong category. We want to lift our string to a string-and-log.

Remember, the return value of the function is a value in our lifted/enhanced type. So it has to be an object, on which we can then invoke more analysis functions. Let’s start with our product type itself, then:

```
1 class Stats
2 {
3     protected string $string;
4 
5     protected array $log;
6 }
```

Note: I would normally argue very strongly against using arrays so willy nilly, as PHP arrays make a terrible data structure for data modeling and have no guaranteed immutability. However, this chapter is about the `Writer` monad, not the pitfalls of arrays, so to save space we’ll just roll with `$log` as an array.

Now we need a `unit` operation for it, which is just a constructor and optionally an `of` method:

```
 1 class Stats
 2 {
 3    // ...
 4 
 5     protected function __construct(string $string, array $log)
 6     {
 7         $this->string = $string;
 8         $this->log = $log;
 9     }
10 
11     public static function of(string $string, array $log = []): self
12     {
13         return new static($string, $log);
14     }
15 }
```

For ergonomics, I’m forcing external users to use the `of` method, which makes `$log` optional, but it’s equally valid to make the constructor public and eliminate `of` entirely.

Now that we can create a new “string with side-band log” object, the next step is to allow us to `bind` other functions to it (i.e., invoke those functions on this value). The name `bind` is really kind of generic and not self-documenting, though. Let’s call it `analyze()` instead.

```
 1 class Stats
 2 {
 3     // ...
 4 
 5     public function analyze(callable $fn): self
 6     {
 7         $result = $fn($this->string);
 8         return new static($result->string, $this->log + $result->log);
 9     }
10 }
```

Here’s where all the interesting bits are. When we `bind` (analyze with) a function, that function gets passed the string to analyze. It passes back a new `Stats` object, which we then merge with the current object. “Merge,” in this case, means to use the new object’s string, and concatenate their logs together.

Moreso than in the previous examples, we can see the monoid behavior at work here. There’s two `Stats` objects, `$this` and “the one that `$fn` returns.” Those two objects of type `Stats` are then added together to produce a third `Stats` object, which is returned. “Added” in this case is defined as “the second one’s string, and both of their logs,” but in concept, we could smush those two objects together in any way we want.

The analysis functions are fairly straightforward. Here’s a sample of possible analyzers:

```
 1 function readingLevel(string $s): Stats
 2 {
 3     return Stats::of($s, [
 4         'Reading Level' => 'high school'
 5     ]);
 6 }
 7 
 8 function normalizeNewlines(string $s): Stats
 9 {
10     $cleaned = preg_replace("/[\r\n]+/", "\n", $s);
11     return Stats::of($cleaned);
12 }
13 
14 function countStats(string $s): Stats
15 {
16     $words = str_word_count($s);
17     $lines = substr_count($s, "\n");
18     return Stats::of($s, [
19         'Word Count' => $words,
20         'Line count' => $lines,
21     ]);
22 }
23 
24 function wordDistribution(string $s, int $minimum = 0): Stats
25 {
26     $words = array_count_values(str_word_count(strtolower($s), 1));
27     $words = array_filter($words, fn($value) => $value >= $minimum);
28     arsort($words);
29     return Stats::of($s, [
30         'Word distributions' => $words
31     ]);
32 }
```

Computing the `readingLevel` of a block of text is actually rather hard, so I’m not going to as it’s off topic. You can implement that yourself (or turn it over to some web service call). But it returns a valid `Stats` object, with an unmodified string and a new log entry.

We can `normalizeNewlines` by folding all multi-newline sequences to a single newline. We wouldn’t want to use that for the string that gets stored, but this isn’t a string to be stored, just analyzed. Its log component is empty, which is fine.

Now that newlines are cleaned up, we can do some basic `countStats` on the string. In this case, we return the string unmodified and a two-element log entry; that is also totally fine.

We can even do some deeper analysis and get a `wordDistribution`. In this case, the analyzer function also takes a minimum count to filter out uninteresting words from the result. The log entry it returns is not a string but an array. That doesn’t violate any rule we’ve established so far, so that’s fine. (However, it’s another reason I would define a `StatItem` class for each entry if this were a real implementation.) Note that this function does modify the `$words` variable internally; if we wanted to be extremely pedantic that violates the no-mutable-variables rule, but the overall function itself is still pure so, meh.

Running an initial string through an stat analyzer pipeline is then just as simple as we’ve come to expect:

```
1 $result = Stats::of($string)
2     ->analyze('normalizeNewlines')
3     ->analyze('readingLevel')
4     ->analyze('countStats')
5     ->analyze(fn($s) => wordDistribution($s, 3))
6 ;
```

The first three functions are already unary, so we can pass them in directly. `wordDistribution()` is multi-parameter, so we first curry it with a minimum value of 3. In the end, we get a `$result` `Stats` object. We now need to get at the log it contains. That’s trivial:

```
1 class Stats
2 {
3     // ...
4 
5     public function log(): array
6     {
7         return $this->log;
8     }
9 }
```

And now we have a complete list of all of the statistical information we requested, with no global state, no mutable values (that matter), built out of pure functions, and flexible enough that we can add an infinite number of analyzers to it, all kept reasonably memory efficient by PHP’s copy-on-write behavior.

And we get to say we’re using monads.

# Combining Monadic Behavior

One limitation of monad-based flow control is that it is not always easy to combine. Stacking two monads on top of each other is difficult to do generically, and depending on the language may be syntactically difficult or even impossible. However, the underlying concepts of the monads involved, their particular “lift,” can be readily combined with one-off solutions that combine both sets of logic. For example, stacking our previous Either and Writer monads while still retaining both of their behavior is difficult. However, writing a single monad that “lifts” values to “Either with a Log” is reasonably straightforward.

To demonstrate how that can be done, let’s take a look at one of the harder problems in software engineering: parsing. Turning a string into a meaningful logical structure is a hard problem; humans take several years to learn how to do it despite constant practice, and even then frequently get it wrong. That computers can be made to do it at all, even for simplified cases, is nothing short of amazing.

The first step in parsing a string is called “lexing,” as in, determining its lexical structure. The input of lexing is a string to analyze. The output is a series of tokens, which represent the structure of the string; it validates that the string is syntactically valid. A second step turns those tokens into an abstract syntax tree that defines meaning; it validates the string is semantically valid.

Lexing is easier, so let’s focus on that. There are numerous algorithms for lexing a string that vary widely in terms of their flexibility, performance, and complexity. The specific algorithm we are implementing is loosely based on the one used by Go’s template package. It is actually an informal state machine. The phrase “functional state machine” may seem odd; aren’t state machines concerned with tracking state, and functional programming with avoiding state? Yes… mostly. In strict functional programming, state is encapsulated in function calls rather than a free-floating mutable value. That’s what we saw before in the Writer monad, and it’s what we are going to implement here.

## The Example

So that we have something to parse, let’s define a Domain Specific Language (DSL) for a hypothetical application that allows non-developers (or at least non-PHP developers) to create triggers that fire on certain events. It won’t be as flexible as writing PHP code, but because it’s more restricted, the potential for misuse (deliberate or accidental) is much less. Consider this example trigger definition:

```
1 On object.triggerName
2 If condition OR condition
3 If condition
4 Execute someAction
```

The first line defines the trigger that causes this handler to fire; the “object” and “triggerName” could map to entities in our domain model, such as “Product” and “Update,” or to some more abstract trigger. It’s followed by zero or more other condition lines, each of which starts with `If` and then has some condition. The structure of the condition could get complicated, but from our point of view, that’s “just” an implementation detail as we’ll see. We’ll also allow conditions to be ORed together, and each condition line represents an AND. Finally, there’s one or more `Execute` lines that cause some named action to trigger.

What does that all mean semantically for our application? The lexer doesn’t care; we can simply define “someAction” to be a string. Whether that string refers to a function name, a class name, an entry in a dependency injection container, or some piece of user configuration is irrelevant at this level. There are still syntactic decisions we have to make, however. For instance, let’s decide that:

*   The literal keywords (`On`, `If`, `Or`, and `Execute`) are all case insensitive.
*   `object`, `triggerName`, and `someAction` are case sensitive strings.
*   Line breaks are significant, so that each directive must be on its own line.
*   Other than that, however, whitespace is not significant.
*   Both `\n` and `\r\n` delimited lines are supported.

We also need to make decisions about the structure of condition, but for the sake of brevity, we’re skipping lexing that part in this chapter.

Let’s also specify that comments are supported; specifically, a `#` begins a comment, and the comment ends at a newline. As a nice side effect, that means comments are only supported at the end of a syntactically valid line, or on their own line. This makes parsing a bit easier.

## The General Approach

### Tokens

Now that we have our DSL, how can we turn it into a list of tokens? For that matter, what is a token?

Ideally, tokens would be alternatives in a coproduct type, aka an enumerated list. There are two caveats, however:

1.  PHP doesn’t have enumerated lists.
2.  Some tokens have additional metadata they carry, such as the value of one of the “string” types like `triggerName` or `someAction`.

We can approximate enumerated lists with classes, and classes can have properties, so that’s how we represent tokens: A class with a single property.

```
1 class Token
2 {
3     public string $value;
4 
5     public function __construct(string $value = '')
6     {
7         $this->value = $value;
8     }
9 }
```

Any arguments against public properties here are entirely valid; a protected value with an accessor method would also be acceptable, but as this is largely an internal value, it’s less critical. Feel free to take a more restricted approach if you prefer.

Distinct tokens are subclasses of `Token`, but do not need or have any additional methods or properties.

### States

Our lexer is going to be a state machine. Each state represents an expectation of what the string following that state is. For instance, at the very beginning of the string, we expect the string to begin with “On” (case insensitive). If it doesn’t, that’s an error. After that, we expect the input string to contain an alphanumeric string that ends in a period. And so on.

Rather than define the entire graph in advance, we can represent each state as a function. Its input is the remaining string to parse, and its output is a product type containing one or more tokens that have been processed off of the string, the remaining string, and the next processing state; i.e., the next state function that handles the remaining string.

At first glance, the code looks like this:

```
1 class Result
2 {
3     protected string $remaining;
4 
5     protected array $tokens = [];
6 
7     protected $nextFunction;
8 }
```

Each state function then is a function from a string to a `Result`, which contains a string. That likely looks familiar by now; it’s a `bind` functor, from `string` to an “enhanced string,” where the enhancement includes a token array and a reference to a function.

However, having a reference to a function in a class seems kind of silly. We are going to have a potentially large number of them, one for each state. Besides, classes already have a way to reference functions; they’re called methods. So let’s restructure our enhanced value like so:

```
 1 abstract class Lexer
 2 {
 3     protected string $remaining;
 4 
 5     protected array $tokens = [];
 6 
 7     protected function __construct(string $remain, array $tokens)
 8     {
 9         $this->remaining = $remain;
10         $this->tokens = $tokens;
11     }
12 
13     public static function of(string $remaining): self
14     {
15         return new static($remaining, []);
16     }
17 
18     abstract public lex(string $string): Lexer;
19 }
```

Now it’s a fully-fledged monad object, and a product of (`string`, `array`, and `callable`). Because the callable `lex()` varies, we’ve made it abstract. Every state is a subclass of `Lexer` that implements `lex()` for a given state. Each of those subclasses also constitutes an Either. A Lexer is “Either” of the various defined states.

## Binding

The `bind` method is going to look a little bit different in this case. It is still passed a callable that takes a `string` and returns a `Lexer` (enhanced string), but unlike the error handling `Either` `bind` we saw before it does the same thing in each case.

```
 1 abstract class Lexer
 2 {
 3     // ...
 4 
 5     public function bind(callable $parseFn): Lexer
 6     {
 7         /** @var static $res */
 8         $res = $parseFn($this->remaining);
 9         $res->tokens = [...$this->tokens, ...$res->tokens];
10         return $res;
11     }
12 }
```

That is, it calls the state function it’s given with the remaining string, then merges the result with itself the same way as the Writer monad we saw before. What’s different is where the `$parseFn` comes from. Specifically, `$parseFn` is always `$this->lex`. While we could internalize that logic into `bind()`, that would break its monadic behavior. Instead, let’s just give ourselves a utility that does this for us.

```
 1 abstract class Lexer
 2 {
 3     // ...
 4     public static function run(string $string): self
 5     {
 6         $l = LexerStart::of($string);
 7         while (! $l instanceof Done) {
 8             $l = $l->bind([$l, 'lex']);
 9         }
10 
11         return $l;
12     }
13 }
```

It could just as easily be its own function, but a static method keeps it close to the Lexer class.

The `run()` method calls `bind()` on each state with its own state function, allowing it to process through the states, turning the string into an array of `Token` objects along the way. The line of returns from each `Lexer`/state to the next (which might be multiple possible states depending on the string) form a graph, which describes the entire state machine of our particular DSL.

We also need an end condition, lest we end up with an infinite loop. That’s what the `instanceof Done` check is for; `Done` is simply an empty marker interface on a given lexer state to indicate that the process is complete. There are two lexer states in particular that implement it: An actual `LexerDone` state when there’s nothing left to do, and an `Error` state in case the input is invalid. We’ll look at the error case in a bit, but for now, here’s the `Done` state:

```
1 class LexerDone extends Lexer implements Done
2 {
3     public function lex($string): Lexer
4     {
5         return $this;
6     }
7 }
```

This should be reminiscent of the `Error` case from the `Either` monad, as it serves a similar purpose.

To ensure we don’t end up in an infinite loop, let’s modify `bind()` so that if there is no remaining string we end up directly in the `Done` state:

```
 1 abstract class Lexer
 2 {
 3     // ...
 4 
 5     public function bind(callable $parseFn): Lexer
 6     {
 7         if (!$this->remaining) {
 8             return new LexerDone($this->remaining, $this->tokens);
 9         }
10 
11         /** @var static $res */
12         $res = $parseFn($this->remaining);
13         $res->tokens = [...$this->tokens, ...$res->tokens];
14         return $res;
15    }
16 }
```

Before we move on, let’s define some additional utilities that individual state functions use. They could be anywhere, but for convenience, let’s put them as methods on `Lexer`.

```
 1 abstract class Lexer
 2 {
 3     // ...
 4 
 5     protected function skipSpaces(string $string): string
 6     {
 7         // Don't skip newlines as those have lexical significance.
 8         return ltrim($string);
 9     }
10 
11     protected function readAlphaNumeric(string $string): string
12     {
13         $matches = [];
14         $result = preg_match('/^\w+/', $string, $matches);
15         if (empty($matches)) {
16             return '';
17         }
18         return $matches[0];
19     }
20 
21     protected function startsWith(string $string, string $needle): bool
22     {
23         return stripos($string, $needle) === 0;
24     }
25 
26     public function tokens(): array
27     {
28         return $this->tokens;
29     }
30 
31     public function remaining(): string
32     {
33         return $this->remaining;
34     }
35 }
```

`skipSpaces()` and `startsWith()` should be self-explanatory. `readAlphaNumeric()` is only slightly more interesting because it uses a regex internally. It reads and returns an alphanumeric string off of the passed string and returns it, but doesn’t modify the string being investigated.

`tokens()` and `remaining()` are just boring accessors for decomposing the product type.

## The Lexers

So far, everything we’ve written has been generic to any DSL format. While it seems involved, the entire class is less than 70 lines long. That forms the core of our lexing engine.

The rest of the code is a collection of token classes and lexer states. The token classes are empty, so we won’t bother showing them to save space. Let’s start with the one mentioned above, `LexerStart`, which is the start state of the graph:

```
 1 abstract class LexerStart extends Lexer
 2 {
 3     public function lex($string): Lexer
 4     {
 5         if ($this->startsWith('on')) {
 6             return new LexerOn(substr($string, strlen('on')), [new On()]);
 7         }
 8 
 9         return LexerError::create(
10             $string, [], sprintf('Expected "%s"', 'ON')
11         );
12    }
13 }
```

In the start state, we know that the next (first) part of the string is supposed to be the keyword “on.” If it is, we can return a new Lexer for the state where “on” has just been parsed, which we call `LexerOn`. Its internal values are the string minus the “on” keyword and the `On` token. If not, then we know the string is invalid, so it can return an error state. The error state is a `Done` state, and is otherwise uninteresting aside from having an additional message string:

```
 1 class LexerError extends Lexer implements Done
 2 {
 3     protected string $message;
 4 
 5     protected function __construct(
 6         string $remain,
 7         array $tokens,
 8         string $msg
 9     ) {
10         parent::__construct($remain, $tokens);
11         $this->message = $msg;
12     }
13 
14     public static function create(
15         string $remain,
16         array $tokens,
17         string $msg
18     ): self {
19         return new static($remain, $tokens, $msg);
20     }
21 
22     public function lex($string): Lexer
23     {
24         return $this;
25     }
26 
27     public function message(): string
28     {
29         return $this->message;
30     }
31 }
```

To be even cleaner, we could have subclasses of LexerError to indicate different failure conditions. Let’s skip that for now in the interest of brevity.

That nearly completes our start state, but if we look ahead the logic for any keyword should be virtually identical. Rather than duplicate it for each keyword, we can abstract that to an intermediary class. This isn’t a technically a functional or monadic technique but an OOP one, and it works fine in this case:

```
 1 abstract class LexerKeyword extends Lexer
 2 {
 3     protected string $keyword;
 4     protected string $token;
 5     protected string $nextState;
 6 
 7     public function lex($string): Lexer
 8     {
 9         if ($this->startsWith($string, $this->keyword)) {
10             $nextState = $this->nextState;
11             return new $nextState(
12                 substr($string, strlen($this->keyword)), 
13                 [new $this->token]
14             );
15         }
16 
17         return LexerError::create(
18             $string,
19             [],
20             sprintf('Expected "%s"', strtoupper($this->keyword))
21         );
22     }
23 }
```

Now any state that expects a keyword to be next is as simple as:

```
1 class LexerStart extends LexerKeyword
2 {
3     protected string $keyword = 'on';
4 
5     protected string $token = On::class;
6 
7     protected string $nextState = LexerOn::class;
8 }
```

Easy enough.

Now we can look at `LexerOn`, which is the state of having just consumed an “on” keyword. What’s expected next is the object on which a trigger is happening. We call that a “subject.” It’s just an alphanumeric string, of which there are several in our DSL. That means we can go ahead and make another abstracted state for when the next expected value is an identifier string:

```
 1 abstract class LexerIdentifier extends Lexer
 2 {
 3     protected string $token;
 4     protected string $nextState;
 5 
 6     public function lex($string): Lexer
 7     {
 8         $string = $this->skipSpaces($string);
 9 
10         $identifier = $this->readAlphaNumeric($string);
11 
12         if ($identifier) {
13             $remain = substr($string, strlen($identifier));
14             $nextState = $this->nextState;
15             $token = $this->token;
16             return new $nextState($remain, [new $token($identifier)]);
17         }
18 
19         return LexerError::create(
20             $string,
21             [],
22             'Expected a valid identifier.'
23         );
24     }
25 }
```

The logic should be fairly self-explanatory. It skips any whitespace, then grabs an alphanumeric string to turn into a token. Then it returns the next state, with that token added. If there’s no identifier, it returns an error state.

The specific “on” state then is trivial:

```
1 class LexerOn extends LexerIdentifier
2 {
3     protected string $token = Subject::class;
4     protected string $nextState = LexerSubject::class;
5 }
```

That is, consume an identifier string to a token of the `Subject` class, then transition to `LexerSubject`.

`LexerSubject` is the state of having just consumed a subject identifier, and the next value is supposed to be a dot. A dot is a literal, which is close enough to a keyword, so we consume it as a keyword:

```
1 class LexerSubject extends LexerKeyword
2 {
3     protected string $keyword = '.';
4     protected string $token = Dot::class;
5     protected string $nextState = LexerTriggerDot::class;
6 }
```

After a dot comes another identifier, this time for the “trigger”:

```
1 class LexerTriggerDot extends LexerIdentifier
2 {
3     protected string $token = Trigger::class;
4     protected string $nextState = LexerEndLine::class;
5 }
```

Now we get to another interesting state, that of being at the end of a line. There are multiple possibilities here for the next state.

*   It could be the actual end of a line, in which case our next state is a “start of line” of the next line.
*   It could be a comment, denoted by a `#`.
*   It could be the end of the string to parse, in which case we’re done.

Each of these cases is individually straightforward:

```
 1 class LexerEndLine extends Lexer
 2 {
 3     public function lex($string): Lexer
 4     {
 5         $string = $this->skipSpaces($string);
 6 
 7         if ($this->startsWith($string, '#')) {
 8             return new LexerCommentMarker(
 9                 substr($string, 1),
10                 [new CommentMarker()]
11             );
12         }
13 
14         if (empty($string)) {
15             return new LexerDone('', []);
16         }
17 
18         $matches = [];
19         preg_match('/^[\n\r?]+/', $string, $matches);
20         if (empty($matches)) {
21             return LexerError::create(
22                 $string,
23                 [],
24                 'Expected newline'
25             );
26         }
27 
28         $remain = substr($string, strlen($matches[0]));
29 
30         return new LexerStartLine($remain, []);
31     }
32 }
```

Note that in the case of `LexerDone` and `LexerStartLine`, there are no tokens to add. That is entirely fine; there’s no rule that every state must produce a token, just as we’ve allowed a state to produce more than one token should the need arise. The newline check also allows for both newline and newline-carriage-return end of line markers, per our spec.

That gives us two more states to consider: `LexerCommentMarker` and `LexerStartLine`.

The comment marker state needs to extract an arbitrary string, bounded by either a newline character or the end of the string. Again, that’s pretty straightforward:

```
 1 class LexerCommentMarker extends Lexer
 2 {
 3     public function lex($string): Lexer
 4     {
 5             $string = $this->skipSpaces($string);
 6             $newlinePos = strpos($string, "\n");
 7             $comment = ($newlinePos === false)
 8                 ? $string
 9                 : substr($string, 0, $newlinePos);
10 
11             $remain = substr($string, strlen($comment));
12 
13             return new LexerEndLine($remain, [new Comment($comment)]);
14    }
15 }
```

After parsing a comment, we loop back to an end-of-line state, for realsies this time. That’s entirely valid; the “Are we done yet?” logic lives there, so it makes sense to move back to that state after having added a `Comment` token to the list.

We’re nearly done; there are only two more interesting states to consider, and we said above we’re going to skip dealing with conditionals right now as they’re a little too interesting. The other interesting state is `LexerStartLine`, which is another branching state; a line could start with “if” or “action”, so we handle both. Both are simple keywords, so the code is nice and simple:

```
 1 class LexerStartLine extends Lexer
 2 {
 3     public function lex($string): Lexer
 4     {
 5         $string = $this->skipSpaces($string);
 6 
 7         if ($this->startsWith($string, 'if')) {
 8             return new LexerIf(substr($string, 2), [new IfToken()]);
 9         }
10         if ($this->startsWith($string, 'action')) {
11             return new LexerAction(substr($string, 6), [new Action()]);
12         }
13 
14         return LexerError::create(
15             $string,
16             [],
17             'Expected one of "If" or "Action"'
18         );
19     }
20 }
```

It could be generalized even further for a generic “one of multiple keywords” state function, but let’s call it good enough for now. Also, we’re naming our `If` token class `IfToken` instead of `If` because `if` is a reserved word in PHP. Oh well.

Since we’re not handling conditionals for now, `LexerIf` can be just a stub:

```
1 class LexerIf extends Lexer
2 {
3     public function lex($string): Lexer
4     {
5         return new LexerDone('', []);
6         // TODO: Implement lex() method.
7     }
8 }
```

`LexerAction`, meanwhile, expects to be followed by an identifier so we can once again use the identifier base class:

```
1 class LexerAction extends LexerIdentifier
2 {
3     protected string $token = ActionName::class;
4     protected string $nextState = LexerEndLine::class;
5 }
```

Which loops back around to `LexerEndLine`, which we already implemented.

## Testing

That seems like a lot of code. Each of the individual pieces, though, is very simple. In fact, it’s almost trivial to unit test. The actual lexing is done by the `lex()` state functors, which are themselves pure functions: They take a string and return an object. While we need to first instantiate the state object they’re on in order to test them, the `lex()` method itself doesn’t read any internal state. Testing pure functions is the easiest kind of testing.

Since we have a lot of `lex()` methods to test, we can make a utility base class to help with that. Assuming we’re testing with PHPUnit, we can start like so:

```
 1 abstract class StateTest extends TestCase
 2 {
 3     /**
 4      * @dataProvider lexerProvider
 5      */
 6     public function test_state(
 7         string $input,
 8         string $nextState,
 9         string $remain,
10         array $expectedTokens
11     ): void
12     {
13         $class = $this->startState();
14 
15         /** @var Lexer $state */
16         $state = $class::of('');
17 
18         $result = $state->lex($input);
19 
20         $this->assertInstanceOf($nextState, $result);
21 
22         $this->assertEquals($remain, $result->remaining());
23 
24         $foundTokens = $result->tokens();
25         foreach ($expectedTokens as $i => $expected) {
26             $this->assertInstanceOf(
27                 get_class($expected),
28                 $foundTokens[$i]
29             );
30             $this->assertEquals(
31                 $expected->value,
32                 $foundTokens[$i]->value
33             );
34         }
35     }
36 
37     abstract function startState(): string;
38 
39     abstract function lexerProvider(): iterable;
40 }
```

We’re using a data provider to minimize boilerplate. For each set of input string, and expected bits of the result, we lex the string, then make sure the value we got back is the expected next state. Then we ensure that the tokens, if any, are the ones we expected.

Let’s look at the test class for `LexerStartLine` as an example:

```
 1 class LexerStartLineTest extends StateTest
 2 {
 3     function startState(): string
 4     {
 5         return LexerStartLine::class;
 6     }
 7 
 8     function lexerProvider(): iterable
 9     {
10         yield ['if foo', LexerIf::class, ' foo', [new IfToken()]];
11         yield [' if foo', LexerIf::class, ' foo', [new IfToken()]];
12         yield ['beep beep', LexerError::class, 'beep beep', []];
13         yield ['Action bonk', LexerAction::class, ' bonk', [new Action()]];
14     }
15 }
```

Simplicity itself! `startState()` says we’re testing `LexerStartLine`. `lexerProvider` returns a series of test strings and the expected decomposed result. Any data we want to throw at it can now be trivially tested with ease.

A similar approach would work for integration tests on the whole Lexer pipeline itself, calling `Lexer::run()`.

```
 1 class LexerTest extends TestCase
 2 {
 3     /**
 4      * @dataProvider lexerProvider
 5      */
 6     public function test_lexing(
 7         string $string,
 8         string $endState,
 9         array $expectedTokens
10     ): void
11     {
12         $l = Lexer::run($string);
13 
14         $this->assertInstanceOf($endState, $l);
15 
16         $foundTokens = $l->tokens();
17         foreach ($expectedTokens as $i => $expected) {
18             $this->assertInstanceOf(
19                 get_class($expected),
20                 $foundTokens[$i]
21             );
22             $this->assertEquals(
23                 $expected->value,
24                 $foundTokens[$i]->value
25             );
26         }
27     }
28 
29     public function lexerProvider(): iterable
30     {
31         // Add as many test sets as desired here.
32 
33         yield ['On foo.bar', LexerDone::class, [
34             new On(),
35             new Subject('foo'),
36             new Dot(),
37             new Trigger('bar'),
38         ]];
39    }
40 }
```

## Analysis

This has been a long chapter, but it’s largely been the same pattern repeating over and over again. Let’s review the core of our lexer:

*   We’re using a product type, `Lexer`, which enhances a string into a string, token list, and callable.
*   We’re using a Writer monad design to build up the token list.
*   We’re using an Either monad design to handle different lexer states.
*   We’ve built a purely functional state machine.
*   We’re leveraging common object-oriented techniques alongside good functional programming techniques.
*   We’ve done it in a way that is simple and straightforward to cleanly unit test.
*   We’ve done it in less than 70 lines of core code.

That’s pretty impressive. We can be even more impressive, though, with two small additions to help this solution scale.

## Being Lazy

In its current form, our lexer builds up a long list of token objects and is not complete until it’s produced all of them. In our simple case, that’s fine; there won’t be more than 20-30 tokens at a time. However, it’s entirely plausible to have a DSL that supports much longer token streams, long enough that having them all in memory at once might be prohibitive. For instance, we may want to process them in a stream rather than build an AST in memory. Or we could be using the same technique as here to process an incoming stream of data into more robust objects than simple tokens. In either case, we want to process each step one at a time rather than all at once.

The normal answer, in that case, is to use a generator to lazily produce values that can be iterated over. As written, though, each step produces an increasing list of token values. Can that be converted into a lazy stream instead?

It turns out it can, and it can be done without modifying any of the individual state functors. In fact, it can be done without modifying any existing code, just providing slightly alternate versions of `bind()` and `run()`.

First, the current version of `bind()` is what smushes the token lists together as a way to combine the two functors. So… let’s not do that. Here’s a lazy version that is identical aside from that one line:

```
 1 abstract class Lexer
 2 {
 3     // ...
 4 
 5     public function lazyBind(callable $parseFn): Lexer
 6     {
 7         if (!$this->remaining) {
 8             return new LexerDone($this->remaining, $this->tokens);
 9         }
10 
11         /** @var static $res */
12         $res = $parseFn($this->remaining);
13         return $res;
14     }
15 }
```

This is entirely legal; it’s just a different monoid operation between `$this` and `$parseFn`.

Next, we need to `yield` the tokens from each step from a generator. That’s nearly the same as `run()`:

```
 1 abstract class Lexer
 2 {
 3     // ...
 4 
 5     public static function lazy(string $string): \Generator
 6     {
 7         $l = LexerStart::of($string);
 8         while (! $l instanceof Done) {
 9             $l = $l->lazyBind([$l, 'lex']);
10             yield from $l->tokens();
11         }
12 
13         return $l;
14     }
15 }
```

And we’re done. `lazy()` produces a generator that `yield`s each lexer state object’s tokens, then returns the last state object; that is an instance of `Done`, either `LexerDone` or `LexerError`, that can be examined. Because the individual states are all just simple functors, with no knowledge of the iteration, the monad, or anything else, they still work exactly as before. We can even reuse the same data provider for testing `lazy()`:

```
 1 class LexerTest extends TestCase
 2 {
 3     /**
 4      * @dataProvider lexerProvider
 5      */
 6     public function test_lazy_lexing(
 7         string $string,
 8         string $endState,
 9         array $expectedTokens
10     ): void
11     {
12         $tokens = Lexer::lazy($string);
13 
14         $tokenProducer = function() use ($tokens) {
15             foreach ($tokens as $token) {
16                 yield $token;
17             }
18         };
19         $foundTokens = iterator_to_array($tokenProducer());
20 
21         foreach ($expectedTokens as $i => $expected) {
22             $this->assertInstanceOf(
23                 get_class($expected),
24                 $foundTokens[$i]
25             );
26             $this->assertEquals(
27                 $expected->value,
28                 $foundTokens[$i]->value
29             );
30         }
31 
32         $end = $tokens->getReturn();
33 
34         $this->assertInstanceOf($endState, $end);
35     }
36 }
```

And now, we have a fully tested lazy purely functional monadic state machine, which is worth at least triple points in software Scrabble.

# Part Four

# Features of Functional Languages

So far, we’ve discussed functional programming in the context of PHP. PHP is, of course, not the ideal language for functional programming, as its syntax doesn’t always make functional techniques easy or pretty. Many other languages, however, do have features that make functional programming more natural. When developers tout the virtues of functional programming, often what they are really raving about are language features that are commonly found in functional languages.

As the saying goes, “programming languages teach you to not want features they don’t have.” Some of these features may seem odd at first, especially if you’ve never worked in a language other than PHP. However, all of them have been implemented in, and successfully used in, many other languages, making them worth understanding, if only to better understand what functional programming can enable.

Not all of these features would be possible in PHP, nor make sense. I still present them in the interests of better understanding functional programming as a concept and practice.

## Auto-Currying

As discussed previously, any pure function can be curried to a function of fewer parameters. In most languages that can be done manually. In Haskell or F#, however, it is the default behavior of all functions.

In Haskell, for instance, the following function:

```
1 add :: Integer -> Integer -> Integer
2 add x y =  x + y
```

defines a function named “add” that is of type “Integer -> Integer -> Integer”. That can be read equally correctly as “a function that takes two integers and returns an integer” or “a function that takes one integer and returns a function that takes one integer and returns an integer.” That is, it can be parenthesized as either of the following:

```
1 add :: (Integer -> Integer) -> Integer
2 
3 add :: Integer -> (Integer -> Integer)
```

That has two key implications. One, as a developer you can curry any function by simply calling it with fewer than the required number of parameters. Two, both the developer and the engine are able to use whichever interpretation is most convenient at the time. That can lead to some very elegant functional syntax, once you know how to recognize it. If you don’t know to look for it, it can lead to Haskell’s famous incomprehensibility to people who aren’t comfortable with Haskell.

It’s extraordinarily unlikely that such functionality would even be possible in PHP.

## Recursion Optimization

Many recursive algorithms have an iterative equivalent that is isomorphic to it but doesn’t suffer from a deep stack trace. Some languages have the ability to detect recursive calls and refactor them during the compilation step into an iterative version, as a performance optimization.

Doing that generically is hard, except in the case of tail recursion. Tail recursion is when the recursive call is the very last statement in the function. For instance:

```
1 function addUp(int $x, int $sum = 0): int
2 {
3     if ($x == 0) return $sum;
4     return addUp($x - 1, $sum + $x);
5 }
```

The typical factorial implementation, however, is not tail recursion since the last statement is multiplication, not the call to `factorial()`:

```
1 function factorial(int $x): int
2 {
3     if ($x == 1) return $x;
4     return $x * factorial($x - 1);
5 }
```

A number of languages support tail recursion optimization. PHP does not. The main question is whether recursion optimization can be done in a reasonable amount of time to not slow down the generation of opcodes.

## Isomorphic Optimization

It’s quite common for functional-style code to have more function calls in it; every `map()` call implies a function call for each item in the list, for instance, and a `bind()` call implies two function calls for each step in a chain. Depending on the language that may involve a non-trivial performance hit, including in PHP.

If a compiler can know reliably it’s safe to do so, it can reorganize code from a more readable, functional form into a more performant procedural form. For instance, a series of Maybe monads is isomorphic to an `is_null` pyramid of doom. That’s why we know it’s safe to write code in the monadic way that ends up being much easier to read, debug, and maintain. However, that has a performance cost. If the compiler could safely convert a series of `Optional`s back into an `is_null` pyramid of doom, that could entirely eliminate the cost of the monad wrapper.

This sort of optimization can lead to what’s called in the Rust world “zero-cost abstractions,” where the abstraction improves readability but gets optimized out of existence before the code actually runs.

It’s unlikely PHP will ever be able to do much here, unfortunately. Aside from the performance cost of the optimization itself, it’s only safe for the compiler to go around rearranging your code if it can be very, very sure of what your code is doing. That generally requires guaranteed pure functions and a strong type system, neither of which PHP has. Guaranteed pure functions are unlikely to ever be an engine-level feature of PHP, and there wouldn’t be much benefit to adding them without also including such optimizations.

## Function Composition

One optimization that could be made is around function composition. We saw before that it’s simple enough to write a `compose()` function in user-space:

```
 1 function compose(callable ...$fns): callable
 2 {
 3     return function($x) use ($fns) {
 4         $ret = $x;
 5         foreach ($fns as $fn) {
 6             $x = $fn($x);
 7         }
 8         return $ret;
 9     };
10 }
```

Or even a single line recursive function with reduce. However, that adds overhead to every function call, especially if several of them have to be curried first. However, to use our example from that chapter, this:

```
1 getPromotions(mostExpensiveItem(getShoppingList(getCurrentUser(), 'wishlist'), [
2     'exclude' => 'onSale'
3 ]), $holiday);
```

is isomorphic to this, which is cleaner to read and maintain:

```
1 $holiday = "Lincoln's Birthday";
2 $findPromotionsFor = compose(
3     fn($x) => getShoppingList($x, 'wishlist'),
4     fn($x) => mostExpensiveItem($x, ['exclude' => 'onSale']),
5     fn($x) => getPromotions($x, $holiday),
6 );
```

A language-native way to concatenate functions would eliminate the user-space overhead, as well as offer more optimization options for the engine, as well as offer a nicer syntax.

For instance, F# (among many other languages, including Facebook’s PHP fork, Hack) has a pipeline operator `|>` that brings the `compose()` function down to the syntax level. In F#, the above example could be written (also taking advantage of auto-currying) as:

```
1 promos = getCurrentUser
2     |> getShoppingList
3     |> mostExpensiveItem onSale
4     |> getPromotions "Lincoln's Birthday"
```

While auto-currying isn’t going to be a feature of PHP anytime soon, there’s no conceptual reason that a pipeline operator couldn’t be. Now that short lambdas make currying any function to single-parameter so easy, there’s little reason not to add it.

One caveat is that most pipeline operator implementations call immediately. That is, the above code would execute `getCurrentUser`, `getShoppingList`, `mostExpensiveItem`, and `getPromotions`, returning the return value from `getPromotions`. That’s different from our `compose()` method, which returns a callable to be used later. Fortunately short lambdas would make that easy enough to wrap just once:

```
1 $finder = fn($x) => $x |> 'getShoppingList' |> 'mostExpensiveItem' |> 'getPromotions\
2 ';
```

## Function Naming

As suggested by the last example, another weakness of PHP in terms of functional programming is simply referring to functions. Because functions in PHP are not truly first-class values, they cannot be referenced as easily as variables. They need to be quoted, and if a function is in a namespace, the string that represents their name must include the full namespace. That can lead to ugly messes like:

```
1 array_map('\foo\bar\baz\compute_stuff', $list);
2 
3 // or sometimes
4 
5 array_map(__NAMESPACE__ . '\compute_stuff', $list);
```

Bare unquoted strings in PHP have traditionally been evaluated to strings with a notice; in PHP 7.2 that became a warning, but they’ve not been removed entirely yet. That precludes referring to functions directly without quotes. Within quotes, of course, functions are completely hidden from refactoring tools.

One possibility that has been discussed is allowing for a function name to have a class-constant-like suffix to refer to its name. That is, something like the following:

```
1 use foo\bar\baz\compute_stuff;
2 
3 array_map(compute_stuff::name, $list);
```

That would not be ideal, compared to what most functional languages offer, but it would be a major improvement over the status quo. Regardless of the approach, though, some better way to refer to functions as first-class values without actually invoking them would greatly improve PHP’s potential as a functional language.

## Generics

PHP has made great strides in recent years in terms of its type system. While still entirely opt-in, the language has been steadily adding to its ability to make explicit the type of values being passed around. Yet much of the code samples in this book have omitted types almost entirely. Why is that?

The bottom line is that for all its improvements, PHP’s type system is still relatively weak compared to many other languages. In particular, it lacks *generics*, also known as “parametric types.” With generics, one can define a type in terms of another type, such as “an `Optional` that contains a `string`” or “an `Optional` that contains a `User` object.” The “that contains” part is deferred to call time. In a hypothetical world where PHP had generics using the same syntax style as C++ and Java, the `Optional` class might look something like the following (abbreviated):

```
 1 class Optional<T>
 2 {
 3     private T $value;
 4 
 5     public static function of(T $value = null)
 6     {
 7         $this->value = $value;
 8     }
 9 
10     public function value(): T
11     {
12         return $this->valid() 
13             ? $this->value 
14             : throw new \RuntimeException("The cat is dead, Schrodinger");
15     }
16 }
17 
18 function getShoppingList(User $u, string $list = 'main'): Optional<ShoppingList>
19 {
20     isset($u->lists[$list])
21         ? Some<ShoppingList>::of($u->lists[$list])
22         : None::none();
23 }
```

In essence, by writing `Optional` in a “generic” way, it can have the extra type `T` defined by the caller when it’s instantiated. That is, `Optional<ShoppingList>` is “an `Optional` wrapped around a `ShoppingList`.” The same `Optional` class can be used for any wrapped type. In one sense, it creates a subclass of `Optional` that fills in `ShoppingList` for `T` on the fly as needed.

Generics would make type-safe monad-based error handling vastly easier.

Another natural use for generics is collections. As of PHP 7.4, neither arrays nor other `iterable` types can be locked down to contain only a specific type. Doing so requires a custom class for each variable type to be wrapped, or else manual `instanceof` checks. Generics would allow for easily declaring “list of type X” variables.

Many people have been pushing for generics in PHP for some time, and it would be the next logical major improvement to the type system. Unfortunately, it also has a lot of edge cases and performance issues to consider, which is largely what has prevented it to date. Hopefully, in the future it will be possible.

## Callable Types

Another major gap in PHP’s type system found in more functional languages is the ability to type a callable. Currently, when typing a parameter or return value it can be typed only as `callable`, meaning any of PHP’s myriad of ways to define a thing you can put `()` after. There’s no way to specify an interface for it. It is possible to define an `__invoke()` method in an interface.

```
1 interface UserFinder
2 {
3     public function __invoke(int $id): User
4 }
```

But that cannot be enforced without specifying `UserFinder` as the parameter or return type, which then precludes using an anonymous function or global function.

There are two ways that callable types could be implemented. One is pre-defining a type and referencing it:

```
1 callable UserFinder(int $id): User;
2 
3 function foo(UserFinder $fn) { ... }
```

While the other would specify the callable syntax inline:

```
1 function foo(callable(int): User $fn) { ... }
```

There’s decent arguments for either approach, and they wouldn’t necessarily be incompatible, either. Either one would be a big boost to PHP’s functional programming support.

## Comprehensions

*Comprehensions* are a way to represent a list in terms of another list by describing its relationship, rather than building a new list explicitly. For instance, “list A is twice list B” or “list A is list B but without the negative numbers.” If that sounds a lot like map and filter, that’s because those two operations allow nearly any list comprehension.

The syntax for comprehensions varies widely from language to language. For example, the following Python code creates a list named `squares` where each element is the value from the list `range(10)`, multiplied by itself:

```
1 squares = [x**2 for x in range(10)]
```

Which would be equivalent to this PHP:

```
1 $squares = [];
2 foreach (range(1, 10) as $x) {
3     $squares[] = $x * $x;
4 }
```

More involved examples are also possible. for instance:

```
1 employees = [emp.name for m in managers if m.dept="sales" for emp in m.reports]
```

That Python comprehension builds a list of the names of all employees who report to a manager in the sales department, equivalent to this PHP code:

```
1 $employees = [];
2 foreach ($managers as $m) {
3     if ($m->department = "shipping") {
4         foreach ($m->reports as $employee) {
5             $employees[] = $employee->name;
6         }
7     }
8 }
```

Comprehensions can be either greedy (meaning they create the new list immediately) or lazy (meaning they create the new list on-demand as it is iterated). The latter makes it possible to work with infinite lists in a very natural fashion.

Haskell of course has strong comprehension support, and everything in Haskell is lazy:

```
1 squares = [x * x | x <- [0...10], x * x > 5]
```

Which can be read as “x times itself, where x is drawn from the list 0 through 10, on condition that x \* x is greater than 5.”

C# supports comprehensions via a custom syntax that is designed to look very much like SQL, called LINQ (Language INtegrated Query):

```
1 var ns = from x in Enumerable.Range(0, 100)
2         where x * x > 3
3         select x * 2;
```

Which is an alternate syntax for the equally valid:

```
1 var ns = Enumerable.Range(0, 100)
2         .Where(x => x * x > 3)
3         .Select(x => x * 2);
```

The latter is essentially what “collection objects” look like in PHP today, with short lambdas. `Where` is `filter` and `Select` is `map`.

There’s no conceptual reason why PHP couldn’t support lazy comprehensions, using either the Python/Haskell style syntax or something LINQ-like. No one’s implemented it yet. They would, however, greatly improve PHP’s ability to be written in a declarative fashion.

## Integrated Optionals

The Optional or Maybe monad is far and away the most common, in part because it’s so simple, and in part because dangling nulls is one of the great evils of programming languages; the “Billion Dollar Mistake” as the inventor of the null pointer, Tony Hoare, once called it. Many newer languages, therefore, have built-in ways to make a variable optional, meaning it gets wrapped into a Maybe monad automatically by the language.

We saw earlier that Rust uses an enumerated `Result` type that can be `Some` (which wraps a value) or `None` (which is nothing), which forces you to consider the null case without having an actual null. Other languages go a step further and encapsulate the optional concept into the syntax itself.

For example, in Swift, a variable must have a value unless it’s declared optional:

```
1 var name:String?
```

The `?` means that the variable may be null, which means it cannot be accessed without “unwrapping” it, using a `!`.

```
1 if name != null {
2     print("Hello, \(name!)")
3 } else {
4     print("Wait, who are you again?")
5 }
```

The `?` is effectively a syntactic Maybe Monad “unit” operation, and `!` is a syntactic `getValue()` or `unwrap()`. The end result is the same: Forcing a developer to handle the case when a value may be missing rather than letting them forget, as we are so prone to do.

Such a change would likely be impractical in PHP today; nullable variables have no built-in guards, and adding them would be a huge breaking change. A Rust-style approach with an explicit wrapper would be more feasible.

## Optional Chaining

Another feature that integrated optionals allows for is optional chaining. That is, dereferencing a variable that may be null without actually dereferencing it if it is null. Which… is exactly the same behavior as the Maybe monad’s `bind` operation.

Consider this Swift example:

```
1 class Employee {
2     var name: String
3     var title: String
4     var manager: Employee?
5 }
```

In this class, `name` and `title` are both required, but `manager` is optional. You can access the manager’s name like so:

```
1 let e = Employee();
2 // ...
3 var boss = e.manager?.name;
```

If `e.manager` is defined, that object’s `name` property is returned. If it’s null, then the entire rest of the chain is skipped, and `boss` is set to null (and thus has type `String?`, so it must be unwrapped to be used). Any number of values in a chain may be optionaled.

There’s no conceptual reason why PHP couldn’t support such a syntax, and it’s been proposed in the past:

```
1 $boss = $e->getManager()?->name;
```

That would, in practice, be syntactic sugar for the same `is_null` pyramid of doom that the Maybe monad encapsulates.

That said, I am not convinced this is a good approach. While it has its uses, a null return frequently means an error, not a single “normal” case like “user not found.” In that case, some way to bake in a syntactic version of `Either` rather than `Maybe` would be more flexible and allow for multiple error types to be returned. What that would look like in practice I’m not sure, but it would essentially be a functional, return-based version of exceptions (albeit only one level deep).

## A Native Bind Operator

Highly functional languages like Haskell or F# often have a native operator for monad binding. Since monads are really just “fancy concatenation,” from a programmer’s point of view, they have a concatenation-like operator. For instance, in Haskell one can write:

```
1 promos = getCurrentUser
2     >>= getShoppingList
3     >>= mostExpensiveItem onSale
4     >>= getPromotions "Lincoln's Birthday"
```

where `>>=` is the Haskell operator for “bind,” assuming a type-appropriate bind function has already been defined. The caveat is that the language needs some way to tell which bind operation to use, which is, in turn, derived from the type of each function. That is easy to do in Haskell with its extremely robust type system and a separate compile-time step. In PHP, with its relatively weak type system and the need for fast opcode-generation times, that becomes substantially harder. It would likely require function pattern-matching logic to be built into the engine, something PHP has long avoided for various reasons (mostly relating to it being a bad idea in combination with a weak type system). It would probably not be impossible to implement, but it’s likely very hard.

## Enumerated Types

While it is possible to create an enumerated structure in use space in PHP, it still would have no type system support. *Enumerated types*, which are the manifestation of coproduct types but in code, would allow for the creation of a closed list of legal values for a type. That, in turn, makes some monadic patterns (such as Either) easier to represent, especially if combined with generics.

For example, in Haskell an enumerated type is as simple as:

```
1 datatype cardsuit = Clubs | Diamonds | Hearts | Spades
```

And now, a variable of type `cardsuit` may only be one of those four values. When combined with generics, the Maybe monad can be expressed in Haskell as simply:

```
1 data Maybe a = Nothing | Just a
```

That’s way less work than the classes we had to build in PHP!

In C or C++, enumerated types are a shorthand over primitive types like integers. For instance, this C code:

```
1 enum cardsuit {
2     Clubs,
3     Diamonds,
4     Hearts,
5     Spades
6 };
```

is simply shorthand for:

```
1 enum cardsuit {
2     Clubs    = 0,
3     Diamonds = 1,
4     Hearts   = 2,
5     Spades   = 3
6 };
```

And printing out “Hearts” would yield the integer value 2. In other languages, such as Haskell and Java, enumerated types have no intrinsic primitive value. There are pros and cons to both approaches.

A fancier version of enumerations, called *tagged unions*, allows a type to be one of a specific set of other types, which themselves could be compound types. For instance, in Rust:

```
1 enum Message {
2     Quit,
3     Move { x: i32, y: i32 }, // anonymous struct
4     Write(String),
5     ChangeColor(i32, i32, i32),
6 }
```

The type `Message` is now defined as “an instance of `Quit`, OR an instance of `Move` which has two properties, OR an instance of `Write` which has one property, OR an instance of `ChangeColor` which has three properties.” It is similar to a marker interface, in a sense, except that the list of legal values can be made closed rather than infinite.

The main question for enumerations in PHP is which model to adopt; there is no technical reason they couldn’t be done at this point.

# When to Go Functional

Throughout this book, we have sought to demonstrate how a functional approach to code works: What the principles of functional programming are, what their implications can be, and the approaches they enable. That led, in turn, to an exploration of the mathematics behind functional programming, and some practical examples of taking a functional, monad-based approach to problem solving.

That’s great for understanding what all the fuss is about in natively functional languages. But PHP lacks some of the finishing touches that make such approaches really and truly powerful. It also lacks the lazy evaluation of a language like Haskell, which means that, in practice, no useful PHP program can be purely functional because then it couldn’t do input or output, which would make it kind of silly. A purely functional PHP program is, in fact, impossible.

Of course, the same is true of virtually every language that claims to be functional. If it can’t have impurity (reading from input, writing to output), then it’s not a useful language. Different functional languages or strictly functional languages address that challenge in different ways. Being a not-functional language (no pun intended), PHP’s approach to that problem, at a language level, is to simply not care.

A PHP program can be as functional as you want to make it. The principles of functional-style programming can all be used in PHP, to varying degrees, quite successfully. Some are applicable in almost any situation, others only in certain contexts. It’s up to the individual developer to decide when they apply, and how. There is no One True Way^(tm) to write functional-style PHP code.

As guidelines, I would offer the following recommendations. They are, as stated, recommendations, and there will be contexts and situations in which every single one of them does not apply. Still, the following mindset, I would argue, will serve developers well in the long term.

These recommendations are listed in roughly their order of decreasing universality (that is, how often you should try to apply them).

## Avoid Global State

While most modern PHP code does a pretty good job on this front, not all does, and there is ample legacy code that was written in the dark times when developers thought global variables were a good way to manage state throughout a request. It was never a good way, but every generation of developers must re-learn certain hard lessons. Global state is the death of purity, and without pure functions, there is no functional programming.

In short, pretend that PHP’s `global` keyword and the `$GLOBALS` super-global variable do not exist. Erase them from your mind. Moreover, never access PHP’s input superglobals except from a single location to convert them into a better, non-global data structure. Your code will thank you.

All that seems easy; however, there is a more pernicious form of global state that is still in widespread use: stateful service entries. While the trend has turned against that in recent years, there are still applications with service containers whose services retain meaningful state. That is still a global variable, even if it does not use a `global` keyword. If the order in which other functions or services call a service ends up mattering to those other services, then your service is impure.

That is especially true for pseudo-services; some frameworks, for instance, still store an object representing the HTTP request in a dependency injection container, or accessible through the container in some way. And that request object is often mutable. Be careful; that is now a global variable, and thus anything it touches is no longer reliably a pure function.

There is a slight exception for memoization. Memoizing the output of a service is technically maintaining state, but it is maintaining state in an idempotent way. That makes it mostly safe, as long as you’re not memoizing output that relies on stateful data (such as a database lookup). But be judicious with it; don’t just memoize everything by default. Wait to see if profiling says it would be useful. If it is, make the memoization its own routine rather than baking it into the code being memoized. For example, if you have a service you want to memoize, write a separate object that implements the same interface and wraps your service that does nothing but cache the output. That makes the code much easier to conceptualize, understand, read, and test. Interweaving caching logic into business logic is a surefire way to make both harder to comprehend.

## Make Pure Functions

If you take nothing else away from this book, make it this: Make your code pure whenever possible, and if it seems impossible, try to make it pure anyway before giving up. Pure functions are the foundation of functional programming, and all by themselves offer massive benefits for readability, testability, even performance. Pure functions are trivially memoizable (if necessary), simple to reuse in another context and adapt to other contexts.

Note that by “function,” I don’t mean just stand-alone functions. Methods are, as we discussed, simply a function that is closed over the object’s state. They can and should be treated the same way. That is, methods should maintain no state of their own, and the state of the object they are on should never change. Most methods can be easily made idempotent with just a little bit of thought and refactoring, and the more you do so, the easier it becomes.

## Isolate IO

The most pernicious form of state and impurity is input and output from your program. You cannot avoid it, only contain it. So, try to contain it.

Any piece of code that interacts with the outside world is inherently impure, and that means any code that calls it is inherently impure. The more you can confine your IO to a specific part of the codebase, the less it can pollute the rest of your application.

The best guidance I’ve found for how to do that is “functional core, imperative shell,” a term and technique coined by Gary Bernhart in a presentation by the same name (See the reference in “Further Reading”). Although his talk is in Ruby, the concept applies generally. The basic concept is that the impure, IO-containing, ugly part of the application should be on the “outside,” where it touches the rest of the world. It forms the basic flow of input and output but does virtually nothing else. Everything else is handed off to other routines that obey functional principles strictly. That makes those parts easily testable and easy to develop against and keeps the hard to test, stateful, ugly bits separate.

If that sounds familiar, the famous “hexagonal architecture” (which is a bad marketing name since the concept has nothing to do with hexagons or even the number six at all) boils down to almost the same concept: Put your clean and important bits on the inside and your ugly world-touching bits on the outside, and don’t let them taint each other.

In PHP, this would largely manifest itself as keeping the request and response objects as far away from the business logical as possible. It also means whatever database lookups are needed for a given request should be done early, while the request handling is still being set up, so that the main logic routines are fed not just their service dependencies but their data dependencies, too.

## List Application

When working with lists of data, it’s natural for most PHP developers to first reach for a `foreach()` loop. That’s been the PHP go-to tool for iterating over a list for 20 years, and it certainly gets the job done.

However, when approaching a problem that involves multiple similar values, try to avoid that habit. Instead, think in terms of function application through map, filter, and reduce. Whether you use the built-in `array_map()`, `array_filter()`, and `array_reduce()` functions or write your own is irrelevant; use whatever gets the job done. However, leveraging those operations lets you separate out your actions from your iteration. It lets you think and code more declaratively, which can make the code easier to reason about as well as test.

That doesn’t necessarily mean inlining all of your application functions. On the contrary, a good heuristic is that if they’re too long to put into a short-lambda, they should be their own function or method in the first place. That’s fine, and they can still be used just as easily but now in a testable fashion.

Over time, you’ll find that thinking declaratively helps to conceptualize the problem space differently, at a higher level, where you can think without being distracted by implementation details.

## Embrace Value Objects

The other core pillar of functional programming is immutable values. While building proper value objects in PHP sometimes takes a bit of work, it pays off enormously in the amount of “spooky action at a distance” you can avoid. As with other aspects of functional programming, it can take some time to get used to, but once you get used to it your life will be a lot easier (and more testable).

In particular, this means embracing “skinny objects”: Value objects that have little business logic of their own other than enforcing data integrity. An object that contains data should never, ever have a dependency on a service object, or auxiliary logic object. Its constructor should be concerned only with its own data and nothing else.

Yes, that does go against traditional OOP dogma, in which objects form a complex network of interacting agents. That’s because it’s a functional approach, not an OOP approach. And, given PHP’s shared-nothing, stateless runtime model, that way of designing objects tends to work better in practice anyway as the setup for it is much, much simpler.

Additionally, for value objects that you can guarantee are internal to your library or module, don’t sweat property access as much. If the object is purely for internal use, and it seems wasteful to build getters and setters that do nothing but wrap private properties, skip them and use a public property instead. From a functional point of view, that’s fine. (That applies only for strictly internal implementation detail objects, however. For objects that form your API, the usual encapsulation practices still apply.)

## Embrace Functions as Values

Don’t think of functions (or any other callable, really) as stand-alone, immutable, set-in-stone things. Rather, a function is a value. You can create one as easily as any other value, pass it around as a value, and use it as a value. You can have function-values that produce function-values if the situation calls for it.

Certainly, it is possible to create a horrible mess that way if you’re not careful. Inlining multiple nested callbacks, for instance, is a proven terrible idea. However, adapting a function that expects one interface (say, multiple parameters) to one that wants a different interface (a single parameter, or even no parameters) using a closure should be a natural part of your workflow. As with any other technique, it can be used wisely to produce very readable code or badly to produce spaghetti code.

## Make Single-Method Callable Services

As previously observed, a service object with only a single public method is isomorphic to (effectively the same thing as) a free-standing function that is closed over some of its parameters. If you have a service with only a single method, don’t bother naming it. Just use the `__invoke()` method. The object now becomes usable exactly like a function: Stick `()` after it to call the `__invoke()` method. Referencing that method as a callable becomes easier as well, since there’s no screwy array syntax needed; just the variable name of the object is sufficient.

That may look weird at first, but after a while, it should start to feel even more natural, to the point you may start restructuring your services to be single-method more often. This is especially true for things like controller actions, command objects, and other objects designed to have a single “do the thing” method; just use `__invoke()` for that.

## Think in Terms of Pipelines and Data Flow

Object-oriented thinking traditionally encourages you to think of objects as a connected graph of persistent things, like neurons in a network. Functional programming encourages you to think of your application as a series of stateless pipelines through which data flows, changing shape as it goes and possibly branching or merging between different pipelines.

That pipeline metaphor is a far better fit for the typical PHP HTTP application than the persistent connected network because that’s what a PHP application is. It takes in an HTTP request message (in whatever form), runs that through a series of operations, and produces a response message (in whatever form) at the other end, after which everything shuts down. That is, conceptually, a function, and can be composed of smaller functions.

Whether those functions are syntactically free-standing functions or methods of an immutable service is an implementation detail. Stateless service objects are likely more familiar to most PHP developers, but in some cases, a pure-function approach may be easier to read and maintain. Using good judgment here case-by-case is the best approach.

However, that also means explicitly composing pipelines rather than having deep method call chains. Many library routines have code that says essentially “do this, then do this, then do this, then do this.” That’s a perfectly reasonable approach conceptually, but the various “this” actions are often methods on disparate objects stitched together through dependency injection. That can obfuscate the actual business logic by spreading it out across a lot of different classes.

Instead, consider building each of those steps as its own callable (be it a method of a service, a function, or a service that uses `__invoke()`) and then gluing them together using `compose()`. That style encourages creating discrete, reusable, testable components, and makes the logic flow between them much more obvious.

Compare:

```
 1 function A($value)
 2 {
 3     // ...
 4     return B($modified_value);
 5 }
 6 
 7 function B($value)
 8 {
 9     // ...
10     return C($modified_value);
11 }
12 
13 function C($value)
14 {
15     // ...
16     return D($modified_value);
17 }
18 
19 function D($value)
20 {
21     // ...
22     return $computed_value;
23 }
24 
25 $val = A($value);
```

with:

```
 1 function A($value)
 2 {
 3     // ...
 4     return $modified_value;
 5 }
 6 
 7 function B($value)
 8 {
 9     // ...
10     return $modified_value;
11 }
12 
13 function C($value)
14 {
15     // ...
16     return $modified_value;
17 }
18 
19 function D($value)
20 {
21     // ...
22     return $modified_value;
23 }
24 
25 $f = compose('A', 'B', 'C', 'D');
26 
27 $val = $f($value);
```

The second is more decoupled, more testable, more reusable, doesn’t hide a long dependency chain, and makes it easier to follow the logic flow from a single place. Those are all things you want.

## Use Maybe and Either for Error Handling

Errors are a fact of life in every codebase, be it developer error, user error, or the combination of the two. Before reaching for exceptions, which are themselves quite expensive, see if you can instead use the Maybe or Either patterns for handling error cases. In particular, monads are a good alternative for cases where the error isn’t world-ending catastrophic (like the database crashing mid-request) but for predictable and recoverable bad data, like a validation error or an entity-not-found.

This requires shifting your mindset a bit. Rather than thinking of a missing user as an error-condition, you’re using types to redefine the problem space. `getUser(int $id): User` is not a total function. It is a partial function over `int` because some integers map to a `User` and some do not. However, by re-reconceptualizing the problem to a map from `int` to `Maybe User`, it becomes a total function; the extra integers that have no corresponding `User` object now map to `None`, which is a legit value in the set `Maybe User`.

A missing user is no longer an error at all, but a valid return value that we can check for. But because of the `Maybe` wrapper, we don’t run the risk of forgetting to check for `null` and breaking code further down the line. It’s closer to a sentinel value but much more robust.

Similarly, a validation pipeline that uses an `Either` pattern acknowledges that a value not passing validation is not an error condition; it’s a frequently expected everyday occurrence.

If you’ve ever heard someone lament that you should never use exceptions for flow control without offering an alternative, here’s the alternative: Use monads for flow control instead. Leave the exceptions for the truly exceptional, unexpected explosions.

## Don’t Overdo It

Finally, acknowledge that you’re writing PHP. PHP allows you to write functional-style code, and you will likely benefit from doing so more often. However, PHP is not a fundamentally functional language. Sometimes a functional approach really is less readable or maintainable than the object-oriented style you’re used to. Or, more typically, a smart integration of functional principles with object-oriented syntax will end up being the sweet spot.

PHP is a multi-paradigm language. Use the paradigm that leads you to the most readable, maintainable, testable, and performant result you can. Often that will be a functional approach, but not always.

At the risk of mixing references, always use the right double-claw hammer for the job.

# Further Resources

It’s common for books and articles to have a “Further Reading” section, but of course, in the 2020s there’s a vast amount of excellent resources that are not in books but in videos, slide shows, and other non-traditional media. They’re still valuable if you want to know more about functional programming in general.

The following is a collection of resources I have found helpful in preparing this book and that I recommend for others whose appetite has been whet by these pages. (Or for those who were thoroughly confused by it and want better; my apologies.)

## Books

“[Category Theory for Programmers](https://bartoszmilewski.com/2014/10/28/category-theory-for-programmers-the-preface/),” by Bartosz Milewski (2018).

This is the book I wish existed 20 years ago, or even 10 years ago. It goes through category theory from the very basics on up, on the assumption the reader is a programmer rather than a Ph.D. mathematician that already knows category theory. It also, uniquely, uses examples from both Haskell and C++, the latter of which is far more helpful to programmers in PHP or, really, most other languages that aren’t built on a purely category theory foundation to begin with. If it has a failing it’s that not enough examples have a C++ version, and the index is far thinner than I’d like. Still, a strongly endorsed read.

“Basic Category Theory for Computer Scientists,” by Benjamine C. Pierce (1991).

An oldie, but very short. It’s a highly dense book that goes straight to hard core theory and includes a large number of Greek letters. It’s only 72 pages long, realistically; the rest of the book is a lengthy further reading section and index. It’s useful primarily as a reference.

“[From design patterns to category theory](https://blog.ploeh.dk/2017/10/04/from-design-patterns-to-category-theory/),” by Mark Seemann.

This isn’t a book per se, but a long series of articles that effectively form an online book. It approaches the topic from a different angle, and one I found reasonably useful. Its example language is C#, which should be somewhat comprehensible for PHP developers. Just remember that C# makes heavy use of generics.

## Videos

[Railway-Oriented Programming](https://fsharpforfunandprofit.com/rop/)

Scott Walachin’s presentation and accompanying slides on Railway-Oriented Programming. This is the talk where I really started to “get” the point of monads, even though the talk insists that it’s not about monads. It’s about structuring error handling pipelines in a useful way, which just so happens to look like an Either monad. He includes some train jokes, too.

[Functional Core, Imperative Shell](https://www.destroyallsoftware.com/screencasts/catalog/functional-core-imperative-shell)

Gary Bernhardt’s video on the “functional core, imperative shell” methodology. Although the video is in Ruby, the concepts apply in any language.

## Papers

[Monads for Functional Programming](http://homepages.inf.ed.ac.uk/wadler/papers/marktoberdorf/baastad.pdf)

Now that you’ve been through an introduction to functional programming, category theory, and the infamous monad, the original paper by Philip Wadler might make sense. It didn’t to me on first read, not even in the slightest, but if I did my job right with this book, you may now be able to follow it.

[Why do Monads Matter?](https://cdsmith.wordpress.com/2012/04/18/why-do-monads-matter/)

Why do Monads Matter? This is a much more academic and abstract take on monads, explaining many of the same concepts around dependency, uncertainty, and side effects that we have covered here. Now armed with some concrete experience from this book, it may even make sense.