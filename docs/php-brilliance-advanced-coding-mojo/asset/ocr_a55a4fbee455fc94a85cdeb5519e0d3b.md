And favour Composition too.

```
<?php
abstract class PizzaBase
{
    private $ingredients = [];
    public function addIngredient($ingredient)
    {
        $this->ingredients[] = $ingredient;
    }
    public function getIngredients()
    {
        return implode(', ', $this->ingredients);
    }
}

class MargheritaPizza
{
    public function __construct()
    {
        $this->addIngredient('cheese');
        $this->addIngredient('tomato');
    }
}

$pizza = new MargheritaPizza();
echo $pizza->getIngredients();
// output: cheese, tomato
```

Going by the UML definition of this pattern, we should now subclass this pizza base in order to start providing decorators. This means that first of all, we need a base decorator, so let’s do that now.