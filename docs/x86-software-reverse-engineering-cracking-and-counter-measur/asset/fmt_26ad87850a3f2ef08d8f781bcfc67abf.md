
Because of time and space constraints, exploring all of these debuggers is infeasible in this book. Immunity was selected because of its popularity for reverse engineering and exploit development. However, it's important to remember that all of these debuggers have similar features, and skills learned in one will often translate over to others.

[Figure 10.22](#c10.xhtml#c10-fig-0022) shows how Immunity looks in Windows. From the top-left and moving clockwise, the four windows show the program's disassembly, registers, stack, and memory.

### Immunity: Assembly

[Figure 10.23](#c10.xhtml#c10-fig-0023) shows a program's disassembly in Immunity. Note that it shows the memory address, machine code, and x86 assembly.

  ![Figure 10.22: Immunity debugger window](images/c10f022.png)

[**Figure 10.22**](#c10.xhtml#R_c10-fig-0022): Immunity debugger window

![Figure 10.23: Assembly code in Immunity debugger](images/c10f023.png)

[**Figure 10.23**](#c10.xhtml#R_c10-fig-0023): Assembly code in Immunity debugger

To select a line of code, click it. Once a line is selected, Immunity offers various keyboard shortcuts, including the following:

*   **;**: Add a comment to the selected line. This is the most important part of reverse engineering; it helps you keep track of your work.

*   **ctrl-a**: Auto-analyze the program. Immunity can do a fairly good job of adding comments and guessing function parameters.

*   **<enter>**: Navigate to the selected function. For example, if you see the assembly `call 0x1234` and want to find out what the function at 0x1234 does.

*   **-**: Go back to the previous location. For example, after you've analyzed function 0x1234 and want to return to where you were.

*   **+**: Go to the next location (after pressing -). For example, if you returned to the calling function with -, but then want to go back to function 0x1234.

*   **ctrl-r**: Find cross-references to the selected line. For example, if you have a string selected in the memory dump window and want to know who uses that string; or if you have the top of a function selected in the disassembly and want to find out who calls that function.

*   **Double-click address**: Set a debugging breakpoint at this address.

### Immunity: Modules

In Immunity, you can load the list of executable modules by pressing the e button. This shows all the code—including dynamically loaded libraries—that you can debug, as shown in [Figure 10.24](#c10.xhtml#c10-fig-0024). After opening the list, you can double-click a module to go to that code.

When you start Immunity, see what module you are currently looking at by checking the *`eip`* register. In nearly every case, you will want to start by debugging the main executable, not a shared library like `ntdll`. You can use the modules window to switch to the main executable.

### Immunity: Strings

It is often useful to find what code is using a certain string in the executable. To find all the strings that a program is using, right-click and select Search For ➪ All Referenced Text Strings, as shown in [Figure 10.25](#c10.xhtml#c10-fig-0025).

In the strings window, right-click and select Search For Text to find a specific string, as shown in [Figure 10.26](#c10.xhtml#c10-fig-0026). Then, right-click again, and select Search For Next to find the next reference to that string. You can double-click a string's address to go to the location where it is used in the disassembly.

  ![Figure 10.24: Executable modules in the Immunity debugger](images/c10f024.png)

[**Figure 10.24**](#c10.xhtml#R_c10-fig-0024): Executable modules in the Immunity debugger

![Figure 10.25: Strings in Immunity debugger](images/c10f025.png)

[**Figure 10.25**](#c10.xhtml#R_c10-fig-0025): Strings in Immunity debugger

![Figure 10.26: String references in Immunity debugger](images/c10f026.png)

[**Figure 10.26**](#c10.xhtml#R_c10-fig-0026): String references in Immunity debugger

### Immunity: Running the Program

Click the play arrow to launch the executable under the debugger, as shown in [Figure 10.27](#c10.xhtml#c10-fig-0027). Execution can be stopped by clicking the X to the left of the play arrow or can be paused using the pause button to its right. Execution can be restarted via the button with two left-facing arrows.

  ![Figure 10.27: Launching an executable in Immunity debugger](images/c10f027.png)

[**Figure 10.27**](#c10.xhtml#R_c10-fig-0027): Launching an executable in Immunity debugger

After execution has been halted by a breakpoint or the pause button, you can click Step Into to progress the program one instruction, as shown in [Figure 10.28](#c10.xhtml#c10-fig-0028). Alternatively, if you are stopped on a function call but already know or do not care about what the function does, click overstep Over, as shown in [Figure 10.29](#c10.xhtml#c10-fig-0029), to continue debugging after the function returns.

![Figure 10.28: Single-stepping in Immunity debugger](images/c10f028.png)

[**Figure 10.28**](#c10.xhtml#R_c10-fig-0028): Single-stepping in Immunity debugger

### Immunity: Exceptions

Many applications generate exceptions as part of normal execution. For example, a `try {} except {}` block will generate an exception if anything goes wrong in the `try` block. As a debugger, dynamic analysis tools like Immunity typically intercept the exception first to see if you want to do anything with it.

But for reverse engineering, you generally don't want to interfere with normal execution. Instead, you want to let the application handle the exception the way it normally would. This means you almost always want to pass the exception from the debugger to the application.

As shown in [Figure 10.30](#c10.xhtml#c10-fig-0030), exceptions are reported at the bottom of the Immunity window, but each debugger is slightly different. In Immunity, press Shift+F9 to pass the exception and continue execution.

  ![Figure 10.29: Stepping over instructions in Immunity debugger](images/c10f029.png)

[**Figure 10.29**](#c10.xhtml#R_c10-fig-0029): Stepping over instructions in Immunity debugger

![Figure 10.30: Exceptions in Immunity debugger](images/c10f030.png)

[**Figure 10.30**](#c10.xhtml#R_c10-fig-0030): Exceptions in Immunity debugger

### Immunity: REwriting the Program

Immunity has many features to aid in the development of patches to modify software behavior. For the purposes of software cracking, this includes making program edits to remove key checks, nag screens, etc.

In your first cracks, you will use the process of “`nop`ing” out code to remove it from the program. This involves replacing program instructions with `nop` instructions.

To do so in Immunity, first select the instruction(s) that you want to remove. Then, right-click and select Binary ➪ Fill With NOPs, as shown in [Figure 10.31](#c10.xhtml#c10-fig-0031).

This will replace the selected instruction(s) with a series of `nop`s, as shown in [Figure 10.32](#c10.xhtml#c10-fig-0032).

![Figure 10.31: noping out code in Immunity debugger](images/c10f031.png)

[**Figure 10.31**](#c10.xhtml#R_c10-fig-0031): `nop`ing out code in Immunity debugger

![Figure 10.32: noped code in Immunity debugger](images/c10f032.png)

[**Figure 10.32**](#c10.xhtml#R_c10-fig-0032): `nop`ed code in Immunity debugger

After modifying the program, test the patch by rerunning the program. If you patched the correct portion of code, you should find that the nag screen (key check, etc.) has disappeared.

However, if the patch crashes or failed to remove your target, you can easily revert your changes and try again. To do so, select the patch button to bring up the patches window. Then, right-click your patch and select Restore Original Code, as shown in [Figure 10.33](#c10.xhtml#c10-fig-0033), to revert your patch and try again.
