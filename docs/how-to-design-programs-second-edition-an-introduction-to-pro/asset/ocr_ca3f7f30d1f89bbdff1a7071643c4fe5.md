# ## 20.2 Refining Data Definitions

Exercise 329 lists some of the questions that users routinely ask about directories. To answer such questions, the computer’s operating system provides programs that can answer them. If you want to design such programs, you need to develop a data representation for directory trees.

In this section, we use iterative refinement to develop three such data representations. For each stage, we need to decide which attributes to include and which to ignore. Consider the directory tree in figure 123 and imagine how it is created. When a user first creates a directory, it is empty. As time goes by, the user adds files and directories. In general, a user refers to files by names but mostly thinks of directories as containers.

**Model 1** Our thought experiment suggests that our first model should focus on files as atomic entities with a name and directories as containers. Here is a data definition that deals with directories as lists and files as strings, that is, their names:

```
; A Dir.v1 (short for directory) is one of:
; -- '()
; -- (cons File.v1 Dir.v1)
; -- (cons Dir.v1 Dir.v1)

; A File.v1 is a String.
```

The names have a .v1 suffix to distinguish them from future refinements.

+   **Exercise 330.** Translate the directory tree in figure 123 into a data representation according to model 1.

+   **Exercise 331.** Design the function how-many, which determines how many files a given Dir.v1 contains. Remember to follow the design recipe; exercise 330 provides you with data examples.

**Model 2** If you solved exercise 331, you know that this first data definition is still reasonably simple. But, it also obscures the nature of directories. With this first representation, we would not be able to list all the names of the sub-directories of some given directory. To model directories in a more faithful