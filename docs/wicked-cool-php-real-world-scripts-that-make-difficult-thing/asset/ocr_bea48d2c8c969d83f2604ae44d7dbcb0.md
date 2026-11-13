# # GD

If you want to create graphics on demand or just get image information when you need it, GD is the library for you. GD allows you to work with JPEGs and GIF files, either creating them as you need them for things like charts, or altering them to create thumbnails of existing images.

# ## MySQL

A completely vanilla build of PHP doesn't know how to access a database. Fortunately, since MySQL and PHP are like Zan and Jayna, most PHP-enabled webservers have the necessary MySQL libraries installed by default, so most people never know that the `mysql_connect()` function is part of an extension.

Other PHP extensions include SOAP (which allows you to access web services), PDF, and Verisign Payment Pro. It may seem like a great idea to add every extension in existence to PHP, but remember that each extension you add can slow initialization time and add security holes. Furthermore, extensions that aren't common often don't have someone actively maintaining them, leaving you without an upgrade path.

# ### Adding PHP Extensions

Now that you know what's available through extensions, let's explore how to install them. The first step is to see if you already have what you're looking for.

# ### Checking to See If Extensions Are Already Loaded

Many webservers have the more useful extensions installed by default, so before you go through the bother of installing an extension, first check to be certain you don't have it already installed and loaded.

The easiest way to check for extensions is run the `phpinfo()` function (described in "#8: Revealing All of PHP's Settings" on page 21). Page through the output, searching for your library. For example, if MySQL is enabled, you'll see a section like this:

```
mysql

MySQL Support => enabled

...
```

If this doesn't work out for you, or you think it's a little slow, there are other things you can try.

An extension adds new functions to PHP—for example, cURL adds functions such as `curl_init()` and `curl_setopt()`, Mcrypt adds `mcrypt_encrypt()` and `mcrypt_decrypt()`, and so on. But let's say that Mcrypt _isn't_ installed. In that case, PHP doesn't know anything about `mcrypt_decrypt()`—it's just an undefined function.