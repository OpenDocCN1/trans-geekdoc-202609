# 156 Part II: Solutions

HTTP headers are considered in more detail in Chapter II.10.

The posed problem of developing a script for storing text and graphics files can be solved using HTTP headers, as is shown in Listing II.3.7.

# Listing II.3.7. A script for saving text and graphics files

The script takes the file name as a GET parameter, for example, index.php?down=file.txt. The name of the file to save, which is determined by the filename attribute, is specified by the first HTTP header. In the script, the filename parameter is the same as the file name, but any name can be used. The second HTTP header tells the browser that the file is binary and should not be interpreted. The third line uses the file_get_contents() function to extract the contents of the file sent using the $_GET['down'] parameter and displays them in the browser window.

It is important that, after the file's contents are output, nothing else is output into the stream by either the echo statement or the direct output; otherwise, all this will be appended to the file. This includes possible spaces and line feeds after the closing >> tag.

# II.3.6. Determining File Size

A file's size can be determined using the filesize() function, which takes a file's name as the argument and returns its size in bytes, kilobytes, or megabytes, depending on the file's size. The size can be determined by a script like the one shown in Listing II.3.8.