# boolean ftp_fput(integer link, string remote, integer file, integer mode)

The ftp_fput function creates a file on the remote server from the contents of an open file stream. The iink argument is returned by ftp_connect. The remote argument is the path to the file to be created on the remote server. The file argument is a file identifier returned by fopen or a similar function. The mode argument should be FTP_ASCII or FTP_IMAGE.

```
<?
//connect to server
if($ftp = ftp_connect("localhost")) {
    print("Unable to connect!BR\n");
    exit();
}

//log in
if(!ftp_login($ftp, "anonymous", "corephp@localhost")) {
    print("Unable to login!BR\n");
    exit();
}

//open local file
if($fp = fopen("/tmp/data.txt", "r")) {
    print("Unable to open local file!BR\n");
    exit();
}

//write file to remote server
ftp_fput($ftp, "data.txt", $fp, FTP_ASCII);

//close local file
close($fp);

//close connection
ftp_quit($ftp);
?>
```

# boolean ftp_get(integer link, string local, string remote, integer mode)

Use ftp_get to copy a file from the remote server to locals filesystem. The link argument is returned by ftp_connect. The local and remote arguments specify paths. The mode argument should use FTP_ASCII or FTP_IMAGE.