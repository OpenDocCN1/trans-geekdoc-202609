This says, “If the filename is *not* a directory, continue with the next iteration.”
And remember, as usual, you need to call `closedir` after all this directory
searching is finished.

# Recursively listing a directory

If you want to find out not only the filenames and subdirectories in a directory,
but also the filenames and subdirectories in the *subdirectories* (that is,
you want to get a recursive listing, which means you want to get every sub-
directory of every subdirectory of every subdirectory . . .), I suggest not
using the `opendir` and `readdir` procedure. Instead, use the File module’s
`Find` function. Doing so is easy, as you can see in the following code:

```
use File::Find;

sub PrintFile {
  $name = $File::Find::name;
  print "$name\n";
}

find (\&PrintFile, "/tmp");
```

The first line of this code says you want to use the `Find` function inside the
File module. The next line begins the definition of a subroutine that will
serve as a *callback function*. When you perform your search using the `Find`
function, the `Find` function calls your callback function for each file that
it finds. Inside this subroutine, I extract the name of that file using this
expression:

```
$File::Find::name
```

I save this value in the `$name` string, and then I print out the string. But
remember, this is all inside a subroutine that will get called for each file.
The next line is the call to `Find` that recursively finds all the files. The first
parameter in the call to `Find` is oddly looking; it’s a reference to the subroutine.
(The `\&` means you’re obtaining a reference to the subroutine.) The next parameter is the string representing the directory where you want to
start your search.

Here’s some sample output where I have a /tmp directory containing four
files (`a.txt`, `b.txt`, `c.txt`, and `d.txt`), and two subdirectories (`subdir1`
and `subdir2`). Additionally, `subdir1` has a single file in it called `a1.txt`.

```
/tmp
/tmp/b.txt
```