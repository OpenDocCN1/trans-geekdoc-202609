
> If you are using a Linux or UNIX system you can install the tcplisten application and use that as a way to debug your client.

Connecting to a server returns a php_socket_t structure:

```
socklen_t size;
php_socket_t socket;
struct timeval tv;

tv.tv_sec = 10;
tv.tv_usec = 0;

socket = php_network_connect_socket_to_host("localhost", 7777, SOCK_STREAM,
    0, &tv, NULL, NULL, NULL, 0, TSRMLS_CC);
if (socket == -1) {
    /* could not connect */
}
```

The preceding example is hard coded, for simplicity, to connect to port 7777 on localhost. The values can, of course, be variable. Once connected, it is time to get the stream from the socket. After that, you can read and write as you would with a normal stream.

```
php_stream *stream;
stream = php_stream_sock_open_from_socket(socket, 0);
php_stream_write(stream, "Ping\n");
php_printf("Pong: %s", php_stream_get_line(stream, NULL, 0, NULL));
```

And, of course, it is necessary to close the stream and free the socket at the end of the script:

```
php_stream_close(stream);
closesocket(socket);
```

## Building a Server

PHP is most often seen acting as a daemon on a local host. It is very rare to see PHP acting as a server in either a web server or an Apache environment. It is also uncommon to see PHP acting as a server for outside connections from the cloud. However, both are definitely possible.

The first step is always to bind to a socket. After that, depending on the mode, it might be useful to set the socket to non-blocking. PHP allows the socket to accept multiple connections. Each connection has its own socket and its own stream. The simple server in this section just accepts one connection and could be used as a basic server for the client from the previous section.

The code to open the socket is straightforward:

```
php_socket_t server;

server = php_network_bind_socket_to_local_addr("127.0.0.1", 7777,
    SOCK_STREAM, NULL, &error,
    TSRMLS_CC);
listen(server, 5);
```

After that it is necessary to listen for a new connection. This is a blocking socket so it just waits until a connection arrives and does everything in sequence. A non-blocking socket would create a loop that simultaneously looks for new connections and reads data from existing connections.

```
socket = php_network_accept_incoming(server,
    NULL, NULL, NULL, NULL, &tv, NULL,
    &error, TSRMLS_CC);

if (socket == -1) {
    closesocket(server);
    RETURN_NULL();
}

stream = php_stream_sock_open_from_socket(socket, 0);
php_stream_write(stream, "Ping\n", 5);

char *pong;
int pong_len;
spprintf(&pong, &pong_len, "Pong: %s",
    php_stream_get_line(stream, NULL, 0, NULL));
php_stream_write(stream, pong, pong_len);
efree(pong);
```

Note that you can get a lot more information about the client that is connecting to your server by passing additional parameters to the php_network_accept_incoming function. For simplicity, the preceding script uses all NULL.

Closing the sockets and freeing the streams work the same way as before. Just remember that you may have more than one socket and many streams open at the time so be sure to close them all.

## Errors and Warnings

All errors and warnings in PHP are output via the same function. The engine then decides how to display the error and log it. You can log an error and display it to the standard output or web page in one of the following ways:

```
php_error(E_WARNING, "Method %s not yet implemented.", method_name);
php_error_docref(NULL, TSRMLS_CC, E_ERROR, "Could not connect to server %s:%i.",
    server_name, port_name);
```

The second and fourth arguments — the format strings bolded in the preceding example — are the same as with printf so you can do replacements into it.

The second function also automatically takes care of putting the current function information in the error if you pass the first argument as NULL. It also highlights HTML when appropriate. Because of the added features, the second is preferable in just about all cases. One notable exception is during initialization and shutdown when there isn’t any active function or page.

Possible values for types of errors are:

- E_ERROR
- E_WARNING
- E_NOTICE
- E_PARSE
- E_CORE_ERROR
- E_CORE_WARNING
- E_USER_ERROR
- E_USER_WARNING
- E_USER_NOTICE
- E_STRICT
- E_RECOVERABLE_ERROR
- E_DEPRECATED
- E_USER_DEPRECATED

The first three in the list are by far the most common from within extensions. It is also possible (although not common or recommended) to output directly to the error log. That is done via the php_error_log function:

```
php_error_log(0, "Message", NULL, NULL, TSRMLS_CC);
```

The error log function is identical to its PHP counterpart. It does not output anything to the screen and does not contain any file or line information. The function also accepts all the same additional parameters that allows for the error to be sent via email or output to a different log file.

The preceding example uses 0 to output to the error logs. Other possible options for the first parameter are:

- A value of 1: Send via email. Use the third parameter as an email address string and the fourth parameter as optional mail headers.
- A value of 2: Send via TCP/IP. The third parameter is a host:port pair.
- A value of 3: Save to the file specified by the third parameter.

## ARRAYS AND HASH TABLES

This chapter already covered Boolean, long, double, and string data types. Two big things that were missing were arrays and hash tables. First, as you may have guessed, the two are the same. Arrays are numerically indexed and pure hash tables act like associative arrays and can be referenced by keys.

Even though both are extremely similar and they share the same data types, they each have their own set of useful functions to create, read, and modify them. Arrays are a tiny bit less complicated so they are covered first.

## Building and Accessing Arrays

Many functions are available for building an array. The first thing that is needed in all cases is to get a handle to the array. There are two possible situations. One is that a zval already exists and it is necessary to get the hash table object, and the other is that a new hash table should be created.

Creating a new array/hash table in a zval looks like this:

```
zval *new_array;
array_init( new_array );
```

Accessing an existing hash table like the one just created based on a zval looks like this:

```
HashTable *hash;
hash = Z_ARRVAL_P( new_array );
```

This is the first time you’re seeing the HashTable data type in this book. The array is being initialized inside of the zval and then being retrieved and pointed to by the hash table. Once the hash table is retrieved or created, new values can then be added or deleted. There are three basic situations with arrays. They are:

- Adding at a specific index
- Using a specific key
- Adding to the next available index

The three functions are very similar:

```
add_assoc_double( new_array, "key_name", 3.14 );
add_index_double( new_array, 3 /* add at index 3 */, 3.14 );
add_next_index_double( new_array, 3.14 );
```

This code shows the double version of each of the functions. In addition to strings there are also functions for all the other data types. The data types have already been mentioned several times in this chapter, but just for review, they are:

- bool
- double
- long
- null
- resource
- string and stringl (takes a length)
- zval

Additionally, each associative array function also has an extended version that takes an extra parameter after the key for the length, thus allowing for binary safe keys. By now it should be clear that whenever a function takes string length it is always passed as an integer immediately after the string.

All the functions that add a value to an array — with the exception of a zval directly — create a new zval. It would be inefficient to add a value and then immediately try to fetch it. For the situations where it is necessary to reference the created zval later there is another set of functions:

```
zval *new_item;
add_get_next_index_double( new_array, 3.14, new_item);
```
