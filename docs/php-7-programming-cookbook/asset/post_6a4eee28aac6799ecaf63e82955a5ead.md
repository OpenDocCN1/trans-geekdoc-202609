
# How it works...

First, you will need to place the code described in the previous recipe into a file called PassGen.php in the Application\Security folder. Now you can create a calling program called chap_12_password_generate.php that sets up autoloading, uses PassGen, and defines the location of the cache directory:

```php
<?php
define('CACHE_DIR', __DIR__ . '/cache');
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . './../');
use Application\Security\PassGen;

Next, you will need to define an array of websites that will be used as a source for the word-base to be used in password generation. In this illustration, we will choose from the Project Gutenberg texts *Ulysses* (J. Joyce), *War and Peace* (L. Tolstoy), and *Pride and Prejudice* (J. Austen):

```php
$source = [
    'https://www.gutenberg.org/files/4300/4300-0.txt',
    'https://www.gutenberg.org/files/2600/2600-h/2600-h.htm',
    'https://www.gutenberg.org/files/1342/1342-h/1342-h.htm',
];
```

Next, we create the `PassGen` instance, and run `generate()`:

```php
$passGen = new PassGen($source, 4, CACHE_DIR);
echo $passGen->generate();
```

Here are a few example passwords produced by `PassGen`:

![](img/39390f6d56c5a83b28db083a8bd5185c_482_0.png)

# See also

An excellent article on how an attacker would approach cracking a password can be viewed at http://arstechnica.com/security/2013/05/how-crackers-make-minced-meat-out-of-your-passwords/. To find out more about brute force attacks you can refer to https://www.owasp.org/index.php/Brute_force_attack. For information on oclHashcat, see this page: http://hashcat.net/oclhashcat/.

# Safeguarding forms with a CAPTCHA

**CAPTCHA** is actually an acronym for **Completely Automated Public Turing Test to Tell Computers and Humans Apart**. The technique is similar to the one presented in the preceding recipe, *Securing forms with a token*. The difference is that instead of storing the token in a hidden form input field, the token is rendered into a graphic that is difficult for an automated attack system to decipher. Also, the intent of a CAPTCHA is slightly different from a form token: it is designed to confirm that the web visitor is a human being, and not an automated system.

# How to do it...

- 1. There are several approaches to CAPTCHA: presenting a question based on knowledge only a human would possess, text tricks, and a graphics image that needs to be interpreted.
- 2. The image approach presents web visitors with an image with heavily distorted letters and/or numbers. This approach can be complicated, however, in that it relies on the GD extension, which may not be available on all servers. The GD extension can be difficult to compile, and has heavy dependencies on various libraries that must be present on the host server.
- 3. The text approach is to present a series of letters and/or numbers, and give the web visitor a simple instruction such as *please type this backwards*. Another variation is to use ASCII "art" to form characters that a human web visitor is able to interpret.
- 4. Finally, you might have a question/answer approach with questions such as *The head is attached to the body by what body part*, and have answers such as *Arm*, *Leg*, and *Neck*. The downside to this approach is that an automated attack system will have a 1 in 3 chance of passing the test.

# Generating a text CAPTCHA

- 1. For this illustration, we will start with the text approach, and follow with the image approach. In either case, we first need to define a class that generates the phrase to be presented (and decoded by the web visitor). For this purpose, we define an `Application\Captcha\Phrase` class. We also define properties and class constants used in the phrase generation process:

```php
namespace Application\Captcha;

class Phrase
{
    const DEFAULT_LENGTH    = 5;
    const DEFAULT_NUMBERS   = '0123456789';
    const DEFAULT_UPPER     = 'ABCDEFGHJKLMNOPQRSTUVWXYZ';
    const DEFAULT_LOWER     = 'abcdefghijklmnopqrstuvwxyz';
    const DEFAULT_SPECIAL   = '!"\'#$%&*()_+[]{}@\^~<,>.?/\';
    const DEFAULT_SUPPRESS  = ['0', 'l'];

    protected $phrase;
    protected $includeNumbers;
    protected $includeUpper;
    protected $includeLower;
    protected $includeSpecial;
    protected $otherChars;
    protected $suppressChars;
    protected $string;
    protected $length;
}
```

- 2. The constructor, as you would expect, accepts values for the various properties, with defaults assigned so that an instance can be created without having to specify any parameters. The $include* flags are used to signal which character sets will be present in the base string from which the phrase will be generated. For example, if you wish to only have numbers, $includeUpper and $includeLower would both be set to FALSE. $otherChars is provided for extra flexibility. Finally, $suppressChars represents an array of characters that will be removed from the base string. The default removes uppercase 0 and lowercase 1:

```php
public function __construct(
        $length = NULL,
        $includeNumbers = TRUE,
        $includeUpper = TRUE,
        $includeLower = TRUE,
        $includeSpecial = FALSE,
        $otherChars = NULL,
        array $suppressChars = NULL)
    {
        $this->length = $length ?? self::DEFAULT_LENGTH;
        $this->includeNumbers = $includeNumbers;
        $this->includeUpper = $includeUpper;
        $this->includeLower = $includeLower;
        $this->includeSpecial = $includeSpecial;
        $this->otherChars = $otherChars;
        $this->suppressChars = $suppressChars
                ?? self::DEFAULT_SUPPRESS;
        $this->phrase = $this->generatePhrase();
    }
```

- 3. We then define a series of getters and setters, one for each property. Please note that we only show the first two in order to conserve space.

```php
public function getString()
{
    return $this->string;
}

public function setString($string)
{
    $this->string = $string;
}

// other getters and setters not shown
```

- 4. We next need to define a method that initializes the base string. This consists of a series of simple if statements that check the various $include* flags and append to the base string as appropriate. At the end, we use str_replace() to remove the characters represented in $suppressChars:

```php
public function initString()
{
    $string = '';
    if ($this->includeNumbers) {
        $string .= self::DEFAULT_NUMBERS;
    }
    if ($this->includeUpper) {
        $string .= self::DEFAULT_UPPER;
    }
    if ($this->includeLower) {
        $string .= self::DEFAULT_LOWER;
    }
    if ($this->includeSpecial) {
        $string .= self::DEFAULT_SPECIAL;
    }
    if ($this->otherChars) {
        $string .= $this->otherChars;
    }
    if ($this->suppressChars) {
        $string = str_replace(
            $this->suppressChars, '', $string);
    }
    return $string;
}
```

![](img/39390f6d56c5a83b28db083a8bd5185c_486_0.png)

# Best practice

Get rid of letters that can be confused with numbers (that is, the letter **O** can be confused with the number **0**, and a lowercase **l** can be confused with the number **1**).

- 5. We are now ready to define the core method that generates the random phrase that the CAPTCHA presents to website visitors. We set up a simple `for()` loop, and use the new PHP 7 `random_int()` function to jump around in the base string:

```php
public function generatePhrase()
{
    $phrase = '';
    $this->string = $this->initString();
    $max = strlen($this->string) - 1;
    for ($x = 0; $x < $this->length; $x++) {
        $phrase .= substr(
            $this->string, random_int(0, $max), 1);
    }
    return $phrase;
}
```

- 6. Now we turn our attention away from the phrase and onto the class that will produce a text CAPTCHA. For this purpose, we first define an interface so that, in the future, we can create additional CAPTCHA classes that all make use of Application\Captcha\Phrase. Note that getImage() will return text, text art, or an actual image, depending on which class we decide to use:

```php
namespace Application\Captcha;

interface CaptchaInterface
{
    public function getLabel();
    public function getImage();
    public function getPhrase();
}
```

- 7. For a text CAPTCHA, we define a Application\Captcha\Reverse class. The reason for this name is that this class produces not just text, but text in reverse. The __construct() method builds an instance of Phrase. Note that getImage() returns the phrase in reverse:

```php
namespace Application\Captcha;

class Reverse implements CaptchaInterface
{
    const DEFAULT_LABEL = 'Type this in reverse';
    const DEFAULT_LENGTH = 6;
```
