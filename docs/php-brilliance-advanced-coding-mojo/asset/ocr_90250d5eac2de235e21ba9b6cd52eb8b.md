```
<?php
class Calculator {
    function addThe(float $a, float $b) {
        return $a + $b;
    }
}
```

That's only a very small, but very significant change. The signature of the addThe() method is now declaring that it needs to be given two floats as the type hinting suggests. Despite the fact that the actual code change is such a small one, the impact is enormous. To use the new version of this package would now mean that we have to search through our entire codebase to find every location where this method is called, making the relevant changes as we go along to ensure that that method is only given two float values.

```
<?php
// Where previously we used
$calc->addThe($first, $second);

// We would now need something like this
$calc->addThe((float) $first, (float) $second);
```

Naturally, that places quite a significant burden squarely upon our shoulders. If the package provider was bundling a major security fix with that update, we would have no choice but to follow the refactoring route - we either meet the new demands expressed through the typing in order to take advantage of the security fix or we switch to an alternative package that provides much the same functionality.

Given that it's already perfectly possible for us to write high quality applications, do we really need to upset the apple cart so much by introducing a significant change to the language? The tools are already there to accommodate the foibles of userland implementations by casting the inputs to the specific types that we expressly want to work with. If we really want to get pernikety about the variable types coming in, we can validate for those types and throw up errors and exceptions if client code is getting wrong.