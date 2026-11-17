module_name/action_name to the script. This means that the action defined in Listing 6-4 can be called by this URL:

http://localhost/index.php/mymodule/index

Adding more actions just means adding more execute methods to the sfActions object, as shown in Listing 6-4.

# Listing 6-4 - Action Class with Two Actions, in frontend/modules/mymodule/actions/actions.class.php

```
class mymoduleActions extends sfActions
{
    public function executeIndex($request)
    {
        // ...
    }

    public function executeList($request)
    {
        // ...
    }
}
```

If the size of an action class grows too much, you probably need to do some refactoring and move some code to the model layer. Actions should often be kept short (not more than a few lines), and all the business logic should usually be in the model.

Still, the number of actions in a module can be important enough to lead you to split it in two modules.

# Symfony coding standards

In the code examples given in this book, you probably noticed that the opening and closing curly braces ({ and }) occupy one line each. This standard makes the code easier to read.

Among the other coding standards of the framework, indentation is always done by two blank spaces; tabs are not used. This is because tabs have a different space value according to the text editor you use, and because code with mixed tab and blank indentation is impossible to read.

Core and generated symfony PHP files do not end with the usual ?> closing tag. This is because it is not really needed, and because it can create problems in the output if you ever have blanks after this tag.

And if you really pay attention, you will see that a line never ends with a blank space in symfony. The reason, this time, is more prosaic: lines ending with blanks look ugly in Fabien's text editor.

# Alternative Action Class Syntax

An alternative action syntax is available to dispatch the actions in separate files, one file per action. In this case, each action class extends sfAction (instead of sfActions) and is named actionNameAction. The actual action method is simply named execute. The file name is the same as the class name. This means that the equivalent of Listing 6-4 can be written with the two files shown in Listings 6-5 and 6-6.

# Listing 6-5 - Single Action File, in frontend/modules/mymodule/actions/indexAction.class.php