# Chapter 14

# Ten PHP Gotchas

# In This Chapter

+   - Recognizing common PHP errors
+   - Interpreting error messages

I guarantee that you will do all the things that I mention in this chapter. It’s not possible to write programs without making these mistakes. The trick is to find out how to recognize them, roll your eyes, say, “Not again,” and then fix them. One error message that you will see many times is

```
Parse error: parse error in c:\test.php on line 7
```

This is PHP’s way of saying, “Huh?” It means it doesn’t understand something. This message helpfully points to the file and the line number where PHP got confused. Sometimes it’s directly pointing at the error, but sometimes PHP’s confusion results from an error earlier in the program.

# Missing Semicolons

Every PHP statement ends with a semicolon (;). PHP doesn’t stop reading a statement until it reaches a semicolon. If you leave out the semicolon at the end of a line, PHP continues reading the statement on the following line. For instance, consider the following statement:

```
$test = 1
echo $test;
```

Of course, the statement doesn’t make sense to PHP when it reads the two lines as one statement, so it complains with an error message, such as the annoying

```
Parse error: parse error in c:\test.php on line 2
```

Before you know it, you’ll be writing your home address with semicolons at the end of each line.