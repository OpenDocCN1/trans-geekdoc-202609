
Turns passive mode on or off. If passive mode is enabled, then connections made to the FTP server will be initiated by the client, rather than by the server. This is often required to allow FTP to work in conjunction with a firewall.

## ftp_put()

```
boolean ftp_put(int ftp_link, string remote_file, string local_file, int mode)
```

Returns true on success, and false on failure:

```php
<?php
// Assume that we have already connected and authenticated to an FTP server
$local_file = '/path/to/local_file.txt';
$remote_file = 'remote_data.txt';

ftp_get($ftp_handle, $local_file, $remote_file, FTP_BINARY)
    or die("Could not copy remote file '$remote_file' to local file ".
    "'$local_file'.");

?>
```

Uploads the given file to the FTP server. The mode argument should be set using the FTP_ASCII or FTP_BINARY named constant.

## ftp_pwd()

```
string ftp_pwd(int ftp_link)
```

Returns the directory name on success, and false on failure:

```php
<?php
// Assume that we have already connected and authenticated to an FTP server

echo("The current remote working directory is " . ftp_pwd($ftp_handle));
?>
```

Returns the name of the remote current working directory.

## ftp_quit()

```
boolean ftp_quit(int ftp_link)
```

Returns true on success, and false on failure:

```php
<?php
// Assume that we have already connected and authenticated to an FTP server
ftp_quit($ftp_handle);
?>
```

Closes an FTP connection. FTP connections opened with `ftp_connect()` should be closed with `ftp_quit()`. The reason for this is that, unlike most PHP functions that connect to remote resources, the FTP extension does not automatically close connections that are opened by it at script end.

Unlike HTTP connections that support one command, one response, and quit, FTP connections support multiple commands and stay open. While orphaned FTP connections will probably (depending on the FTP server) get closed after they are idle for a time; a popular web interface to FTP could easily leave quite a few orphans open, thus wasting connection space for those FTP servers where this matters. Unlike other PHP commands, the FTP commands can be used to access someone else's service, so extra care should be taken.

## ftp_rawlist()

```
array ftp_rawlist(int ftp_link, string directory)
```

Returns array of directory listing, and false on failure:

```php
<?php
// Assume that we have already connected and authenticated to an FTP server
// Get a list of the files in the parent of the remote current working directory
$directory = '..';
$file_list = ftp_rawlist($ftp_handle, $directory)
or die("Could not list the files in directory '$directory'.");
echo("Directory '$directory' contains the following files:");
print_r($file_list);
?>
```

Executes the FTP LIST command on the FTP server and return the results as an array. Each entry in the array will contain a single line of output from the LIST command.

The output of this command will vary based on the operating system of the remote server. Use the `ftp_systype()` function to determine the operating system of the remote server and parse the data returned accordingly.

## ftp_rename()

```
boolean ftp_rename(int ftp_link, string from, string to)
```

Returns true on success, and false on failure:

```php
<?php
// Assume that we have already connected and authenticated to an FTP server
$old = 'original.txt';
$new = 'backup.txt';
ftp_rename($ftp_handle, $old, $new)
or die("File '$old' could not be renamed to '$new'.");
?>
```

Renames (or moves) a file on the FTP server.

## ftp_rmdir()

```
boolean ftp_rmdir(int ftp_link, string directory)
```

Returns true on success, and false on failure:

```php
<?php
// Assume that we have already connected and authenticated to an FTP server

$directory = 'temp';
ftp_rename($ftp_handle, $directory)
    or die("Directory '$directory' could not be removed.");

echo("Directory '$directory' was removed.");
?>
```

Removes a directory on the remote system. If the directory contains any files, the directory will not be removed.

## ftp_site()

```
boolean ftp_site(int ftp_link, string command)
```

Returns true on success, and false on failure:

```php
<?php
// Assume that we have already connected and authenticated to an FTP server

// Try to change the permissions of a remote file
$command = 'chmod 0755 /path/to/file.txt';

ftp_site($ftp_handle, $command)
    or die("Command '$command' could not be run.");

echo("Command '$command' was run successfully.");
?>
```

Sends a SITE command to the FTP server. SITE commands vary from server to server. They are often used for handling operating system specific commands such as chmod. To find what SITE commands a server supports, manually FTP into the server and run the REMOTEHELP command.

## ftp_size()

```
int ftp_size(int ftp_link, string filepath)
```

Returns the size of the file in bytes, and -1 on error:

```php
<?php
// Assume that we have already connected and authenticated to an FTP server

$file = '/path/to/file.txt';
$size = ftp_size($ftp_handle, $file);
if (-1 == $size) {
    echo("The size of file '$file' could not be determined.");
} else {
    echo("File '$file' is $size bytes in size.");
}
?>
```

## ftp_systype()

```
string ftp_systype(int ftp_link)
```

Returns the system type identifier of the FTP server, and NULL on failure:

```php
<?php
// Assume that we have already connected and authenticated to an FTP server

$systype = ftp_systype($ftp_handle)
    or die("The system type of the FTP server cannot be determined.");

echo("The FTP server's system type is '$systype'.");
?>
```

Sends a SYST command to the FTP server. If the command fails, the function returns NULL. This function is often used in conjunction with ftp_rawlist() to determine how to parse the directory list information returned by ftp_rawlist().

## Common FTP Client Commands and Corresponding PHP Functions

| Command | Description | Equivalent PHP Function |
|---|---|---|
| ! | Escape to the shell | Use PHP's program execution functions |
| $ | Execute macro | |
| ? | Alias for HELP | |
| ACCOUNT | Send account information to remote server | |
| APPEND | Append to a file | |
| ASCII | Set the transfer type to ASCII | Set on a per-call basis with calls to ftp_fget(), ftp_fput(), ftp_get(), and ftp_put() |
| BELL | Toggle bell mode on or off | |
| BINARY | Set the transfer type to binary | Set on a per-call basis with calls to ftp_fget(), ftp_fput(), ftp_get(), and ftp_put() |
| BYE | Alias for QUIT | |
| CASE | Toggle case conversion on or off | Use str2lower() in conjunction with the FTP functions to force filenames to lowercase |
| CD | Change remote working directory | ftp_chdir() |
| CDUP | Change remote working directory to be the parent of the current working directory | ftp_cdup() |
| CHMOD | Change the permissions of a remote file | |
| CLOSE | Terminate the FTP session | ftp_quit() |
| CR | Toggle carriage return (\r) stripping on or off for ASCII gets | |
| DEBUG | Toggle debugging on or off | |
| DELETE | Delete remote file | ftp_delete() |
| DIR | Alias for LS | |
| DISCONNECT | Terminate the FTP session | ftp_quit() |
| FORM | Set file transfer format on a per-call basis | |
| GET | Get a remote file | ftp_fget(), ftp_get() |
| GLOB | Toggle file globbing on/off | |
| HASH | Enable or disable the display a hash mark (#) for every file transferred | |
| HELP | Print local help information | |
| IDLE | Get or Set remote idle timeout | |
| IMAGE | Alias for BINARY | |
| LCD | Change local working directory | chdir() |
| LS | List contents of remote directory | ftp_rawlist() |
| MACDEF | Define a macro | |
| MDELETE | Delete multiple remote files | |
| MDIR | Alias for MLS | |
| MGET | Get multiple remote files | |
| MKDIR | Create directory on remote system | ftp_mkdir() |
| MLS | List contents of multiple remote directories | |
| MODE | Set file transfer mode | |
| MODTIME | Show last modification time of remote file | ftp_mdtm() |
| MPUT | Send multiple files to remote system | |
| NEWER | Get file if remote file is newer than local file | |
| NLIST | Get a terse list of files in a remote directory | ftp_nlist() |
| NMAP | Set templates for default file name mapping | |
| NTRANS | Set translation table for default file name mapping | |
| OPEN | Open connection to FTP server | ftp_connect() |
| PASSIVE | Toggle passive mode transfers on or off | ftp_pasv() |
| PROMPT | Toggle interactive mode on or off | |
| PROXY | Execute FTP command on secondary FTP connection | |
| PUT | Send local file to remote system | ftp_fput(), ftp_put() |
| PWD | Display remote current working directory | ftp_pwd() |
| QUIT | Close connection to FTP server and exit FTP client | ftp_quit() |
| QUOTE | Send arbitrary command to remote server | |
| RECV | Alias for GET | |
| REGET | Resume transfer of a file after network error | |
| RENAME | Rename (or move) remote file | ftp_rename() |
| RESET | Re-synch command/reply sequence with remote server | |
| RESTART | Restart the following get or put command at the marker specified | |
| RHELP | Get remote help | |
| RMDIR | Remove remote directory | ftp_rmdir() |
