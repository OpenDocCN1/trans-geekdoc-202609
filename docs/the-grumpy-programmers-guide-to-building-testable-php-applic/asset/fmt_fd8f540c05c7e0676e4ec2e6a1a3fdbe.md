
Whatever solution you choose, keep in mind the goal: a consistent environment for all locations that your application will exist in.

## 6 Static Code Analysis

Tools for doing static code analysis have come to PHP very late in its lifecycle. Tools like these have been far more common in languages like Java or C++: languages where it’s easy to create complex code…and difficult to tame if it gets out of control.

Obviously it is easier to do static analysis of code that is statically typed and compiled. Proper static code analysis of dynamic languages is difficult and has been the subject of a few research papers. So treat them as tools that compliment what you are doing, not critical parts of the testing toolchain.

In this chapter we will examine several tools that I use every day when working with fairly complex code bases.

For a project where more than one person has to work on it (or integrate it into their own project) it’s important to pick a coding standard. This covers things like tabs vs. spaces, brace location, variable naming conventions, things like that. Sure, there have been plenty of nerd fights over what set of coding standards are the “best”, but most important is to set a standard and FOLLOW it.

Have you ever worked with a programmer who coded in such a distinct style that you could instantly tell which code was his? Don’t be that person. Follow the standard and save being an individual for your choice of code editor.

[PHP Code Sniffer](https://github.com/squizlabs/PHP_CodeSniffer) is a CLI utility that will take your code and compare it to a particular standard. I have found it to be a useful tool for making sure that your code stays organized and consistent.

Let’s run it on a file I created for this project, a Data Mapper for talking to our Postgres database to get information about franchises in our simulation baseball league.

```
chartjes@yggdrasil [09:39:25] [~/Sites/local.ibl/lib/ibl] [master *]
-> % phpcs --standard=Zend FranchiseMapper.php 

FILE: /Users/chartjes/Sites/local.ibl/lib/ibl/FranchiseMapper.php
FOUND 4 ERROR(S) AND 5 WARNING(S) AFFECTING 9 LINE(S)
   6 | ERROR   | Expected 0 spaces before opening brace; 1 found
   7 | ERROR   | Protected member variable "conn" must contain a leading
     |         | underscore
   8 | ERROR   | Protected member variable "map" must contain a leading
     |         | underscore
  15 | WARNING | Line exceeds 80 characters; contains 86 characters
  77 | WARNING | Line exceeds 80 characters; contains 84 characters
 139 | WARNING | Line exceeds 80 characters; contains 90 characters
 142 | ERROR   | Line exceeds maximum limit of 120 characters; contains 181
     |         | characters
 152 | WARNING | Line exceeds 80 characters; contains 117 characters
 154 | WARNING | Line exceeds 80 characters; contains 86 characters

Time: 1 second, Memory: 5.50Mb
```

Ah, look at all the problems it found. Tsk, tsk, Mister Hartjes. That’s some laziness in there. Complaints about line lengths (makes things less readable) and not following proper naming conventions for protected variables.

I will go and fix those right now but let’s see what happens if we go with the default standard it uses.

```
chartjes@yggdrasil [09:39:37] [~/Sites/local.ibl/lib/ibl] [master *]
-> % phpcs FranchiseMapper.php 

FILE: /Users/chartjes/Sites/local.ibl/lib/ibl/FranchiseMapper.php
FOUND 13 ERROR(S) AND 5 WARNING(S) AFFECTING 18 LINE(S)
   2 | ERROR   | Missing file doc comment
   5 | ERROR   | Missing class doc comment
   6 | ERROR   | Expected 0 spaces before opening brace; 1 found
  10 | ERROR   | Missing function doc comment
  15 | WARNING | Line exceeds 85 characters; contains 86 characters
  20 | ERROR   | You must use "/**" style comments for a function comment
  36 | ERROR   | Missing function doc comment
  53 | ERROR   | Missing function doc comment
  74 | ERROR   | Missing function doc comment
  95 | ERROR   | Missing function doc comment
 109 | ERROR   | Missing function doc comment
 127 | ERROR   | Missing function doc comment
 136 | ERROR   | Missing function doc comment
 139 | WARNING | Line exceeds 85 characters; contains 90 characters
 142 | WARNING | Line exceeds 85 characters; contains 181 characters
 149 | ERROR   | Missing function doc comment
 152 | WARNING | Line exceeds 85 characters; contains 117 characters
 154 | WARNING | Line exceeds 85 characters; contains 86 characters

Time: 0 seconds, Memory: 6.75Mb
```

That’s a completely different set of problems. In this case, it expects that I would put [DocBlock](https://en.wikipedia.org/wiki/PHPDoc) comments around all my methods along with some warnings about line length.

It is an interesting exercise to analyze your code using all of the standards that it includes by default, just to see some other ideas on how code should look. The PHP Code Sniffer website also shows you how to create your own coding standards should you want to undertake such a task.

However, ensuring 100% compliance with what PHP Code Sniffer reports isn’t always a practical goal to aim for. For example, it complains about my use of non-camel-cased, protected variable names in our model classes. They are protected to prevent direct access by developers and are non-camel-cased to match the values that are in the database tables themselves.

Altering the code to allow the model variables to be camelCased and prefixed with an underscore (as is the Zend convention) might also not be practical. The code that dynamically determines what model variable needs to be returned would also need to be altered.

Should I do the necessary work to make it happen? That depends. Do I have tests in place that I can run while I tweak things under the hood to make it happen? Of course I do! Showing you boring patches for the changes I made to the code will not suffice. Instead, let me show you the code itself and we’ll discuss what had to be done.

I really only had to change code in one place: the `BaseModel` I am extending all my other models off of:

```
<?php

// Base data model that all our existing models will extend off of
namespace IBL;

class BaseModel
{
    protected $_id;

    public function setId($id) 
    {
        // Never allow the ID for a model to be overwritten
        if (!$this->_id) {
            $this->_id = $id; 
        } 
    }

    public function __call($name, $args)
    {
        if (preg_match('/^(get|set)(\w+)/', $name, $match)) {
            $attribute = $this->validateAttribute($match[2]);

            if ($match[1] == 'get') {
                return $this->{$attribute};
            } else {
                $this->{$attribute} = $args[0];
            }
        } else {
            throw new \Exception(
                'Call to undefined ' . 
                __CLASS__ . 
                '::' . 
                $name . 
                '()'
            ); 
        }
    }
    
    protected function validateAttribute($name) 
    {
        // Convert first character of the string to lowercase 
        $field = '_' . $name;
        $field[1] = strtolower($field[1]); 

        // We don't use __CLASS__ here because there are scope problems
        $currentClass = get_class($this);

        if (in_array($field, array_keys(get_class_vars($currentClass)))) {
            return $field; 
        }

        return false;
    }
}
```

Before all this, I used to have an `inflect()` module that was using PHP 5.3 closures to take something like `HomeTeamId` and turn it into `home_team_id`, and then match it against the available class variables for the model.

In order to make all the class variables for the class models conform to the standard, I no longer needed the inflector. Sure, it was a neat bit of code that used a closure as a callback, but the cleverness wasn’t needed.
