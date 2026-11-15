Now you can test the script:

```
$ ./hello.php --name=Matt --pet=Rover
Number of arguments: 3

Argument list:

Array
(
    [0] => ./hello.php
    [1] => --name=Matt
    [2] => --pet=Rover
)
```

There are a couple of things to note here. First of all the first “argument” ($argv[0]) is always the name of the script itself. Secondly, PHP doesn’t make any attempt to separate the argument names from the argument values. Indeed, the "--" and "=" characters are just conventions; as far as the PHP engine is concerned, the command-line arguments are anything after the script name, with each argument separated by a space.

Here’s an enhanced hello.php script. This script loops through $argv and separates the argument names from the argument values, removing the initial “--” from the argument names, and storing the resulting values in an $arguments array, keyed by argument name. It then queries the $arguments array to display the output to the user:

```
#!/usr/bin/php
<?php
$arguments = array();

foreach ( $argv as $arg ) {
    list( $argName, $argValue ) = split( "=", $arg );
    $argName = preg_replace( "/^--/", "", $argName );
    $arguments[$argName] = $argValue;
}

echo "Hello, " . $arguments["name"] . "!\n";
echo "Your pet is called " . $arguments["pet"] ". \n";
?>
```

Here’s how this script looks when run:

```
$ ./hello.php --name=Matt --pet=Rover
Hello, Matt! Your pet is called Rover.
```

# Creating Interactive Scripts

Because there are no Web form controls for a user to interact with, a command-line script is limited to prompting the user for input (unless the script has a GUI). Fortunately, prompting for and reading input is easy to do. When running a PHP script from the command line, the PHP engine automatically opens three standard streams for you: