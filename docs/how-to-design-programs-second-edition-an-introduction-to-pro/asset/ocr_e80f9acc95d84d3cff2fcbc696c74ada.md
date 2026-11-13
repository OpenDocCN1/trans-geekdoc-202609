the best ticket price to a dime.

Here is an alternative version of the same program, given as a single function definition:

```
(define (profit price)
  (- (* (+ 120
     (* (/ 15 0.1)
        (- 5.0 price))))
     price)
  (+ 180
     (* 0.04
        (+ 120
           (* (/ 15 0.1)
              (- 5.0 price))))))
```

Enter this definition into DrRacket and ensure that it produces the same results as the original version for $1, $2, $3, $4, and $5. A single look should suffice to show how much more difficult it is to comprehend this one function compared to the above four.

**Exercise 29.** After studying the costs of a show, the owner discovered several ways of lowering the cost. As a result of these improvements, there is no longer a fixed cost; a variable cost of $1.50 per attendee remains.

Modify both programs to reflect this change. When the programs are modified, test them again with ticket prices of $3, $4, and $5 and compare the results.