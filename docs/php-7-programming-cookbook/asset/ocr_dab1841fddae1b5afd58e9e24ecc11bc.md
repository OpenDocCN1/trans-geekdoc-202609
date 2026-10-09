```
if ($node->hasAttribute($attr)) { 
 	$value = $node->getAttribute($attr);
 	if ($domain) { 
 		if (stripos($value, $domain) !== FALSE) { 
 			$result[] = trim($value);
 		}
 	} 
 	} else { 
 		$result[] = trim($value);
 	}
 	}
 	return $result;
}
```

# How it works...

In order to use the new Hoover class, initialize the autoloader (described previously) and create an instance of the Hoover class. You can then run the Hoover::getTags() method to produce an array of tags from the URL you specify as an argument.

Here is a block of code from chap_01_vacuuming_website.php that uses the Hoover class to scan the O'Relly website for `<A>` tags:

```
<?php
// modify as needed
define('DEFAULT_URL', 'http://oreilly.com/');
define('DEFAULT_TAG', 'a');

require __DIR__ . './../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . './../');

// get "vacuum" class
$vac = new Application\Web\Hoover();

// NOTE: the PHP 7 null coalesce operator is used
$url = strip_tags($_GET['url'] ?? DEFAULT_URL);
$tag = strip_tags($_GET['tag'] ?? DEFAULT_TAG);

echo 'Dump of Tags: ' . PHP_EOL;
var_dump($vac->getTags($url, $tag));
```