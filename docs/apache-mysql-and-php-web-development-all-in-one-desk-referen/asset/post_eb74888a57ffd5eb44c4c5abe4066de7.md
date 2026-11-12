
## Keeping variables local to the subroutine

If you’re inside a subroutine and you create a variable, that variable will be accessible to parts of the program outside the subroutine. For example, if you have a subroutine called Bank that creates a variable called $amount, that variable will still exist after you call the subroutine, like so:

```
sub Bank {
  $amount = $_[0];
  print "Wow! Depositing $amount! I'm rich!\n";
}

Bank(13527985);
print "The amount is still $amount.\n";
```

When you run this code, you see the following output:

```
Wow! Depositing 13527985! I'm rich!
The amount is still 13527985.
```

Even though the Bank subroutine created a variable called $amount, that variable is now available to the rest of the program. Generally computer scientists (and normal people as well) consider this a bad thing: When a subroutine (or function, as other languages call it) creates a variable, that variable should be available only to the subroutine itself. When the subroutine ends, the variable should go away. This is called information hiding, which is a good thing: Only make information available where it is needed, so the rest of the program doesn’t have to worry about it.

![](img/3f967ab8a8fddc723173059f56621648_181_0.png)

When a subroutine creates a variable and the variable exists only while the subroutine is running, we say that the variable's scope is the subroutine. The word scope refers to the part of the program where the variable exists.

If you want to limit a variable's scope to the subroutine itself (which is called keeping a variable local to the subroutine), you can use the word my. The following code is the same as the preceding example code, except the scope is now limited:

```
sub Bank {
  my $amount = $_[0];
  print "Wow! Depositing $amount! I'm rich!\n";
}

Bank(13527985);
print "The amount is still $amount.\n";
```

Inside the function, when I created the variable $amount, I put the word my in front of it. In doing so, I'm telling the Perl system that the variable's scope is limited to the function — that is, the variable is local to the function.

Here's the output from the program:

```
Wow! Depositing 13527985! I'm rich!
The amount is still .
```

(Note: I'm running this without the -W option because otherwise you'll get some errors; Perl knows that I'm trying to fake it out here.) The final line of the program doesn't know about the $amount variable in the subroutine and prints nothing. The subroutine's $amount variable is gone when the subroutine finishes.

When I try to access the $amount variable outside the subroutine, I'm actually using a separate variable also called $amount. That's the interesting thing about the my word: You can use it to create a separate variable in each subroutine and use whatever names you want without having to worry about the variable name being in use elsewhere in the program. Take a look at the following code, which has two subroutines, each with a separate variable called $amount, as well as a main section that also has its own $amount variable:

```
sub Bank {
	my $amount = $_[0];
	print "Wow! Depositing $amount! I'm rich!\n";
}

sub Grocery {
	my $amount = $_[0];
	print "I am about to spend $amount in groceries!\n";
}

$amount = 10000;
print "I have $amount dollars in my pocket.\n";
Bank(50);
Grocery(25);
print "The amount in my pocket is still $amount!\n";
```

The $amount variable inside the Bank subroutine is a separate $amount variable from the one in the Grocery subroutine, and these are both separate from the main $amount variable. Here's the output:

I have 10000 dollars in my pocket.
Wow! Depositing 50! I'm rich!
I am about to spend 25 in groceries!
The amount in my pocket is still 10000!

![](img/3f967ab8a8fddc723173059f56621648_183_0.png)

If you're familiar with other languages, the idea that variables are global by default will seem strange. In Perl, if you declare a variable inside a subroutine, by default that variable becomes part of the global scope. To prevent this from happening, declare the variable using the my keyword.

## Returning data to the caller

Although passing a single or multiple items to a subroutine is exciting, the most amazing thing you can possibly imagine is for a subroutine to return data back to the caller. If you haven't experienced this, then your life has been far from complete.

Just as you can pass a set of parameters to a subroutine as a list, you can pass a set of data back out of the subroutine as a list. Or, you can pass a single item of data, which is a scalar.

Take a look at this example.

```
sub Multiply {
    $first = $_[0];
    $second = $_[1];
    return $first * $second;
}

$total = Multiply(10,20);
print "The total is $total\n";
```

The Multiply subroutine accepts two parameters. It then multiplies these two parameters and returns the single number as a scalar. In the main code, the call to the subroutine is on the right side of an equal sign. That means that when the subroutine returns, you get back a single number, and you store that number in the variable called $total. Then in the next line, you print out that number.

Here's the output from this program:

The total is 200

The subroutine returned a value, 200, and you were able to store that value inside a variable.

You don't have to return just a scalar. You can also return an entire list, as in this example:

```
sub Sequence {
    $start = $_[0];
    return ($start, $start+1, $start+2, $start+3);
}

@mylist = Sequence(10);
foreach (@mylist) {
    print "$_\n";
}
```

Here's the output from this program:

```
10
11
12
13
```

## Chapter 5: Processing Text Files and Directories

### In This Chapter

- Getting and setting the working directory
- Reading directory listings
- Opening and reading from the file
- Removing newline characters (chomping)
- Writing and appending to a file
- Deleting a file

One of the most important uses of Perl is the processing of text files. Although Perl allows you to do much more than this, processing text files is one of its strong points and is among its most common uses.

In this chapter, I show you the different ways to open files, read and process the contents of those files, write new text files, and manipulate directories of files. Note, however, that in order to get the most out of Perl, you must use various _modules_ in Perl. Modules are additions to Perl that make life easier. Over time, Perl users found the need for additional functionality that the language did not offer, so they wrote these additional parts themselves.

The samples in this chapter that use an extra module have the word `use` at the start of the code, followed by the name of the module. To use the module, all you have to do is type in the code I provide.

![](img/3f967ab8a8fddc723173059f56621648_186_0.png)

In this chapter, I show you the basics of reading and writing text files, in addition to processing directories. Generally, when reading files, you will want to process the data using _regular expressions_. See Book VII for further discussion of the topic of processing text files with regular expressions.

## Processing Directories

Perl has built-in features for processing directories. With these features, you can get the current working directory, set the current working directory, or get a list of files and subdirectories within a directory. In the following sections, I show you how to do all this with remarkable ease.

### Getting and setting the working directory

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

![](img/3f967ab8a8fddc723173059f56621648_187_0.png)

If you're working in Windows, you can use forward slashes, /, between directory names, instead of the standard backslash. Doing so has the advantage that you don't need to double up the backslashes as in \\, because a single backslash is an escape character used in such escape sequences as \n.

### Obtaining a directory listing

Perl has directory listing features built right into the language. To get a directory listing, you have to open the directory. Yes, this may seem a bit odd; how do you open a directory? Don't you just open files? Well, yes, that's correct, but Perl uses an open metaphor for the directories. To open a directory, you call the opendir subroutine, passing a variable that will hold a directory handle (which is a variable you can use in later directory operations) along with the directory you want to read. From there, you call readdir over and
