# Chapter 5: Manipulating Files

# In This Chapter

+   - Creating a new file and writing to the file
+   - Opening a file and reading from the file
+   - Appending to an existing file
+   - Finding out information about a file
+   - Managing files and directories

If you're interested in opening and closing files, and reading and writing from files, Tcl can do all of these things. This chapter focuses on how to manipulate files. I also show you how to find out such information as whether a file exists, whether a filename is a file or directory, and much more.

# Creating a New File and Writing to It

To create and open a new file for writing, you use the open command. What you're about to read is a holdover from the ancient days of C programming, and if I had my way, things would be different. But I don't, at least not in Tcl. Thus, you have to use a command that's nothing more than a copy of the old C way of doing things.

The open command takes two parameters: the name of a file (which can also contain a path to the file) and a cryptic string that describes how you want to open the file. Suppose that you want to create a new file so that you can write to it; for that, you use a letter w (which stands for write). Here's the command:

```
open "/tmp/data.txt" "w"
```

This command creates and opens a file in the /tmp directory called data.txt and returns a value that represents the file. But you also need to store that value in a variable. Therefore, you typically put the open command inside brackets and save the results like this:

```
set myfile [open "/tmp/data.txt" "w"]
```