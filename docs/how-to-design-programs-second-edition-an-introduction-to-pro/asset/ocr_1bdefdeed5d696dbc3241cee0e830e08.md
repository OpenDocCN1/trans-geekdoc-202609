Use the data definition to explain why these pieces of data belong to Low.
Stop! Also use the data definition to generate two more examples.

> When you work on real-world projects, you won’t use such suffixes; instead you will use a tool for managing different versions of code.

Now that you know that the definition of Low makes sense, it is time to
redesign the function wage* so that it consumes elements of Low, not just lists of
numbers:

```
; Low -> List-of-numbers
; computes the weekly wages for the given records
(define (wage*.v2 an-low)
  '())
```

The suffix “.v2” at the end of the function name informs every reader of the code
that this is a second, revised version of the function. In this case, the revision
starts with a new signature and an adapted purpose statement. The header is the
same as above.

The third step of the design recipe is to work through an example. Let’s start
with the second list above. It contains one work record, namely, (make-work
"Robby" 11.95 39). Its interpretation is that "Robby" worked for 39 hours and
that he is paid at the rate of $11.95 per hour. Hence his wage for the week is
$466.05, that is, (* 11.95 39). The desired result for wage*.v2 is therefore
(cons 466.05 '()). Naturally, if the input list contained two work records, we
would perform this kind of computation twice, and the result would be a list of
two numbers. Stop! Determine the expected result for the third data example
above.

**Note on Numbers** Keep in mind that BSL—unlike most other programming
languages—understands decimal numbers just like you do, namely, as exact
fractions. A language such as Java, for example, would produce
466.04999999999995 for the expected wage of the first work record. Since you
cannot predict when operations on decimal numbers behave in this strange way,
you are better off writing down such examples as