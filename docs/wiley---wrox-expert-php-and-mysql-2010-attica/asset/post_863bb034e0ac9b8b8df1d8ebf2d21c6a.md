
The base class takes care of validating the input as well as displaying the help if the input is invalid. The utility also calls for an interactive mode that will prompt the user for input. To accomplish that, it's necessary to read from standard input.

## Prompting for Input

Two types of input can come into an application from the standard input stream. The first is piped data and the second is direct user input. The base class takes care of the piped data so for now it is just necessary to handle the interactive mode (for when the user types ./phpcrypt --interactive or ./phpcrypt -i).

PHP automatically opens a handle to the standard input stream, standard output stream, and standard error stream when using PHP CLI. They are referenced via the STDIN, STDOUT, and STDERR, respectively. Alternatively the stream can be manually opened. For example, to get a handle to standard input:

```
$stdin = fopen('php://stdin', 'r');
```

Reading a line from standard input is as easy as $this->readln() when using the base class in this chapter. To help out even further, the base class has a method called prompt() that asks for input and then reads a line or sets a default if the input is empty. Interactive mode reads the values of the cipher, secret, mode, and source string from standard input. The resulting run() method (the method called when executing the command-line application) looks like this:

```
public function run() {
    parent::run();

    if ( $this->interactive ) {
        $this->runInteractiveMode();
    } else {
        echo $this->crypt();
    }
}

private function runInteractiveMode() {
    $defaultCipher = $this->cipher;
    do {
        $this->cipher = $this->prompt("Choose a cipher",$defaultCipher);
    } while ( !$this->isValidCipher( $this->cipher ) );

    $defaultMode = $this->mode;
    do {
        $this->mode = $this->prompt("Choose an encoding mode",$defaultMode);
    } while ( !$this->isValidMode( $this->mode ) );

    $defaultSecret = $this->secret;
    do {
        $this->secret = $this->prompt("Choose an encryption key/secret",
            $defaultSecret);
    } while ( strlen( $this->secret ) == 0 );

    while ( count($this->data) == 0 ) {
        $data = $this->prompt('Enter the data that you would like to encrypt: ');
        if ( $data ) $this->data = array($data);
    }
}
```

```
}
    $this->crypt();
}
```

```
private function crypt() {
    if ( $this->iv == null ) {
        $iv_size = mcrypt_get_iv_size($this->cipher, $this->mode);
        srand();
        $this->iv = mcrypt_create_iv($iv_size, MCRYPT_RAND);
    }

    if ( $this->decrypt ) return $this->doDecrypt( $this->data );
    else return $this->doEncrypt( $this->data );
}

private function doEncrypt( $source ) {
    return mcrypt_encrypt($this->cipher, $this->secret,
        $source, $this->mode, $this->getIV());
}

private function doDecrypt( $data ) {
    return mcrypt_decrypt( $this->cipher, $this->secret, $data,
        $this->mode, $this->iv );
}
```

The base class automatically puts anything that is not part of a flag into the $data member variable as an item in an array. Just like the command line, data can also be enclosed in quotes to keep it all in one piece.

Chapter 11, “Rewrite Rules,” uses a command-line application to constantly read values and spit out the results. This class would be useful for that but because of the simplicity of the application (no command-line parameters, no interactivity, and so on) it is more efficient to just write it from scratch.

## Completed Classes

Two complete classes are defined in this section:

- **The base class:** Defines basic functionality of a command-line application.
- **The application class:** You use this to do the encryption and decryption.

The base class needs to perform two functions: input and high-level output. To facilitate input, the class has utility functions that make it easy to read and register command-line options as well as prompt for input. The class first reads in all the command-line parameters and then calls the run() method.

The base class is too large to list inline in the book. It is also probably unnecessary to review basic string parsing and array handling. However, here are some key concepts to remember:

- The $argv variable, as mentioned earlier, stores a vector (array) of arguments, passed through the command line. The first argument at index zero is always the path to the script.

The variable $argc stores the count of the arguments. PHP CLI takes care of all the hard work of dealing with quotations, but it is up to the script to gain meaning from the command line.

php://stdin can be read from and written to like any other file on the system. It benefits from a concept called protocol wrappers, which allow different protocols to act as a standard file handle in PHP.

The next step is to take a command-line program, which is already quite useful, and make it even more useful by running it on a schedule.

## Setting Up Cron Jobs

A cron job is a recurring task on a Linux/UNIX server and is very useful for cleanup operations, messaging, or any number of actions that you periodically need to take care of. It can be set up to run at specific intervals ranging from once a minute to annually. You cannot create jobs that run more frequently than a minute — for that, it’s probably best to set up a daemon.

> A daemon, besides being a supernatural being, is a program on a UNIX/Linux system that runs in the background. Usually that means that it runs indefinitely until it is shut down or restarted. Although not covered in this chapter, it is possible to write a daemon in PHP. The Rewrite Map code from earlier acted as a type of daemon. The key is one line of code:
>
> `set_time_limit(0);`

The list of cron jobs is edited by a program called crontab (again, the system must be UNIX or Linux). To enter the crontab editor, type:

```
crontab -e
```

Once there, it’s possible to create cron jobs. There can be one job per line, which consists of two main parts: the timing indicators and the command to be executed. The command should be a PHP file that is set up properly with executable permissions and a shebang in place. A job that runs every hour on the hour would look like this:

```
0 * * * *  /some/php/script
```

The five dots, in order, represent minutes, hours, day of month, month, and day of week. Minutes, hours, and day of week are zero-based. Day of month and the month itself are one-based. So, if a job were to run once a year at the very start of the year, it would look like this:

```
0 0 1 1 *  /happy/new/year
```

The last star is intentionally left in this code. A star indicates every time. For instance, a star for minutes means that the script will run once per minute. If that last star were changed to a 0 it means the script will only execute if the first day of the year also happens to align with the first day of the week.

It is also possible to have a job run only at specific increments, for example once every fifteen minutes. To do this it's necessary to represent the time as a fraction (an asterisk over the delta):

```
*/15 * * * *  /some/php/script
```

## Bonus: Output in Color

Command lines are not all black and white (or black and green, or whatever your settings may be). They come in a range of colors. Colors are useful for providing emphasis or for design but they are only easily accessible in Bash-compatible shells (which is fine for most Linux but not Windows users). The section shows how to switch colors on the fly.

You create colored text using special escape sequences (called ANSI control codes) in the output. They always start with a null byte, followed by an ASCII 33 and then the color number (in decimal) followed by the letter m. For example, to make text red:

```
echo "\033[31mThis text will be red";
```

Why the number 31? That is the code for a red foreground. Table 15-1 shows the complete color table:

| COLOR | FOREGROUND VALUE | BACKGROUND VALUE |
|---|---|---|
| Black | 30 | 40 |
| Red | 31 | 41 |
| Green | 32 | 42 |
| Brown | 33 | 43 |
| Yellow | 33 | 43 |
| Blue | 34 | 44 |
| Purple | 35 | 45 |
| Cyan | 36 | 46 |
| Grey | 37 | 47 |

It doesn't take much to notice a pattern in the colors. The background color code is always exactly 10 higher than the foreground color code. You can combine multiple color codes by separating them with a semicolon. For instance, to get gray text on a black background:

```
echo "\033[37;40mThis text will be grey on a black background";
```

There are also several codes that have special effects on the text. The text can start blinking just by adding a ";5" to the end. Normal (0) returns the text back to its default state (including color and background). Light or bold (1) make the text stick out compared to other text. There are more but they are less useful and not honored by all console emulators and terminals.
