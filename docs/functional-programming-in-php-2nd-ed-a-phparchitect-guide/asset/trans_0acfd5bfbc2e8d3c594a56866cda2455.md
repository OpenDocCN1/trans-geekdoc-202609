

泛型提供了一种有用的方法，可以将某种类型处理引入 PHP 的姐妹语言 Hack。它们通过接受任何类型（如标量（`int`、`string` 等）、数组和类）来执行此操作。一旦在 `Generic` 的实例上设置了类型，就只能向 `Generic` 添加相同指定类型的内容。因此，如果创建了一个泛型并分配了字符串类型的值，则它将推断整个泛型为字符串类型，并禁止添加其他类型的值。

这一切都很好，但仅靠这一点并不能提供多大帮助。因此，你还可以向类定义添加方法来处理其内容的操作。这可能包括诸如 `map()` 之类的操作，它有助于对值列表执行方法。泛型还允许你编写以通用方式对数据结构进行操作的函数。这意味着你可以编写可跨类型使用的代码，并防止为每种不同类型重复形式。

你可以使用一组 PHP 对象、`instanceof` 检查和值的强制转换来实现类似的效果。但是，拥有对该功能的语言支持可以让你专注于业务问题，而不是试图实现自己的类型系统。

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

在 Listing 5.3 中，类型 `T` 用于指示当变量传递给它时将推断的类型。你几乎可以将其视为一种变量类型——在定义时未指定，但在首次调用时指定。如果你传入一个 `string`，解析器将把 `T` 设置为 `string` 类型，否则在传递 `array` 时，`T` 将变为 `array` 类型。

`Generic` 可以包含任何值，但一旦选择了类型（`T`），它就会提供工具来帮助你确保最初提供的类型是允许添加的唯一类型。

查看上面的代码，变量 `$a` 将是 `IO` 的实例，其 `T` 为 `string`，而 `$b` 的 `T` 将为 `int`。这种将类型推断为 `T` 的机制正是使 `Generic` 成为泛型的原因。

另一种有用的实现是创建一个更通用的列表处理类，可用于对列表执行常见操作，无论它们包含何种类型。

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

Listing 5.4 故意更加复杂，并利用了 Hack 更多的类型检查，指定了 `array` 的键和值类型。在这种情况下，当第一个值分配给 `Generic` 时，数组值的类型将采用 `T` 的类型。因此，如果分配了字符串类型的值，则 `T` 和数组值都将设置为字符串类型。

`MappableList` 还有一个构造函数，不仅在其参数上指定了数组类型，还添加了可空的 `?` 前缀。这允许使用默认值 `null` 调用构造函数，或者传递正确类型的数组作为 `$data` 类属性的初始值。

这有助于 `map()` 方法的包装返回值，因此每次调用 map 时，它都会将函数映射的结果以整齐包装好的 `MappableList` 实例返回。

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

实现 `Generic` 将设置 `T` 的类型，在 Listing 5.4 中我们非常小心地在所有地方都将 `T` 指定为所需类型。然后在 Listing 5.5 中调用它时，我们必须确保遵守初始设置的类型（本例中为 `string`），所有后续值必须为相同类型。

Listing 5.5 中调用的映射是一个简单的匿名函数，用于将列表中的所有值转换为大写。`MappableList` 类随后将这个简单的 `array` 列表包装成其自身的实例，返回一个所有值均为大写的新 `MappableList`。

### Shapes

Shapes 允许在 Hack 中使用结构化数据类型，其中可以描述记录并稍后依赖其“形状”。这可能是查询的结果、地图坐标或其他形式的结构化数据。

要声明 `Shape`，必须包含类型定义并布局结构内容的设置方式。

然后可以用数据填充此结构，如 Listing 5.6 所示，博客文章结构被填充了与虚构博客文章相关的一些信息。

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

Shapes 提供了一种基于已填充和提供的字段对内容进行分类的整洁方式。可以对结构进行类型检查，然后根据其中包含的数据和结构以不同方式处理。

Shapes 是在 Hack 应用程序中表示、存储和查询结构化数据的一种简单而有用的方法。

## 5.2 Lambda Expressions

匿名函数在 Hack 中通过引入 Lambda 表达式获得了一种更简洁的语法。与 PHP 的闭包类似，Lambda 表达式可以从其周围环境中获取上下文。事实上，Hack 会隐式地这样做，以减少所需的按键次数。这实际上取消了 PHP 中的 `use` 关键字，并通过自动提取环境变量来替代它。唯一的例外是按引用输入，这仍然必须在 `use` 子句中指定，并以 & 符号开头。

这是一种减少冗余的方法，但 Hack 还有一个绝招，即使用 `==>` 快捷方式定义 Lambda 函数。这就是 Hack Lambda 表达式的精髓。

最好将此示例与等效的 PHP 代码并排描述。这不仅使语法更清晰，而且也非常清楚地展示了语法糖的优势。不过，首先我们需要定义一个简单的辅助函数，用于执行带有一个提供参数的函数。

在 PHP 中，我们会调用它，在这种情况下，我们将一个匿名函数传递给它。

在 Hack 中，可以以更简单、更短的方式编写，重复使用之前的 `apply()` 函数。

```
$add_one = $v ==> $v + 1;
$y = applyFunc(1, $add_one); // 2
```

闭包更加紧凑，具有隐式上下文。

如示例所示，因为 `$func` 与 `$a` 在同一作用域中，变量会自动在闭包（`$func`）内可用。在 PHP 中，它看起来会长一些：

最后的 Hack 示例还演示了 Lambda 表达式的另一个特性，即如果没有参数，必须在表达式开头使用括号。接受多个参数的表达式也是如此。

