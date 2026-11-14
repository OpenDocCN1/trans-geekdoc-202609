
Answer:
PHP has strpos() function which can search a string inside other string.

### 81: How can you modify the case of the letters in a string?

Answer:
One can use the functions like strtoupper, strtolower, ucfirst, ucwords to modify the case of the letters of a PHP string.

### 82: How do you write to standard output in PHP?

Answer:
Apart from using print, printf, echo functions, one can use fopen('PHP://stderr', 'w') to write to the standard output in PHP.

### 83: How can you read a file's permissions and ownership data?

Answer:
The PHP function stat() returns an array of information about a file.

### 84: How to get the complete physical path to the file?

Answer:
The PHP function dirname() can be used to get the complete physical path to the file.

### 85: How do you copy and move a file in PHP?

Answer:
PHP uses functions copy() and rename() to copy and move the file respectively. On Unix, rename() function cannot move files across file systems.

### 86: How do you remove all the HTML and PHP tags from a string?

Answer:
One can use the function strip_tags() to remove all the HTML and PHP tags from a string.

### 87: How do you find an element inside an array?

Answer:
PHP function array_search() is used to search an element inside an array. This returns the index of the found value.

### 88: How do you open a file to write into?

Answer:
One can use fopen() function to write to the file. E.g. $f = fopen("sample.txt", "w");

### 89: Where do you use ob_start() in PHP?

Answer:
This function is used for output buffering in PHP.

### 90: How can you combine two arrays in PHP?

Answer:
One can use array_merge() function in PHP to combine different arrays.

### 91: Why do they use @ operator before variable names in PHP?

Answer:
@ operator suppresses any warnings/errors while trying to access any undefined variable.

### 92: Is it valid to declare a PHP variable with var keyword?

Answer:
It is deprecated, but still valid to declare a PHP variable with var keyword.

### 93: Does fclose() function return anything?

Answer:
It is not a void function. It returns a bool, indicating whether shutdown of the file has been successful or not.

## Object-Oriented Programming

### 94: Does PHP support multiple inheritance?

Answer: PHP does not support multiple inheritance. A class in PHP can only be extended on a single base class.

### 95: Is PHP pure object oriented?

Answer: No, PHP is not a pure object oriented language.

### 96: Does PHP support method/function overloading?

Answer: PHP isn’t a strongly typed language and hence it doesn’t make much sense to support the traditional functional overloading in PHP.

### 97: Does PHP support C++ style operator overloading?

Answer: No, PHP doesn’t support C++ style operator overloading.

### 98: Does PHP support java like interfaces? Can a class implement two interfaces?

Answer: Yes, PHP supports interface implementation concept. A class can implement only one interface.

### 99: Can interface constants be overridden by class that implements that interface?

Answer: No, interface constants cannot be overridden by class in PHP.

### 100: How can you force the destruction of an object?

Answer: Objects are automatically destroyed when a script terminates. To force the destruction, unset() can be used.

### 101: How can you clone an existing object in PHP?

Answer:
One can use a simple assignment operator to clone an existing object in PHP.

### 102: How do you call the parent class constructor in PHP?

Answer:
This can be done using parent::constructor($value) in PHP.

### 103: Does PHP support data encapsulation?

Answer:
PHP supports data encapsulation by providing access specifiers such as public, private, protected to the class members.

### 104: Does PHP support exception handling?

Answer:
Yes, PHP supports exception handling using the usual try/catch block.

### 105: If a class property is declared without visibility specifier, will it be public, private or protected?

Answer:
A class property is public by default.

## Regular Expressions

### 106: What do you mean by greedy regular expression matching? Are PHP regexes greedy? How do you overcome this problem?

Answer:
Regular Expressions are also known as regex. The standard quantifiers in regular expressions are greedy, meaning they match as much as they can, only giving back as necessary to match the remainder of the regex. We use “?” inside the regex to oppose this behavior.

### 107: What is the difference between preg_replace and ereg_replace?

Answer:
Ereg_replace uses a basic version of regular expression, while preg_replace uses the perl-compatible regular expressions.

### 108: Can you write a PHP regular expression to see if an email address is valid or not?

Answer:
```
/^[^@\s]+@([-a-z0-9]+\.)+[a-z]{2,}$/i
```

### 109: Can you write a PHP function to extract URLs from an HTML document?

Answer:
```
function pc_link_extractor($s) {
    $a = array();
    if (preg_match_all('/<a\s+.*?href=[\"\' ]?([^\"\' >]*)[\"\' ]?[^>]*>(.*)<\/a>/i', $s, $matches, PREG_SET_ORDER)) {
        foreach($matches as $match) {
            array_push($a,array($match[1],$match[2]));
        }
    }
    return $a;
}
```

### 110: How can we extract string 'abc.com' from a string 'http://xyz@a...' using regular_expression of PHP?

Answer:
We can use the preg_match() function with "/.*(@(.*))$/" as the regular expression pattern. For example:

```
preg_match("/.*(@(.*))$/","http://xyz@abc.com",$data);
echo $data[1];
```

### 111: Can you write PHP regex to match alphanumeric characters?

Answer:
```
[\w]
```

## Web Automation

### 112: How do you get the web page content using PHP?

Answer:
This can be done using PHP Curl extension or file_get_contents which is a library module. For advanced options such as sending POST request requires the usage of Curl.

### 113: What does Curl stand for? What all protocols does PHP Curl support?

Answer:
Curl stands for Client URL. PHP Curl supports http, https, ftp, gopher, telnet, dict, file and ldap protocols.

### 114: How do you overcome the stateless nature of HTTP using PHP?

Answer:
One needs to use PHP sessions to overcome the stateless nature of HTTP.

### 115: How can you send SOAP request using PHP?

Answer:
One can use PEAR's SOAP classes to send a SOAP request using PHP.

### 116: How can you read an RSS feed using PHP?

Answer:
One can use PEAR XML_RSS class to read RSS feeds from different web sites.

### 117: Can PHP be used for web scraping?

Answer:
Yes, PHP can be used for web scraping as PHP can retrieve the web content dynamically and parse it using various options.

## Advanced PHP

### 118: Does PHP support multithreading?

Answer:
PHP does not have a built-in support for multithreading. One can fake a fork in PHP. Forking is one method of multitasking and there exists an extension called Process Control Extension to handle this. There are also command line PHP commands that will allow for an process to run outside of PHP and return the output to PHP.

### 119: Can you lookup domain name using PHP?

Answer:
PHP has a function gethostbyname() that can be used to look up the domain name.

### 120: Are the host names returned by gethostbyaddr() correct always?

Answer:
This may not be true always. A malicious user may configure the DNS server to reply with incorrect hostnames. A combination of gethostbyname() and gethostbyaddr() can be used to verify the correctness of the results.

### 121: Can you ping a host using PHP?

Answer:
One can use PEAR's Net_Ping package to ping a host to see if it is reachable.

```
$ping = new Net_Ping;
if ($ping->checkhost('www.vibrantpublishers.com')) {
  print 'Reachable';
} else {
  print 'Not reachable';
}
```

### 122: Does PHP have support for FTP? Can you list some of the FTP functions offered by PHP?
