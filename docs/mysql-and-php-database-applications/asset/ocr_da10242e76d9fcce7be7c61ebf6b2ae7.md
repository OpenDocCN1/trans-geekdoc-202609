# Chapter 7: Writing Organized and Readable Code

```
{
echo "Between 50 and 99.";
}
```

> Tip Are you getting a parse error you can't identify? Make sure you have an identical number of opening and closing curly braces and parentheses. If you have,say, five closing curly braces in a page and only three opening, you haven't closed one of your code blocks.

# Function calls

Indenting should not stop at code blocks. Often you will need to use nested function calls or complex variables that take up several lines. You will be much happier in your coding life if you use indents in these situations. Take a look at the following, which is borrowed from the Catalog application.

```
$file_ext = strtolower(
 substr($file
```

```
$file_ext = strtolower(substr($file,strpos(\$file,".")));));
```

Or you may find this easier to read. A lot of things we'll talk about this chapter are matters of personal preference. The important thing is that you spend a lot of time considering how to make your code as readable as possible.