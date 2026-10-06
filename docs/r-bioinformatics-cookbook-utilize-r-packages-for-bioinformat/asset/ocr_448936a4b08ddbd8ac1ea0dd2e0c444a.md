For this chapter, we'll need the following packages:

+   - Regular packages:
  - dplyr
  - ggplot2
  - multcomp
  - rcompanion
- GitHub:
  - danmaclean/rbioinfcookbook

In addition to these packages, we will also need some R tools such as Conda. All these will be described when needed.

# Further information

Not all the recipes in this chapter happen in R; some are command-based setups. I generally assume a bash terminal for these bits. most macOS and Linux machines will have these available in a terminal. Windows users will likely not need these specific steps, though various packages for running a Linux subsystem on Windows exist if you wish to search for them.

In R, it is normal practice to load a library and use functions directly by name. Although this is great in short interactive sessions, it can cause confusion when many packages are loaded at once and share function names. To clarify which package and function I am using at a given moment, I will occasionally use the packageName::functionName ().

Sometimes, in the middle of a recipe, I'll interrupt the code to dive into some intermediate output or to look at the structure of an object. When happens, you'll see a code block where each line begins with ## (double hash symbols). Consider the following command:

```
letters [1:5]
```

This will give us the output:

```
## a b c d e
```

Note that the output lines are prefixed with ##.