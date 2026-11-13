The function consumes a list of 1Strings ed and a natural number x; the former represents the complete string in some Editor and the latter the x-coordinate of the mouse click. The function produces

```
(make-editor p s)
```

such that (1) p and s make up ed and (2) x is larger than the image of p and smaller than the image of p extended with the first 1String on s (if any).

Here is the first condition expressed with an ISL+ expression:

```
(string=? (string-append p s) ed)
```

The second one is

```
(<= (image-width (editor-text p))
x
(image-width (editor-text (append p (first s)))))
```

assuming (cons? s).

**Hints** (1) The x-coordinate measures the distance from the left. Hence the function must check whether smaller and smaller prefixes of ed fit into the given width. The first one that doesn’t fit corresponds to the pre field of the desired Editor, the remainder of ed to the post field.

(2) Designing this function calls for thoroughly developing examples and tests. See chapter 4.

**Exercise** 509. Design the function split. Use the accumulator design recipe to improve on the result of exercise 508. After all, the hints already point out that when the function discovers the correct split point, it needs both parts of the list, and one part is obviously lost due to recursion.

Once you have solved this exercise, equip the main function of chapter 10.4 with a clause for mouse clicks. As you experiment with moving the cursor via mouse clicks, you will notice that it does not exactly behave like applications that you use on your other devices—even though split passes all its tests.

Graphical programs, like editors, call for experimentation to come up with the best “look and feel” experiences. In this case, your editor is too simplistic with its placement of the cursor. After the applications on your computer determine the split point, they also determine which letter division is closer to