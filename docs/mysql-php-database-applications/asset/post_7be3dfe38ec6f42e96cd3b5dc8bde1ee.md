
6 => 6
7 => 7
8 => 8
9 => 9
10 => 10
11 => 11
12 => 12
);

```
// set the $years array to a list of plausible years
$y = date('Y');
$years = array(
	$y => $y++
, $y => $y++
, $y => $y++
, $y => $y++
, $y => $y++
, $y => $y++
, $y => $y++
, $y => $y++
);
```

```
// use January of next year as a default expiration date
if (empty($order->cc_exp_mon))
{
	$order->cc_exp_mon = 1;
}
if (empty($order->cc_exp_yr))
{
	$order->cc_exp_yr = date('Y')+1;
}
```

```
print labeled_row(
	'Expires',
	select_field(array(
		'name' => 'cc_exp_mon'
		, 'values' => $months
		, 'match' => $order->cc_exp_mon
	))
	, select_field(array(
		'name' => 'cc_exp_yr'
		, 'values' => $years
		, 'match' => $order->cc_exp_yr
	))
);

print end_table();

// display the order button
print paragraph(
    submit_field($order_button)
    , submit_field('Test Submit')
);

print end_form();

print end_page();

$_SESSION['order'] = serialize($order);
?>
```

## Summary

This chapter explained a lot of PHP concepts, using a shopping cart as a vehicle (no pun intended).

One of the most important concepts we discussed was persistence – the ability to store information related to a particular user (such as shopping–cart items) across multiple visits. PHP relies upon its connectivity to a database – a connection mediated by the PEAR classes, if you're smart– to store information.

Another key concept is state maintenance. Because HTTP is an inherently stateless protocol, you have to do a bit of work to correlate one HTTP request from someone with the next request from the same person, all the while distinguishing those requests from the hundreds of others that might be showing up at about the same time. PHP provides some useful state-management features. You saw, for example, that there's nothing to the process of registering a session identifier and examining it later to identify a particular use.

These capabilities are key in our shopping cart application. For one thing, we used persistence to store the contents of each shopping cart in a database, in such a way that they were kept separate from all others. Furthermore, we used session management to track users through our site – across many request/response transactions – as they browsed our wares and added and removed items from their carts.

## Chapter 15

## XML Parsing

### IN THIS CHAPTER

- Learning how to work with XML documents
- Examining an XML document retrieved from a URL

What HTML is to web pages, the eXtensible Markup Language, or XML, is to data. Whereas HTML is about presenting your information to the world — handling typefaces, sizes, colors, layout, and so on — XML concerns itself purely with structuring and identifying that information. Given the number of new and different Web platforms that seem to pop up each week — desktop computers, laptops, cell phones, televisions, wristwatches, car stereos — this separation of content from presentation is the great holy goal of Web programmers. Both languages are wildly successful because at heart they're both very simple, yet allow for a huge range of applications. They even look alike — which they should, considering they're both based on the Standard Generalized Markup Language (SGML).

In an XML document containing meteorological-observation data, for example, distinct tags can identify certain numbers as wind-velocity values and other numbers as wind-direction values. The question of how to represent these values visually — if they are to be displayed visually at all, rather than just read into a database or other processing environment — is a separate issue.

The other great thing about XML is that it's an excellent format for transmitting information not just data, but the kinds of queries and responses you might normally associate with a regular programming language (like PHP itself). This is because it's lightweight — it's just ASCII (or Unicode), after all — and transparent. You can look at an XML document for the first time and stand a good chance of understanding it right away. Yet it's also suitable for interpretation by machines, which are notoriously dim when it comes to understanding.

In this chapter we'll explore XML and the capabilities of PHP when it comes to processing it. We'll read a document in from a URL and reformat its contents for use in Netsloth, our content-management application.

The Web site Slashdot.org is used in this chapter merely for example purposes. Most sites like Slashdot.org have terms and conditions governing the use of the content they post, so be sure to pursue the proper permission before you publicly post any content taken from another Web site through your own Web application. For information about using headlines from Slashdot specifically, you should take a look at http://slashdot.org/code.shtml.

## Scope and Goals of Application

Not long ago, we had this great application to show you here. It had XML parsers, and event handlers, and function callbacks, and all kinds of flashy bits. The idea was to grab the headlines from a Web site like Slashdot (www.slashdot.org), which makes their content available in about every format known to modern humanity. One of these formats is XML, and you can see it yourself at http://slashdot.org/slashdot.xml. We would read it, parse it, and spit it back out as HTML, to be included on our tiny yet distinctive example of a Web content site, Netsloth (which you might remember from Chapter 11).

But then the folks building PHP decided that they would change their underlying XML support, building it around the Gnome XML library libxml2, and introducing this new extension called Simplexml, and, this is how you would build our first example now. Completely.

```
<?php
// keep the errors off the page
ini_set('display_errors', 0);
$url = 'http://www.slashdot.org/slashdot.xml';
$cachefile = "/tmp/slashdot.xml.cache";

if (($xml = file_get_contents($url)))
{
        file_put_contents($cachefile, $xml);
}
else
{
        error_log('Unable to contact www.slashdot.org');
        if (($xml = file_get_contents($cachefile)) == FALSE)
        {
error_log("Unable to open cache file: $cachefile");
print <<<EOT
<p>
Unable to obtain Slashdot.org content.
Please try again later.
</p>
EOT;
return;
}
$stories = simplexml_load_string($xml);
print <<<EOT
<h3>Slashdot Stories:</h3>
<ul>
EOT;
foreach ($stories->story as $story)
{
print <<<EOT
<li><a href="{$story->url}">{$story->title}</a>
EOT;
}
print <<<EOT
</ul>
EOT;
?>
```

This would make for a rather short chapter. You'll notice particularly that the "handle the XML" part of this code is just ten lines. So we've jazzed it up a bit.

We'll want to be able to include more information about each story, including the topic-representing images the site provides. At the same time, we want our own page at Netsloth to keep running if Slashdot gets slashdotted and goes off the air, while minimizing the amount that we add to their site's traffic. Both goals involve setting up local caches of content. Figure 15-1 shows you the new Netsloth home page.

> The stories shown in Figure 15-1 are for example purposes only. None of the content in this chapter represents postings that ever actually appeared on Slashdot.org.

![](img/47897cc2ae80cbce8ce42ba6e77e4d39_553_0.png)

Figure 15–1: Netsloth21 home page with mock sample stories

## Code Overview

The essential purpose of our application is to reach out across the Internet, grab an XML document, pick it apart, and reformat the chopped-up pieces into a form that's acceptable for use in our Netsloth content-management suite. To accomplish these goals, this software will need to be able to look at an XML document, distinguish the tags from the tagged text (also known as character data), and separate them if necessary. The piece of code that does this is generically called an _XML parser_. XML parsers can be designed in a couple of different ways.

## An introduction to parsers

If you're going to work with XML, you need a parser. Parsers come in two different general varieties:

- Tree-style parsers (also called Document Object Model (DOM) parsers), which read through entire XML documents at once and convert the imported data into hierarchically organized objects representing whole documents at once. Microsoft's MSXML parser is of this kind.
