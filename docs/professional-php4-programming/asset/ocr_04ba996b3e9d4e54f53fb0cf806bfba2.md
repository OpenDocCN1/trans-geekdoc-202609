# socket_set_blocking()

```
int socket_set_blocking(int socket_descriptor, int mode)
```

This function sets or unsets the blocking I/O status of a socket. The first argument is the socket
descriptor and if the second argument is true, the socket is set to be a blocking socket. A false
argument would set it to be a non-blocking socket.

Functions that read from a blocking socket will wait until data is available on the socket to be read. If the
socket is non-blocking, such functions will return immediately with an error condition if data is not available.

# socket_set_timeout()

```
boolean socket_set_timeout(int socket_descriptor, int seconds, int micros)
```

This function sets the timeout for a socket with micro-second granularity. The first argument is the
socket descriptor, the second argument is the seconds component of the timeout period and the third
argument is the micro-second component of the timeout period. The timeout period determines how
long a socket should stay open without any I/O activity.

# read()

```
int read(int socket_descriptor, string buffer, int length [, int type])
```

This function can be used to read from a socket descriptor specified as the first argument. The length
argument indicates the number of bytes to read and the buffer argument indicates the buffer where
the read data is to be placed.

The optional type argument can be specified as PHP_NORMAL_READ or PHP_BINARY_READ. If type is
PHP_NORMAL_READ, the read operation stops as soon as it encounters a \n (newline) or \r (carriage-
return) character. If type is PHP_BINARY_READ, the read operation continues until there is no more data
or the specified number of bytes has been read. As of release 4.0.6, if type is omitted, the default
behavior is the same as specifying PHP_NORMAL_READ. The function returns the number of bytes read
or FALSE if an error occurs.

# write()

```
int write(int socket_descriptor, string &buffer, int length)
```

This function is complementary to the read() function. It writes the bytes present in the buffer
specified by the second argument to the socket descriptor specified by the first argument. The third
argument dictates the number of bytes to be written. The function returns the number of bytes written
or false if an error occurs.

# strerror()

```
string strerror(int errno)
```

The error number set by socket functions does not give us much of a clue as to what went wrong. Passing
the error number as an argument to strerror() causes a string to be returned which is a verbose
description of the error message.