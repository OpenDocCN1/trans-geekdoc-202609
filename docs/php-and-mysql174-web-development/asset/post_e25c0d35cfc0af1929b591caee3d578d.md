
override it. That is, a trait's methods override inherited methods, but the current's class methods override a trait's methods.

One nice thing about traits is that you can combine multiple traits and when there are methods with the same names, you can explicitly specify which trait's functionality you wish nnto use. Consider the following example:

```php
<?php
trait fileLogger
{
    public function logmessage($message, $level='DEBUG')
    {
        // write $message to a log file
    }
}
trait sysLogger
{
    public function logmessage($message, $level='ERROR')
    {
        // write $message to the syslog
    }
}
```

```php
class fileStorage
{
    use fileLogger, sysLogger
    {
        fileLogger::logmessage insteadof sysLogger;
        sysLogger::logmessage as private logsysmessage;
    }
}
```

```php
function store($data)
{
    // ...
    $this->logmessage($message);
    $this->logsysmessage($message);
}
?>
```

We use the two different logging traits by listing them in the use clause. Because each of the traits implements the same logmessage() method, we must specify which one to use. If we don't specify this, PHP will generate a fatal error as it will not be able to resolve the conflict.

You can specify which one to use using the insteadof keyword, as in the following example:
fileLogger::logmessage insteadof sysLogger;

This line explicitly tells PHP to use the logmessage() method from the fileprivate trait. However, in this case we'd also like access to the logmessage() method from the sysLogger trait. In order to do so, we rename it using the keyword, as follows:
sysLogger::logmessage as private logsysmessage;

This method will now be available as the logsysmessage() method. Note that in this particular example, we've also changed the visibility of the method. This is not required, but is shown here so you can see that this is possible.

You can even take a step further, and build traits that include or consist entirely of other traits. To do this, use a use statement inside a trait, just as you would inside a class.

## Designing Classes

Now that you know some of the concepts behind objects and classes and the syntax to implement them in PHP, it is time to look at how to design useful classes.

Many classes in your code will represent classes or categories of real-world objects. Examples of some classes you might use in Web development include pages, user interface components, shopping carts, error handling, product categories, and customers.

Objects in your code can also represent instances of the previously mentioned classes—for example, the home page, a particular button, or the shopping cart in use by Fred Smith at a particular time. Fred Smith can be represented by an object of type customer. Each item that Fred purchases can be represented as an object, belonging to a category or class.

In the preceding chapter, you used simple include files to give the fictional company TLA Consulting a clean look and feel across the different pages of your site. Using classes and the timesaving power of inheritance, you can create a more advanced version of the same.

Now you want to be able to quickly create pages for T that look and behave in the same way. You should be able to modify these pages to suit the different parts of the site.

For purposes of this example, you are going to create a Page class. The main goal of this class is to limit the parts that change from page to page, while automatically generating the elements that stay the same. The class should provide a flexible framework for creating new pages and should not compromise your freedom.

Because you are generating the page from a script rather than with static HTML, you can add any number of things including functionality to:

- Enable you to alter pages in only one place. If you change the copyright notice or an extra footer, you should need to make the change in only a single page.
- Have default content for most parts of the page but be able to modify each element where required, setting custom values for the title and metatags.

## Writing the Code for Your Class

- Recognize which page is being viewed and alter navigation elements to suit; there is no point in having a button that takes you to the home page located on the home page.
- Allow you to replace standard elements for particular pages. For instance, you want different navigation buttons in sections of the site, you should be able to replace the standard ones.

## Writing the Code for Your Class

Having decided what you want the output from your code to look like and a few features you would like for it to, how do you implement it? Later in the book, we discuss design and project management for large projects. For now, we concentrate on the parts specific to writing object-oriented PHP.

The class needs a logical name. Because it represents a page, you can call it Page. To declare a class called Page, type

```php
class Page
{}
```

The class needs some attributes. For this example, set elements that you might want changed from page to page as attributes of the class. The main contents of the page, which are a combination of HTML tags and text, are called $content. You can declare the content with the following line of code within the class definition:

```php
public $content;
```

You can also set attributes to store the page's title. You will probably want to change this title to clearly show what particular page the visitor is looking at. Rather than blank tiles, you can provide a default title with the following declaration:

```php
public $title = "TLA Consulting Pty Ltd";
```

Most commercial web pages use metatags to help search engines index them. To be useful, metatags should probably change from page to page. Again, you can provide a default value:

```php
public $keywords = "TLA Consulting, Three Letter Abbreviation,
of my best are search engines";
```

The navigation buttons shown on the original page in Figure 5.2 (the preceding chapter) should probably be kept the same on page to avoid confusing people, but to change them easily, you can make them an attribute. Because the number of buttons might be variable, you can use an array and store the text for the button and the URL it should point to:

```php
public $buttons = array(
"Home" => "home.php",
"Contact" => "contact.php",
"Services" => "services.php",
"Site Map" => "map.php"
);
```

To provide some functionality, the class also needs operations. You can start by providing accessor functions to set and get the values of the attributes defined:

```php
public function __set($name, $value)
{
    $this->$name = $value;
}
```

The __set() function does not contain error checking (for brevity), but this capability can be easily later, as required. Since it is unlikely that you will be requesting any of these values from outside the class, you can elect not to provide a __get() function, as done here.

The main purpose of this class is to display a page so you need a function. We called ours Display(), and here it is:

```php
public function Display()
{
    echo "<html><head>\n";
    $this->DisplayTitle();
    $this->DisplayKeywords();
    $this->DisplayStyles();
    echo "</head><body>\n";
    $this->DisplayHeader();
    $this->DisplayMenu($this->buttons);
    echo $this->content;
    $this->DisplayFooter();
    echo "</body>\n</html>\n";
}
```

The function includes a few echo statements to display HTML but mainly consists of calls to other functions. As you have probably guessed by their names, these other functions display parts of the page.

Breaking up functions like this is not compulsory. All these separate functions might have been combined into one big function. We separated them out for a number of reasons.

Each function should have a defined task to perform. The simpler this task, the easier writing and testing the function will be. Don't go too far; if you break your program into too many small units, it will be hard to read.

Using inheritance, you can override operations. When you replace one large Display() function, it is unlikely that you will want to change the entire page is displayed. It will be much better to break up the display into a few self-contained tasks and be able to override only the parts that you want to change.
