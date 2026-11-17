# View Elements

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

# Action and Front Controller

The controller doesn’t do much in the previous example, but in real web applications, the controller has a lot of work. An important part of this work is common to all the controllers of the application. The common tasks include request handling, security handling, loading the application configuration, and similar chores. This is why the controller is often divided into a front controller, which is unique for the whole application, and actions, which contain only the controller code specific to one page.

One of the great advantages of a front controller is that it offers a unique entry point to the whole application. If you ever decide to close the access to the application, you will just need to edit the front controller script. In an application without a front controller, each individual controller would need to be turned off.