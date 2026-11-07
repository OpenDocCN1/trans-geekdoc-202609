
A very simple solution to this is to move the code that loads the template into its own function. Amend `index.php` to the code below.

**Example: [OOP-EntryPoint-Template](https://github.com/spbooks/phpmysql7/tree/OOP-EntryPoint-Template)**

```
<?php
function loadTemplate($templateFileName, $variables) {
    extract($variables);

    ob_start();
    include  __DIR__ . '/../templates/' . $templateFileName;

    return ob_get_clean();
}

try {
    include __DIR__ . '/../includes/DatabaseConnection.php';
    include __DIR__ . '/../classes/DatabaseTable.php';
    include __DIR__ . '/../controllers/JokeController.php';

    $jokesTable = new DatabaseTable($pdo, 'joke', 'id');
    $authorsTable = new DatabaseTable($pdo, 'author', 'id');

    $jokeController = new JokeController($jokesTable, $authorsTable);

    $action = $_GET['action'] ?? 'home';

    $page = $jokeController->$action();

    $title = $page['title'];

    $variables = $page['variables'] ?? [];
    $output = loadTemplate($page['template'], $variables);

} catch (PDOException $e) {
    $title = 'An error has occurred';

    $output = 'Database error: ' . $e->getMessage() . ' in ' .
    $e->getFile() . ':' . $e->getLine();
}

include  __DIR__ . '/../templates/layout.html.php';
```

I’ve created the `loadTemplate` function to load template files and create variables supplied in the `$variables` argument.

When the function is called, it’s given the name of the template specified by the controller action in the `$page`, along with the variables specified in the `$page['variables']`:

```
$variables = $page['variables'] ?? [];
$output = loadTemplate($page['template'], $variables);
```

Because the `'variables'` key may not exist, I’ve used the now familiar `??` operator to set the `$variables` variable to either the variables specified by the return value of the controller action or an empty array.

By moving the code that loads the template into its own function, if the `variables` array does contain keys called `page` or `title`, the existing variables won’t be overwritten, because they don’t exist inside the function’s scope.

In this chapter, I’ve shown you how to use object-oriented programming to break up the code further and reduce repetition. We’ve also begun to add a clearer structure to the controller code.

With this new structure, adding a new page to the website is now a very simple task:

1. Create a function in `jokeController` that returns an array containing the template file name, page title and variables used by the template.
2. Access the page by specifying the name of the function in the URL: `index.php?action=functionName`.

You may have realized that this isn’t very scalable. A website with 100 pages would require a controller with 100 functions. That would be very difficult to manage.

In the next chapter, I’ll show you how to make `index.php` usable with other controllers and start thinking about code that we can use on different websites.

## Summary

In this chapter, you’ve learned the basics of object-oriented programming and how to break code up into classes. With these changes in place, adding new pages to the website has become much simpler and requires a lot less copying and pasting (remember the DRY principle!).

Each page is now a function call accessed via `index.php` instead of having one file per page. As a result, all the setup code that happens on every page for connecting to the database and loading class files can be done in a single place.

# Chapter 9: Creating an Extensible Framework

Now that you’re able to write a controller with methods, and call those methods from `index.php`, the next step is to add the rest of the pages for managing the website. Currently, we can add jokes to the database through `index.php` by specifying an `action` URL parameter. However, a real website will need to do considerably more than handle basic database operations for a single table.

The next extension of the website will be allowing users to register as authors and post their own jokes. However, before we do that, I’ll show you how to write a modern, flexible framework to build upon. By the end of this chapter, you’ll have the foundation for building any website, and you’ll have a good understanding of the techniques and concepts used by professional PHP developers.

We’re not going to add any new features in this chapter. Instead, I’m going to show you how the code can be organized so that it can be reused on each website you build.

In the last chapter, we ended with this code in `index.php`:

```
<?php
function loadTemplate($templateFileName, $variables) {
    extract($variables);

    ob_start();
    include  __DIR__ . '/../templates/' . $templateFileName;

    return ob_get_clean();
}

try {
    include __DIR__ . '/../includes/DatabaseConnection.php';
    include __DIR__ . '/../classes/DatabaseTable.php';
    include __DIR__ . '/../controllers/JokeController.php';

    $jokesTable = new DatabaseTable($pdo, 'joke', 'id');
    $authorsTable = new DatabaseTable($pdo, 'author', 'id');

    $jokeController = new JokeController($jokesTable, $authorsTable);

    $action = $_GET['action'] ?? 'home';

    $page = $jokeController->$action();

    $title = $page['title'];

    $variables = $page['variables'] ?? [];
    $output = loadTemplate($page['template'], $variables);

} catch (PDOException $e) {
    $title = 'An error has occurred';

    $output = 'Database error: ' . $e->getMessage() . ' in ' .
    $e->getFile() . ':' . $e->getLine();
}

include  __DIR__ . '/../templates/layout.html.php';
```

This lets us call any of the functions in the `JokeController` class by specifying the `action` URL parameter—for example, by linking to or visiting `index.php?action=list`.

## Search Engine Optimization

Before we make any structural changes to the code, we need to do a little housekeeping. In PHP, functions aren’t case-sensitive. `list` is treated exactly the same way as `LIST`. Due to case insensitivity, visiting `index.php?action=list` will display the page, but so will `index.php?action=LIST` or `index.php?action=List`. This may seem like a good thing, as people will be able to mistype the URL and still see the correct page. However, this feature can also cause problems for search engines.

Some search engines will see these two URLs as two entirely different pages, even if they display the exact same content. Both `index.php?action=LIST` and `index.php?action=list` will appear in search results. You might think “Great, more of my pages will appear in search results!” But search engines generally dislike “duplicate content”, either ranking it lower or ignoring it altogether. Would you prefer one result on the first page or two results potentially much further down in the search pages?

There are several ways to fix this. You can tell search engines to ignore certain pages. Or you can tell them which is the “canonical” (primary) version. But this can be difficult to manage on larger sites, and it’s usually simpler to enforce strict URLs. A common way to do this is to force all URLs to be lowercase.

Forcing URLs to be lowercase is possible using a simple piece of PHP code, which detects whether or not the user entered a lowercase URL:

```
$action = $_GET['action'];

if ($action == strtolower($action)) {
    $jokeController->$action();
} else {
    echo 'Sorry that page does not exist.';
}
```

This code compares `$action` to a lowercase version of `$action`. The `strtolower` function converts any string to lowercase: `LISTJOKES`, `listJokes` or `listjokes` all become `listjokes`. By comparing the original `$action` to the lowercase version, it’s possible to work out whether or not someone came to the page using a lowercase value for `$action`. If they didn’t, an error is displayed. Visitors and search engines will only see the content on the lowercase version of the URL.

### Configuration: PHP vs Server
