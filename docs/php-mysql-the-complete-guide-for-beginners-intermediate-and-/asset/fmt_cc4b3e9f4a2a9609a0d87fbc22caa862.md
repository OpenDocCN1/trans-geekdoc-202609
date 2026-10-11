
Which returns this output:

![](Image01212.jpg)

This technique can be used to avoid post-processing loops over the `$_POST` array, making your code leaner and more concise.

## Section 55.6: Uploading files with HTTP PUT

[PHP provides support](http://php.net/manual/en/features.file-upload.put-method.php) for the HTTP PUT method used by some clients to store files on a server. PUT requests are much simpler than a file upload using POST requests and they look something like this:

![](Image01213.jpg)

Into your PHP code you would then do something like this:

![](Image01214.jpg)

Also [here](http://stackoverflow.com/questions/12005790/how-to-receive-a-file-via-http-put-with-php) you can read interesting SO question/answers about receiving file via HTTP PUT.

# Chapter 56: Type juggling and Non-Strict Comparison Issues

## Section 56.1: What is Type Juggling?

PHP is a loosely typed language. This means that, by default, it doesn't require operands in an expression to be of the same (or compatible) types. For example, you can append a number to a string and expect it to work.

![](Image01215.jpg)

The output will be:

![](Image01216.jpg) string(24) "This is example number 1"

PHP accomplishes this by automatically casting incompatible variable types into types that allow the requested operation to take place. In the case above, it will cast the integer literal `1` into a string, meaning that it can be concatenated onto the preceding string literal. This is referred to as type juggling. This is a very powerful feature of PHP, but it is also a feature that can lead you to a lot of hair-pulling if you are not aware of it, and can even lead to security problems.

Consider the following:

![](Image01217.jpg)

The intent appears to be that the programmer is checking that a variable has a value of `1`. But what happens if `$variable` has a value of `"1 and a half"` instead? The answer might surprise you.

![](Image01218.jpg)

The result is:

![](Image01219.jpg) bool(true)

Why has this happened? It's because PHP realised that the string `"1 and a half"` isn't an integer, but it needs to be in order to compare it to integer `1`. Instead of failing, PHP initiates type juggling and attempts to convert the variable into an integer. It does this by taking all the characters at the start of the string that can be cast to integer and casting them. It stops as soon as it encounters a character that can't be treated as a number. Therefore `"1 and a half"` gets cast to integer `1`.

Granted, this is a very contrived example, but it serves to demonstrate the issue. The next few examples will cover some cases where I've run into errors caused by type juggling that happened in real software.

## Section 56.2: Reading from a file

When reading from a file, we want to be able to know when we've reached the end of that file. Knowing that `fgets()` returns `false` at the end of the file, we might use this as the condition for a loop. However, if the data returned from the last read happens to be something that evaluates as boolean `false`, it can cause our file read loop to terminate prematurely.

![](Image01220.jpg)

If the file being read contains a blank line, the `while` loop will be terminated at that point, because the empty string evaluates as boolean `false`.

Instead, we can check for the boolean `false` value explicitly, using strict equality operators:

![](Image01221.jpg)

Note this is a contrived example; in real life we would use the following loop:

![](Image01222.jpg)

Or replace the whole thing with:

![](Image01223.jpg)

## Section 56.3: Switch surprises

Switch statements use non-strict comparison to determine matches. This can lead to some [nasty surprises](http://stackoverflow.com/questions/4098104/odd-behaviour-in-a-switch-statement). For example, consider the following statement:

![](Image01224.jpg)

This is a very simple statement, and works as expected when `$name` is a string, but can cause problems otherwise.

For example, if `$name` is integer `0`, then type-juggling will happen during the comparison. However, it's the literal value in the `case` statement that gets juggled, not the condition in the `switch` statement. The string `"input 1"` is converted to integer `0` which matches the input value of integer `0`. The upshot of this is if you provide a value of integer `0`, the first `case` always executes.

There are a few solutions to this problem:

**Explicit casting**

The value can be typecast to a string before comparison:

![](Image01225.jpg)

Or a function known to return a string can also be used:

![](Image01226.jpg)

Both of these methods ensure the value is of the same type as the value in the `case` statements.

**Avoid switch**

Using an `if` statement will provide us with control over how the comparison is done, allowing us to use strict comparison operators:

![](Image01227.jpg)

## Section 56.4: Strict typing

Since PHP 7.0, some of the harmful effects of type juggling can be mitigated with [strict typing](http://php.net/manual/en/functions.arguments.php#functions.arguments.type-declaration.strict). By including this `declare` statement as the first line of the file, PHP will enforce parameter type declarations and return type declarations by throwing a `TypeError` exception.

![](Image01228.jpg)

For example, this code, using parameter type definitions, will throw a catchable exception of type `TypeError` when run:

![](Image01229.jpg)

Likewise, this code uses a return type declaration; it will also throw an exception if it tries to return anything other than an integer:

![](Image01230.jpg)

# Chapter 57: Sockets

## Section 57.1: TCP client socket

Creating a socket that uses the TCP (Transmission Control Protocol)

```
$socket = socket_create(AF_INET, SOCK_STREAM, SOL_TCP);
```

Make sure the socket is successfully created. The `onSocketFailure` function comes from Handling socket errors example in this topic.

```
if (!is_resource($socket)) onSocketFailure("Failed to create socket");
```

Connect the socket to a specified address. The second line fails gracefully if connection failed.

```
socket_connect($socket, "chat.stackoverflow.com", 6667)
    or onSocketFailure("Failed to connect to chat.stackoverflow.com:6667", $socket);
```

Sending data to the server

The `socket_write` function sends bytes through a socket. In PHP, a byte array is represented by a string, which is normally encoding-insensitive.

![](Image01234.jpg)

Receiving data from the server

The following snippet receives some data from the server using the `socket_read` function.

Passing `PHP_NORMAL_READ` as the third parameter reads until a `\r` / `\n` byte, and this byte is included in the return value.

Passing `PHP_BINARY_READ`, on the contrary, reads the required amount of data from the stream.

If `socket_set_nonblock` was called in prior, and `PHP_BINARY_READ` is used, `socket_read` will return `false` immediately. Otherwise, the method blocks until enough data (to reach the length in the second parameter, or to reach a line ending) are received, or the socket is closed.

This example reads data from a supposedly IRC server.

![](Image01235.jpg)

Closing the socket

Closing the socket frees the socket and its associated resources.

![](Image01236.jpg)

## Section 57.2: TCP server socket

Socket creation

Create a socket that uses the TCP. It is the same as creating a client socket.

![](Image01237.jpg)

Socket binding

Bind connections from a given network (parameter 2) for a specific port (parameter 3) to the socket.

The second parameter is usually `"0.0.0.0"`, which accepts connection from all networks. It can also
