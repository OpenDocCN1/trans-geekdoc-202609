```
// Opening the current directory
$dir = opendir($dirname);
// A loop to read the current directory
while (($file = readdir($dir)) != false)
{
    // If the item is a file, processing its contents
    if($file != "." && $file != "..")
    {
        // If the current entry is a file,
        // opening it to count the lines
        if(is_file($dirname."/"$file))
        {
            // Extracting the file's extension
            $ext = strchr($dirname."/"$file, ".");
            foreach($extensions as $exten)
            if (preg_match($exten, $ext))
            {
                // Reading the file's contents
                $content = file($dirname."/"$file);
                // Counting the lines
                $count += count($content);
                // Deleting the array
                unset($content);
            }
        }
        // If the current entry is a directory,
        // calling the scan_dir() function recursively
        if(is_dir($dirname."/"$file))
        {
            scan_dir($dirname."/"$file);
        }
    }
}
// Closing the directory
closedir($dir);
}

// The name of the project's root directory
$dirname = ".";

// An array to hold the extensions of the
```