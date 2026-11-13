is guaranteed to be a structure, and the second one is a string, an atomic piece of data. In other words, the template just pulls out the pieces from the given editor representation:

```
(define (editor-ins ed k)
 (... ed ... k ...
  ... (editor-pre ed) ...
  ... (editor-post ed) ...))
```

Remember a template lists parameters because they are available, too.

From the template and the examples, it is relatively easy to conclude that editor-ins is supposed to create an editor from the given editor's pre and post fields with k added to the front of the former:

```
(define (editor-ins ed k)
 (make-editor (cons k (editor-pre ed)))
 (editor-post ed)))
```

Even though both (editor-pre ed) and (editor-post ed) are lists of 1Strings, there is no need to design auxiliary functions. To get the desired result, it suffices to use cons, which creates lists.

At this point, you should do two things. First, run the tests for this function. Second, use the interpretation of Editor and explain abstractly why this function performs the insertion. And as if this isn't enough, you may wish to compare this simple definition with the one from exercise 84 and figure out why the other one needs an auxiliary function while our definition here doesn't.

# **Exercise 179. Design the functions**

```
; Editor -> Editor
; moves the cursor position one 1String left,
; if possible
(define (editor-lft ed) ed)
```

```
; Editor -> Editor
; moves the cursor position one 1String right,
; if possible
```