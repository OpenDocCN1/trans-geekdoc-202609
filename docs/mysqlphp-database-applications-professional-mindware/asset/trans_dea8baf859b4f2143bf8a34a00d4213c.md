
(描述对象的项目)是变量。而方法（对对象采取的动作）是函数。让我们从一个名为 Category 的简单类开始。

![](img/de0823012275cf4ceebdb822a56e6b71_214_0.png)

> 这不是第 10 章目录应用程序中使用的同一组类。为教学目的，此处的代码已进行了简化。

```php
class Category
{
    //here are the properties
    var $category_name;
    var $category_desc;
    var $category_id;
}
```

这里，在这个类的开头，我们定义了属性。请注意使用 var 来声明每个属性。在 PHP 中，其他地方不需要声明属性，但在类中必须声明。现在我们将创建第一个方法。

```php
class Category
{
    //here are the properties
    var $category_name;
    var $category_desc;
    var $category_id;

    //gets all the properties for a given category_id
    function Category($category_id=0)
    {
        //expecting a category id when the object is
        //instantiated
        if ($category_id == 0)
        {
            return;
        }

        $query = "select category_name, category_desc from
            categories where category_id = $category_id";
        $result = mysql_query($query) or
            die(mysql_error());

        list($category_name, $category_desc) =
        mysql_fetch_array($result);
```

```php
$this->category_name=$category_name;
$this->category_desc=$category_desc;
$this->category_id=$category_id;
}
}
```

这里有几件事需要解释。首先，注意该方法（即函数）的名称与类完全相同。这告诉 PHP 这是构造函数。构造函数在类被实例化后立即自动运行。另一个需要注意的是 $this-> 的使用。它表示当前类中的属性或方法。上面，我们正在为属性赋值：category_id、category_name 和 category_description。如果我们想调用一个方法，我们会用括号表示：$this->method_call() 或 $this->method_call($value)

为了继续这个示例，我们将添加一个用于删除分类的方法。请注意，下面的方法假设数据库包含两个表——一个名为 categories，一个名为 products——并且 categories 与 products 之间存在一对多的关系。因此，您需要确保在分类包含产品时不要删除该分类。

```php
class Category
{
//all the stuff you saw above goes here

    function delete_category($category_id=0)
    {
        //make sure a category_id was defined in the
        //constructor or is indicated explicitly
        if($category_id == 0 && empty($this->category_id))
        {
            $this->error = "Nothing to delete";
            return FALSE;
        }
        //create where clause with the category_id
        //retrieved from the proper place
        if ($category_id !=0)
        {
            $where_clause = "where category_id = 
                $category_id";
        }
        else
        {
            $where_clause = "where category_id = 
                $this->category_id";
        }
```

```
//make sure there are no products left for this
//category
$query = "select * from products  $where_clause";
$result = mysql_query($query) or
    die(mysql_error());
if (mysql_num_rows($result)>0)
{
    $this->error = "There are
still products for this category";
    return FALSE;
}
$query="delete from categories $where_clause";
$result = mysql_query($query) or
    die(mysql_error());
if(mysql_affected_rows() == 0)
{
    $this->error = "There were no rows to delete";
    return FALSE;
}
return TRUE;
}
```

我们现在有一个类，其中包含两个方法——构造函数和 delete_category——以及三个属性。现在是时候让这个类发挥作用了。

## 实例化对象

实例化基本上意味着“创建”。假设我们有一个 PHP 页面，其目的是删除分类。为了使其与上面的类一起工作，我们需要做几件事。首先，我们需要包含包含该类的文件。

```
require "classes.php";
```

接下来我们必须创建一个对象的实例。我们可以用关键字 new 来实现：

```
$c = new Category;
```

现在，使用对象 $c，我们可以使用前面示例中看到的相同语法访问任何属性或方法：$c-> property 或 $c->method()。

现在我们想要组装一个实际从数据库中删除记录的页面。为此示例起见，假设单个 $category_id 已通过查询字符串传递。

```
<?

require "classes.php";

$c = new Category($category_id);

if(!$c->delete_category())
{
    echo "Deletion Failed: $c->error";
}
else
{
    echo "Deletion Succeeded for:";
    echo "<ul>
        <li>$c->category_name
        <li>$c->category_description
        <li>$c->category_id
    </ul>
    ";
}
?>
```

如你所见，这使得页面非常简洁，而这正是大家最终所追求的。

## 继承

到目前为止，我们只使用了一个类。但面向对象编程的巨大优势之一是，一个类的属性和方法可以被另一个类继承。我们将通过编写一个名为 Product 的类来展示一个非常快速的示例。以下是其框架：

```
class Product extends Category
{
    var $product_id;
    var $product_name;
    var $product_price;
}
```

注意 extends 这个词的使用。这告诉 PHP Category 中所有可用的属性和方法都应该在 Product 中可用。如果我们想从 Product 类内部调用 delete_category() 方法，我们可以用 $this->delete_category($category_id) 来调用它。

![](img/de0823012275cf4ceebdb822a56e6b71_218_0.png)

在 PHP 中，父类的构造函数方法在调用子类时不会自动运行。例如，调用 $p = new Product 不会运行 Category() 方法。

现在我们添加一个快速的构造函数方法：

```php
class Product extends Category
{
    var $product_id;
    var $product_name;
    var $product_price;

    function Product($product_id=0)
    {
        //expecting a product_id to be passed
        if ($product_id ==0)
        {
            return FALSE;
        }

        $query = "select product_name, product_desc,
product_price, category_id from
products where product_id = $product_id";

        $result = mysql_query($query);
        list($this->product_name, $this->product_desc,
$this->product_price) =
mysql_fetch_array($result)
;
        $this->Category($category_id);
    }
}
```

请注意，此方法不仅为该产品分配属性值，还调用了 Category 类的构造函数，后者随后为这些属性分配值。请注意，由于继承，我们可以按如下方式编写脚本：

```php
require 'classes.php';

$p = new Product($product_id);
echo $p->category_name;
```

你可以看到 Category 的属性对 Product 对象可用。

## 面向对象代码与过程式代码

这就是百万美元的问题：在你的应用程序中，应该使用面向对象代码还是过程式代码？这又是另一个引发宗教式争论的话题。但实际上没有必要争论，因为有一个正确的答案：取决于情况。如果你有丰富的面向对象编程背景，并且更习惯于编写类，那就这样做。然而，如果你不喜欢面向对象代码的工作方式，只使用函数即可。

![](img/de0823012275cf4ceebdb822a56e6b71_219_0.png)

CD-ROM 上有一些大型类库，其中一些取自 Manual Lemos 令人印象深刻的网站 http://phpclasses.upperdesign.com。他的表单创建和验证类确实很史诗般，但对某些人来说可能有点笨重。

面向对象代码有一些优点和缺点。权衡它们并自行决定是否应该使用类还是仅使用函数。

优点：
- 使用面向对象的方法可以节省时间。
- 你可以创建高度可重用的代码片段。
- 你可以利用网络上免费提供的广泛类库。

缺点：
- 它比过程式方法慢。
- 语法起初可能令人困惑。
- Web 编程并不能利用面向对象代码的许多优势。
- 如果你使用非常大的类库，可能会有性能损失。

## 注释

在任何编程语言中，注释都是必不可少的——不仅对你在编写代码时有用，对后来阅读代码的人也很有用。对你来说可能一目了然的东西，对其他人来说可能完全无法读懂。或者，如果你必须做一些特别复杂的事情，你可能会发现你甚至不理解
