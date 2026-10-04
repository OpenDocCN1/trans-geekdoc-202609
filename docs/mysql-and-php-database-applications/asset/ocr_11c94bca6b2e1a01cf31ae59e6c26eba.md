# Appendix E: PHP Function Reference 477

PHP must be compiled with --enable-dba in order to use these functions.

# TABLE E-28 FTP FUNCTIONS

| Function | Returns | Action |
| --- | --- | --- |
| ftp_login(int stream, string username, password) | int | Logs into the FTP server |
| ftp_pwd(int stream) | string | Returns the present working directory |
| ftp_cdup(int stream) | int | Changes to the parent directory |
| ftp_chdir(int stream, string directory) | int | Changes directories |
| ftp_mkdir(int stream, string directory) | string | Creates a directory |
| ftp_rmdir(int stream, string directory) | int | Removes a directory |
| ftp_nlist(int stream, string directory) | array | Returns an array of filenames in the given directory |
| ftp_rawlist(int stream, string directory) | array | Returns a detailed listing of the directory as an array of output lines |
| ftp_type(int stream) | string | Returns the system type identifier |
| ftp_fget(int stream, int fp, int remote_file, int mode) | int | Retrieves a file from the FTP server and writes it to an open file |
| ftp_pasv(int stream, int pasv) | int | Turns passive mode on or off |

Continued