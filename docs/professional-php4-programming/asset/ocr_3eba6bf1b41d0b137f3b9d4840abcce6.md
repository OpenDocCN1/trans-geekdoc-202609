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