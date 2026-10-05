# 94

# LANGUAGE FUNDAMENTALS

# 5.1.1 Syntax Errors

We make a brief note on this since as it can be puzzling – merely a waste of time – to figure out where a missed bracket or semicolon is when writing a few q statements which go beyond the trivial. In that sense, mainstream languages do an excellent job at “spelling” out the syntax or variable names to the developer’s delight. Of course, this is not so much a feature of the language itself, rather than that of advanced IDEs, such as IntelliJ. Recently, support for q in this area has grown, and the IntelliJ plugin mentioned in the previous chapter shows a full range of syntax highlighting, variable name autocompletion and highlights for most cases of incorrect syntax, the latter continuously improving with each release. The usual shortcut for function definition and usages are also there, making navigating your codebase as it grows more productive, which arguably means that a large codebase is very easy to find and navigate – especially “large” in q means a few hundred to thousands lines of code, instead of tens or hundreds of thousands of code in most other languages.

As mentioned, due to the very interactive nature of the language, even when using an IDE as IntelliJ or a GUI such as QPad, one finds frequently interacting with the q console directly and is still the “go-to” place once we’re past the simple syntax errors and our code breaks mid-execution.

# 5.1.2 Runtime Errors

In this section, we review the debugging options available. The two reasons we need to debug the code if it breaks with an exception or if the output of the function is not as expected, the latter case being rather common as the computer does what we tell it to do, not what we think it to do.

First of all, let us define what “breaks” means. An interruption to the normal flow of execution, an error signal, or what is known in layman terms as an “exception” is denoted in q with the rather laconic single ‘ quote ', usually followed by a – naturally – explanation of the error. A break will result in a q script executing with an error due to its inability to load, or a function call within a process being interrupted by an error.

Let us start with the ubiquitous case of the code-breaking with an exception. The following function definition:

```
wrongFunction:[x;y]
add: x + y;
addmore: add + 50;
z+3;
```