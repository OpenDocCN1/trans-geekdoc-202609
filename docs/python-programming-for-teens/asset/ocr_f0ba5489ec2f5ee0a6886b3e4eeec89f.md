Another major type of software is called *applications software*, or simply applications (or apps on handheld devices). An application is a program that is designed for a specific task, such as editing a document or displaying a web page. Applications include web browsers, word processors, spreadsheets, database managers, graphic design packages, music production systems, and games, among many others.

As you have learned, computer hardware can run only instructions that are written in binary form—that is, in machine language. Writing a machine language program, however, would be an extremely tedious, error-prone task. To ease the process of writing computer programs, computer scientists have developed high-level programming languages for expressing programs. These languages resemble English and allow authors to express their programs in a form that they and other people can understand.

As you have been doing thus far in this book, you start by writing high-level language statements in a text editor. You then run another program called a *compiler* to convert the high-level program code into runnable code. (When you press the F5 key in Python, that’s what happens.) Because it is possible for you to make grammatical mistakes even when writing high-level code, the compiler checks for syntax errors before it completes the translation process. If it detects any of these errors, the compiler alerts you via error messages.

If the translation process succeeds without a syntax error, the program can be executed by the runtime system. The runtime system might execute the program directly on the hardware or run yet another program called an *interpreter* or *virtual machine* to execute the program. Figure 4.5 shows the steps and software used in this process for a Python program.

![](bbox=[0.05, 0.7, 0.9, 0.88])

Figure 4.5
Software used to compile and run a program.