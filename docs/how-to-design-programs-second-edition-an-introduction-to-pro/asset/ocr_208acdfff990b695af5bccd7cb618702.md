liners.” Here are definitions for sum and product, two functions used several times in the first few sections of this chapter:

```
; [List-of Number] -> Number ; [List-of Number] -> Number
(define (sum lon) (define (product lon)
 (reduce lon 0 +)) (reduce lon 1 *))
```

For sum, the base case always produces 0; adding the first item and the result of the natural recursion combines the values of the second clause. Analogous reasoning explains product. Other list-processing functions can be defined in a similar manner using reduce.