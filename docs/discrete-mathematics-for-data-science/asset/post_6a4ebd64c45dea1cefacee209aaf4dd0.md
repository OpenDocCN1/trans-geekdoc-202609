
R_11 = the entry in row 1, column 1. R_12 = the entry in row 1, column 2. R_21 = the entry in row 2, column 1. etc.

Using a matrix to represent relations between sets A and B, for each relation R_ai_bj enter a 1 (if true) or 0 (if false). Table 7.1 is an example of such a relation matrix, where a relation is defined as a > b with set A = { 1 3 5 7 } and set B = { 1 3 4 6 }.

### TABLE 7.1 Relation where a > b

| | a1 | a3 | a5 | a7 |
|---|---|---|---|---|
| b1 | 0 | 1 | 1 | 1 |
| b3 | 0 | 0 | 1 | 1 |
| b4 | 0 | 0 | 1 | 1 |
| b6 | 0 | 0 | 0 | 1 |

As can be seen, the pair (3, 1) has a relation denoted as 1, because 3 > 1. But the pair (5, 6) has no relation denoted by 0, because a > b is not satisfied.

The relation set aRb is comprised of the respective pairs indicated by the 1s in the table:

aRb = { (3, 1) (5, 1) (5, 3) (5, 4) (7, 1) (7, 3) (7, 4) (7, 6) }

Excluded are the pairs that do not satisfy this relation, such as (1, 1) (1, 3) (1, 4) ...

The domain of the relation is the list of distinct a elements comprising each pair:

DoR = { 3 5 7 }

The range of the relation is the list of distinct b elements comprising each pair:

RaR = { 1 3 4 6 }

A matrix for the relation R on a sets A and B, with four rows and four columns, as in the above example, contains entries that are indexed as follows:

| R11 | R12 | R13 | R14 |
|---|---|---|---|
| R21 | R22 | R23 | R24 |
| R31 | R32 | R33 | R34 |
| R41 | R42 | R43 | R44 |

For the relation in Table 7.1, we have R11 = 0, R12 = 1, R13 = 1, R14 = 1, etc.

Note that the NW → SE diagonal coordinate set is { R11 R22 R33 R44 } and the NE → SW diagonal coordinate set is { R14 R23 R32 R41 }.

Related to the matrix shown in Table 7.1 is another matrix that includes additional rows and columns for *all* the numbers in the union of sets A and B. This enlarged matrix, called an *adjacency matrix*, for the aforementioned relation, $aRb = \{ (3, 1), (5, 1), (5, 3), (5, 4), (7, 1), (7, 3), (7, 4), (7, 6) \}$, is shown in Table 7.2, where the value of the relation is given for each $R_{a_i b_j}$ column × row intersection.

### TABLE 7.2 An adjacency matrix

| | a1 | a2 | a3 | a4 | a5 | a6 | a7 |
|---|---|---|---|---|---|---|---|
| b1 | 0 | 0 | 1 | 0 | 1 | 0 | 1 |
| b2 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| b3 | 0 | 0 | 0 | 0 | 1 | 0 | 1 |
| b4 | 0 | 0 | 0 | 0 | 1 | 0 | 1 |
| b5 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |
| b6 | 0 | 0 | 0 | 0 | 0 | 0 | 1 |
| b7 | 0 | 0 | 0 | 0 | 0 | 0 | 0 |

While a matrix may not always be square, an adjacency matrix will always be square, with a row count that is the same as the column count.

We can use the adjacency matrix to determine whether or not R is reflexive. If all entries were “1” along the NW → SE diagonal, then R would be reflexive. The relation $aRb$ shown in Table 7.2 is not reflexive since not all elements on the diagonal are “1”. In fact, they are all zeros for this particular relation.

We can also use the adjacency matrix to determine whether R is symmetric. The values in the areas above the NW → SE diagonal should mirror those below the NW → SE diagonal. The relation $aRb$ shown in Table 7.2 is obviously not symmetric, comparing the sides of the NW → SE diagonal.

## 7.7 VENN DIAGRAMS OF SETS

Another useful visual tool for analyzing logical relations between sets is the Venn diagram. In each Venn diagram, the shaded area represents the set described by a logical set operation.

![](img/ff796e63b14a88ab72583e78f3994e90_183_0.png)

Figure 7.1 (a) An intersection of sets. (b) A union of sets.

![](img/ff796e63b14a88ab72583e78f3994e90_184_0.png)

(a)

![](img/ff796e63b14a88ab72583e78f3994e90_184_1.png)

(b)

Figure 7.2 (a) A difference of sets. (b) A difference of sets.

![](img/ff796e63b14a88ab72583e78f3994e90_184_2.png)

(a)

![](img/ff796e63b14a88ab72583e78f3994e90_184_3.png)

(b)

Figure 7.3 (a) The complement of intersecting sets. (b) The complement of a union of sets.

## 7.8 PROGRAMMATIC TREATMENT OF SETS AS LISTS

Lists and sets can be treated similarly in their processing.7

Consider the following list construction:

```
{ } L LIST
```

Since this list contains no elements its cardinality is zero:

```
L' LEN 0 EQ ( → 1,true)
```

Conversely, suppose that we create a nonempty list:

```
{l₀ l₁ ... lₙ} L LIST
```

This list has cardinality greater than zero:

```
L \not LEN 0 > ( → 1,true)
```

By an element count of 0 we can determine that a list is empty. Any greater count signifies that the list is not empty.

Suppose we wish to prove that two lists, L₀ and L₁, have the same cardinality. We want to show that:

```
(L₀) = (L₁)
```

This Boolean operation has an outcome of either true or false.

Programmatically, given the following two lists Ia and Ix, we can check if they have the same cardinality.

```
{ a b c } Ia LIST
{ x y z } Ix LIST
Ia' LEN Ix' LEN EQ ( → 1, or true)
```

### Theorem:

```
For all lists L₀, L₁, ..., Lₙ :
|L₀ L₁ ... Lₙ| = |L₀| + |L₁| + ... + |Lₙ|
```

The concatenation (the joining) of the separate lists into the one list $L_0$ can be done as:

```
{L0 L1} L0 LIST
{L0 L2} L0 LIST
...
{L0 LN} L0 LIST
```

Then, the new cardinality of list $L_0$ may be shown as:

```
$L_0!$LEN
```

## EXERCISES

- 1. Suppose $S(x)$ is x swims and $D(x)$ is builds a dam. Use symbols such as \(\forall\) or \(\exists\) to translate the following statement to symbolic form:

Some of these animals swim.

- 2. Given that x and y represent real numbers, explain the expression: \(\forall x \exists y(x < y)\)

- 3. Given set $B = \{ 10 \ 12 \ 14 \ 8 \ 7 \}$ and relation $R = \{ (10 \ 11), (10 \ 12) (10, 14) (10, 8) (10, 7) (12, 12) (12, 8) (12, 7) (14, 14) (14, 8) (14, 7) (8, 8) (8, 7) (7, 7) \}$, determine if R is reflexive, symmetric, asymmetric, and/or transitive.

- 4. Explain the cardinality of the Power Set of the set { 0 1 2 }.

- 5. Explain the Power Set of { a b }, where a and b are distinct elements.

- 6. Given that sets A and B have 3 and 4 elements respectively, what is the number of subsets of the set \(A \times B\)?

- 7. Find the members of the set S = { x | x is the square of an integer and x < 49 }.

- 8. Find the union of the sets { 1 2 5 } and { 1 2 6 }.

- 9. Find the intersection of the sets { 1 2 5 } and { 1 2 6 }. Are these sets disjoint? Explain.

- 10. Give the difference of the sets A = { 1 2 5 } and B = { 1 2 6 }, with respect to the order A − B.

- 11. Find the union, intersection and difference of the sets { 2 3 6 } and { 1 3 5 }. Are the resulting sets disjoint from one another? Explain.

- 12. Write a symbolic expression for a set of all of the odd integers greater than 0 and less than 10.

- 13. Explain how two sets can be equivalent.

- 14. Describe in general terms a reflexive relation R on set A.

- 15. Describe in general terms a symmetric relation R on set A.

- 16. Describe in general terms a transitive relation R on set A.

- 17. Describe in general terms an equivalence relation R on set A.

- 18. What are the domain and range of the following relation? { (-1, 2) (2, 5) (1, 3) (8, 7) (9, 5) }

- 19. What are the domain and range of the following relation? { (-5, 6) (12, -15) (11, 33) (81, 99) (19, 15) }

- 20. Write an algorithm to show that R ∩ G ∩ B = C. Sets R, G and B contain elements of red (r), green (g), and blue (b) respectively. The proportion of elements in their intersection determines the color, C. Related: https://www.w3schools.com/colors/colors_rgb.asp

- 21. Sketch Venn diagrams to illustrate:
  - (a) \( (A' \cup B) \)
  - (b) \( (A \cap B') \)

- 22. For sets \( A = \{ 2 3 5 7 9 \} \) and \( B = \{ 2 4 5 7 \} \) and relation \( a \ge b \),
  - (a) Set up an adjacency matrix to show the relation \( aRb \).
  - (b) Explain how to use the adjacency matrix to determine whether this relation is reflexive and/or symmetric.

- 23. Determine and explain if the relation \( R \) is an equivalence relation.
\( R = \{ (1,1)(2,2)(3,3)(4,4)(3,4)(4,3) (1,4)(4,1)(4,2)(2,4)(3,1)(1,3) \} \)

- 24. Create two sets, \( A \) and \( B \), such that \( A \cap B \neq \{ \} \) or \( \emptyset \), where \( A \) is a set of positive integers and \( B \) is a set of odd positive integers.

- 25. Create two sets, \( A \) and \( B \), such that \( A = B \), where \( A \) is a set of positive base\(_{10}\) integers and \( B \) is a set of positive base\(_{2}\) integers.
