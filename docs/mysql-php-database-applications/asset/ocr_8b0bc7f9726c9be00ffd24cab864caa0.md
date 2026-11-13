| Function | Return Value | Action |
| :--- | :--- | :--- |
| ftp_size(resource stream, string filename) | int | Returns the size of the file, or -1 on error |
| ftp_mdtm(resource stream, string filename) | int | Returns the last modification time for the file, or -1 on error |
| ftp_rename(resource stream, string src, string dest) | bool | Renames the given file to a new path |
| ftp_delete(resource stream, string file) | bool | Deletes a file |
| ftp_site(resource stream, string cmd) | bool | Sends a SITE command to the server |
| ftp_close(resource stream) | void | Closes the FTP stream |
| ftp_set_option(resource stream, int option, mixed value) | bool | Sets an FTP option |
| ftp_get_option(resource stream, int option) | mixed | Gets an FTP option |

# TABLE F-25 CYBERCASH FUNCTIONS

| Function | Return Value | Action |
| :--- | :--- | :--- |
| cybercash_encr(string wmk, string sk, string data) | array | CyberCash encrypt |
| cybercash_decr(string wmp, string sk, string data) | array | CyberCash decrypt |
| cybercash_base64_encode(string data) | string | base64 encode data for CyberCash |
| cybercash_base64_decode(string data) | string | base64 decode data for CyberCash |