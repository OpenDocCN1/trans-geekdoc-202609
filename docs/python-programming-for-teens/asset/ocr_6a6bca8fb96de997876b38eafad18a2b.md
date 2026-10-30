Throughout this book, you will conduct analysis, design, and testing informally. In this chapter, you will focus on the tools in IDLE for coding, compiling, and running Python programs.

# COMPOSING A PROGRAM

Thus far in this book, you have typed your Python code fragments in the IDLE shell and run them there. You have viewed the results either in the shell window or in a turtle graphics window. When you want to enter and save code that you can edit and run later, you can open a new file in IDLE and work in a separate window. In this section, you learn how to do that. You also explore the kind of structure your code should have, as a complete Python program.

# Program Edits

There are several ways to edit a program with IDLE. Each one depends on where you are in the process.

+   - You’re starting from scratch on a new program. You launch IDLE and then select the New File option from the shell window’s File menu. A new, empty window pops up. You can then place the two windows (the shell and the file windows) side by side on your screen and get to work.
+   - You’ve been experimenting with code fragments in the shell, and you want to write a complete program. You just open a new file window as before.
+   - You want to edit a file that you saved earlier or that you got from another programmer. You launch IDLE and select the Open option from the File menu. You then browse for the file in your file system. On some systems, such as Mac OS, you can combine both of these steps into one by launching (double-clicking on) the Python program file in its directory window. Finally, you can run the command `idle3 filename` in a terminal window after navigating to the file’s directory with the appropriate system commands in the terminal window.

Like a word processor, IDLE lets you have several file windows open at the same time. Thus, you could open windows on existing program files to copy code from them to a new program in a different window. Note that your Python code in these windows is color-coded, just as it is in the shell window. IDLE also knows how to indent your code automatically when you enter selection statements and loops. Common editing commands, such as Copy/Cut/Paste and Find/Replace, are similar to those of the word