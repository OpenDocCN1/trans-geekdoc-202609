# Core PHP Programming

```
//word not recognized, get
suggestions $suggestion =
aspell_suggest($aspell_link, $token);

print("<B>Unrecognized word:</B>\n$token<BR\n");

while (list($index, $word)) {
{
print("\$val<BR\n");
}
}
print("<BR\n");
}
?>
```

# boolean aspell_check(integer link, string word)

The aspell_check function returns true if the word argument is found in the dictionary specified by the link argument. This function attempts to trim extraneous characters before validating the spelling.

# boolean aspell_check_raw(integer link, string word)

This function behaves like aspell_check, except that it makes no attempt to trim extraneous characters.

# array aspell_suggest(integer link, string word)

The aspell_suggest function returns an array of spellings for a word. The link argument is an integer returned by the aspell_new function.

# COM

The component object model (COM) is a framework that allows sharing of executable modules without recompiling. If you have used Windows for any time at all, you are aware of dynamic-link libraries (DLLs), collections of functions a program can load on demand. Many programs can share a DLL, which goes a long way toward the principle of reuse. Unfortunately, DLLs that work with some programming languages don't