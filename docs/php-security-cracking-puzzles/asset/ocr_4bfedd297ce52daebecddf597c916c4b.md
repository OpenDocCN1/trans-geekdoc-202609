# Part II: Solutions

"chr(\\11)";

```
// Stripping tags and displaying the text in the browser window
$content = preg_replace($search, $replace, $content);

$text = preg_split("|\\.\!?][\s]+||", $content);
echo "<pre>";
print_r($text);
echo "</pre>";
?
```

The results of the script operation are shown in Fig. II.2.1. Breaking the text into sentences, however, is only an intermediate step; now, each sentence must be broken into individual words.

![](bbox=[0.181, 0.437, 0.951, 0.703])

+   [1] => You might need to use local servers because of many reasons – for example, assume that you need to study PHP or MySQL, and testing applications on commercial hosting is too expensive, or there is no such a possibility at all
[2] => In this case you'll need a combination of Apache+PHP+MySQL on the local host
[3] => To begin with, you'll need to get Apache and MySQL distributions, as well as PHP archive

> Fig. II.2.1. The contents of the text array

The one-dimensional array $text can be converted into a two-dimensional array containing individual words in each finite element using the script shown in Listing II.2.13.

# Listing II.2.13. Converting the $text array into a two-dimensional array

```
<?php
for($i = 0; $i < count($text); $i++) {

```