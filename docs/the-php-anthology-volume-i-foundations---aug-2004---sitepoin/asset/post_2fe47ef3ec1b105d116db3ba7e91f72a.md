
## 5 Text Manipulation

Despite the fact that we're living in an era of multimedia, the majority of Web content appears in that most dull but effective of formats: text. Most of your work as a PHP developer will involve manipulating text in some form or other—be it HTML, XML or otherwise—for display on your Website.

## How do I solve problems with text content in HTML documents?

Learning (X)HTML is generally fairly easy, at least when compared to object oriented programming languages and the like. HTML is almost deceptively simple though. There's more to it than meets the eye, particularly when it comes to generating HTML on the fly.

In this solution, I'll look at some of the common problems you'll encounter when constructing HTML with PHP, and what's on offer to help you solve them.

## Dynamic Link URLs

When they're used as part of a link in a Web page, certain characters will cause problems for users who try to activate that link by clicking on it. Take spaces, for example; the exact number of spaces contained in the URL may be lost as the browser identifies the address of the page. However, it is possible to send a representation of a space character in a URL using the code %20. This process of replacing special characters with appropriate codes is called **URL encoding**.

There are two types of problem characters:

- **reserved characters**, which already serve some purpose in URLs, such as ? and &

- **unsafe characters**, which may be dealt with unpredictably depending on the Web browser and Web server

Imagine, for example, you have in your database a user whose login name is “Ben&Jerry.” You build a page through which you can view that user’s profile. To access it, you decide to construct a link using the login name from the database. You might end up with a link like this:

```html
<a href="/index.php?view=profile&amp;user=Ben&Jerry">
View Ben&Jerry </a>
```

The index.php script that receives the request will receive the GET variable ($_GET['user']) as just “Ben”, ignoring “Jerry” (who will probably not be pleased). When the script tries to locate that name in the database, there will obviously be a problem.

Thankfully, PHP provides the urlencode function to handle this situation. If we pass the user name that's included in the link through urlencode as the link is rendered, this will be the result:

```html
<a href="/index.php?view=profile&amp;user=Ben%26Jerry">
View Ben&Jerry </a>
```

Notice that the user name in the link becomes Ben%26Jerry. The script will now receive “Ben&Jerry” as the value of $_GET['user'] and will be able to locate the user in the database.

### Other URL Encoding/Decoding Functions

PHP also provides the urldecode function, which can be useful when you need to parse HTML with PHP. It also provides the functions rawurlencode and rawurldecode, which use a + character instead of %20 for marking spaces. This is the result of an alternative specification for encoding URLs.

At the end of this chapter, I've suggested a source of further reading that takes a detailed look at the subject of URL encoding in general.

urlencode and similar functions should only be applied to text as it is being used to create an HTML document. Don't be lulled into the trap of modifying the text before you store it in the database! In the above example, I had to render the user name in two different formats. If, instead, I had applied the urlencode to the user name before I inserted it into the database, I'd need to apply urldecode whenever I wanted to display the user name as normal text. I'd also run into problems when performing operations such as searching the database; I'd need yet more code to translate between the two versions. All this can be avoided if we simply insert the text into the database “as is”, and encode it only as required.

### Form Fields and HTML Content

We face another catch in dealing with HTML form elements that should be pre-populated with a value—perhaps one that’s taken from a database.

Imagine you have a form that allows users to edit the details of their account with your site, such as the “profile” page that’s common in online forums. In the form there's a text field that allows users to modify their “nickname.” The field might look something like this:

```html
<input type="text" name="nickname"
value="<?php echo $nickname; ?>" />
```

The value of the $nickname variable would come from your database. If the user has a nickname like “Joe Bloggs” there's no problem. The final HTML that's delivered to the browser will be:

```html
<input type="text" name="nickname"
value="Joe Bloggs" />
```

But what happens if someone uses a nickname like “Joe “The Hacker” Bloggs”? The form element will end up looking like this:

```html
<input type="text" name="nickname"
value="Joe "The Hacker" Bloggs" />
```

This is bad news for Web browsers. At best, they'll display a form field containing just the name “Joe”; at worst, they'll scramble the page completely.

Again, it's PHP to the rescue! The function htmlspecialchars will identify characters that are likely to cause problems, and convert them to a special code so that browsers recognize them as being part of the content. The characters in
