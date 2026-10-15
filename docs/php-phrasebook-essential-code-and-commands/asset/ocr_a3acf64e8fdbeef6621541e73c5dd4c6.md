```
echo 'Original file size: ' . strlen($data) .
    '.';
?>
```

# *Zipping and Unzipping a File (zip.php; excerpt)*

One of them can be used to use ZIP files. The pseudo protocol compress.zlib:// can be used to access ZIP files as you would access regular files. For this to work, you have to use the configuration switch -with-gzip under UNIX/Linux; Windows systems have the required libraries already included. Then, you can use the files using, for instance, file_get_contents() and file_put_contents().

The preceding code loads the current file (with file_get_contents()), zips it, and writes it to the hard disk (with file_put_contents()). Then, it reads in the zipped file (with file_get_contents()) and compares the file sizes.

When testing this, the code managed to compress the file from 729 to 336 bytes.

Alternatively, you can use PHP's built-in ZIP functions, which are implemented by a wrapper to the ZZ IPlib library from http://zziplib.sourceforge.net/. This one can only read data from a ZIP file, unfortunately, but also supports multiple files within an archive (when using the stream wrapper compress.zlib://, you first have to tar data to support multiple files).

To install, use extension=php_zip.dll in php.ini under Windows, or configure PHP with -with-zip, providing the path to ZZ IPlib. The following steps must be taken to use this extension:

+   - Open the archive using zip_open()