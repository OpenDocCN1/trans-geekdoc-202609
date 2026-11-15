# # Chapter 3
HTTP

Our web framework is going to deal with HTTP messages. We will receive a HTTP
request, and return a HTTP response.

We need to parse and extract information from the HTTP request. What resource is being
requested? What action is to be taken? What content types does the client accept? Our
application may be accepting input from the user, in which case we'll need to look in the
HTTP request for form field inputs, url parameters, and uploaded files.

We also need to construct a valid HTTP response so the client can understand what we are
sending back to them in reply to their request. This includes the content, and information
about the format and how it is encoded.

Rather than studying the specifications of HTTP messages and URIs we can use a PHP
package that hides all the details and provides a more developer-friendly way of receiving
and creating HTTP messages. The PHP FIG (Framework Interoperability Group) has
defined a standard set of HTTP message interfaces[20] which frameworks and PHP
packages can adopt to improve interoperability. You can search Packagist[14] for popular
PHP packages related to HTTP. We will use the most popular HTTP message abstraction,
the Symfony HttpFoundation component[27]. It is the same component used in many
popular PHP systems like Drupal and Laravel.

Let's go back to our composer.jsonand add the HTTP Foundation component to our
requirements, so Composer can install it in our project. You can edit the composer.jsonfile
manually, or use the Composer requirecommand:

```
$ composer require symfony/http-foundation
```

This will download the most recent stable version. At the time of writing this is v3.0.6.
You will notice that it also downloads the mbstring polyfill package because it is a
required dependency of the HTTP Foundation component. The requireSection of your
composer.json configuration file now looks something like listing 3.1.

```
9 "require": {
10 "symfony/http-foundation": "^3.0" 11 }
Listing 3.1: composer.json
```