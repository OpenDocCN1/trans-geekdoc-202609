
Prior to this example, I created a file called myfile.txt. Then in this example, I copied the file to myfile2.txt. Then I tried copying the file again, but because the myfile2.txt file already exists, I received an error message. So I tried again, but this time, I added the -force option, which did the trick.

Here's an example of delete. When I created the myfile.txt file, I gave it read-only permissions, meaning it can't be deleted without overriding the permissions:

```
% file delete myfile.txt
%
```

Oops; Tcl deleted the file without regard for permissions. For this reason, you need to be careful with the delete command. But this "deleting without regard for permission" isn't the case with directories because that's where the -force option applies. If you have a directory with files in it, delete won't delete the directory:

```
% file delete mydir
error deleting "mydir": directory not empty
%
% file delete -force mydir
%
```

At first, delete refused to delete mydir because I put some files in mydir. Instead, I received an error message. But then I tried again with the -force option, and this time delete deleted the directory for me.

The mkdir and rename commands are easy to use:

```
% mkdir newdirectory
% file rename test.txt newfilename.txt
```

Be careful using the -force option with directories because it will delete everything in them. Also, be careful with delete in general because a read-only permission won't prevent delete from deleting a file.

Additionally, you can use the following commands with files and directories; these are not subcommands of the file command:

- cd: This command changes the directory.
- pwd: This command prints the working directory.

Here's a short example program that demonstrates these two commands:

```
cd /tmp
puts [pwd]
```

The `cd` command takes as a single parameter the directory you want to switch to. (On both Linux and Windows, you can use the forward slash, as usual.) The `pwd` command returns a string representing the current directory; it doesn't actually print out the string. To print out the string, put the `pwd` command in quotes and print it with `puts`. Or save it to a variable like this:

```
set mydir [pwd]
```

In interactive mode (but not in a program), you can also use many of the usual shell commands, depending on your operating system. Here are some examples:

- dir: This command displays a directory listing. (Windows)
- ls: This command displays a directory listing. (Linux)
- copy: This command copies a file. (Windows)
- cp: This command copies a file. (Linux)

![](img/3f967ab8a8fddc723173059f56621648_309_0.png)

You can include all the usual options, such as `dir /s` on Windows or `ls -ltr` on Linux. Because all these commands are present, you can use `tclsh` as your shell, rather than the usual shell, if you prefer.

## Creating File Links

![](img/3f967ab8a8fddc723173059f56621648_309_1.png)

For you advanced users, Tcl includes a `link` command that lets you inspect or create a symbolic or hard link. This is something most Linux users are aware of; however, most people don't realize that links also exist on Windows 2000 and XP. But on these Windows operating systems, you can have only symbolic links for directories and hard links for files.

On Linux, to create a link called `file2` to an existing file called `file1`, use this line:

```
file link file2 file1
```

This results in a symbolic link, where the new file effectively points to the original file. The default is to create a symbolic link; however, you can be redundant and specify `-symbolic` as an option like so:

```
file link -symbolic file2 file1
```

Or, you can create a hard link, whereby you have two separate filenames aliased to the same file structure on the disk, like so:

```
file link -hard test2.txt test.txt
```

You can use these two techniques on either files or directories.

On Windows XP and 2000, you can create a hard link only for a file, like so, assuming file1.txt already exists:

```
file link -hard file2.txt file1.txt
```

After you run this command, you see what appears to be a copy of file1.txt. However, if you modify the contents of file2.txt, you also modify the contents of file1.txt, and vice versa. Amazing, no? Most people don't know this exists in Windows. (If you get an error message, it means you're not using an NTFS drive, even if you have Windows 2000 or XP. The error message you see is: could not create new link 'file2.txt' pointing to 'file1.txt': invalid argument.)

Directory links are interesting because you get to see something you might never have seen on Windows. For directories, you must specify the -symbolic option, even though on Linux that's the default. If you have a directory called testdir1, you can create a link like so:

```
file link -symbolic testdir2 testdir1
```

You then have two names for the same directory. In the DOS window, you see this, containing a rather interesting JUNCTION item (because Microsoft uses the term junction for a linked directory):

```
C:\temp\more>dir
Volume in drive C has no label.
Volume Serial Number is 9090-6698
Directory of C:\temp\more
08/31/2003 06:08 PM <DIR> .
08/31/2003 06:08 PM <DIR> ..
08/31/2003 06:08 PM 12 test1.txt
08/31/2003 06:08 PM 12 test2.txt
08/31/2003 06:12 PM <DIR> testdir1
08/31/2003 06:01 PM <JUNCTION> testdir2
4 File(s) 34 bytes
4 Dir(s) 12,648,849,408 bytes free
```

Anything you put in testdir1, you also see in testdir2 and vice versa; they are effectively the same directory just with different names. (But remember, this works only on an NTFS drive, not FAT or FAT32.)

## Chapter 6: Programming with the Tcl Packages

### In This Chapter

- Accessing files on the Web
- Manipulating text
- Building advanced data structures: queues, stacks, and records

Tcl comes standard with several extra packages that provide extended functionality. A package is a Tcl program that is stored inside a subdirectory under the special directory called `lib`.

Several of the main packages available with Tcl are collectively known as tcllib, which is supposed to stand for Standard Tcl Library. If you want to see a list of all the packages available and view the online docs, visit www.tcl.tk/software/tcllib/. Additionally Tcl ships with some other packages that aren't technically part of the Standard Tcl Library. In this chapter, I look at some of these available packages.

### Accessing Files on the Web

Tcl includes a handy package for accessing data on the Web. (This package isn't part of tcllib.) The following program accesses the Web site www.dummies.com and prints out the contents to the console:

```
package require http
set tok [http::geturl "www.dummies.com"]
set res [http::data $tok]
puts $res
```

Amazing: only four lines of code! This program first opens the package called http, which allows you to access the Web. Then the program calls http::geturl, which makes the connection to the site. The http::data command grabs the Web page, and I save the results to the res variable. Then I print out the variable.

However, this program gets stuck if the server sends back a redirection. If you try the preceding program on www.dummies.com, you won't see anything. Here, then, is a more sophisticated program that checks the error code. If the error code is between 300 and 399, then the response is a redirection request. In that case, I grab the redirection and try again. (This only works for redirections on the same server, however.)

```
package require http
set url "www.dummies.com"
set tok [http::geturl $url]
set ncode [http::ncode $tok]
puts $ncode
if {$ncode >= 300 && $ncode <=399} {
    # Redirect
    upvar #0 $tok state
    array set meta $state(meta)
    puts "Redirecting to $meta(Location)"
    http::cleanup $tok
    set tok [http::geturl "$url$meta(Location)"]
}
```

```
set res [http::data $tok]
puts $res
```

Now you can try this program on www.dummies.com, as I did here.

### Manipulating Text

The tcllib library includes a handy package called textutil. This package has several commands for manipulating text. Typically, it works like this: First you read all the text from a file into a single string; then you use textutil to manipulate the string, as I do in the following sections. Note also that in order to use the textutil library, you need the following command in your .tcl file prior to any textutil commands:

```
package require textutil
```

You then access the commands by typing two colons, textutil, two colons again, and the command. For example, if a command is indent, you type ::textutil::indent to specify this command.

### Adjusting indentation level

Want to change the indentation level of a text file (such as a file containing Tcl source)? Use the indent command found in the textutil package. Suppose this is a file called indenttest.txt:
