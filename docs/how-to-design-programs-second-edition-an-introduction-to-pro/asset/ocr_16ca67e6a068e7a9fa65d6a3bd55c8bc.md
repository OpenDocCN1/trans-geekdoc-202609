return key ("\\r").

The function pays attention to only two KeyEvents longer than one letter: "left" and "right". The left arrow moves the cursor one character to the left (if any), and the right arrow moves it one character to the right (if any). All other such KeyEvents are ignored.

Develop a goodly number of examples for edit, paying attention to special cases. When we solved this exercise, we created 20 examples and turned all of them into tests.

**Hint** Think of this function as consuming KeyEvents, a collection that is specified as an enumeration. It uses auxiliary functions to deal with the Editor structure. Keep a wish list handy; you will need to design additional functions for most of these auxiliary functions, such as string-first, string-rest, string-last, and string-remove-last. If you haven't done so, solve the exercises in chapter 2.1.

**Exercise 85.** Define the function run. Given the pre field of an editor, it launches an interactive editor, using render and edit from the preceding two exercises for the to-draw and on-key clauses, respectively.

**Exercise 86.** Notice that if you type a lot, your editor program does not display all of the text. Instead the text is cut off at the right margin. Modify your function edit from exercise 84 so that it ignores a keystroke if adding it to the end of the pre field would mean the rendered text is too wide for your canvas.

**Exercise 87.** Develop a data representation for an editor based on our first idea, using a string and an index. Then solve the preceding exercises again. Retrace the design recipe. **Hint** if you haven't done so, solve the exercises in chapter 2.1.

**Note on Design Choices** The exercise is a first study of making design choices. It shows that the very first design choice concerns the data representation. Making the right choice requires planning ahead and weighing the complexity of each. Of course, getting good at this is a question of gaining experience.