Create a new file named for example: fileRead.php, in which you put the following code:

```
<?php
// Define custom exception for file operations
class FileException extends Exception {
// Constructor with default message
public function __construct($message = "File error") {
parent::__construct($message);
}

// Function to addition additional information
public function fileInfo() {
return "Problem with file path: " . $this->getFile()
."<br>"
."Error line: " . $this->getLine()
."<br>"
."Error code: " . $this->getCode();
}
}

// File read function with custom exception handling
function fileRead($path) {
```