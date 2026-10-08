# Debugging and Global Variables

Professional PHP programmers don't use a simple text editor like PSPad to develop their code. Instead they install what's known as an IDE, or Integrated Development Environment, on their PC. This includes PHP, a web server, and a sophisticated debugger to help in solving problems.

There are various PHP IDEs on the market, some of which are very reasonably priced and some of which are most definitely not. However, they are best avoided by all but the most serious PHP developers, because they're large, complex, and require you to install things on your PC (specifically PHP and a web server) which pose a serious risk to stability and security unless you know what you're doing. After all, with a web server on your computer, anyone who knows its IP address could connect to your PC and browse your files if you don't configure it correctly.

All of which leaves us with one problem. If all you have is a copy of PSPad and access to a web server over the internet, how do you track down those elusive errors in your programs without the aid of a proper debugger? Hopefully, the remainder of this chapter will help.

There are two main types of error that you'll encounter. The first is a syntax error, where the code you write isn't valid PHP. For example:

```
echo "Sorry, room " . $room[1] . " is occupied"
```

You'll spend ages looking for the missing quote, or dot, only to realise that the problem is actually a missing semi-colon on the end of the line.

The other type of problem is where your PHP code is valid, but doesn't produce the results that you were expecting. For example, having added a semicolon to the above line, it produces:

```
Sorry, room is occupied
```

The mistake is clearly yours rather than the server's. It's a coding error. The $room[1] variable is empty and you need to find out why.

# Syntax Errors

A syntax error in a PHP file will normally prevent the entire program from running, even if the error is towards the end of the file. In most cases, you'll receive an error message from the server which will help you identify the cause of the problem. For example: