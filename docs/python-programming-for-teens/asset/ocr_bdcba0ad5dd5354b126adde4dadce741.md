Python variables are spelled using letters, digits, and the underscore (`_`). The following rules apply to their use:

+   - A variable must begin with a letter or an underscore (`_`) and contain at least one letter.
+   - Variables are case sensitive. Thus, the variable `volume` is different from the variable `Volume`, although they may refer to the same value.
+   - Python programmers typically spell variables in lowercase letters but use capital letters or underscores to emphasize embedded words, as in `firstVolume` or `first_volume`.
+   - When the value of a variable will not change after its initial assignment, it's considered a constant. PI is an example of a constant. Python programmers typically spell constants using all caps to indicate this.
+   - Before you can use a variable, you must assign it a value. An attempt to use a variable that has not been initialized in this way generates an error message, as shown in Figure 1.5.

![](bbox=[0.11, 0.48, 0.72, 0.63])

Figure 1.5
Attempting to use a variable that has not been assigned a value.
© 2014 Python Software Foundation.

To summarize, there are three reasons to use variables in Python code:

+   1. They make code easy to read and understand.
+   2. They help to eliminate unnecessary computations.
+   3. They make code easy to modify and maintain (to be discussed later).