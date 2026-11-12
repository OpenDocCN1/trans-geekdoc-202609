This particular escape character denotes a newline. Now, to illustrate the difference between the single- and double-quote methods of specifying strings, try rewriting each of the two preceding lines of code with a \n at the end, followed by a few more characters:

```
print 'Where did all the time go?<BR>\n...';
print "Where did all the time go?<BR>\n...";
```

These two lines of code look similar, but they produce different output in the resulting HTML. Running these two lines produces the following output:

```
Where did all the time go?<BR>\n...Where did all the time
go?<BR>
...
```

See what happened? The \n inside the single quotes resulted in the literal characters \n appearing in the output. However, the double quotes caused the PHP processor to convert the \n to a newline.

If you plan to use escape characters in your strings, or if you plan to embed variables (described in the section, “Embedding variables [and printing them, too],” later in this chapter), you must use double quotes. These characters and variables are then converted properly. However, if you want your text to print exactly as is — backslashes, dollar signs, and all — then use single quotes.

You're rolling along, having a great day, and suddenly you're hit with a major bug where you're seeing a bunch of \n's appear in your Web browser. Most likely the problem is that you accidentally used single quotes when you should have used double quotes. I speak, ahem, from experience. (Yup.)

If you're running a Web site that receives lots of hits, and you're looking for every possible way to maximize the speed, always use the single-quote style strings except when you need to embed either an escape sequence or a variable in the string. The PHP processor grinds though a single-quote string a bit faster than through a double-quote string.

# Specifying with heredocs

The third way to specify strings may look a little odd if you’re coming from the perspective of a traditional programming language, such as C++ or Pascal. You can use a string-specifying method called heredoc. The idea with heredoc is that you type into the code file exactly what you want your lines of strings to look like. Here’s an example: