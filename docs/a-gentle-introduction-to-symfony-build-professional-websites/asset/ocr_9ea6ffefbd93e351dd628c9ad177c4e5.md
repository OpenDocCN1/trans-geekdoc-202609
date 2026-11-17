```
<p>Hello, world!</p>
<?php include_partial('mypartial', array('mytotal' => $total)) ?>
```

Listing 7-10 - The Partial Can Now Use the Variable, in mymodule/templates/
__mypartil.php

```
<p>Total: <?php echo $mytotal ?></p>
```

All the helpers so far were called by <?php echo functionName() ?>. The partial helper, however, is simply called by <?php include_partial() ?>, without echo, to make it behave similar to the regular PHP include() statement. If you ever need a function that returns the content of a partial without actually displaying it, use get_partial() instead. All the include_helpers described in this chapter have a get_counterpart that can be called together with an echo statement.

TIP Instead of resulting in a template, an action can return a partial or a component. The renderPartial() and renderComponent() methods of the action class promote reusability of code. Besides, they take advantage of the caching abilities of the partials (see Chapter 12). The variables defined in the action will be automatically passed to the partial/component, unless you define an associative array of variables as a second parameter of the method.

```
public function executeFoo()
{
 // do things
 $this->foo = 1234;
 $this->bar = 4567;

 return $this->renderPartial('mymodule/mypartial');
}
```

In this example, the partial will have access to $foo and $bar. If the action ends with the following line:

```
return $this->renderPartial('mymodule/mypartial', array('foo' =>
$this->foo));
```

Then the partial will only have access to $foo.

# Components

In Chapter 2, the first sample script was split into two parts to separate the logic from the presentation. Just like the MVC pattern applies to actions and templates, you may need to split a partial into a logic part and a presentation part. In such a case, you should use a component.

A component is like an action, except it's much faster. The logic of a component is kept in a class inheriting from sfComponents, located in an actions/components.class.php file. Its presentation is kept in a partial. Methods of the sfComponents class start with the word execute, just like actions, and they can pass variables to their presentation counterpart in the same way that actions can pass variables. Partials that serve as presentation for components are named by the component (without the leading execute, but with an underscore instead). Table 7-1 compares the naming conventions for actions and components.

Table 7-1 - Action and Component Naming Conventions

| Convention | Actions | Components |
| --- | --- | --- |
| Logic file | actions.class.php | components.class.php |