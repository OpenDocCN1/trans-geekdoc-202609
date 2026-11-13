```
; Editor -> Editor
```

The last one takes two arguments instead of one:

```
; Editor 1String -> Editor
```

We leave the proper formulation of wishes for the first three functions to you and focus on the fourth one.

Let's start with a purpose statement and a function header:

```
; insert the 1String k between pre and post
(define (editor-ins ed k)
  ed)
```

The purpose is straight out of the problem statement. For the construction of a function header, we need an instance of Editor. Since pre and post are the pieces of the current one, we just put them back together.

Next we derive examples for editor-ins from those for editor-kh:

```
(check-expect
  (editor-ins (make-editor '() '()) "e")
  (make-editor (cons "e" '()) '()))

(check-expect
  (editor-ins
    (make-editor (cons "d" '())
                 (cons "f" (cons "g" '()))))
  "e")
  (make-editor (cons "e" (cons "d" '()))
               (cons "f" (cons "g" '()))))
```

You should work through these examples using the interpretation of Editor. That is, make sure you understand what the given editor means in terms of information and what the function call is supposed to achieve in those terms. In this particular case, it is best to draw the visual representation of the editor because it represents the information well.

The fourth step demands the development of the template. The first argument