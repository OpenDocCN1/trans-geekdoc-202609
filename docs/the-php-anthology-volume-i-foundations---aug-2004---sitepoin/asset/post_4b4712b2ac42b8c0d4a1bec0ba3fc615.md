
The most obvious way to change the filename that appears in the URL is to rename the file; that is, we could simply rename the script article.php to article. Of course, without the .php extension, Apache has no way of knowing that the file is a PHP script. By default, therefore, it will simply send the unparsed PHP code straight to the browser—definitely *not* what we want!

To correct this, we need to tell Apache specifically to treat the file as a PHP script. This can be done easily with a .htaccess file, but you first need to make sure Apache is configured to allow it. If you're working on your own server, you simply need to ensure that AllowOverride is set to All in Apache's httpd.conf file. If you're working with a Web host, you'll need to ask them to do the honours. Once that's done, drop the following code into a file named .htaccess, and save it in the same directory as the script you want to rename:

```
File: forcetype/.htaccess

<Files article>
 ForceType application/x-httpd-php
</Files>
```

This directive tells Apache to treat the file named article as a PHP script. Simple, right?

To try this out yourself, check out the forcetype directory in the code archive for this chapter. I've set it up with a script called article and a .htaccess file that identifies it as a PHP script. Here's the code for article:

```
File: forcetype/article

<?php
 // Include the PathVars class
 require_once 'Url/PathVars.php';

 // Create instance of PathVars
 $pathVars = new PathVars($_SERVER['SCRIPT_NAME']);

 echo 'This is the article script<br />';

 if ($pathVars->fetchByIndex(0)) {
  echo 'The article ID is ' . $pathVars->fetchByIndex(0);
 }
 ?>
```

Try loading it with an article ID in the URL suffix (e.g. http://www.example.com/phpanth/WebPageElements/forcetype/article/123). If Apache is correctly configured to allow the ForceType directive in the `.htaccess` file, it should correctly display the ID.

## Hiding PHP Scripts by Rewriting URLs

Although `ForceType` is a neat solution that does the trick, there is an alternative that offers more power and completely eliminates the need for any part of the PHP script filename to appear in the URL. That alternative is **mod_rewrite**. This is an optional Apache module that will need to be installed on your server, and as with `ForceType`, you'll need `AllowOverride All` set for your Website in `httpd.conf`.

Generally speaking, `mod_rewrite` lets you detect browser requests for particular URLs and instruct Apache to treat them as if they were for a different URL entirely. In the simplest case, you could tell Apache to detect requests for, say, `/article` and treat them as if they were requests for `/article.php`. Of course, this is no different from what we achieved with `ForceType` above, so let's go one step further and see just how flexible `mod_rewrite` really is!

Instead of detecting a specific URL, we can use `mod_rewrite` to detect *any* URL and point the request at a single PHP file. Let's look at a sample `.htaccess` file that does this:

```
RewriteEngine On
RewriteRule !(\.gif|\.jpe?g|\.css|\.php|^images/.*|^files/.*)$ index.php [nocase,last]
```

The `RewriteEngine` line simply tells Apache to switch on `mod_rewrite` processing for this directory; `RewriteRule` is where the *real* action is. The above `RewriteRule` tells Apache to send *all* requests to `index.php` *except* for requests for `.gif`, `.jpg`, `.jpeg`, `.css`, `.php` files, or anything from the subdirectories `images` and `files`, which it should allow to proceed normally.

Obviously, `index.php` becomes a very important script! Here's what it might look like:

```
<?php
// Include the PathVars class
require_once 'Url/PathVars.php';

// MODIFY THIS FOR YOUR CONFIGURATION!!!
$baseUrl = '/phpanth/WebPageElements/rewrite/';

// Create instance of PathVars
$pathVars = new PathVars($baseUrl);

// What's the first path variable?
switch ($pathVars->fetchByIndex(0)) {
case 'download':
  // Examine the second path variable
  if ($pathVars->fetchByIndex(1)) {
    echo 'Downloading file ' . $pathVars->fetchByIndex(1);
  } else {
    echo 'Download <a href="' . $baseUrl .
      'download/myStuff.zip">myStuff.zip</a><br />';
  }
  break;
case 'article':
  // Examine the second path variable
  if ($pathVars->fetchByIndex(1)) {
    echo 'Viewing article ' . $pathVars->fetchByIndex(1);
  } else {
    echo 'View <a href="' . $baseUrl .
      'article/123">Article 123</a><br />';
  }
  break;
default:
  echo 'This is the home page<br />';
  echo '<a href="' . $baseUrl .
    'download/">Downloads</a><br />';
  echo '<a href="' . $baseUrl . 'article/">Articles</a><br />';
  break;
}
?>
```

In this code, I've used the PathVars class to allow index.php to handle most of the requests on the site. Here are some of the URLs it might be asked to handle:

- **http://www.example.com/phpanth/WebPageElements/rewrite/**
  PathVars doesn't find any parameters in the URL suffix. The script will display the home page of the site.

- **http://www.example.com/phpanth/WebPageElements/rewrite/download/myStuff.zip**
  PathVars detects the parameters download and myStuff.zip in the URL suffix. The script will send the specified file to the browser as a download.

- **http://www.example.com/phpanth/WebPageElements/rewrite/article/123**
  PathVars detects the parameters article and 123 in the URL suffix. The script will display the article with ID 123 for viewing.

## URL Rewriting and PathVars

Pay special attention to the way PathVars is instantiated in this example:

```
// MODIFY THIS FOR YOUR CONFIGURATION!!!
$baseUrl = '/phpanth/WebPageElements/rewrite/';

// Create instance of PathVars
$pathVars = new PathVars($baseUrl);
```

One side-effect of URL rewriting is that $_SERVER['SCRIPT_NAME'] and $_SERVER['REQUEST_URI'] can no longer be compared in order to find the URL suffix. The former contains the actual name of the PHP script, while the latter contains the URL that the browser actually requested.

For this reason, when you use PathVars in a URL rewriting setup like this, you need to supply the constructor with the path to the directory that contains .htaccess, instead of simply passing it $_SERVER['SCRIPT_NAME'] as we've done before.

To put it simply, when using URL rewriting, give PathVars the portion of the URLs that you want it to ignore.

Note also that we've made use of the $baseUrl variable when building links, rather than $_SERVER['PHP_SELF']. The latter would include index.php in the links again, which we don't want.

## Designing URLs

PHP based Websites are typically a collection of applications that perform different tasks, each with its own identifiable URL. For example:

- http://www.example.com/forums/
  a forum

- http://www.example.com/blog/
  a Web log (or “blog”)

- http://www.example.com/downloads/
  a download manager

Each of these URLs is the root of an application. If a site is well constructed, these will be integrated so that, for example, if downloading a file requires a user name and password, the same user name and password is used for the forum.

Within each application, there are *views* that correspond to the different page types your site’s visitors will see. For example:

- `http://www.example.com/forums/discussion/php`
  a view of the PHP discussion forum

- `http://www.example.com/forums/discussion/php/34`
  a view of a message in the PHP forum

Each view has a default appearance but may be able to accept additional *parameters*. For example:

- `http://www.site.com/forums/discussion/php/?sort=popularity`
  orders the posts in terms of their popularity

- `http://www.site.com/forums/discussion/php/?sort=date&numposts=10`
  shows the latest ten posts on the forum

See what I’m suggesting here? Applications and views are identified by a URL suffix, while parameters used by that view are identified by standard query string variables.

Making this division between views and parameters can really help in structuring the PHP that powers the site. Determining which application and view a visitor to your site has requested requires a fixed number of variables that can be identified by their relative position within the URL. By contrast, a particular view will often make use of a number of parameters, not all of which will be present at the same time. Parameters, therefore, are best identified with name/value pairs, which a query string makes possible.

Using URL suffix values in your code requires a little planning. Consider again this URL:

`http://www.site.com/forums/discussion/php/`

You can only access the variables by their index—the position in which they appear in the URL. With the above URL you might use **PathVars** to retrieve an array containing the variables:
