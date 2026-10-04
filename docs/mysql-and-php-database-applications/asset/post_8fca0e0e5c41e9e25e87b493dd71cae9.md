
# Appendix E: PHP Function Reference

| Function | Returns | Action |
| --- | --- | --- |
| fileowner(string filename) | int | Gets file owner's userid |
| filegroup(string filename) | int | Gets file's groupid |
| fileat(string filename) | int | Gets last access time of file |
| filetime(string filename) | int | Gets last modification time of file |
| filectime(string filename) | int | Gets inode modification time of file |
| filetype(string filename) | string | Gets file type |
| is_writable(string filename) | int | Returns true if file can be written |
| is_readable(string filename) | int | Returns true if file can be read |
| is_executable(string filename) | int | Returns true if file is executable |
| is_file(string filename) | int | Returns true if file is a regular file |
| is_dir(string filename) | int | Returns true if file is directory |
| is_link(string filename) | int | Returns true if file is symbolic link |
| file_exists(string filename) | bool | Returns true if filename exists |
| lstat(string filename) | array | Gives information about a file or symbolic link. The returned array contains the following elements: device, inode; protection mode; number of links; user id of owner; group id owner; device type if inode device; size in bytes; time of last access; time of modification; time of last change; blocksize for filesize I/O; number of blocks allocated |
| stat(string filename) | array | Gives information about a file, the same as described in lstat |

# Part V: Appendixices

# TABLE E-7 EXECUTION FUNCTION

| Function | Returns | Action |
|---|---|---|
| exec(string command [, array output [, int return_value]]) | int | Executes an external program |
| system(string command [. int return_value]) | int | Executes an external program and displays output |
| passthru(string command [. int return_value]) | void | Executes an external program and draws raw output. Usually will be used with something like PBMPlus |
| escapeshellcmd(string command) | string | Escapes shell metacharacters |

# TABLE E-8 FILE MANIPULATION FUNCTIONS

| Function | Returns | Action |
|---|---|---|
| flock(int fp, int operation [. int wouldblock]) | bool | Locks a file so that it is not accessible by other PHP scripts. The locking will not keep other processes from opening the file |
| get_meta_tags(string filename [, int use_include_path]) | array | Extracts all <meta> tag content from a file and returns an array |
| file(string filename [, int use_include_path]) | array | Reads entry file into an array, with each line as an element |
| tempnam(string dir, | string | Creates a unique filename in a string prefix)/directory |
| tmpfile(void) | int | Creates a temporary file that will be deleted automatically after a call fclose() function or at the end of the script |
| fopen(string filename, string mode [, int use_include_path]) | int | Opens a file or a URL and returns a file pointer |

# Appendix E: PHP Function Reference 453

| Function | Returns | Action |
| --- | --- | --- |
| fclose(int fp) | int | Closes an open file pointer |
| open(string command, string mode) | int | Executes a command and opens either a read or a write pipe to it |
| pclose(int fp) | int | Closes a file pointer opened by open() |
| feof(int fp) | int | Tests for end-of-file on pointer |
| set_socket_blocking(int socket_descriptor, int mode) | int | Sets blocking/non-blocking mode on a socket |
| socket_set_timeout(int socket_descriptor, int seconds, microseconds) | bool | Sets timeout on socket read to seconds + microseconds |
| socket_get_status(resource socket_descriptor) | array | Returns an array describing socket status. The array contains four elements: timed_out (bool), eof (bool), and unbound bytes (int) |
| fgets(int fp, length) | string | Gets a line from file pointer |
| fgetc(int fp) | string | Gets a character from file pointer |
| fgets(int fp, length, [. string allowable_tags]) | string | Gets a line from file pointer and strips HTML tags |
| sscanf(string str, string format [, string ...])]) | mixed | Formats a file using the specified format |
| fwrite(int fp, string str, [int length]) | int | Implements a binary-safe file write |
| fflush(int fp) | int | Flushes output |
| set_file_buffer(int fp, int buffer) | int | Sets file buffer; the default size is 8 kb |
| rewind(int fp) | int | Moves the position of a file pointer to the beginning of a file |
| ftell(int fp) | int | Gets file pointer's read/write position |

Continued

# Table E-8 FILE MANIPULATION FUNCTIONS (Continued)

| Function | Returns | Action |
| --- | --- | --- |
| fseek(int fp, int offset [, int whence]) | int | Seeks the position of a file pointer |
| mkdir(string pathname, int mode) | int | Creates a directory |
| rmdir(string dirname) | int | Removes a directory |
| readfile(string filename, [. int use_include_path]) | int | Outputs a file or a URL |
| umask([int mask]) | int | Returns or changes the umask. See the Unix man page on umask for further details |
| fpassthru(int fp) | int | Outputs all remaining data from a file pointer |
| rename(string old_name, string new_name) | int | Renames a file |
| unlink(string filename) | int | Deletes a file, similar to the C unlink function |
| ftruncate(int fp, int size) | int | Truncates file to the size indicated in the second argument |
| fstat(int fp) | int | Returns the same information as stat() (described earlier) on a file handle |
| copy(string source_file, string destination_file) | int | Copies a file |
| fread(int fp, int length) | int | Conducts a binary-safe file read |
| getcsv(int fp, int length) | array | Gets line from file pointer |
| realpath(string path) | string | Returns the resolved path, from symbolic links |

# Appendix E: PHP Function Reference

| Function | Returns | Action |
| --- | --- | --- |
| sprintf(string format, mixed arg1 [, mixed ...]) | string | Returns a formatted string |
| printf(string format, mixed arg1 [, mixed ...]) | int | Outputs a formatted string |
| print_r(mixed var) | void | Prints out information about the variable |
| var_dump(mixed var) | void | Dumps a string representation of variable |

Table E-10 HTTP FUNCTIONS

| Function | Returns | Action |
| --- | --- | --- |
| header(string header) | void | Sends a raw header |
| setcookie(string name [, string value [, int expires [, string secure]]]) | void | Sends a cookie |
| headers_sent(void) | int | Returns true if headers have been sent; false otherwise |

Table E-11 HTML FUNCTIONS

| Function | Returns | Action |
| --- | --- | --- |
| htmlspecialchars(string string) | string | Converts special characters (ampersand, double quotes, single quotes, less than, and greater than) to HTML entities |
| htmlntities(string string) | string | Converts all applicable characters to HTML entities |
| get_html_translation_table([int whichone]) | array | Returns the translation table used by htmlspecialchars and htmlntities |

Table E-12 MAIL FUNCTION

| Function | Returns | Action |
| --- | --- | --- |
| mail(string to, string subject, string additional_ headers[]) | int | Sends an e-mail message |

Table E-13 RANDOM NUMBER FUNCTIONS

| Function | Returns | Action |
| --- | --- | --- |
| srand(int seed) | void | Seeds random number generator |
| rand(int min, int max) | int | Returns a random number |
| getrandmax(void) | int | Returns the maximum value a random number can have |
| mt_srand(int seed) number generator | void | Seeds Mersenne Twister |
| mt_rand([int min, int max]) | int | Returns a random number from Mersenne Twister |
| mt_getrandmax(void) | int | Returns the maximum value a random number from Mersenne Twister can have |

Table E-14 REGULAR EXPRESSION FUNCTIONS

| Function | Returns | Action |
| --- | --- | --- |
| ereg(string pattern, string string [, array registers]) | int | Conducts a regular expression match |
| erei(string pattern, string string [, array registers]) | int | Case-insensitive regular expression match |
| ere_replace(string pattern, string replacement, string string) | string | Replaces regular expression |
| eregi_replace(string pattern, string replacement, string string) | string | Conducts a case-insensitive replace regular expression |
| split(string pattern, string string [, int limit]) | array | Splits string into array by regular expression |
| spliti(string pattern, string string [, int limit]) | array | Splits string into array by case-insensitive regular expression |
| sql_regcase(string string) | string | Makes regular expression for case-insensitive match |
