![](images/cover.jpg)

![Cover: Mathematical Foundations of Computer Science, written by Ashwin Lall, published by CRC Press, Taylor and Francis Group, Boca Raton, London, New York, CRC Press is an imprint of the Taylor and Francis Group, an informa business, a Chapman and Hall book.](images/cover.jpg)

First edition published 2025

by CRC Press

2385 NW Executive Center Drive, Suite 320, Boca Raton FL 33431

and by CRC Press

4 Park Square, Milton Park, Abingdon, Oxon, OX14 4RN

*CRC Press is an imprint of Taylor & Francis Group, LLC*

© 2025 Ashwin Lall

Reasonable efforts have been made to publish reliable data and information, but the author and publisher cannot assume responsibility for the validity of all materials or the consequences of their use. The authors and publishers have attempted to trace the copyright holders of all material reproduced in this publication and apologize to copyright holders if permission to publish in this form has not been obtained. If any copyright material has not been acknowledged please write and let us know so we may rectify in any future reprint.

Except as permitted under U.S. Copyright Law, no part of this book may be reprinted, reproduced, transmitted, or utilized in any form by any electronic, mechanical, or other means, now known or hereafter invented, including photocopying, microfilming, and recording, or in any information storage or retrieval system, without written permission from the publishers.

For permission to photocopy or use material electronically from this work, access [www.copyright.com](https://www.copyright.com) or contact the Copyright Clearance Center, Inc. (CCC), 222 Rosewood Drive, Danvers, MA 01923, 978-750-8400. For works that are not available on CCC please contact [mpkbookspermissions@tandf.co.uk](mailto:mpkbookspermissions@tandf.co.uk)

*Trademark notice*: Product or corporate names may be trademarks or registered trademarks and are used only for identification and explanation without intent to infringe.

ISBN: 978-1-032-46789-4 (hbk)

ISBN: 978-1-032-46787-0 (pbk)

ISBN: 978-1-003-38328-4 (ebk)

DOI: [10.1201/9781003383284](https://doi.org/10.1201/9781003383284)

Typeset in Latin Modern font

by KnowledgeWorks Global Ltd.

*Publisher's note:* This book has been prepared from camera-ready copy provided by the authors.

# Preface

The guiding principle behind this book is to make the mathematics needed in computer science accessible to students who are motivated by computer science topics. By being introduced to mathematical topics just in time to understand the next computer science concept, students will be motivated to master the mathematical ideas. This book also includes concepts such as automata, regular expressions, grammars, Turing machines, and computability, which students may not otherwise see until much later courses (if they see them at all).

I assume that the reader of this book has had an algebra course (not necessarily calculus) and has taken an introductory computer science course that covers computer arithmetic, functions, iteration, conditionals, and recursion.

## Note for Students

This book is written to be example-heavy—there are over 250 worked examples. As you read each concept, work through the examples that come right after. (Keep paper and pen handy!) To solidify your understanding, practice the concept using the exercises that are given at the end of each chapter—there are over 550. The book was written with concision in mind, but this means that there are some sections you may have to read through several times to fully understand the ideas. It is well worth making sure you understand each section before moving on, as each section builds on the previous one(s).

## Note for Instructors

The goal of this book is to introduce students to the mathematical concepts needed in computer science just in time to apply them to learning some basic theory of computation. I have found that having real computer science topics helps motivate the mathematics for most students. The just-in-time philosophy works really well with theory of computation topics as you can make connections such as sets/languages to DFAs, direct proof to closure properties, induction to proving the language of a DFA, and proof by contradiction to the pumping lemma.

For programs that have a limited number of credits that they can require (such as at liberal arts colleges), this book offers a way to fold discrete math and automata theory into a single course. It covers most of the standard topics in both courses with some exceptions (e.g., pushdown automata). If you choose to adopt the approach of this book, your department will have to coordinate learning goals between this course and any later theory of computation course that you offer.

While I recommend going through most chapters sequentially, please feel free to reorder some topics. The dependencies between chapters are given in [Figure 0.1](#preface.xhtml#fig0_1). I prefer to get to DFAs ([Chapter 2](#chapter2.xhtml)) very quickly, but you could choose to cover logic ([Chapter 3](#chapter3.xhtml)) before it. When I teach this course over 15 weeks, we typically get through the entire book with the exception of [Chapters 9](#chapter9.xhtml) and [12](#chapter12.xhtml) and Appendices C and E. Depending on time constraints at your institution, you can also choose to not spend a lot of time on [Chapter 6](#chapter6.xhtml) and cut some of the later theory of computation material ([Chapters 13](#chapter13.xhtml) and [14](#chapter14.xhtml)), though it is compelling to get to decidability in this course. The appendices are included to cover other topics that are needed by your curriculum. They can be taught in any order, except that [Appendix A](#appA.xhtml#appA) (Counting) briefly references [Chapter 3](#chapter3.xhtml) (Logic), [Appendix B](#appB.xhtml#appB) (Probability) uses [Appendix A](#appA.xhtml#appA), [Appendix D](#appD.xhtml#appD) (Asymptotic Notation) relies on [Chapter 3](#chapter3.xhtml) (Logic), and Appendices F and G (Loop Invariants and Recurrence Relations) should be covered after [Chapter 8](#chapter8.xhtml) (Induction).

![Figure 1 Chapter dependencies](images/fig0_1.jpg)

[Figure 1](#preface.xhtml#bfig0_1) Chapter dependencies

This book was typeset in LaTeX, and all figures were made using TikZ. I recommend having your students write up their solutions in LATEX. Many resources for this book can be found at [https://personal.denison.edu/~lalla/MFCS](https://personal.denison.edu/~lalla/MFCS).

If you do end up adopting this book for a course, I would love to hear about it at [lalla@denison.edu](mailto:lalla@denison.edu). If you have comments or find any typos, please also feel free to reach out.

## Acknowledgments

I'd like to thank the following individuals:

*   Randi Cohen and Solomon Pace-McCarrick, for guiding me through the process of getting this book published;
    
*   Sean McCulloch and Sam Gutekunst, who gave me some excellent feedback that considerably improved the style of the book;
    
*   Ali Miller, for using a draft of this book and giving me practical feedback for many parts;
    
*   my students in the Fall 2023 section of CS 234, who gave me careful feedback: Caroline, Chloe, Daniel C., Lam, Khoa, Kian, Oghap, Ashwin, Phan Ahn, Phuong, Eleanor, Andrew, Cheryl, Tomer, Aryah, Ethan, Dipanker, Hieu, John, Daniel Z;
    
*   my PhD advisor, Mitsu Ogihara, for his guidance on this project;
    
*   the late Laura Sanchis, who instilled in me a love for the theory of computation that I hope is replicated in even a single reader of this book;
    
*   my Denison colleagues for their support, both direct and indirect, particularly Dee Ghiloni, Mikey Goldweber, Dave Goodwin, Jessen Havill (now at Bucknell), David Kahn, Matt Kretchmar, Matt Law, Lew Ludwig, May Mei, Ali Miller, Tony Silveira, Stacey Truex, and David White;
    
*   Pria and Ramona, for decades of love and care; and
    
*   Erin, Kiran, and Shannon: the best family a dad-dad could ask for.
    

This book is dedicated to the memory of my father, Ajit.

# Chapter 1Mathematical Data Types

DOI: [10.1201/9781003383284-1](https://doi.org/10.1201/9781003383284-1)

## 1.1 Why You Should Care

In this chapter, you will learn about the basic mathematical objects that you will use throughout this book. You can think of this as analogous to learning about primitive data types (e.g., int or float) in a programming language. It is critical to understand these very well to be able to understand more complex ideas.

## 1.2 Sets

You can think of a set as a box with a collection of objects in it. For example, below is an instance of a set with the numbers 1, 2, and 3 in it. This set is represented by the notation {1, 2, 3}.

There are a few important things to note about the idea of a set. First, a set does not have any repeated objects. If an object is repeated, it is only counted once. In particular, both the sets in the example below are the same because it doesn't matter how many times 3 appears in the set.

Second, the order of a set is immaterial. The sets {1, 2, 3} and {2, 1, 3} are the same set. This is very different from the idea of a list in a programming language like Python, where \[1,2,3\] and \[2,1,3\] are different lists.

Sets can contain objects of a variety of types, not just numbers.

We are now prepared to see our first definition:

## 1.3 Set Terminology

There is much terminology surrounding sets that is necessary to know as a computer scientist. The easiest way to learn it is to see lots of examples.

Any object in a set is called an **element** or **member** of the set.

We say that any object not in a set is not an element.

If all the elements of a set *A* are elements of another set *B*, we say that the first set is **contained** in the second or that *A* is a **subset** of *B* and write this as *A* ⊆ *B*.

A special case of this is that a set is always a subset of itself.

A special set, called the **empty set**, denoted by ∅, is the set with no elements. The empty set is a subset of all sets, including itself.

A set is a **proper subset** of another if the former is a subset that does not have all the elements of the latter.

Two sets are **equal** if they have exactly the same elements. An alternative definition is that both sets are subsets of each other.

The **cardinality** of a set is the number of distinct items it contains. The cardinality of a set is denoted by vertical bars around the set.

A set is called **finite** if its size or cardinality is a finite integer.

A set is called **infinite** if the number of elements in it is infinite.

There are a few infinite sets that have special symbols to represent them. The set of natural numbers ℕ is defined as:

The set of integers ℤ is defined as follows:

The set of all real numbers is denoted by ℝ.

## 1.4 Set-Builder Notation

When we are representing sets, especially infinite ones, it is useful to use **set-builder notation**. In this notation, a set is given in the form { expression: constraints}, where the expression is an operation performed on all possible values with the given constraints before insertion into the set.

You can think of this as a for loop that iterates through all the values that fit the conditions to the right of the colon (i.e., the natural numbers 0, 1, 2, 3, 4) and inserts these values into the set.

The expression to the left of the colon is an operation that can be applied to the values being iterated over. In the above example, the operation does nothing to each value. In the example below we double the value instead.

Set-builder can also be used for sets with infinite elements, even though a for loop to build it would never terminate.

We can also use set-builder notation to describe sets using plain English, as shown in the examples below:

The type of elements of the set can sometimes be included before the colon, as shown in the example below:

## 1.5 Union, Intersection, Difference, Complement

There are a number of standard operations that are performed on sets. The **union** of sets is the set of elements in at least one of them.

The **intersection** of sets is the set of elements in all of them.

The **difference** of two sets is the set of elements in the first that are not also in the second. The difference of sets *A* and *B* is written *A* − *B* or *A* ∖ *B*.

In some cases, sets are defined as being subsets of a universal set, sometimes denoted by the symbol *U*. When such a universal set is defined, we can define the **complement** of a set *A* to be the set of elements in *U* that are not in *A* (i.e., *U* − *A*).

Some writers use the notation *A*^(*c*) or  ∼ *A* to denote complement, but we will use $\\overset{―}{A}$ throughout this book.

In terms of order of operations, the complement operation has the highest precedence and all other ordering is shown using parentheses.

## 1.6 Venn Diagrams

A way to visualize set operations is to draw Venn diagrams. These diagrams shade in the region representing the operation between one or more sets. Venn diagrams for the various set operations described in the previous section are given in [Figure 1.1](#chapter1.xhtml#fig1_1).

![Figure 1.1 Venn diagrams for set operations](images/fig1_1.jpg)

[Figure 1.1](#chapter1.xhtml#b1fig1_1) Venn diagrams for set operations

We can even visualize set operations involving three sets, as seen in [Figure 1.2](#chapter1.xhtml#fig1_2).

![Figure 1.2 Venn diagrams for 3-way set operations](images/fig1_2.jpg)

[Figure 1.2](#chapter1.xhtml#b1fig1_2) Venn diagrams for 3-way set operations

These Venn diagrams can sometimes be used to demonstrate relationships between different expressions. For example, De Morgan's Laws state that $\\overset{―}{A \\cup B} = \\overset{―}{A} \\cap \\overset{―}{B}$ and $\\overset{―}{A \\cap B} = \\overset{―}{A} \\cup \\overset{―}{B}.$ These can be derived from Venn diagrams as seen next.

Try and show that $\\overset{―}{A \\cap B} = \\overset{―}{A} \\cup \\overset{―}{B}$ using an approach similar to the above example.

## 1.7 Power Sets

It is sometimes useful to refer to the set of all subsets of a set.

We can also have even more complex power sets.

Since each element of a set can either be included or not included in a subset, we can have an exponential number of subsets. More specifically, the cardinality of the power set of a set *A* is given by

  
$$\\begin{array}{l} {{|\\mathcal{P}(A)|} = 2^{|A|}.} \\\\ \\end{array}$$  

## 1.8 Tuples and Cartesian Products

Next, we look at the tuple type that is closest to the notion of a list in most programming languages.

Tuples are comma-separated lists with parentheses on both ends, such as (1, 2, 3). They are different from sets in that they allow repeats, and the order of items actually matters.

Tuples that have two items are called **pairs**. Tuples with three items are called **triples**. Longer tuples are referred to as *n* -**tuples**, where *n* is the length of the tuple.

An important way in which tuples arise is when we look at all combinations of items in two or more sets, called the **Cartesian product**.

The Cartesian product can be done in three (or more) ways as well, as seen in the following example:

You can denote the Cartesian product of a set with itself using power notation.

One has to be careful if parentheses are added to the Cartesian product.

The cardinality of a Cartesian product can be computed as the product of the cardinalities of the individual sets. If we have sets *A*[1], *A*[2], *A*[3], …, *A*[*n*], then the cardinality of the Cartesian product *A*[1] × *A*[2] × *A*[3] × … × *A*[*n*] is |*A*[1]| ⋅ |*A*[2]| ⋅ |*A*[3]| ⋅ … ⋅ |*A*[*n*]|.

A special case to consider is when the Cartesian product involves a set that is empty. By the above cardinality relationships, we know that for any set *A* we have that *A* × ⌀ must have cardinality |*A*| ⋅ 0 = 0 and must therefore be the empty set.

Another way to see this is to consider that the result of the Cartesian product can be computed by [Algorithm 1.1](#chapter1.xhtml#algo1_1). If any of the nested loops runs zero times, then the innermost line is never run, meaning that *S* remains empty.

## 1.9 Functions

You will make extensive use of functions in computer science and this book.

It is useful to think of the domain as the types of the input parameters to our function, as we would in a strongly typed language such as Java, and the codomain as the type of the output of the function.

Later in this book, we will see functions that have more complex domains and codomains over tuples.

## 1.10 Strings

Strings are mathematical objects that are very similar to strings in programming languages. They are sequences of characters such as abc or 123. Similar to programming languages, strings can be **concatenated** with one another so that if we have two strings *s*[1]\= abc and *s*[2]\= def then the concatenated string *s*[1]*s*[2]\= abcdef.

Strings are defined over an **alphabet** set Σ (the Greek symbol uppercase sigma).

Notice that, unlike programming language strings, we do not include any quotes around the string. Another important difference is that programming languages allow for all characters (ASCII or Unicode), but mathematical strings will usually be restricted to a smaller collection of characters.

The **length** of a string *s* is the number of characters in it and denoted |*s*|.

The unique string of length zero is called the **empty string**. It is usually denoted in programming languages by "", but since no quotation marks are used for mathematical strings, we use the Greek symbol lowercase lambda (*λ*). Some books also use lowercase epsilon (*ϵ*) to denote the empty string.

A shorthand that we will use for strings such as aaaaaaa is to use power notation to express it more succinctly as a⁷. We can also combine this with concatenation to write strings such as a³b²a³ to be shorthand for aaabbaaa. This shorthand can also be applied to string expressions, such as (`a``b`) ³ for ababab.

A **substring** is any consecutive sequence of characters in a string.

A **prefix** is any initial substring of a string.

A **suffix** is any substring at the end of a string.

Notice that strings above were listed in ascending order in their length, breaking ties using the usual dictionary order. This is known as **shortlex** ordering.

This is easiest seen by the way of a few examples:

Note that shortlex ordering is not the same as standard dictionary ordering as, for example, the string cat comes before the string abacus (since cat is shorter).

We will refer to all the strings over an alphabet Σ as *Σ*^(\*). Using the notion of shortlex ordering, we can now write all strings in *Σ*^(\*) in the following example:

## 1.11 Languages

Almost all the computation we will see in this book will consist of recognizing or accepting languages.

We can write out languages more succinctly and precisely by using mathematical notation.

We can also introduce string variables to write out sets over strings more compactly, as shown in the following examples:

The term language comes from the fact that the languages that you are familiar with can be represented by sets of strings.

The computational tasks we will perform in this book then just become ones of determining whether a string (the input) is in a particular language. Any function that we can compute that has a Boolean output (True or False) can be thought of as the set of input strings that return True.

This may appear unusual to you as computations such as addition and multiplication (or more complex functions) aren't tasks where you are trying to determine if something is in a set. While it is true that we lose the ability to describe such computation with languages, we still retain considerable expressive power that is sufficient to prove many results about various models of computation.

## 1.12 Chapter Summary and Key Concepts

*   A **set** is an unordered collection of distinct objects (numbers, strings, programming languages, etc.). The objects in a set are called its **elements** or **members**. The notation *x* ∈ *A* is how we denote that *x* is an element of the set *A* and *x* ∉ *A* is how we denote that *x* is not an element of the set *A*.
    
*   The **empty set** (∅) is the unique set with no elements.
    
*   A set is a **subset** of another set if all its elements are contained in the other set. The empty set is a subset of all sets. A set is always a subset of itself.
    
*   Two sets are **equal** if they have the same elements. To show that two sets are equal, we have to show that both sets are subsets of each other.
    
*   The **cardinality** of a set is the number of elements in the set. Sets can be **finite** or **infinite**.
    
*   The set ℕ is all the **natural numbers**, the set ℤ is the set of **integers**, the set ℝ is the set of all **real numbers**, and the set ℚ is the set of all **rational numbers** (i.e., numbers of the form *p*/*q*, where *p* and *q* are integers and *q* is not zero).
    
*   Sets are often expressed in **set builder notation**, which takes the form { expression: constraints}.
    
*   The **union** of sets *A* and *B* is *A* ∪ *B* = {*x* : *x* ∈ *A* or *x* ∈ *B*}. The **intersection** of sets *A* and *B* is *A* ∩ *B* = {*x* : *x* ∈ *A* and *x* ∈ *B*}. The **difference** of sets *A* and *B* is *A* − *B* = {*x* : *x* ∈ *A* and *x* ∉ *B*}.
    
*   The **complement** of a set *A* is its difference from a universal set *U*, $\\overset{―}{A} = U - A$.
    
*   **Venn diagrams** are diagrams that visualize set operations.
    
*   The **power set** of a set is the set of all its subsets. The cardinality of the power set of a set *A* is given by |𝒫(*A*)| = 2^(|*A*|).
    
*   A **tuple** is an ordered collection of items that allows for repeated items. Sets of tuples are commonly created by computing **Cartesian products** of sets. The size of the set created from the Cartesian product of several sets is the product of the sizes of those sets.
    
*   **Functions** are mappings of values from a **domain** set to a **codomain** set. Functions can be represented by formulas or tables.
    
*   A **string** is an ordered sequence of characters from an **alphabet**. The number of characters in a string *s* is called its **length** and is denoted by |*s*|. The unique string of length zero is called the **empty string** *λ*.
    
*   Any consecutive sequence of characters in a string is called a **substring**. When the substring appears at the start of the string, it is called a **prefix**. When it appears at the end of the string, it is called a **suffix**.
    
*   Strings can be sorted using **shortlex ordering**. In this ordering, shorter strings come before longer strings. For strings of the same length, the dictionary ordering is used—the leftmost character at which the two strings differ is used to order them.
    
*   Any set of strings over an **alphabet** Σ is called a **language**. Languages are used extensively in computer science to define sets with the same property (e.g., whether a number is a prime or whether a computer program is syntactically correct).
    

## Exercises

### Exercises for 1.4

Write out the elements of the following sets within set braces:

*   1.1 The set of programming languages you have coded in
    
*   1.2 The set of the days of the week
    
*   1.3 {2*n* : *n* ∈ ℕ, *n* < 5}
    
*   1.4 {3*n* : *n* ∈ ℕ, 7 ≤ *n* ≤ 10}
    
*   1.5 {7*n* : *n* ∈ ℕ}
    
*   1.6 {10*n* : *n* ∈ ℤ}
    
*   1.7 {4*n* + 1 : *n* ∈ ℕ}
    
*   1.8 {3*n* − 1 : *n* ∈ ℤ}
    
*   1.9 {2*n*² : *n* ∈ ℤ}
    
*   1.10 {*n*³ : *n* ∈ ℕ}
    

Write the following sets using set-builder notation:

*   1.11 {4, 5, 6, …, 40}
    
*   1.12 { − 3,  − 2,  − 1, …, 17}
    
*   1.13 {0, 2, 4, 6, …}
    
*   1.14 {0, 1, 4, 9, 16, …}
    
*   1.15 {3, 7, 11, 15, 19, …}
    

### Exercises for 1.5

Assuming that *A* = {1, 2, 3, 4, 5}, *B* = {2, 3, 5, 7}, *C* = {4, 5, 6, 7, 8} and a universal set *U* = {1, 2, 3, 4, 5, 6, 7, 8}, compute the following:

*   1.16 *A* ∪ *B*
    
*   1.17 *B* ∩ *C*
    
*   1.18 *A* − *B*
    
*   1.19 *B* − *C*
    
*   1.20 $\\overset{―}{C}$
    
*   1.21 (*A* ∩ *B*) ∪ *C*
    
*   1.22 $\\overset{―}{A \\cap B}$
    
*   1.23 $(A \\cup B) \\cap (\\overset{―}{B \\cup C})$
    

### Exercises for 1.6

Draw Venn diagrams for the following expressions, showing the steps (intermediate diagrams) in each case:

*   1.24 (*A* − *B*) ∪ (*B* − *A*)
    
*   1.25 $(A \\cap B) \\cup \\overset{―}{A}$
    
*   1.26 (*A* ∪ *B*) − *C*
    
*   1.27 $\\overset{―}{A} \\cup \\overset{―}{B} \\cup \\overset{―}{C}$
    
*   1.28 $\\overset{―}{A} \\cap \\overset{―}{B} \\cap \\overset{―}{C}$
    

Show using Venn diagrams, using labeled intermediate steps, whether the following pairs of expressions are equal:

*   1.29 *A* ∪ (*B* ∩ *C*) and (*A* ∩ *B*) ∪ (*A* ∩ *C*)
    
*   1.30 *A* ∪ (*B* ∩ *C*) and (*A* ∪ *B*) ∩ (*A* ∪ *C*)
    
*   1.31 *C* − (*A* ∩ *B*) and (*C* − *A*) ∪ (*C* − *B*)
    
*   1.32 *C* − (*A* ∪ *B*) and (*C* − *A*) ∩ (*C* − *B*)
    
*   1.33 *A* − *B* and $A \\cap \\overset{―}{B}$
    

### Exercises for 1.7

List the elements of the following sets within set braces:

*   1.34 𝒫({0, 1})
    
*   1.35 𝒫({*a*, *b*, *c*})
    
*   1.36 𝒫({*a*, {*b*, *c*}})
    
*   1.37 𝒫(𝒫({0, 1}))
    
*   1.38 𝒫(𝒫(𝒫({0})))
    

Compute the *size* of each of the following sets:

*   1.39 𝒫({0, 1, 2, 3, 4})
    
*   1.40 𝒫({0, 1, {2, 3, 4}})
    
*   1.41 𝒫({{0, 1}, {2, 3, 4}})
    
*   1.42 𝒫({{0, 1}, {2, 3}, 4})
    
*   1.43 𝒫(𝒫({0, 1, 2, 3, 4}))
    
*   1.44 𝒫(𝒫(𝒫({0, 1})))
    

### Exercises for 1.8

Assuming that *A* = {0, 1}, *B* = {*a*, *b*} and *C* = {1, 2, 3}, list the elements of the following sets within set braces:

*   1.45 *A* × *B*
    
*   1.46 *B* × *C*
    
*   1.47 *C*²
    
*   1.48 *A*⁴
    
*   1.49 *A* × *B* × *B*
    
*   1.50 *A* × *B* × *C*
    
*   1.51 (*A* × *B*) × *C*
    
*   1.52 *A* × (*B* × *C*)
    

Assuming that *A* = {0, 1}, *B* = {*a*, *b*} and *C* = {1, 2, 3}, compute the *size* of each of the following sets:

*   1.53 *A* × *C*
    
*   1.54 *A* × *B* × *A* × *B*
    
*   1.55 *A*⁵
    
*   1.56 *C*^(10)
    
*   1.57 𝒫(*A*) × 𝒫(*B*)
    
*   1.58 𝒫(𝒫(*A*) × 𝒫(*B*) × 𝒫(*C*))
    

### Exercises for 1.9

List the domain and the codomains for the following functions:

*   1.59 A function double that takes as input a real number and returns twice its value
    
*   1.60 A function max that takes as input 5 integers and returns the largest one
    
*   1.61 A function sum that takes as input 10 real numbers and returns their sum
    
*   1.62 A function sort5 that takes as input 5 integers and returns them sorted
    

### Exercises for 1.10

Write out the following strings in shorthand notation:

*   1.63 aaaaaaa
    
*   1.64 aaabbbbccc
    
*   1.65 aaaaabbaaaaa
    
*   1.66 abcabcabcabc
    
*   1.67 aaaaababababababcccccc
    

Write out all the prefixes and suffixes for the following strings:

*   1.68 aaaa
    
*   1.69 ababa
    
*   1.70 aaaaabbbbbbb
    
*   1.71 aaabbccc
    
*   1.72 abcabcabc
    

### Exercises for 1.11

List all strings of length at most 4 from the following languages:

  
$$\\begin{array}{l} {\\Sigma = \\{ 0,1\\}} \\\\ \\end{array}$$  

*   1.73 {0^(*n*) : *n* ∈ ℕ}
    
*   1.74 {0^(*n*)1^(*n*) : *n* ∈ ℕ}
    
*   1.75 {0^(*n*)1^(*m*) : *n*, *m* ∈ ℕ}
    
*   1.76 {0^(*n*)1^(*m*) : *n*, *m* ∈ ℕ, *n* + *m* ≥ 2}
    
*   1.77 {*x*01 : *x* ∈ *Σ*^(\*)}
    
*   1.78 {*x*11*y* : *x*, *y* ∈ *Σ*^(\*)}
    

Write the following languages in set builder (mathematical) notation:

  
$$\\begin{array}{l} {\\Sigma = \\{ 0,1\\}} \\\\ \\end{array}$$  

*   1.79 The set of all strings which consist of zero or more 0s and no 1s.
    
*   1.80 The set of all strings which consist of one or more 1s and no 0s.
    
*   1.81 The set of all strings which consist of one or more 0s followed by one or more 1s.
    
*   1.82 The set of all strings that consist of a number of 0s followed by the same number of 1s (at least one of both).
    
*   1.83 The set of all strings that consist of a number of 0s followed by a larger number of 1s (at least one of both).
    
*   1.84 The set of all strings with a prime number of 1s and no 0s.
    
      
    $$\\begin{array}{l} {\\Sigma = \\{ a,b\\}} \\\\ \\end{array}$$  
    
*   1.85 The set of all strings that begin with an a.
    
*   1.86 The set of all strings that begin with an a and end with a b.
    
*   1.87 The set of all strings that have an even number of as and no bs.
    
*   1.88 The set of all strings that have an even number of as followed by an odd number of bs.
    
*   1.89 The set of all strings that contain ab as a substring.
    
*   1.90 The set of all strings that have an a in the third position.
    
*   1.91 The set of all strings that have a b four positions from the end.
    
*   1.92 The set of all strings that start and end with the same three characters.
    

# Chapter 2Deterministic Finite Automata

DOI: [10.1201/9781003383284-2](https://doi.org/10.1201/9781003383284-2)

## 2.1 Why You Should Care

We are now ready to study a simple model of computation. As computer scientists, we have to understand the computing models that we working with to determine what is easily computable and (later in this book) what is not computable at all. The first model of computation that we will study is called a **deterministic finite automaton** or **DFA** (plural: deterministic finite automata).

## 2.2 A Vending Machine Example

Suppose that you had a vending machine that only accepts nickels (5 cent coins) and dimes (10 cent coins) and sold snacks for 20 cents. (Wouldn't it be lovely to be able to buy anything for 20 cents!) The DFA for such a machine is given in this example.

The circles in the diagram are called states and the computation is always at exactly one state at any given time. Any computation on this DFA starts at the start state (*q*[0] in this example) that is denoted by an arrow entering it. The actions that are then performed are the insertion of nickels (denoted with an arrow labeled with an N) or dimes (denoted by arrows labeled with a D). These actions cause the computation to transition between the states {*q*[0], *q*[5], *q*[10], *q*[15], *q*[20]}. Note that arrows with multiple characters have commas separating them, for example we can transition from *q*[15] to *q*[20] on either N or D.

The names of the states were picked in such a way to denote how much money has been entered into the vending machine. For example, when a dime is entered at state *q*[0], the vending machine should transition to the state *q*[10] denoting a total of 10 cents that have been entered thus far.

The state *q*[20] is called the final or accepting state and indicates the condition under which the vending machine dispenses a snack. It is denoted by a double circle.

For a DFA to be completely defined, each state must have a transition for each possible input (in this case a nickel or dime). In particular, in this example, we send any over-payment (a dime at *q*[15] or any additional coins at *q*[20]) to *q*[20]. Conceptually, this represents the idea that the machine should still dispense the snack if there is over-payment—it may just eat change.

Rather than performing any actions, this DFA is designed to capture the set of inputs that should cause the machine to dispense a snack. For example, if a user enters a nickel and a dime, this input would be represented by the string ND and since it would end at state *q*[15] (a non-final state), this input would be rejected—there was insufficient money for the snack.

Make sure to follow the transitions for each string in the above examples to see why they do(n't) end up at the accepting state.

To solidify your understanding of this example, try to construct a DFA for a vending machine for a 30 cent snack. You can also add a Q action for quarters (25 cent coins).

## 2.3 Formal Definition of a DFA

A DFA is formally defined by a 5-tuple (*Q*, *Σ*, *δ*, *q*[0], *F*). These are as follows:

*   *Q* is the set of states
    
*   Σ is the input alphabet
    
*   *δ* : *Q* × *Σ* → *Q* is called the transition function
    
*   *q*[0] is the start state
    
*   *F* is the set of final or accepting states
    

These are best illustrated with examples.

When designing your own DFAs, you should make sure that the table for the *δ* transition function is fully filled in—every pair of state and input symbol must have an entry. This is something easy to forget when you are first learning to create DFAs.

Notice how the entire computation model can be so precisely captured using the mathematical data types that you learned about in [Chapter 1](#chapter1.xhtml), including sets, tuples, alphabets, strings, and functions. This is conceptually similar to “coding” up your computation using technical notation.

We give a name to all the languages accepted by a DFA:

## 2.4 Matching Phone Numbers

The next example of a DFA we will look at is for one that will identify numbers that start with the author's area code (740). This can be represented by the language

  
$$\\begin{array}{l} {\\{ 740s:s \\in \\{ 0,\\ldots,9\\}^{\\ast}\\}.} \\\\ \\end{array}$$  

The next figure shows a DFA that will accept only strings that start with 740. (Note that it will accept strings of any length that start with 740, including ones that are too short or long to be a phone number, but we will ignore that detail for now.)

This DFA works by moving toward the accepting state (*q*[3]) precisely when the first three symbols are 7, 4, and 0. Notice that the states *q*[3] and *q*[4] are what are known as **sink states**. That is, it is impossible to leave them once entered. The difference, of course, is that once the state *q*[3] is entered, the string is accepted no matter what (it has been confirmed to start with 740), whereas once the state *q*[4] is entered the string is definitely rejected since it did not start with a 740 pattern.

As before, we can create a tuple for this DFA.

A common error to avoid with DFAs is to be imprecise about its language. In particular, someone looking at this DFA might notice that it accepts all strings that start with 74 and infer that that is its language. Of course, since this DFA does not accept strings such as 747, this is not correct—saying that it accepts all strings that start with 74 was too broad.

The opposite problem might occur as well. It might be noted that this DFA does accept all strings that start with 7405. This time, the observation is too specific—this characterization excludes strings such as 7401234567. Being precise about the language of a DFA you are given or that you design is very important. Just as with writing code, you want to test your DFA with lots of examples and think about special cases.

## 2.5 Computational Biology

You might have heard that DNA is encoded by four types of nucleotides that are represented by the letters A, C, G, and T. Sequences of these nucleotides are studied by computational biologists to analyze DNA and search for proteins. Our next problem will be to take a string of DNA and determine whether the substring of length three (called a codon) TTA appears anywhere in it. This can be written as the language

  
$$\\begin{array}{l} {\\{ pTTAs:p,s \\in \\{ A,C,G,T\\}^{\\ast}\\}.} \\\\ \\end{array}$$  

For example, the string GATTACA should be accepted but the string CATCAT should not. A DFA for this language is given in the example below:

Similar to the previous example, we create a path to the accepting state when TTA is seen as a substring (*q*[0] → *q*[1] → *q*[2] → *q*[3]). This time, however, the substring can be in any part of the string, so we have to be careful about the other transitions. It is useful here to think about what strings should reach each of the states. Since we have to keep track of whether the substring TTA has appeared, we use states to remember our progress toward this goal. We use *q*[1] to denote the case that we have not yet found a TTA substring and we have most recently encountered a single T (but not a TT). The state *q*[2] is reachable by strings for which we have not yet found a TTA substring and we have most recently encountered a TT. The accepting sink state *q*[3] is reached once we have encountered the entire substring TTA. The start state *q*[0] then is reachable from all other strings.

Armed with this intuition, we can understand why all the transitions were chosen in [Example 2.6](#chapter2.xhtml#exam2_6). Any transition out of a state that does not make progress toward the goal of identifying the string TTA should go back to state *q*[0]. For example, the state *q*[1] returns to *q*[0] on an A, C, or G. The only exception here is that *q*[2] on a T self-loops since the past two characters were still TT, so we want to stay on *q*[2] on a T.

As with the other DFAs, trace the path for strings in the language such as TTA, ATTGTTA, and ATTTTAGC to see why they get to the accepting state as well as why other strings such as TTG, TATTCTT, and TTTTGTT do not get to the accepting state.

Generating the tuple for this DFA is left as an exercise for the reader.

## 2.6 Stop Codons

Our next example, also from computational biology, will be to identify strings that do *not* end with the stop codon TAG. That is, we want to accept the complement of the language {*x**T**A**G* : *x* ∈ {*A*, *C*, *G*, *T*}^(\*)}. Just like the previous example, we need to create states that will allow us to keep track of whether the last three symbols were T, A, and G. We will use a state *q*[1] to represent whether the last symbol seen was a T, *q*[2] to represent whether the last two symbols were TA, and *q*[3] to represent whether the last three symbols were TAG. The state *q*[0] will once again catch all the remaining strings. The resulting DFA is shown below:

Notice here that, unlike the previous example, we accept strings that reach any state other than *q*[3]. Since we have multiple accepting states, *F* really has to be a set to hold all of them.

Again, practice creating the tuple for this DFA.

## 2.7 Divvying Up Candy

A mom wants to split up the candy between her two kids and wants to know if she can divide it evenly between them. There are three types of candies: chocolates, lollipops, and taffy. The mom wants to make sure that there is an even number of chocolates and lollipops, but she doesn't care about the taffy since neither kid likes it.

We will create a DFA that will determine whether a pile of candies can be evenly divided two ways. The pile will be represented by a string in which chocolates, lollipops, and taffy are represented by the letters C, L, and T, respectively. For example, the DFA should accept the strings CLTTLLLC and TCCTT since they have an even number of chocolates and an even number of lollipops. The DFA should reject the string TLLC and TLC because the first has an odd number of chocolates and the second has an odd number of both chocolates and lollipops.

To design a DFA for this problem, we have to think about the possible states that we need to represent. Specifically, we care if there is an even or an odd number of chocolates, and similarly for the lollipops. Since the number of chocolates and lollipops are unrelated numbers, we will have a total of four possibilities: both even, odd chocolates and even lollipops, even chocolates and odd lollipops, and both odd. Armed with this intuition, we design the DFA seen in the example below:

The states *q*[0], *q*[1], *q*[2], *q*[3] represent the four possibilities listed above. Each time we see another piece of chocolate we switch between the left and right states. Each time we see another lollipop we switch between and the top and bottom states. Since the number of pieces of taffy doesn't affect anything, we just self-loop on the current state when we see a taffy. Lastly, we make *q*[0] the accepting state since this is the one that captures strings that have an even number of chocolates and lollipops—a nice even split for the kids!

Once again, write out the full tuple for this DFA as practice.

## 2.8 Divisibility in Binary

Finite automata can also be used to compute mathematical properties. For example, we will see how to determine whether a number, given in binary, is divisible by three next. Before we do this, we will take a short detour to review binary numbers.

In the decimal number system (or base 10) that we are used to using, the digit at each position indicates the corresponding power of ten's place for the number. For example, the decimal number 1234 can be written as

  
$$\\begin{array}{l} {1234 = 1 \\times 10^{3} + 2 \\times 10^{2} + 3 \\times 10^{1} + 4 \\times 10^{0}.} \\\\ \\end{array}$$  

In other words, there is a 1 in the thousand's (10³) place, a 2 in the hundred's (10²) place, a 3 in ten's (10¹) place, and a 4 in the one's (10⁰) place.

Similarly, binary (or base 2) numbers have places for the powers of two. For example, the binary number 1011[2] (here, the subscript 2 indicates that the number is in binary) can be written as

  
$$\\begin{array}{l} {1011\_{2} = 1 \\times 2^{3} + 0 \\times 2^{2} + 1 \\times 2^{1} + 1 \\times 2^{0} = 8 + 0 + 2 + 1,} \\\\ \\end{array}$$  

which is just the number eleven.

Now, to solve the divisibility by three in binary problem, we will use the following strategy. An alternative way of saying that a number is divisible by three is to say that it leaves a remainder of zero when divided by three. We will thus design a DFA that keeps track of the remainder of the number when dividing by three, with one state for each of the remainders 0, 1, and 2, as seen in the following DFA:

To understand how the DFA was designed, it is first necessary to understand what happens to a binary number when a 0 or a 1 is appended to the end of it. When we add a 0 to the end of a binary number, it is the same as multiplying the number by 2 (similar to how adding a 0 to the end of a decimal number multiplies it by 10). When we add a 1 to the end of a binary number, it is the same as multiplying it by 2 and then adding 1. Therefore, when we start at state *q*[0] (the state representing a remainder of 0 when dividing by 3), doubling the number still gives a remainder of 0 when dividing by 3 so we have a self-loop on 0. On the other hand, when multiplying a number with remainder 0 by 2 and adding 1, we get a number that has a remainder of 1 when dividing by 3, so we transition from *q*[0] to *q*[1] on a 1. See what happens when you do the same for numbers that have a remainder of 1 when divided by 3 (state *q*[1]) and numbers that have a remainder of 2 when divided by 3 (state *q*[2]) to make sure you understand how the transitions out of *q*[1] and *q*[2] were determined.

Note that, for simplicity, we assume that the empty string is in the language. We also allow the binary number to have leading 0s, that is, we treat the number 0011[2] the same as the number 11[2].

## 2.9 Chapter Summary and Key Concepts

*   A **deterministic finite automaton (DFA)** is a simple model for computing whether a string is in a language. It consists of **states**, including one **starting state** and one or more **accepting states**, with transitions between them.
    
*   DFAs are formally defined by a **5-tuple (*Q*, *Σ*, *δ*, *q*[0], *F*)**, where *Q* is the set of **states**, Σ is the **input alphabet**, *δ* is the **transition function**, *q*[0] is the **start state**, and *F* is the set of **final or accepting states**.
    
*   A language is called **regular** if it has a DFA that accepts it.
    
*   DFAs can be used to accept the languages with applications such as vending machines, pattern matching, computational biology, and testing arithmetic properties.
    

## Exercises

Give the full 5-tuple for DFAs for the following languages:

*   2.1 {*w* ∈ {0, 1}^(\*) : *w* starts with a 0}
    
*   2.2 {*w* ∈ {0, 1}^(\*) : *w* ends with a 1}
    
*   2.3 {*w* ∈ {0, 1}^(\*) : *w* ends with 00}
    
*   2.4 {*w* ∈ {0, 1}^(\*) : *w* has 01 as a substring}
    
*   2.5 {*w* ∈ {0, 1}^(\*) : *w* does not have 01 as a substring}
    

Draw DFAs for the following languages:

*   2.6 {*w* ∈ {0, 1}^(\*) : *w* is of odd length}
    
*   2.7 {*w* ∈ {0, 1}^(\*) : *w* has an even number of 0s}
    
*   2.8 {*w* ∈ {0, 1}^(\*) : *w* has an even number of 0s and an odd number of 1s}
    
*   2.9 {*w* ∈ {0, 1}^(\*) : *w* has an even number of 0s and an even number of 1s}
    
*   2.10 {*w* ∈ {0, 1}^(\*) : *w* has an odd number of 0s and an even number of 1s}
    
*   2.11 {*w* ∈ {0, 1}^(\*) : *w* has an odd number of 0s and an odd number of 1s}
    
*   2.12 {*w* ∈ {0, 1}^(\*): the third character in *w* is 0}
    
*   2.13 {*w* ∈ {0, 1}^(\*) : *w* starts and ends with a 0}
    
*   2.14 {*w* ∈ {0, 1}^(\*) : *w* starts or ends with a 0}
    
*   2.15 {*w* ∈ {0, 1}^(\*) : *w* has exactly one 0}
    
*   2.16 {*w* ∈ {0, 1}^(\*) : *w* contains 10 but not 1010}
    
*   2.17 {*w* ∈ {0, 1}^(\*) : *w* contains at least two 0s and at least one 1}
    
*   2.18 {*w* ∈ {0, 1}^(\*) : *w* contains at most two 0s and at least one 1}
    
*   2.19 {*w* ∈ {0, 1}^(\*): the number of 0s in *w* is divisible by 3}
    
*   2.20 {*w* ∈ {0, 1}^(\*) : *w* is divisible by 4 in binary} (Let *λ* be in the language and ignore leading 0s.)
    
*   2.21 {*w* ∈ {0, 1}^(\*) : *w* is divisible by 5 in binary} (Let *λ* be in the language and ignore leading 0s.)
    
*   2.22 {*w* ∈ {0, 1}^(\*) : *w* has remainder 1 when divided by 5 in binary} (ignore leading 0s)
    
*   2.23 {*w* ∈ {0, …, 9}^(\*) : *w* is even in decimal} (Let *λ* be in the language and ignore leading 0s.)
    
*   2.24 {*w* ∈ {0, …, 9}^(\*) : *w* is divisible by 5 in decimal} (Let *λ* be in the language and ignore leading 0s.)
    
*   2.25 {*w* ∈ {0, …, 9}^(\*) : *w* is divisible by 7 in decimal} (Let *λ* be in the language and ignore leading 0s.)
    
*   2.26 {*w* ∈ {*A*, *C*, *G*, *T*}^(\*) : *w* has the substring ATG followed later by the substring TAA}
    
*   2.27 {*w* ∈ {*A*, *C*, *G*, *T*}^(\*) : *w* has the substring ATG followed later by the substring TAA or TAG or TGA}
    
*   2.28 {*w* ∈ {*a*, …, *z*, 0, …, 9}^(\*) : *w* is a password (string) of length at least 6 characters}
    
*   2.29 {*w* ∈ {*a*, …, *z*, 0, …, 9}^(\*) : *w* is a password (string) of length at least 6 characters with at least one digit}
    
*   2.30 {*w* ∈ {*a*, …, *z*, 0, …, 9}^(\*) : *w* is a password (string) of length at least 6 characters with at least one digit and one letter}
    
*   2.31 {*w* ∈ {0, 1}^(\*): the third character from the end in *w* is 0}
    
*   2.32 {*w* ∈ {0, 1}^(\*): at least one of the last three characters from the end is a 0}
    
*   2.33 {*w* ∈ {0, 1}^(\*) : *w* starts and ends with the same two characters}
    

# Chapter 3Logic

DOI: [10.1201/9781003383284-3](https://doi.org/10.1201/9781003383284-3)

## 3.1 Why You Should Care

It is not an exaggeration to say that mathematical logic underlies all of computer science. Computer circuits are made out of logical operators. The mathematical arguments we make about algorithms follow the rules of logic. Moreover, understanding logic will make you better at writing conditional (if) statements and (while) loops when you code.

## 3.2 Logical Statements

A **logical statement** is a mathematical statement that has a value of **true** or **false**.

We can treat logical statements like mathematical objects (for instance, sets or strings) and give them names.

Sometime propositions take arguments, in which case they are called predicates.

## 3.3 Logical Operations

Similar to conditional statements in computer code, we use three operations to modify logical statements: and, or, and not.

Logical **conjunction** (and) is an operation that takes on the value true precisely when both the statements it modifies are true. It is denoted by the ∧ symbol.

Logical **disjunction** (or) is an operation that takes on the value true precisely when either of the statements it modifies are true. It is denoted by the ∨ symbol.

Logical **negation** (not), denoted by the ¬ symbol, is an operation on a single expression that flips true to false and false to true.

We can use variables to serve as placeholders for logical statements.

In terms of order of operations, the negation operation has the highest precedence and all other ordering is shown using parentheses.

## 3.4 Truth Tables

A convenient way to represent expressions involving the above logical expressions is to use **truth tables**. The truth table for the operations from the previous section is given in [Figure 3.1](#chapter3.xhtml#fig3_1). The values true and false are abbreviated with T and F.

![Figure 3.1 Truth table for logical operations](images/fig3_1.jpg)

[Figure 3.1](#chapter3.xhtml#b3fig3_1) Truth table for logical operations

You should create truth tables for more complex expressions by breaking them into smaller pieces.

The notation for and (∧) and or (∨) may remind you of the notation for set intersection (∩) and set union (∪) and this is for good reason. When you compute the intersection of two sets, you are saying that the resulting elements must be in the first set **and** the second. Similarly, the elements of the union of two sets must be in the first set **or** the second.

The above connection means that some rules with sets generalize to logical statements. The following example shows that one of De Morgan's laws for sets applies for logic as well since the column for ¬(*A* ∨ *B*) is identical to the one for ¬*A* ∧ ¬*B*.

Since ¬(*A* ∨ *B*) and ¬*A* ∧ ¬*B* have identical columns in the truth table, we say that they are **logically equivalent**.

As an exercise, show that ¬(*A* ∧ *B*) and ¬*A* ∨ ¬*B* are logically equivalent (this is another of De Morgan's laws).

## 3.5 Conditional Statements

Another important logical operation is the conditional. This applies when one logical expression implies another and is denoted using the ⇒ operator.

The truth table for conditionals is given in [Figure 3.2](#chapter3.xhtml#fig3_2). For example, a true expression always implies a true expression, so T ⇒ T is true and T ⇒ F is false. However, a false expression can imply a false or true expression, so F ⇒ T and F ⇒ F are both true. Another way to say this is that the result of the operation is true if the first expression is false or if the second is true and this logical equivalence is demonstrated with ¬*A* ∨ *B* in the last column of the table.

![Figure 3.2 Truth table for conditional operation](images/fig3_2.jpg)

[Figure 3.2](#chapter3.xhtml#b3fig3_2) Truth table for conditional operation

Some people are thrown off when they see that *F* ⇒ *T* is true. An example helps to understand why this is the case.

A common error made by novices to logic is to confuse a statement and its **converse**.

A quick check of the truth tables for *P* ⇒ *Q* and *Q* ⇒ *P* will show you that these expressions are not logically equivalent. We can see this more intuitively from the following example.

A useful tool when proving conditionals later will be to use the **contrapositive** of a conditional statement.

The logical equivalence of ¬*B* ⇒ ¬*A* and *A* ⇒ *B* is demonstrated in [Figure 3.3](#chapter3.xhtml#fig3_3).

![Figure 3.3 Logical equivalence of the contrapositive](images/fig3_3.jpg)

[Figure 3.3](#chapter3.xhtml#b3fig3_3) Logical equivalence of the contrapositive

Thus, the contrapositive of a true statement is always a true statement.

One last logical operator that we will define is called the **biconditional**.

The truth table for the biconditional is given in [Figure 3.4](#chapter3.xhtml#fig3_4).

![Figure 3.4 Truth table for biconditional](images/fig3_4.jpg)

[Figure 3.4](#chapter3.xhtml#b3fig3_4) Truth table for biconditional

## 3.6 Quantifiers

While it is easy to use logical operators for finite sets, we need additional notation when making statements about larger sets. For this, we introduce two **quantifiers**, namely the universal or “for all” quantifier ∀ and the existential or “there exists” quantifier ∃.

These quantifiers can be alternated to make more complex mathematical statements. It is important to note that the *order* of the quantifiers matters and changing the order can greatly change the meaning of the statement.

## 3.7 Big-O Notation

Quantifiers are the basis of asymptotic notation that is used ubiquitously in computer science. You may have encountered Big-O notation when analyzing the running time of an algorithm you were studying. You'll get a taste of how this is defined using quantifiers in this section.

Say that you have an algorithm that on input of size *n* performs *f*(*n*) = 2*n* + 3 computational operations. For practical purposes, the +3 in the formula is not very relevant as it is going to contribute very little when *n* gets large. Even the coefficient of 2 in the formula is not very important when we want to study the growth of the function *f*. In Big-O notation, we say that *f* is *O*(*n*) or linear in *n*.

The mathematical definition of Big-O is as follows:

In other words, we can say that the function *f* is bounded by *g* times some constant factor for sufficiently large values of *n*. This definition allows us to categorize the growth rate of functions into ones such as linear (*O*(*n*)) or quadratic (*O*(*n*²)).

For more on asymptotic notation, see [Appendix D](#appD.xhtml#appD).

## 3.8 Negating Logical Statements

You will at times need to negate logical statements. For example, negating statements is really important for writing while loops because you will want to negate the stopping condition to get the while condition.

To negate unquantified statements, we can apply De Morgan's laws to get that the negation of *P* ∧ *Q* is ¬*P* ∨ ¬*Q* and the negation of *P* ∨ *Q* is ¬*P* ∧ ¬*Q*

To negate quantified statements, we have to flip universal (∀) and existential (∃) quantifiers before negating the innermost statement.

## 3.9 Chapter Summary and Key Concepts

*   A **logical statement** is a mathematical statement that takes on the values **true** or **false**.
    
*   Commonly used **logical operations** performed on logical statements include **conjunction (and), disjunction (or)**, and **negation (not)**.
    
*   **Truth tables** can be used to compute logical operations and to show that two logical expressions are **logically equivalent**.
    
*   **Conditional statements** are used for logical conditionals or implication. The **contrapositive** of a statement is logically equivalent to the original statement. A conditional statement is different from its **converse**.
    
*   The **for all ∀ quantifier** and **there exist ∃ quantifier** allow us to make quantified statements for the elements of a set.
    
*   **Big-O notation** allows us to measure the rate of growth of functions, with applications such as expressing the running time of an algorithm.
    
*   Logical statements can be **negated** by carefully switching ∀/∃ and negating the innermost statement.
    

## Exercises

### Exercises for 3.2

Determine whether each of the following statements is true or false. Give a one line explanation for each.

*   3.1 (Assume that *x* = 3) *x* ≤ 2
    
*   3.2 (Assume that *x* = 3) *x* < 3
    
*   3.3 (Assume that *x* = 3) (*x* ≤ 3) ∧ (*x* ≤ 2)
    
*   3.4 (Assume that *x* = 3) (*x* ≤ 3) ∨ (*x* ≤ 2)
    
*   3.5 (Assume that *x* = 3 and *y* = 4) (*x* < *y*) ∧ (*x* + 1 ≤ *y*)
    
*   3.6 Every number is either even or odd.
    
*   3.7 For every number, there is always a bigger number.
    
*   3.8 For every natural number, there is always a smaller natural number.
    
*   3.9 For all integers *x* and *y*, *x* + *y* is an integer.
    
*   3.10 For all integers *x* and *y, x* / *y* is a real number.
    

### Exercises for 3.3

Write each of the following statements in symbolic form in terms of ¬, ∧, and ∨ operations.

*   3.11 The value *x* is bigger than zero but smaller than ten.
    
*   3.12 The value *x* is at least zero and at most ten.
    
*   3.13 The value *x* is smaller than zero or at least eleven.
    
*   3.14 The value *x* is not bigger than six.
    
*   3.15 The value *x* is not bigger than six and is not smaller than four.
    
*   3.16 All three values *x, y, z* are equal to ten.
    
*   3.17 At least one of the values *x, y, z* is equal to ten.
    
*   3.18 Exactly one of the values *x, y, z* is equal to ten.
    
*   3.19 Exactly two of the values *x, y, z* are equal to ten.
    
*   3.20 The value *year* is divisible by four, but when it is divisible by 100 it must also be divisible by 400. (This is the condition for a year to be a leap year.) You can use the % operation for computing the remainder from division.
    
*   3.21 The value *year* is not a leap year. (See the previous problem for computing if a year is a leap year.)
    

### Exercises for 3.4

Show whether the following pairs of expressions are equivalent by creating truth tables for them. Be sure to show each of the intermediate steps for each expression.

*   3.22 *A* ∧ *A* and *A*
    
*   3.23 *A* ∨ *A* and *A*
    
*   3.24 *A* ∧ *B* and *B* ∧ *A*
    
*   3.25 *A* ∨ *B* and *B* ∨ *A*
    
*   3.26 *A* ∧ (*A* ∨ *B*) and *B*
    
*   3.27 *A* ∧ (*A* ∨ *B*) and *A*
    
*   3.28 *A* ∨ (*A* ∧ *B*) and *B*
    
*   3.29 *A* ∨ (*A* ∧ *B*) and *A*
    
*   3.30 (*A* ∧ *B*) ∧ *C* and *A* ∧ (*B* ∧ *C*)
    
*   3.31 (*A* ∨ *B*) ∨ *C* and *A* ∨ (*B* ∨ *C*)
    
*   3.32 *A* ∧ (*B* ∨ *C*) and (*A* ∧ *B*) ∨ (*A* ∧ *C*)
    
*   3.33 *A* ∨ (*B* ∧ *C*) and (*A* ∨ *B*) ∧ (*A* ∨ *C*)
    

### Exercises for 3.5

Write each of the following statements in the form *P* ⇒ *Q* or *P* ⇔ *Q*, stating the values of *P* and *Q* for each.

*   3.34 Your code works correctly precisely when it passes all your test cases.
    
*   3.35 If a number is divisible by 4 it must be divisible by 2.
    
*   3.36 The sum of two numbers is an integer if both numbers are integers.
    
*   3.37 It is safe to divide by *x* if *x* ≠ 0.
    
*   3.38 It is safe to divide by *x* only if *x* ≠ 0.
    

Show whether the following pairs of expressions are equivalent by creating truth tables for them. Be sure to show each of the intermediate steps for each expression.

*   3.39 *A* ∨ *B* and ¬*B* ⇒ *A*
    
*   3.40 *A* ∨ *B* and ¬*A* ⇒ *B*
    
*   3.41 *A* ∧ *B* and *A* ⇒ ¬*B*
    
*   3.42 *A* ⇔ *B* and (¬*A* ∨ *B*) ∧ (*A* ∨ ¬*B*)
    
*   3.43 (*A* ⇒ *B*) ∧ (*A* ⇒ *C*) and *A* ⇒ (*B* ∧ *C*)
    
*   3.44 (*A* ⇒ *B*) ∨ (*A* ⇒ *C*) and *A* ⇒ (*B* ∨ *C*)
    
*   3.45 (*A* ⇒ *C*) ∧ (*B* ⇒ *C*) and (*A* ∧ *B*) ⇒ *C*
    
*   3.46 (*A* ⇒ *C*) ∧ (*B* ⇒ *C*) and (*A* ∨ *B*) ⇒ *C*
    

### Exercises for 3.6

Write the following as English statements with no mathematical notation.

*   3.47 *n* ∈ ℕ, 2*n* ∈ ℕ
    
*   3.48 *n* ∈ ℝ, *n*/2 ∈ ℝ
    
*   3.49 *S* ∈ 𝒫(*A*), *S* ⊆ *A*
    
*   3.50 *n* ∈ ℤ, ∃*m* ∈ *Z*, *m* < *n*
    
*   3.51 *n* ∈ ℕ, ∃*l*, *m* ∈ ℕ, *n* = *l* + *m*
    
*   3.52 *n* ∈ ℕ, ∃*s* ∈ {0, 1}^(\*), |*s*| = *n*
    
*   3.53 *s* ∈ {0, 1}^(\*), ∃*q*, *r* ∈ {0, 1}^(\*), *s* = *q**r*
    

### Exercises for 3.7

Show the following Big-O relationships by giving constants *c* and *n*[0] in each case and showing that they work.

*   3.54 3*n* + 4 ∈ *O*(*n*)
    
*   3.55 7*n* − 2 ∈ *O*(*n*)
    
*   3.56 2*n*² + 4 ∈ *O*(*n*²)
    
*   3.57 3*n*² − 2*n* + 4 ∈ *O*(*n*²)
    
*   3.58 *n*³ − *n*² + *n* − 1 ∈ *O*(*n*³)
    

### Exercises for 3.8

Rewrite the following statements into mathematical form and then negate them.

*   3.59 The value *x* is bigger than zero and smaller than ten.
    
*   3.60 The values *x* and *y* are both equal to ten.
    
*   3.61 The values *x, y, z* are all equal.
    
*   3.62 The values *x, y, z* are all different.
    
*   3.63 The Boolean value *hasWon* or *hasLost* is true
    
*   3.64 The Boolean value *hasWon, hasLost*, or *isTied* is true
    

Negate the following quantified statements.

*   3.65 *n* ∈ ℝ, 2*n* ∈ ℝ
    
*   3.66 ∃*n* ∈ ℤ, 1/*n* ∉ ℝ
    
*   3.67 *n* ∈ ℕ, ∃*m* ∈ ℕ, *m* < *n*
    
*   3.68 *n* ∈ ℕ, ∃*l*, *m* ∈ ℕ, *n* = *l* + *m*
    
*   3.69 *n* ∈ ℕ, ∃*s* ∈ {0, 1}^(\*), |*s*| = *n*
    
*   3.70 *s* ∈ {0, 1}^(\*), ∃*q*, *r* ∈ {0, 1}^(\*), *s* = *q**r*
    
*   3.71 ∃*w* ∈ *Σ*^(\*), *x*, *y* ∈ *Σ*^(\*), ∃*z* ∈ *Σ*^(\*), (|*w**x*| ≤ |*y**z*|) ∨ (|*z**x*| ≤ |*y**w*|)
    

# Chapter 4Nondeterministic Finite Automata

DOI: [10.1201/9781003383284-4](https://doi.org/10.1201/9781003383284-4)

## 4.1 Why You Should Care

Nondeterministic Finite Automata (NFAs) allow us to create simpler, often smaller, automata for the same language. They are a generalization of DFAs that add in a property called nondeterminism. While nondeterminism is not something that any real computer can exhibit, it is an important concept for much of theoretical computer science. In particular, in later courses you will learn about hard NP-complete problems for which nondeterminism is an integral concept to understand.

## 4.2 Why NFAS Can be Simpler Than Dfas

We will start with an example of a language that is tricky to get a correct DFA for and then see how to create an exceedingly simple NFA for it. Consider the language *L* = {*s* ∈ {0, 1}^(\*) : *s* ends in 010101}. A DFA for this language is given below:

This DFA works by having states for strings that end in each of the following prefixes of 010101: 0, 01, 010, 0101, 01010, and 010101 (states *q*[1] through *q*[6]). However, you have to be careful about where each transition goes to maintain the correct prefix property for each state, making the diagram fairly complicated.

In contrast, consider an NFA for the same language in the following example:

Let us use this example to understand a few differences between NFAs and DFAs. You may first notice that the state *q*[0] has two possible destinations on a 0. Nondeterminism means that the NFA is able to follow either transition. The diagram is also a lot simpler because there are no transitions for many state/symbol pairs—for example, there is no transition from *q*[1] on a 0. These are two of the major differences between NFAs and DFAs. The other big difference to understand is how strings are accepted.

An NFA accepts a string if there exists a legal path from *q*[0] to an accepting state while traversing the string. For example, the string 010101 is accepted by the NFA since it can follow the transitions to *q*[1] on the first 0, to *q*[2] on the first 1, and so on, until it reaches the accepting state *q*[6]. Importantly, there may be other paths that don't lead to an accepting state, but this doesn't change the fact that an accepting path exists. For example, an alternate processing of string 010101 would be to stay at *q*[0] and thus reject. Yet another rejecting path would be to stay at *q*[0] for 0101 and then get to *q*[2] on the final 01. However, since there does exist at least one accepting path, we ignore all the rejecting paths and conclude that 010101 is accepted by the NFA.

Now, to understand why this NFA accepts the correct language, we will see that it accepts all strings that end in 010101 and no others. For any string that does end in 010101, we can self-loop at *q*[0] until such time that we arrive at the sixth last symbol and then follow the transitions to *q*[6]. Conversely, the only strings that can be accepted must end in 010101 as that is the sequence that must be followed to arrive at the only accepting state *q*[6]. Also note that there are no transitions out of *q*[6], so the string really must end in 010101 to be accepted.

## 4.3 More Example Nfas

This last example shows us a way to easily create an NFA for any finite language.

This example shows an easy way to design an NFA that accepts the union of two regular languages—we can simply create NFAs for the two languages and then create an NFA that nondeterministically chooses between them so that the strings from both languages are accepted.

## 4.4 Formal Definition of an NFA

Now that you have seen some examples, we can see a formal definition for an NFA. An NFA is formally defined by a 5-tuple (*Q*, *Σ*, *δ*, *q*[0], *F*), where *Q* is the set of states, Σ is the input alphabet, *δ* : *Q* × *Σ* → 𝒫(*Q*) is the transition function, *q*[0] is the start state, and *F* is the set of final or accepting states.

Note that the mathematical definition is nearly identical to that of a DFA and only *δ* is really different. The *δ* function's output is now a *set* of states since transitions can now go to multiple states from any state/symbol pair. In the case that a transition is missing, the output state of *δ* is the empty set (∅).

## 4.5 Language of an NFA

With the formal definition of an NFA in hand, let us see how to mathematically define which strings an NFA accepts.

At first glance the above quantified formula looks quite intimidating. However, we can break it down to see that the idea is not very complex. It says that the string *s* = *s*[1]*s*[2]*s*[3]…*s*[*n*] will be accepted if we can find a sequence of states *p*[0] through *p*[*n*] (where *p*[0] is just defined to be the start state *q*[0]) such that after each symbol *s*[*i*] (1 ≤ *i* ≤ *n*) we can use a transition in *δ* that takes us from state *p*[*i* − 1] to state *p*[*i*] on symbol *s*[*i*] and that the last state we reach (*p*[*n*]) must be an accepting state. We can see this using an example.

## 4.6 Subset Construction

The NFA is what is called a generalization of the DFA because it can do all that a DFA can do. In particular, we can think of a DFA as an NFA that has exactly one transition defined for each state/symbol pair. This might seem to imply that NFAs are more powerful than DFAs. However, we will see next that DFAs are capable of accepting all the languages that NFAs can accept showing that they are in fact equivalent in the languages that they can accept.

We will show that DFAs are as powerful as NFAs constructively by giving an algorithm that can convert any NFA into a DFA with the same language. This algorithm is known as the Subset Construction algorithm. For any NFA, we construct a DFA that has as its states sets of states from the NFA. The complete Subset Construction procedure is given in [Algorithm 4.1](#chapter4.xhtml#algo4_1).

The algorithm works by creating a DFA that has as states the *sets of states* of the NFA. Intuitively, each state of the DFA (a set of states of the NFA) represents the set of states that a string can reach. We then have to add in the transitions from each state appropriately. If the number of states of the DFA is *n*, we may have as many as 2^(*n*) subsets of these states. However, in practice the number we need often turns out to be a lot smaller. We only create the states that are necessary by adding in new states as needed. We start at the state {*q*[0]} since *q*[0] is the unique starting state of the NFA and add any new states reachable from it. We continue this process until there are no new states and every state has all its transitions defined for it.

Since we can see that any NFA can be converted to a DFA by the Subset Construction algorithm, and any DFA can be trivially converted to an NFA, this means that DFAs and NFAs accept the same languages. In other words, we can now give an alternative definition for regular languages.

## 4.7 NFAS with *λ* Transitions

There is a variation of the NFA with *λ*\-transitions called a *λ*\-NFA. A *λ*\-transition can be followed while not consuming a character of the string. For example, if the language is the union of two languages with simple NFAs, we can create an NFA with the union of their languages by adding initial *λ*\-transitions, as seen in the following example:

The formal definition of an *λ*\-NFA is identical to that of an NFA except that we now add transition rules for *δ* on each state on a *λ* as seen in this example.

We can also convert a *λ*\-NFA into a DFA using a procedure similar to the Subset Construction algorithm. The only difference will be that we have to make sure to also follow *λ*\-transitions when determining what set of states can be reached from any state.

## 4.8 Chapter Summary and Key Concepts

*   **Nondeterminism** is an important concept in computer science. A **nondeterministic finite automaton (NFA)** can nondeterministically transition between states.
    
*   The transition function for an NFA outputs a **set of states** that can be reached on a given state, character pair.
    
*   A string is accepted by an NFA if **there exists a path for it from the start state to an accepting state**.
    
*   The **Subset Construction** algorithm can be used to convert any NFA into a DFA.
    
*   A **regular language** is one that has a DFA or an NFA that accepts it.
    
*   A variation of the NFA, called the *λ* -**NFA**, allows for *λ*\-transitions to go from a state to another state without consuming a character of the string.
    

## Exercises

Give a sequence of states that show that the following strings are accepted by the following NFAs:

*   4.1 10010101 for the NFA in [Example 4.2](#chapter4.xhtml#exam4_2)
    
*   4.2 0011 for the NFA in [Example 4.3](#chapter4.xhtml#exam4_3)
    
*   4.3 01010 for the NFA in [Example 4.4](#chapter4.xhtml#exam4_4)
    
*   4.4 1111 for the NFA in [Example 4.6](#chapter4.xhtml#exam4_6)
    
*   4.5 101010 for the NFA in [Example 4.6](#chapter4.xhtml#exam4_6)
    
*   4.6 ababab for the NFA in [Example 4.8](#chapter4.xhtml#exam4_8)
    
*   4.7 baaab for the NFA in [Example 4.8](#chapter4.xhtml#exam4_8)
    

Draw nondeterministic finite automata (that are not also deterministic ones) with no *λ* transitions for the following languages:

*   4.8 {*w* ∈ {0, 1}^(\*) : *w* ends in 00}
    
*   4.9 {*w* ∈ {0, 1}^(\*) : *w* has 01 as a substring}
    
*   4.10 {*w* ∈ {0, 1}^(\*) : *w* has 01 or 10 as a substring}
    
*   4.11 {*w* ∈ {*a*, *b*}^(\*) : *w* ends in ab or ba}
    
*   4.12 {*w* ∈ {0, 1}^(\*) : *w* starts with a 0 and ends with a 1}
    
*   4.13 {*w* ∈ {0, 1}^(\*) : *w* starts with 00 and ends with 11}
    
*   4.14 {*a*}^(\*) ∪ {(*a**b*)^(*n*) : *n* ≥ 1}
    
*   4.15 {*a*^(*n*)*b*^(*m*) : *n* ≥ 0, *m* ≥ 1}
    
*   4.16 {0^(*p*)1^(*q*)0^(*r*) : *p* ≥ 1, *q* ≥ 0, *r* ≥ 1}
    
*   4.17 {*w* ∈ {0, 1}^(\*): the third character from the end in *w* is 0}
    
*   4.18 {*w* ∈ {0, 1}^(\*): at least one of the last three characters from the end is a 0}
    
*   4.19 {*w* ∈ {0, 1}^(\*) : *w* does not have 01 as a substring}
    

Convert the following NFAs to DFAs using the Subset Construction algorithm:

*   4.20 The NFA in [Example 4.4](#chapter4.xhtml#exam4_4)
    
*   4.21 The NFA in [Example 4.5](#chapter4.xhtml#exam4_5)
    
*   4.22 The NFA in [Example 4.8](#chapter4.xhtml#exam4_8)
    

# Chapter 5Regular Expressions

DOI: [10.1201/9781003383284-5](https://doi.org/10.1201/9781003383284-5)

## 5.1 Why You Should Care

Regular expressions are a shorthand way to express regular languages. By using combinations of just three operations, we can express any regular language. In addition to their connection with regular languages, regular expressions are used extensively in string matching in text search and modern text editors, as well as for search utilities for the Unix command line.

## 5.2 Why Regular Expressions

Suppose that you are doing a research project in which you are looking up all winners of the Turing award (the computer science equivalent of the Nobel Prize) and you find a web page that has the list on it. You'd like to get your hands on the list, but it is encoded using HTML (HyperText Markup Language) that looks something like this:

```
<li><span>1966</span><a   href="/perlis">Perlis, Alan J</a></li>
<li><span>1967</span><a   href="/wilkes">Wilkes, Maurice V</a></li>
<li><span>1968</span><a   href="/hamming">Hamming, Richard W</a></li>
<li><span>1968</span><a   href="/minsky">Minsky, Marvin L</a></li>
...
```

You figure out the code for scraping this web page using your language of choice and now have the task of extracting the names from this HTML. While it would be a good problem-solving exercise with string processing to get each of the names, a far better way to solve this problem is to use a tool called regular expressions. By simply making the observation that each line above is of the form  < li > < span > YEAR < /span > < a href="URL" > NAME < /a > < /li >, where YEAR is the year they won the award, URL is the URL (uniform resource locator) for their page, and NAME is the name of the winner, you can get all the names easily with a couple lines of code. You'll see how to do this later in this chapter.

## 5.3 Regular Expression Operations

The three operations for regular expressions are union (+), concatenation (⋅), and Kleene star (^(\*)). The union operation is identical to set union.

The concatenation operation allows for concatenation of two regular expressions to represent the set of strings that have a string from the first expression followed by a string from the second.

Finally, the Kleene star operation on a regular expression generates the set of strings consisting of zero or more strings from the regular expression.

It is worth paying attention to the precedence of the above three operations. The Kleene star operation has the highest precedence in that it applies to the smallest sequence of characters before it that make up a valid regular expression. The concatenation operation is next in precedence and union comes last. Parentheses can always be added to group expressions.

You may have noticed that in all the examples above the expression is said to represent the set. This is an important distinction—the type of a regular expression is not a set, but its own type that represents a set. More specifically, we will use the notation *L*(*r*) to represent the language of a regular expression *r*.

For convenience, we allow shorthand notation for strings to appear in regular expressions. Note that the exponent must always be a fixed natural number—we do not allow variables in the exponent.

## 5.4 Formal Definition of Regular Expressions

Regular expressions are defined recursively as follows.

We can build fairly complex expressions using these rules, as seen next.

## 5.5 Applications

Many programming languages have support for regular expressions as you can use them to search through large bodies of text to find substrings that are formatted like phone numbers or addresses. Several advanced text editors will also allow you to perform searches using regular expressions.

Regular expressions are invaluable when you are learning the command line in Linux. For example, say that you want to search for all files in a folder that start with the letter a. You would do this typing ls a\* into the terminal. This invokes Linux's list command ls and specifies that only the files that have an a at the start should be shown. Here, the \* symbol corresponds to the regular expression *Σ*^(\*), so any string (including the empty string) can match the end of the filename. Similarly, if you want all files that start with an a and end in the extension .txt, you would use the following command: ls a\*.txt. If you want to find all files that contain the string Lall, you would use this command: ls \*Lall\*.

You also have the ability to match single characters using the symbol ?. For example, to match all filenames that start FILE and then have a single character, you could use: ls FILE? or if you want all files that have names exactly three characters long, you would use ls ???.

## 5.6 Regular Expressions in Python

Python has a package called re 

The following table contains some of the special syntax for regular expressions in Python.

 
| syntax || meaning || example || in words |
| --- | --- | --- | --- |
| \[ \] || a set of characters || \[a-zA-Z\] || the letters a to z and A to Z |
| --- | --- | --- | --- |
| \* || zero or more instances || \[a-z\]\* || zero or more letters from a to z |
| + || one or more instances || \[a-z\]+ || one or more letters from a to z |
| {} || exact number of instances || \[a-z\]{3} || exactly three letters from a to z |
| \\d || a digit (0-9) || \\d{3} || a number with exactly 3 digits |
| \\w || the characters a-z, A-Z, 0-9, \_ || \\w+ || one or more characters from a-z, A-Z, 0-9, \_ |

We can now use this to see how to extract the information we are looking for from the HTML example from earlier in this chapter.

## 5.7 Chapter Summary and Key Concepts

*   Regular expressions have three operations: **union (+), concatenation (⋅)**, and **Kleene star (\*)**.
    
*   Regular expressions are formally defined by these rules:
    
    *   – The empty set ∅ is a regular expression.
        
    *   – The empty string *λ* is a regular expression.
        
    *   – For any *s* ∈ *Σ*, *s* is a regular expression.
        
    *   – For any regular expressions *r*[1] and *r*[2], *r*[1] + *r*[2] is a regular expression.
        
    *   – For any regular expressions *r*[1] and *r*[2], *r*[1] ⋅ *r*[2] is a regular expression.
        
    *   – For any regular expression *r*[1], (*r*[1])^(\*) is a regular expression.
        
*   Regular expressions are used in some **text editors** and on the **Linux command line**.
    
*   Regular expressions can be computed in programming languages such as **Python**.
    

## EXERCISES

List the strings of length at most 4 for each of the following languages in shortlex order (see [Section 1.10](#chapter1.xhtml#sec1_10)):

*   5.1 00(0 + 1)^(\*)
    
*   5.2 0(0 + 1)^(\*)0
    
*   5.3 (0 + 1)^(\*)0(0 + 1)^(\*)1(0 + 1)^(\*)
    
*   5.4 (0 + 1)²1(0 + 1)
    
*   5.5 (1 + 00)^(\*)
    

Give regular expressions for the following languages:

*   5.6 Every string over {0, 1}
    
      
    $$\\begin{array}{l} {\\Sigma = \\{ a,b\\}} \\\\ \\end{array}$$  
    
*   5.7 Starts with *b*
    
*   5.8 Ends with *ab*
    
*   5.9 Contains at least one *a*
    
*   5.10 Contains the substring *aab*
    
*   5.11 Contains the characters *a, a, b* in that order but not necessarily next to one another
    
*   5.12 The 4th symbol is an *a*
    
*   5.13 The 4th last symbol is a *b*
    
*   5.14 Strings of length divisible by 3
    
*   5.15 Contains exactly one *a*
    
*   5.16 Contains exactly two *b*s
    
*   5.17 Contains at most two *b*s
    
*   5.18 Contains at least one *a* and one *b* (in any order)
    
*   5.19 Contains an even number of *a*s and any number of *b*'s
    
*   5.20 Does not contain the substring *aa*
    
*   5.21 Does not end *ab*
    
      
    $$\\begin{array}{l} {\\Sigma = \\{ a - z,0 - 9,\\underset{―}{}\\}} \\\\ \\end{array}$$  
    
*   5.22 Valid variable name (cannot start with a digit, ignore reserved words)
    
*   5.23 Valid password (at least one letter and one digit)
    
      
    $$\\begin{array}{l} {\\Sigma = \\{ 0 - 9, - \\}} \\\\ \\end{array}$$  
    
*   5.24 Valid integer (no leading 0s, but could be negative)
    
*   5.25 Phone numbers of the form 555-555-5555
    

Write Python code to search strings for the following patterns:

*   5.26 Phone numbers of the form (555)-555-5555
    
*   5.27 Dates of the form MM-DD-YYYY (you don't have to check that the days or months are valid)
    
*   5.28 Email addresses of the form [username@domain.com](http://username@domain.com) that could contain the symbols a-z, A-Z, 0-9, and at most one period.
    
*   5.29 Email addresses that may have multiple periods (e.g., [username@domain.co.uk](http://username@domain.co.uk))
    

# Chapter 6Equivalence of Regular Languages and Regular Expressions

DOI: [10.1201/9781003383284-6](https://doi.org/10.1201/9781003383284-6)

## 6.1 Why You Should Care

In this section we will see that the languages accepted by DFAs and NFAs are exactly the same as the languages of regular expressions. This means that we can use these two ideas interchangeably. Moreover, we will prove the equivalence constructively, which means that we will have a way to design a regular expression from any DFA and vice versa.

## 6.2 Converting a Regular Expression to a *λ*\-NFA

We will first see a procedure for converting any regular expression to a *λ*\-NFA. This *λ*\-NFA can then be converted to a DFA using the subset construction technique from [Chapter 4](#chapter4.xhtml). Recall from [Section 5.4](#chapter5.xhtml#sec5_4) that regular expressions are defined recursively using the following rules:

1.  The empty set has the regular expression ∅.
    
2.  The set {*λ*} has the regular expression *λ*.
    
3.  For each symbol *s* ∈ *Σ*, the set {*s*} has the regular expression *s*.
    
4.  For any regular expressions *r*[1] and *r*[2], the set *L*(*r*[1]) ∪ *L*(*r*[2]) has the regular expression *r*[1] + *r*[2].
    
5.  For any regular expressions *r*[1] and *r*[2], the set {*s*[1] ⋅ *s*[2] : *s*[1] ∈ *L*(*r*[1]) ∧ *s*[2] ∈ *L*(*r*[2])} has the regular expression *r*[1] ⋅ *r*[2].
    
6.  For any regular expression *r*[1], the set {*s*[1]…*s*[*n*] : *n* ≥ 0 ∧ *s*[1], …, *s*[*n*] ∈ *L*(*r*[1])} has the regular expression (*r*[1])^(\*).
    

The *λ*\-NFAs for the languages ∅, {*λ*}, and {*a*} for any *a* ∈ *Σ* are given in [Figures 6.1a](#chapter6.xhtml#fig6_1), [6.1b](#chapter6.xhtml#fig6_1), and [6.1c](#chapter6.xhtml#fig6_1). Using these as our starting point, we see how to construct expressions that involve unions, concatenation, and Kleene \*.

![Figure 6.1 λ-NFAs for simple regular expressions](images/fig6_1.jpg)

[Figure 6.1](#chapter6.xhtml#b6fig6_1) *λ*\-NFAs for simple regular expressions

We can construct a *λ*\-NFA for the union of two languages for which we have *λ*\-NFAs by using *λ*\-transitions from a new start state to the start states of the two *λ*\-NFAs. [Figure 6.2](#chapter6.xhtml#fig6_2) shows a scheme for how you can do this for any pair of *λ*\-NFAs.

![Figure 6.2 A λ-NFA for the union of the languages of two λ-NFAs](images/fig6_2.jpg)

[Figure 6.2](#chapter6.xhtml#b6fig6_2) A *λ*\-NFA for the union of the languages of two *λ*\-NFAs

We can concatenate the language of two *λ*\-NFAs by adding *λ*\-transitions from each of the accepting states of the first *λ*\-NFA (and making them non-accepting) to the start state of the second *λ*\-NFA. This is illustrated in the scheme shown in [Figure 6.3](#chapter6.xhtml#fig6_3).

![Figure 6.3 A λ-NFA for the concatenation of the languages of two λ-NFAs](images/fig6_3.jpg)

[Figure 6.3](#chapter6.xhtml#b6fig6_3) A *λ*\-NFA for the concatenation of the languages of two *λ*\-NFAs

Lastly, we can take the Kleene \* of the language of any *λ*\-NFA by using the scheme in [Figure 6.4](#chapter6.xhtml#fig6_4). We create a new start state (labeled *q*[0]^′ in the figure), make it accepting, and then add a *λ*\-transition to the start state of the original *λ*\-NFA. We then add *λ*\-transitions from each accepting state back to the start state *q*[0]^′.

![Figure 6.4 A λ-NFA for the Kleene \* of the language of a λ-NFA](images/fig6_4.jpg)

[Figure 6.4](#chapter6.xhtml#b6fig6_4) A *λ*\-NFA for the Kleene \* of the language of a *λ*\-NFA

We can create an NFA for any regular expression by repeating these three procedures as needed.

## 6.3 Converting a Dfa to a Regular Expression

We can convert DFAs to regular expressions using a state elimination algorithm. This is useful in and of itself because there are some regular languages for which it is easy to define a DFA, but hard to come up with a regular expression. This algorithm then can be used to extract a regular expression from a DFA. Before formally defining the algorithm, let us see a few simple examples.

Now, it will not always be the case that the starting state is the only accepting one. In these situations, we must eliminate states down to just the start state and each accepting state. We see an example of this next.

We can now generalize the above two examples for any DFA. If we have eliminated down to the start state and it is an accepting state with a self-loop with expression *R*, then the regular expression for the original DFA was (*R*)^(\*). If there is a non-starting accepting state, then we eliminate down to the start state and the accepting state as in [Figure 6.5](#chapter6.xhtml#fig6_5) and the final regular expression will be (*R* + *S**U*^(\*)*T*)^(\*)*S**U*^(\*).

![Figure 6.5 General form for when the accepting state is not the start state](images/fig6_5.jpg)

[Figure 6.5](#chapter6.xhtml#b6fig6_5) General form for when the accepting state is not the start state

We are now ready to see the full algorithm for state elimination ([Algorithm 6.1](#chapter6.xhtml#algo6_1)). Note that if *q*[0] is an accepting state, we also eliminate down to just *q*[0] by itself.

Let us see one more example with multiple accepting states. We will see how the State Elimination algorithm works on the DFA in [Figure 6.6](#chapter6.xhtml#fig6_6).

![Figure 6.6 Example DFA for State Elimination algorithm](images/fig6_6.jpg)

[Figure 6.6](#chapter6.xhtml#b6fig6_6) Example DFA for State Elimination algorithm

Finally, to get the set of strings that can reach any of the accepting states {*q*[0], *q*[1], *q*[3]}, we union the expressions from [Examples 6.6](#chapter6.xhtml#exam6_6), [6.7](#chapter6.xhtml#exam6_7), and [6.8](#chapter6.xhtml#exam6_8), to get the expression

  
$$\\begin{array}{ll} {(00 + 11^{\\ast}00 + (01 + 11^{\\ast}01)1^{\\ast}0)^{\\ast}(01 + 11^{\\ast}01)1^{\\ast}} & {+} \\\\ {(00 + 011^{\\ast}0 + 11^{\\ast}(00 + 011^{\\ast}0))^{\\ast}11^{\\ast}} & {+} \\\\ {(00 + 011^{\\ast}0 + 11^{\\ast}(00 + 011^{\\ast}0))^{\\ast}.} & \\\\ \\end{array}$$  

While this formula is long and complicated, you can verify that it correctly captures the strings that get to each state. Here, *q*[0] is reachable by strings that have an even number of 0s and don't end in 1, *q*[1] is reachable by strings with an even number of 0s and do end in 1, and *q*[3] is reachable by strings that have an odd number of 0s and do end in 1.

## 6.4 Another Definition for Regular Languages

Now that we have established that the language of every finite automaton has a regular expression and vice versa, we can expand our definition of regular languages even further.

## 6.5 Chapter Summary and Key Concepts

*   There is a procedure for converting any regular expression into a *λ*\-NFA.
    
*   Any DFA can be converted to a regular expression using the **State Elimination** algorithm.
    
*   A **regular language** is one that has a DFA, NFA, or regular expression.
    

## EXERCISES

Give *λ*\-NFAs *using the algorithm in this chapter* for the regular expressions below:

*   6.1 *a**b*(*a* + *b*)
    
*   6.2 (*a* + *b**a*)^(\*)
    
*   6.3 *a**b* + (*a**b*)^(\*)
    
*   6.4 (*a* + *b*)^(\*)(*a**b*)(*a* + *b*)^(\*)
    
*   6.5 (*a* + *b**b*)^(\*) + (*b* + *a**a*)^(\*)
    
*   6.6 (000)^(\*)
    
*   6.7 00(0 + 1)^(\*)00
    
*   6.8 0(0 + 1)^(\*)0 + 1(0 + 1)^(\*)1
    
*   6.9 (0 + 1)^(\*)0(0 + 1)²
    
*   6.10 001^(\*)00 + 110^(\*)11 + (01)^(\*)(0 + 11)^(\*)
    

Construct DFAs for the following languages and *use the state elimination algorithm in this chapter* to create a regular expression for each. Show the intermediate steps as you eliminate each state along the way.

*   6.11 {*w* ∈ {0, 1}^(\*) : *w* is of even length}
    
*   6.12 {*w* ∈ {0, 1}^(\*) : *w* has an odd number of 1s}
    
*   6.13 {*w* ∈ {0, 1}^(\*) : *w* has at least two 1s}
    
*   6.14 {*w* ∈ {0, 1}^(\*) : *w* has at most three 0s}
    
*   6.15 {*w* ∈ {0, 1}^(\*): the number of 0s in *w* is divisible by 3}
    
*   6.16 {*w* ∈ {0, 1}^(\*) : *w* does not have 01 as a substring}
    
*   6.17 {*w* ∈ {0, 1}^(\*) : *w* has an even number of 0s and an odd number of 1s}
    
*   6.18 {*w* ∈ {0, 1}^(\*) : *w* has an even number of 0s and an even number of 1s}
    
*   6.19 {*w* ∈ {0, 1}^(\*) : *w* has an odd number of 0s and an even number of 1s}
    
*   6.20 {*w* ∈ {0, 1}^(\*) : *w* has an odd number of 0s and an odd number of 1s}
    
*   6.21 {*w* ∈ {0, 1}^(\*): the number of 1s in *w* is not divisible by 4}
    

# Chapter 7Direct Proof and Closure Properties

DOI: [10.1201/9781003383284-7](https://doi.org/10.1201/9781003383284-7)

## 7.1 Why You Should Care

Proofs are the means by which we demonstrate that an algorithm does what we intend for it to do. It is usually impossible to test all possible inputs to an algorithm so we have to make a logical argument about its correctness. Making rigorous arguments then is a critical skill for a computer scientist.

## 7.2 Tips for Writing Proofs

When writing proofs, here are a few rules of thumb to keep in mind:

1.  Write in full, grammatical sentences. Don't forget punctuation, especially periods after mathematical expressions.
    
2.  Write in paragraph form.
    
3.  Show where the proof begins and ends very clearly.
    
4.  Know your audience. This will tell you how formal you have to be.
    
5.  Define variables before they are used.
    
6.  Don't start a sentence with math.
    

## 7.3 The Importance of Definitions

When making an argument, we have to start with some basic assumptions. This is particularly true in the case of **direct proofs**, where we prove statements such as “If *P* is true, then *Q* is true.” For this kind of proof, we start by assuming that *P* is true and then make a sequence of logical arguments to show that *Q* then also must be true. To help us along the way, we need to make use of **definitions**. As an example, consider the following two definitions.

We can now use these definitions to prove theorems such as the following.

This theorem can be re-written as an if/then statement as follows.

To rigorously prove such a theorem, we need to use the above definitions to introduce notation for the lengths of the string to get us started. To show the result, we will need to use a definition again. The proof of the above theorem is given below:

Notice that we start by stating the assumption and defining our variables, even if they were defined in the theorem statement. This is always the first step in a direct proof. We proceed by unpacking the definition of our assumption, in this case introducing more notation to indicate that the strings are of even and odd lengths. At this point it is helpful to jump ahead to look at what we are trying to prove—here, that the concatenated string has odd length. We can work backwards from here by seeing that we will need to show using the definition of odd length that the concatenated string has odd length in the penultimate step. This gives us a direction for how to go about the proof: we must use the notation introduced by the definition of even and odd length strings to show that that concatenated string has an odd length. All that is left is to develop the reasoning to fill in the middle of this proof.

This proof follows the style conventions mentioned previously. We must clearly show where the proof begins by making the assumption and where it ends by stating the conclusion. Every step must be written out using complete sentences with punctuation, including periods ending sentences with math in them. All the variables should be defined before they are used and no sentence should start with a mathematical expression. Here is another similar example.

Sometimes a proof needs cases. Consider the following definition and theorem.

For some direct proofs, it is easier to show the contrapositive. Recall from [Chapter 3](#chapter3.xhtml) that the contrapositive of the statement *A* ⇒ *B* is the statement ¬*B* ⇒ ¬*A*, and they are logically equivalent. An example is given below:

We sometimes get an exact characterization of a property when a conditional statement and its converse is true. To show that *A* ⇔ *B* we have to show both *A* ⇒ *B* and *B* ⇒ *A*. This is called an “if and only if” (sometimes abbreviated iff) proof.

## 7.4 Numerical Proofs

When comparing the running time of two algorithms we want to show that one is faster than the other. For example, we may have Algorithm A that on an input of size *n* needs 10*n* + 4 operations, while Algorithm B needs *n*² operations. If we were to only look at small values of *n*, it would appear that Algorithm B is better. However, we may want to show that Algorithm A is preferable for larger values of *n*. We start by trying different values of *n* until we find one for which 10*n* + 4 < *n*². After some trial and error we find that this inequality holds true when *n* = 11. But perhaps it is no longer true for some larger value (like *n* = 100) ? We can show this is not the case using a direct proof.

Here is another example.

## 7.5 Closure under Set Operations

We can use direct proofs to show that performing a variety of operations on regular languages will result in languages that are also regular. This is useful as another way to show that a language is regular. For example, showing closure under complements easily lets us see that the set

  
$$\\begin{array}{l} {\\{ s \\in \\{ a,b\\}^{\\ast}:s\\text{~doesn't\\ start\\ with\\ an~}a\\text{~or~}s\\text{~doesn't\\ end\\ with\\ a~}b\\}} \\\\ \\end{array}$$  

is regular because the complement of this set is the language of the expression *a*(*a* + *b*)^(\*)*b*, which we know is regular as it has a regular expression.

A nearly identical proof shows closure under concatenation:

As practice, use the above technique to show that the following theorem is true:

Sometimes a proof will require you to use a different version of a definition to show the result more easily. We know that there are three equivalent definitions for a regular language: the language must have a DFA, an NFA, or a regular expression. We take advantage of this in the following result:

Once we have proved some closure properties, we can even start to combine them together in our proofs. Consider the proof for closure under intersections below.

Here is another example where we can combine several properties together to show closure under set difference.

We can also show closure under the reverse operation. We define *w*^(*R*) to be the reverse of any string *w*.

We define the reverse of a language to be the set of strings that are the reverse of the strings in the language.

Rather than formally proving this claim, we will see a construction that demonstrates it for any regular language. We'll see a formal proof of the claim in [Chapter 8](#chapter8.xhtml).

Any regular language *L* must have a regular expression *E*. We will see how to take the regular expression and convert it into a regular expression *E*^(*R*) for the language *L*^(*R*). Recall that regular expressions were defined recursively using six rules in [Section 5.4](#chapter5.xhtml#sec5_4). We show how to reverse the expression for each of these rules as follows:

1.  We leave instances of ∅, *λ*, and single characters *s* ∈ *Σ* unchanged.
    
2.  If the expression is of the form *E*[1] + *E*[2], we replace it with the expression *E*[1]^(*R*) + *E*[2]^(*R*) (recursively following this procedure for the expressions *E*[1] and *E*[2]).
    
3.  If the expression is of the form *E*[1] ⋅ *E*[2], we replace it with the expression *E*[2]^(*R*) ⋅ *E*[1]^(*R*).
    
4.  If the expression is of the form (*E*[1])^(\*), we replace it with the expression (*E*[1]^(*R*))^(\*).
    

While we can verify that the reverse of expressions seems to work for all the examples (and perhaps several more that you have tried), this doesn't definitively prove that this procedure always works. We should be skeptical when something works for a few cases because it may stop working for a more complicated case. You will need to learn a proof technique called strong induction later in this book to show that this procedure does correctly reverse any expression to give the reverse of its language.

## 7.6 Chapter Summary and Key Concepts

*   Proofs are how computer scientists demonstrate the **correctness and efficiency** of their algorithms.
    
*   A proof is written for another person. Know who is your **audience** and make sure the proof is easy for them to read.
    
*   Knowing how to use **definitions** is central to understanding how to start and how to end a proof.
    
*   **Closure properties** give us an easy way to show that a language is regular.
    
*   Regular languages are **closed** under union, concatenation, Kleene star, complement, intersection, difference, and reversal.
    

## Exercises

*   7.1 Show that the concatenation of two even length strings gives an even length string.
    
*   7.2 Show that if *x* and *y* are odd length strings and *z* is an even length string that *xyz* is an even length string.
    
*   7.3 Show that if *x* and *y* are odd length strings and *z* is an even length string that *xyyz* is an odd length string.
    
*   7.4 Show that if for strings *x, y, z* if *xy* and *xz* are both odd length, then *yz* must be even length.
    
*   7.5 Show that for all *n* ≥ 8, 7*n* + 100 < 20*n*.
    
*   7.6 Show that for all *n* ≥ 101, 100*n* + 100 < *n*².
    
*   7.7 Show that for all *n* ≥ 501, 1000*n* + 1000 < 2*n*².
    
*   7.8 Show that for all *n* ≥ 3, 4*n*² + 6*n* ≤ 2*n*³.
    
*   7.9 Show that if *L*[1], *L*[2], and *L*[3] are regular languages that *L*[1] ∪ *L*[2] ∪ *L*[3] is also a regular language.
    
*   7.10 Define the *NOR* operation as *N**O**R*(*L*[1], *L*[2]) = {*x* : *x* ∉ *L*[1] ∧ *x* ∉ *L*[2]}. Show that regular languages are closed under the *NOR* operator.
    
*   7.11 The symmetric difference of two sets is the set of elements that are in exactly one of the two sets. Show that the regular languages are closed under symmetric difference.
    
*   7.12 Show that if *L*[1], *L*[2], and *L*[3] are regular languages that *L*[1] ∩ *L*[2] ∩ *L*[3] is also a regular language.
    
*   7.13 Prove that any language with exactly two strings must be regular.
    
*   7.14 Prove that any finite language must be regular.
    

# Chapter 8Induction

DOI: [10.1201/9781003383284-8](https://doi.org/10.1201/9781003383284-8)

## 8.1 Why You Should Care

Proof by induction is a key proof technique that is used extensively in computer science. It is used for proving correctness of algorithms with loops and recursion. It is also used for showing bounds on the run-time of many recursive algorithms. We'll also see how some of the results for sets and regular languages from earlier chapters can be formally proved.

## 8.2 Induction and Recursion

Consider the pseudo-code in [Algorithm 8.1](#chapter8.xhtml#algo8_1) for computing the factorial function.

Why does the above algorithm work? How do we go about proving that it always returns the correct answer? The intuitive reasoning goes something like this:

1.  When *n* = 1 (the smallest possible input), the function returns the correct answer of 1 in the second line.
    
2.  When *n* = 2, the third line of the function returns factorial(1) \* 2, which is 1 \* 2 or 2, again the correct answer.
    
3.  When *n* = 3, the third line of the function returns factorial(2) \* 3, which is 2 \* 3 or 6, again the correct answer.
    
4.  When *n* = 4, the third line of the function returns factorial(3) \* 4, which is 6 \* 4 or 24, again the correct answer.
    
5.  This pattern can be continued indefinitely until we reach any desired positive integer.
    

The idea behind proof by induction is to formalize this pattern. We have to show that the function gives the correct answer for the smallest input *n* = 1 (called the base step). We then have to show that if the function works for the case of some *n* = *k*, then it also must work for the case when *n* = *k* + 1 (called the inductive step).

Let us use the above example to write a more formal proof. A proof by induction always has four parts and you should practice writing all four parts until you become a more experienced proof-writer. These parts are:

1.  State the hypothesis
    
2.  Base step
    
3.  Inductive step
    
4.  C​onclusion
    

For ease of writing our proof, we denote the hypothesis by the function *P* to refer to it more succinctly later. The hypothesis is always a logical statement (i.e., taking on a value of true or false). A common error is to mistakenly think of *P*(*n*) as a number, which it is not.

The base step is usually the simplest part of a proof by induction. You should make sure to verify the hypothesis for the smallest possible value of *n*. This may not always be 1, depending on the result being proved.

The inductive step of the proof is where all the “work” is done. It always takes the same form: fix *k*, assume the hypothesis for *k*, prove the hypothesis for *k* + 1 while making sure to use the assumption. More specifically, before writing the induction step, it helps to write down the inductive hypothesis (*P*(*k*)) and what you are trying to prove (*P*(*k* + 1)). Here, *P*(*k*) is the statement “The factorial program on input *k* returns 1 × 2 × 3 × … × *k* ” and *P*(*k* + 1) is the statement “The factorial program on input *k* + 1 returns 1 × 2 × 3 × … × (*k* + 1).” We have to explain why it is that *P*(*k*) implies *P*(*k* + 1) for any *k* ≥ 1.

The conclusion simply summarizes the proof by induction argument. It is somewhat verbose and is almost identical in all proofs, but I recommend that you write it out after each proof to remind yourself of why it is that induction works.

A proof doesn't just convince us that an algorithm is correct, it gives us a deeper understanding of *why* the algorithm is correct. It takes away the mystery of how the algorithm works and gives us insight into how to adapt it to solve new problems. Hopefully, the above proof gave you a deeper understanding and appreciation for the recursive factorial function.

## 8.3 An Analogy for Understanding Induction

An analogy for induction is building a multi-floor building or tower. When constructing the building, it is important to make sure that the bottom-most level has a firm foundation, which is analogous to the base case of induction. We can only build the second level of the building after the first (the base) has been firmly established. Similarly, we need the second level before we can build the third level, and so on.

In an induction proof, we have to show the following two facts:

1.  The bottom level or base case is firmly established. \[Show *P*(1) is true.\]
    
2.  If any level *k* is firmly established, then the level *k* + 1 will also be firmly established. \[For all *k* ≥ 1, show that if *P*(*k*) is true then *P*(*k* + 1) is true.\]
    

Using these two facts, it is clear to see that we can build a tower of any height. The base level is firmly established by the first fact. The second level is firmly established by applying the second fact with *k* = 1 to the base case. The third level is firmly established by applying the second fact with *k* = 2 to the previous result about the second level. Continuing in this way, we can show that any level *n* ≥ 1 will be firmly established. This is illustrated in [Figure 8.1](#chapter8.xhtml#fig8_1).

![Figure 8.1 The tower analogy for induction](images/fig8_1.jpg)

[Figure 8.1](#chapter8.xhtml#b8fig8_1) The tower analogy for induction

## 8.4 Induction for Analyzing Sorting Run-Time

When analyzing the running time of sorting algorithms such as selection sort and insertion sort, it can be shown that to sort a list of *n* items takes time proportional to 1 + 2 + 3 + … + (*n* − 1) time steps. To demonstrate that these sorting algorithms take quadratic time, it helps to show that 1 + 2 + 3 + … + (*n* − 1) = *n*(*n* − 1)/2 for all *n* ≥ 1. Before proving this result, we will take a short detour to introduce some notation that you will encounter frequently in this book and in later courses.

Rather than write out long series such as 1 + 2 + 3 + … + (*n* − 1), we can use summation or sigma notation (for the Greek letter used to represent it), as follows:

  
$$\\begin{array}{l} {\\sum\\limits\_{i = 1}^{n - 1}i = 1 + 2 + 3 + \\ldots + (n - 1).} \\\\ \\end{array}$$  

In this notation, the Σ indicates summation (not to be confused with a string alphabet). The subscript (here, *i* = 1) indicates what value we start *i* at in the summation, the superscript (here, *n* − 1) indicates the (inclusive) stopping point, and the expression right after is the function that is applied to each of the values of *i* that are being summed. In this example, we are just adding up all these values of *i*.

We will now demonstrate $\\sum\\limits\_{i = 1}^{n - 1}i = n(n - 1)/2$ using induction.

Once again, note that *P*(*n*) is a logical statement (taking values true or false) and not the sum of the series. Specifically, it denotes whether or not the sum of the series is equal to the formula *n*(*n* − 1)/2.

Let us understand how the derivation above was developed. First, start with what you are assuming (*P*(*k*)), which is $\\sum\\limits\_{i = 1}^{k - 1}i = k(k - 1)/2$ and what you are trying to prove (*P*(*k* + 1)), which is $\\sum\\limits\_{i = 1}^{(k + 1) - 1}i = (k + 1)((k + 1) - 1)/2$ or $\\sum\\limits\_{i = 1}^{k}i = (k + 1)k/2$. When proving equality, we start with one side of what we are trying to prove (here, $\\sum\\limits\_{i = 1}^{k}i$) and we want to show that it is equal to the right side ((*k* + 1)*k*/2). To do this, we have to make a connection to the induction hypothesis. For proving the sum of series, this will almost always look the same: observe that the sum of the larger series is the same as the smaller one with an additional term. This is why, for this example, we break down the summation $\\sum\\limits\_{i = 1}^{k}i$ into $\\sum\\limits\_{i = 1}^{k - 1}i$ and *k* on the third line of the derivation. We can now apply the induction hypothesis to replace $\\sum\\limits\_{i = 1}^{k - 1}i$ with *k*(*k* − 1)/2 on the fourth line. Finally, we use algebra to show that we get the expression on the right-hand side of the equality we are trying to prove ((*k* + 1)*k*/2).

The conclusion step is identical to the one in the first example.

## 8.5 How Many Bit Strings are There of Length (At Most) *N*?

We'll next use induction to prove a result about the number of distinct bit strings, that is, strings of length *n* over the alphabet *Σ* = {0, 1}. There is exactly one string of length 0, namely *λ*. For length one, we have two: {0, 1}. For length two we have 4: {00, 01, 10, 11}, and for length three we have eight: {000, 001, 010, 011, 100, 101, 110, 111}. Before reading ahead, what is the pattern that you notice?

You may have noticed that the number of strings of each successive length is twice that of the length one smaller. We might then use this to make the hypothesis *P*(*n*): the number of strings of length *n* is equal to 2^(*n*). Let us see how to prove this.

Notice that this case was slightly different than the previous examples as we started from *n* = 0. The induction step also needed a slightly more sophisticated argument showing that *P*(*k*) implies *P*(*k* + 1). The approach we used earlier still works. Start by writing out the statements for *P*(*k*) and *P*(*k* + 1) fully for the problem. Then articulate why *P*(*k* + 1) is true given the fact that *P*(*k*) is true.

We can take this analysis one step further to answer the question of how many strings there are of length *at most* *n*. We know from the previous theorem that the number of strings of length *n* is exactly 2^(*n*), so the number of strings of length at most *n* must be the number of strings of lengths 0, 1, 2, …, *n*, or $\\sum\\limits\_{i = 0}^{n}2^{i}$. When *n* = 0, this is just 2⁰ or 1. When *n* = 1, we get 2⁰ + 2¹ = 3. When *n* = 2, we have 2⁰ + 2¹ + 2² = 7. When *n* = 3, it is 2⁰ + 2¹ + 2² + 2³ = 15. Do you see a pattern emerging? Try to guess the pattern before reading on.

You may have noticed that the *n*th number consistently turns out to be 2^(*n* + 1) − 1. (This is not the only way of expressing the pattern; you might have also observed that each number is one more than twice the previous, which is also correct.) Let us state this formally as a hypothesis and see how we can prove it.

Notice that this time we used the proof by induction as part of a larger proof. It is important to tell your reader that you are doing this, both in the setup to say how you will use the inductive hypothesis and in the conclusion explaining how you used the induction result for the larger proof.

## 8.6 Comparing Growth of Functions

When you later learn about running times of algorithms, you will have to compare the running time of various functions to see which ones grow quicker. We will show that the factorial function (*n*!, seen earlier in this chapter) grows faster than an exponential function (2^(*n*)). Before trying to prove this result, we should check it for small values of *n* to make sure that it checks out. From [Table 8.1](#chapter8.xhtml#tbl8_1) we can see that for small values of *n* (*n* ≤ 3), the factorial function has a smaller value than this exponential one but for larger values (*n* ≥ 4) the factorial function seems to get substantially larger with larger values of *n*.

[Table 8.1](#chapter8.xhtml#b8tbl8_1) Table for 2^(*n*) and *n*! for small values of *n*

  
| *n* || 1 || 2 || 3 || 4 || 5 || 6 || 7 |
| --- | --- | --- | --- | --- | --- | --- | --- |
| 2^(*n*) || 2 || 4 || 8 || 16 || 32 || 64 || 128 |
| *n*! || 1 || 2 || 6 || 24 || 120 || 720 || 5040 |

The table is insufficient to tell us that the inequality holds true for all bigger values, so we will prove it by induction. Note that the base and conclusion steps will be different from the earlier examples as the hypothesis will hold only for *n* ≥ 4.

While the above induction step is correct, it doesn't give a lot of insight of how it was obtained, so we'll break it down next. When proving the induction step, it is helpful to write down your assumption *P*(*k*) (here, that 2^(*k*) < *k*!) and what you are trying to prove (here, 2^(*k* + 1) < (*k* + 1)!) first. This will help you to figure out the connection between them. In this case, we start with one side of the inequality we are trying to prove (here, 2^(*k* + 1)) and figure out how it relates to our induction hypothesis (2^(*k*) < *k*!). We can make the observation that 2^(*k* + 1) is just 2 times 2^(*k*) to make that connection, as we do in the second line of the derivation. We then use the induction hypothesis to replace 2 × 2^(*k*) with 2 × *k*! in the third line, stating that we used the induction hypothesis. You should always make sure that you used the induction hypothesis somewhere in the inductive step. Next, we have to make sure that the value 2 × *k*! is at most the value (*k* + 1)! from what we are trying to prove. To make this connection, we observe that (*k* + 1)! is just (*k* + 1) × *k*! and so we really need to just show that 2 × *k*! is at most (*k* + 1) × *k*!, which it must be as 2 is less than (*k* + 1) as we assumed that *k* ≥ 4. This gives us the third line of the derivation above.

Notice how this proof is different from the previous ones in that our base case must be when *n* = 4 since *P*(1), *P*(2), *P*(3) are all false. This is a good reminder that *P*(*n*) may not always be true for all values of *n*. It is also a good cautionary example for why we must pay attention to the base case. The above induction step seems to work whenever (*k* + 1) > 2 or *k* > 1, but the hypotheses *P*(2) and *P*(3) are false, so we really needed to check to make sure that the base case was true.

## 8.7 Common Errors When Using Induction

1.  Not clearly defining the induction hypothesis: Any induction proof should start with a clear statement of the induction hypothesis *P*(*n*) and for which values it is being proved to be true.
    
2.  Treating *P*(*n*) as a number: A common error, particularly in proofs involving summations, is to treat *P*(*n*) as a number. Remember that *P*(*n*) is a logical statement and can only take on the values true and false.
    
3.  Omitting the base step: If we don't check the base case, we can run into serious issues. For example, consider the following untrue claim:
    
      
    $$\\begin{array}{l} {P(n):3^{n}\\text{~is\\ even,\\ for\\ all~}n \\geq 1} \\\\ \\end{array}$$  
    
    Proof (inductive step): Fix some *k* ≥ 1. We assume the hypothesis is true for *n* = *k*, that is 3^(*k*) is even. This means that we can write 3^(*k*) = 2*f* for some *f* ≥ 1. Then, 3^(*k* + 1) can be written as 3^(*k* + 1) = 3^(*k*) ⋅ 3 = 2*f* ⋅ 3, which means that 3^(*k* + 1) is even as it can be written as 2(3*f*).
    
    This proof must clearly be erroneous since we know that no natural number power of 3 is even. This proof breaks down because the base step does not hold—when *n* = 1, 3^(*n*) = 3 is not an even number.
    
4.  Making an error in the inductive step: When proving the inductive step, you have to make sure that the proof works for all stated values. The following is an example of an incorrect proof that all horses are the same color!
    
      
    $$\\begin{array}{l} {P(n):\\text{~every\\ horse\\ in\\ a\\ set\\ of~}n\\text{~horses\\ has\\ the\\ same\\ color,\\ for\\ all~}n \\geq 1} \\\\ \\end{array}$$  
    
    Base step: When *n* = 1, there is only one horse in the set and thus every horse in that set has the same color.
    
    Inductive step: Fix some *k* ≥ 1. We assume the hypothesis is true for *n* = *k*. When *n* = *k* + 1 we exclude the first horse and get a set of size *k* for which we know that all the horses are the same color (by the induction hypothesis). Again, doing the same but this time excluding the last horse, we get that all the horses in this set are the same color. Now, since both sets have horses of the same color, it follows that all the *k* + 1 horses are the same color.
    
    The error here stems from the fact that the inductive step does not work when showing that *P*(2) is true. The last statement in the proof is false.
    

## 8.8 Strong Induction

Sometimes, regular induction is hard to make work because we cannot build the argument based on one smaller value of *n*. In such cases, we need a stronger hypothesis—that the induction hypothesis is true for all smaller values of *n*. In such situations, we use a technique known as strong induction. The proof of the recursive Fibonacci program in [Algorithm 8.2](#chapter8.xhtml#algo8_2) below is a great example of this.

Recall that the Fibonacci numbers start 1, 1, 2, 3, 5, … and each subsequent one is the sum of the previous two. It is not obvious how to write a proof of correctness for the above algorithm by regular induction because computing the (*n* + 1) th Fibonacci number correctly relies on having correctly computed the *n*th and (*n* − 1) th Fibonacci numbers.

We'll next see an example of strong induction that gets around this. Specifically, in strong induction we assume the hypothesis is true for all values up to *n* and then prove it for the case of (*n* + 1). The other changes we make include showing multiple base cases and modifying the concluding step.

A question you might have about strong induction is how many base cases you need to show. This depends on the largest value of *n* that cannot be proved using the inductive argument. In this example, we cannot argue that the two smallest Fibonacci numbers were computed from any smaller numbers, so we had to include base cases for both. More generally, if your inductive step relies on the problem being a certain size, then you need to show the hypothesis for all smaller sizes in the base step.

One might infer from the name that strong induction is stronger than regular induction—you can prove more with it. This turns out not to be the case as they are equivalent in proving power. Any strong induction proof can be converted into a regular induction proof by modifying the proposition so that it holds for all values up to *n*. However, this makes the proof more complicated to read, so we just use strong induction instead. The term “strong” simply indicates that we are making a stronger assumption than in regular induction.

## 8.9 An Analogy for Understanding Strong Induction

Proofs by strong induction rely on the induction hypothesis being true for all smaller values of *n*. Continuing our tower analogy from earlier, this means that each level of the tower (except the bottom most ones) relies on direct support from levels one or more down from it.

In an induction proof, we have to show the following two facts:

1.  The bottom levels that are connected to the ground are firmly established. \[Show *P*(*n*) is true for all *n* that don't rely on *P*(1), *P*(2), …, *P*(*n* − 1).\]
    
2.  If all levels 1, 2, 3, …, *k* are firmly established, then the level *k* + 1 will also be firmly established. \[Show that if *P*(1), *P*(2), *P*(3), …, *P*(*k*) are all true then *P*(*k* + 1) is true.\]
    

Sometimes we only need only some of *P*(1), *P*(2), *P*(3), …, *P*(*k*) to be true to prove that *P*(*k* + 1) is true. For example, in the Fibonacci proof, we only need the hypothesis to be true for the previous two values. The tower analogy for strong induction for the first few levels of the Fibonacci function is illustrated in [Figure 8.2](#chapter8.xhtml#fig8_2).

![Figure 8.2 The tower analogy for strong induction for the Fibonacci example](images/fig8_2.jpg)

[Figure 8.2](#chapter8.xhtml#b8fig8_2) The tower analogy for strong induction for the Fibonacci example

## 8.10 Proofs with Regular Expressions

We can use strong induction to prove the correctness of some of the procedures we designed for regular expressions in previous chapters. For example, in [Chapter 6](#chapter6.xhtml) we showed that any regular expression has a *λ*\-NFA. We can prove this rigorously using strong induction.

Recall in [Section 6.2](#chapter6.xhtml#sec6_2) we saw a procedure for converting any regular expression into a *λ*\-NFA. This involved designing *λ*\-NFAs for the empty set, the set containing just the empty string, and for the set containing a one character string that will make up the base case of the following proof. In addition, there were procedures for designing *λ*\-NFAs for the union and concatenation of any pair of expressions and the Kleene star of any expression; these are used in the inductive step of the following proof.

In our next example we will prove that the procedure for reversing a regular expression in [Chapter 7](#chapter7.xhtml) does indeed give the reverse of the original language.

## 8.11 Correctness of Binary Search

Another great application of strong induction is to more deeply understand the recursive binary search algorithm, shown in [Algorithm 8.3](#chapter8.xhtml#algo8_3). This algorithm assumes that the input list *L* is already sorted and gives an efficient way to search for the index of a target element by bisecting the region to be searched in half at every step. The recursive version of this algorithm also includes the left and right ends of the range of the indexes to be searched. When searching a list *L* indexed from 0 to *n* − 1 for a target, the recursive function is called with parameters BinarySearch(*L*, *t**a**r**g**e**t*, 0, *n* − 1). The base cases of the recursion are when there are no more items to search (when the left index crosses the right index), in which case we return  − 1 to indicate that the search failed, and when the target is found at the middle of the active range of indices, in which case we return that middle index. Otherwise, the recursive procedure narrows the range to the appropriate half and continues the search.

It can be notoriously hard to get the details of the indexes correct, which is why proving the correctness of the algorithm is so very important. For example, it is easy to mess up the indexes and end up in an infinite loop. We will show how to prove the correctness of this algorithm.

Unlike the earlier examples, it is not immediately clear here what should be the induction variable *n*. The size of the binary search problem isn't denoted by a single variable. If we think about how the problem is shrinking at each recursive call, we can see that the *range* of indices gets smaller each time. Therefore, we choose our induction variable to be the size of the range of indexes *n* = *r**i**g**h**t* − *l**e**f**t* + 1. For example, if the range is *l**e**f**t* = 0 and *r**i**g**h**t* = 4, then there are 5 indices in the range.

The base case is when the list cannot be split any further, i.e., when *n* = 0.

The wrapup step is similar to other strong induction proofs.

Finally, we should connect the induction hypothesis we just proved with our original goal: to show correctness of the BinarySearch function.

## 8.12 Chapter Summary and Key Concepts

*   **Induction** is a proof technique that allows us to prove many results in computer science, including showing that **recursive** algorithms are correct.
    
*   An induction proof should be written with four parts:
    
    *   – A **hypothesis** *P*(*n*) that states what you will prove.
        
    *   – A **base step** that shows *P*(*n*) is true for small value(s) of *n*.
        
    *   – An **inductive step** that assumes *P*(*k*) is true and shows that *P*(*k* + 1) is true.
        
    *   – A **conclusion step** that reminds you and the reader why the hypothesis *P*(*n*) is true for all values of *n*.
        
*   For any *a*, *b* ∈ ℤ, *a* ≤ *b* and function *f*, the notation $\\sum\\limits\_{i = a}^{b}f(i)$ is a shortened way of expressing the sum *f*(*a*) + *f*(*a* + 1) + *f*(*a* + 2) + … + *f*(*b*).
    
*   Induction is used for **analyzing run-time of algorithms** and for **counting the number of strings of a given length**.
    
*   **Strong induction** makes a stronger assumption that the induction hypothesis is true for all values up to *k* before showing it to be true for *k* + 1.
    
*   Strong induction is used to show correctness of recursive problems in which the recursion operates on instances more than one smaller.
    

## EXERCISES

Prove the following using induction:

*   8.1 Show that $\\sum\\limits\_{i = 1}^{n}(3i - 2) = \\frac{n(3n - 1)}{2}$ for all *n* ≥ 1.
    
*   8.2 Show that $\\sum\\limits\_{i = 1}^{n}i^{2} = \\frac{n(n + 1)(2n + 1)}{6}$ for all *n* ≥ 1.
    
*   8.3 Show that $\\sum\\limits\_{i = 1}^{n}i(i + 2) = \\frac{n(n + 1)(2n + 7)}{6}$ for all *n* ≥ 1.
    
*   8.4 Show that $\\sum\\limits\_{i = 1}^{n}i^{3} = \\left( \\frac{n(n + 1)}{2} \\right)^{2}$ for all *n* ≥ 1.
    
*   8.5 Show that $\\sum\\limits\_{i = 1}^{n}\\frac{1}{i(i + 1)} = \\frac{n}{n + 1}$ for all *n* ≥ 1.
    
*   8.6 Show that $3^{0} + 3^{1} + 3^{2} + \\ldots + 3^{n} = \\frac{3^{n + 1} - 1}{2}$.
    
*   8.7 Show that for any *a*, *r* ∈ ℝ, *r* ≠ 1, $a + ar + ar^{2} + \\ldots + ar^{n} = \\frac{a(r^{n + 1} - 1)}{r - 1}$.
    
*   8.8 Show that the sum of the first *n* odd natural numbers is equal to *n*² for all *n* ≥ 0.
    
*   8.9 Write a recursive function to sum the first *n* positive integers and show that it is correct.
    
*   8.10 Write a recursive function to compute *a*^(*n*) for two positive integer parameters *a, n* and show that it is correct.
    
*   8.11 Write a recursive function to sum a list and show that it is correct.
    
*   8.12 Write a recursive function to find the minimum of a list and show that it is correct.
    
*   8.13 Write a recursive function to determine if a string is a palindrome and show that it is correct.
    
*   8.14 Write a recursive function to reverse a string and show that it is correct.
    
*   8.15 Write a recursive function to count the number of times a target item appears in a list and show that it is correct.
    
*   8.16 Write a recursive function that given a set as a list of unique elements returns the power set of the set (i.e., a list of lists) and show that it is correct. You may assume that all the elements in the list are unique.
    
*   8.17 Say that we have 3^(*n*) identically looking coins all of which weigh the same except one which is lighter than the others. Design a recursive procedure to find the lighter coin within *n* weighings on a balance scale. Prove this procedure correct using induction.
    
*   8.18 Show that 2^(*n*) > *n* for all *n* ≥ 1.
    
*   8.19 Show that 2^(*n*) ≥ *n*² for all *n* ≥ 4.
    
*   8.20 Find a value *n*[0] such that 2^(*n*) ≥ *n*³ for all *n* ≥ *n*[0] and then prove the result.
    
*   8.21 Show using induction that $\\overset{―}{S\_{1} \\cup S\_{2} \\cup \\ldots \\cup S\_{n}} = \\overset{―}{S\_{1}} \\cap \\overset{―}{S\_{2}} \\cap \\ldots \\cap \\overset{―}{S\_{n}}$ for all *n* ≥ 1 and all sets *S*[1], …, *S*[*n*]. (Hint: Use De Morgan's laws in both the base step and the induction step.)
    
*   8.22 Show using induction that $\\overset{―}{S\_{1} \\cap S\_{2} \\cap \\ldots \\cap S\_{n}} = \\overset{―}{S\_{1}} \\cup \\overset{―}{S\_{2}} \\cup \\ldots \\cup \\overset{―}{S\_{n}}$ for all *n* ≥ 1 and all sets *S*[1], …, *S*[*n*]. (Hint: Use De Morgan's laws in both the base step and the induction step.)
    
*   8.23 Prove that the size of the power set of a set *S* of size *n* is 2^(*n*).
    
*   8.24 Show that it is possible to use postage stamps of values 2 and 3 to make any amount of postage *n* ≥ 3.
    
*   8.25 Design your own analogy for induction similar to [Section 8.3](#chapter8.xhtml#sec8_3). Be sure to clearly state what are the hypothesis, base case, and inductive step in your analogy.
    

Prove the following using strong induction:

*   8.26 Let *F*[*i*] be the *i*th Fibonacci number for each *i* ≥ 1. Show that $\\sum\\limits\_{i = 1}^{n}F\_{i} = F\_{n + 2} - 1$.
    
*   8.27 Prove that the *n*th Fibonacci number *F*[*n*] is equal to
    
      
    $$\\begin{array}{l} {\\frac{\\sqrt{5}}{5}\\left( \\left( \\frac{1 + \\sqrt{5}}{2} \\right)^{n} - \\left( \\frac{1 - \\sqrt{5}}{2} \\right)^{n} \\right).} \\\\ \\end{array}$$  
    
*   8.28 Prove that for any *n* ≥ 1 it is possible to tile a 2^(*n*) × 2^(*n*) grid with L-shaped tiles (i.e., a 2 × 2 tile with one of the four corners missing) with just one corner square missing.
    
*   8.29 Show that it is possible to use postage stamps of values 3 and 5 to make any amount of postage *n* ≥ 8.
    
*   8.30 Design your own analogy for strong induction. Be sure to clearly state what are the hypothesis, base case, and inductive step in your analogy
    

# Chapter 9Proving the Language of a DFA

DOI: [10.1201/9781003383284-9](https://doi.org/10.1201/9781003383284-9)

## 9.1 Why You Should Care

Now that you know how to create DFAs, you should next verify that the DFA you created does accept the language you think it does. This is analogous to showing that the algorithm you designed gives the correct answer on all possible inputs, something that every computer scientist should be doing.

## 9.2 A Simple Example

We will start with the simple DFA below ([Figure 9.1](#chapter9.xhtml#fig9_1)):

![Figure 9.1 DFA for odd length strings over \\{ 0,1\\} ](images/fig9_1.jpg)

[Figure 9.1](#chapter9.xhtml#b9fig9_1) DFA for odd length strings over {0, 1} 

It should be apparent that this DFA accepts strings of odd length. Why is this the case? Well, intuitively, the reason is that we flip-flop between the states *q*[0] and *q*[1] on any character, so that all even length strings end at *q*[0] and odd length strings end at *q*[1]. We will formalize this idea next.

We first need to generalize the *δ* function to operate on strings rather than symbols. This will allow us say which state a string will end up at.

More formally, we recursively define *δ̂*(*q*[*i*], *s*) as follows:

  
$$\\begin{array}{l} {\\hat{\\delta}(q\_{i},s) = \\left\\{ \\begin{matrix} {q\_{i},\\qquad\\qquad\\qquad\\text{~if~}s = \\lambda} \\\\ {\\delta(\\hat{\\delta}(q\_{i},p),c),\\qquad\\text{if~}s = pc,\\ \\text{where~}p \\in \\Sigma^{\\ast}\\ \\text{and~}c \\in \\Sigma.} \\\\ \\end{matrix} \\right.} \\\\ \\end{array}$$  

Using this new notation, we can see that for the above DFA we have the following two criteria for the pair of states. For any string *s* ∈ *Σ*^(\*),

1.  *δ̂*(*q*[0], *s*) = *q*[0] if and only if |*s*| is even.
    
2.  *δ̂*(*q*[0], *s*) = *q*[1] if and only if |*s*| is odd.
    

Note that we always start from *q*[0] because this is the start state. It should be fairly clear why proving the above pair of statements is sufficient to prove the language of the DFA. Since the only accepting state is *q*[1], the set of strings that reach *q*[1]—the odd length strings—is the set that the DFA accepts.

To prove this result, we need a more involved hypothesis, sometimes referred to as a **mutual induction** hypothesis. Notice that this hypothesis is over the length of the string *n* and thus must be shown true for every string of length *n*. It also has multiple parts, one per state of the DFA.

The base case of this induction hypothesis is more involved than usual because we have to prove if and only if results for both statements.

The proofs for the second part of the hypothesis are very similar and you can closely follow much of the language. Pay close attention to what has changed from the proof of the first part and be sure to understand why the changes are needed.

The induction wrapup is the same as the previous proofs by induction that you have seen before. However, there is an additional step where you should tell your reader why the hypothesis proves that the DFA does indeed accept the desired language. Specifically, you should tell the reader the language of the DFA, which is all the strings that can reach an accepting state.

## 9.3 A More Involved Example

The above example was simple in that the DFA had the same transition for both symbols of the alphabet from both states. Let us look at a slightly more complex example in which this is not the case.

Take a look at the DFA in [Figure 9.2](#chapter9.xhtml#fig9_2) and think about what language it accepts.

![Figure 9.2 DFA for all strings over \\{ 0,1\\} that end in 01](images/fig9_2.jpg)

[Figure 9.2](#chapter9.xhtml#b9fig9_2) DFA for all strings over {0, 1} that end in 01

After giving it some thought, hopefully you came to the conclusion that this DFA accepts precisely the set of strings over *Σ* = {0, 1} that end in 01. Intuitively, the strings that reach state *q*[1] must be precisely the ones that end in 0 and thus the strings that reach state *q*[2] must be precisely the ones that end in 01. By the process of elimination, this means that the strings that reach state *q*[0] are the ones that neither end in 0 nor 01. We use this to once again prove the result as above.

We wrap the proof up similar to before.

## 9.4 An Example with Sink States

Here is another example with sink states.

Before reading on, try to determine the set of strings that can reach the states *q*[0], *q*[1], *q*[2], and *q*[3] in [Figure 9.3](#chapter9.xhtml#fig9_3). Some examples of strings in each set are given below to help you get started.

![Figure 9.3 DFA for all strings over \\{ 0,1\\} that start with 0 and contain a 1](images/fig9_3.jpg)

[Figure 9.3](#chapter9.xhtml#b9fig9_3) DFA for all strings over {0, 1} that start with 0 and contain a 1

Here are the sets for each state:

*   The start state *q*[0] has no transitions entering it, so the only string that ends at *q*[0] is *λ*. Thus, the set in this case is {*λ*}.
    
*   The state *q*[1] is a sink state for strings that start with a 1. The set is then {1*s* : *s* ∈ {0, 1}^(\*)}.
    
*   The state *q*[2] can only be reached by strings that have one or more 0s and no 1s. The set is thus {0^(*n*) : *n* ≥ 1}.
    
*   Lastly, the state *q*[3] has all the remaining strings, namely the ones that start with a 0 and contain a 1. This set is {0*s*1*t* : *s*, *t* ∈ {0, 1}^(\*)}.
    

Finally, we wrap up the induction step and explain to the reader how the induction hypothesis tells us the language of the DFA.

## 9.5 Chapter Summary and Key Concepts

*   We can prove that a DFA accepts a given language using **mutual induction.**
    
*   The function *δ̂* extends the *δ* function of a DFA to apply to strings.
    
*   The mutual induction **hypothesis** defines precisely what set of strings ends at each state.
    
*   The mutual induction **base case** verifies the hypothesis for the empty string.
    
*   The mutual induction **inductive step** proves that strings of length *n* + 1 end at the correct state assuming that the strings of length *n* do so.
    
*   The mutual induction **conclusion** both concludes the induction proof and demonstrates the language of the DFA by examining the set of strings that reach the accepting state(s).
    

## Exercises

Draw DFAs with as few states as possible for each of the following languages and then prove that they accept that language.

*   9.1 {*w* ∈ {0, 1}^(\*) : *w* starts with a 0}
    
*   9.2 {*w* ∈ {0, 1}^(\*) : *w* ends with a 1}
    
*   9.3 {*w* ∈ {0, 1}^(\*) : *w* has 01 as a substring}
    
*   9.4 {*w* ∈ {0, 1}^(\*) : *w* does not have 01 as a substring}
    
*   9.5 {*w* ∈ {0, 1}^(\*) : *w* has an even number of 0s}
    
*   9.6 {*w* ∈ {0, 1}^(\*) : *w* has an even number of 0s and an odd number of 1s}
    
*   9.7 {*w* ∈ {0, 1}^(\*) : *w* has an even number of 0s and an even number of 1s}
    
*   9.8 {*w* ∈ {0, 1}^(\*) : *w* has an odd number of 0s and an even number of 1s}
    
*   9.9 {*w* ∈ {0, 1}^(\*) : *w* has an odd number of 0s and an odd number of 1s}
    
*   9.10 {*w* ∈ {0, 1}^(\*) : *w* starts with 00}
    
*   9.11 {*w* ∈ {0, 1}^(\*) : *w* starts and ends with a 0}
    
*   9.12 {*w* ∈ {0, 1}^(\*) : *w* has exactly one 0}
    
*   9.13 {*w* ∈ {0, 1}^(\*): the number of 0s in *w* is divisible by 3}
    
*   9.14 {*w* ∈ {0, 1}^(\*): the second character in *w* is 0}
    
*   9.15 {*w* ∈ {0, 1}^(\*): the second last character in *w* is 0}
    

# Chapter 10Proof by Contradiction

DOI: [10.1201/9781003383284-10](https://doi.org/10.1201/9781003383284-10)

## 10.1 Why You Should Care

Proof by contradiction is a powerful technique that is often the best way to prove many results in computer science. It can be an easier way to prove some results than, say, direct proof because it allows the prover to assume more facts to be used in the proof.

## 10.2 Overview of the Technique

Proof by contradiction works by assuming the opposite (negation) of what you are trying to prove and then arriving at a contradictory statement (usually that a statement and its negation are both true). In other words, the structure of proving some statement *S* looks like the following:

1.  Assume for a contradiction that the negation of *S* is true.
    
2.  Make arguments based on this assumption.
    
3.  Show that you arrive at a contradiction.
    

This technique gives you a starting point for your proof—assuming the negation of the statement you are trying to prove. The tricky part with it is figuring out how to get to the final contradiction.

## 10.3 Why You Can't Write $\\sqrt{2}$ as an Integer Fraction

The technique of proof by contradiction dates back at least to the ancient Greek who used it to show that $\\sqrt{2}$ is irrational.

The Pythagoreans used proof by contradiction to show that $\\sqrt{2}$ is irrational. An interesting side effect of this is that it is impossible to precisely store the value of $\\sqrt{2}$ as a float, double, or even using a rational number class since we would need infinite precision to capture all the digits in the number. We see why next.

In the above proof we use the fact that the square of an odd number is always an odd number. This follows from the fundamental theorem of arithmetic.

We can use this theorem to see that since an odd number has no factor of 2 in its prime factorization, then neither will its square.

## 10.4 Will we Run out of Prime Numbers?

A number of algorithms, such as several for encrypting data, rely on the existence of large prime numbers. It would be problematic if there were only a finite number of prime numbers. This next proof shows that this is not the case.

## 10.5 The Mindbending Number of Languages

The next result we will see is that the number of possible languages is so large that we cannot even list them all.

This proof is an adaptation of Cantor's diagonalization technique that showed that the real numbers cannot be listed either, which means that there are different sizes of infinity. This technique will be important for us in [Chapter 14](#chapter14.xhtml) when we show that there are languages that cannot be accepted by any computer.

## 10.6 Chapter Summary and Key Concepts

*   The **proof by contradiction** technique is used to show a statement is true by starting with the negation of the statement and ending in an impossible situation (contradiction).
    
*   The square root of two cannot be written as a fraction of integers.
    
*   There are infinitely many prime numbers.
    
*   The number of possible languages is so large that we cannot even make an infinite list of them.
    

## Exercises

*   10.1 Prove that $\\sqrt{3}$ is irrational.
    
*   10.2 Explain why the proof used to show that $\\sqrt{2}$ is irrational cannot be adapted to show that $\\sqrt{4}$ is irrational.
    
*   10.3 Prove that for any prime number *p*, $\\sqrt{p}$ is irrational.
    
*   10.4 Prove that the cube root of two ($\\sqrt\[3\]{2}$) is irrational.
    
*   10.5 Prove that if *a, b* are integers, then *a*² − 4*b* ≠ 2.
    
*   10.6 Prove that if *a, b, c* are integers and *a*² + *b*² = *c*², then *a* or *b* is even.
    
*   10.7 Prove that log[2]3 is irrational.
    
*   10.8 Prove that log[10]8 is irrational.
    
*   10.9 Prove that any number *x* ≠ 0 is irrational if and only if 1/*x* is irrational.
    
*   10.10 Prove that the sum of a rational number and an irrational number is an irrational number.
    
*   10.11 Prove that there is an irrational number *x* such that $x^{\\sqrt{2}}$ is rational.
    
*   10.12 Define a majority item in a list to be an item that makes up **more** than half the list. Prove that there can be at most one majority item in the list.
    
*   10.13 Define a majority item in a list to be an item that makes up **more** than half the list. Let *L* be an even length list with a majority item. Prove that any way that *L* is split into two equal halves, one of the halves must have the same majority item as a majority item of the entire list.
    
*   10.14 Prove that the average of two numbers is at least as large as at least one of the two numbers.
    
*   10.15 Prove that the average of *n* numbers is at most as large as at least one of the numbers.
    
*   10.16 Prove that all positive integers can be written as a sum of unique, integer powers of 2. (Hint: You will need strong induction and contradiction for this proof.)
    

# Chapter 11Pumping Lemma for Regular Languages

DOI: [10.1201/9781003383284-11](https://doi.org/10.1201/9781003383284-11)

## 11.1 Why You Should Care

Now that you have learned about proof by contradiction, you will see how to apply it to show that certain languages are not regular—no matter how hard you try, you cannot create a DFA for them. This is our first taste of what is not computable with (a specific model of) computers. It also means that there are fairly simple problems for which we cannot design a DFA and thus DFAs are not the model of computation that we want to use to represent all computers.

## 11.2 The Pigeonhole Principle

Before we can see the proof technique for showing a language is not regular, we need to understand a mathematical idea called the pigeonhole principle. This idea sounds obvious but turns out to be a very powerful tool for showing surprising results.

Here are some interesting examples:

We can use the pigeonhole principle to show that a language is not regular as follows.

This proof very neatly shows why the language is not regular. However, it is not easy to generalize to other languages that are not regular. A more general method is to use the pumping lemma.

At a high level, the pumping lemma says that for any regular language, if we take any sufficiently long string in the language, we can break it into three parts (with some conditions on the lengths of these three parts) in such a way that the string can be pumped—repeating the middle of the three parts any number of times (including zero) must always give us back a string in the language. This pumping condition is what gives the lemma its name.

If we can show that the pumping lemma does not apply to a language *L*, then this means (by contradiction) that *L* is not regular. Before we see an example of this, we will prove the pumping lemma.

A question you may have is what happens if a language does not have arbitrarily long strings. For example, a simple language like {*a**a*, *a**b*} should be regular (it has a regular expression *a**a* + *a**b*) but does not have strings larger than *n* for any *n* > 2. This is an example of a vacuously true statement. For this language, we can pick *n* = 3 and note that since there are no strings longer than length 2 for this language, the pumping lemma conditions apply for all these strings (all zero of them!).

## 11.3 Applying the Pumping Lemma

The general form of the proof to show that a language is not regular is to assume for a contradiction that it is regular and then show that the pumping lemma does not apply to it for a contradiction. To show why the pumping lemma doesn't apply, we have to show its negation.

The pumping lemma takes the following form for a regular language *L*:

  
$$\\begin{array}{ll} & {(\\exists n > 0)} \\\\ & {(\\text{~strings~}w\\ \\text{in~}L\\ \\text{of\\ length\\ at\\ least~}n)} \\\\ & {(\\exists\\text{~a\\ way\\ to\\ break\\ up\\ the\\ string\\ into~}w = xyz\\text{~with~}|y| > 0\\ \\text{and~}|xy| \\leq n)} \\\\ & {(k \\geq 0)(xy^{k}z \\in L).} \\\\ \\end{array}$$  

To show the negation, we need to negate the above statement. We can do so using the quantifier negation that you learned about in [Chapter 3](#chapter3.xhtml). This gives the following:

  
$$\\begin{array}{ll} & {(n > 0)} \\\\ & {(\\exists\\text{~a\\ string~}w\\ \\text{in~}L\\ \\text{of\\ length\\ at\\ least~}n)} \\\\ & {(\\text{~ways\\ to\\ break\\ up\\ the\\ string\\ into~}w = xyz\\text{~with~}|y| > 0\\ \\text{and~}|xy| \\leq n)} \\\\ & {(\\exists k \\geq 0)(xy^{k}z \\notin L).} \\\\ \\end{array}$$  

We are now ready to see how we can use the pumping lemma to show that the same language from earlier is not regular.

When using the pumping lemma, there are three places in which you have to use your insight into how these proofs work to get a correct argument. These are (i) correctly selecting an appropriate *w*, (ii) correctly splitting *w* into *x, y*, and *z* in all possible ways, and (iii) correctly selecting an appropriate *k* for each case. The next few examples will give some insights into how to solve each of these problems.

## 11.4 Selecting the String from the Language

This example will help us see a way to choose the string in the language.

Notice that for this language we had any number of strings that we could have chosen. The string we chose was done so deliberately so as to make the cases for how to split *w* into *xyz* as simple as possible since *x* and *y* had to consist entirely of *a*s. This may not always be the case as we'll see in the next example.

## 11.5 Splitting the Chosen String

Next, we'll look at an example where there are many possible ways to split the string.

For this problem, the choice of string *w* is easy since we can just select one of the given form (here, 01^(*n*)01^(*n*)). Pause here to try to figure out what are the different ways to split the string into *x, y, z* such that |*y*| > 0 and |*x**y*| ≤ *n* before reading on.

Hopefully, you found the edge case where *x* = *λ*. For this case, *y* must start with a 0 and have some number of 1's. Note that it is not possible for *y* to have a second 0 since that would mean that |*x**y*| > *n*. The second case is that *x* has the first 0. We could further break this into the cases where *x* is just 0 and *x* is a 0 followed by some 1s, but this is more cases than we would need. If we let *x* = 01^(*i*) where *i* ≥ 0, then we cover both these sub-cases together. We can now write the proof.

Notice that it is fine to pick different values of *k* in the different sub-cases.

## 11.6 Choosing the Number of Times to Pump

The next example we will look at has us be careful about the *k* that we select.

Notice in this example that we had to be very particular about the *k* that we chose. Here, only *k* = 0 would work as any larger *k* would pump the string into a string in *L*.

## 11.7 A More Complex Example

This final example shows how we have to be careful to select a string in the language and be creative in how we pump the string.

In the pumping lemma proof for this language, when we select a string from the language, it is tempting to pick a string such as 0^(*n*). However, note that we know nothing about *n* and in particular we don't know if it is a perfect square. To make the conditions of our selection of *w* work, we need a string of length a perfect square, so we ensure this by picking *w* = 0^(*n*²).

To make this proof work, we had to come up with a way of showing that the pumped string did not have a length that was a perfect square. To do this, we had to make use of all the conditions (|*y*| > 0 and |*x**y*| ≤ *n*) to show that the pumped string fell between two perfect squares.

## 11.8 Chapter Summary and Key Concepts

*   The **pigeonhole principle** states that if more than *n* objects are assigned to *n* containers, then some container must have more than one of the objects.
    
*   The **pumping lemma** demonstrates a property that must be true for all regular languages.
    
*   We can show that a language is not regular by assuming for a contradiction that it is regular and proving that the pumping lemma does not apply to it.
    

## EXERCISES

Prove that the following languages are not regular:

*   11.1 {0^(*n*)1^(2*n*) : *n* ≥ 0}
    
*   11.2 {0^(*n*)1^(*m*) : *n* < *m*}
    
*   11.3 {0^(*n*)1^(*m*) : *n* ≤ *m*}
    
*   11.4 {0^(*n*)1^(*m*) : *n* ≥ *m*}
    
*   11.5 {0^(*n*)1^(*m*)0^(*n*)1^(*m*) : *n*, *m* ≥ 0}
    
*   11.6 {0^(*n*)1^(*m*)0^(*m*)1^(*n*) : *n*, *m* ≥ 0}
    
*   11.7 {0^(*n*)1^(*m*)0^(*n* + *m*) : *n*, *m* ≥ 0}
    
*   11.8 {0^(*n*)1^(*m*)0^(*n**m*) : *n*, *m* ≥ 0}
    
*   11.9 {0^(*n*)1^(*m*)0^(*l*) : *n*, *m*, *l* ≥ 0, *l* ≤ *n* + *m*}
    
*   11.10 {0^(*n*)1^(*m*)0^(*l*) : *n*, *m*, *l* ≥ 0, *l* ≥ *n* + *m*}
    
*   11.11 The set of strings of matched parentheses over {(,)} (e.g., (()) and ()((())) are in the language, but ()) is not)
    
*   11.12 {*w**w* : *w* ∈ {0, 1}^(\*)}
    
*   11.13 {*w**w*^(*R*) : *w* ∈ {0, 1}^(\*)} (Note: *w*^(*R*) is the reverse of the string *w*.)
    
*   11.14 {(01)^(*n*)(10)^(*n*) : *n* ≥ 0}
    
*   11.15 {*w* ∈ {0, 1}^(\*) : *w* is a palindrome} (Note: A string is a palindrome if it is the same read forwards as backwards, e.g., 0, 101, 1001, 111010111.)
    
*   11.16 {0^(*n*) : *n* is a perfect cube}
    
*   11.17 {0^(*n*) : *n* is a perfect fourth power}
    
*   11.18 {0^(*n*) : *n* is a power of 2}
    
*   11.19 (Harder) {0^(*n*) : *n* is a prime number}
    
*   11.20 (Harder) {*w* ∈ {0, 1}^(\*) : *w* is not a palindrome}
    

# Chapter 12Context-Free Grammars

DOI: [10.1201/9781003383284-12](https://doi.org/10.1201/9781003383284-12)

## 12.1 Why You Should Care

Now that we have established that DFAs are not powerful enough to capture all computation, we will look at a different way to model languages called Context-Free Grammars (CFGs). These grammars lay the foundation for all natural languages, such as English, Hindi, Spanish, and Vietnamese and programming languages, such as C++, Java, and Python.

## 12.2 An Example Context-Free Grammar

We'll start with an example of a context-free grammar (CFG) for the non-regular language *L* = {0^(*n*)1^(*n*) : *n* ≥ 0}.

In the above example *S* is called a variable or non-terminal. In particular, *S* is what is called the initial variable. Each production of the grammar has a variable on the left and an expression on the right that is any combination of variables, symbols from the alphabet Σ (called terminals), and *λ*. Starting from the initial variable, we can produce strings by applying productions until we have only terminals left. For example, consider how we would produce strings using the above grammar:

It should be clear that we can similarly apply the *S* → 0*S*1 production *n* times (for any *n* ≥ 0), followed by the *S* → *λ* production to get any string in *L* = {0^(*n*)1^(*n*) : *n* ≥ 0}. Even the empty string can be derived (as it should, since 0⁰1⁰ = *λ*) by right away applying the *S* → *λ* rule. Moreover, because of the limited productions, we cannot produce any strings not in *L*. Thus, the example grammar does indeed generate precisely the strings in *L*.

## 12.3 Palindromes

We will next see an example of a CFG for the language *P* = {*w* ∈ {0, 1}^(\*) : *w* is a palindrome}. Recall that a palindrome is a string that reads the same forwards and backwards, such as the word *racecar*. We will show how to make a grammar for this language over the binary alphabet *Σ* = {0, 1}.

You should verify that any palindrome over {0, 1} can be generated by this grammar and that this grammar only generates palindromes. A few example derivations are given next:

## 12.4 Context-Free Grammars for Regular Languages

You will show in an exercise that any regular language has a context-free grammar. Some examples of this are given next:

Here are how some strings are generated from this grammar:

## 12.5 Formal Definition of CFGS

Now that we have seen a few different grammars, we can formally define them.

The language of a CFG *G* = (*V*, *Σ*, *P*, *S*) is defined as the set of strings that can be produced from *S* using productions in *P* until there are only terminals left. Any language that has a context-free grammar is called *context-free*.

## 12.6 Closure under Union

We can construct a CFG for the union of two context-free languages such as

  
$$\\begin{array}{l} {U = \\{ 0^{n}:n \\geq 1\\} \\cup \\{ w01:w \\in \\{ 0,1\\}^{\\ast}\\}} \\\\ \\end{array}$$  

from the CFGs for the two individual languages.

We can generalize the above example to give a procedure to find a CFG for the union of any two context-free languages.

You can show closure under concatenation and Kleene star in a similar manner. These are left as exercises.

## 12.7 Applications of CFGS

Grammars can be developed for a variety of languages, both computing languages and natural languages that are used by people.

In a similar way, we can write grammars for languages used by people. Computer scientists call these natural languages.

While CFGs have many useful applications in computer science, they cannot capture all computable languages. For example, it is possible to use a pumping lemma for context-free languages to show that there can be no context-free grammar for {0^(*n*)1^(*n*)2^(*n*) : *n* ≥ 1}. Thus, we will need a more powerful model, such as the Turing machine that you will learn about in the next chapter.

## 12.8 Chapter Summary and Key Concepts

*   A **context-free grammar** can be used to generate strings. The set of strings generated by the grammar are called its language.
    
*   Context-free grammars can be found for **all regular languages**.
    
*   The **formal definition** of a context-free grammar is given by *G* = (*V*, *Σ*, *P*, *S*), where *V* is a set of **variables**, Σ is the **alphabet**, *P* is a set of **productions**, and *S* is the **start variable**.
    
*   Any language that has a context-free grammar is called a **context-free language**.
    
*   Context-free languages are **closed under union**.
    
*   Context-free grammars have computer science applications in the subareas of **programming languages** and **natural language processing**.
    

## Exercises

Give grammars for the following languages:

*   12.1 {0^(*n*)1^(2*n*) : *n* ≥ 0}
    
*   12.2 {(01)^(*n*)(10)^(*n*) : *n* ≥ 1}
    
*   12.3 {0^(*n*)1^(*m*) : *n* ≤ *m*}
    
*   12.4 {0^(*n*)1^(*m*) : *n* ≥ *m*}
    
*   12.5 {01^(*n*)01^(*n*) : *n* ≥ 0}
    
*   12.6 {0^(*n*)1^(*n*)0^(*m*)1^(*m*) : *n*, *m* ≥ 0}
    
*   12.7 {0^(*n*)1^(*m*)0^(*m*)1^(*n*) : *n*, *m* ≥ 0}
    
*   12.8 {0^(*n*)1^(*m*)0^(*n* + *m*) : *n* ≥ 0}
    
*   12.9 {0^(*n*)1^(*m*)0^(2*n* + *m*) : *n* ≥ 0}
    
*   12.10 {0^(*n*)1^(*m*)0^(*l*) : *l* < *n* + *m*}
    
*   12.11 {0^(*n*)1^(*m*)0^(*l*) : *l* > *n* + *m*}
    
*   12.12 {0^(*n*)1^(*m*)0^(*l*) : *l* ≠ *n* + *m*}
    
*   12.13 {1^(*m*) :  is a multiple of 3 or 5}
    
*   12.14 (0 + 1)^(\*)010(0 + 1)^(\*)
    
*   12.15 The set of strings of matched parentheses over {(,)} (e.g., (()) and ()((())) are in the language, but ()) is not)
    
*   12.16 The set of strings of matched parentheses over {(,), \[,\], {,}} (e.g., (\[\]) and (){\[()\]} are in the language, but (\]) is not)
    
*   12.17 Show that it was important to make sure that the variables of the two grammars were unique in the proof of [Theorem 12.1](#chapter12.xhtml#theo12_1) by giving an example in which they are not unique and the construction does not give the union of the two languages.
    
*   12.18 Use the construction in the proof of [Theorem 12.1](#chapter12.xhtml#theo12_1) to give a grammar for
    
      
    $$\\begin{array}{l} {\\{ 0^{n}1^{n}:n \\geq 0\\} \\cup \\{ w:w\\text{~is\\ a\\ palindrome\\ over~}\\{ 0,1\\}\\}.} \\\\ \\end{array}$$  
    
*   12.19 Show that the context-free languages are closed under concatenation. That is, show that if *L*[1] and *L*[2] are context-free languages, then
    
      
    $$\\begin{array}{l} {L = \\{ s\_{1}s\_{2}:s\_{1} \\in L\_{1} \\land s\_{2} \\in L\_{2}\\}} \\\\ \\end{array}$$  
    
    is a context-free language.
    
*   12.20 Show that the context-free languages are closed under Kleene star. That is, show that if *L* is a context-free languages, then
    
      
    $$\\begin{array}{l} {L^{\\prime} = \\{ s\_{1}s\_{2}s\_{3}\\ldots s\_{n}:n \\geq 0 \\land s\_{1},\\ldots,s\_{n} \\in L\\}} \\\\ \\end{array}$$  
    
    is a context-free language.
    
*   12.21 Prove using strong induction that every regular language has a grammar. (Hint: You can use the closure under union proof from this chapter for part of this proof.)
    

# Chapter 13Turing Machines

DOI: [10.1201/9781003383284-13](https://doi.org/10.1201/9781003383284-13)

## 13.1 Why You Should Care

The Turing machine is the standard model for all computation. It is capable of accepting all regular languages, context-free languages, and indeed any language computation that is believed to be possible by a computer. All programming languages are called Turing-complete, which is an informal way of saying that they can do all that a Turing machine can do. Thus understanding how Turing machines work is important for any computer scientist.

## 13.2 An Example Turing Machine

What makes the DFA an unsatisfactory model of computation is that it necessarily has finite memory and thus cannot count arbitrarily high, leading it to be unable to accept simple languages like

  
$$\\begin{array}{l} {L = \\{ 0^{n}1^{n}:n \\geq 0\\}.} \\\\ \\end{array}$$  

To get around this deficiency, the Turing machine adds an infinitely long tape (stretching forever to the left and right) that has data on it in the form of cells, each of which holds a single character and can be modified by a head that moves along the tape one cell at a time. This unbounded memory allows us to model all known computation. The input string now starts on the tape with the head pointed to the leftmost character. All other cells are filled with a special blank symbol (usually B).

![Figure 13.1 A Turing machine with the input 01 on its doubly infinite tape](images/fig13_1.jpg)

Figure 13.1 A Turing machine with the input 01 on its doubly infinite tape

Here are several differences from DFAs that are important to understand:

*   Not all state/symbol combinations need to be defined for a Turing machine. If there is no rule for a given combination during the computation (for example, seeing a 1 on the tape at *q*[0]), then the machine simply halts and rejects.
    
*   The transitions that are defined are still deterministic—we don't allow a state/symbol combination to appear multiple times in this model of the Turing machine. There are non-deterministic models of Turing machines, but we will not study them in this book.
    
*   Unlike DFAs for which we go through the string only once, for a Turing machine we can traverse the string multiple times and go back to characters we have processed previously. In fact, most interesting problems will require us to make several passes over the input or use the blank tape cells in their computation.
    
*   A Turing machine accepts a string simply by reaching an accepting state. As soon as an accepting state is reached, the computation halts and accepts.
    

In particular, the last item means that we do not have to “consume” the entire string to accept/reject it. For example, a Turing machine for *Σ*^(\*) can have a single accepting state (and no others) or a Turing machine for ∅ can be one with a single starting state that is not accepting (and no others).

We will next see some notation for tracing the steps of a Turing machine. The trace will contain all the characters on the tape (other than the blank symbols that go off infinitely to the left and right) with the current state written immediately to the left of the position of the head.

The language of a Turing machine is the set of strings accepted by it. Notice that this first example Turing machine will halt and accept or halt and reject on all strings, but it is possible that a Turing machine can reject by running forever. This detail will be important later.

## 13.3 Formal Definition of a Turing Machine

A Turing machine can be defined using a 7-tuple as follows.

## 13.4 Recognizing Addition

Our second example will demonstrate how Turing machines can recognize addition with unary numbers. Unary, or tally numbering, is a very simple numerical encoding that has a single symbol (usually 1 or 0) and each positive integer is represented by that number of that symbol.

The following language allows us to recognize or check addition in unary by using 0s for the first number, 1s for the second, and 0s for the sum:

  
$$\\begin{array}{l} {L\_{+} = \\{ 0^{n}1^{m}0^{n + m}:n,m \\geq 0\\}.} \\\\ \\end{array}$$  

To design a Turing machine for this language, we can use an algorithm similar to the previous example. We can match 0s at the start of the string with 0s at the end by erasing them. Once this is done we erase matched pairs of 1s from the beginning with 0s on the end until the entire string is erased. If the end result of the computation is a blank tape, then the computation should accept. If the string is not of the given form, the computation should reject.

You should also verify that the Turing machine works correctly when *n* = 0 (for example, by accepting strings such as 10 and 1100 and rejecting strings such as 110 and 100), when *m* = 0 (for example, by accepting strings such as 00 and 0000 and rejecting strings such as 0 and 000), and when both *n* and *m* are zero (i.e., when the input is *λ*).

## 13.5 Conditional Branching with a Turing Machine

We will next see an example of a Turing machine for a more complex language, the set of strings with equal numbers of *a*s and *b*s. This example will illustrate the idea of branching with a Turing machine. The algorithm this time will mark off the leftmost *a* or *b* with a new symbol and then move to the right through the string to find a matching complementary symbol (*b* or *a*, respectively). Once this has been marked off, the Turing machine returns to the start of the string and repeats this procedure again. The computation terminates successfully when all the *a*s and *b*s have been marked off. If this does not happen, then the computation rejects.

## 13.6 Turing Machines Can Accept All Regular Languages

We will show that every regular language has a Turing machine that accepts it by simulating the actions of the DFA with its finite state. We'll start with an example and then generalize this idea to any regular language.

## 13.7 Turing Machines as Computers of Functions

Besides computing languages, Turing machines can also compute functions. Specifically, such a the Turing machine starts with its input on the tape and writes the output of the function before it halts.

The next simple example shows how to add two unary numbers (as defined in [Section 13.4](#chapter13.xhtml#sec13_4)), represented by 0^(*n*) and 1^(*m*). To compute the sum for 0^(*n*)1^(*m*) we need to create the output 1^(*n* + *m*). This is very simple to do by converting all the initial 0s to 1s as in the following example:

## 13.8 Chapter Summary and Key Concepts

*   The **Turing machine** is the standard model for all possible computation. Any computational system that can do all that a Turing machine does is called **Turing-complete**.
    
*   A Turing machine has a **doubly-infinite tape** with a read/write **tape head** that can move along the tape. It also has **finite control** in the form of states with transitions.
    
*   A Turing machine is **formally defined** by a tuple (*Q*, *Σ*, *Γ*, *δ*, *q*[0], *B*, *F*), where *Q* is the set of **states**, Σ is the **input alphabet**, Γ is the **tape alphabet**, *δ* is the **transition function**, *q*[0] is the **start state**, *B* is the **blank symbol**, and *F* is the set of **accepting states**.
    
*   A Turing machine can be used for computational operations such as **recognizing arithmetic operations** and performing **conditional branching**.
    
*   Every regular language has a Turing machine that accepts it.
    
*   Turing machines can also be used to **compute functions** with string inputs and outputs.
    

## Exercises

Create Turing machines for the following languages:

*   13.1 {*w* ∈ {0, 1}^(\*) : *w* has 01 as a contiguous substring}
    
*   13.2 {*w* ∈ {0, 1}^(\*) : *w* ends in 00}
    
*   13.3 {*w* ∈ {0, …, 9}^(\*) : *w* is even in decimal} (*λ* is even)
    
*   13.4 {*w* ∈ {0, 1}^(\*) : *w* has an odd number of 0s and an even number of 1s}
    
*   13.5 {0^(*n*)1^(*m*) : *n* ≤ *m*}
    
*   13.6 {0^(*n*)1^(*m*) : *n* ≥ *m*}
    
*   13.7 {0^(*n*)1^(2*n*) : *n* ≥ 0}
    
*   13.8 {0^(*n*)1^(*n*)2^(*n*) : *n* ≥ 0}
    
*   13.9 {0^(*n*)1^(*n*)0^(*m*)1^(*m*) : *n*, *m* ≥ 0}
    
*   13.10 {0^(*n*)1^(*m*)0^(*m*)1^(*n*) : *n*, *m* ≥ 0}
    
*   13.11 {(01)^(*n*)(10)^(*n*) : *n* ≥ 1}
    
*   13.12 {0^(*n*)1^(*m*)0^(*n* − *m*) : *n* > *m* > 0}
    
*   13.13 {0^(*n*)1^(*m*)0^(2*n* + *m*) : *n* ≥ 0}
    
*   13.14 {0^(*n*)1^(*m*)0^(*n**m*) : *n*, *m* ≥ 1}
    
*   13.15 even length palindromes over {0, 1}
    
*   13.16 odd length palindromes over {0, 1}
    
*   13.17 all palindromes over {0, 1}
    
*   13.18 all non-palindromes over {0, 1}
    
*   13.19 {*w* ∈ {0, 1, 2}^(\*) : *w* has an equal number of 0s, 1s, and 2s}
    
*   13.20 (Harder) {*w**w* : *w* ∈ {0, 1}^(\*)}
    
*   13.21 (Harder) The set of strings of matched parentheses over {(,)} (e.g., (()) and ()((())) are in the language, but ()) is not)
    
*   13.22 (Harder) The set of strings of matched parentheses over {(,), \[,\], {,}} (e.g., (\[\]) and (){\[()\]} are in the language, but (\]) is not)
    

Create Turing machines for the following functions:

*   13.23 Given a number in binary as input, multiply the number by 2.
    
*   13.24 Given a number in binary as input, increment the number by 2.
    
*   13.25 Given a number in binary as input, decrement the number by 1 (or output 0 if the input is zero).
    
*   13.26 (Harder) Given a pair of numbers in binary separated by the special # tape character, output the sum of the numbers.
    
*   13.27 (Harder) Given a pair of numbers in binary separated by the special # tape character, output the difference of the numbers.
    
*   13.28 (Harder) Given a pair of numbers in binary separated by the special # tape character, output the result of modding the first by the second.
    
*   13.29 (Harder) Given a pair of numbers in binary separated by the special # tape character, output the product of the numbers.
    
*   13.30 (Harder) Given a pair of numbers in binary separated by the special # tape character, output the quotient of the numbers (rounding down).
    

# Chapter 14Computability

DOI: [10.1201/9781003383284-14](https://doi.org/10.1201/9781003383284-14)

## 14.1 Why You Should Care

In this chapter we will study what Turing machines are capable of from a higher level and see why we believe this model of computation to be the one that captures everything we believe a computer capable of doing. We will then show that there is a problem that is uncomputable. Since we established Turing machines as our model of computation, we will see that no mechanical computer that currently exists or ever will exist can solve this problem. We will then show that a number of other problems are also uncomputable by bootstrapping from this one problem using a technique called a reduction, another important concept in computer science.

## 14.2 Variations of Turing Machines

While the standard model of the Turing machine from the last chapter is as powerful as we will need, we will see in this section that it is equivalent in power to seemingly more advanced models of computation, such as Turing machines that have multiple tapes.

We will first see how to construct a Turing machine with multiple tracks using a standard Turing machine. A two-track Turing machine has each cell on the tape split into a top and bottom part so that each cell can hold two symbols. (See [Figure 14.1](#chapter14.xhtml#fig14_1).) This model of the Turing machine can then make transitions based on the state and the symbols on both of the tracks.

![Figure 14.1 Multi-track TM](images/fig14_1.jpg)

[Figure 14.1](#chapter14.xhtml#b14fig14_1) Multi-track TM

We can simulate any such two-track Turing machine by treating the tape alphabet as pairs of symbols from the original tape alphabet. For example, if a cell had a 1 and a B in it, we would represent this with a single symbol [*B*]¹ and make a standard Turing machine that did whatever the two-track Turing machine did by designing the appropriate rules. Similarly, we can see that a multi-track Turing machine, for some number of tracks *k*, would be no more powerful than a standard Turing machine because we can replace the tape alphabet with *k*\-tuples that represent any combination of *k* symbols from the original tape alphabet.

We can also design multi-tape Turing machines in which there are multiple independent tapes, for which each tape has a separate head. (See [Figure 14.2](#chapter14.xhtml#fig14_2).) Now, each head can be at a different cell of the tape. A *k*\-tape Turing machine can be simulated by a 2*k*\-track Turing machine by using odd numbered tracks to represent the tapes and the even numbered tracks to maintain the head position of the track before it. We omit the details of how to design such a Turing machine as they would be excessively complex. (You can take a Theory of Computation course to learn more.) Since we know that we can simulate a 2*k*\-track Turing machine with a standard one, we can now simulate a Turing machine with any (finite) number of independent tapes with a standard Turing machine from the last chapter.

![Figure 14.2 Multi-tape TM](images/fig14_2.jpg)

[Figure 14.2](#chapter14.xhtml#b14fig14_2) Multi-tape TM

The point of demonstrating these variations is to show you that there are more complex models possible that are no more powerful than the Turing machine. These variations are also getting closer to models of computation you are used to in which you can keep track of multiple values at the same time.

## 14.3 The Church-Turing Thesis

Now that we have seen that Turing machines are capable of maintaining multiple tapes (variables in memory) and can perform many of the operations we deem necessary for computation (arithmetic, loops, conditionals) in examples and exercises in the last chapter, we are ready to make an assertion about the power of Turing machines. The following is one version of what is called the Church-Turing thesis, named after two pioneers in the theory of computation, Alonzo Church and Alan Turing.

The above statement is called a thesis because it is a hypothesis. Since the term “mechanical computation” is not well defined, the above thesis cannot be mathematically proved. It hypothesizes that any computation that we think is feasible can be done by a Turing machine. All modern computers are no more or less powerful than a Turing machine in that they can solve the same problems. Given enough time and memory, a Turing machine can perform any computation that we can do on a computer. Conversely, modern computers can perform any computation that a Turing machine is capable of given enough time and computer memory.

Now, this is not to say that we will never be able to build a computer that is more powerful than a Turing machine. It just means that we don't currently believe some more powerful computer is possible and all empirical evidence seems to support that belief.

## 14.4 Universal Turing Machines

An important property of the Turing machine is that it is powerful enough to simulate itself. That is, given the encoding of a Turing machine and an input string, we can design a Turing machine (called a **Universal Turing Machine**) that can simulate the given Turing machine on the given input.

You might be wondering how you can encode a Turing machine as a string. Since the description of a Turing machine is always finite, we can encode the description into a single string. For example, we can encode the name of the states, the input and tape alphabet, the starting and accepting states, and the blank symbol into a string. We can then encode the *δ* transition rules as sequences—for example, *δ*(*q*[0], 0) = (*q*[1], *B*, *R*) could be encoded by a string such as *q*0#0#*q*1#*B*#*R*, where # is a special separator symbol. Thus, any Turing machine can be represented with a string encoding.

Given such an encoding of a Turing machine, it is possible (with a lot of effort!) to design a Turing machine that could take such an encoding and use it to process the behavior of the Turing machine on some input string. We could do this by, for example, storing the input string on one tape, the current state on another, the head position on a third, and the Turing machine encoding on a fourth. For each step of the Turing machine simulation, we would look up what character is at the current head position and what state we are currently at and then search the Turing machine encoding tape for the correct move to execute next.

The idea of the Universal Turing Machine is important for a number of reasons. For one, it tells us that Turing machines are capable of running other Turing machines. In fact, this is exactly what happens when you run a program using a compiler or interpreter—these are examples of Universal Turing Machine programs in that they can process arbitrary (correct) code.

Another important reason for Turing machines being able to simulate other Turing machines is that we can have a Turing machine call another Turing machine in a subroutine, allowing us to chain together increasingly complex computations.

## 14.5 Recursive and Recursively Enumerable Languages

We are now ready to define what languages are computable.

Note that we specify that the Turing machine for the language must halt on all inputs. This is because Turing machines are allowed to reject a string by running forever. Since computations that run forever are not very useful, we specify that the Turing machine must halt and accept or halt and reject on every possible input.

There is also a broader collection of languages that defines everything a Turing machine is capable of computing called the recursively enumerable languages.

Notice that this collection of languages contains the recursive ones because recursive languages all have Turing machines (that also must halt on all inputs). This classification isn't as useful from a practical standpoint because it allows Turing machines to run forever on some inputs, but it does help us with some proofs later in this chapter. Next, we prove a few results based on these definitions.

Notice in the above proof that we had to run the simulations for *M* and $\\overset{―}{M}$ in parallel because it could be possible for either *M* or $\\overset{―}{M}$ to run forever on rejection and so if we had run them sequentially the computation may never end.

## 14.6 A Non-Computable Problem

To show that there are non-recursive problems, we first need to understand that all strings and Turing machines can be enumerated (listed in a numbered list). To list off all the strings in a fixed order, we can use shortlex ordering. For a review of shortlex ordering of strings, take a look at [Section 1.10](#chapter1.xhtml#sec1_10). To list all Turing machines, we can write an encoding for each one (see [Section 14.4](#chapter14.xhtml#sec14_4)) and then also use a shortlex ordering on these. Let us call the Turing machines generated in this manner *M*[*i*] for each string *i*.

We are now ready to define the Diagonal Problem (*D*). The Diagonal Problem can be intuitively thought of as the set of strings that when interpreted as a Turing machine accepts itself as an input.

To understand the above definition, we have to interpret the string *i* in two distinct ways. In one interpretation, we treat the string *i* as the encoding for a Turing machine *M*[*i*] as we saw in [Section 14.4](#chapter14.xhtml#sec14_4). If the string *i* does not correspond to the encoding of any Turing machine, then we simply define *M*[*i*] to be a simple Turing machine that rejects all inputs by immediately halting and rejecting. The second interpretation of *i* is simply that of a string—an input string to be accepted or rejected.

Next, we define the complement of the language *D*, called $\\overset{―}{D}$.

We will now show that $\\overset{―}{D}$ does not have a Turing machine that accepts it. Before formally proving this, let us build some intuition about why this is the case. We use a technique called **diagonalization**.

Imagine that we could construct an infinitely large table that has all the Turing machines on the rows and the strings on the columns, as illustrated in [Figure 14.3](#chapter14.xhtml#fig14_3). For simplicity, we will assume that the strings are over the alphabet {0, 1}. Each entry in the table will indicate whether the Turing machine on the row accepts (A) the string on the column or rejects (R) it. (The entries in [Figure 14.3](#chapter14.xhtml#fig14_3) are not real and just shown for illustrative purposes.) We will focus on the diagonal entries of the table (marked with boxes) as the diagonal language and its complement are about these values. We can show that *M*[*λ*] is not a Turing machine for $\\overset{―}{D}$ because (in this example table) *λ* is accepted by *M*[*λ*], putting *λ* in *D* (by the definition of *D*) but then a Turing machine for $\\overset{―}{D}$ should reject *λ*. A similar argument shows that *M*[0] is also not a valid Turing machine for $\\overset{―}{D}$. On the other hand, the Turing machine *M*[1] rejects the string 1, which means that 1 is in $\\overset{―}{D}$, but now *M*[1] cannot be a Turing machine for $\\overset{―}{D}$ as it should have accepted 1. Continuing this argument for each diagonal entry (whether it is A or R), shows that no Turing machine in our list of all possible Turing machines can accept $\\overset{―}{D}$. This shows that $\\overset{―}{D}$ is not recursively enumerable.

![Figure 14.3 Table of whether each Turing machine accepts/rejects each string](images/fig14_3.jpg)

[Figure 14.3](#chapter14.xhtml#b14fig14_3) Table of whether each Turing machine accepts/rejects each string

We can conclude from this the following result for *D*.

We have shown that $\\overset{―}{D}$ and *D* are not recursive or computable, but they are not very natural languages. We will use them to next show that other, more easy to understand problems, are not computable as well.

## 14.7 Reductions

We will now show how to prove the non-computability of another language by bootstrapping from the previous two languages using a technique called a reduction. Consider the following language:

The language *A* consists of all pairs of Turing machine encodings and strings such that the Turing machine accepts the string. We encode pairings such as this by introducing new symbols (, ), and ,. If we could compute this language, we could then tell whether any arbitrary program accepts an arbitrary input. Unfortunately, no Turing machine (that halts on all inputs) exists for it as we see next.

Intuitively, the above reduction uses the fact that determining whether *M*[*i*] accepts an arbitrary string *x* should be even harder than determining whether *M*[*i*] accepts the specific string *i*.

Since we believe Turing machines to be able to perform any mechanical computation possible on a computer, we can rephrase the implications of the above theorem thus:

> It is impossible to design a program that can predict the output of an arbitrary program on arbitrary input.

## 14.8 Program Comparison

We'll next see a reduction that is a little more involved. The notation *L*(*M*[*a*]) denotes the language of the Turing machine *M*[*a*].

The language *SAME* is conceptually the pairs of Turing machines that behave identically on all inputs. Translated from Turing machines to more practical usage, the uncomputability of *SAME* implies the following:

> It is impossible to design a program that can tell if two programs behave identically on all inputs.

By showing that this problem is non-computable, this means that it is impossible for your CS instructor to design a program that takes as input two programs (for example, a working solution and a student's submission) and determine whether they behave identically on all inputs.

At the heart of this reduction is the design of the Turing machine *M*[*a*] that ignores its input and simulates *M*[*i*] on input *i*. It is designed specifically so that for any *i* ∈ *D* the Turing machine *M*[*a*] will always accept giving *L*(*M*[*a*]) = *Σ*^(\*) and for all *i* ∉ *D* the Turing machine *M*[*a*] always rejects giving *L*(*M*[*a*]) = ⌀. This stark dichotomy allows us to use *M*[*a*] in the reduction to distinguish whether a given string is in *D* or not by using a Turing machine for *SAME*.

More specifically, we have set up the Turing machines *M*[*a*] and *M*[*b*] that are given as input to the Turing machine for *SAME* as follows:

 
| *i* ∈ *D* ? || *M*[*i*] accepts *i*? || *L*(*M*[*a*]) || *L*(*M*[*a*]) = *L*(*M*[*b*]) ? || *M* accepts || *M*^′ accepts |
| --- | --- | --- | --- | --- | --- |
| Yes || Yes || *Σ*^(\*) || Yes || Yes || Yes |
| --- | --- | --- | --- | --- | --- |
| No || No || ∅ || No || No || No |

The proof then takes the following form:

1.  Assume for a contradiction that some Turing Machine *M* accepts *SAME* and halts on all inputs.
    
2.  Build a new machine *M*^′ that on input *i* halts and accepts if *i* ∈ *D* and halts and rejects if *i* ∉ *D*. It does so by running *M* (the Turing machine for *SAME*) on the Turing machines *M*[*a*] and *M*[*b*] described above. (This is the part of the proof that you will have to adapt, using a table similar to the one above, to solve most of the exercises.) Since *M* halts on all inputs, so must *M*^′.
    
3.  Since we showed in the last step that *M*^′ is a Turing machine for *D* that halts on all inputs, this shows that *D* is recursive. This is a contradiction, so *SAME* can not be recursive.
    

## 14.9 The Halting Problem

Another classic problem that is known to be uncomputable is the **Halting Problem**. Simply put, the Halting Problem asks whether a given computation will ever halt or if it will run forever. By showing that this problem is not recursive we know, for example, that it is impossible to design a compiler that can always detect infinite loop bugs in arbitrary code.

Next, we define the Halting Problem and show that it is undecidable as well.

Notice that this definition is about whether a Turing machine halts or not on a given input, making it about the behavior of the Turing machine beyond whether it accepts certain strings or not. This makes the reduction a little more complicated.

In practical terms:

> It is impossible to design a program that can tell if another program will ever terminate.

The Halting Problem is one of the classic problems in computer science that is uncomputable.

## 14.10 Classes of Languages

When studying the difficulty of solving a problem, computer scientists use the notion of a class of problems.

In conclusion, here is a diagram with the containment properties of these classes.

![A Venn diagram defines the relationship between different classes of languages. The innermost circle represents regular languages, surrounded by a larger circle representing context free languages, which in turn is surrounded by a circle representing recursive languages. The outermost circle represents recursively enumerable languages.](images/fig14_4.jpg)

Figure 14.4 All classes of languages in this book

## 14.11 Chapter Summary and Key Concepts

*   **Variations** of Turing-machine models include ones with **multiple tracks** and **multiple tapes**. These models are no more powerful than the standard Turing machine model.
    
*   The **Church-Turing thesis** states that all mechanical computation can be performed by a Turing machine.
    
*   The **Universal Turing machine** is one that takes as input the encoding of a Turing machine and an input and simulates that Turing machine on that input.
    
*   A language is called **recursive** or **computable** or **decidable** if there exists a Turing machine that accepts it and halts on all inputs.
    
*   A language is called **recursively enumerable** if there exists a Turing machine that accepts it.
    
*   A language is recursive if and only only if its complement is recursive.
    
*   A language is recursive if and only if it and its complement are recursively enumerable.
    
*   The **diagonal language *D*** and its complement can be shown to be non-recursive using **diagonalization**.
    
*   **Reductions** are a way of showing that a language is not recursive. To do this, you must reduce from a problem known not to be recursive to the problem being shown is not recursive.
    
*   Many problems, such as determining (1) whether a Turing machine (program) will accept a given input, (2) whether two Turing machines (programs) accept the same language, and (3) whether a Turing machine (program) will ever halt are all known to be non-recursive.
    
*   A **class** of problem is a set of languages that have the same computational difficulty. These include **regular, context-free, recursive**, and **recursively enumerable** languages.
    

## EXERCISES

Read the entries in the Stanford Encyclopedia of Philosophy on Computability ([https://plato.stanford.edu/entries/computability/](https://plato.stanford.edu/entries/computability/)) and Alan Turing ([https://plato.stanford.edu/entries/turing/](https://plato.stanford.edu/entries/turing/)) and other sources to give short answers to the following questions:

*   14.1 Who designed the Lambda Calculus?
    
*   14.2 What was Gödel's Incompleteness Theorem?
    
*   14.3 What was the *entscheidungsproblem*?
    
*   14.4 What was the title of the paper in which Turing introduced the Turing machine?
    
*   14.5 What is the Turing Test?
    
*   14.6 Do you think that a Turing machine can simulate a human brain?
    

Prove that the following problems are undecidable using reductions. For each problem, write a sentence explaining in words what the implication of the undecidability of the language is for computer programs.

*   14.7 *A**L**L* = {*i* : *L*(*M*[*i*]) = *Σ*^(\*)}
    
*   14.8 *I**N**F**I**N**I**T**E* = {*i* : *L*(*M*[*i*]) is infinite}
    
*   14.9 *N**O**N**E**M**P**T**Y* = {*i* : *L*(*M*[*i*]) ≠ ⌀}
    
*   14.10 *H**A**S**E**M**P**T**Y* = {*i* : *λ* ∈ *L*(*M*[*i*])}
    
*   14.11 *F**U**L**L**C**O**V**E**R* = {(*i*, *j*) : *L*(*M*[*i*]) ∪ *L*(*M*[*j*]) = *Σ*^(\*)}
    
*   14.12 *S**U**B**S**E**T* = {(*i*, *j*) : *L*(*M*[*i*]) ⊆ *L*(*M*[*j*])}
    
*   14.13 *D**I**F**F**E**R**E**N**T* = {(*i*, *j*) : *L*(*M*[*i*]) ≠ *L*(*M*[*j*])}
    
*   14.14 *O**V**E**R**L**A**P* = {(*i*, *j*) : *L*(*M*[*i*]) ∩ *L*(*M*[*j*]) ≠ ⌀}
    
*   14.15 *E**M**P**T**Y* = {*i* : *L*(*M*[*i*]) = ⌀} (Hint: Reduce from $\\overset{―}{D}$ rather than *D*)
    
*   14.16 *D**I**S**J**O**I**N**T* = {(*i*, *j*) : *L*(*M*[*i*]) ∩ *L*(*M*[*j*]) = ⌀} (Hint: Reduce from $\\overset{―}{D}$)
    
*   14.17 (Harder) *F**I**N**I**T**E* = {*i* : *L*(*M*[*i*]) is finite}
    
*   14.18 (Harder) *S**I**Z**E*5 = {*i* : *L*(*M*[*i*]) has exactly 5 strings}
    
*   14.19 (Harder) *O**N**E**S**T**A**R* = {*i* : *L*(*M*[*i*]) = 1^(\*)}
    
*   14.20 (Harder) *R**E**G**U**L**A**R* = {*i* : *L*(*M*[*i*]) is regular}
    

# Appendix ACounting

## A.1 Why You Should Care

Being able to count up the number of different ways or combinations that are possible for a problem is an exceedingly useful skill in computer science. It is needed for tasks as different as counting the number of passwords (to improve computer security), determining the number of ways processes can be scheduled, to measuring the search space for a variety of games so that you can compute an optimal play strategy.

## A.2 The Multiplication Rule

Remember back in [Chapter 3](#chapter3.xhtml) when we created truth tables? A truth table with two variables had 4 rows but another with three variables had 8 rows. If we added another variable, we would need a total of 16 rows. The number of rows doubles each time we add a variable. Why is this?

The easiest way to think about the number of rows needed by a truth table is to consider the possibilities. The first variable can be T or F for a total of 2 possibilities. When we add a second variable, each of the original possibilities is now paired with a T or F for the second variable for a total of 2 × 2 = 4. Continuing in this manner, if we have *n* variables, we need 2 × 2 × … × 2 (*n* times) or 2^(*n*) rows. Put another way, every time we add a variable we need to have two copies of the previous table: one for when the new variable is T and another for when it is F. This is a demonstration of the multiplication rule.

It is important to note here that repeated values are allowed, e.g., more than one variable can be T in the same row of a truth table. The count is quite different when values are not allowed to be repeated and this will be explored further in later sections of this chapter.

## A.3 Arrangements Without Repeats, Order Matters

Let us enumerate the number of ways you can rearrange a list of three items (say, 1, 2, and 3). The different ways are \[1,2,3\],\[1,3,2\],\[2,1,3\],\[2,3,1\],\[3,1,2\],\[3,2,1\], for a total of six arrangements. Where did this number six come from? Well, we had three options for the first number (1, 2, or 3), followed by any of the two remaining numbers for the second, followed by a single option for the third. Multiplying these out, we get 3 × 2 × 1 or 6.

Extending this idea, we get that the number of ways to arrange a list of size *n* is *n* × (*n* − 1) × … × 1. We give a special name to this function called factorial.

We can think of rearrangements without repetitions as a special case of the multiplication rule in which *c*[1] = *c*[2] + 1 = *c*[3] + 2 = ….

## A.4 Arrangements Without Repeats, Order Doesn't Matter

When counting the number of hands in a card game the order in which you get dealt cards usually doesn't matter. For example, getting the 2, 3, and 4 of spades is the same as getting the 4, 3, and 2 of spades. In such situations, where the order in which items appear in the arrangement are immaterial, we are effectively over-counting the number of arrangements by the number of arrangements of that size. For instance, when drawing three cards, there are 3! or 6 different ways to be dealt the same set of three cards. To correct for this over-counting, we can divide the total number of rearrangements by six.

In general, if you are picking exactly *k* items without repetition from a collection of *n* items and the order doesn't matter, then we use combinations.

## A.5 Chapter Summary and Key Concepts

*   The **multiplication rule** is that if there are *c*[1] possibilities for a first option, *c*[2] possibilities for a second option, …, *c*[*n*] possibilities for an *n*th option, then the total number of combinations of all the options is *c*[1]*c*[2]…*c*[*n*].
    
*   The number of arrangements of *n* distinct items when there are **no repeats and order matters** is *n*!.
    
*   The number of arrangements of *k* items out of *n* distinct items when there are **no repeats and order doesn't matter** is $\\left( \\frac{n}{k} \\right) = \\frac{n!}{(n - k)!k!}.$
    

## Exercises

Multiplication rule (repeats allowed, order matters)

*   A.1 How many license plates are possible with a three letter combination followed by a 4 digit number? (Note: the number may have a leading 0.)
    
*   A.2 How many variable names of length 5 are possible? Recall that a variable name must start with a letter (upper or lower case) or underscore character and the other positions can have a letter (upper or lower case), underscore, or digit.
    
*   A.3 Suppose you are required to enter an eight character password. The first character must be a letter (upper or lower case). The next 6 characters can be upper/lower case letters, or digits 0-9. The last character must be one of these punctuation marks: underscore, asterisk, exclamation point, caret, dollar sign, percent sign, or ampersand. How many different passwords are possible?
    
*   A.4 How many passwords are possible when you string together four random English words (repetitions allowed)? You may assume that there are 170,000 words in the English language. (Relevant XKCD: [https://xkcd.com/936/](https://xkcd.com/936/))
    

Permutations (no repeats, order matters)

*   A.5 Four players are engaged in a Scrabble competition. There is a large prize for first place and a smaller one for second place. How many different ways can these two prizes be distributed?
    
*   A.6 How many different ways can you select and arrange four out of ten cards (in order) in your hand?
    
*   A.7 Three friends are have four ice pops to choose from: apple, mango, orange, and grape. In how many ways can they pick one each?
    
*   A.8 There are nine new movies available on your streaming service. In how many ways can you watch one different movie each night this week?
    
*   A.9 You're going on a road trip with seven other friends and have room for three of them in your car. If it matters which seat each person takes (front passenger's seat, rear left, and rear right), then how many ways are there to pick friends for your car?
    

Basic combinations (no repeats, order doesn't matter)

*   A.10 How many ways are there to be dealt a seven-card hand from a standard 52 card deck?
    
*   A.11 How many ways are there to select a four person group from a class of 20 students?
    
*   A.12 How many different sums of money can you make from exactly two coins out of a penny (1 cent), a nickel (5 cents), a dime (10 cents), and a quarter (25 cents)?
    
*   A.13 Suppose that 20 people all decide to high five each other. How many high fives would this amount to?
    
*   A.14 Ten kids are making teams to play soccer against one another. First, two captains are selected. The captains then alternate picking kids for their team until all the kids are on a team. How many different ways are there to end up with a pair of teams selected in this manner?
    
*   A.15 A lottery involves selecting six numbers without replacement from 1 to 70. If you select six of these numbers at random, what is the probability of winning?
    

# Appendix BProbability

## B.1 Why You Should Care

Computer scientists need to know about probability to be able to design randomized algorithms—ones that have random choices made in them. Randomized algorithms are useful because they can either improve the expected running time (these are called Las Vegas algorithms) or allow faster computation at the expense of a small probability of failure (called Monte Carlo algorithms). In addition, randomness is important for designing data structures such as hash functions, computing in scientific applications such as Monte Carlo simulations, and making video game AI opponents less predictable.

## B.2 Sample Spaces

When studying probabilities of events, we must first consider the sample space of possibilities. For example, when you roll a six-sided die there are six possible outcomes or possible rolls. When you flip a coin there are two outcomes (heads or tails). This set is called the sample space.

## B.3 Events

When studying probability, we will often want to group together a number of outcomes and refer to them collectively as an event.

The probability of an event is simply the sum of probabilities of the outcomes that make up that event.

The probability of the complement of an event is one minus the probability of the event itself.

For mutually exclusive events, the probability that either event happens is the sum of the probabilities of the two events.

A pair of events is called **independent** if neither event affects the probability of the other.

We now recast the definition mathematically.

## B.4 Chapter Summary and Key Concepts

*   The **sample space** of a random trial is the set of all possible outcomes of the trial.
    
*   The **probability** of an outcome *x* is denoted by Pr (*x*), where 0 ≤ Pr (*x*) ≤ 1. The sum of the probabilities of all the outcomes in the sample space must be 1.
    
*   An **event** is a subset of a sample space. The probability of the event is the sum of the probabilities of the outcomes that make up the event.
    
*   The **complement** of an event is the complement of the event set.
    
*   Two events are called **mutually exclusive** if their sets do not intersect.
    
*   Two events are called **independent** if neither affects the probability of the other.
    

## Exercises

A standard deck of cards has one each of the values Ace, 2 through 10, Jack, Queen, and King of each the suits Hearts (red ♥), Diamonds (red ♠), Clubs (black ♣), and Spades (black ♠) for a total of 13 × 4 = 52 cards.

*   B.1 What is the probability of drawing an Ace of Hearts from a deck?
    
*   B.2 What is the probability of drawing an Ace from a deck?
    
*   B.3 What is the probability of drawing a Diamond from a deck?
    
*   B.4 What is the probability of drawing an Ace or a King from a deck?
    
*   B.5 What is the probability of drawing a red card (Heart or Diamond) from a deck?
    
*   B.6 What is the probability of drawing an Ace or a Black card (Club or Spade) from a deck?
    
*   B.7 What is the probability of not drawing an Ace of Spades from a deck?
    
*   B.8 What is the probability of not drawing a Queen from a deck?
    
*   B.9 What is the probability of not drawing a King or Queen from a deck?
    
*   B.10 What is the probability of not drawing an Ace or a red card (Heart or Diamond) from a deck?
    

For the following questions, you should assume that cards are returned to the deck and shuffled before the next card is drawn (this is called “sampling with replacement”):

*   B.11 What is the probability of drawing an Ace and then a Queen from a deck?
    
*   B.12 What is the probability of drawing two Aces from a deck?
    
*   B.13 What is the probability of drawing an Ace and then a Black card (Club or Spade) from a deck?
    
*   B.14 What is the probability of drawing an Ace and then a card that's not an Ace from a deck?
    
*   B.15 What is the probability of drawing two cards neither of which is an Ace from a deck?
    

For the following questions, you should assume that cards are *not* returned to the deck before the next card is drawn (this is called “sampling without replacement”):

*   B.16 What is the probability of drawing an Ace and then a Queen from a deck?
    
*   B.17 What is the probability of drawing two Aces from a deck?
    
*   B.18 What is the probability of drawing an Ace and then a Black card (Club or Spade) from a deck?
    
*   B.19 What is the probability of drawing an Ace and then a card that's not an Ace from a deck?
    
*   B.20 What is the probability of drawing two cards neither of which is an Ace from a deck?
    

The following questions assume that you have already read [Appendix A](#appA.xhtml#appA). In the game poker, each player is dealt a hand with five cards the order of which does not matter.

*   B.21 In poker, what is the probability of being dealt a royal flush (10, Jack, Queen, King, and Ace all of the same suit)?
    
*   B.22 In poker, what is the probability of being dealt a flush (all five cards of the same suit)?
    
*   B.23 In poker, what is the probability of being dealt a straight (consecutive cards such as Ace, 2, 3, 4, 5 or 10, Jack, Queen, King, Ace)?
    
*   B.24 In poker, what is the probability of being dealt a straight flush (consecutive cards of the same suit)?
    
*   B.25 In poker, what is the probability of being dealt a four-of-a-kind (four cards with the same value and one other)?
    
*   B.26 In poker, what is the probability of being dealt a full house (three cards of the same value and two other cards with the same value)?
    
*   B.27 In poker, what is the probability of being dealt a three-of-a-kind (three cards of the same value and the remaining two different from the rest and each other)?
    
*   B.28 In poker, what is the probability of being dealt a pair (two cards of the same value and all the remaining three different from the rest and each other)?
    
*   B.29 In poker, what is the probability of being dealt a two pair (two pairs of cards of the same value and a fifth card with value different from the rest)?
    
*   B.30 (Harder) In poker, what is the probability of not getting any of the above hands?
    

# Appendix CElementary Number Theory

## C.1 Why You Should Care

Number theory is the basis of a number of algorithms involving hash functions, pseudo-random number generators, and cryptography. Most modern cryptography and cryptocurrencies would not be possible without it.

## C.2 Modular Arithmetic

When we divide integers in Python, we are actually performing floor division. **Floor division** is when we divide an integer by a non-zero integer and round down.

We can now define the quotient and remainder for division as follows:

The quotient and remainder can be computed using the following division algorithm: We get the remainder using an operation called the **modulus**, abbreviated to **mod**. This is the same as the % operation in most programming languages, though it operates differently for negative numbers in different languages (as with division).

The mod terminology is also sometimes used to show that two numbers are related as they have the same remainder when divided by the same divisor. This is called congruence modulo the divisor and written *a* ≡ *b* (*m**o**d* *c*) (“*a* is congruent to *b* modulo the divisor *c*”).

We say that an integer *a* is divisible by another non-zero integer *b* (written *b* | *a*) if *b* evenly divides into *a* with no remainder. We say *b* is a **divisor** or **factor** of *a*.

For a variety of numerical algorithms, such as reducing fractions to lowest terms, we need to compute the greatest common divisor (also called the highest common factor in some parts of the world) between a pair of numbers.

Another useful function on a pair of positive integers is the least common multiple that is used for finding the common denominator of two fractions.

The greatest common divisor and lowest common multiple are related to one another. For any positive integers *a* and *b*, we have that gcd (*a*, *b*) ⋅ *l**c**m*(*a*, *b*) = *a* ⋅ *b*. This means that we can easily compute one if we have the other. We usually compute the gcd using Euclid's algorithm that you will learn about next.

## C.3 Euclid's Algorithm for GCD

Rather than try every possible divisor of a pair of numbers, Euclid's algorithm computes the gcd very efficiently and elegantly.

## C.4 Chapter Summary and Key Concepts

*   **Floor division** is when integers are divided with no remainder.
    
*   When dividing two positive integers, the result of the floor division is called the **quotient**. Any remaining amount is called the **remainder** and is computed using the **mod** operation.
    
*   The **greatest common divisor** of a pair of positive integers is the largest integer that divides both.
    
*   The **least common multiple** of a pair of positive integers is the smallest positive integer that is a multiple of both.
    
*   **Euclid's algorithm** allows us to quickly compute the greatest common denominator for two positive integers.
    

## Exercises

Compute the quotient and remainder in each of the following cases:

*   C.1 10 divided by 4
    
*   C.2 24 divided by 7
    
*   C.3 \-12 divided by 5
    
*   C.4 17 divided by -10
    

Compute the gcd and lcm of the following pairs of numbers. Show the steps of Euclid's algorithm for the gcd.

*   C.5 21 and 63
    
*   C.6 10 and 16
    
*   C.7 15 and 23
    
*   C.8 17 and 64
    
*   C.9 19 and 128
    
*   C.10 128 and 144
    

# Appendix DAsymptotic Notation

## D.1 Why You Should Care

When analyzing the efficiency of our algorithms, computer scientists use asymptotic notation to capture such metrics as running time, memory used, number of queries, energy usage, etc. Analyzing the rate of growth of each of these quantities is far more important than computing the exact value for a few instances.

## D.2 Why Asymptotic Notation

Suppose that you are comparing a pair of algorithms and trying to decide which one you will implement for an application that you are working on. If you are interested in understanding which one will run quicker, you may count up the number of basic operations of each and use this for comparison. To make things concrete, say that you have one algorithm that, on an input size of *n*, needs *f*(*n*) = 1000*n* operations and another that needs *g*(*n*) = *n*² operations. If you were to run these on small instances of your problem, you would likely find that the second algorithm runs faster. However, in practice computer scientists are wary of small instances as we know that data sizes are constantly increasing and we should instead plan ahead for large data sets. This is where asymptotic notation allows us to compare the above algorithms for larger sizes.

In the above example, we would say that the first algorithm is a *Θ*(*n*) (pronounced “theta of *n*”) time algorithm and the second is *Θ*(*n*²) time. In other words, the rate of growth of the second function is considerably higher than the first. For example, if we increase the size a thousand-fold, then the first algorithm's run-time goes up by a factor of a thousand but the second's run-time goes up by a factor of one million! When working with large size inputs the second algorithm will be several orders of magnitude slower than the first.

When performing asymptotic analysis, we ignore constant multiplicative factors such as the 1000 in *f*(*n*) = 1000*n*. In most algorithms these factors are not very large and don't significantly affect the analysis. We also ignore how algorithms perform on small input sizes as these are not as relevant to us most of the time. Both these considerations have lead to computer scientists using asymptotic notation as the way we analyze the performance of our algorithms.

## D.3 Theta Notation

The most useful form of asymptotic notation is theta notation since it gives an exact characterization of the growth rate of the function. When in doubt about which type of asymptotic notation you should be using, theta notation is your best bet since it is the most precise.

In other words, if we can sandwich the function *f*(*n*) between constant multiples of *g*(*n*) for sufficiently large *n*, then we can say that *f*(*n*) = *Θ*(*g*(*n*)).

Notice that there could be several different constants *n*[0], *c*[1], *c*[2] that could also work. Which ones you pick is not important as long as they show the above sandwich property.

## D.4 Big-O and Big-Ω Notation

Sometimes we are unable to, or don't care to, compute the exact characterization of a function and are happy to settle for an upper or lower bound. For example, we may want to argue that our sorting routine takes at most quadratic time. In such a case, we might use Big-O for an upper bound and Big-Ω (“big omega”) for a lower bound.

This is identical to the definition and examples introduced in [Section 3.7](#chapter3.xhtml#sec3_7). Since Big-O notation is only an upper bound, it may not be a precise bound on the function that you are studying. This is why you should use theta notation if you are trying to be precise. Big-O notation can give an overestimate of the growth rate of a function as can be seen in the following example:

Similar to upper bounds, we sometimes have need for lower bounds on the growth of a function. For example, we may want to argue that the runtime of an algorithm is always at least quadratic.

Once again note that since Big-Ω notation is only a lower bound, it may not be a tight bound.

## D.5 Strict Bounds

All the above bounds were inclusive ones that included the function being compared with. In some circumstances we want to say that the asymptotic growth rate of a function is strictly smaller than, or strictly larger than, another function. This is where little-o and little-*ω* (“little omega”) notation is used.

The strict lower bound little-*ω* is defined similarly.

## D.6 Common Errors

There are a number of common errors that novices make with asymptotic notation. Some that you will want to avoid are listed below:

1.  Asymptotic notation is about the growth rate of functions and not just the running time of an algorithm. Thus, for example, you should say that an algorithm has *O*(*n*) *running time* and not simply that an algorithm is *O*(*n*). Asymptotic notation can also be used to analyze memory, disk usage, number of database queries, and other properties of algorithms.
    
2.  Never say “at least Big-O” since Big-O is an upper bound. Instead, use Ω or, better yet, Θ notation. When in doubt, be precise and use Θ notation unless you really don't have an exact characterization of the function.
    
3.  While it is the case that 2*n* = *O*(*n*) and 3*n* = *O*(*n*), be wary of any circumstance in which you get something like *n* + *n* + … + *n* (*n* times) = *O*(*n*) since this is not true.
    

## D.7 Chapter Summary and Key Concepts

*   **Asymptotic notation** allows us to compare the growth rate of functions. It is used extensively when analyzing the time and memory used by algorithms.
    
*   **Theta (Θ) notation** is used to exactly capture the growth rate of a function. We say *f*(*n*) is *Θ*(*g*(*n*)) if there exists *n*[0], *c*[1], *c*[2] > 0 such that for all *n* ≥ *n*[0] we have that *c*[1]*g*(*n*) ≤ *f*(*n*) ≤ *c*[2]*g*(*n*).
    
*   **Big-O (*O*) notation** is used to compute upper bounds on a function. We say *f*(*n*) is *O*(*g*(*n*)) if there exists *n*[0], *c* > 0 such that for all *n* ≥ *n*[0] we have that *f*(*n*) ≤ *c**g*(*n*).
    
*   **Big-Omega (Ω)** is used to compute lower bounds on a function. We say that *f*(*n*) is *Ω*(*g*(*n*)) if there exists *n*[0], *c* > 0 such that for all *n* ≥ *n*[0] we have that *c**g*(*n*) ≤ *f*(*n*).
    
*   **Little-o (*o*) notation** is used to compute strict upper bounds on a function. We say that *f*(*n*) is *o*(*g*(*n*)) if for all *c* > 0 there exists a constant *n*[0] > 0 such that for all *n* ≥ *n*[0] we have that *f*(*n*) < *c**g*(*n*).
    
*   **Little-omega (*ω*) notation** is used to compute strict lower bounds on a function. We say that *f*(*n*) is *ω*(*g*(*n*)) if for all *c* > 0 there exists a constant *n*[0] > 0 such that for all *n* ≥ *n*[0] we have that *c**g*(*n*) < *f*(*n*).
    

## Exercises

Prove the following by giving constants and then showing that the inequalities hold:

*   D.1 *n*² = *O*(*n*²)
    
*   D.2 3*n*² = *O*(*n*³)
    
*   D.3 2*n* + 3 = *O*(*n*)
    
*   D.4 2*n*² + 4*n* = *O*(*n*²)
    
*   D.5 3*n*² − 4*n* + 5 = *O*(*n*²)
    
*   D.6 *n*² = *Ω*(*n*²)
    
*   D.7 7*n*⁴ = *Ω*(*n*²)
    
*   D.8 3*n* + 4 = *Ω*(*n*)
    
*   D.9 4*n*² − 3*n* = *Ω*(*n*²)
    
*   D.10 *n*² − 2*n* + 3 = *Ω*(*n*²)
    
*   D.11 *n*³ = *Θ*(*n*³)
    
*   D.12 7*n*² = *Θ*(*n*²)
    
*   D.13 *n* + 8 = *Θ*(*n*)
    
*   D.14 *n*² + 2*n* = *Θ*(*n*²)
    
*   D.15 4*n*² − 5*n* + 6 = *Θ*(*n*²)
    
*   D.16 *n*² = *o*(*n*³)
    
*   D.17 100*n*³ = *o*(*n*⁴)
    
*   D.18 *n*⁵ = *ω*(*n*⁴)
    
*   D.19 10*n*³ = *ω*(*n*²)
    

Prove the following properties.

*   D.20 If *f*(*n*) = *O*(*h*(*n*)) and *g*(*n*) = *O*(*h*(*n*)) then *f*(*n*) + *g*(*n*) = *O*(*h*(*n*)).
    
*   D.21 If *f*(*n*) = *O*(*g*(*n*)) and *g*(*n*) = *O*(*h*(*n*)) then *f*(*n*) = *O*(*h*(*n*)).
    
*   D.22 We have *f*(*n*) = *O*(*g*(*n*)) if and only if *g*(*n*) = *Ω*(*f*(*n*)).
    
*   D.23 We have *f*(*n*) = *o*(*g*(*n*)) if and only if *g*(*n*) = *ω*(*f*(*n*)).
    
*   D.24 Prove that *f*(*n*) = *Θ*(*g*(*n*)) if and only if *f*(*n*) = *O*(*g*(*n*)) and *f*(*n*) = *Ω*(*g*(*n*)).
    
*   D.25 Prove that any polynomial of degree *d* is *O*(*n*^(*d*)). That is, for any *c*[0], *c*[1], *c*[2], …, *c*[*d*] where *c*[*d*] > 0, show that $\\sum\\limits\_{i = 0}^{d}c\_{i}n^{i} = O(n^{d})$.
    
*   D.26 Prove that any polynomial of degree *d* is *Θ*(*n*^(*d*)). That is, for any *c*[0], *c*[1], *c*[2], …, *c*[*d*] where *c*[*d*] > 0, show that $\\sum\\limits\_{i = 0}^{d}c\_{i}n^{i} = \\Theta(n^{d})$.
    
*   D.27 Prove that for any base *b* > 1, log[*b*](*n*) = *Θ*(log[2](*n*)). (Hint: Use the change of base formula $\\log\_{b}(a) = \\frac{\\log\_{d}(a)}{\\log\_{d}(b)}.)$
    
*   D.28 Prove that for any *e* > 0, log[2](*n*) = *O*(*n*^(*e*)). (Hint: Choose *c* = 1/*e* and use the fact that log[2](*x*) < *x* for all *x* > 0.)
    

# Appendix EGraphs

## E.1 Why You Should Care

Graphs are a data type that have many applications in computer science. They show up when we study computer networks and social networks and when your GPS finds the shortest route to your destination. In fact, there are so many applications of graphs in computer science that there are entire courses taught on the subject.

## E.2 Formal Definition

Simply put, a graph is collection of objects, called nodes or vertices, together with connections between some of them, called edges. While this sounds like a rather simple description, the study of graphs involves a large array of ideas and algorithms.

The above example is technically called an undirected graph. In some situations, we want the edges to be directed from one vertex to another. Some applications where this might be useful include one-way roads and relationships that are not symmetric (e.g., you could follow a celebrity on a social network, but they may not follow you back).

## E.3 Graph Representation

There are two standard ways to represent graphs: adjacency lists and adjacency matrices.

The adjacency list representation of a graph maintains lists of vertices that each vertex is adjacent to, as in the following examples:

The adjacency matrix representation of a graph uses a matrix or table to indicate when there is an edge between each vertex on the rows with each vertex on the columns, as seen in the following examples:

The adjacency list and adjacency matrix representations each have their own advantages. The adjacency list might be a lot smaller in the case where most pairs of vertices don't have edges (e.g., social networks) as the total space usage is proportional to the number of vertices plus the number of edges (*O*(|*V*| + |*E*|)). An adjacency matrix on the other hand always uses the same amount of space equal to the square of the number of vertices (*O*(|*V*|²)), which can get prohibitive when there are a large number of vertices.

On the other hand, adjacency matrices have very fast lookups. To see if a pair of vertices has an edge between them, we can just look up the matrix in constant (*O*(1)) time. The time to perform a similar operation on an adjacency list is proportional to the size of the list, which could be as large as the number of vertices in the graph (*O*(|*V*|)). Thus, which representation to pick depends on whether you have enough memory to store the matrix, failing which you have to deal with slower lookups.

## E.4 Graph Terminology

When working with graphs, it is important to know the terminology being used. All the following definitions are for undirected graphs, but similar analogs exist for directed graphs as well.

![Figure E.1 An example graph](images/fig19_1.jpg)

[Figure E.1](#appE.xhtml#bfig19_1) An example graph

![Figure E.2 A complete graph](images/fig19_2.jpg)

[Figure E.2](#appE.xhtml#bfig19_2) A complete graph

![Figure E.3 A disconnected graph](images/fig19_3.jpg)

[Figure E.3](#appE.xhtml#bfig19_3) A disconnected graph

![Figure E.4 A tree](images/fig19_4.jpg)

[Figure E.4](#appE.xhtml#bfig19_4) A tree

![Figure E.5 A bipartite graph](images/fig19_5.jpg)

[Figure E.5](#appE.xhtml#bfig19_5) A bipartite graph

## E.5 Chapter Summary and Key Concepts

*   A **graph** is defined by a collection of **vertices** *V* with **edges** *E* between them.
    
*   Graphs can be represented using **adjacency lists** or **adjacency matrices**.
    
*   It is important to know graph terminology such as **neighbors, degree, complete, path, simple path, cycle, connected, tree,** and **bipartite**.
    

## Exercises

*   E.1 Give the sets *V* and *E* for the graph in [Figure E.3](#appE.xhtml#fig19_3).
    
*   E.2 Give the sets *V* and *E* for the graph in [Figure E.4](#appE.xhtml#fig19_4).
    
*   E.3 Give the sets *V* and *E* for the graph in [Figure E.5](#appE.xhtml#fig19_5).
    
*   E.4 Give the sets *V* and *E* for the graph in [Figure E.6](#appE.xhtml#fig19_6).
    
    ![Figure E.6 Exercise graph 1](images/fig19_6.jpg)
    
    [Figure E.6](#appE.xhtml#bfig19_6) Exercise graph 1
    
*   E.5 Give the sets *V* and *E* for the graph in [Figure E.7](#appE.xhtml#fig19_7).
    
    ![Figure E.7 Exercise graph 2](images/fig19_7.jpg)
    
    [Figure E.7](#appE.xhtml#bfig19_7) Exercise graph 2
    
*   E.6 Give the adjacency list representation for the graph in [Figure E.3](#appE.xhtml#fig19_3).
    
*   E.7 Give the adjacency list representation for the graph in [Figure E.4](#appE.xhtml#fig19_4).
    
*   E.8 Give the adjacency list representation for the graph in [Figure E.5](#appE.xhtml#fig19_5).
    
*   E.9 Give the adjacency list representation for the graph in [Figure E.6](#appE.xhtml#fig19_6).
    
*   E.10 Give the adjacency list representation for the graph in [Figure E.7](#appE.xhtml#fig19_7).
    
*   E.11 Give the adjacency matrix representation for the graph in [Figure E.3](#appE.xhtml#fig19_3).
    
*   E.12 Give the adjacency matrix representation for the graph in [Figure E.4](#appE.xhtml#fig19_4).
    
*   E.13 Give the adjacency matrix representation for the graph in [Figure E.5](#appE.xhtml#fig19_5).
    
*   E.14 Give the adjacency matrix representation for the graph in [Figure E.6](#appE.xhtml#fig19_6).
    
*   E.15 Give the adjacency matrix representation for the graph in [Figure E.7](#appE.xhtml#fig19_7).
    
*   E.16 List the degree of each node for the graph in [Figure E.6](#appE.xhtml#fig19_6).
    
*   E.17 List the degree of each node for the graph in [Figure E.7](#appE.xhtml#fig19_7).
    
*   E.18 A subgraph of a graph is a subset of the vertices and all the edges between them. What is the size of the largest subgraph for the graph in [Figure E.6](#appE.xhtml#fig19_6) that is a complete graph? What is the size of the largest subgraph for the graph in [Figure E.7](#appE.xhtml#fig19_7) that is a complete graph?
    
*   E.19 Find a longest cycle with only the first and last vertices repeated in the graph in [Figure E.6](#appE.xhtml#fig19_6).
    
*   E.20 Find a longest cycle with only the first and last vertices repeated in the graph in [Figure E.7](#appE.xhtml#fig19_7).
    
*   E.21 Is the graph in [Figure E.6](#appE.xhtml#fig19_6) a tree?
    
*   E.22 Is the graph in [Figure E.7](#appE.xhtml#fig19_7) a tree?
    
*   E.23 Is the graph in [Figure E.6](#appE.xhtml#fig19_6) bipartite? List out the vertices in *L* and *R* if it is.
    
*   E.24 Is the graph in [Figure E.7](#appE.xhtml#fig19_7) bipartite? List out the vertices in *L* and *R* if it is.
    

# Appendix FLoop Invariants

## F.1 Why You Should Care

When you write a function to search or sort a list, how do you know that it will work on all valid inputs? You certainly can't test it on every possible input. In computer science, we prove correctness of our algorithms. A common technique for proving correctness of algorithms with loops is the loop invariant proof. Read on to learn more!

## F.2 Summing a List

Consider the following algorithm ([Algorithm F.1](#appF.xhtml#algoF_1)) for summing up a list of numbers:

This is a very simple algorithm, but it makes a great first example to see how we can prove that it always works. To prove that the sum algorithm is correct, we introduce a loop invariant.

A loop invariant for the sum problem is given below. Note that for the rest of this chapter we will use the notation *L*\[*i* : *j*\] to indicate the sub-list consisting of *L*\[*i*\], *L*\[*i* + 1\], …, *L*\[*j* − 1\] (i.e., starting from the *i*th element up to but not including the *j*th element), similar to the notation used by Python for list slices.

We use loop invariants such as this one to essentially write a proof by induction to show correctness of the algorithm. We start with the loop initialization (similar to the base step) and then show that the invariant is maintained (similar to the inductive step) after each iteration. Unlike a proof by induction that shows the result for all positive *n*, we terminate our proof based on the termination condition of the loop.

Every loop invariant proof needs all of the above four parts: statement of the loop invariant, initialization, maintenance, and termination. We'll see some more examples next.

## F.3 Exponentiation

Consider the standard algorithm for exponentiation ([Algorithm F.2](#appF.xhtml#algoF_2)) below. It very straightforwardly just uses an accumulator to compute the exponent. Think about what would be the loop invariant in this case.

The invariant involves the *result* variable that starts at 1 and should end at *a*^(*n*). At each iteration, the value of *result* is multiplied by *a*. Guided by this, we propose the following invariant:

The rest of the proof looks as follows.

The correctness of the previous algorithm might have looked obvious to you, so let us see how we can write a proof for a more interesting exponentiation algorithm ([Algorithm F.3](#appF.xhtml#algoF_3)). It will also show us an example that has a while loop rather than a for loop.

This algorithm works similarly to the previous one, accumulating the product into an accumulator variable, except that if the exponent is even it performs the following speedup: it squares the base and halves the exponent. This considerably decreases the number of multiplications needed since we often halve the exponent, earning the algorithm the name **fast exponentiation**.

To prove correctness of the algorithm, we need to find a pattern in the values of *result, b*, and *e*. Notice that at every iteration the remaining product that needs to be multiplied into the *result* variable is *b*^(*e*). After some thought, you might get the following invariant:

For example, in the table in the previous example, you should verify that *r**e**s**u**l**t* ⋅ *b*^(*e*) is always equal to 2^(31). Notice that this invariant doesn't have an iteration number as we had in the previous for loop examples.

## F.4 Insertion Sort

The following Insertion Sort algorithm ([Algorithm F.4](#appF.xhtml#algoF_4)) sorts a list of comparable types (i.e., types that have the > operation defined). It works much in the same way that most people sort playing cards in their hands: as we encounter a card (starting from the left), we insert that card in the correct position for the cards encountered thus far. More precisely, during each iteration *i*, the algorithm inserts the *i*th element in the correct position for the sublist *L*\[0 : *i* + 1\]. At each successive iteration a larger sublist of the list is sorted. Eventually, when all the items in the list have been encountered, the entire list will be sorted.

We will formally prove the correctness of Insertion Sort next. Notice that each iteration of Insertion Sort has a larger prefix of the list sorted (indicated in bold in the above example). We will use this idea to develop the following loop invariant for it:

Note that the above proof could be made even more rigorous by adding in a separate loop invariant proof for the while loop. This is left as an excercise for the reader.

## F.5 Chapter Summary and Key Concepts

*   **Loop invariants** are statements that are true at the start of each iteration of a loop. They allow us to prove correctness of the algorithm.
    
*   Any loop invariant proof has four parts: (1) **stating** the invariant, (2) an **initialization** step in which the invariant is shown to be true at the start of the loop, (3) a **maintenance** step in which it is shown that if the invariant was true before the previous iteration then it must be true before the next iteration, and (4) a **termination** step in which the invariant is used to show that the loop correctly computed what it was suppsed to.
    

## Exercises

Write out algorithms (with **loops**) for each of the following and prove them correct using loop invariant proofs.

*   F.1 Finding the maximum of a list
    
*   F.2 Finding the minimum of a list
    
*   F.3 Summing up the first *n* positive integers
    
*   F.4 Summing up the first *n* powers of 2
    
*   F.5 Computing the factorial of *n* (1 × 2 × 3… × *n*)
    
*   F.6 Computing the *n*th Fibonacci number (iterative)
    
*   F.7 Linear search of a list
    
*   F.8 Reversing a list by creating a new list
    
*   F.9 Reversing a list in place
    
*   F.10 Selection sort (Hint: First prove a loop invariant for the inner loop, then use this to prove a loop invariant for the outer loop.)
    
*   F.11 Bubble sort (Hint: First prove a loop invariant for the inner loop, then use this to prove a loop invariant for the outer loop.)
    
*   F.12 Binary search (iterative)
    

# Appendix GRecurrence Relations

## G.1 Why You Should Care

Recurrence relations, sometimes called recurrences, are a way of analyzing recursive algorithms to compute their run-time. Since recursion, particularly divide-and-conquer, comes up quite often in algorithm design, knowing how to solve them is important for computer scientists.

## G.2 Merge Sort

Divide and conquer is a recursive algorithmic technique in which the instance of the problem being solved is broken down into two or more smaller versions of the original problem and the answer to these helps compute the answer to the original problem. An important example of this is the Merge Sort algorithm.

The Merge Sort algorithm sorts a list by splitting the list into two close-to-equal halves, sorting both halves recursively, and then merging the halves together. (Since the length of the list could be odd, one of the halves might be one larger than the other, hence the “close-to-equal.”) In the base case, when the list has length one, we don't have to do anything as a list of size one is already sorted. We won't delve into the details of the algorithm here and will instead just analyze its run-time.

Let the run-time of Merge Sort on a list of size *n* be denoted by *T*(*n*) for all *n* ≥ 1. From the above description, we can see that the running time of the entire algorithm will be the time to sort two half-sized lists and the time to merge these lists. The time to sort each half-sized list can be denoted by *T*(*n*/2) based on the definition of *T*. For simplicity, we'll assume that *n* is always a power of two to avoid complications of unequal halves. The time to merge the lists together turns out to be linear in *n* and, for simplicity, we just denote it as *cn* for some constant *c* > 0. Lastly, the base case of Merge Sort is when the list has size one, in which case we simply return the list with zero additional work done because a list of size one is already sorted. Putting all this together, we get the following definition of *T*, called a **recurrence relation** or **recurrence**:

  
$$\\begin{array}{l} {T(n) = \\left\\{ \\begin{matrix} 0 & {\\text{if~}n = 1} \\\\ {2T(n/2) + cn} & {\\text{if~}n > 1.} \\\\ \\end{matrix} \\right.} \\\\ \\end{array}$$  

We'll see next a few different ways to solve such a recurrence relation.

## G.3 Recursion Tree Method

One way to solve the above recurrence relation, called the recursion tree method, is to use the formula for *T* and expand it a few times like this:

  
$$\\begin{matrix} {T(m)} & {=} & {2T(m/2) + cm} & & {\\text{~(using\\ the\\ formula\\ for~}T\\ \\text{when~}n = m)} \\\\ & {=} & {2\\left( 2T(m/4) + cm/2 \\right) + cm} & & {\\text{~(using\\ the\\ formula\\ for~}T\\ \\text{when~}n = m/2)} \\\\ & {=} & {4T(m/4) + 2cm} & & \\text{(simplifying\\ with\\ algebra)} \\\\ & {=} & {4\\left( 2T(m/8) + cm/4 \\right) + 2cm} & & {\\text{~(using\\ the\\ formula\\ for~}T\\ \\text{when~}n = m/4)} \\\\ & {=} & {8T(m/8) + 3cm} & & \\text{(simplifying\\ with\\ algebra).} \\\\ \\end{matrix}$$  

We can continue this process a few more times to see that this seems to be following the pattern (after expanding the formula *k* times):

  
$$\\begin{array}{l} {T(m) = 2^{k}T(m/2^{k}) + kcm.} \\\\ \\end{array}$$  

We can continue the above expansion until such time as we have reduced the problem down to size one. This happens precisely when *m*/2^(*k*) = 1 or when *m* = 2^(*k*) or *k* = log[2](*m*). Substituting this value of *k* into the above formula, we get

  
$$\\begin{matrix} {T(m)} & {=} & {2^{\\log\_{2}(m)}T(m/2^{\\log\_{2}(m)}) + cm\\log\_{2}(m)} & & \\\\ & {=} & {mT(m/m) + cm\\log\_{2}(m)} & & {\\text{(as~}2^{\\log\_{2}(m)} = m)} \\\\ & {=} & {mT(1) + cm\\log\_{2}(m)} & & \\\\ & {=} & {cm\\log\_{2}(m)} & & {\\text{(as~}T(1) = 0).} \\\\ \\end{matrix}$$  

We can conclude from this derivation that the run-time of Merge Sort is then *c**m*log[2](*m*), more simply expressed (using Big-O notation, see [Appendix D](#appD.xhtml#appD)) as *O*(*n*log (*n*)).

## G.4 A Review of Some Log Rules

As you just saw in the previous section, you will need to be comfortable working with logarithms in this chapter. Here are a few rules that are worth remembering. For any *b* > 1 and *n*, *m* > 0, we have

  
$$\\begin{array}{ll} {\\log\_{b}{(1)}} & {= 0} \\\\ {\\log\_{b}{(b)}} & {= 1} \\\\ b^{\\log\_{b}{(n)}} & {= n} \\\\ {\\log\_{b}{(nm)}} & {= \\log\_{b}{(n)} + \\log\_{b}{(m)}} \\\\ {\\log\_{b}{(n/m)}} & {= \\log\_{b}{(n)} - \\log\_{b}{(m)}} \\\\ {\\log\_{b}{(n^{m})}} & {= m\\log\_{b}{(n)}.} \\\\ \\end{array}$$  

## G.5 Substitution Method

Another, simpler, way to prove the recurrence can be to use strong induction. For this method, we need to know what the formula is beforehand. We can write the following induction hypothesis and prove it inductively.

For any *n* ≥ 1,

  
$$\\begin{array}{l} {P(n):T(n) = cn\\log\_{2}(n).} \\\\ \\end{array}$$  

For the base case, we have that when *n* = 1, we know that *T*(1) = 0 and *c**n*log[2](*n*) = 0 since log[2](1) = 0. Thus *P*(1) holds.

We fix some *k* > 1 and assume that the induction hypothesis holds for all values *n* < *k*. We will show that the induction hypothesis holds for *n* = *k* as well.

When *n* = *k*, we have

  
$$\\begin{matrix} {T(k)} & {=} & {2T(k/2) + ck} & & {\\text{(by\\ the\\ definition\\ of~}T)} \\\\ & {=} & {2(c(k/2)\\log\_{2}(k/2)) + ck} & & {\\text{(by\\ the\\ induction\\ hypothesis\\ when~}n = k/2)} \\\\ & {=} & {ck\\log\_{2}(k/2) + ck} & & \\text{(simplifying\\ with\\ algebra)} \\\\ & {=} & {ck\\log\_{2}(k) - ck + ck} & & {\\text{(as~}\\log\_{2}(k/2) = \\log\_{2}(k) - \\log\_{2}{(2)} = \\log\_{2}(k) - 1)} \\\\ & {=} & {ck\\log\_{2}(k),} & & \\\\ \\end{matrix}$$  

thus proving the inductive step. We can wrap up the strong induction proof as usual.

## G.6 Analyzing the Karatsuba-Ofman Algorithm

There is another divide and conquer algorithm for multiplying large numbers called the Karatsuba-Ofman algorithm with the following recurrence:

  
$$\\begin{array}{l} {T(n) = \\left\\{ \\begin{matrix} 0 & {\\text{if~}n = 1} \\\\ {3T(n/2) + cn} & {\\text{if~}n > 1.} \\\\ \\end{matrix} \\right.} \\\\ \\end{array}$$  

We'll see how to analyze it using the above two techniques next. Using the recursion tree method, we get:

  
$$\\begin{matrix} {T(m)} & {=} & {3T(m/2) + cm} & & {\\text{~(formula\\ for~}T\\ \\text{when~}n = m)} \\\\ & {=} & {3\\left( 3T(m/4) + cm/2 \\right) + cm} & & {\\text{~(formula\\ for~}T\\ \\text{when~}n = m/2)} \\\\ & {=} & {9T(m/4) + (3/2)cm + cm} & & \\text{(simplifying\\ with\\ algebra)} \\\\ & {=} & {9\\left( 3T(m/8) + cm/4 \\right) + (3/2)cm + cm} & & {\\text{~(formula\\ for~}T\\ \\text{when~}n = m/4)} \\\\ & {=} & {27T(m/8) + (3/2)^{2}cm + (3/2)cm + cm} & & \\text{(simplifying\\ with\\ algebra).} \\\\ \\end{matrix}$$  

We can continue this procedure a few more times to see that this seems to be following the pattern (after expanding the formula *k* times):

  
$$\\begin{array}{l} {T(m) = 3^{k}T(m/2^{k}) + \\sum\\limits\_{i = 0}^{k - 1}(3/2)^{i}cm.} \\\\ \\end{array}$$  

We can continue this until we have reduced the problem down to size one. This happens precisely when *m*/2^(*k*) = 1 or when *m* = 2^(*k*) or *k* = log[2](*m*). Substituting this value of *k* into the above formula, we get

  
$$\\begin{array}{l} \\begin{matrix} {T(m)\\ } & {= 3^{\\log\_{2}(m)}T(m/2^{\\log\_{2}(m)}) + \\sum\\limits\_{i = 0}^{\\log\_{2}(m) - 1}(3/2)^{i}cm} & \\\\ \\ & {= 3^{\\log\_{2}(m)}T(m/m) + \\sum\\limits\_{i = 0}^{\\log\_{2}(m) - 1}(3/2)^{i}cm} & {\\text{(as~}2^{\\log\_{2}(m)} = m)} \\\\ \\ & {= 3^{\\log\_{2}(m)}T(1) + \\sum\\limits\_{i = 0}^{\\log\_{2}(m) - 1}(3/2)^{i}cm} & \\\\ \\ & {= \\sum\\limits\_{i = 0}^{\\log\_{2}(m) - 1}(3/2)^{i}cm} & {\\text{(as~}T(1) = 0)} \\\\ \\ & {= \\frac{\\left( 3/2 \\right)^{\\log\_{2}(m)} - 1}{3/2 - 1}cm} & \\text{(\\ formula\\ for\\ geometric\\ sum)} \\\\ \\ & {= 2cm(3^{\\log\_{2}(m)}/2^{\\log\_{2}(m)} - 1)} & \\text{(dividing\\ by\\ 1/2\\ is\\ the\\ same\\ as} \\\\ \\ & & \\text{multiplying\\ by\\ 2)} \\\\ \\ & {= 2cm(3^{\\log\_{2}(m)}/m - 1)} & {\\text{(as~}2^{\\log\_{2}(m)} = m)} \\\\ \\ & {= 2cm^{\\log\_{2}3} - 2cm} & \\text{(logarithm\\ rules).} \\\\ \\end{matrix} \\\\ \\end{array}$$  

We can conclude from this derivation that the run-time of the algorithm is thus *O*(*n*^(log[2]3)) or *O*(*n*^(1.585)).

The substitution method for this proof proceeds as follows. For any *n* ≥ 1,

  
$$\\begin{array}{l} {P(n):T(n) = 2cn^{\\log\_{2}3} - 2cn.} \\\\ \\end{array}$$  

For the base case, we have that when *n* = 1, we know that *T*(1) = 0 and 2*c**n*^(log[2]3) − 2*c**n* = 2*c* − 2*c* = 0. Thus *P*(1) holds.

We fix some *k* > 1 and assume that the induction hypothesis holds for all values *n* < *k*. We will show that the induction hypothesis holds for *n* = *k* as well.

When *n* = *k*, we have

  
$$\\begin{matrix} {T(k)} & {=} & {3T(k/2) + ck} & & {\\text{(by\\ the\\ definition\\ of~}T)} \\\\ & {=} & {3(2c(k/2)^{\\log\_{2}3} - 2ck/2) + ck} & & {\\text{(by\\ the\\ induction\\ hypothesis\\ when~}n = k/2)} \\\\ & {=} & {6ck^{\\log\_{2}3}/2^{\\log\_{2}3} - 3ck + ck} & & \\text{(algebra)} \\\\ & {=} & {2ck^{\\log\_{2}(3)} - 2ck} & & {\\text{(as~}2^{\\log\_{2}(3)} = 3),} \\\\ \\end{matrix}$$  

thus showing the inductive step. We can again wrap up the strong induction proof as usual.

## G.7 Chapter Summary and Key Concepts

*   **Recurrences** are recursive formulas, usually used to express the running time of a recursive algorithm.
    
*   The **recursion tree method** can be used to unroll a recurrence to get an exact formula for it.
    
*   The **substitution method** uses strong induction to formally prove the formula for the recurrence.
    

## Exercises

Solve the following recurrences using the recursion tree method. In each case, assume that *T*(1) = 0.

*   G.1 *T*(*n*) = 2*T*(*n*/4) + *n*
    
*   G.2 *T*(*n*) = 2*T*(*n*/2) + *n*²
    
*   G.3 *T*(*n*) = 7*T*(*n*/8) + *n*
    
*   G.4 *T*(*n*) = 3*T*(*n*/4) + *n*²
    
*   G.5 *T*(*n*) = 5*T*(*n*/8) + *n*³
    

Solve the following recurrences using the substitution method (strong induction). In each case, assume that *T*(1) = 0. (Hint: Use the recursion tree method first to get an induction hypothesis in each case.)

*   G.6 *T*(*n*) = 2*T*(*n*/4) + *n*
    
*   G.7 *T*(*n*) = 2*T*(*n*/2) + *n*²
    
*   G.8 *T*(*n*) = 7*T*(*n*/8) + *n*
    
*   G.9 *T*(*n*) = 3*T*(*n*/4) + *n*²
    
*   G.10 *T*(*n*) = 5*T*(*n*/8) + *n*³
    

# Further Reading

There are a number of books on discrete math for computer science available, see for example \[[Epp19](#refbib.xhtml#refbib2), [FK03](#refbib.xhtml#refbib3), [GKP89](#refbib.xhtml#refbib4), [LN22](#refbib.xhtml#refbib8), [LZ19](#refbib.xhtml#refbib9), [SDB10](#refbib.xhtml#refbib13)\]. However, I believe this is the first book that uses theory of computation as the way to introduce these discrete math topics.

Since this book is intended to be an introduction to the mathematical ideas in computer science first and only a light introduction to the theory of computation, there are many topics in the latter that have been very briefly discussed and others that have been omitted entirely. For those wishing to read more about these topics, I recommend some of the standard texts by Hopcroft, Motwani, Ulman \[[HMU06](#refbib.xhtml#refbib6)\], Martin \[[Mar90](#refbib.xhtml#refbib10)\], and Sipser \[[Sip96](#refbib.xhtml#refbib15)\]. For a more advanced look at the topic one could look at the Complexity Theory Companion \[[HO02](#refbib.xhtml#refbib7)\]—some of my treatment of topics was heavily influenced by what I have learned from the authors of this book.

For students looking to brush up on some of the basic computer science prerequisites in this book, I recommend the Discovering Computer Science book by Havill \[[Hav20](#refbib.xhtml#refbib5)\].

I often like to delve into the philosophy of computer science with my students. For this, I like to use the Stanford Encyclopedia of Philosophy \[[sep24](#refbib.xhtml#refbib14)\].

For more detail on the algorithmic topics, especially loop invariants and recurrences, I recommend the algorithms bible by Cormen, Leiserson, Rivest, and Stein \[[CLRS09](#refbib.xhtml#refbib1)\].

To learn more about probability in computer science, please see \[[MU05](#refbib.xhtml#refbib12)\]. The book by Motwani and Raghavan \[[MR95](#refbib.xhtml#refbib11)\] is the standard text on randomized algorithms.

# Bibliography

*   [Thomas H. Cormen](#chapter-bm.xhtml#b-bmrefbib1), Charles E. Leiserson, Ronald L. Rivest, and Clifford Stein. Introduction to Algorithms, Third Edition. The MIT Press, 3rd edition, 2009.
*     [Susanna Samuels Epp](#chapter-bm.xhtml#b-bmrefbib2). Discrete Mathematics with Applications. Cengage Learning, 5th edition, 2019.
*     [T. Feil](#chapter-bm.xhtml#b-bmrefbib3) and J. Krone. Essential Discrete Mathematics for Computer Science. Prentice Hall, 2003.
*    [Ronald L. Graham](#chapter-bm.xhtml#b-bmrefbib4), Donald E. Knuth, and Oren Patashnik. Concrete Mathematics: A Foundation for Computer Science. Addison-Wesley, 1989.
*    [Jessen Havill](#chapter-bm.xhtml#b-bmrefbib5). Discovering Computer Science: Interdisciplinary Problems, Principles, and Python Programming (Second Edition). Chapman and Hall/CRC Press, 2nd edition, 2020.
*   [J. E. Hopcroft](#chapter-bm.xhtml#b-bmrefbib6), R. Motwani, and J. D. Ullman. Introduction to Automata Theory, Languages, and Computation. Addison Wesley, 3rd edition, 2006.
*     [Lane A. Hemaspaandra](#chapter-bm.xhtml#b-bmrefbib7) and Mitsunori Ogihara. The Complexity Theory Companion. Springer-Verlag, 2002.
*     [David Liben-Nowell](#chapter-bm.xhtml#b-bmrefbib8). Connecting Discrete Mathematics and Computer Science. Cambridge University Press, 2nd edition, 2022.
*     [Harry Lewis](#chapter-bm.xhtml#b-bmrefbib9) and Rachel Zax. Essential Discrete Mathematics for Computer Science. Princeton University Press, 2019.
*    [John C. Martin](#chapter-bm.xhtml#b-bmrefbib10). Introduction to Languages and the Theory of Computation. McGraw-Hill, Inc., USA, 1st edition, 1990.
*    [Rajeev Motwani](#chapter-bm.xhtml#b-bmrefbib11) and Prabhakar Raghavan. Randomized Algorithms. Cambridge University Press, 1995.
*    [Michael Mitzenmacher](#chapter-bm.xhtml#b-bmrefbib12) and Eli Upfal. Probability and Computing: Randomized Algorithms and Probabilistic Analysis. Cambridge University Press, 2005.
*    [Cliff Stein](#chapter-bm.xhtml#b-bmrefbib13), Robert Drysdale, and Kenneth Bogart. Discrete Mathematics for Computer Scientists. Addison-Wesley Publishing Company, 2010.
*     [Stanford](#chapter-bm.xhtml#b-bmrefbib14) Encyclopedia of Philosophy. [https://plato.stanford.edu](https://plato.stanford.edu), 2024.
*     [Michael Sipser](#chapter-bm.xhtml#b-bmrefbib15). Introduction to the Theory of Computation. International Thomson Publishing, 1st edition, 1996.

# Index

*   *λ*\-transition, [56](#chapter4.xhtml#p56)

*   adjacency list, [188](#appE.xhtml#p188)
*   adjacency matrix, [189](#appE.xhtml#p189)
*   Alan Turing, [163](#chapter14.xhtml#p163)
*   alphabet, [13](#chapter1.xhtml#p13)
*   asymptotic notation, [181](#appD.xhtml#p181)

*   base step, [88](#chapter8.xhtml#p88)
*   biconditional, [40](#chapter3.xhtml#p40)
*   Big-O notation, [41](#chapter3.xhtml#p41), [182](#appD.xhtml#p182)
*   Big-Omega (Ω) notation, [183](#appD.xhtml#p183)
*   binary, [30](#chapter2.xhtml#p30), [166](#appA.xhtml#p166)
*   Binary Search algorithm, [102](#chapter8.xhtml#p102), [201](#appF.xhtml#p201)
*   bipartite graph, [191](#appE.xhtml#p191)
*   Bubble Sort algorithm, [201](#appF.xhtml#p201)

*   Cantor, [119](#chapter10.xhtml#p119)
*   cardinality, [3](#chapter1.xhtml#p3)
*   Cartesian product, [10](#chapter1.xhtml#p10)
*   Church-Turing thesis, [152](#chapter14.xhtml#p152)
*   class (of languages), [161](#chapter14.xhtml#p161)
*   closure properties, [82](#chapter7.xhtml#p82), [134](#chapter12.xhtml#p134)
*   codomain, [12](#chapter1.xhtml#p12)
*   codon, [27](#chapter2.xhtml#p27)
*   complement, [6](#chapter1.xhtml#p6)
*   complete graph, [190](#appE.xhtml#p190)
*   computable, [154](#chapter14.xhtml#p154)
*   computational biology, [27](#chapter2.xhtml#p27)
*   concatenation, [13](#chapter1.xhtml#p13)
*   conditional, [38](#chapter3.xhtml#p38)
*   congruence, [177](#appC.xhtml#p177)
*   connected, [190](#appE.xhtml#p190)
*   context-free grammar, [130](#chapter12.xhtml#p130), [133](#chapter12.xhtml#p133)
*   context-free language, [134](#chapter12.xhtml#p134)
*   contradiction, [117](#chapter10.xhtml#p117)
*   contrapositive, [39](#chapter3.xhtml#p39)
*   converse, [39](#chapter3.xhtml#p39)
*   cycle, [190](#appE.xhtml#p190)

*   De Morgan's Laws, [6](#chapter1.xhtml#p6), [37](#chapter3.xhtml#p37)
*   decidable, [154](#chapter14.xhtml#p154)
*   decimal, [30](#chapter2.xhtml#p30)
*   definition, [77](#chapter7.xhtml#p77)
*   degree, [190](#appE.xhtml#p190)
*   deterministic finite automaton, [23](#chapter2.xhtml#p23)
*   DFA, [23](#chapter2.xhtml#p23)
*   Diagonal Problem *D*, [155](#chapter14.xhtml#p155)
*   diagonalization, [119](#chapter10.xhtml#p119), [156](#chapter14.xhtml#p156)
*   direct proof, [77](#chapter7.xhtml#p77)
*   divisible, [30](#chapter2.xhtml#p30), [177](#appC.xhtml#p177)
*   division algorithm, [177](#appC.xhtml#p177)
*   divisor, [177](#appC.xhtml#p177)
*   domain, [12](#chapter1.xhtml#p12)

*   edge, [187](#appE.xhtml#p187)
*   element (of a set), [2](#chapter1.xhtml#p2)
*   empty set, [2](#chapter1.xhtml#p2)
*   empty string, [13](#chapter1.xhtml#p13)
*   Euclid's algorithm, [179](#appC.xhtml#p179)
*   even, [77](#chapter7.xhtml#p77)
*   event, [171](#appB.xhtml#p171) 
    *   complement, [171](#appB.xhtml#p171)
    *   independent, [172](#appB.xhtml#p172)
    *   mutually exclusive, [172](#appB.xhtml#p172)
*   exponentiation algorithm, [196](#appF.xhtml#p196)

*   factor, [177](#appC.xhtml#p177)
*   factorial, [87](#chapter8.xhtml#p87), [167](#appA.xhtml#p167), [201](#appF.xhtml#p201)
*   fast exponentiation, [197](#appF.xhtml#p197)
*   Fibonacci numbers, [97](#chapter8.xhtml#p97), [201](#appF.xhtml#p201)
*   floor division, [176](#appC.xhtml#p176)
*   function, [12](#chapter1.xhtml#p12) 
    *   codomain, [12](#chapter1.xhtml#p12)
    *   domain, [12](#chapter1.xhtml#p12)
*   fundamental theorem of arithmetic, [118](#chapter10.xhtml#p118)

*   grammar, [130](#chapter12.xhtml#p130), [133](#chapter12.xhtml#p133)
*   graph, [187](#appE.xhtml#p187) 
    *   bipartite, [191](#appE.xhtml#p191)
    *   complete, [190](#appE.xhtml#p190)
    *   connected, [190](#appE.xhtml#p190)
    *   directed, [188](#appE.xhtml#p188)
    *   undirected, [188](#appE.xhtml#p188)
*   greatest common divisor (gcd), [178](#appC.xhtml#p178)

*   Halting Problem, [160](#chapter14.xhtml#p160)
*   HTML, [60](#chapter5.xhtml#p60)

*   iff, [80](#chapter7.xhtml#p80)
*   independent, [172](#appB.xhtml#p172)
*   induction, [88](#chapter8.xhtml#p88) 
    *   mutual, [108](#chapter9.xhtml#p108)
    *   strong, [97](#chapter8.xhtml#p97)
*   induction hypothesis, [88](#chapter8.xhtml#p88)
*   inductive step, [88](#chapter8.xhtml#p88)
*   Insertion Sort algorithm, [198](#appF.xhtml#p198)
*   integers, [3](#chapter1.xhtml#p3)
*   intersection, [5](#chapter1.xhtml#p5)
*   IP address, [166](#appA.xhtml#p166)
*   irrational, [118](#chapter10.xhtml#p118)

*   Karatsuba-Ofman algorithm, [204](#appG.xhtml#p204)
*   Kleene star, [61](#chapter5.xhtml#p61)

*   language, [14](#chapter1.xhtml#p14) 
    *   class, [161](#chapter14.xhtml#p161)
    *   context-free, [134](#chapter12.xhtml#p134)
    *   recursive, [154](#chapter14.xhtml#p154)
    *   recursively enumerable, [154](#chapter14.xhtml#p154)
    *   regular, [56](#chapter4.xhtml#p56)
    *   reverse, [84](#chapter7.xhtml#p84)
*   least common multiple (lcm), [178](#appC.xhtml#p178)
*   Linear search algorithm, [201](#appF.xhtml#p201)
*   Little-o notation, [183](#appD.xhtml#p183)
*   Little-omega (*ω*) notation, [183](#appD.xhtml#p183)
*   logarithm, [203](#appG.xhtml#p203)
*   logic 
    *   and, [35](#chapter3.xhtml#p35)
    *   negation, [36](#chapter3.xhtml#p36)
    *   or, [35](#chapter3.xhtml#p35)
    *   variable, [36](#chapter3.xhtml#p36)
*   logical statement, [34](#chapter3.xhtml#p34)
*   logically equivalent, [37](#chapter3.xhtml#p37)
*   loop invariant, [194](#appF.xhtml#p194)

*   Merge Sort algorithm, [202](#appG.xhtml#p202)
*   mod, [177](#appC.xhtml#p177)
*   multiple, [177](#appC.xhtml#p177)
*   multiplication rule, [165](#appA.xhtml#p165)
*   mutually exclusive, [172](#appB.xhtml#p172)

*   natural language, [136](#chapter12.xhtml#p136)
*   natural numbers, [3](#chapter1.xhtml#p3)
*   negation, [36](#chapter3.xhtml#p36), [42](#chapter3.xhtml#p42)
*   neighbor, [189](#appE.xhtml#p189)
*   NFA, [48](#chapter4.xhtml#p48)
*   node, [187](#appE.xhtml#p187)
*   nondeterminism, [49](#chapter4.xhtml#p49)
*   nondeterministic finite automaton, [48](#chapter4.xhtml#p48)
*   nor, [86](#chapter7.xhtml#p86)
*   nucleotide, [27](#chapter2.xhtml#p27)

*   odd, [78](#chapter7.xhtml#p78)

*   pair, [10](#chapter1.xhtml#p10)
*   palindrome, [131](#chapter12.xhtml#p131)
*   parity, [79](#chapter7.xhtml#p79)
*   password, [166](#appA.xhtml#p166)
*   path, [190](#appE.xhtml#p190) 
    *   simple, [190](#appE.xhtml#p190)
*   pigeonhole principle, [122](#chapter11.xhtml#p122)
*   playing cards, [167](#appA.xhtml#p167), [173](#appB.xhtml#p173)
*   power set, [9](#chapter1.xhtml#p9)
*   predicate, [35](#chapter3.xhtml#p35)
*   prefix, [13](#chapter1.xhtml#p13)
*   prime number, [119](#chapter10.xhtml#p119)
*   probability, [170](#appB.xhtml#p170)
*   production, [130](#chapter12.xhtml#p130)
*   programming language, [135](#chapter12.xhtml#p135)
*   proof, [77](#chapter7.xhtml#p77) 
    *   by contradiction, [117](#chapter10.xhtml#p117)
*   proper subset, [3](#chapter1.xhtml#p3)
*   pumping lemma, [123](#chapter11.xhtml#p123)

*   quantifier 
    *   existential ∃ (there exists), [40](#chapter3.xhtml#p40)
    *   universal ∀ (for all), [40](#chapter3.xhtml#p40)
*   quotient, [176](#appC.xhtml#p176)

*   rational, [117](#chapter10.xhtml#p117)
*   rational numbers, [4](#chapter1.xhtml#p4)
*   real numbers, [3](#chapter1.xhtml#p3)
*   recurrence, [202](#appG.xhtml#p202)
*   recurrence relation, [202](#appG.xhtml#p202)
*   recursion, [87](#chapter8.xhtml#p87)
*   Recursion Tree method, [203](#appG.xhtml#p203)
*   recursive, [154](#chapter14.xhtml#p154)
*   recursively enumerable, [154](#chapter14.xhtml#p154)
*   reduction, [157](#chapter14.xhtml#p157), [159](#chapter14.xhtml#p159)
*   regular expression, [60](#chapter5.xhtml#p60), [62](#chapter5.xhtml#p62), [99](#chapter8.xhtml#p99) 
    *   concatenation, [61](#chapter5.xhtml#p61)
    *   in Python, [63](#chapter5.xhtml#p63)
    *   Kleene star, [61](#chapter5.xhtml#p61)
    *   Linux commands, [63](#chapter5.xhtml#p63)
    *   union, [61](#chapter5.xhtml#p61)
*   regular language, [56](#chapter4.xhtml#p56), [75](#chapter6.xhtml#p75)
*   remainder, [176](#appC.xhtml#p176)

*   sample space, [170](#appB.xhtml#p170)
*   Selection Sort algorithm, [201](#appF.xhtml#p201)
*   set, [1](#chapter1.xhtml#p1) 
    *   cardinality, [3](#chapter1.xhtml#p3)
    *   complement, [6](#chapter1.xhtml#p6)
    *   difference, [5](#chapter1.xhtml#p5)
    *   element, [2](#chapter1.xhtml#p2)
    *   equality, [3](#chapter1.xhtml#p3)
    *   finite, [3](#chapter1.xhtml#p3)
    *   infinite, [3](#chapter1.xhtml#p3)
    *   intersection, [5](#chapter1.xhtml#p5)
    *   member, [2](#chapter1.xhtml#p2)
    *   of integers, [3](#chapter1.xhtml#p3)
    *   of natural numbers, [3](#chapter1.xhtml#p3)
    *   of rational numbers, [4](#chapter1.xhtml#p4)
    *   of real numbers, [3](#chapter1.xhtml#p3)
    *   power, [9](#chapter1.xhtml#p9)
    *   proper subset, [3](#chapter1.xhtml#p3)
    *   set-builder notation, [4](#chapter1.xhtml#p4)
    *   subset, [2](#chapter1.xhtml#p2)
    *   union, [5](#chapter1.xhtml#p5)
    *   universal, [6](#chapter1.xhtml#p6)
*   set-builder notation, [4](#chapter1.xhtml#p4)
*   shortlex ordering, [14](#chapter1.xhtml#p14)
*   sorting, [90](#chapter8.xhtml#p90)
*   state, [24](#chapter2.xhtml#p24) 
    *   accepting state, [24](#chapter2.xhtml#p24)
    *   sink state, [26](#chapter2.xhtml#p26)
    *   start state, [24](#chapter2.xhtml#p24)
    *   transition, [24](#chapter2.xhtml#p24)
*   State Elimination algorithm, [72](#chapter6.xhtml#p72)
*   string, [13](#chapter1.xhtml#p13) 
    *   alphabet, [13](#chapter1.xhtml#p13)
    *   empty, [13](#chapter1.xhtml#p13)
    *   length, [13](#chapter1.xhtml#p13)
    *   prefix, [13](#chapter1.xhtml#p13)
    *   reverse, [84](#chapter7.xhtml#p84)
    *   shorthand, [13](#chapter1.xhtml#p13)
    *   shortlex ordering, [14](#chapter1.xhtml#p14)
    *   suffix, [14](#chapter1.xhtml#p14)
*   strong induction, [97](#chapter8.xhtml#p97)
*   subset, [2](#chapter1.xhtml#p2)
*   Subset Construction algorithm, [53](#chapter4.xhtml#p53)
*   Substitution method, [204](#appG.xhtml#p204)
*   substring, [13](#chapter1.xhtml#p13)
*   suffix, [14](#chapter1.xhtml#p14)
*   sum algorithm, [194](#appF.xhtml#p194)
*   symmetric difference, [86](#chapter7.xhtml#p86)

*   text editor, [63](#chapter5.xhtml#p63)
*   Theta (Θ) notation, [182](#appD.xhtml#p182)
*   tree, [191](#appE.xhtml#p191)
*   triple, [10](#chapter1.xhtml#p10)
*   truth table, [36](#chapter3.xhtml#p36)
*   tuple, [10](#chapter1.xhtml#p10)
*   Turing award, [60](#chapter5.xhtml#p60)
*   Turing machine, [139](#chapter13.xhtml#p139) 
    *   multi-tape, [151](#chapter14.xhtml#p151)
    *   multi-track, [151](#chapter14.xhtml#p151)
    *   Universal, [153](#chapter14.xhtml#p153)

*   unary, [143](#chapter13.xhtml#p143)
*   Uniform Resource Locator (URL), [60](#chapter5.xhtml#p60)
*   union, [5](#chapter1.xhtml#p5)
*   universal set, [6](#chapter1.xhtml#p6)
*   Universal Turing machine, [153](#chapter14.xhtml#p153)

*   Venn diagram, [6](#chapter1.xhtml#p6)
*   vertex, [187](#appE.xhtml#p187) 
    *   degree, [190](#appE.xhtml#p190)
    *   neighbor, [189](#appE.xhtml#p189)