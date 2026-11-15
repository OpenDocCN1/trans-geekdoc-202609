ify a maximum length for how much data should be written. This may be interesting if you want to accept and shorten data from an external source such as a database or from the user. In any case, make sure that you have previously opened the file in a mode with write access (i.e., not in r mode).

```
<?php
if ($file = fopen("test.txt", "wb")) {
    if (fwrite($file, "All of life is a test\r\n") &&
        fwrite($file, "and we are only the candidates.")) {
        echo "File has been filled!";
    } else {
        echo "Error while writing!";
    }
    fclose($file);
} else {
    echo "File could not be opened!";
}
?>
```

# Listing 25.2 The File Is Filled (“file-write.php”)

The return value of fwrite() is the number of bytes written—or false if writing was not possible. This is shown in the code from Listing 25.2. Figure 25.2 shows the new content of the file.

![](bbox=[0.139, 0.53, 0.49, 0.655])

# Figure 25.2 The Data Is in the File

# Write Files in Fast Forward

This went relatively quickly, but three calls are still required: fopen(), fwrite(), and fclose(). In one step, you can use the file_put_contents() function. You only specify the file name and the data to be written; PHP does the rest. The return value of the function is the size of the new file, or false if something went wrong:

```
<?php
file_put_contents("test.txt",
    "All of life is a test\r\n");
?>
```