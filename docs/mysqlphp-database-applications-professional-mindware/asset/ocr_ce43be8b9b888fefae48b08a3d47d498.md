| Function | Returns | Action |
|---|---|---|
| fclose(int fp) | int | Closes an open file pointer |
| popen(string command, string mode) | int | Executes a command and opens either a read or a write pipe to it |
| pclose(int fp) | int | Closes a file pointer opened by popen() |
| feof(int fp) | int | Tests for end-of-file on a file pointer |
| set_socket_blocking(int socket_descriptor, int mode) | int | Sets blocking/non-blocking mode on a socket |
| socket_set_timeout(int socket_descriptor, int seconds, int microseconds) | bool | Sets timeout on socket read to seconds + microseconds |
| socket_get_status(resource socket_descriptor) | array | Returns an array describing socket status. The array contains four elements: timed_out (bool), blocked (bool), eof (bool), and unread bytes (int) |
| fgets(int fp, int length) | string | Gets a line from file pointer |
| fgetc(int fp) | string | Gets a character from file pointer |
| fgetss(int fp, int length [, string allowable_tags]) | string | Gets a line from file pointer and strips HTML tags |
| fscanf(string str, string format [, string ...]) | mixed | Formats a file using the specified format |
| fwrite(int fp, string str [, int length]) | int | Implements a binary-safe file write |
| fflush(int fp) | int | Flushes output |
| set_file_buffer(int fp, int buffer) | int | Sets file write buffer; the default size is 8 kb |
| rewind(int fp) | int | Moves the position of a file pointer to the beginning of a file |
| ftell(int fp) | int | Gets file pointer's read/write position |