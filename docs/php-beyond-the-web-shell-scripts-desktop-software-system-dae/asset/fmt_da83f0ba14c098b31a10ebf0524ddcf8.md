
# PHP-GTK

PHP-GTK is an official PHP extension which provides direct bindings to the GTK+ widget toolkit from PHP. The first version was released in 2001 and the project has enjoyed some success. However activity on the project has waned in recent years, the most recent posting on the official website (`gtk.php.net`) at the time of writing was nearly five years ago in 2010. That said, the code is mature and reasonably complete/stable and it is relatively easy to begin with.

## Pros

*   Provides direct binding to the GTK+ toolkit
*   Fast and complete control over the toolkit elements
*   Officially supported PHP project
*   Availability of tools such as Glade for help with interface design and layout Cross platform
*   PHP compilers such as PriadoBlender, Roadsend PHP and bcompiler offer some support for php-gtk
*   Various additional GTK components are available through the PEAR repository

## Cons

*   Lack of activity on the project raises questions on its future direction (if any)
*   GTK+ doesn’t look native on all platforms, the look and feel of GTK+ apps is most at home on Linux type OSes.
*   GTK+ itself is less popular than it once was, although as a project it is still very active and progressing

| ![](Images/image00249.gif) | `php-gtk` |
| --- | --- |
| | Official PHP GUI toolkit |
| | **Main website** : [http://gtk.php.net/](http://gtk.php.net/) |
| | **Main documentation & Installation info** : [http://gtk.php.net/docs.php](http://gtk.php.net/docs.php) |
| | **Github Repository** : [https://github.com/php/php-gtk-src](https://github.com/php/php-gtk-src) |
| | **Mailing list archives** : [http://marc.info/?l=php-gtk-general](http://marc.info/?l=php-gtk-general) |
| | **Community Sites** |
| | Worldwide Community |
| | [http://php-gtk.eu/](http://php-gtk.eu/) |
| | Brazilian Portal |
| | [http://www.php-gtk.com.br/](http://www.php-gtk.com.br/) |

| ![](Images/image00249.gif) | `Glade` |
| --- | --- |
| | GTK+ visual interface design tool, can be used with php-gtk. |
| | **Main website** : [http://glade.gnome.org/](http://glade.gnome.org/) |
| | **Main documentation & Installation info** : [https://wiki.gnome.org/action/show/Apps/Glade](https://wiki.gnome.org/action/show/Apps/Glade) |
| | **Tutorial** : |
| | Using Glade with php-gtk |
| | [http://gtk.php.net/manual/en/tutorials.helloglade.php](http://gtk.php.net/manual/en/tutorials.helloglade.php) |

# 5.12 Local web server & browser

One general technique that has been employed with varying degrees of success when creating local PHP apps is to deploy the whole web stack locally on each PC. This means installing a copy of PHP and Apache (or Nginx, or similar) and accessing the PHP webpages over a local port (e.g. `http://127.0.0.1:80`) in a web browser.

## Pros

*   Re-use existing web code and web skills, mostly as-is
*   Cross platform

## Cons

*   Heavy resource overhead for the web-server
*   Non-native experience
*   Must be secured to stop external access
*   Web servers can be temperamental if not properly tuned to the system it’s on
*   Large maintenance overhead
*   Larger vector for security exploits
*   Performance hit of using the verbose HTTP protocol for UI->backend interaction
*   Cross-browser compatibility issues occur in the same way as the web, unless a particular browser is deployed or required.

In general this is definitely one to avoid if at all possible, certainly for public distribution of software. It may be worth considering where you have existing web applications you need to deploy in short-order on local machines that you have responsibility for and control over.

If you are going to go down this route, it is worth considering deploying an existing stack “solution” which have already ironed out some of the issues involved in local deployment of web stacks. A handy list of “LAMP” ( LinuxApache/Mysql/(PHP|Perl|Python) ) type stacks can be found on Wikipedia, and likewise a comparison of WAMP (Windows/AMP) stacks can be found there too. Remember that while the solution is generally cross-platform, the set-up and fine-tuning of the web stack can vary a lot across different OSes, depending on exactly what you are trying to achieve and the complexity of your application.

| ![information](Images/image00248.jpeg) | **Further Reading** List of AMP (inc LAMP & WAMP) type stacks on Wikipedia |
| --- | --- |
| | [http://en.wikipedia.org/wiki/List\_of\_Apache%E2%80%93MySQL%E2%80%93PHP\_packages](http://en.wikipedia.org/wiki/List_of_Apache%E2%80%93MySQL%E2%80%93PHP_packages) |

# 5.13 PHP’s Built-in testing server

Since v5.4, PHP comes equipped with a built-in web server, primarily designed for testing purposes. It is intended to be used locally by single users rather than on the public web, so lacks the performance, security and resource management controls a fully-fledged web server like Apache has, and is not extensible by means of modules and the like. Nevertheless, a lightweight server like this makes more sense for local apps than the Apache based solution described above, where these extra facilities aren’t generally required. That said, it still has a longer than desirable list in the “Cons” section.

## Pros

*   Re-use existing web code and web skills, mostly as-is
*   Cross platform
*   No extra server to deploy beyond PHP itself

## Cons

*   Non-native experience
*   Must be secured to stop external access
*   The PHP developers have explicitly stated that it was designed specifically for the testing/development environment.
*   Performance hit of using the verbose HTTP protocol for UI->backend interaction
*   Cross-browser compatibility issues occur in the same way as the web, unless a particular browser is deployed or required.
*   Not all features of servers like Apache are included, so some re-writing of the web app may be required if these are relied upon.

| ![](Images/image00249.gif) | `PHP Built In Web server` |
| --- | --- |
| | PHP’s own built-in test web server |
| | **Main website** : [http://php.net/manual/en/features.commandline.webserver.php](http://php.net/manual/en/features.commandline.webserver.php) |
| | **Installation info** : Installed as part of standard PHP install |
| | **Main documentation** : [http://php.net/manual/en/features.commandline.webserver.php](http://php.net/manual/en/features.commandline.webserver.php) |
| | **Tutorial** |
| | “Taking Advantage of PHP’s Built-in Server” by Vito Tardia |
| | [http://www.sitepoint.com/taking-advantage-of-phps-built-in-server/](http://www.sitepoint.com/taking-advantage-of-phps-built-in-server/) |

# 5.14 Web sockets & browser

A variation on the web server/browser scenarios above is using Web Sockets, part of the evolving HTML5 specification designed to allow 2-way communication and “push” type data flows in the browser. LAMP type stacks and the PHP Built in Web Server don’t, by default, handle Web Socket connections. The specification is quitep new and browser support varies, and you’ll need to deploy a dedicated web socket server or a PHP web socket server library (usually based on spawning PHP CLI processes to handle communications). Beyond that, the pros and cons are roughly the same as those discussed for traditional web server communications. Due to the “push” ability of sockets, communications may be quicker and less frequent.

| ![](Images/image00249.gif) | `Ratchet` |
| --- | --- |
| | Popular PHP WebSocket library. Uses ReactPHP. |
| | **Main website** : [http://socketo.me/](http://socketo.me/) |
