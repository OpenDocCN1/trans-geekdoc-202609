
this special value.

Our experimentation suggests two insights. First, we are **not** looking for a data definition that describes how to generate instances of child structures but for a data definition that describes how to represent family trees. Second, the data definition consists of two clauses, one for the variant describing unknown family trees and another one for known family trees:

```
(define-struct no-parent [])
(define-struct child [father mother name date eyes])
; An FT (short for *family tree*) is one of:
; -- (make-no-parent)
; -- (make-child FT FT String N String)
```

Since the “no parent” tree is going to show up a lot in our programs, we define NP as a short-hand and revise the data definition a bit:

```
(define NP (make-no-parent))
; An FT is one of:
; -- NP ;
; -- (make-child FT FT String N String)
```

Following the design recipe from chapter 9, we use the data definition to create examples of family trees. Specifically, we translate the family tree in figure 111 into our data representation. The information for Carl is easy to translate into data:

```
(make-child NP NP "Carl" 1926 "green")
```

Bettina and Fred are represented with similar instances of child. The case for Adam calls for nested children, one for Carl and one for Bettina:

```
(make-child (make-child NP NP "Carl" 1926 "green")
                (make-child NP NP "Bettina" 1926 "green")
                "Adam"
                1950
                "hazel")
```

Since the records for Carl and Bettina are also needed to construct the records for Dave and Eva, it is better to introduce definitions that name specific instances of child and to use the variable names elsewhere. Figure 112 illustrates this approach for the complete data representation of the family tree from figure 111. Take a close look; the tree serves as our running example for the following design exercise.

```
; Oldest Generation:
(define Carl (make-child NP NP "Carl" 1926 "green"))
(define Bettina (make-child NP NP "Bettina" 1926 "green"))

; Middle Generation:
(define Adam (make-child Carl Bettina "Adam" 1950 "hazel"))
(define Dave (make-child Carl Bettina "Dave" 1955 "black"))
(define Eva (make-child Carl Bettina "Eva" 1965 "blue"))
(define Fred (make-child NP NP "Fred" 1966 "pink"))

; Youngest Generation:
(define Gustav (make-child Fred Eva "Gustav" 1988 "brown"))
```

Figure 112: A data representation of the sample family tree

Instead of designing a concrete function on family trees, let's first look at the generic organization of such a function. That is, let's work through the design recipe as much as possible without having a concrete task in mind. We start with the header material, that is, step 2 of the recipe:

```
; FT -> ???
; ...
(define (fun-FT an-ftree) ...)
```

Even though we aren't stating the purpose of the function, we do know that it consumes a family tree and that this form of data is the main input. The “???” in the signature says that we don't know what kind of data the function produces; the “...” remind us that we don't know its purpose.

The lack of purpose means we cannot make up functional examples. Nevertheless, we can exploit the organization of the data definition for FT to design a template. Since it consists of two clauses, the template must consist of a cond expression with two clauses:

```
(define (fun-FT an-ftree)
(cond
[(no-parent? an-ftree) ...]
[else ...]))
```

In case the argument to fun-FT satisfies no-parent?, the structure contains no additional data, so the first clause is complete. For the second clause, the input contains five pieces of data, which we indicate with five selectors in the template:

```
; FT -> ???
(define (fun-FT an-ftree)
(cond
[(no-parent? an-ftree) ...]
[else (... (child-father an-ftree) ...
... (child-mother an-ftree) ...
... (child-name an-ftree) ...
... (child-date an-ftree) ...
... (child-eyes an-ftree) ...)]))
```

The last addition to templates concerns self-references. If a data definition refers to itself, the function is likely to recur and templates indicate so with suggestive natural recursions. The definition for FT has two self-references, and the template therefore needs two such recursions:

```
; FT -> ???
(define (fun-FT an-ftree)
(cond
[(no-parent? an-ftree) ...]
[else (... (fun-FT (child-father an-ftree)) ...
... (fun-FT (child-mother an-ftree)) ...
... (child-name an-ftree) ...
... (child-date an-ftree) ...
... (child-eyes an-ftree) ...)]))
```

Specifically, fun-FT is applied to the data representation for fathers and mothers in the second cond clause because the second clause of the data definition contains corresponding self-references.

Let’s now turn to a concrete example, the blue-eyed-child? function. Its purpose is to determine whether any child structure in a given family tree has blue eyes. You may copy, paste, and rename fun-FT to get its template; we replace “???” with Boolean and add a purpose statement:

```
; FT -> Boolean
; does an-ftree contain a child
; structure with "blue" in the eyes field
(define (blue-eyed-child? an-ftree)
  (cond
    [(no-parent? an-ftree) ...]
    [else (... (blue-eyed-child?
                 (child-father an-ftree)) ...
                 ... (blue-eyed-child?
                     (child-mother an-ftree)) ...
                 ... (child-name an-ftree) ...
                 ... (child-date an-ftree) ...
                 ... (child-eyes an-ftree) ...)]))
```

When you work in this fashion, you must replace the template’s generic name with a specific one.

Checking with our recipe, we realize that we need to backtrack and develop some examples before we move on to the definition step. If we start with Carl, the first person in the family tree, we see that Carl’s family tree does not contain a child with a "blue" eye color. Specifically, the child representing Carl says the eye color is "green"; given that Carl’s ancestor trees are empty, they cannot possibly contain a child with "blue" eye color:

```
(check-expect (blue-eyed-child? Carl) #false)
```

In contrast, Gustav contains a child for Eva who does have blue eyes:

```
(check-expect (blue-eyed-child? Gustav) #true)
```

Now we are ready to define the actual function. The function distinguishes between two cases: a no-parent and a child. For the first case, the answer should be obvious even though we haven’t made up any examples. Since the given family tree does not contain any child whatsoever, it cannot contain one with "blue" as the eye color. Hence the result in the first cond clause is #false.

For the second cond clause, the design requires a lot more work. Again following the design recipe, we first remind ourselves what the expressions in the template accomplish:

- 1. according to the purpose statement for the function,
   (blue-eyed-child? (child-father an-ftree))
   determines whether some child in the father’s FT has "blue" eyes;
- 2. likewise, (blue-eyed-child? (child-mother an-ftree)) determines whether someone in the mother’s FT has blue eyes; and
- 3. the selector expressions (child-name an-ftree), (child-date an-ftree), and (child-eyes an-ftree) extract the name, birth date, and eye color from the given child structure, respectively.

Now we just need to figure out how to combine these expressions.

Clearly, if the child structure contains "blue" in the eyes field, the function’s answer is #true. Next, the expressions concerning names and birth dates are useless, which leaves us with the recursive calls. As stated, (blue-eyed-child? (child-father an-ftree)) traverses the tree on the father’s side, while the mother’s side of the family tree is processed with (blue-eyed-child? (child-mother an-ftree)). If either of these expressions returns #true, an-ftree contains a child with "blue" eyes.

Our analysis suggests that the result should be #true if one of the following three expressions is #true:

- (string=? (child-eyes an-ftree) "blue")
- (blue-eyed-child? (child-father an-ftree))
- (blue-eyed-child? (child-mother an-ftree))

which, in turn, means we need to combine these expressions with or:
