
actually means asking the computer to do the following:

`h = round(sqrt(round(round(x * x) + round(y * y))))`.

That can be written more concisely using the overbar notation ([Section 3.6](#chapter3.xhtml#sec3_6)):

$$h = \overline{sqrt(\overline{\overline{x\cdot x}+\overline{y\cdot y}})}.$$

Whatever the rules for a computer language, if it supports posits, then the use of fused operations or non-fused operations must be visible in the code, never done covertly. We will see later why this prevents disasters.

The Posit Standard requires support for the functions you find on a scientific calculator: logs, exponentials, trig and inverse trig functions. We stopped short of mandating support for some of the more sophisticated functions like Bessel functions. Those can always be added to a future version of the Posit Standard.

While posits can replace floats in a program, it seems likely that both formats may coexist for a while, and there needs to be a way to convert posits to IEEE 754 floats and vice versa. So, the Posit Standard specifies how to do that for the various rounding modes and exception types of IEEE 754 floats.

The Standard also solves a subtle and long-standing issue: How should an indeterminate result (`NaR` for posits, `NaN` for floats) be converted into an integer, and back? Posits can do it properly, preserving the fact that a `NaR` result occurred.

It is extremely easy to convert between two posit precisions with the same exponent size `eS`, much like converting between two integer precisions. There is no need to decode the number. This is one of the reasons that Draft Posit Standard 4.0 changed to specifying that `eS` = 2 for any precision. Earlier Draft versions required that the precisions be restricted to `n` = 8, 16, 32, 64, … with corresponding `eS` values `eS` = 0, 1, 2, 3, …, in other words, `eS` = log[2](`n`) - 3. The ratified version of the Posit Standard described here does not restrict `n` that way. Strange precisions like 5-bit posits have proved useful for the *inference* task of AI, for example. A fixed `eS` also simplifies the work of the hardware designer.

The approach to explaining when any operation or function should return `NaR` is to apply a single mathematical principle, uniformly. This contrasts with using different rules for different functions, as is presently done for IEEE 754.

Because this is not a language standard, nor does it say how the functions in a math library are to be labeled, we refer to well-known math functions but only describe how they should behave, not how they should be spelled or parsed. A computer language will of course allow the writing of something like `a = b + c`, not the form `a = addition(b, c)` used in the Posit Standard.

There are no “recommendations” in the document because following recommendations or not following them leads to irreproducibility. Including recommendations makes a document a guideline, not a standard.

If someone wants to build a computing environment for 9-bit posits because they work well for AI, say, there is no need to support any other precision to be posit-compliant. The entire environment could be done in software, written using native integer operations, or (what seems more likely) the kernel operation of multiply-accumulate would be done with hardware that is as fast as possible, and most of the lesser-used operations like logarithms could be done in software.

## 5.3 Definitions Section of the Posit Standard

[Chapter 3](#chapter3.xhtml) introduced the concept of “ghost bits” beyond the end of a posit, which always have value `0`. Here is another figure illustrating the concept, where an “`x`” is an explicit bit and may be a `0` or a `1`:

![](images/pg107_1.jpg)

As the figure shows, while ghost bits are always `0`, they can play different roles depending on the explicit bits. Case 1 is the two exception values, either zero or `NaR` depending on the value of the sign bit. Case 2 is `maxPos` if the sign bit `x` is `0`, or −`minPos` if `x` is `1`. Case 3 is the “Twilight Zone” where exponent bits can be pushed off the end of the explicit bits by the length of the regime. Case 4 is the normal situation where the ghost bits are like the unexpressed bits of a decimal like “3.75”, which is the same thing as “3.7500000". The term “ghost bit” helps explain posit format, but for the sake of brevity, that phrase is not defined in the Posit Standard.

[Chapter 4](#chapter4.xhtml) disparaged the design of a number format by carving a word into bit fields resembling scientific notation. Posit arithmetic was invented by the geometric reasoning of [Chapter 1](#chapter1.xhtml) (the ring plots and the projective reals), which then *dictated* the bit fields, including one with a new and variable-length meaning, the regime.

For posits, an “exception” does not mean “throw control to an exception handler.” It means the software or the circuit must do something different since the regime value, –∞, is not representable with positional notation. Although the formula for zero correctly works out to `2^(-∞)`, obviously the way to actually handle it is with a conditional branch for the case of all bits `0`.

For the case of `NaR`, this definition and its footnote represent one of the most profound departures from IEEE Std 754, which specifies that the arithmetic must also play the role of a debugger, constantly monitoring calculations for bad behavior and then either halting the calculation (“signaling NaN”) or continuing (“quiet NaN”). But that is what debugging tools do; they can set a breakpoint when a particular value occurs as a result. Once a program is debugged, you can turn off “debug mode” and compile it for maximum speed; that is standard practice, because compiling to enable debug mode can make a program many times slower than the optimal compilation. With IEEE floats, however, you have a debugger you cannot turn off. It spends energy on every clock cycle to check for exceptions even after the programmer has guaranteed that they cannot occur.

A side bit of history, while we are on the subject of bugs:

This is a fun story, and Grace Hopper later became an Admiral and one of the most respected computer pioneers of the 20th century.

![Grace Hopper (1906–1992), inventor of the concept of a programming language](images/pg108_1.jpg)

Grace Hopper (1906–1992), inventor of the concept of a programming language

Years before IBM introduced Fortran, she conceived of programs written in a high-level language that would run on any computer, and built a language environment that later evolved into COBOL.

We even have the actual moth, taped to a logbook that recorded the event:

![Literally the first computer bug](images/pg109_1.jpg)

Literally the first computer bug

The etymology (and entomology) is not quite right, however. Thomas Edison, decades earlier, used to write about getting the “bugs” out of his electrical inventions, so that slang was already in popular use. The log entry shows that they found it quite funny that the bug turned out to be, literally, a bug. It almost certainly is not Grace Hopper's logbook, but her team found it amusing and she (and her team) deserve credit for spreading the term “debuggers” for the software tools used to find errors in programs.

In preventing a program from stumbling into indeterminate nonsense, there are three lines of defense:

1.  The programmer is careful to think about all the possible ways things could go wrong, and makes sure the program handles exceptions in an intelligent way. Tools like debuggers and automated language analyzers assist the programmer with this task. Good compilers also issue warnings when the software does something dubious, like using a variable before it has been assigned a value.
