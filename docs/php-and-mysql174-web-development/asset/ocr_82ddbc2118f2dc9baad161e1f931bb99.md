# Next 421

A handy use of ftp_size() is to work out the maximum execution time set for a particular transfer. Given the file size and speed of your connection, you can take a guess as to how long the transfer ought to take and use the set_time_limit() function accordingly.

You can get and display list of files in a directory on a remote FTP server using the following code:

```
$listing = ftp_list($conn, dirname($remotfile));
foreach ($listing as $filename) {
  echo $filename.'.br />
}
```

This code uses the ftp_list() function to get a list of files in a particular directory.
in terms of FTP functions, anything that you can do from an FTP command, you can do with the FTP functions, with the exception of mget (multiple get). For mget, you could use ftp_list() to get a list of files and then fetch them as needed.

For a complete list of PHP functions corresponding to each FTP command, please see the PHP online manual at http://php.net/manual/en/book.ftp.php.

# Further Reading

We covered a lot of ground in this chapter, and as you might expect, a lot of material is out there on these topics. For information on the individual protocols and how they work, you can consult the RFCs at http://www.rfc-editor.org/.

You might also find some of the protocol information at the World Wide Web Consortium interesting; go to http://www.w3.org/Protocols/.

You can also try consulting a book on TCP/IP such as Computer Networks by Andrew Tanenbaum.

# Next

We are ready to move on to Chapter 19, “Managing the Date and Time,” and look at PHP’s libraries of date and calendar functions. There, you see how to convert from user-entered formats to PHP formats to MySQL formats, and back again.