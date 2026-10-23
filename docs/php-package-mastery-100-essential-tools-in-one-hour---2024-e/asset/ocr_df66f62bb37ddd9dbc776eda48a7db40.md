# 14. file_exists and is_writable

The file_exists function checks if a file or directory exists, and is_writable checks if a file or directory is writable. These are critical for verifying access permissions and existence before attempting file operations.

```
```php
Ex:file_exists and is_writable
if (file_exists('example.txt') && is_writable('example.txt')) {
    file_put_contents('example.txt', "Appending new content.", FILE_APPEND);
} else {
    echo "File does not exist or is not writable.";
}
```
```

If 'example.txt' exists and is writable, it appends "Appending new content." to the file. Otherwise, it outputs "File does not exist or is not writable."

This code snippet demonstrates a practical use case involving file manipulation while ensuring that the operations are safe to perform. The file_exists('example.txt') function checks if the specified file or directory exists, which is crucial to avoid errors in attempting to access or modify a non-existent file.The is_writable('example.txt') function checks if the file