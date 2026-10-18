the page to display the content we are reading from the server. In our example, we use a 'div' with the id of 'feed':

```
<div id="feed"></div>
```

This is where we write the content to when we get the response.

The other main change that we need to make is to provide a function that does more than just show an alert when it makes a connection. We need instead to navigate the DOM of the RSS XML document. You will note from the structure of RSS documents that there is a 'description' element inside the 'channel' element, and another inside each 'item' element. In the following function we use the 'getElementsByTagName' method to get a collection of all the description elements. Then we navigate to the first of the item descriptions using the index '1' (since the first index, 0, would be the channel description). We then set the 'innerHTML' property of the 'div' to the value of the content of the element. When we connect to the Yahoo news feed, the content is a set of anchors that link to HTML content.

```
// File: processnewsfeed.js
function processYahooNewsFeed()
{
    if(xhr...)
    {
        var descriptions=xhr...getElementsByTagName('description');
        var firstItemDescription=descriptions[1];
        feed.innerHTML=firstItemDescription.firstChild.nodeValue;
    }
}
```

Here is the web page that retrieves the content and displays it. It is similar to the last example, except that it includes the div tag and calls the 'processYahooNewsFeed' function.

```
<?xml version="1.0"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN" "http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en">
<head>
<title>Ajax RSS Reader</title>
<script type="text/javascript" src="getxmlhttprequest.js"></script>
<script type="text/javascript" src="processnewsfeed.js"></script>
</head>
<body>
<!-- File: example7-13.htm -->
<h1>Yahoo News Feed</h1>
<div id="feed"></div>
<script type="text/javascript">
// no 'var', so this is a global variable!
xhr...
```