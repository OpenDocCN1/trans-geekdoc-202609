
and make changes where necessary. Note that you do no coding here, but you determine what the results of your program should be. You will check the program for these results during program testing. You might also write the manual for the program’s users.

- 2. **Design**—In this stage, you use the results of analysis to determine how the program will solve its assigned problem. Some coding might occur here, although design tools such as the pseudocode that you saw in Chapter 3, “Control Structures: Sequencing, Iteration, and Selection,” might also be used.
- 3. **Coding**—In this stage, you translate the results of design into the code of a programming language. Note that the same design could be coded in different languages, such as Python, Java, and C++, depending on the needs of the client and the computer system where the program will be run.
- 4. **Compilation**—In this stage, you run a program that translates your program into a form that can be run on a computer. Compilation may reveal syntax errors, which you must correct before continuing.
- 5. **Testing**—In this stage, you repeatedly run the program with different inputs and observe the outputs. If the program halts with an error message, or if the program produces unexpected outputs, you have to retreat to an earlier phase to fix the errors.

![](img/4dc3f6307b32ff815a6d58ec1c84708c_104_0.png)

Figure 4.1
The program development process.

Very rarely would you participate in all of these stages in a large programming project. In fact, you might have an entire career in just one area, as an analyst, designer, coder, or tester. But for short programs, you might do everything.

Throughout this book, you will conduct analysis, design, and testing informally. In this chapter, you will focus on the tools in IDLE for coding, compiling, and running Python programs.

## COMPOSING A PROGRAM

Thus far in this book, you have typed your Python code fragments in the IDLE shell and run them there. You have viewed the results either in the shell window or in a turtle graphics window. When you want to enter and save code that you can edit and run later, you can open a new file in IDLE and work in a separate window. In this section, you learn how to do that. You also explore the kind of structure your code should have, as a complete Python program.

### Program Edits

There are several ways to edit a program with IDLE. Each one depends on where you are in the process.

- You’re starting from scratch on a new program. You launch IDLE and then select the New File option from the shell window’s File menu. A new, empty window pops up. You can then place the two windows (the shell and the file windows) side by side on your screen and get to work.
- You’ve been experimenting with code fragments in the shell, and you want to write a complete program. You just open a new file window as before.
- You want to edit a file that you saved earlier or that you got from another programmer. You launch IDLE and select the Open option from the File menu. You then browse for the file in your file system. On some systems, such as Mac OS, you can combine both of these steps into one by launching (double-clicking on) the Python program file in its directory window. Finally, you can run the command `idle3 filename` in a terminal window after navigating to the file’s directory with the appropriate system commands in the terminal window.

Like a word processor, IDLE lets you have several file windows open at the same time. Thus, you could open windows on existing program files to copy code from them to a new program in a different window. Note that your Python code in these windows is color-coded, just as it is in the shell window. IDLE also knows how to indent your code automatically when you enter selection statements and loops. Common editing commands, such as Copy/Cut/Paste and Find/Replace, are similar to those of the word processors on your particular system. The Format menu includes some commands for formatting Python code and cleaning up indentation problems.

To save a program to a file, select the Save option from the File menu, or use the control key sequence on your particular system (Command+S on a Mac, and Ctrl+S on other systems). Python program files have a .py extension. If you don’t provide that when you save a file for the first time, Python adds it for you.

### Program Structure

As you saw in Chapter 3, some Python statements, such as loops and selection statements, have a structure. Python follows this structure to run the statements, just as you follow it to understand what they mean.

A complete Python program also has a structure—one that you employ in each program you write. Here is an example turtle graphics program that draws a pattern of hexagon shapes similar to the one you saw in Chapter 3. You can find this program in the file named samplepattern.py on the companion website (www.cengageptr.com/downloads). The next few subsections explain each part of the program’s structure.

```python
"""
samplepattern.py
Draws a pattern using a hexagon.
"""

from turtle import *

def main():
    reset()
    speed(0)
    pensize(2)
    hideturtle()
    color("blue", "yellow")    # Blue outline, yellow fill
    begin_fill()
    for count in range(10):    # Draw 10 hexagons
        for count in range(6):  # Draw each hexagon
            forward(70)
            left(60)
        left(36)                # Rotate them evenly
    end_fill()
    return "Done!"
```

```python
if __name__ == '__main__':
    msg = main()
    print(msg)
    mainloop()
```

### Docstrings and End-of-Line Comments

The first four lines at the top of this program form a string enclosed in triple-double quotes. When a string appears in Python code in this manner, it is called a docstring. Python ignores docstrings when it runs a program, but you should not ignore docstrings when you read it. This docstring tells you the name of the program’s file and summarizes what the program does. Python also displays a program’s docstrings when you ask for help with the help function in the shell. Although the docstring in this program seems to provide only trivial information, it’s a good idea to make a practice of beginning all of your programs with docstrings.

About halfway into the program code, you see several pieces of text that begin with the # character and are colored red in IDLE. Python also ignores this text, called end-of-line comments, at runtime. Once again, this information is there for you, the reader, to help you understand what’s going on at those points in the program code. You should include end-of-line comments sparingly—only when you think your code needs some clarification.

### import Statements

This program uses turtle graphics functions, so it must import them, as you did in your shell experimentation. In a program file, all import statements should appear before the rest of the program code. Note that blank lines, which Python ignores, separate the initial docstring from the import section and that section from the rest of the program code.

### The main Function

Although Python does not require it, programmers typically organize their top-level code in a main function. The next part of the example program defines this function, which is not built in to Python. Note that the function’s first line, or heading, is aligned to the left of its code, or body, by indentation. The body of the main function contains the sequence of statements that are run when the function is called. That’s all you need to know about function definitions for now.

Review the code in the main function. It sets up the initial state of the turtle so that it can draw the pattern of hexagons, and then it runs the nested for loop to do so. When the main function has finished its work, it returns the string "Done!" to its caller with a return statement.

Each turtle graphics program that you write from now on will contain a main function. You can use this first one as a template and just edit the code before the return statement.

### The if main == "__main__" Idiom

The last four lines of code in the program form a one-way if statement. This statement determines whether the code is being run as a Python program or whether it is being imported as a Python module. Once again, Python does not require this part, but it is standard practice for Python programmers.

Each Python program file can be viewed as a module. Which view Python takes of a file depends on how it’s loaded into the Python runtime system. If you were to enter the statement import samplepattern into the shell, Python would view the file as a module. You could then get help by entering help(samplepattern) or call the main function by entering samplepattern.main(). The next shell session shows the results of entering the first two commands:

```
>>> import samplepattern
>>> help(samplepattern)
Help on module samplepattern:

NAME
    samplepattern

DESCRIPTION
    samplepattern.py
    Draws a pattern using a hexagon.

FUNCTIONS
    main()

FILE
    /Users/ken/examples/samplepattern.py
```

However, if you were to run the program from an IDLE file window or from a terminal window (as described in the next section), the program itself would have to call its own main function to start things up. That’s the purpose of the one-way if statement at the end of the program.

When the program is imported as a module, Python sets the hidden module variable __main__ to the name of the module—in this case, "samplepattern". But if the program is launched from an IDLE file window or from a terminal window, Python gives this
