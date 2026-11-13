```
(define projected-content
   (("Alice" #true)
     ("Bob" #false)
     ("Carol" #true)
     ("Dave" #false)))
```

```
(define projected-schema
   (("Name" ,string?) ("Present" ,boolean?)))
```

```
(define projected-db
   (make-db projected-schema projected-content))
; Stop! Read this test carefully. What's wrong?
(check-expect (project school-db '("Name" "Present"))
   projected-db)
```

If you run the above code in DrRacket, you get the error message

```
first argument of equality cannot be a function
```

before DrRacket can even figure out whether the test succeeds. Recall from chapter 14.4 that functions are infinitely large objects and it is impossible to ensure that two functions always produce the same result when applied to the same arguments. We therefore weaken the test case:

```
(check-expect
   (db-content (project school-db '("Name" "Present")))
   projected-content)
```

For the template, we again reuse existing abstractions; see figure 140. The local expression defines two functions: one for use with filter for narrowing down the schema of the given database and the other for use with map for thinning out the content. In addition, the function again extracts and names the schema and the content from the given database.