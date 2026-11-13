| BSL expression | representation of BSL expression |
| :--- | :--- |
| `(+ (* 1 1) 10)` | `(make-add (make-mul 1 1) 10)` |
| `(+ (* 3 3)` | `(make-add (make-mul 3 3)` |
| `(* 4 4))` | `(make-mul 4 4))` |
| `(+ (* (+ 4 1 2) 3)` | `(make-add (make-mul (make-add 1 2) 3)` |
| `(* (* (+ 1 1)` | `(make-mul (make-mul` |
| `2)` | `(make-add 1 1)` |
| `4))` | `2)` |
| | `4))` |

# Figure 124: Representing BSL expressions in BSL

**Exercise 345.** Formulate a data definition for the representation of BSL expressions based on the structure type definitions of add and mul. Let's use _BSL-expr_ in analogy for S-expr for the new class of data.

Translate the following expressions into data:

+   1. `(+ 10 -10)`
+   
+   2. `(+ (* 20 3) 33)`
+   
+   3. `(+ (* 3.14 (* 2 3)) (* 3.14 (* -1 -9)))`

Interpret the following data as expressions:

+   1. `(make-add -1 2)`
+   
+   2. `(make-add (make-mul -2 -3) 33)`
+   
+   3. `(make-mul (make-add 1 (make-mul 2 3)) 3.14 ▪`

> Here “interpret” means “translate from data into information.” In contrast, “interpreter” in the title of this chapter refers to a program that consumes the representation of a program and produces its value. While the two ideas are related, they are not the same.

Now that you have a data representation for BSL programs, it is time to design an evaluator. This function consumes a representation of a BSL expression and produces its value. Again, this function is unlike any you have ever designed so it pays off to experiment with some examples. To this end, either you can use the rules of arithmetic to figure out what the value of an