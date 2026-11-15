+   stdin is used for reading user input. PHP gives you a handle to the opened stdin stream in the form of the constant STDIN.

+   stdout is used for sending output back to the shell (which usually results in displaying it in the terminal window, much like using print or echo). PHP gives you a handle to the opened stdout stream as the constant STDOUT.

+   stderr is for outputting error messages. As with stdout, this usually defaults to the terminal window, but can be redirected by the shell (to an error log, for example). You can access this opened stream through the handle STDERR.

Because STDIN, STDOUT, and STDERR are streams, you can read from and write to them just like files (see Chapter 11 for more on PHP’s file handling functions). Here’s a simple example that prompts the user for his address and contact details, then generates a signature file suitable for including in an email message:

```
#!/usr/bin/php
<?php
echo "Welcome to the signature file generator.\n";
echo "Please enter your full name: ";
$name = trim( fgets( STDIN ) );
echo "Please enter your street address: ";
$address = trim( fgets( STDIN ) );
echo "Please enter your city: ";
$city = trim( fgets( STDIN ) );
echo "Please enter your state: ";
$state = trim( fgets( STDIN ) );
echo "Please enter your zip code: ";
$zip = trim( fgets( STDIN ) );
echo "Please enter your phone number: ";
$phone = trim( fgets( STDIN ) );
echo "Please enter your email address: ";
$email = trim( fgets( STDIN ) );
echo "Please enter a name for this signature: ";
$sig = trim( fgets( STDIN ) );
$data = "\n--\n$name\n$address\n$city, $state $zip\n$phone\n$email\n";
$sigfile = fopen( $sig, "w" ) or die( "Could not open file for writing\n" );
fwrite( $sigfile, $data ) or die( "Failed writing data\n" );
fclose( $sigfile );
echo "Your signature file is ready now.\n";
?>
```