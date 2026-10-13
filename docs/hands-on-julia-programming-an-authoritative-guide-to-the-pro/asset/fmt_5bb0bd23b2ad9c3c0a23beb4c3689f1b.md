
REPL is a great utility when trying simple code segments for prototyping. However, production quality code development requires large volumes of code to be written, debugged, and verified. While an average engineer may be writing under 20 lines of code a day, the number of lines of code in maintenance is really large[1](#iftzdvy1.html#n4upl4fndk5). Unless you have informative visualization, it is not practical to be able to maintain such code. While most code is written as plaintext, source code editing requires certain aspects of the language to be understood by the editors.

1.  **Syntax highlighting**: Programmers use various indentation schemes while editing code; for example: tabs vs space, matching of delimiters like brackets, keywords like `function…end` or `try…end`. The highlighting is dynamic as well; while typing the relevant matching parenthesis is highlighted. Automatically inserting matched parenthesis is another area the editors help while typing. The highlighting can be with multiple colored texts, changing the type face to bold or italics. Some editors provide the flexibility to the users to define their own highlighting schemes.

2.  **Declaration or definition to usage matching**: When a function is being used, a programmer will like to see the definition of the function to understand how it works. In older editors, reference tags were generated as part of the compilation process with tools like `ctags` or `etags`. These tags were loaded into the editors for getting to reference locations of the functions. Some integrated development platforms like the visual studio would generate tags as part of code compilation to be able to track caller and callee graphs of the functions.

3.  **Documentation reference**: A developer will like to look at the documentation of a function before using it. While integrated document generation systems like literate programming[2](#iftzdvy1.html#n4upl4fndk6) have been in existence for several decades, help lookup of functions is particularly useful and popularized by Javadoc integration with IDEs. Visual Studio and many IDEs for Python language offer similar functionalities.

4.  **Code and data bundling**: Data used during the execution of the code like the user interface or string resources can be created using IDEs and embedded in the executables as a part of the compilation and linking process. Code and data are organized in specific directory structures and maintained in metadata called project or solution files. These metadata ensure the consistent organization of the code in the IDE.

5.  **Building of executables**: The integration of the build tools with IDEs provides a seamless build experience; for example, automation of build steps as the code is modified. The builds can cater to specific environment configurations like debug versus release executables. Invocation of specific environment start up scripts can be carried out as part of the runtime activities.

6.  **Test execution and debugging**: The code built can be run immediately with or without additional inputs to verify the code. Integrated test suites also offer complete validation of unit tests against the code modified. The ability to put breakpoints and debug each line of code execution while verifying the values of the variables are one of the most important functionalities of the IDEs.

7.  **Source control**: Many IDEs provide integration with source control. The code can be checked out from the remote repositories, modified, and checked back into the final remote repository. Some of the advanced IDEs even provided sharing of private workspaces between developers for collaborative application development ^(\[[3](#iftzdvy1.html#n4upl4fndk7),[4](#iftzdvy1.html#n4upl4fndk8)\]).

8.  **Deployment**: With cloud deployments being the standard for most production deployments, the final output needs to be integrated into an operations framework. For example, the final code needs to be packaged into deployable containers or virtual machine template so that they can be pushed onto the private or public cloud. This is part of a DevOps framework where development and operations are presented a unified view reducing costs and management overheads.

Julia is a relatively newer platform. The ecosystem for all the preceding components existed before Julia became popular as a language. Developers will like to see Julia seamlessly be used along with the tools they are most comfortable with. In the world of text editors in the UNIX environments, there is almost cult following for `vi` vs. `emacs`[5](#iftzdvy1.html#n4upl4fndk9). JuliaEditorSupport[6](#iftzdvy1.html#n4upl4fndla) organization under *GitHub* maintains integration with several of the well-known editors at differing levels of capabilities; some such editors being *Vim*, *Emacs*, *Sublime*, *Atom*, *Notepad++*, and *Eclipse*. Some of the integrations are active while many are deprecated due to lack of focus and usage. Julia IDEs are being developed for *Atom* under a project *Juno*[7](#iftzdvy1.html#n4upl4fndlb) and Microsoft **Visual Studio Code** (**VS Code**)[8](#iftzdvy1.html#n4upl4fndlc).

## Editor Integrations

With editor integrations, one can experience simple syntax highlighting, some navigation helpers, tagging of code to locate code blocks. The experience will not be IDE like. Although, some integrations are called plug-ins they are limited to simple scripts and regular expressions for syntax highlighting and tracking.

## vi and vim

`vi` has taken a significant mindshare in the UNIX community as one of the oldest multiline text editors. The extended version of `vi` called `vim` is rather the most popular flavor of the editor:

![](n4upl4fndq4.jpeg)

**Figure 12.1:** Syntax highlighting using julia-vim

The Julia plug-in for `vim`, called `julia-vim`, is a *GitHub* project[9](#iftzdvy1.html#n4upl4fndld) that can be installed in a `vim` set up for Mac OS X, UNIX, and Windows operating systems[10](#iftzdvy1.html#n4upl4fndle). The plug-in is a set of vim scripts that provide the following functionalities:

*   Syntax highlighting of Julia code, documentation, and links.
*   Integration with `ctags` for navigation.
*   Moving along code blocks, matching to code regular expressions or matched parenthesis, and so on.
*   Latex to Unicode substitution for specifying Julia variables and parameters as Unicode characters.
*   While some people have used terminal emulations with vim to use Julia REPL, it is not part of the plug-in per se[11](#iftzdvy1.html#n4upl4fndlf).
*   `vim` integration does not have any concept of a workspace or project to organize the Julia code as a package.

## Emacs

It is one of the most popular editors in the UNIX platforms like `vi`. Unlike vi, where the focus is text editing, `Emacs` is developed more like a programmer's development environment. It has integrations with terminals, build systems, source control, email, internet browsers, and so on. Although originally started as a text-based system, it now integrates into most GUIs and runs equally well on Windows, UNIX, and Mac OS X operating systems. It also ships a LISP like scripting interface (Emacs Lisp) to develop customized solutions. Hence, you will see the integration with Julia is far elaborate and evolved. Emacs also has package management systems like `GNU elpa` and `melpa` to find and use various packages needed:

![](n4upl4fndq5.jpeg)

**Figure 12.2:** julia-emacs in action
