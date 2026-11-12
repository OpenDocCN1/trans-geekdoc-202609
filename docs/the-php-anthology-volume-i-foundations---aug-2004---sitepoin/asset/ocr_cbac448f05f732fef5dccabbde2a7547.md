rectly configured to allow the ForceType directive in the `.htaccess` file, it should correctly display the ID.

# # Hiding PHP Scripts by Rewriting URLs

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
```