
# 156 Part II: Solutions

HTTP headers are considered in more detail in Chapter II.10.

The posed problem of developing a script for storing text and graphics files can be solved using HTTP headers, as is shown in Listing II.3.7.

## Listing II.3.7. A script for saving text and graphics files

The script takes the file name as a GET parameter, for example, index.php?down=file.txt. The name of the file to save, which is determined by the filename attribute, is specified by the first HTTP header. In the script, the filename parameter is the same as the file name, but any name can be used. The second HTTP header tells the browser that the file is binary and should not be interpreted. The third line uses the file_get_contents() function to extract the contents of the file sent using the $_GET['down'] parameter and displays them in the browser window.

It is important that, after the file's contents are output, nothing else is output into the stream by either the echo statement or the direct output; otherwise, all this will be appended to the file. This includes possible spaces and line feeds after the closing >> tag.

## II.3.6. Determining File Size

A file's size can be determined using the filesize() function, which takes a file's name as the argument and returns its size in bytes, kilobytes, or megabytes, depending on the file's size. The size can be determined by a script like the one shown in Listing II.3.8.

## Chapter II.3: Working with Files 157

## Listing II.3.8. A function for determining file size

```php
<?php
echo filesize($_GET['name']);
// A function for determining file size
function getfilesize($filename)
{
    // Checking whether the file exists
    if(!file_exists($filename)) return "No such file";
    // Determining the file's size
    $filesize = filesize($filename);
    // If the file is larger than 1024 bytes,
    // calculating the size in kilobytes
    if($filesize > 1024)
    {
        $filesize = (float) ($filesize/1024);
        // If the file is larger than 1024 KB,
        // calculating the size in megabytes
        if($filesize > 1024)
        {
            $filesize = (float) ($filesize/1024);
            // Rounding to the first decimal place
            $filesize = round($filesize, 1);
            return $filesize." MB";
        }
        else
        {
            // Rounding to the first decimal place
            $filesize = round($filesize, 1);
            return $filesize." KB";
        }
    }
    else
    {
        return $filesize." byte";
    }
}?>
```

The script takes the file's name as the parameter and checks first whether the file size returned by the filesize() function is larger than 1 KB, and then whether it's larger than 1 MB. In each case, the file's size in the corresponding units is returned.

## II.3.7. Determining the Number of Lines in a File

The simplest solution to counting lines is to use the file() function. The function takes a file name as the argument and returns an array, each element of which contains a single line from the file. The remaining task is to count the number of elements in the returned array. A script for solving the problem is shown in Listing II.3.9.

## Listing II.3.9. Determining the number of lines in a file

```php
<?php
echo getlinecount($_GET['name']);

function getlinecount($filename)
{
    // Checking whether the file exists
    if(!$file_exists($filename)) return "No such file!";
    // Breaking the file into separate lines
    // using the file() function
    $filearr = file($filename);
    // Counting and returning the number of lines in a file
    return count($filearr);
}
?>
```

## II.3.8. Reversing the Line Order in a File

As the previous example, the line order problem can be solved using the file() function to break the file into individual lines. The line order in the obtained array can then be reversed using the array_reverse() function. Finally, the implode() function is used to convert the array into a string, which is then written to the file (Listing II.3.10).

## Chapter II.3: Working with Files 159

## Listing II.3.10. Reversing the line order in a file

```php
<?php
// Breaking the file into separate lines
// using the file() function
$Arr = file("text.txt");
// Reversing the order of the array elements
$Arr = array_reverse($Arr);
// Converting the array into a string and
// rewriting the contents of the text.txt file
$fd = fopen("text.txt", "w");
if ($fd) {
    fwrite($fd, implode("", $Arr));
    fclose($fd);
}
?>
```

## II.3.9. Listing Files and Subdirectories

The best way to traverse a directory and its subdirectories is to recursively descend the directory tree. This can be done using the scan_dir() script (Listing II.3.11), which extracts the contents of the current directory and displays the names of its files and subdirectories. If a function encounters a subdirectory, it recursively calls itself, passing the subdirectory as the argument.

Listing files and subdirectories.

## Listing II.3.11. Listing files and subdirectories

```php
<?php
///////////////////////////////////////
// A recursive function to descend the directory tree
///////////////////////////////////////
function scan_dir($dirname)
{
    // Opening the current directory
    $dir = opendir($dirname);
```

Part II: Solutions

$dirname = ".";
// Calling the function that recursively
// the subdirectories of the root directory
scan_dir($dirname);

When traversing the directory, it important to exclude the . (current) and .. (parent) directories to prevent an endless loop.

## II.3.10. Counting Files

The problem of counting files is also solved using the recursive descent technique (Listing II.3.12). However, information is displayed only if the current item is a directory. Files in directories are counted using the filesize() function.

Chapter II.3: Working with Files

## Listing II.3.12. Counting files in directories

```php
<?php
////////////////////////////////////////////////
// A recursive function to descend the directory tree
////////////////////////////////////////////////
function scan_dir($dirname)
{
    // Opening the current directory
    $dir = opendir($dirname);
    // A loop to read the current directory
    while (($file = readdir($dir)) != false)
    {
        // Checking whether $file variable equals
        // the current or upper-level directory
        if($file != "." && $file != "..")
        {
            // If the current entry is a directory,
            // calling the scan_dir() function
            if(is_dir($dirname."/"$file))
            {
                echo $dirname."/"$file." - ";
                file_count($dirname."/"$file)."<br>";
                scan_dir($dirname."/"$file);
            }
        }
    }
    // Closing the directory
    closedir($dir);
}
////////////////////////////////////////////////
// A function to count the files in a directory
////////////////////////////////////////////////
function file_count($dirname)
{
    // A counter variable
    $count = 0;
    // Opening the current directory
    $dir = opendir($dirname);
    // Reading the contents looping through the directory
    while($file = readdir($dir))
    {
      // If the current item is a file, counting it
      if(is_file($dirname."/"$file)) ++$count;
    }
    // Closing the directory
    closedir($dir);
    return $count;
}
```

162 Part II: Solutions

## II.3.11. Counting Lines in Project Files

Lines in project files are counted by recursively traversing the project’s directory and counting the lines in files whose extension matches those specified in the $extensions array (Listing II.3.13). The array is declared to be global, so you need not pass the reference to it using the parameters of the scan_dir() recursive function. Moreover, the $count variable, which stores the current number of lines, is declared.

## Listing II.3.13. Counting the lines in project files

```php
<?php
///////////////////////////////////////
// A recursive function to descend the directory tree
///////////////////////////////////////
function scan_dir($dirname)
{
  // Declaring global replacement variables
  GLOBAL $extensions, $count;
```
