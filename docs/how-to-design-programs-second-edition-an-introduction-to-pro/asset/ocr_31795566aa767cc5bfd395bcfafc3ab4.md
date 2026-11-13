```
(cons (cons "TTT" '())
 (cons '()
   (cons (cons "Put"
      (cons "up"
         (cons ... '()) )))
   (cons ...
      '()) )))
```

This representation has an advantage over the second one in that it preserves the organization of the file, including the emptiness of the second line. The price is that all of a sudden lists contain lists.

While the idea of list-containing lists may sound frightening at first, you need not worry. The design recipe helps even with such complications.

Before we get started, take a look at figure 67. It introduces a number of useful file reading functions. They are not comprehensive: there are many other ways of dealing with text from files, and you will need to know a lot more to deal with all possible text files. For our purposes here—teaching and learning the principles of systematic program design—they suffice, and they empower you to design reasonably interesting programs.

```
;
; String -> String
; produces the content of file f as a string
(define (read-file f) ...)

;
; String -> List-of-string
; produces the content of file f as a list of strings,
; one per line
(define (read-lines f) ...)

;
; String -> List-of-string
; produces the content of file f as a list of strings,
; one per word
(define (read-words f) ...)

;
; String -> List-of-list-of-string
; produces the content of file f as a list of list of
; strings, one list per line and one string per word
(define (read-words/line f) ...)

;
; The above functions consume the name of a file as a String
; argument. If the specified file does not exist in the
; same folder as the program, they signal an error.
```