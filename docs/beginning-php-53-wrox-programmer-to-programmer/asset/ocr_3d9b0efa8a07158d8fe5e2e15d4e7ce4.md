# Part II: Learning the Language

```
echo "<h2>Consuming an apple...</h2>h2";
$apple = new Fruit;
$apple->consume();

echo "<h2>Consuming a grape...</h2>h2";
$grape = new Grape;
$grape->consume();

?></body>
</html>
```

You can see the output from this script in Figure 8-6. Notice how the overridden methods, peel() and slice(), are called for the Grape object, where the parent class's peel() and slice() methods are called for the Fruit object.

![](bbox=[0.166, 0.375, 0.733, 0.725])

# Preserving the Functionality of the Parent Class

Occasionally you want to override the method of a parent class in your child class, but also use some of the functionality that is in the parent class's method. You can do this by calling the parent class's overridden method from within the child class's method. To call an overridden method, you write parent:: before the method name:

```
parent::someMethod();
```