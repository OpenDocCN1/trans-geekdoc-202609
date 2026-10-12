

## 3.2. 面向对象编程中的弱映射

PHP 8 引入了弱映射的概念，这是面向对象编程的一项宝贵补充。弱映射提供了一种将数据与对象关联的方式，而不会阻止这些对象在代码中其他地方不再被引用时被垃圾回收。在本节中，我们将探讨弱映射的概念及其在 PHP 中的应用。

### 3.2.1. 理解弱映射

在传统的关联数组或映射中，对象被用作键来与其关联数据。然而，使用对象作为数组键会导致对这些对象的强引用，即使它们不再需要，也会阻止它们被垃圾回收。

另一方面，弱映射允许你将数据与对象关联，而无需创建强引用。这意味着，如果对某个对象的唯一引用仅存在于 `WeakMap` 中，那么当该对象在代码的其他地方不再被使用时，它就可以被垃圾回收。

### 3.2.2. 创建弱映射

你可以在 PHP 8 中使用 `WeakMap` 类来创建弱映射。以下是创建一个空弱映射的方法：

```php
$weakMap = new WeakMap();
```

### 3.2.3. 将数据与对象关联

要使用弱映射将数据与对象关联，可以使用 `set()` 方法，指定一个对象作为键，关联的数据作为值：

```php
$object = new stdClass();
$weakMap->set($object, "Associated Data");
```

在本例中，我们创建了一个新的 `stdClass` 对象，并使用 `set()` 方法将字符串“Associated Data”与其关联。

### 3.2.4. 从弱映射中检索数据

你可以使用 `get()` 方法从弱映射中检索关联的数据，提供对象作为键：

```php
$data = $weakMap->get($object);
```

此时 `$data` 变量将包含关联的数据，本例中即为“Associated Data”。

### 3.2.5. 检查对象是否存在于弱映射中

要检查对象是否作为键存在于弱映射中，可以使用 `has()` 方法：

```php
if ($weakMap->has($object)) {
    echo "Object found in Weak Map";
} else {
    echo "Object not found in Weak Map";
}
```

此代码片段将判断 `$object` 是否作为键存在于弱映射中。

### 3.2.6. 从弱映射中移除对象

如果你不再需要在弱映射中将对象与数据关联，可以使用 `delete()` 方法将其移除：

```php
$weakMap->delete($object);
```

执行此操作后，该对象将不再与弱映射中的任何数据关联。

### 3.2.7. 弱映射的用例

弱映射在以下场景中特别有用：你希望暂时将数据与对象关联，或者以一种不阻止对象在不再需要时被垃圾回收的方式进行关联。弱映射的一些常见用例包括：

*   **缓存**：你可以使用弱映射来缓存与对象关联的数据，而不会阻止这些对象在不再使用时被清理。
*   **事件监听器**：在事件驱动编程中，弱映射可用于将事件监听器与对象关联。当对象不再需要时，关联的事件监听器可以被自动移除。
*   **对象相关元数据**：在使用面向对象编程时，你可能希望将元数据或附加信息附加到对象上。弱映射提供了一种无需创建对对象的强引用即可实现此目的的方法。
*   **资源管理**：在管理与对象关联的资源（例如数据库连接）时，弱映射有助于确保在对象不再被引用时释放资源。

总之，PHP 8 中的弱映射提供了一种强大的工具，用于将数据与对象关联，而不会阻止这些对象在不再需要时被垃圾回收。它们在面向对象编程场景中尤为宝贵，适用于需要临时或非侵入式关联的场景，有助于编写更高效、更节省内存的 PHP 代码。

---

## 3.3. 静态返回类型及其用法

PHP 8 引入了为方法声明 `static` 返回类型的能力。此功能通过允许你指定方法返回其所属类的实例，增强了面向对象代码的类型安全性。在本节中，我们将探讨静态返回类型的概念，并了解如何在 PHP 开发中使用它们。

### 3.3.1. 理解静态返回类型

在 PHP 中，返回类型声明指定了函数或方法应返回的值的类型。在 PHP 8 之前，你可以指定 `int`、`string`、`array` 或类名等返回类型。然而，没有内置的方法来指定某方法应返回其所属类的实例。静态返回类型的引入解决了这一限制。

静态返回类型通过在返回类型声明中使用 `static` 关键字来表示。这意味着该方法应返回其定义所在类的实例，从而实现更好的类型提示和代码清晰度。

### 3.3.2. 声明静态返回类型

要为方法声明静态返回类型，请在方法的返回类型声明中使用 `static` 关键字。示例如下：

```php
class MyClass {
    public function newInstance(): static {
        return new static();
    }
}
```

在本例中，`newInstance()` 方法被声明为返回同一个类的实例（`static`）。这意味着当你在 `MyClass` 的实例上调用 `newInstance()` 时，它将返回一个 `MyClass` 的实例。

### 3.3.3. 静态返回类型的用例

静态返回类型在面向对象 PHP 开发中提供了多种优势和用例：

*   **流式接口**：静态返回类型常用于流式接口，其中方法返回同一个类实例以允许方法链调用。例如，你可以像 `$object->method1()->method2()->method3()` 这样链式调用多个方法。
*   **工厂方法**：静态返回类型在创建并返回同一类或子类实例的工厂方法中很有用。这在扩展类时提供了更大的灵活性。
*   **构建器模式**：在构建器设计模式中，静态返回类型支持通过方法链逐步构建复杂对象。
*   **方法重写**：当子类重写父类的方法时，可以使用静态返回类型来指明重写的方法应返回子类的实例。

### 3.3.4. 示例：流式接口

以下是使用静态返回类型为构建查询对象创建流式接口的示例：

```php
class QueryBuilder {
    private array $query = [];

    public function select(string ...$fields): static {
        $this->query['select'] = $fields;
        return $this;
    }

    public function from(string $table): static {
        $this->query['from'] = $table;
        return $this;
    }

    public function where(string $condition): static {
        $this->query['where'] = $condition;
        return $this;
    }

    public function getQuery(): array {
        return $this->query;
    }
}
```

通过此流式接口，你可以链式调用方法来构建查询：

```php
$queryBuilder = new QueryBuilder();
$query = $queryBuilder->select('id', 'name')
    ->from('users')
    ->where('status = 1')
    ->getQuery();
```

### 3.3.5. 结合静态返回类型的方法重写

在扩展类并重写方法时，你可以使用静态返回类型来确保重写的方法返回子类的实例。这允许更精确的类型提示，并有助于保持代码一致性。示例如下：

```php
class ParentClass {
    public function createChild(): static {
        return new static();
    }
}

class ChildClass extends ParentClass {
    // 使用相同的静态返回类型重写 createChild 方法
}
```

在本例中，当在 `ChildClass` 的实例上调用 `createChild()` 时，它将返回一个 `ChildClass` 的实例。

### 3.3.6. 静态返回类型的优势

静态返回类型在 PHP 开发中提供了多项优势：

