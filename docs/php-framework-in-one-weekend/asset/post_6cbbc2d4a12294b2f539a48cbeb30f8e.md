
## Chapter 5 Content

Now that we’ve got a templating system in place we need some content to put in the templates. At some point we might need a database for more advanced content management. For now we are going to store our content in simple text data files.

Create a folder in your project called data that will be the root of our flat file data store. We will use a folder on the local filesystem during our development, but thanks to the Flysystem[9] package these data files could be anywhere. Instead of using PHP’s built-in file access, we use Flysystem because it provides a filesystem abstraction. This provides a nice API for working with files, including loading, saving, renaming, copying, deleting, and listing. Because it is an abstraction we can work with multiple filesystems in the same way. Plugins provide the implementation details for different types of filesystem. Flysystem calls these plugins Adapters. There are Adapters available for local files, Azure, Amazon S3, Dropbox, FTP, SFTP, WebDAV, and many more.

Use Composer to install Flysystem:

```
$ composer require league/flysystem
```

Composer will download the latest version, add it to the require section of your config, and make it available to your PHP code via the autoloader. Listing 5.1 shows what the require section of the composer.json file looks like with the new addition.

```
9 "require": {
10 "symfony/http-foundation": "^3.0",
11 "twig/twig": "^1.24",
12 "league/flysystem": "^1.0"
13 }
```

### Listing 5.1: composer.json

We will interact with the filesystem using a \League\Flysystem\Filesystem object. In order to instantiate a filesystem we need to first create the Adapter. We are using the Local adapter which requires we pass the folder we want to use as the root of our filesystem as parameter to the constructor. We import the namespaces from Flysystem, and then create the objects like this:

```
<?php
use League\Flysystem\Adapter\Local;
use League\Flysystem\Filesystem;
$adapter = new Local(__DIR__.'../data');
$filesystem = new Filesystem($adapter);
```

Let's create a simple data structure in JSON format. We can use PHP’s built in json_decode() function to convert the JSON data in the file to a PHP array. In your data folder create a file data/menu.json as per listing 5.2.

```
1 {
2 "index": {
3 "title": "Hello World!",
4 "content": "Welcome to my PHP framework."
5 },
6 "about": {
7 "title": "About",
8 "content": "This is an example site."
9 }
10 }
```

### Listing 5.2: data/menu.json

We can read() the file from our $filesystem and parse it as JSON data. I pass true as the second parameter to the json_decode() function because I want the result as an array of values, not a PHP object:

```
$variables = json_decode($filesystem->read('menu.json'), true);
```

I then pull out the data I want from the $variables array and pass it to the Twig template as the second parameter to $twig->render(). Listing 5.3 shows the new index.php file with these changes.

```
1 <?php
2 use League\Flysystem\Adapter\Local;
3 use League\Flysystem\Filesystem;
4 use Symfony\Component\HttpFoundation\Request;
5
6 require __DIR__.'./../vendor/autoload.php';
7
8 $request = Request::createFromGlobals();
9 $adapter = new Local(__DIR__.'./../data');
10 $filesystem = new Filesystem($adapter);
11
12 $variables = json_decode($filesystem->read('menu.json'), true);
13
14 $loader = new Twig_Loader_Filesystem(__DIR__.'./../templates');
15 $twig = new Twig_Environment($loader);
16 echo $twig->render('index.html', $variables['index']);
17
```

### Listing 5.3: public/index.php

You can see I'm not currently using anything from the $request but I've left it in for now. Listing 5.4 shows the new Twig template that has been updated to make use of the variables passed in from menu.json.

```
1 <!doctype html>
2 <html lang="en">
3 <head>
4 <meta charset="UTF-8">
5 <title>{{ title }}</title>
6 </head>
7 <body>
8 <h1>{{ title }}</h1>
9 <p>{{ content }}</p>
10 </body>
11 </html>
```

### Listing 5.4: templates/index.html

## Chapter 6 Routing

We’ve got a templating system, and a basic flat file data store. Now we need the ability to serve different responses based on the request. Web frameworks tend to use a design pattern called Front Controller where a single script is responsible for handling all requests. This usually requires some configuration of the web server. If you don’t include configuration for the web server, you would need to include the name of your controller script in every URL of your site, and your URLs would look like this:

http://example.com/index.php?page=about

when what you really want is:

http://example.com/about

You may want to pass in more information via the URL. For example, if you want to display an article with ID=1 your URL might be:

http://example.com/index.php?type=article&id=1

when you really want:

http://example.com/article/1

or maybe even:

http://example.com/articles/my-article-title

Without configuration, the web server does not know that it should map all incoming requests to your front controller script. When it sees:

http://example.com/about

it might try to load a file called about or about/index.html and return a 404 error.

### Server Configuration

The process for configuring your front controller will depend on what server you are using. I give hints at how to configure this on both Apache and Nginx below. For this weekend we are only using the PHP built-in web server. This dev server doesn’t need any configuration. We automatically get routing to our index.php file for free when we start the built-in server with:

```
$ php -S localhost:4000 -t public/
```

If you are using Apache then you can create a .htaccess file to add your web server configuration. Something like this will work for Apache:

```
RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . index.php
[L]
```

This requires Apache’s rewrite module to be enabled. The configuration first checks that the request is not for an existing file (images, css, js, etc) and then routes everything else to index.php.

Nginx is another popular web server used with PHP. In which case you will add something like this to your nginx.conf:

```
try_files $uri $uri/ /index.php;
```

## Creating Responses

We added in the HTTP Foundation component to give us a nice object-oriented interface for working with HTTP messages. We saw how to create an object from the HTTP request. Now let's use the HTTP Foundation to create our HTTP response objects too. Up until now we have been printing the output directly, and relying on PHP to send this as the response. It's easy to turn this into a `Response` object thanks to HttpFoundation. The component provides different response types to make it easy to send JSON results, or binary files, but for now we will just use a standard HTML response.

The package provides a few different ways of creating responses. You can create a new `Response` object:
`use Symfony\Component\HttpFoundation\Response; $response = new Response($content);`

You can also set the HTTP status code and HTTP headers via the constructor. By default the HTTP status code will be 200. If you want to serve a “404 page not found” you can create a response like this:
`$response = new Response(“not found”, 404);`

Once you have finished generating the response you have to send it to the user. This is done by calling `send()` on the `$response` object, like this:
`$response->send();`

A convenient factory method is also provided, to which you can also (optionally) provide content, status, and headers:
`$response = Response::create($content, $status, $headers);`

The default content is the empty string, so you will want to provide your own value for this. You can omit status and headers and use the defaults (assuming nothing went wrong). The default status is 200. The factory method supports chaining when generating the response, so you can call the `send()` method directly, like this:
`Response::create($content)->send();`

Listing 6.1 shows the new version of our `index.php` file that wraps the Twig result as a HTTP Request object and sends it (line 20).

```
1 <?php
2 use League\Flysystem\Adapter\Local;
3 use League\Flysystem\Filesystem;
4 use Symfony\Component\HttpFoundation\Request;
5 use Symfony\Component\HttpFoundation\Response;
6
7 require __DIR__.'../vendor/autoload.php';
8
9 $request = Request::createFromGlobals();
10
11 $adapter = new Local(__DIR__.'../data');
12 $filesystem = new Filesystem($adapter);
13
14 $variables = json_decode($filesystem->read('menu.json'), true);
15
16 $loader = new Twig_Loader_Filesystem(__DIR__.'../templates');
17 $twig = new Twig_Environment($loader);
18
19 $content = $twig->render('index.html', $variables['index']);
20 Response::create($content)->send();
```

### Listing 6.1: public/index.php
