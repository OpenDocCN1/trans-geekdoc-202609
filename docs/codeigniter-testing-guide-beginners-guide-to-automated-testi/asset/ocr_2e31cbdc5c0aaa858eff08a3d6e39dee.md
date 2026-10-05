# Setting Up the Environment

CodeIgniter/application/tests/phpunit.phar

> You can download the latest PHPUnit PHAR from https://phar.phpunit.de/phpunit.phar and download all releases of the PHPUnit PHAR from https://phar.phpunit.de/. PHPUnit 5.0 requires PHP 5.6 or later.

Let’s confirm the installed version of PHPUnit. Go to your terminal.

```
$ cd CodeIgniter/application/tests/
$ php phpunit.phar --version
PHPUnit 4.8.10 by Sebastian Bergmann and contributors.
```

# Windows users

I recommend you use Git Bash for Git for Windows https://git-for-windows.github.io.

# Where to run phpunit

You have to go to the application/tests directory to run phpunit, because this is where the PHPUnit config file phpunit.xml is installed.

# 2.5 (Optional) Installing PsSh

> PsSH is an interactive debugger and Read-Eval-Print Loop (REPL) for PHP which enables you to debug your test code via the CLI.

Download the latest version of PsSH (in this book we use v0.6.0-dev) from http://psysh.org/psysh and put it into the application/tests directory.