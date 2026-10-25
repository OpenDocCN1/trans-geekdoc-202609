
## Sequence Multiplication

The multiplication over a sequence is denoted as the uppercase Greek letter pi (Π). It is specified in the same way as the sequence summation with the beginning and end of the operation below and above the letter respectively.

![](img/aa6336b23f772f63e5bedc91bdf02fe6_206_0.png)

This is the product of the sequence a starting at element 1 to element n.

## D.6 Set Notation

A set is a group of unique items. We may see set notation used when defining terms in machine learning.

### D.6.1 Set of Numbers

A common set you may see is a set of numbers, such as a term defined as being within the set of integers or the set of real numbers. Some common sets of numbers you may see include:

- Set of all natural numbers: ℕ
- Set of all integers: ℤ
- Set of all real numbers: ℝ

There are other sets, see Special sets on Wikipedia². We often talk about real-values or real numbers when defining terms rather than floating point values, which are really discrete creations for operations in computers.

### D.6.2 Set Membership

It is common to see set membership in definitions of terms. Set membership is denoted as a symbol that looks like an uppercase “E” (∈).

![](img/aa6336b23f772f63e5bedc91bdf02fe6_206_1.png)

Which means a is defined as being a member of the set ℝ or the set of real numbers. There is also a host of set operations, two common set operations include:

- Union, or aggregation: \(A \cup B\)
- Intersection, or overlap: \(A \cap B\)

Learn more about sets on Wikipedia³.

²https://en.wikipedia.org/wiki/Set_(mathematics)#Special_sets
³https://en.wikipedia.org/wiki/Set_(mathematics)

## D.7 Other Notation

There is other notation that you may come across. I try to lay some of it out in this section. It is common to define a method in the abstract and then define it again as a specific implementation with separate notation. For example, if we are estimating a variable x we may represent it using a notation that modifies the x, for example:

- x-bar (x̄)
- x-prime (x̊)
- x-hat (x̂)
- x-tilde (x̃)

The same notation may have different meaning in a different context, such as use on different objects or sub-fields of mathematics. For example, a common point of confusion is |x|, which, depending on context can mean:

- |x|: The absolute or positive value of x.
- |x|: The length of the vector x.
- |x|: The cardinality of the set x.

This tutorial only covered the basics of mathematical notation. There are some subfields of mathematics that are more relevant to machine learning and should be reviewed in more detail. They are:

- Linear Algebra.
- Statistics.
- Probability.
- Calculus.

And perhaps a little bit of multivariate analysis and information theory.

## D.8 Tips for Getting More Help

This section lists some tips that you can use when you are struggling with mathematical notation in machine learning.

### D.8.1 Think About the Author

People wrote the paper or book you are reading. People that can make mistakes, make omissions, and even make things confusing because they don't fully understand what they are writing. Relax the constraints of the notation you are reading slightly and think about the intent of the author. What are they trying to get across? Perhaps you can even contact the author via email, Twitter, Facebook, Linked-in, etc, and seek clarification. Remember that academics want other people to understand and use their work (mostly).

### D.8.2 Check Wikipedia

Wikipedia has lists of notation which can help narrow down on the meaning or intent of the notation you are reading. Two places I recommend you start are:

- List of mathematical symbols on Wikipedia.
  https://en.wikipedia.org/wiki/List_of_mathematical_symbols

- Greek letters used in mathematics, science, and engineering on Wikipedia.
  https://en.wikipedia.org/wiki/Greek_letters_used_in_mathematics,_science,_and_engineering

### D.8.3 Sketch in Code

Mathematical operations are just functions on data. Map everything you’re reading to pseudocode with variables, for-loops and more. You might want to use a scripting language as you go along with small arrays of contrived data or even an Excel spreadsheet. As your reading and understanding of the technique improves, your code-sketch of the technique will make more sense and at the end you will have a mini prototype to play with.

I never used to take much stock in this approach until I saw an academic sketch out a very complex paper in a few lines of Matlab with some contrived data. It knocked my socks off because I believed the system had to be coded completely and run with a real dataset and that the only option was to get the original code and data. I was very wrong. Also, looking back, the guy was gifted. I now use this method all the time and sketch techniques in Python.

### D.8.4 Seek Alternatives

There is a trick I use when I’m trying to understand a new technique. I find and read all the papers that reference the paper I’m reading with the new technique. Reading other academics interpretation and re-explanation of the technique can often clarify my misunderstandings in the original description. Not always though. Sometimes it can muddy the waters and introduce misleading explanations or new notation. But more often than not, it helps. After circling back to the original paper and re-reading it, I can often find cases where subsequent papers have actually made errors and misinterpretations of the original method.

### D.8.5 Post a Question

There are places online where people love to explain math to others. Seriously! Consider taking a screen shot of the notation you are struggling with, write out the full reference or link to it and put it and your area of misunderstanding to a question and answer site. Two great places to start are:

- Mathematics Stack Exchange.
  https://math.stackexchange.com/

- Cross Validated.
  https://stats.stackexchange.com/

## D.9 Further Reading

This section provides more resources on the topic if you are looking to go deeper.

- Section 0.1. Reading Mathematics, Vector Calculus, Linear Algebra, and Differential Forms, 2009. http://amzn.to/2qarp8L

- The Language and Grammar of Mathematics, Timothy Gowers. http://assets.press.princeton.edu/chapters/gowers/gowers_I_2.pdf

- Understanding Mathematics, a guide, Peter Alfeld. http://www.math.utah.edu/~pa/math.html

## D.10 Summary

In this tutorial, you discovered the basics of mathematical notation that you may come across when reading descriptions of techniques in machine learning. Specifically, you learned:

- Notation for arithmetic including variations of multiplication, exponents, roots and logarithms.

- Notation for sequences and sets including indexing, summation and set membership.

- 5 Techniques you can use to get help if you are struggling with mathematical notation.

## Part VIII

## Conclusions

## How Far You Have Come

You made it. Well done. Take a moment and look back at how far you have come. You now know:

- What linear algebra is and why it is relevant and important to machine learning.
- How to create, index, and generally manipulate data in NumPy arrays.
- What a vector is and how to perform vector arithmetic and calculate vector norms.
- What a matrix is and how to perform matrix arithmetic, including matrix multiplication.
- A suite of types of matrices, their properties, and advanced operations involving matrices.
- What a tensor is and how to perform basic tensor arithmetic.
- Matrix factorization methods, including the eigendecomposition and singular-value decomposition.
- How to calculate and interpret basic statistics using the tools of linear algebra.
- How to implement methods using the tools of linear algebra, such as principal component analysis and linear least squares regression.

Don’t make light of this. You have come a long way in a short amount of time. You have developed the important and valuable foundational skills in linear algebra. You can now confidently:

- Read the linear algebra mathematics in machine learning papers.
- Implement the linear algebra descriptions of machine learning algorithms.
- Describe your machine learning models using the notation and operations of linear algebra.

The sky’s the limit.

## Thank You!

I want to take a moment and sincerely thank you for letting me help you start your linear algebra journey. I hope you keep learning and have fun as you continue to master machine learning.

Jason Brownlee 2018
