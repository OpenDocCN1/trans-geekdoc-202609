trade-off between authoring such expressions manually and processing them automatically. The best way to deal with the latter problem is to provide functions that make X-expressions look like structures, especially functions that access the quasi-fields:

+   * xexpr-name, which extracts the tag of the element representation;
+   * xexpr-attr, which extracts the list of attributes; and
+   * xexpr-content, which extracts the list of content elements.

Once we have these functions, we can use lists to represent XML yet that act as if they were instances of a structure type.

These functions parse S-expressions, and parsers are tricky to design. So let's design them carefully, starting with some data examples:

```
(define a0 '((initial "X")))
(define e0 '(machine))
(define e1 `(machine ,a0))
(define e2 '(machine (action)))
(define e3 '(machine () (action)))
(define e4 `(machine ,a0 (action) (action)))
```

The first definition introduces a list of attributes, which is reused twice in the construction of X-expressions. The definition of e0 reminds us that an X-expression may not come with either attributes or content. You should be able to explain why e2 and e3 are basically equivalent.

Next we formulate a signature, a purpose statement, and a header:

```
; Xexpr.v2 -> [List-of Attribute]
; retrieves the list of attributes of xe
(define (xexpr-attr xe) '())
```

Here we focus on xexpr-attr; we leave the other two as exercises.

Making up functional examples requires a decision concerning the extraction of attributes from X-expressions without any. While our chosen representation