# # Integrating the Output Class

Now that we've seen how we can switch easily between different languages by creating several objects, let's take a look at how we would use these objects in a real script.

First of all, we should get rid of the process that creates an object of a specific language. The application ought to be able to switch languages at run time, so the language shouldn't be hard-coded into the script.

The output object should be made a member object of the parent. In our example, the parent object keeps track of the number of visits made by a particular user. We call the output object output:

```
```php
<?php
class App
{
    var $output;

    function App($language)
    {
        $this->setLanguage($language);
    }

    function setLanguage($new_language)
    {
        switch ($new_language) {
        case 'da':
            $this->output = new Danish_Output();
            break;

        case 'pl':
            $this->output = new Polish_Output();
            break;

        default:
            $this->output = new English_Output();
            break;
        }
    }
}
?>
```
```

This class has a method, `setLanguage()`, that is used to change the language. It takes a country code as an argument, and tries to match it up against a list of languages. When it finds the correct language, the member object is created.

Then we create a new class and use it, like this:

```
```php
$obj = new App('da');
$obj->output->outNumFiles(2);
```
```

Notice the use of two arrows `->`. This is necessary, as we want to access the `outNumFiles()` method of the output object. The first arrow accesses the member object called output, and the second arrow accesses the method we want. To change the language:

```
```php
$obj->setLanguage('en');
```
```