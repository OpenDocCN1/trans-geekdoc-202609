
* @var string
 */
var $AllowedTags = '<a><b><strong><i><em><u>';

/**
 * Instance of native XML parser
 * @access private
 * @var resource
 */
var $parser;

/**
 * String of allowed tags
 * @access private
 * @var string
 */
var $post = '';

/**
 * Used to store any XML error string
 * @access private
 * @var string
 */
var $error = '';

/**
 * Constructs FormFilter
 * @access public
 */
function FormFilter()
{
    $this->parser = xml_parser_create();
    xml_set_object($this->parser, $this);
    xml_set_element_handler($this->parser, 'open', 'close');
    xml_set_character_data_handler($this->parser, 'data');
}

/**
 * Constructs FormFilter
 * @param string data to filter
 * @return string filter data
 * @access public
 */
function filter($post)
{
    $this->post = '';
$post = strip_tags($post, $this->allowedTags);
$post = '<?xml version="1.0"?><post>' . $post . '</post>';
if (!xml_parse($this->parser, $post, true)) {
    $this->error = 'Post data is not well formed: ' .
    xml_error_string(xml_get_error_code($this->parser)) .
    ' on line ' . xml_get_current_line_number($this->parser);
    return false;
}
return $this->post;
}

/**
 * Returns any XML errors
 * @return string XML error
 * @access public
 */
function getError()
{
    return $this->error;
}

Within the constructor of our FormFilter class, the first thing we must do is create an instance of the native Expat parser and tell it which call back functions to use (much more on this in Volume II, Chapter 2). With that done, we provide the filter method to “screen” the string containing HTML. First, we strip out everything but the tags defined in the $allowedTags member variable. We then need to prepend the XML processing instruction to the start of the string, and make sure the lot is wrapped in a root XML node; this is done so that the parser won’t complain about the string being badly formed.

If we run into problems during parsing, the error message will be stored locally and made available via the getError method. Once parsing is complete, we return the post to the code that called the filter method.

The real work happens in the XML handlers:

File: TextManipulation/FormFilter.php (in SPLIB) (excerpt)

```
/**
 * Sax Open TagHandler
 * @param XML_HTMLSax
 * @param string tag name
 * @param array attributes
 * @return void
 * @access private
 */
function open(&$parser, $tag, $attrs)
{
    switch ($tag) {
    case 'A':
    if (isset($attrs['HREF']) &&
    Validate::url($attrs['HREF'])) {
    $this->post .= '<a href="' . $attrs['HREF'] .
    '" target="_blank">';
    } else {
    $this->post =
    '<a href="javascript;" target="_blank">';
    }
    break;
    case 'B':
    case 'STRONG':
    $this->post .= '<strong>';
    break;
    case 'I':
    case 'EM':
    $this->post .= '<em>';
    break;
    }
}

/**
 * Sax Close TagHandler
 * @param XML_HTMLSax
 * @param string tag name
 * @param array attributes
 * @return void
 * @access private
 */
function close(&$parser, $tag)
{
    switch ($tag) {
    case 'A':
    $this->post .= '</a>';
    break;
    case 'B':
    case 'STRONG':
    $this->post .= '</strong>';
    break;
    case 'I':
    case 'EM':
    $this->post .= '</em>';
    break;
    }
}

/**
 * Sax Data Handler
 * @param XML_HTMLSax
 * @param string data inside tag
 * @return void
 * @access private
 */
function data(&$parser, $data)
{
	$this->post .= $data;
}
}
```

The handler methods are called by the parser as it reads through the XML document. Looking at the open method, you can see how we might deal with different tag names. In particular, when we receive an a tag, we use PEAR::Validate to check whether the URL is valid. Note also that we’re converting b and i to strong and em. Any other attributes that we encounter that are not specifically identified here are simply thrown away.

Note that for this example the use of strip_tags was actually unnecessary, as the handler methods will also ignore any tags that are not specifically identified. Of course, we’re limiting ourselves to only a few HTML tags here. Dealing with others—lists, for example—typically requires more complex code, adding to the risk that we might allow HTML tags we weren’t expecting. The strip_tags function acts as our insurance policy.

One benefit of our using the XML extension is that we require users to post well formed XML. This has the advantage that an unclosed a, for example, won’t be accepted. It does mean that certain tags, such as br (if allowed), will cause problems if they aren’t written to XML standards.

Here’s an example of the class in action:

```
File: 12.php

<?php
// Include PEAR::Validate
require_once 'Validate.php';

// Include PEAR::XML_HTMLSax
require_once 'TextManipulation/FormFilter.php';

// Include file to strip quotes if needed
require_once 'MagicQuotes/strip_quotes.php';

// If the form is submitted...
if (isset($_POST['submit'])) {
    // Instantiate the form filter
    $FormFilter = &new FormFilter();

    // Filter the message
    if (FALSE === ($filtered_message =
        $FormFilter->filter($_POST['message']))) {
        $filtered_message = $FormFilter->getError();
    }
}
?>
<!DOCTYPE html "-//W3C//DTD XHTML 1.0 Transitional//EN"
"http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">
<html xmlns="http://www.w3.org/1999/xhtml">
<head>
<title>Form HTML Filter</title>
<meta http-equiv="Content-Type"
    content="text/html; charset=iso-8859-1" />
</head>
<body>
<p><b>Add your comment:</b></br />
<form action="<?php echo $_SERVER['PHP_SELF']; ?>" method="POST">
<textarea cols="40" rows="5" name="message"></textarea><br />
<input type="submit" name="submit" value=" Post " />
</form></p>
<p>Allowed tags: <code>&lt;code&gt;&lt;a&gt; &lt;b&gt; &lt;strong&gt; &lt;i&gt; &lt;em&gt;</code></p>
<?php
    if (isset ( $filtered_message )) {
        echo ( "<p>Your post:</b><br />\n<code>\n".
            htmlspecialchars($filtered_message)."</code>\n" );
    }
?>
</body>
</html>
```

You'll see by testing that this code allows only those elements that we identified in the class.

## Further Reading

- URL Encoding: http://www.blooberry.com/indexdot/html/topics/urlencoding.htm

This makes a useful reference for URL encoding.

- HTML Entities Reference: http://www.htmlhelp.com/reference/html40/entities/

Bookmark this handy reference for characters that have special meanings in HTML.

- PCRE Tutorial: http://codewalkers.com/tutorials/30/2.html

In this tutorial, you'll find some worthwhile and practical help on Perl Compatible Regular Expressions.

## 6 Dates and Times

Wouldn't it be nice if we had a ten-day week? How about 100 minutes in an hour? Ten months each year?

Dates and times are probably something you take for granted. You deal with
them every day and are probably unaware of the clever mathematical algorithms
your brain uses to work out how long you have to wait before Friday comes
around again. It's only when you start programming that you realize that what
you've been taking for granted all these years is not as easy to deal with in code
as you'd expect. Blame the Romans!

In our day-to-day lives, we're used to working with decimal (base ten) numbers,
which are optimized for dealing with groups of ten (ten ones in ten, ten tens in
a hundred, ten hundreds in a thousand, etc.). Avoiding a math lecture, the
problem with dates and times is that they don't break down into groups of ten:

- In one second you have one thousand milliseconds. No problem.
- In one minute you have sixty seconds.
- In one hour you have sixty minutes.
- In one day you have twenty-four hours.

So, how do you calculate the number of days given a value in milliseconds? That’s a stack of long division! And that’s just time—what about dates?

- In one week, you have seven days (does your week begin on Sunday or Monday?)

- In one month you have... er... you don’t know exactly how many days or weeks; it depends on the month (and don’t get me started on leap years!)

- In one year you have twelve months.

Of course, that’s too easy. How about making it more difficult? You often need to be able to express a date in multiple formats such as “Tuesday 18th March, 2003”, “03/18/03” (US format), “18/03/03” (European format), “18th Mar 2003”, and “20030318” (a MySQL-style timestamp), not to forget “1047942000” (a Unix timestamp)!

How do you plan to display a list of articles fetched from a database and ordered by date? What if you want to present something more complex, such as an online calendar? There’s a lot to think about when dealing with dates and times in your applications.

PHP really helps to make times and dates as painless as possible, thanks to powerful functions like date. But it’s important to develop the right strategy for dealing with dates and times early in your career as a PHP programmer. Take the right approach from day one, and you’ll avoid having to go back later and write insanely complex code to fix the mistakes you made as a newbie. In this chapter, we’ll be looking at the kinds of strategies you can employ, and solving some of the common problems you’ll face when it comes to dates and times.

## How do I store dates in MySQL?

At first glance, the easiest way to store dates in MySQL may appear to be to simply drop them in exactly as they’d appear on a Web page, for example, as “18th March 2003”. Be warned—this is the first step on the path to serious hair loss. The WHERE clause in an SQL statement run against MySQL will not allow you to do things like this:

```
SELECT * FROM table WHERE date > '14th February 2003'
```

A far better way to store date information is to use a timestamp. Timestamps are numbers that identify dates and times in a format that can be used to solve
