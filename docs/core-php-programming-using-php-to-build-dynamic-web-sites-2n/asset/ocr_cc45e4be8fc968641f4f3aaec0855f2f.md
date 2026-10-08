# Core PHP Programming

# boolean virtual(string filename)

The virtual function is available only when PHP is an Apache module. It is equivalent to writing <!--#include virtual filename->, which is an Apache subrequest. You may wish to refer to the Apache documentation to learn more. Use the include and require functions if you need to parse a PHP script. FALSE is returned on error.

```
<?php
virtual("ssi-example.shtml");
?>
```

# Aspell

The Aspell library is used to verify the spelling of a word. It is the result of an open source project run by Kevin Atkinson. The official Web site is http://metalab.unc.edu/kevina/aspell/. In order for PHP to use Aspell, the functions must be loaded as an extension. At the time of this writing, no win32 extension exists for Aspell, so its functionality is available to UNIX users only. Mark Musone added Aspell to PHP.

# integer aspell_new(string dictionary, string personal_words)

Use aspell_new to load a dictionary into the system. An identifier is returned that must be used in subsequent calls to Aspell functions. The second argument is optional and specifies a personal dictionary.

```
//create a test sentence
$text = "Thiss sentense haz some spllingin errors.";

//load dictionary
aspell_link = aspell_new('english');

//tokenize sentence
for($word = strtok($text, ' '); $word != ''; $word = strtok(' ')) {
    //check for unrecognized words
    if(!aspell_check($aspell_link, $token)) {
        //try checking raw version
        if(!aspell_check_raw($aspell_link,
    }
}
$token));
```