The fourth parameter is also optional. The fopen() function allows filenames to be prefixed with a protocol (such as http://) and opened at a remote location. Some protocols allow for an extra parameter. We look at use of the fopen() function in the next section of this chapter.

If fopen() opens the file successfully, a resource that is effectively a handle or pointer to the file is returned and should be stored in a variable--in this case, $fp. You use this variable to access the file when you actually want to read from or write to it.

# Opening Files Through FTP or HTTP

In addition to opening local files for reading and writing, you can open files via FTP, HTTP, and other protocols using fopen(). You can disable this capability by turning off the allow_url_fopen() directive in the php.ini file. If you have trouble opening remote files with fopen(), check your php.ini file.

If the filename you begins with ftp://, a passive mode FTP connection will be opened to the server you specify and a pointer to the start of the file will be returned.

If the filename you begins with http://, an HTTP connection will be opened to the server you specify and a pointer to the response will be returned.

Remember that the domain names in your URL are not case sensitive, but the path and file-name might be.

# Addressing Problems Opening Files

An error you might make is trying to open a file you don't have permission to read from or write to. (This error occurs commonly on Unix-like operating systems, but you may also see it occasionally under Windows.) When you do, PHP gives you a warning similar to the one shown in Figure 2.2.