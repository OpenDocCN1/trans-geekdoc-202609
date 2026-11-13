Assumption The given database passes an integrity check, meaning each row is as long as the schema and thus its list of names.

Figure 141 puts all the pieces together. The function project has the suffix .v1 because it calls for some improvement. The following exercises ask you to implement some of those.

```
(define (project.v1 db labels)
  (local ((define schema  (db-schema db))
          (define content (db-content db)))

  ; Spec -> Boolean
  ; does this column belong to the new schema
  (define (keep? c)
    (member? (first c) labels))

  ; Row -> Row
  ; retains those columns whose name is in labels
  (define (row-project row)
    (row-filter row (map first schema)))

  ; Row [List-of Label] -> Row
  ; retains those cells whose name is in labels
  (define (row-filter row names)
    (cond
      [(empty? names) '()]
      [else
       (if (member? (first names) labels)
           (cons (first row)
                 (row-filter (rest row) (rest names)))
           (row-filter (rest row) (rest names)))]))

  (make-db (filter keep? schema)
           (map row-project content))))
```

# Figure 141: Database projection

Exercise 406. The row-project function recomputes the labels for every row of the database’s content. Does the result differ from function call to function call? If not, hoist the expression.

Exercise 407. Redesign row-filter using foldr. Once you have done so, you may merge row-project and row-filter into a single function. Hint The foldr function in ISL+ may consume two lists and process them in parallel.

The final observation is that row-project checks the membership of a label in labels for every single cell. For the cells of the same column in different rows, the result is going to be the same. Hence it also makes sense to hoist this computation out of the function.