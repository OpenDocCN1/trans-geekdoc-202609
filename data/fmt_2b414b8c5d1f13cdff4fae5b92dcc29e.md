
# UNIX 命令参考

## 基础命令

- `put file1 [file2]`
- `pwd`
- `rmdir directory`
- `rev file1 [file2]` (retrieve from remote)
- `remotehelp command`
- `rename file1 file2`
- `send file1 [file2]`

## 常用命令详解

| UNIX Command | Explanation | Example | End Results |
| :--- | :--- | :--- | :--- |
| `date` | Writes the current date to the screen | `date` | Mon Nov 20 18:25:37 EST 2000 |
| `sort infile` | Sorts the contents of the input file in alphabetical order | `sort names` | Sorts the contents of `names` in alphabetical order |
| `who` | Tells who is logged onto your server | `who` |  |
| `who am i` | Tells you your user information | `who am i` |  |
| `clear` | Clears the window and the line buffer | `clear` |  |
| `echo whatever I type` | Writes `whatever I type` to the screen | `echo hey you!` | Writes `hey you!` to the screen |
| `banner big words` | Does the same thing as echo only in big words | `banner hey!` | Writes `hey!` in large letters on the screen |
| `cat file1 file2 file3` | Shows the three files in consecutive order as one document (can be used to combine files) | `cat cheese milk` | Prints the `cheese` file to the screen first and immediately follows it with the `milk` file |
| `df system` | Reports the number of free disk blocks | `df`<br>`df $home` | Both commands will print the total kb space, kb used, kb available, and %used on the home system (your system) |
| `head file` | Prints the first 10 lines of the file to the screen | `head addresses` | Prints the first 10 lines of `addresses` to the screen |
|  | Number of lines can be modified | `head -25 addresses` | Prints the first 25 lines of `addresses` to the screen |
| `tail file` | Prints the last 10 lines of the file to the screen. Number of lines can be modified | `tail test.txt` | Prints the last 10 lines of `test.txt` to the screen |
|  | Number of lines can be modified | `tail -32 test.txt` | Prints the last 32 lines of `test.txt` to the screen |
| `more input` | Prints to screen whatever is input—useful because it only shows one screen at a time.<br>Scroll bar continues to the next screen<br>Return moves one line forward<br>`q` quits<br>`g` goes to the end<br>`1g` goes to the beginning<br>`Ctrl+u` moves up screen<br>`Ctrl+d` moves down screen | `more groceries` | Will list the groceries file to the screen |

## 目录列表命令 (`ls`)

| Command | Explanation | Example | End Result |
| :--- | :--- | :--- | :--- |
| `ls` (-option optional) | Lists all the non-hidden files and directories | `ls`<br>`ls bin` | Lists all non-hidden files and directories in the current directory<br>Lists all non-hidden files and directories in the `bin` directory |
| `ls -l` or `ll` | Lists all non-hidden files and directories in long format | `ls -l`<br>`ll`<br>`ls -l work`<br>`ll work` | Lists all non-hidden files and directories in the current directory in long format<br>Lists all non-hidden files and directories in the `work` directory in long format |
| `ls -a` | Lists all files and directories including hidden ones | `ls -a`<br>`ls -a temp` | Lists all files and directories, including hidden, in the current directory<br>Lists all files and directories in the `temp` directory |
| `ls -r` | Lists all files and directories in reverse alphabetical order | `ls -r`<br>`ls -r abc` | Lists all non-hidden files and directories in the current directory in reverse alphabetical order<br>Lists all non-hidden files and directories in the `abc` directory in reverse alphabetical order |
| `ls -t` | Lists all non-hidden files in the order they were last modified | `ls -t`<br>`ls -t work` | Lists all the non-hidden files in the current directory in the order they were last modified from most recent to last<br>Lists all the non-hidden files in the `work` directory in the order they were last modified from most recent to last |

> **Note:** Options can be combined using `ls`.
> Example: `ls -al` — Lists all files (including hidden (`-a`)) in long format (`-l`)

## 重要字符

| Character | Explanation | Example | End Result |
| :--- | :--- | :--- | :--- |
| `|` (Pipe) | Directs the output of the first command to the input of another | `ls -l \| more` | Lists your files in long format one screen at a time |
| `>` | Sends the output of a command to a designated file | `ls -l > myfiles` | Prints your listing to a file named `myfiles` |
| `>>` | Appends the output of a command to a designated file | `ls -l >> allfiles` | Appends your filenames to the end of the `allfiles` file |
| `&` | Runs command in the background; you can still work in the window | `xclock &` | Runs xclock (a clock) allowing you to keep working |

## 特殊字符

| Character | Explanation | Example | End Result |
| :--- | :--- | :--- | :--- |
| `~` | Designates the home directory (`$HOME`) | `echo ~` | Writes your home directory to the screen |
| `<` | Designates input from somewhere other than terminal | `progA < input1` | ProgA program gets its input from a file named `input1` |

## 通配符

| Wildcard | Explanation | Example | End Result |
| :--- | :--- | :--- | :--- |
| `*` | Any string of characters | `ls *.c` | Lists any file or directory (non-hidden) ending with `.c` |
| `?` | Any one character | `ls file?` | Lists any file/directory with `file` and 1 character at the end |
| `[]` | Match any character in the brackets (a hyphen is used for ranges of characters) | `ls v[6-9]file` | Lists `v6file`, `v7file`, `v8file`, and `v9file` |

## 目录与文件管理命令

| Command | Explanation | Example | End Result |
| :--- | :--- | :--- | :--- |
| `cd directory` | Changes your current directory to the directory specified | `cd bin`<br>`cd ..`<br>`cd ../..` | Changes directory to the `bin` directory<br>Moves you to the directory that contains the directory you are currently in (e.g., Current directory=/home/users/bob/bin execute `cd ..` New directory=/home/users) |
|  |  | `cd -`<br>`cd ~`<br>`cd` | Moves you to the directory you just came from<br>Each will move you to your home directory (the directory you start from initially) |
| `mkdir dirname` | Creates a directory | `mkdir junk` | Makes a directory named `junk` in your current directory |
|  | Also allows you to designate where the directory is to reside | `mkdir ~/left` | Makes a directory in your home directory named `left` |
| `rm file1 file2 file3` | Removes (deletes) file(s) | `rm xyz`<br>`rm xyz abc`<br>`rm *` | Deletes a file named `xyz`<br>Deletes the files named `xyz` and `abc`<br>Deletes everything non-hidden |
| `rm -i file1 file2` | Prompts before deletion of files | `rm -i *` | Prompts at each non-hidden file and lets you decide whether or not to delete it |
| `rm -f file1 file2` | Forces deletion without prompt regardless of permissions | `rm -f program` | Removes the file `program` without regard to permissions, status, etc. |
| `rm -r directory`<br>`rm -R directory` | Remove a directory along with anything inside it | `rm -r bin`<br>`rm -R bin` | Each will remove the `bin` directory and everything inside of it |
| `rmdir directory` | Removes a directory like `rm -r` does if the directory is empty | `rmdir bin` | Removes the `bin` directory if it is empty |
| `rm -fR name`<br>`rm -Rf name` *dangerous* | This combination will force the removal of any file and any directory including anything inside it | `rm -Rf c_ya` | Forces removal without prompts of the `c_ya` directory and anything inside it |
| `rm -Ri directory` | Deletes the contents of a directory and the directory if it is empty by prompting the user before each deletion | `rm -Ri rusure` | Deletes anything in the directory called `rusure` that you verify at the prompt, and if you remove everything in the directory, you will be prompted whether you want to remove the directory itself or not |

> **Note:** Options can be combined using `rm`.
