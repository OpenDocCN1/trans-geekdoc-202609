# TABLE E-5 DIRECTORY FUNCTIONS

| Function | Returns | Action |
| --- | --- | --- |
| opendir(string path) | int | Opens a directory and return a dir_handle |
| dir(string directory) | class | Returns an object with three methods (read, rewind, and close) and two properties (handle and path) |
| closedir([int dir_handle]) | void | Closes directory connection identified by the dir_handle |
| chdir(string directory) | int | Changes the current directory |
| getcwd(void) | string | Gets the current directory |
| reindir([int dir_handle]) | void | Rewinds dir_handle back to the start |
| readdir([int dir_handle]) | string | Readsdirectory entry from dir_handle |

# TABLE E-6 FILESYSTEM FUNCTIONS

| Function | Returns | Action |
| --- | --- | --- |
| diskfreespace(string path) | double | Gets free diskspace for filesystem that path on, in bytes |
| chown(string filename, mixed user) | bool | Changes file owner. Returns TRUE on success, otherwise FALSE |
| chgrp(string filename, mixed group) | bool | Changes file group. Returns TRUE on success, otherwise FALSE |
| chmod(string filename, int mode) | bool | Changes file mode. Returns TRUE on success, otherwise FALSE |
| touch(string filename [, int time]) | bool | Sets modification time of file |
| clearstatcache(void) | void | Clears file stat cache |
| fileperms(string filename) | int | Gets file permissions in octal |
| inode(string filename) | int | Gets file inode |
| filesize(string filename) | int | Gets file size |