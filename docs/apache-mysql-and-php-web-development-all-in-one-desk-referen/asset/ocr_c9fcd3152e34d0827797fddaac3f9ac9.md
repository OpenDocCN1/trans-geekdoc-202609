# # Processing Directories

Perl has built-in features for processing directories. With these features, you can get the current working directory, set the current working directory, or get a list of files and subdirectories within a directory. In the following sections, I show you how to do all this with remarkable ease.

# ## Getting and setting the working directory

The easiest way to get the current working directory is by using a module called Cwd and then calling getcwd. Here's some code that does this:

```
use Cwd;
print getcwd;
```

The first line tells Perl that you want to use the Cwd module. The next line calls getcwd and prints out the results, which is the current working directory.

Setting the current working directory is even easier; you don't need to use the Cwd module. You can do it in a single line of code:

```
chdir "/tmp";
```

The chdir command is actually a subroutine, and Perl lets you call subroutines without parentheses. This line sets the current working directory to /tmp for the current program. (When Perl ends, the shell will still be in the directory it was in before the program ran.)

![](bbox=[0.153, 0.61, 0.233, 0.69])

If you're working in Windows, you can use forward slashes, /, between directory names, instead of the standard backslash. Doing so has the advantage that you don't need to double up the backslashes as in \\, because a single backslash is an escape character used in such escape sequences as \n.

# ## Obtaining a directory listing

Perl has directory listing features built right into the language. To get a directory listing, you have to open the directory. Yes, this may seem a bit odd; how do you open a directory? Don't you just open files? Well, yes, that's correct, but Perl uses an open metaphor for the directories. To open a directory, you call the opendir subroutine, passing a variable that will hold a directory handle (which is a variable you can use in later directory operations) along with the directory you want to read. From there, you call readdir over and