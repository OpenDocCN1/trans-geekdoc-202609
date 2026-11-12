+   -r determines whether you can read from the named file.

+   -w determines whether you can write to the named file.

Here's a sample program that tests out all these functions:

```
if ( -e "/tmp/a.txt" ) {
    print "Yuppers, good old a.txt is there!\n";
}

if ( -d "/tmp/subdir2" ) {
    print "Oh boy, it's true: It's a directory!\n";
}

if ( -r "/tmp/a.txt" ) {
    print "Oh yeah, I can read the file!\n";
}

if ( -w "/tmp/a.txt" ) {
    print "Yessir, I can write to the file!\n";
}
```

The first if block tests whether the file /tmp/a.txt exists. To call the function, I first typed -e, and then I put the name of the file in quotes. If the file exists, the function returns true, and the program drops down into the code block and prints out a nice message.

The next if block determines whether /tmp/subdir2 exists and is a directory. If so, the program drops into the code block and prints out an exciting message.

The third if block determines whether it can read from the file /tmp/a.txt. If so, I print out a friendly message. And finally, the fourth if block determines whether it can write to the file. If so — you guessed it — the program prints out a message.

If you're familiar with Windows, you may be surprised that there's a distinction between a file's existence and the fact that you may or may not be able to read that file. The Unix operating system has a nice permission set that allows you to specify who has rights to read a file, write to a file, and execute a file. You can turn off any or all of these permissions. If you turn off the read permission for a group of users, those users can see that the file exists, but they can't read its contents.