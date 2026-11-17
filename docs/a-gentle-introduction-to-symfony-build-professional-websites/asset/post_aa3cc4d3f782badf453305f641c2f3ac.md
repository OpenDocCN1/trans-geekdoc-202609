

## View Elements

The view layer can also benefit from some code separation. A web page often contains consistent elements throughout an application: the page headers, the graphical layout, the footer, and the global navigation. Only the inner part of the page changes. That’s why the view is separated into a layout and a template. The layout is usually global to the application, or to a group of pages. The template only puts in shape the variables made available by the controller. Some logic is needed to make these components work together, and this view logic layer will keep the name view. According to these principles, the view part of Listing 2-3 can be separated into three parts, as shown in Listings 2-8, 2-9, and 2-10.

```
Listing 2-8 - The Template Part of the View, in mytemplate.php

<h1>List of Posts</h1>
<table>
<tr><th>Date</th><th>Title</th></tr>
<?php foreach ($posts as $post): ?>
    <tr>
    <td><?php echo $post['date'] ?></td>
    <td><?php echo $post['title'] ?></td>
    </tr>
<?php endforeach; ?>
</table>
```

```
Listing 2-9 - The View Logic Part of the View

<?php
$title = 'List of Posts';
$posts = getAllPosts();
```

```
Listing 2-10 - The Layout Part of the View

<html>
<head>
<title><?php echo $title ?></title>
</head>
<body>
<?php include('mytemplate.php'); ?>
</body>
</html>
```

## Action and Front Controller

The controller doesn’t do much in the previous example, but in real web applications, the controller has a lot of work. An important part of this work is common to all the controllers of the application. The common tasks include request handling, security handling, loading the application configuration, and similar chores. This is why the controller is often divided into a front controller, which is unique for the whole application, and actions, which contain only the controller code specific to one page.

One of the great advantages of a front controller is that it offers a unique entry point to the whole application. If you ever decide to close the access to the application, you will just need to edit the front controller script. In an application without a front controller, each individual controller would need to be turned off.

## Object Orientation

All the previous examples use procedural programming. The OOP capabilities of modern languages make the programming even easier, since objects can encapsulate logic, inherit from one another, and provide clean naming conventions.

Implementing an MVC architecture in a language that is not object-oriented raises namespace and code-duplication issues, and the overall code is difficult to read.

Object orientation allows developers to deal with such things as the view object, the controller object, and the model classes, and to transform all the functions in the previous examples into methods. It is a must for MVC architectures.

> If you want to learn more about design patterns for web applications in an object-oriented context, read Patterns of Enterprise Application Architecture by Martin Fowler (Addison-Wesley, ISBN: 0-32112-742-0). Code examples in Fowler's book are in Java or C#, but are still quite readable for a PHP developer.

## Symfony's MVC Implementation

Hold on a minute. For a single page listing the posts in a weblog, how many components are required? As illustrated in Figure 2-2, we have the following parts:

- Model layer
  - Database abstraction
  - Data access
- View layer
  - View
  - Template
  - Layout
- Controller layer
  - Front controller
  - Action

Seven scripts—a whole lot of files to open and to modify each time you create a new page! However, symfony makes things easy. While taking the best of the MVC architecture, symfony implements it in a way that makes application development fast and painless.

First of all, the front controller and the layout are common to all actions in an application. You can have multiple controllers and layouts, but you need only one of each. The front controller is pure MVC logic component, and you will never need to write a single one, because symfony will generate it for you.

The other good news is that the classes of the model layer are also generated automatically, based on your data structure. This is the job of the ORM library, which provides class skeletons and code generation. If the ORM finds foreign key constraints or date fields, it will provide special accessor and mutator methods that will make data manipulation a piece of cake. And the database abstraction is totally invisible to you, because it is handled natively by PHP Data Objects. So if you decide to change your database engine at anytime, you have zero code to refactor. You just need to change one configuration parameter.

And the last thing is that the view logic can be easily translated as a simple configuration file, with no programming needed.

Figure 2-2 - Symfony workflow

![](img/0f886a7f4cbcc3939be96e985ca35ff4_26_0.png)

That means that the list of posts described in our example would require only three files to work in symfony, as shown in Listings 2-11, 2-12, and 2-13.

```
Listing 2-11 - list Action, in myproject/apps/myapp/modules/weblog/actions/actions.class.php

```php
<?php

class weblogActions extends sfActions
{
    public function executeList()
    {
        $this->posts = PostPeer::doSelect(new Criteria());
    }
}
```
```

```
Listing 2-12 - list Template, in myproject/apps/myapp/modules/weblog/templates/listSuccess.php

```php
<?php slot('title', 'List of Posts') ?>

<h1>List of Posts</h1>
<table>
<tr><th>Date</th><th>Title</th></tr>
<?php foreach ($posts as $post): ?>
<tr>
<td><?php echo $post->getDate() ?></td>
<td><?php echo $post->getTitle() ?></td>
</tr>
<?php endforeach; ?>
</table>
```
```

In addition, you will still need to define a layout, as shown in Listing 2-13, but it will be reused many times.

Listing 2-13 - Layout, in myproject/apps/myapp/templates/layout.php

```
<html>
<head>
<title><?php include_slot('title') ?></title>
</head>
<body>
<?php echo $sf_content ?>
</body>
</html>
```

And that is really all you need. This is the exact code required to display the very same page as the flat script shown earlier in Listing 2-1. The rest (making all the components work together) is handled by symfony. If you count the lines, you will see that creating the list of posts in an MVC architecture with symfony doesn't require more time or coding than writing a flat file. Nevertheless, it gives you huge advantages, notably clear code organization, reusability, flexibility, and much more fun. And as a bonus, you have XHTML conformance, debug capabilities, easy configuration, database abstraction, smart URL routing, multiple environments, and many more development tools.

## Symfony Core Classes

The MVC implementation in symfony uses several classes that you will meet quite often in this book:

- sfController is the controller class. It decodes the request and hands it to the action.
- sfRequest stores all the request elements (parameters, cookies, headers, and so on).
- sfResponse contains the response headers and contents. This is the object that will eventually be converted to an HTML response and be sent to the user.
- The context (retrieved by sfContext::getInstance()) stores a reference to all the core objects and the current configuration; it is accessible from everywhere.

You will learn more about these objects in Chapter 6.

As you can see, all the symfony classes use the sf prefix, as do the symfony core variables in the templates. This should avoid name collisions with your own classes and variables, and make the core framework classes sociable and easy to recognize.

> Among the coding standards used in symfony, UpperCamelCase is the standard for class and variable naming. Two exceptions exist: core symfony classes start with sf, which is lowercase, and variables found in templates use the underscore-separated syntax.

