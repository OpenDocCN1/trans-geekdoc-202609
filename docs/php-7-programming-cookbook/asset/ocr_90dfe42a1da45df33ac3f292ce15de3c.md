Also, you can see how the elements appear in the view source page:

![](bbox=[0.18, 0.18, 0.82, 0.45])

# Implementing a form factory

The purpose of a form factory is to generate a usable form object from a single configuration array. The form object should have the ability to retrieve the individual elements it contains so that output can be generated.

# How to do it...

+   1.  First, let's create a class called Application\Form\Factory to contain the factory code. It will have only one property, $elements, with a getter:

```
namespace Application\\Form;

class Factory
{
    protected $elements;
    public function getElements()
    {
        return $this->elements;
    }
    // remaining code
}
```