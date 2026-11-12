```
 * @access public
 */
function WordFilter($badWords)
{
    $this->badWords = array();
    srand((float)microtime() * 1000000);
    $censors = array('$', '@', '#', '*', '£');
    foreach ($badWords as $badWord) {
        $badWord = preg_quote($badWord);
        $replaceStr = '';
        $size = strlen($badWord);
        for ($i = 0; $i < $size; $i++) {
            shuffle($censors);
            $replaceStr .= $censors[0];
        }
        $this->badWords[$badWord] = $replaceStr;
    }
}

/**
 * Searches for bad words in text and censors them
 * @param string text to filter
 * @return string the filtered text
 * @access public
 */
function filter($text)
{
    foreach ($this->badWords as $badWord => $replaceStr) {
        $text = preg_replace('/' . $badWord . '/i', $replaceStr,
            $text);
    }
    return $text;
}
}
```

If you're wondering about the constructor, the idea is to create a random string with which to replace each word—just for fun. Note that I used preg_quote to ensure that bad words aren't interpreted as regular expression syntax.

Now, I have a loathing of Teletubbies™. In fact, the mere mention of the word “Tubby” sends me into a blind rage. Putting the class into action, I can eradicate from my site the discussion of all things “Tubby”: