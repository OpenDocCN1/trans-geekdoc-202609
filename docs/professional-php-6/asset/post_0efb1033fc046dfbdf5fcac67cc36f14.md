
This completely negates the need to explicitly tell Smarty whether an error exists. It can determine this for itself by looking for a non-blank value in the conditional.

## Rewriting search.php with Smarty

Now you can put these skills into practice with a slightly more complex example. Using Smarty, you can quite easily rewrite the search.php and search.phtml pair from the first part of the chapter.

Look at the content you are creating in search.php so that you know what you have to reproduce using Smarty. Currently, by the time it reaches search.phtml, the $displayHash variable may contain the following:

- HADPROBLEMS — A true/false variable, which, again, you can represent as an ordinary variable in Smarty

- PROBLEMS — An array of strings, each of which is a problem that has been experienced, only to be echoed if HADPROBLEMS is set to true

Quickly modify search.php so that it looks like the following. The shaded area indicates the code that's been modified or added from the original version:

```php
require_once("constants.php");
require_once("request.php");
require_once("constraint.php");
require_once("constraintfailure.php");
```

```php
$strTemplateFile = "s_search.tpl";
require("Smarty.class.php");
$objSmarty = new Smarty;
```

```php
$objRequest = new request();
$blHadProblems = ($objRequest->IsRedirectFollowingConstraintFailure());
```

```php
if ($blHadProblems) {
$objSmarty->assign("HADPROBLEMS", "true");
};
```

```php
if ($blHadProblems) {
$objFailingRequest =
$objRequest->GetOriginalRequestObjectFollowingConstraintFailure();
$arConstraintFailures = $objFailingRequest->GetConstraintFailures();
$problemArray = Array();
for ($i=0; $i<sizeof($arConstraintFailures)-1; $i++) {
$objThisConstraintFailure = &$arConstraintFailures[$i];
$objThisFailingConstraintObject =
$objThisConstraintFailure->GetFailedConstraintObject();
$intTypeOfFailure = $objThisFailingConstraintObject->GetConstraintType();
switch ($intTypeOfFailure) {
case CT_MINLENGTH:
$problemArray[] = "Your search term was too short.";
break;
case CT_MAXLENGTH:
$problemArray[] = "Your search term was too long.";
break;
case CT_PERMITTEDCHARACTERS:
$problemArray[] = "Your search term contained characters I
didn't understand.";
break;
}
```

```php
if ($problemArray) {
$objSmarty->assign("PROBLEMS", $problemArray);
}
$objSmarty->display($strTemplateFile);
```

Create a corresponding template file in the templates subfolder called s_search.tpl:

```html
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
<head>
<title>Ed's Search Page</title>
</head>
<body>
<H1>Ed's Search Page</H1>
<hr>
You can search for types of steak here.
<BR><BR>
{if $HADPROBLEMS}
<B>Sorry, there were problems with your search!</B>
{section name=x loop=$PROBLEMS}
({$PROBLEMS[x]})
{/section}
{/if}
<FORM METHOD="GET" ACTION="searchresults.php">
<TABLE BORDER="0">
<TR>
<TD>Type of Steak</TD>
<TD><INPUT TYPE="TEXT" NAME="typeOfSteak"></TD>
</TR>
</TABLE><BR>
<INPUT TYPE="SUBMIT">
</FORM>
</body>
</html>
```

Run the revised search.php and try to generate errors as you did before. You'll notice that the output upon receiving such errors is almost exactly the same, so the template conversion has been a resounding success.

There is one small problem, however. If you generate only one error, you will still receive a message stating that “there were problems,” rather than “there was a problem,” with your search.

In the original .PHTML native PHP template, you accounted for this using the following:

```php
<B>Sorry, there
<?= (sizeof($displayHash["PROBLEMS"]) > 1) ? "were problems" : "was a problem") ?>
with your search!</B>
```

Thankfully, you can account for this in Smarty, too. All you need to do is measure the size of the array and adjust the output accordingly, exactly as you do in native PHP:

```smarty
<B>Sorry, there {if $PROBLEMS[1]}were problems{else}was a problem{/if}
with your search!</B>
```

There is some slight cheating going on, however. There is no way in Smarty to measure the size of an array without calling upon PHP code, so the code simply checks for the existence of a second element in the array. If it exists, then the user sees the plural text. Otherwise, the user sees the singular text.

If you modify your template to use this new code, you should find that the output of the script is exactly the same now as it was when you used native PHP templating in the first half of the chapter. You could, of course, rewrite searchresults.php and searchresults.phtml using the same technique. Why not try doing that now?

## Advanced Smarty

Now that you’ve familiarized yourself with basic Smarty use, it’s worth looking in a little more detail at some of the more advanced features it offers.

### Run-time Configuration

As mentioned at the beginning of this section, you may well find yourself confronted with situations in which creating subfolders under every single location where .php files reside is undesirable. Thankfully, Smarty enables you to specify these locations at run-time:

```php
$smarty->template_dir = '/web/www.mydomain.com/smarty/guestbook/templates/';
$smarty->compile_dir = '/web/www.mydomain.com/smarty/guestbook/templates_c/';
$smarty->config_dir = '/web/www.mydomain.com/smarty/guestbook/configs/';
$smarty->cache_dir = '/web/www.mydomain.com/smarty/guestbook/cache/';
```

### Multidimensional Arrays

Multidimensional arrays may be treated in much the same manner as their single-dimensional counterparts, whether they are associative, linear, or a mixture:

```php
$multiArray = Array(Array("x","o","x"),Array("o","x","x"),
Array("o","o","x")); $objSmarty->assign("TicTacToeBoard", $multiArray);
```

Tie this to the following template:

```smarty
<TABLE BORDER="1">
{section name=y loop=$TicTacToeBoard}
<TR>
{section name=x loop=$TicTacToeBoard[y]}
<TD>{$TicTacToeBoard[y][x]}</TD>
{/section}
</TR>
{/section}
</TABLE>
```

This is the expected, familiar Tic-Tac-Toe board, with X winning down the left-to-right diagonal.

### Variable Modifiers

Variable modifiers may be used by template designers to perform very simple modifications to the variables they have received:

```php
$smarty->assign('bookTitle', "Professional PHP5");
```

Couple this with the template code:

```smarty
{$bookTitle|replace:"PHP5":"PHP6"}
```

The output is very much as expected.

### Functions

Smarty defines a number of functions in its language. It considers some to be built-in — that is, unable to be modified or overwritten. The functions provided in Smarty are really better described as methods, in that they do not generally perform any function on an input, unlike the modifiers you have just met (such as replace, which changes its input before rendering it).

One very useful example is the strip function, which enables you to neatly lay out HTML properly tabulated and spaced, safe in the knowledge that any extraneous white space will be stripped out before it is sent to the browser. This makes the templates very easy to maintain:

```smarty
{strip}
<table border="0">
<tr>
<td>
Here is some content.
</td>
</tr>
</table>
{/strip}
```

This is a great deal easier for a human being to read. When the HTML is sent to the browser, however, how it looks behind the scenes is far less important than how it is displayed to the user. The {strip} tag removes any whitespace for you that might disturb the output:

```html
<table border="0"><tr><td>Here is some content.</td></tr></table>
```

### Capturing Output

Sometimes, rather than simply spit the parsed template output directly to screen, you may want to capture it into a variable. For example, this can be particularly useful should you want to render XML content using Smarty, and then pass it through an XSL stylesheet to actually render it to the Web browser. Alternatively, you may not want to pass the rendered content at all. For example, you may be sending an HTML e-mail. Here, Smarty is very useful indeed, as you may have discovered in Chapter 11:

```php
// capture the output
$strOutput = $objSmarty->fetch("index.tpl");
```

Simply assign the rendered template's output HTML to the variable $strOutput, with which you can then do whatever you desire.

### Including Other Templates

Smarty even enables you to include other templates, which will be parsed in the normal way. You could use this to add common headers and footers to your pages:

```smarty
{include file="header.tpl"}
```

### Further Reading

The functionality of Smarty is enormous and far beyond the scope of this chapter. Having been introduced to some examples of standard usage, however, you should now be well equipped to explore its features further.

The obvious starting point is the Smarty reference site at www.smarty.net/manual/en/. All modifiers, functions, and even obscure configuration parameters are documented here in full. Conveniently, the documentation is divided into two sections that target both programmers (the people doing the PHP) and HTML template developers.

### When to Use Smarty vs. Traditional Templating

The decision to use Smarty over traditional native PHP templating should not be taken lightly. Although Smarty is clearly a great tool for simple templating, its functionality is still only a subset of what might be needed in large-scale projects.

Although it can be extended with native PHP through the use of the {php} and {/php} tags, doing so rather defeats the purpose of using safe templates in the first place. Indeed, Smarty's own Web site states that "embedding PHP code into templates is highly discouraged."

The skills and experience of any other developers working with you on the project are likely to be the deciding factor. If you are the sole engineer working on a project, it is almost certainly better to use native templating. Conversely, if the project requires a number of designers and HTML specialists working on the output from your scripts, Smarty templates are a much safer bet, because they allow such individuals to manipulate the display logic of your application to their hearts' content, without touching the PHP code behind it.
