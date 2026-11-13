```
(define (contains-flatt? alon)
  (cond
    [(empty? alon) #false]
    [(cons? alon)
     (... (string=? (first alon) "Flatt")
       ... (rest alon) ...))]))
```

Furthermore, if the comparison yields #true, the function must produce #true.
If the comparison yields #false, we are left with another list of strings: (rest
alon). Clearly, the function can’t know the final answer in this case, because the
answer depends on what “...” represents. Put differently, if the first item is not
"Flatt", we need some way to check whether the rest of the list contains
"Flatt".

Fortunately, we have contains-flatt? and it fits the bill. According to its
purpose statement, it determines whether a list contains "Flatt". The statement
implies that (contains-flatt? 1) tells us whether the list of strings 1 contains
"Flatt". And, in the same vein, (contains-flatt? (rest alon)) determines
whether "Flatt" is a member of (rest alon), which is precisely what we need
to know.

In short, the last line should be (contains-flatt? (rest alon)):

```
;
; List-of-names -> Boolean
(define (contains-flatt? alon)
  (cond
    [(empty? alon) #false]
    [(cons? alon)
     (... (string=? (first alon) "Flatt") ...
       ... (contains-flatt? (rest alon)) ...))]))
```

The trick is now to combine the values of the two expressions in the appropriate
manner. As mentioned, if the first expression yields #true, there is no need to
search the rest of the list; if it is #false, though, the second expression may still
yield #true, meaning the name "Flatt" is on the rest of the list. All of this
suggests that the result of (contains-flatt? alon) is #true if **either** the first
expression in the last line **or** the second expression yields #true.
Figure 47 then shows the complete definition. Overall it doesn’t look too