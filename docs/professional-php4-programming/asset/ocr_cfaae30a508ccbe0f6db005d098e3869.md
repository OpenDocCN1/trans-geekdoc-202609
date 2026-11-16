```
'(\S+)\s+' .      // Get group name
'(\S+)\s+' .      // Get size
'(\S+\s+\S+\s+\S+\s+)' .  // Get file/dir last mod time
'(.+)\s/';      // Get file/dir name
      break;
}
// Map short identifiers to full names
$type = array('-' => 'file', 'd' => 'directory');
$listings = array ();
```

Once we have chosen the regular expression to use, it is used to parse the listings that are stored in $temp. To do this, we use the preg_match() function. This function applies a Perl-style regular expression to a string and stores parts of the string that match the parenthesized sections of the expression in an array. In this case, we have called the array that stores the matches $matches:

```
foreach ($temp as $entry) {       //Loop through raw listings
    // Try to parse raw data into fields
    $match = preg_match($re, $entry, $matches);
```

If the regular expression could not be applied to the listing, it fails:

```
if (!$match) {                 // If we could not parse the listings
    user_error ("The directory listings could not be parsed.");
    return array ();
}
```

Now that the listings have been split into separate fields, let's put them in an associative array, to make working with the fields easier. We do different things, based on the FTP server's system type. For most Windows NT servers, we have fewer fields to deal with. The elements in the array that we don't use are set to NULL.

There are a few tricky things going on in this code. Our regular expression for parsing the Windows FTP server listing uses the same parenthesized sub-expression to capture the directory or file size information. To make this information match our UNIX file listing information, we can do a few conversions.

First, when setting the type element in the array, check to see if the value we are working with is numeric. If it is, we know that we are dealing with a file, since only files have sizes. Any other value indicates that we are dealing with a directory.

Similarly, when setting the size element of the array, we force the value to be an integer using an (int) cast. If it contains the <dir> string the cast will convert it to zero (0):

```
switch ($this->systype) {       // Give fields sensible names
case 'Windows_NT':          // Handle WinNT-style dir listings
    $listings[] = array   // Put parsed data into readable format
        'type'  =>
        is_numeric($matches[2]) ? 'file' : 'directory',
        'permissions' => NULL,
```