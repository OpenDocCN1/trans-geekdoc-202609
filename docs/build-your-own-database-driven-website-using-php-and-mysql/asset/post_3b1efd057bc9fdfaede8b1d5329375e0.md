
Despite these two little stumbling blocks, PHP's built-in `mail` function provides incredible convenience and ease of sending email messages from your Web page.

## Summary

In this chapter, we've looked at some of PHP's convenient and powerful built-in functions. With the `include` function, you can increase the security of your site and reuse code that might appear on many pages of your site (e.g. connecting to MySQL and selecting your database). With the file manipulation functions, you can reduce the strain that your semi-dynamic pages place on your server. And with the incredibly simple `mail` function you can send email from any PHP script with a single line of code. In addition, we looked at how to accept and handle file uploads in PHP.

## 11 Storing Binary Data in MySQL

In the previous chapter, we developed a system whereby users could upload image files and have them stored on your Web server for display on your site. In developing this system, we had to tackle several issues:

- Ensure that non-conflicting filenames are generated.
- Synchronize stored files with the database by adding an entry for each file as it is uploaded.
- Delete old files when their database entries are deleted.

While I effectively demonstrated that these constraints can be met, after 10 chapters of pushing the advantages of relational databases, you may have been surprised that I didn't opt for a solution where the files were stored in the database.

In cases where you're dealing with relatively small files (e.g. small head shots for use in a staff directory), the storage of data in MySQL is in fact quite practical. In this chapter, I'll demonstrate how to use PHP to store binary files uploaded over the Web in a MySQL database, and how to retrieve those files for download or display.

### Binary Column Types

As with most database-driven Web applications, the first thing to consider is the layout of the database. For each of the files that's stored in our database, we will store the file name, the MIME type (e.g. image/pjpeg for JPEG image files), a short description of the file, and the binary data itself. Here's the CREATE TABLE statement that must be entered in MySQL to create the table:

```
mysql> CREATE TABLE filestore (
-> ID INT NOT NULL PRIMARY KEY AUTO_INCREMENT,
-> FileName VARCHAR(255) NOT NULL,
-> MimeType VARCHAR(50) NOT NULL,
-> Description VARCHAR(255) NOT NULL,
-> Filedata MEDIUMBLOB
-> );
```

Most of this should be familiar to you; however, the MEDIUMBLOB column type is new. If you consult the MySQL Column Type Reference in Appendix C, you'll find that MEDIUMBLOB is the same as MEDIUMTEXT, except that it performs case-sensitive searches and sorts. In fact, from MySQL's point of view, there is no difference between binary data and blocks of text – both are just long strings of bytes to be stored in the database. The reason we'll use MEDIUMBLOB instead of MEDIUMTEXT is simply to anticipate the situation where we might need to compare the contents of one binary file with another. In such cases, we'd want the comparison to be 'case sensitive', as binary files may use byte patterns that are equivalent to alphabetical letters, and we'd want to distinguish between the byte pattern that represents 'A' from that which represents 'a'.

MEDIUMBLOB is one member of a family of 'BLOB' column types designed to store variable-length binary data (BLOB stands for Binary Large Object). These column types differ from one another only in two aspects: the maximum size of the data a particular value in the column can contain, and the number of bytes used to store the length of each data value. The different binary column types are listed with these details in Table 1.

### Table 1 -- Binary Column Types in MySQL

| Column Type | Maximum Size | Space req'd per entry |
| :--- | :--- | :--- |
| TINYBLOB | 255B | Data size + 1 byte |
| BLOB | 65KB | Data size + 2 bytes |
| MEDIUMBLOB | 16.7MB | Data size + 3 bytes |
| LONGBLOB | 4.3GB | Data size + 4 bytes |

As you can see, the table we created above will be able to store files up to 16.7MB in size. If you think you'll need larger files, you can bump the FileData column up to a LONGBLOB. Each file will occupy 1 more byte in the database (because MySQL will require that extra byte in order to record larger file sizes), but you'll be able to store files up to 4.3GB in size (assuming that your operating system allows files of that size)!

### Storing Files

The next step is to create a PHP script that lets users upload files and store them in the database. You can hold off copying the code in the next two sections – I'll present it all as a complete script at the end of the chapter.

Here's the code for the form (there should be no surprises here):

```
<form action="<?=PHP_SELF?>?action=ulfile" method="post" enctype="multipart/form-data">
<p>Upload File:<br />
<input type="file" name="uploadfile" /></p>
<p>File Description:<br />
<input type="text" name="desc" maxlength="255" /></p>
<p><input type="submit" name="go" value="Upload" /></p>
</form>
```

As you should already know from our work in Chapter 10, this form will create a temporary file on the server and store the filename of that temp file in $uploadfile. It also creates $uploadfile_name (the original name of the file), $uploadfile_size (the file size in bytes), and $uploadfile_type (the MIME type of the file).

Inserting the file into the database is a relatively straightforward process: open the temporary file, read the data it contains into a PHP variable, and then use that variable in a standard MySQL INSERT query. Again, we make use of is_uploaded_file to make sure the filename we use does in fact correspond to an uploaded file before we do any of this. Here's the code:

```
// Bail out if the file isn't really an upload.
if (!is_uploaded_file($uploadfile))
  die("$uploadfile is not an uploaded file!");

// Open file for binary reading ("rb")
$tempfile = fopen($uploadfile,"rb");

// Read the entire file into memory using PHP's
// filesize function to get the file size.
$filedata = fread($tempfile,filesize($uploadfile));

// Prepare for database insert by adding backslashes
// before special characters.
$filedata = addslashes($filedata);

// Create the SQL query.
$sql = "INSERT INTO filestore SET
   FileName = '$uploadfile_name',
   MimeType = '$uploadfile_type',
   Description = '$desc',
   FileData = '$filedata';";

// Perform the insert.
$ok = @mysql_query($sql);
if (!$ok) die("Database error storing file: " .
  mysql_error());
```

### Viewing Stored Files

Armed with the code that accepts file uploads and stores them in a database, you're halfway home. But you still need to be able to pull that data out of the database to use it. For our purposes, this will mean sending the file to a requesting browser.

Once again, this turns out to be a relatively straightforward process. We simply retrieve the data for the requested file from the database and send it on to the Web browser. The only tricky part is to send the browser information about the file, including:

- The file size (so that the browser can display accurate download progress information to the user)
- The file type (so that the browser knows what to do with the data it receives, e.g. display it as a Web page, a text file, an image, or offer to save the file)
- The filename (if we don't specify it, the browser will assume all files downloaded from our script have the same filename as the script)

All this information is sent to the browser using HTTP headers - special lines of information that precede the transmission of the file data itself. Sending HTTP headers via PHP is quite easy using the header() function, but as headers must be sent before plain content, any calls to this function must come before anything is output by your script.

The file size is specified with a content-length header:

```
header("Content-Length: " . strlen($filedata));
```

strlen is a built-in PHP function that returns the length of the given string. Since binary data is just a string of bytes as far as PHP is concerned, you can use this function to count the length in bytes of the file data.

The file type is specified with a content-type header:

```
header("Content-Type: $mimetype");
```

Finally, the filename is specified with a content-disposition header:

```
header("Content-Disposition: filename=$filename");
```

Thus, use the script below to fetch a file with a given ID from the database and send it to the browser:

```
$sql = "SELECT FileName, MimeType, FileData FROM filestore WHERE ID = 'id'";
$result = @mysql_query($sql);
if (!$result) die("Database error: " . mysql_error());

$filename = mysql_result($result,0,"FileName");
$mimetype = mysql_result($result,0,"MimeType");
$filedata = mysql_result($result,0,"FileData");

header("Content-disposition: filename=$filename");
header("Content-Type: $mimetype");
header("Content-Length: " . strlen($filedata));

echo($filedata);
```
