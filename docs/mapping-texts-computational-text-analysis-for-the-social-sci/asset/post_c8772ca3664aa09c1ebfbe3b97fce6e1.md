
2 As are common file formats like XML, HTML, CSV, and TXT files.

## Figure 3.1: The RStudio IDE.

These languages are written in plain text and we call the resulting files "scripts."

![](img/ccc0ce559da97114ef913045f55e3801_29_0.png)

3 Microsoft Word is a word processor, while Notepad is a plain-text editor and Mac's TextEdit has the option to be a plain-text editor.

In addition to RStudio, popular IDEs include VS Code, VSCodium, Sublime, Vim, Emacs, and Notepad++.

4 There are differences, but console, terminal, shell, and command line are often used as synonyms.

5 RStudio Cloud is an online IDE at posit.cloud. We can use RStudio Cloud for nearly all examples in this book. Some examples in the Extended chapters require more computational resources than the free plan offers.

We write our scripts in plain text to organize it. To "run" the script, though, we need to "send" it to a program that can "interpret" its conventions and produce the desired output. In our case, this program is R. We could do this directly from a console. For this book, though, we'll assume you're using an Integrated Development Environment (IDE), a beefy plain-text editor.

RStudio (Figure 3.1) is a dedicated R IDE with many point-and-click features that make our life easier (Team 2020). The free and open-source version of RStudio is sufficient for most.

IDEs, like RStudio, include a script editor and a visual directory (respectively, left top and right bottom panels in Figure 3.1). Our scripts and data files are in these directories. We must "tell" R where those files are. Directory errors are common; unintentional typos are often the culprits. Finally, IDEs will include a console. We send code from the editor to the console to "run" it and the "output" of that code appears in real-time (bottom left in Figure 3.1). We can also see any "objects" we've created during that R session in our environment (top right in Figure 3.1).

If new to R, we suggest using a free RStudio Cloud account. For each section in this book, create a new session in R and open a new R script. Any packages required will be in a margin note with the heading "This Section Needs" and should be loaded at the top of the script. Then, copy each subsequent "code chunk" into this script. Finally, run this code to see the output in the console. A few general reminders (that will make more sense as we go):

- Run the code in the order it appears in each section.
- Creating new objects will overwrite objects of the same name.
- Object names should be short but descriptive.⁶
- Be sure to close any parentheses, brackets, and quotes.⁷

## Data Objects, Types, and Structures

Data structures are how we organize our data. In R, these include **vectors**, **lists**, **matrices**, and **dataframes** (Table 3.1). Vectors and lists are similar because they are _flat_ (think of a grocery list, a record of cattle weights, or a tally of coin flips). Matrices and dataframes, on the other hand, are squares with rows and columns (e.g., Excel spreadsheets or gradebooks).

## Table 3.1: Basic Data Structures

| Structure | Different Types? | Rows and Columns? |
|---|---|---|
| Vector | NO | NO |
| List | YES | NO |
| Matrix | NO | YES |
| Dataframe | YES | YES |

Typically, we’ll use “dimensions” to refer to how many rows or columns dataframes and matrices have, or the length of vectors and lists.

With vectors and matrices, all the elements must be the same _type_. Lists and dataframes, however, can be collections of different _types_ of elements. Types tell R what can be done with the objects—it sets expectations. There are four basic types, from most to least encompassing: character, numeric or double, 8 integer, logical (see Table 3.2). R automatically picks the type that can encompass all the elements in a vector. Here are some quick examples (outputs in the margin). We’ll “combine” elements with c() to create vectors.

Naming in R is case sensitive, and lowercase words with underscores between them (i.e. snake case) is preferred. Typically, we’ll want to avoid single-character names because they are hard to search for and can make debugging tricky.

If these are not closed, the R console will show a new line with a +, waiting for the remaining code. Typing CTRL+C or CMD+C will end the run and so we can fix the code.

```
words <- c("space", "is", "big")
typeof(words)
```

```
nums <- c(1.2, 2.8, 2)
typeof(nums)
```

[1] "character"

[1] "double"

R calls these “double” because of “double-precision floating-point vector.”

Notice the `L` in the code below. This forces `R` to treat a number as `integer` rather than a `double`.

```r
ints <- c(1L, 3L, 2L)
typeof(ints)
```

[1] "integer"

```r
lgcl <- c(TRUE, FALSE, TRUE, TRUE)
typeof(lgcl)
```

[1] "logical"

## Table 3.2: Basic Data Types

| Type | Words/Punctuation | Decimals | Integers |
|---|---|---|---|
| character | YES | YES | YES |
| numeric or double | NO | YES | YES |
| integer | NO | NO | YES |
| logical | NO | NO | NO |

The above are the basic building blocks of `R` objects. We can combine them to create a `class`. Like type, this sets `R`’s expectations for the object. The simplest class is a `factor`, which combines `character` and `numeric` types by pairing labels to levels.9

9 Factors are often used for ordinal variables (e.g., “Disagree” to “Agree”). They also force labels into a specific order, which is handy when visualizing.

```r
levels <- c("Okay Idea", "Good Idea", "Bad Idea", "Good Idea")
levels <- c("Bad Idea", "Okay Idea", "Good Idea", "Good Idea")
fac <- factor(labels, levels)
```

```r
typeof(fac)
class(fac)
```

[1] "integer" [1] "factor"

Matrices are also a class. The `c()` function combines elements into a vector, and `cbind()` “column binds” the vectors. The result is a matrix class object.10

10 Arrays include our two-sided matrix, but also objects with more than two sides—like a cube or tesseract. These show up once in this book.

```r
c1 <- c(1.2, 2.8, 3)
c2 <- c(0, 4, 2)
mat <- cbind(c1, c2)
```

```
 c1 c2
[1,] 1.2 0
[2,] 2.8 4
[3,] 3.0 2
```

The `typeof` is a “double” because it is the type that can represent both whole numbers and decimals.

```r
class(mat)
typeof(mat)
```

[1] "matrix" "array" [1] "double"

Finally, highlight the object name (`mat`) and click “run” or type CTRL + ENTER or CMD + ENTER. It will print the contents of the object to the console (output in margin).

```
mat
```

Below `cbind()` creates `matrix`, but now it's `character` as that is the type encompassing both numbers and words (output in margin).

```
d4 <- c(0, 4, 2)
d5 <- c("space", "is", "big")
mat2 <- cbind(d4, d5)
typeof(mat2)
```

[1] "character"

We can tell because double quotes surround each element. When we use `data.frame()`, though, one column is `numeric`, and the other is `character`, creating an object of class `data.frame`. Technically, a `data.frame` is a set of (vertical) lists of the same length. Each list retains its data type.

```
cbind(mat2)
```

```
data.frame(d4, d5)
```

```
   d4 d5
[1,] "0" "space"
[2,] "4" "is"
[3,] "2" "big"
```

```
  d4  d5
1  0 space
2  4 is
3  2 big
```

To help us navigate these objects, whenever we have a `named` list or dataframe, we can use the `$` operator to call that element by name. Let's create a list

```
lrrs_list <- list(first = "fireman",
                  second = "math teachers",
                  third = "and so on in that fashion")
names(lrrs_list)
```

[1] "first" "second" "third"

To access the element named `third`, we would:

```
lrrs_list$third
```

[1] "and so on in that fashion"

Most data structures we encounter are variations on the above. Specifically, objects can be within other objects: for example, a list where the elements are lists (or even lists of lists of lists, and so on in that fashion).

### Dialects of R

There are two `dialects` of `R` which we label *nesting* and *chaining*.11

- Nesting: An object is transformed by an inner function, then sent to the next outward function.
- Chaining: An object is transformed by a function, then sent to the next right function.
