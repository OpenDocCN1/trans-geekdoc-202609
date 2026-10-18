
Generics provide a useful method of bringing some kind of type handling to PHPs sister language Hack. They perform this action by accepting any type such as a scalar (`int`, `string`, etc), arrays, and classes. Once the type has been set on an instance of a `Generic` it is only possible to add content of the same specified type to the `Generic`. So if a generic is created and assigned a value of type string then it will infer the whole generic is of type string and disallow the addition of values of other types.

All well and good, but this would not be a whole dose of help just on its own. So you can also add methods to the class definition to handle operations on its contents. This might include operations such as `map()` that assists with method execution against a list of values. Generics also allow you to write functions which can operate in a general way on data structures. This means you can write code to be used across types and prevent repeating formalisms for each different type.

You could achieve a similar effect with a set of PHP objects, `instanceof` checks and casts of the values. However, having language support for this feature allows you to concentrate on the business problem rather than attempting to implement your own type system.

**Listing 5.3**

```
class IO<T> {
   private T $data;

   public function __construct(T $value) {
      $this->data = $value;
   }

   public function toScreen() {
      echo (string) $this->data;
   }

   public function write() {
      file_put_contents('/tmp/io_out', $this->data);
   }
}
```

In Listing 5.3 the type `T` is used to indicate the type that will be inferred when a variable is passed into it. You could think of it almost like a variable type—one not specified at the point of definition, but when first called. If you pass in a `string` the parser will set `T` to be a type of `string` otherwise when passing an `array` `T` will become a type of `array`.

A `Generic` can contain any value, but once a type (`T`) is chosen it puts tools in place to help you ensure only the type initially supplied is permissible for addition.

Looking at the code above, the variable `$a` will be an instance of `IO` with a `T` of `string` and `$b` would have a `T` of `int`. This inference of type to `T` is what makes a `Generic` a generic.

Another useful implementation can be to create a more universal list handling class which can be used to perform common operations on lists no matter the type they contain.

**Listing 5.4**

```
class MappableList<T> {
   public array<int, T> $data = [];

   public function __construct(
      ?array<int, T> $initial_value = null
   ) {
      if($initial_value) {
         $this->data = $initial_value;
      }
   }

   public function add(T $value) {
      $this->data[] = $value;
   }

   public function map(callable $function) {
      return new MappableList(
         array_map($function, $this->data)
         );
   }
}
```

Listing 5.4 is deliberately more complicated and makes use of more Hack type checking with the `array` key and value types specified. In this case the type of the array value will adopt the type of `T` when the first value is assigned to the `Generic`. So if a value of type `string` is assigned, then both `T` and the array value with be set to type `string`.

`MappableList` also has a constructor with not only the array type specified on its parameter, but also the nullable `?` prepended too. This allows the constructor to be called with the default value of `null` or by passing an array of the correct type as the initial value for the `$data` class property.

This facilitates the wrapped return value of the `map()` method so any time map is called it will return the result of the function mapping in a neatly wrapped up instance of `MappableList`.

**Listing 5.5**

```
$c = new MappableList;
$c->add('Sawubona');
$c->add('Ibizo');
$c->add('Inja');

$xs = $c->map(function($item) {
   return strtoupper($item);
});

// MappableList (
//   'SAWUBONA',
//   'IBIZO',
//   'INJA',
// )
```

Implementing a `Generic` will set the type of `T` and in Listing 5.4 we have been very careful to specify `T` as the required type across the board. When we then call it in Listing 5.5 we must ensure we abide by the initial type set (`string` in this case) and all subsequent values must be of the same type.

The mapping called from Listing 5.5 is a simple anonymous function to convert all values in the list to uppercase. The `MappableList` class will then wrap this simple `array` list into an instance of itself returning a new `MappableList` with all the values in uppercase.

### Shapes

Shapes allow a structured data type in Hack where records can be described and their “shape” later relied upon. This could be things like the product of a query, map coordinates, or other forms of structured data.

To declare a `Shape` you must include a type definition and layout how the contents of the structure will be set out.

This structure can then be populated with data as evidenced in Listing 5.6 with the blog post structure being filled out with some information relating to a fictional blog post.

**Listing 5.6**

```
$bp = shape(
   'id' => 10,
   'date' => '2015-05-08',
   'tags' => [
      'functional',
      'programming',
      'book',
   ],
   'title' => 'Blog post title',
   'content' => 'The content of the blog post goes here.',
);
print $bp['id']; // 10
```

Shapes provide a neat way of categorizing content based on the fields which are fulfilled and supplied. The structures can be type checked and then handled differently dependent upon the data and structure contained within them.

Shapes are a simple and useful way to represent, store, and interrogate structured data in your Hack applications.

## 5.2 Lambda Expressions

Anonymous functions get a new sweeter syntax in Hack with the introduction of lambda expressions. Similar to PHP’s closure a lambda expression can take in context from its surrounding environment. In fact, Hack does this implicitly to reduce the number of key strokes required. This effectively does away with the `use` keyword found in PHP and replaces it by automatically pulling in the environment variables. The only exception is input by reference, which must still be specified in a `use` clause and preceded by an ampersand.

That is one way to cut down on bloat, but Hack has another trick up its sleeve with the `==>` shortcut for defining a lambda function. This is the essence of a Hack lambda expression.

An example of this is best described side-by-side with the equivalent PHP code. Not only does this make the syntax clearer, but it also very clearly shows the advantages of syntactic sugar. First, though, we need to define a simple helper function to execute a function with one supplied parameter.

In PHP we would then call it and in this case we are passing an anonymous function into it.

In Hack this could be written in a simpler and shorter manner reusing the `apply()` function from before.

```
$add_one = $v ==> $v + 1;
$y = applyFunc(1, $add_one); // 2
```

Closures are even more compact with their implicit context.

As you can see in the example, because `$func` is in the same scope as `$a` the variable is automatically available inside the closure (`$func`). In PHP it would look a little longer:

The last Hack example also demonstrates another trait of lambda expressions where, if you do not have an argument, you must use parenthesis at the beginning of your expression. This is also the case with expressions accepting multiple parameters.
