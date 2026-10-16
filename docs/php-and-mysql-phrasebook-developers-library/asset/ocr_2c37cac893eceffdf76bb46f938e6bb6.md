![](bbox=[0.17, 0.07, 0.72, 0.57])

Figure 7.1 Allowing the IIS user to access a file or directory

# Reading from Files

```
echo file_get_contents('file.txt');
```

To read data from a file, PHP offers several possibilities. Probably the easiest way is to read it all at once and then output it to the user.

The function file_get_contents() returns the contents of a file (or stream) as a string so that it all can be processed further. The following code reads in a file called file.txt and prints out its contents. This function is binary safe, and that's why no file mode can (or has to) be used: