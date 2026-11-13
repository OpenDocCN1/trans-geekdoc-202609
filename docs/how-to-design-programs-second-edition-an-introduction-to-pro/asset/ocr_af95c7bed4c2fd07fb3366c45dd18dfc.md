```
; --- 0 through 1000
; --- 1000 through 10000
; --- 10000 and above.
; interpretation the price of an item
```

Do you understand how these ranges relate to the original problem?

+   2. As far as the signature, purpose statement, and function header are concerned, you proceed as before.

Here is the material for our running example:

```
; Price -> Number
; computes the amount of tax charged for p
(define (sales-tax p) 0)
```

> Developers in the real world do not use plain numbers in the chosen programming language for representing amounts of money. See intermezzo 4 for some problems with numbers.

+   3. For functional examples, however, it is imperative that you pick at least one example from each sub-class in the data definition. Also, if a sub-class is a finite range, be sure to pick examples from the boundaries of the range and from its interior.

Since our sample data definition involves three distinct intervals, let’s pick all boundary examples and one price from inside each interval and determine the amount of tax for each: 0, 537, 1000, 1282, 10000, and 12017.

Stop! Try to calculate the tax for each of these prices.

Here is our first attempt, with rounded tax amounts:

| 0 | 537 | 1000 | 1282 | 10000 | 12017 |
|---|---|---|---|---|---|
| 0 | 0 | ??? | 64 | ????? | 961 |

The question marks point out that the problem statement uses the vague phrase “those costing less than $1,000” and “more than $10,000” to specify the tax table. While a programmer may jump to the conclusion that