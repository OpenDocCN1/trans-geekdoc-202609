
```php
function processForm() {
    $requiredFields = array( "firstName", "lastName", "password1",
        "password2", "gender" );
    $missingFields = array();

    foreach ( $requiredFields as $requiredField ) {
        if ( !isset( $_POST[$requiredField] ) or !$_POST[$requiredField] ) {
            $missingFields[] = $requiredField;
        }
    }

    if ( $missingFields ) {
        displayForm( $missingFields );
    } else {
        displayThanks();
    }
}

function displayForm( $missingFields ) {
    $results = array (
        "pageTitle" => "Membership Form",
        "scriptUrl" => "registration.php",
        "missingFields" => $missingFields,
        "firstNameAttrs" => validateField( "firstName", $missingFields ),
        "firstNameValue" => setValue( "firstName" ),
        "lastNameAttrs" => validateField( "lastName", $missingFields ),
        "lastNameValue" => setValue( "lastName" ),
        "genderAttrs" => validateField( "gender", $missingFields ),
        "genderMChecked" => setChecked( "gender", "M" ),
        "genderFChecked" => setChecked( "gender", "F" ),
        "favoriteWidgetOptions" => array(
            "superWidget" => setSelected( "favoriteWidget", "superWidget" ),
            "megaWidget" => setSelected( "favoriteWidget", "megaWidget" ),
            "wonderWidget" => setSelected( "favoriteWidget", "wonderWidget" ),
        ),
        "newsletterChecked" => setChecked( "newsletter", "yes" ),
        "commentsValue" => setValue( "comments" )
    );

    require( "templates/registration_form.php" );
}

function displayThanks() {
    $results = array (
        "pageTitle" => "Thank You"
    );

    require( "templates/thanks.php" );
}
?>
```

Run the registration.php script by opening its URL in your Web browser. You should see the registration form appear. Try filling in a few fields and clicking Send Details. Notice how the script behaves much like its equivalent from Chapter 9.

## How It Works

Functionally, this application is pretty much the same as `registration.php` from Chapter 9. The main difference is that the presentation code has been separated from the application code and stored in separate template files in the `templates` folder.

Take a look at the `registration.php` script. Unlike the Chapter 9 script, the `displayForm()` and `displayThanks()` functions no longer contain embedded HTML. Instead, they use `require()` to include the relevant page templates from the `templates` folder:

```php
function displayForm( $missingFields ) {
$results = array (
	"pageTitle" => "Membership Form",
	"scriptUrl" => "registration.php",
	"missingFields" => $missingFields,
	"firstNameAttrs" => validateField( "firstName", $missingFields ),
	"firstNameValue" => setValue( "firstName" ),
	"lastNameAttrs" => validateField( "lastName", $missingFields ),
	"lastNameValue" => setValue( "lastName" ),
	"genderAttrs" => validateField( "gender", $missingFields ),
	"genderMChecked" => setChecked( "gender", "M" ),
	"genderFChecked" => setChecked( "gender", "F" ),
	"favoriteWidgetOptions" => array (
		"superWidget" => setSelected( "favoriteWidget", "superWidget" ),
		"megaWidget" => setSelected( "favoriteWidget", "megaWidget" ),
		"wonderWidget" => setSelected( "favoriteWidget", "wonderWidget" ),
	),
	"newsletterChecked" => setChecked( "newsletter", "yes" ),
	"commentsValue" => setValue( "comments" )
);
require( "templates/registration_form.php" );
}

function displayThanks() {
$results = array (
	"pageTitle" => "Thank You"
);
require( "templates/thanks.php" );
}
```

Each function creates a `$results` array variable containing information to display in the page. The page template then uses this array to display the information. In this way, data can be passed between the application and presentation code. For example, `registration_form.php` uses the `firstNameAttrs` array element to insert any attributes (such as `'class="error"'`) into the `firstName` label's tag, and the `firstNameValue` array element to display any previously typed value in the `firstName` field:

```php
<label for="firstName"<?php echo $results["firstNameAttrs"] ?>>
First name </label>
<input type="text" name="firstName" id="firstName" value="<?php echo $results["firstNameValue"] ?>" />
```

The form helper functions in `registration.php`, such as `validateField()` and `setValue()`, have been rewritten to return their output values, rather than display them using `echo()`. This is so that the values can then be passed via the `$results` array to the template pages.

The end result of these changes is that pretty much all the presentation markup has been removed from `registration.php`, while the template pages contain very little PHP — in fact there is just one chunk of decision-making code (the `if` block near the top of `registration_form.php`), a few calls to `require()` to include the page header and footer files, and a series of `echo` statements to display the results. Generally speaking you should try to limit your template files' PHP code to `echo`/`print` statements, includes, decisions, and loops, and then only if the code is directly related to displaying results. Anything more complex belongs in the application code.

This example could be improved further. For instance, ideally `registration.php` would not contain the form helper functions `validateField()`, `setValue()`, `setChecked()`, and `setSelected()`, because these are specific to the output medium (XHTML). A better approach would be to use classes and inheritance to further separate the presentation logic from the application logic, so that the application logic has no knowledge of the particular output medium (whether it's HTML, XHTML, plain text, PDF, and so on).

A good example of such a technique is the Model-View-Controller design pattern. This is out of the scope of this book, but you can find an overview at `http://en.wikipedia.org/wiki/Model-View-Controller`. A great book on design patterns in general is _Patterns of Enterprise Application Architecture_ by Martin Fowler (Addison-Wesley, ISBN: 978-0321127426).

Another good approach is to use a templating framework such as Smarty (`http://www.smarty.net/`). This powerful framework allows you to separate your presentation code to the point of never needing to include a single line of PHP within your template files. This is great if you're working on a big project with a team of designers who don't want to touch your PHP code.

## Automated Code Testing with PHPUnit

Testing is an important aspect of writing good code. By testing your application thoroughly before you release it, you ensure that the application is as stable and as bug-free as possible (though it's highly likely that it will still contain bugs).

Many approaches to testing code exist. You can manually run the application, try different inputs (such as different form field values), and verify that the application produces the expected output. This technique is known as _integration testing_ because you are testing the application as a whole.

A complementary approach is known as _unit testing_. This involves testing each unit of your application (such as each function or method), rather than the application as a whole. It's usually a good idea to use both integration testing and unit testing to test an application thoroughly.

Because testing a single unit of code is more straightforward than testing an entire application, it's usually possible to automate unit tests, and this is where PHPUnit comes in.

PHPUnit is a framework for automated unit testing. You can use it to write tests in PHP to test each unit of your application, then run the tests automatically and see the results.

To install PHPUnit, you use the PEAR installer (see Chapter 15 for more on PEAR). Because PHPUnit is not in the standard PEAR channels, you first need to run (possibly as root or an admin user):

```
pear channel-discover pear.phpunit.de
```

You should then see:

```
Adding Channel "pear.phpunit.de" succeeded
Discovery of channel "pear.phpunit.de" succeeded
```

Now install PHPUnit as follows (again as root if necessary):

```
pear install --alldeps phpunit/PHPUnit
```

## Try It Out Write a Simple PHPUnit Test Suite

Now that you've installed PHPUnit, try writing some simple tests. In this example you test a few methods of the Car class created in the car_simulator.php script in Chapter 8 (and reprised in the “Documenting Your Code” section earlier in this chapter).

Save the following script as car_tests.php in your document root folder:

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
    "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
<head>
<title>Car Test Suite Example</title>
<link rel="stylesheet" type="text/css" href="common.css" />
</head>
<body>
<h1>Car Test Suite Example</h1>
<pre>
<?php
require_once ( "PHPUnit/Framework.php" );
require_once ( "PHPUnit/TextUI/TestRunner.php" );

class Car {
    public $color;
    public $manufacturer;
    public $model;
    private $_speed = 0;

    public function accelerate() {
        if ( $this->_speed >= 100 ) return false;
        $this->_speed += 10;
```
