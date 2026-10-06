# Chapter 11: Working with Files and Directories

![](bbox=[0.214, 0.087, 0.856, 0.483])

Figure 11-5

# ## Examining the Editor Code

The text editor demonstrates many of the functions you've learned in this chapter, and also illustrates some coding techniques. In the following sections you explore the workings of each part of the text script, and take a look at how the parts fit together to make the application work.

# ## The Main Logic

The script kicks off by defining the path to the folder that will hold the text files. It does this using a constant called PATH_TO_FILES:

```
define("PATH_TO_FILES", "/home/matt/sandbox" );
```

The user will create and edit all his text files in this folder. For security reasons it's important to make sure that the user isn't allowed to create or modify files outside this folder, and you see how this is done in a moment.

329