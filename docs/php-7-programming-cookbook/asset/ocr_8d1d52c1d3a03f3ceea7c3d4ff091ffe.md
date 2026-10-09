+   3.  Next, we use Composer to install PHPUnit. This is accomplished by creating a `composer.json` file that contains a series of directives outlining project parameters and dependencies. A full description of these directives is beyond the scope of this book; however, for the purposes of this recipe, we create a minimal set of directives using the key parameter require. You will also note that the contents of the file are in **JavaScript Object Notation (JSON)** format:

```
    {
        "require-dev" : {
            "phpunit/phpunit" : "*"
        }
    }
```

+   4.  To perform the installation from the command line, we run the following command. The output is shown just after:

```
    php composer.phar install
```

![](bbox=[0.25, 0.4, 0.75, 0.64])

+   5.  PHPUnit and its dependencies are placed in a vendor folder that Composer will create if it does not already exist. The primary command to invoke PHPUnit is then symbolically linked into the vendor/bin folder. If you place this folder in your PATH, all you need do is to run this command, which checks the version and incidentally confirms the installation:

```
    phpunit --version
```