Here is the actual output:

![](bbox=[0.35, 0.17, 0.64, 0.41])

# There's more...

A checkbox element generator would be almost identical to the HTML radio button generator. The main difference is that a set of checkboxes can have more than one value checked. Accordingly, you would use PHP array notation for the element names. The element type should be `Generic::TYPE_CHECKBOX`.

# Creating an HTML select element generator

Generating an HTML single select element is similar to the process of generating radio buttons. The tags are structured differently, however, in that both a **SELECT** tag and a series of **OPTION** tags need to be generated.

# How to do it...

+   1.  First of all, create a new `Application\Form\Element\Select` class that extends `Application\Form\Generic`.
2.  The reason why we extend `Generic` rather than `Radio` is because the structuring of the element is entirely different:

```
```python
namespace Application\Form\Element;

use Application\Form\Generic;

class Select extends Generic
```
```