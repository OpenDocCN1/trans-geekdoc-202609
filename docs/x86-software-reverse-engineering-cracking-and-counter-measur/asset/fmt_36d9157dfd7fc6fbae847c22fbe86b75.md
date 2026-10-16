
In [Figure 10.18](#c10.xhtml#c10-fig-0018), the CAPTION string determines the title on the application window. Change this string to rebrand the application as your own.

After changing the CAPTION, click the green arrow button shown in [Figure 10.19](#c10.xhtml#c10-fig-0019). This will compile the modified Calculator application.

After the application has been compiled, the updated version of the window should be shown in the window preview. This should include the modified caption, as shown in [Figure 10.20](#c10.xhtml#c10-fig-0020).

Compiling the application doesn't automatically save the modified version. To do so, select File ➪ Save, as shown in [Figure 10.21](#c10.xhtml#c10-fig-0021).

![Figure 10.18: Calculator window in Resource Hacker](images/c10f018.png)

[**Figure 10.18**](#c10.xhtml#R_c10-fig-0018): Calculator window in Resource Hacker

![Figure 10.19: Compiling the modified application](images/c10f019.png)

[**Figure 10.19**](#c10.xhtml#R_c10-fig-0019): Compiling the modified application

![Figure 10.20: Modified window in Resource Hacker](images/c10f020.png)

[**Figure 10.20**](#c10.xhtml#R_c10-fig-0020): Modified window in Resource Hacker

![Figure 10.21: Saving the modified application in ResHack](images/c10f021.png)

[**Figure 10.21**](#c10.xhtml#R_c10-fig-0021): Saving the modified application in ResHack

At this point, you've successfully rebranded Windows Calculator. For more of a challenge, try the following:

*   Use Resource Hacker to resize the window to accommodate your new name.

*   Modify the available buttons.

*   Modify the calculator background.

*   Open and edit other programs in your VM.

## Patching

Patching involves modifying a compiled binary to modify code affecting its execution. Depending on the situation, sometimes the easiest thing to do is patch an application to circumvent its security.

### Patching vs. Key-Genning

In some cases, advanced integrity checks or obfuscation might make patching difficult. For example:

*   Patching an encrypted/packed program on disk is not feasible.

*   Patching around dynamic integrity checks (e.g., continuously validated checksums) may be too cumbersome.

*   The logistics of distributing a patched executable may not be desirable.

In these situations, you may choose to fall back on key generators instead. Otherwise, patching a program to remove its key checks (or any other logic you want to avoid) is often the easier approach, when possible.

### Where to Patch

Patching can be done in two different places: in memory or on disk.

Patching in memory modifies the machine code in memory. This is useful for reverse engineering attempts because you may need to try dozens (or hundreds…or more…gasp) of things before one works. In-memory patching affects only the current execution of the application. Each time you restart the application, any in-memory patching will be lost.

Patching on disk modifies the machine code in the compiled binary. This is useful once you know what works and affects all future executions of the application. It makes the modifications persistent and will be there every time the application is launched.

### NOPs

Recall the instruction `nop`. It is a one-byte instruction (`0x90`) that does nothing.

When patching applications, it is critical to not move the code. In fact, modifying the size or simply deleting code will crash the application. To remove sections of code yet maintain the same size, fill the space with `nop`s.

For those of you who are curious why simply deleting code doesn't work, there are many factors to this, but the most important is that some x86 code is relative and some of it is absolute references. Looking at the relative case first: this means some code translates to relative things like “jump forward 40 bytes from where I am now.” In cases like this, if you remove code between the jump and its destination 40 bytes away, you've messed up the jump. It will continue to jump 40 bytes ahead, except that now it may land in the middle of an opcode or skip critical instructions, which then results in a crash. If the code you remove is outside of that 40-byte bubble and the jump forward 40 bytes still lands in the same spot, then it would have no effect.

Now, consider absolute references. These types of references would look like “use the data value at address 0x1234567.” If you remove code anywhere in the binary before that address, you've caused everything to shift. So, when any absolute reference goes to grab its values or perform an absolute jump, all of the locations will be wrong, even if all you did was remove 1 byte from the binary.

This means relative references are affected only by adding/removing bytes if they occur in between where the reference is made and the destination. However, all absolute references are destroyed if you shift the application even by 1 byte. This is why it's critical in patching to maintain the size (unless of course causing everything to crash is your goal, in which case smash away!).

Circling back to `nop`, if you want to remove a piece of code, such as causing software to skip a key checker, instead of deleting the code, you simply replace it all with `nop`s. This maintains the application's byte alignment but causes nothing to happen when it reaches the undesirable code.

## Other Debuggers

For reverse engineering with dynamic analysis on Windows, there are numerous popular choices. Here are a few:

*   OllyDbg

*   Immunity

*   x64dbg

*   WinDbg

Which of these to use depends on the situation and user preference. All of them have similar features, and skills in one typically translate to the others as well. You'll dip your toes into a few different pieces of software throughout the book; the goal is to give you a taste of many so you can get a feel for when each is useful.

### OllyDbg

OllyDbg is an immensely popular and powerful debugger. While most debuggers focus on debugging, Olly has extended features, including the following:

*   Extensibility, plugins, scripting

*   Execution tracing system

*   Code patching features

*   Automatic parameter descriptions for most Windows functions

*   Emphasis on binary code analysis (i.e., not based around source debugging)

*   Small and portable

These features make OllyDbg excellent for the following:

*   Writing exploits

*   Analyzing malware

*   Reverse engineering

However, while OllyDbg is a powerful and popular tool, it does have its limitations. One of these is that it works only for 32-bit executables, which admittedly are a dying breed but not dead yet.

The other is that the OllyDbg interface often takes some getting used to and does not feel robust or intuitive at first. However, you should definitely stick with it, as it is a powerful dynamic analysis tool.

### Immunity

Immunity is a fork of OllyDby, meaning that it has many of the same capabilities. It also introduces many additional features that make it popular for exploit developers, such as support for Python scripting.

However, like OllyDbg, Immunity can be used only to debug 32-bit executables. Also, it inherits OllyDbg's unintuitive user interface.

### x86dbg

x86dbg is a replacement for OllyDbg that supports both 32-bit (x86dbg) and 64-bit (x64dbg) applications. This wider support means that it is commonly the tool of choice when reversing or debugging 64-bit applications.

### WinDbg

WinDbg is a debugger that is universally applicable, has strong support, and offers excellent debugging symbol support (but which is less useful with RE). However, it has a debugging focus and lacks some features of RE-focused tools.

## Debugging with Immunity
