1. If the input is '(), there is only one possible rearrangement of the input: the '() word. Hence the result is (list '()), the list that contains the empty list as the only item.

2. Otherwise there is a first letter in the word, and (first w) is that letter. Also, the recursion produces the list of all possible rearrangements for the rest of the word. For example, if the list is

```
(list "d" "e" "r")
```

then the recursion is (arrangements (list "e" "r")). It will produce the result

```
(cons (list "e" "r")
 (cons (list "r" "e")
 '()))
```

To obtain all possible rearrangements for the entire list, we must now insert the first item, "d" in our case, into all of these words between all possible letters and at the beginning and end.

Our analysis suggests that we can complete arrangements if we can somehow insert one letter into all positions of many different words. The last aspect of this task description implicitly mentions lists and, following the advice of this chapter, calls for an auxiliary function. Let’s call this function insert-everywhere/in-all-words and let’s use it to complete the definition of arrangements:

```
(define (arrangements w)
 (cond
 [(empty? w) (list '())]
 [else (insert-everywhere/in-all-words (first w)
 (arrangements (rest w)))]))
```

Exercise 213. Design insert-everywhere/in-all-words. It consumes a 1String and a list of words. The result is a list of words like its second argument, but with the first argument inserted at the beginning, between all letters, and at