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
| getcsv(int fp, int length) | array | Gets line from file pointer and parses for CSV fields |
| realpath(string path) | string | Returns the resolved path, from root. Works on symbolic links and references using .. |