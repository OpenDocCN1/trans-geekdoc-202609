```
<?php
declare(strict_types=1);

class Calculator {
    public function addThe(float $sa, $float $b): float {
        return $sa-$b;
    }
}
```

Hopefully, you'll recognise this class from the previous section of this appendix. If you don't, where is your brain at? We were only just discussing this bit a few pages ago. I suppose you could be forgiven if you happen to be reading this in a coffee shop crewed by remarkably attractive baristas.

Alright, focus.
Here we are again with a very simple object that allows us to add two numbers together. As you can see, we're declaring for the float parameters types of both $sa and $sb. In addition, we're now declaring for the float type by appending to the method signature a class followed by the return type.

As a result, the public interface of objects of this type has now become much more expressive. Not only can we see what types of parameters the addThe method requires, but also we can be confident that the method invocation will give us back a float value as the return type. A string, not an array, but a float.

This is a great boon for us. Since we should be striving for code that is bug-free as it can be, this gives us the ability to express in code a fully documented interface finally. The whole gamut of input parameter types are now catered for with the addition of scalar type hinting, complemented by the ability to hint the whole gamut of data types that a method will return.

When our colleagues and co-developers read the code we've written, the ability to readily discern the type of thing that will come back from a particular method invocation has enormous value.

Should such a method fail to return the correct data type, the failure will be isolated and localised to the method itself, which in turn can lead to some very targeted bugfixing attention. The benefit of this becomes even more apparent when you consider