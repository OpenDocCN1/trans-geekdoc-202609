```
(define (editor-kh ed k)
  (cond
    [(key=? k "left") ...]
    [(key=? k "right") ...]
    [(key=? k "\b") ...]
    [(key=? k "\t") ...]
    [(key=? k "\r") ...]
    [(= (string-length k) 1) ...]
    [else ...]))
```

The cond expression doesn’t quite match the data definition for KeyEvent because some KeyEvents need special attention ("left", "\b", and so on), some need to be ignored because they are special ("\t" and "\r"), and some should be classified into one large group (ordinary keys).

**Exercise 178.** Explain why the template for editor-kh deals with "\t" and "\r" before it checks for strings of length 1.

For the fifth step—the definition of the function—we tackle each clause in the conditional separately. The first clause demands a result that moves the cursor and leaves the string content of the editor alone. So does the second clause. The third clause, however, demands the deletion of a letter from the editor’s content—if there is a letter. Last, the sixth cond clause concerns the addition of letters at the cursor position. Following the first basic guideline, we make extensive use of a wish-list and imagine one function per task:

```
(define (editor-kh ed k)
  (cond
    [(key=? k "left") (editor-lft ed)]
    [(key=? k "right") (editor-rgt ed)]
    [(key=? k "\b") (editor-del ed)]
    [(key=? k "\t") ed]
    [(key=? k "\r") ed]
    [(= (string-length k) 1) (editor-ins ed k)]
    [else ed]))
```

As you can tell from the definition of editor-kh, three of the four wish-list functions have the same signature: