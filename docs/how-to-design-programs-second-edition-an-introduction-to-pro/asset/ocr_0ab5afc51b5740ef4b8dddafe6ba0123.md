# 32.4 A Graphical Editor, with Mouse

Chapter 5.10 introduces the notion of a one-line editor and presents a number of exercises on creating a graphical editor. Recall that a graphical editor is an interactive program that interprets key events as editing actions on a string. In particular, when a user presses the left or right arrow keys, the cursor moves left or right; similarly, pressing the delete key removes a 1String from the edited text. The editor program uses a data representation that combines two strings in a structure. Chapter 10.4 resumes these exercises and shows how the same program can greatly benefit from a different data structure, one that combines two strings.

Neither of these sections deals with mouse actions for navigation, even though all modern applications support this functionality. The basic difficulty with mouse events is to place the cursor at the appropriate spot. Since the program deals with a single line of text, a mouse click at (x,y) clearly aims to place the cursor between the letters that are visible at or around the x position. This section fills the gap.

Recall the relevant definitions from chapter 10.4:

```
(define FONT-SIZE 11)
(define FONT-COLOR "black")
```

```
; [List-of 1String] -> Image
; renders a string as an image for the editor
(define (editor-text s)
 (text (implode s) FONT-SIZE FONT-COLOR))
```

```
(define-struct editor [pre post])
; An Editor is a structure:
;   (make-editor [List-of 1String] [List-of 1String])
; interpretation if (make-editor p s) is the state of
; an interactive editor, (reverse p) corresponds to
; the text to the left of the cursor and s to the
; text on the right
```

**Exercise 508.** Design split-structural using the structural design recipe.