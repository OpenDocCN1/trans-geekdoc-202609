# Part II: Solutions

Because the format of the command's output is intended for the command line

Windows system functions output their results in cp866 because by default the command line uses this encoding for backward compatibility with earlier versions of console applications. In Windows XP, it is possible to change the encoding using the chcp command. If this command is called without parameters, it returns the current code page (Listing II.1.2).

# Listing II.1.2. Displaying the current encoding

```
<?php
echo `chcp`;
?>
```

As a result of the operation of the script shown in Listing II.1.2, the browser displays the following: Current code page: 866. If you pass the code page name to the chcp command, it will change the current code page to the specified one. Thus, the program in Listing II.1.1 can be rewritten as shown in Listing II.1.3.

# Listing II.1.3. Changing the code page using the chcp system command

```
<?php
echo "pre>
```