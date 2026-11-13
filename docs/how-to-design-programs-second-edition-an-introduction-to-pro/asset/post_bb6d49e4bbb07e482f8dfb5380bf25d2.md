
This form of hoisting is somewhat more difficult than plain expression hoisting. We basically wish to pre-compute the result of

```
(member? label labels)
```

for all rows and pass the results into the function instead of the list of labels. That is, we replace the list of labels with a list of Booleans that indicate whether the cell in the corresponding position is to be kept. Fortunately, computing those Booleans is just another application of keep? on the schema:

```
(map keep? schema)
```

Instead of keeping some Specs from the given schema and throwing away the others, this expression just collects the decisions. Figure 142 shows the final version of project and integrates the solutions for the preceding exercises. It also uses local to extract and name schema and content, plus keep? for checking whether the label in some Spec is worth keeping. The remaining two definitions introduce mask, which stands for the list of Booleans discussed above, and the revised version of row-project. The latter uses foldr to process the given row and mask in parallel.

```
(define (project db labels)
(local ((define schema (db-schema db))
        (define content (db-content db)))
; Spec -> Boolean
; does this column belong to the new schema
(define (keep? c)
(member? (first c) labels))
; Row -> Row
; retains those columns whose name is in labels
(define (row-project row)
(foldr (lambda (cell m c) (if m (cons cell c) c))
        '()
        row
        mask))
(define mask (map keep? schema)))
(make-db (filter keep? schema)
         (map row-project content))))
```

Figure 142: Database projection

Compare this revised definition of `project` with `project.v1` in figure 141. The final definition is both simpler and faster than the original version. Systematic design combined with careful revisions pays off; test suites ensure that revisions don't mess up the functionality of the program.

### Exercise 408.
Design the function `select`. It consumes a database, a list of labels, and a predicate on rows. The result is a list of rows that satisfy the given predicate, projected down to the given set of labels.

### Exercise 409.
Design `reorder`. The function consumes a database `db` and list `lol` of Labels. It produces a database like `db` but with its columns reordered according to `lol`. **Hint** Read up on `list-ref`.

At first assume that `lol` consists exactly of the labels of `db`'s columns. Once you have completed the design, study what has to be changed if `lol` contains fewer labels than there are columns and strings that are not labels of a column in `db`.

### Exercise 410.
Design the function `db-union`, which consumes two databases with the exact same schema and produces a new database with this schema and the joint content of both. The function must eliminate rows with the exact same content.

Assume that the schemas agree on the predicates for each column.

### Exercise 411.
Design `join`, a function that consumes two databases: `db-1` and `db-2`. The schema of `db-2` starts with the exact same Spec that the schema of `db-1` ends in. The function creates a database from `db-1` by replacing the last cell in each row with the *translation* of the cell in `db-2`.

Here is an example. Take the databases in figure 137. The two satisfy the assumption of these exercises, that is, the last Spec in the schema of the first is equal to the first Spec of the second. Hence it is possible to join them:

| Name String | Age Integer | Description String |
|---|---|---|
| "Alice" | 35 | "presence" |
| "Bob" | 25 | "absence" |
| "Carol" | 30 | "presence" |
| "Dave" | 32 | "absence" |

Its translation maps #true to "presence" and #false to "absence".

### Hints
- (1) In general, the second database may “translate” a cell to a row of values, not just one value. Modify the example by adding additional terms to the row for “presence” and “absence”.
- (2) It may also “translate” a cell to several rows, in which case the process adds several rows to the new database. Here is a second example, a slightly different pair of databases from those in figure 137:

| Name String | Age Integer | Present Boolean |
| :--- | :--- | :--- |
| "Alice" | 35 | #true |
| "Bob" | 25 | #false |
| "Carol" | 30 | #true |
| "Dave" | 32 | #false |

| Present Boolean | Description String |
| :--- | :--- |
| #true | "presence" |
| #true | "here" |
| #false | "absence" |
| #false | "there" |

Joining the left database with the one on the right yields a database with eight rows:

| Name String | Age Integer | Description String |
| :--- | :--- | :--- |
| "Alice" | 35 | "presence" |
| "Alice" | 35 | "here" |
| "Bob" | 25 | "absence" |
| "Bob" | 25 | "there" |
| "Carol" | 30 | "presence" |
| "Carol" | 30 | "here" |
| "Dave" | 32 | "absence" |
| "Dave" | 32 | "there" |

- (3) Use iterative refinement to solve the problem. For the first iteration, assume that a “translation” finds only one row per cell. For the second one, drop the assumption.

### Note on Assumptions
This exercise and the entire section mostly rely on informally stated assumptions about the given databases. Here, the design of join assumes that “the schema of db-2 starts with the exact same Spec that the schema of db-1 ends in.” In reality, database functions must be checked functions in the spirit of chapter 6.3. Designing checked-join would be impossible for you, however. A comparison of the last Spec in the schema of db-1 with the first one in db-2 calls for a comparison of functions. For practical solutions, see a text on databases.

## 24 Summary

This fourth part of the book is about the design of functions that process data whose description requires many intertwined definitions. These forms of data show up everywhere in the real world, from your computer’s local file system to the world wide web and geometric shapes used in animated movies. After working through this part of the book carefully, you know that the design recipe scales to these forms of data, too:

- 1. When the description of program data calls for several mutually referential data definitions, the design recipe calls for the simultaneous development of templates, one per data definition. If a data definition A refers to a data definition B, then the template function-for-A refers to function-for-B in the exact same place and manner. Otherwise the design recipes work as before, function for function.

- 2. When a function has to process two types of complex data, you need to distinguish three cases. First, the function may deal with one of the arguments as if it were atomic. Second, the two arguments are expected to have the exact same structure, and the function traverses them in a completely parallel manner. Third, the function may have to deal with all possible combinations separately. In this case, you make a two-dimensional table that along one dimension enumerates all kinds of data from one data definition and along the other one deals with the second kind of data. Finally you use the table’s cells to formulate conditions and answers for the various cases.

This part of the book deals with functions on two complex arguments. If you ever encounter one of those rare cases where a function receives three complex pieces of data, you know you need (to imagine) a three-dimensional table.

You have now seen all forms of structural data that you are likely to encounter over the course of your career, though the details will differ. If you are ever stuck, remember the design recipe; it will get you started.

## INTERMEZZO 4: THE NATURE OF NUMBERS

When it comes to numbers, programming languages mediate the gap between the underlying hardware and true mathematics. The typical computer hardware represents numbers with fixed-size chunks of data; they also come with processors that work on just such chunks. In paper-and-pencil calculations, we don’t worry about how many digits we process; in principle, we can deal with numbers that consist of one digit, 10 digits, or 10,000 digits. Thus, if a programming language uses the numbers from the underlying hardware, its calculations are as efficient as possible. If it sticks to the numbers we know from mathematics, it must translate those into chunks of hardware data and back—and these translations cost time. Because of this cost, most creators of programming languages adopt the hardware-based choice.

> *These chunks are called bits, bytes, and words.*

This intermezzo explains the hardware representation of numbers as an exercise in data representation. Concretely, the first subsection introduces a concrete fixed-size data representation for numbers, discusses how to map numbers into this representation, and hints at how calculations work on such numbers. The second and third sections illustrate the two most fundamental problems of this choice: arithmetic overflow and underflow, respectively. The last one sketches how arithmetic in the teaching languages works; its number system **generalizes** what you find in most of today’s programming languages. The final exercises show how bad things can get when programs compute with numbers.

### Fixed-Size Number Arithmetic
