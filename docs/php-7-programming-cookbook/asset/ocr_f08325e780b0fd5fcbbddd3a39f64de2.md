Here is the actual output:

![](bbox=[0.32, 0.17, 0.68, 0.38])

# **Creating an HTML radio element generator**

A radio button element generator will share similarities with the generic HTML form element generator. As with any generic element, a set of radio buttons needs the ability to display an overall label and errors. There are two major differences, however:

+   - Typically, you will want two or more radio buttons
- Each button needs to have its own label

# How to do it...

+   1. First of all, create a new `Application\Form\Element\Radio` class that extends `Application\Form\Genericic`:
```php
namespace Application\Form\Element;
use Application\Form\Genericic;
class Radio extends Genericic
{
// code
}
```
2. Next, we define class constants and properties that pertain to the special needs of a set of radio buttons.