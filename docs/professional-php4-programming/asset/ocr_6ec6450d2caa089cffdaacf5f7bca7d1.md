Based on the array of available languages ($avail_lang), and the browser's Accept-Language header, this function will return the language code for the best language:

```
function getBestLanguage()
{
    $accept_lang = explode(', ', $GLOBALS['HTTP_ACCEPT_LANGUAGE']);
    while (list($key, $lang) = each($accept_lang)) {
        if (in_array($lang, $this->avail_lang)) {
            return $lang;
        }
    }
    return reset($this->avail_lang);
}
```

setLanguage() switches to another language by constructing a new output object:

```
function setLanguage($new_language = '')
{
    switch ($new_language) {
    case 'en':
        $this->output = new English_Output();
        break;
    case 'da':
        $this->output = new Danish_Output();
        break;
    case 'pl':
        $this->output = new Polish_Output();
        break;
    default:
        $this->setLanguage($this->getBestLanguage());
        break;
    }
}
```

Here's our base class for all output classes:

```
class Basic_Output
{
    var $strings;

    function _($string)
    {
        if (isset($this->strings[$string])) {
            return $this->strings[$string];
        } else {
            return $string;
        }
    }
}
```