

```php
public function setScreenSize($screenSize) {
    $this->$screenSize = $screenSize;
}
```

```php
public function addStock($numItems) {
    $this->$stockLevel += $numItems;
}
```

```php
public function sellItem() {
    if ($this->$stockLevel > 0) {
        $this->$stockLevel--;
        return true;
    } else {
        return false;
    }
}
```

```php
public function getStockLevel() {
    return $this->$stockLevel;
}
```

```php
class TennisBall implements Sellable {
    private $_color;
    private $_ballsLeft;
```

```php
public function getColor() {
    return $this->$color;
}
```

```php
public function setColor($color) {
    $this->$color = $color;
}
```

```php
public function addStock($numItems) {
    $this->$ballsLeft += $numItems;
}
```

```php
public function sellItem() {
    if ($this->$ballsLeft > 0) {
        $this->$ballsLeft--;
        return true;
    } else {
        return false;
    }
}
```

```php
public function getStockLevel() {
    return $this->$ballsLeft;
}
```

```php
class StoreManager {
    private $_productList = array();
```

![](img/ede05b7b77968b82cbd9a513122fb183_244_0.png)

# 创建和使用接口

库存中有 102 台 42 英寸电视和 100 个黄色网球。

正在卖出一台电视...

正在卖出两个网球...

现在库存中有 99 台 42 英寸电视和 98 个黄色网球。

已完成

图 8-7

# 第二部分：学习语言

# 工作原理

此脚本创建了一个名为 `Sellable` 的接口，其中包含三个方法声明：

```php
public function addStock($numItems);
public function sellItem();
public function getStockLevel();
```

接下来，创建了两个类——`Television`（电视）和 `TennisBall`（网球）。这两个类彼此无关，包含不同的属性和方法；例如，`Television` 包含一个私有的 `$_screenSize` 属性以便访问，而 `TennisBall` 包含一个私有的 `$_color` 属性以及相关的方法。

然而，这两个类都实现了 `Sellable` 接口。这意味着它们提供了实现 `Sellable` 中声明的三个方法——`addStock()`、`sellItem()` 和 `getStockLevel()`——的代码。它们实现得正确。顺便提一下，每个类记录库存的方式都不同；`Television` 在 `$_stockLevel` 中记录库存水平，而 `TennisBall` 有一个 `$_ball` 属性。这完全没有关系；从外部世界的来看，重要的是这些类正确地实现了 `Sellable` 接口中的三个方法。

接下来，脚本创建了一个 `Manager` 类，用于在在线商店中存储和处理销售的产品。该类包含一个私有的 `$_productList` 用于存储不同类型的产品；一个 `addProduct()` 方法用于将产品添加到产品列表中；以及一个 `stockUp()` 方法用于遍历产品列表，并将每个产品类型的库存水平增加 100。

`stockUp()` 调用了对象的 `addStock()` 方法向库存中添加商品；它知道这种方法必须存在，因为它处理的是 `Sellable` 接口。注意，`addProduct()` 使用了类型提示来确保传递它的所有对象都实现了 `Sellable` 接口（你可以使用接口名称代替类名来使用类型提示）：

```php
public function addProduct( Sellable $product ) {
```

最后，脚本测试了接口和类。它创建了一个 `Television` 对象 `$tv`，并将其屏幕设置为 42 英寸。同样，它创建了一个 `TennisBall` 对象 `$ball`，并将其颜色设置为黄色。
