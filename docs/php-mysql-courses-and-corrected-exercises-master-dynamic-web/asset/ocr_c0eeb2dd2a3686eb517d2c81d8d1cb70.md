error code ($this->getCode()). The getFile(), getLine() and getCode() methods are native methods of the Exception class.

**FileException class constructor:** The class constructor takes an optional $message parameter, which represents the error message to be displayed when a FileException is thrown. By default, this message is defined as "File error". The constructor then calls the constructor of the parent Exception class, passing the error message.

**readFile() function:** This function takes the path of the file to be read as a parameter. It first checks whether the file exists, using the **file_exists()** function. If the file does not exist, it throws a FileException with a specific error message indicating that the file does not exist. Otherwise, it simulates the reading of the file, returning a message indicating the file's contents.

Using the function with exception handling: The code uses the fileRead() function to read the contents of a file named "example.txt". It is surrounded by a **try-catch** block to catch any FileException. If an exception is thrown, the error message is displayed to the user, along with further details provided by the exception's **fileInfo()** method.

In summary, this code illustrates the creation and use of a custom exception to handle errors specific to file operations, while providing additional information to facilitate debugging and troubleshooting.

At this point, if you run the fileRead.php file, you will get a result similar to the following: