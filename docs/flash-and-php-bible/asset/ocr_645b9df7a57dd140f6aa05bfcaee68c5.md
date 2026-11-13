The following are a few important points to keep in mind with using this specialized gateway:

+   - Sessions won't work properly.
+   - cURL must be enabled in PHP
+   - The server will experience a drop in performance.
+   - It should only be used on a development system.

# ## Testing AMFPHP with a custom service

With AMFPHP properly installed, you can test a very simple service using the service browser. Later, you build a small search application in Flash and PHP.

An AMFPHP service is a standard PHP file that is built in a known order. For example, the first part of a service file is the method table, which is used to expose the available methods and define the access restrictions of that service.

A method table is a multidimensional array containing each of the methods. This sample method table defines the method getDate, which returns the current UNIX timestamp from PHP. The method table is located within the constructor of the class seen in the next portion of code.

```
```php
$this->methodTable = array
(
    "getDate" => array
    (
        "access" => "remote",
        "description" => "Example, returns Unix timestamp"
    )
);
```
```

Continuing with this example, you would create the sample PHP class, which will become the AMFPHP service. Here is the sample class, which contains one method and the constructor.

```
```php
<?php

class Example
{

function Example()
{

$this->methodTable = array
(
    "getDate" => array
    (
        "access" => "remote",
        "description" => "Returns the current date."
    )
```
```