```
///////////////////////////////////////////////////////
// Defining a recursive descending function
///////////////////////////////////////////////////////
function descend($dirname, $dirdestination)
{
    // Opening the directory
    $dir = opendir($dirname);
    // Looping through the directory outputting the contents
    while (($file = readdir($dir)) != false)
    {
        echo $file."<br";
        // If it's a file, copying it
        if (is_file($dirname."/"$file))
        {
            copy($dirname."/"$file, $dirdestination."/"$file);
        }
        // If it's a directory, creating it
        if (is_dir($dirname."/"$file)) &&
            $file != \." &&
            $file != ""
        {
            // Creating a directory
            if (!mkdir($dirdestination."/"$file))
            {
                echo "Can't create ".$dirdestination."/"$file.".\n";
            }
            // Calling the recursive descend function
            descend($dirname."/"$file, "$dirdestination."/"$file");
        }
    }
    // Closing the directory
    closedir($dir);
}
?
```

# ## II.3.24. Hacking a Guest Book

The reason the code shown in Listing I.3.3 is vulnerable is that the messages appended to the file are not filtered. Consequently, JavaScript, as well as PHP scripts, can be embedded into a message. This circumstance can be used for malicious purposes. For example, sending the script shown in Listing II.3.37 will delete all files in the current directory.