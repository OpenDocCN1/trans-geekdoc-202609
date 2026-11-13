
If you ignore the last row and apply the first three questions to any function that consumes a List-of-strings, you arrive at this shape:

```scheme
(define (fun-for-los alos)
  (cond
    [(empty? alos) ...]
    [else
      (... (first alos) ... (rest alos) ...)]))
```

Recall, though, that the purpose of a template is to express the data definition as a function layout. That is, a template expresses as code what the data definition for the input expresses as a mix of English and BSL. Hence all important pieces of the data definition must find a counterpart in the template, and this guideline should also hold when a data definition is self-referential—contains an arrow from inside the definition to the term being defined. In particular, when a data definition is self-referential in the ith clause and the kth field of the structure mentioned there, the template should be self-referential in the ith cond clause and the selector expression for the kth field. For each such selector expression, add an arrow back to the function parameter. At the end, your template must have as many arrows as we have in the data definition.

Figure 51 illustrates this idea with the template for functions that consume List-of-strings shown side by side with the data definition. Both contain one arrow that originates in the second clause—the rest field and selector, respectively—and points back to the top of the respective definitions.

Since BSL and most programming languages are text-oriented, you must use an alternative to the arrow, namely, a self-application of the function to the appropriate selector expression:

```scheme
(define (fun-for-los alos)
  (cond
    [(empty? alos) ...]
    [else
      (... (first alos) ...
        ... (fun-for-los (rest alos)) ...)]))
```

We refer to a self-use of a function as *recursion* and in the first four parts of the book as *natural recursion*.

> For the curious among our readers, the design recipe for arbitrarily large data corresponds to so-called “proofs by induction” in mathematics, and the “leap of faith” represents the use of the induction hypothesis for the inductive step of such a proof. Logic proves the validity of this proof technique with an Induction Theorem.

- 5. For the function body we start with those cond lines without recursive function calls, known as *base cases*. The corresponding answers are typically easy to formulate or already given as examples.
- Then we deal with the self-referential cases. We start by reminding ourselves what each of the expressions in the template line computes. For the natural recursion we assume that the function already works as specified in our purpose statement. This last step is a leap of faith, but as you will see, it always works.

**The rest is then a matter of combining the various values.**

Figure 53 formulates the first four questions and answers for this step. Let’s use this game to complete the definition of how-many. Renaming the fun-for-los template to how-many gives us this much:

```scheme
; List-of-strings -> Number
; determines how many strings are on alos
(define (how-many alos)
 (cond
   [(empty? alos) ...]
   [else
    (... (first alos) ...
     ... (how-many (rest alos)) ...)]))
```

## Figure 53: How to turn a template into a function definition

| Question | Answer |
| :--- | :--- |
| What are the answers for the non-recursive `cond` clauses? | The examples should tell you which values you need here. If not, formulate appropriate examples and tests. |
| What do the selector expressions in the recursive clauses compute? | The data definitions tell you what kind of data these expressions extract, and the interpretations of the data definitions tell you what this data represents. |
| What do the natural recursions compute? | Use the purpose statement of the function to determine what the value of the recursion means, not how it computes this answer. If the purpose statement doesn't tell you the answer, improve the purpose statement. |
| How can the function combine these values to get the desired answer? | Find a function in BSL that combines the values. Or, if that doesn't work, make a wish for a helper function. For many functions, this last step is straightforward. The purpose, the examples, and the template together tell you which function or expression `combines` the available values into the proper result. We refer to this function or expression as a `combinator`, slightly abusing existing terminology. |

As the functional examples already suggest, the answer for the base case is 0. The two expressions in the second clause compute the first item and the number of strings in `(rest alos)`. To compute how many strings there are on all of `alos`, the function just needs to add 1 to the value of the latter expression:

```scheme
(define (how-many alos)
  (cond
    [(empty? alos) 0]
    [else (+ (how-many (rest alos)) 1)]))
```

> *Felix Klock suggested this table-based approach to guessing the combinator.*

Finding the correct way to combine the values into the desired answer isn't always as easy. Novice programmers often get stuck with this step. As figure 54 suggests, it is a good idea to arrange the functional examples into a table that also spells out the values of the expressions in the template. Figure 55 shows what this table looks like for our how-many example. The left-most column lists the sample inputs, while the right-most column contains the desired answers for these inputs. The three columns in between show the values of the template expressions: (first alos), (rest alos), and (how-many (rest alos)), which is the natural recursion. If you stare at this table long enough, you recognize that the result column is always one more than the values in the natural recursion column. You may thus guess that

```
(+ (how-many (rest alos)) 1)
```

is the expression that computes the desired result. Since DrRacket is fast at checking these kinds of guesses, plug it in and click RUN. If the examples-turned-into-tests pass, think through the expression to convince yourself it works for all lists; otherwise add more example rows to the table until you have a different idea.

| Question | Answer |
| :--- | :--- |
| So, if you are stuck here, ... | ... arrange the examples from the third step in a table. Place the given input in the first column and the desired output in the last column. In the intermediate columns enter the values of the selector expressions and the natural recursion(s). Add examples until you see a pattern emerge that suggests a combinator. |
| If the template refers to some other template, what does the auxiliary function compute? | Consult the other function's purpose statement and examples to determine what it computes, and assume you may use the result even if you haven't finished the design of this helper function. |

Figure 54: Turning a template into a function, the table method

| alos | (first alos) | (rest alos) | (how-many (rest alos)) | (how-many alos) |
|---|---|---|---|---|
| (cons "a" '()) | "a" | '() | 0 | 1 |
| (cons "b" (cons "a" '())) | "b" | (cons "a" '()) | 1 | 2 |
| (cons "x" (cons "b" (cons "a" '()))) | "x" | (cons "b" (cons "a" '())) | 2 | 3 |

Figure 55: Tabulating arguments, intermediate values, and results

The table also points out that some selector expressions in the template are possibly irrelevant for the actual definition. Here (first alos) is not needed to compute the final answer—which is quite a contrast to contains-flatt?, which uses both expressions from the template.

As you work your way through the rest of this book, keep in mind that, in many cases, the combination step can be expressed with BSL’s primitives, say, +, and, or cons. In some cases, though, you may have to make a wish, that is, design an auxiliary function. Finally, in yet other cases, you may need nested conditions.

- 6. Finally, make sure to turn all examples into tests, that these tests pass, and that running them covers all the pieces of the function.

Here are our examples for how-many turned into tests:

```scheme
(check-expect (how-many '()) 0)
(check-expect (how-many (cons "a" '())) 1)
(check-expect
 (how-many (cons "b" (cons "a" '()))) 2)
```

Remember, it is best to formulate examples directly as tests, and BSL allows this. Doing so also helps if you need to resort to the table-based guessing approach of the preceding step.

Figure 56 summarizes the design recipe of this section in a tabular format. The first column names the steps of the design recipe, and the second the expected results of each step. In the third column, we describe the activities that
