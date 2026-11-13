```
(define school-schema
 '(("Name" ,string?)
   ("Age" ,integer?)
   ("Present" ,boolean?)))

(define school-content
 '(("Alice" 35 #true)
   ("Bob" 25 #false)
   ("Carol" 30 #true)
   ("Dave" 32 #false)))

(define school-db
 (make-db school-schema
   school-content))
```

```
(define presence-schema
 '(("Present" ,boolean?)
   ("Description" ,string?)))

(define presence-content
 '((#true "presence")
   (#false "absence")))

(define presence-db
 (make-db presence-schema
   presence-content))
```

Figure 138: Databases as ISL+ data

**Exercise 403.** A Spec combines a Label and a Predicate into a list. While acceptable, this choice violates our guideline of using a structure type for a fixed number of pieces of information.

Here is an alternative data representation:

```
(define-struct spec [label predicate])
; Spec is a structure: (make-spec Label Predicate)
```

Use this alternative definition to represent the databases from figure 137.

**Integrity Checking** The use of databases critically relies on their integrity. Here “integrity” refers to the constraints (I1) and (I2) from the data definition. Checking database integrity is clearly a task for a function:

```
; DB -> Boolean
; do all rows in db satisfy (I1) and (I2)
```

```
(check-expect (integrity-check school-db) #true)
(check-expect (integrity-check presence-db) #true)
```

```
(define (integrity-check db)
  #false)
```

The wording of the two constraints suggests that some function has to