# Part II: Solutions

// Directory name
$dirname = ".";
// Calling the function that recursively descends
// the subdirectories of the root directory
scan_dir($dirname);

When traversing the directory tree, it important to exclude the . (current)
 and .. (parent) directories from the recursive descent to prevent an endless loop.

# II.3.10. Counting Files in Directories

The problem of counting files in directories is also solved using the recursive
descent technique (Listing II.3.12). However, here information is displayed only if
the current item is a directory. Files in a directory are counted using the special
file_count() function.