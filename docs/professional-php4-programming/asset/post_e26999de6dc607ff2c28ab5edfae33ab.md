
```php
// Login to the connection
// ... (code block content)
?>
```

## Building FTP Clients

The FTP functions were designed to be low level. This approach gives developers the control they need to build advanced FTP applications. The trade-off for this extra control is that extra effort is required to build the applications. Every step in the process must be explicitly called, thus making the extension inconvenient to use.

Now let's build two simple applications:

- A wrapper that makes the FTP functions more convenient to use. This wrapper will be optimized for scripts that need to transfer files between FTP servers and local file systems.

- A basic web-based FTP client. This application will be designed for users who need to transfer files to and from public FTP sites.

## An FTP Convenience Wrapper

The wrapper should reduce the effort needed to use FTP with PHP and should have the following features:

- [ ] Provide convenient methods that reduce the number of steps required to manage files
- [ ] Manage connections silently in the background, automatically creating, caching and destroying them as needed
- [ ] Integrate well with the local file system
- [ ] Work as a back-end for applications that use FTP to manage files

Let's expand these notes into some ideas on how we could implement the wrapper.

A class should be used for this wrapper. This could be done using functions and static or less optimally, global variables; but using an object-oriented approach is cleaner.

The wrapper should silently handle the connection and authentication involved in using FTP. This means that we need to have a way to manage the connection data easily. We need one method to handle connecting to FTP servers, and another to manage caching established connections. It is best to use an object or array to store the connection information. Let's decide what to do when we get to the actual coding.

Copying files between the local file system and FTP hosts should be as easy as copying files between two FTP hosts. This could be done using an interface that resembles rcp or scp.

> **scp** is a Linux command line utility based on **rcp**. It allows files to be transferred between two hosts using the SSH protocol. The syntax for **scp** allows the user to specify almost all of the data needed to make the file transfer on a single line. Basic syntax: **scp [[user@]host1:]file1 [[user@]host2:]file2.**

We take this idea to create a convenient_copy() method for our class. Something like method_name(from_argument, to_argument) should work. A call to copy a log file from example.com to the current working directory looks like this:

```
$ftp->copy('lenny:jamjam@example.com:/var/log/ftp.log', 'ftp.log');
```

This type of syntax allows us to roll up a good deal of functionality in a single method call. The class would manage connection and authentication, along with the details involved in transferring files. The only drawback of this type of syntax is that we will need to parse the locations into separate values for "user name", "password", "host name", and so on. This should be handled in a separate method.

Finally, to be tidy, we should have a _destructor() method that automatically closes the FTP connections opened by the class. While PHP does not have class destructors, we can fake one with a combination of register_shutdown_function() and the $this variable.

Now let's take a look at the code for the wrapper.

We'll start by defining some helper constants. These constants will be used as flags that note if a location is part of the local file system, or is on an FTP server. The wrapper needs this information to determine how to transfer the files:

```
<?php
define('LOCAL',
	1 << 0);		// Define helper constants
define('REMOTE',
	1 << 1);
define('TO_LOCAL',
	LOCAL);
define('TO_REMOTE',
	REMOTE);
define('FROM_LOCAL',
	LOCAL << 2);
define('FROM_REMOTE',
	REMOTE << 2);
```

The class Ftp_Wrapper has three class properties:

- $connection stores the open FTP connections. A simple cache for the open connections will be built using an associative array. It stores the connection id's as values, and uses keys generated from the data used to make the connection. Once a particular FTP server has been connected to, subsequent calls with the same connection and authentication data would generate the same key. This key could be used to fetch the cached connection id.
- $tmp_dir stores the location of the tmp directory on the local server. The class needs to store files in a temporary location when transferring files between two FTP servers.
- $mode stores the current transfer mode when transferring files via FTP.

```
class Ftp_Wrapper
{
	var $connection,
						// A list of the open ftp connections
	$tmp_dir = '/tmp',
						// The system temp directory
	$mode;
						// The transfer mode (ASCII or BINARY)
```

The Ftp_Wrapper() method is the class constructor. It is called automatically when the class is instantiated. Here the constructor initializes the $connection array, registers the _destructor() method to be called when the script ends, and sets the default transfer mode to BINARY:

```
function Ftp_Wrapper ()
{			// Class constructor

$this->connection = array();	// Initialize the connections array
register_shutdown_function(array($this, '_destructor'));
$this->mode = FTP_BINARY;		// Default transfer mode is BINARY
}
```

$this is a special variable that refers to the current instance of the class. It is used when the class needs to call its own methods, or manipulate its class properties.

The _destructor() method is prefixed with an underscore. PHP does not have the concept of private or protected methods. Conventionally, methods that should not be called outside the class should be named with a leading underscore:

The mode() method is one of two public methods for the class. It returns the current transfer mode that the class is using for FTP transfers. If passed an argument, it sets the transfer mode before returning it:

```
function mode($mode = NULL)
{
    // Set the transfer mode
    if (NULL != $mode)     // If needed, set the mode
    $this->mode = $mode;
    return $this->mode;    // Return the current setting
}
```

copy() is the major method for the class. It allows a file to be copied from a location. The file can be copied over the local file system, from the file system to a local file (or vice versa), or between two FTP servers:

```
function copy($from, $to)
{
```

We need to take the location information stored in $from and $to and break it into separate parts. This information will be placed in an array. It will overwrite the original data that was in the $from and $to arguments. See the _parse() method for more information on what happens at this step. Note that _parse() adds a type element to the array. This element contains the constant which indicates if the location is local or remote (and was defined above):

```
$from = $this->_parse ($from); // Split the locations into separate
$to = $this->_parse ($to);     // values
if (!$from || !$to)      // Exit if _parse() failed
    return FALSE;
```

Once the location has been parsed into separate values, we attempt to connect to the host names stored in the $to and $from arrays. If the location is a local path, then no connection is necessary:

```
if (!$this->_connect($from))   // Connect to the source location
    return FALSE;        // Exit if connection fails
if (!$this->_connect($to))     // Connect to the source location
    return FALSE;        // Exit if connection fails
```

Once we have connected to the remote server(s) we need to determine how to copy the files. We combine the values stored in the type elements of the location array to determine if the file is being copied from a local file to another local file, from a local file to an FTP server, from an FTP server to a local file, or between two FTP servers.

Note how we shift the type value of the $from location array two bit positions to the right. This converts the value of a REMOTE or LOCAL constant to a FROM_REMOTE or FROM_LOCAL constant. We then use the bitwise operator OR to combine the values stored in the type elements into one larger bit flag:

```
switch ($from['type'] << 2 | $to['type']) {
```

If the bit flag matches the combined values of the FROM_LOCAL and TO_LOCAL constants, then we are copying one local file to another. In this case, we just pass the path data from the location arrays to the PHP built in copy() function:
