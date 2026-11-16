

## 组合模式

你在第 2 章的 `Instrument` 接口中已经初步接触过一种模式——组合模式。请再次查看图 4-1 中的类图。

![](img/a1b732997d9cb194dceec0570dc79710_89_0.png)

图 4-1：表示组合对象的用例图

图 4-1 显示，`DrumSet` 对象可以由 `Drum` 和 `Cymbal` 对象组成。可以将 `Drum` 和 `Cymbal` 视为 `DrumSet` 对象的子对象。`DrumSet` 可以由任意数量的 `Drums` 和 `Cymbals` 组成。不过需要注意的是，`DrumSet` 及其子对象的类型相同，即均为 `Instrument`。当客户端对象与 `DrumSet` 交互时，它使用的接口与与其子对象交互时相同。这种关系被称为 _组合模式_。

图 4-2 展示了组合模式的一般情况。

![](img/a1b732997d9cb194dceec0570dc79710_89_1.png)

图 4-2：组合模式的一般情况

组合模式包含两部分：组件抽象类和组合，组合是组件类的具体实现。所有组合对象都派生自抽象组件类。任何组件都可以包含其他组件。包含其他组件的组件可以视为组合。没有子对象的组件可以视为空组合。

- 某些组合的实现会区分组合对象和叶子对象。叶子对象是不能包含子对象的组件。为简化此示例，所有组件都能充当组合。

从一般情况回过头来，有必要对设计进行修改，将 `Instrument` 接口改为抽象类。接口和抽象类相似之处在于，两者都不能直接用于实例化对象。关键区别在于，抽象类可以包含一些完全实现的方法，而接口只有方法声明。

当你希望在所有子类中保持相同的方法，但又有一些可以由子类共享的通用功能时，应使用抽象类。当子类中大多数或所有方法的实现会有所不同时，应使用接口。图 4-3 展示了新的类图。请注意，抽象类图以斜体表示。

![](img/a1b732997d9cb194dceec0570dc79710_90_0.png)

**图 4-3：新类图**

关联线表示，抽象乐器类的每个具体实例可以包含任意数量（包括零个）其他抽象乐器类实例。

## 实现

以下 PHP 代码展示了组合模式的实现：

```php
<html>
<body>
<head>
<style>
body { font: 12px verdana; font-weight: bold; }
td { font: 11px verdana; }
</style>
</head>

<?php

abstract class AbstractInstrument {

    private $name;
    private $category;
    private $instruments = array();

    public function add(AbstractInstrument $instrument) {
        array_push($this->instruments, $instrument);
    }

    public function remove(AbstractInstrument $instrument) {
        array_pop($this->instruments);
    }

    public function hasChildren() {
        return (bool)(count($this->instruments) > 0);
    }

    public function getChild($i) {
        return $this->instruments[$i];
    }

    public function getDescription() {
        echo "- one " . $this->getName();
        if ($this->hasChildren()) {
            echo " which includes<br>";
            foreach($this->instruments as $instrument) {
                echo "<table cellspacing=5 border=0><tr><td>&nbsp; &nbsp; &nbsp;
                </td><td>";
                $instrument->getDescription();
                echo "</td></tr></table>";
            }
        }
    }

    public function setName($name) {
        $this->name = $name;
    }

    public function getName() {
        return $this->name;
    }

    public function setCategory($category) {
        $this->category = $category;
    }

    public function getCategory() {
        return $this->category;
    }
}

class Guitar extends AbstractInstrument {
    function __construct($name) {
        parent::setName($name);
        parent::setCategory("guitars");
    }
}

class DrumSet extends AbstractInstrument {
    function __construct($name) {
        parent::setName($name);
        parent::setCategory("drums");
    }
}

class SnareDrum extends AbstractInstrument {
    function __construct($name) {
        parent::setName($name);
        parent::setCategory("snare drums");
    }
}

class BaseDrum extends AbstractInstrument {
    function __construct($name) {
        parent::setName($name);
        parent::setCategory("base drums");
    }
}

class Cymbal extends AbstractInstrument {
    function __construct($name) {
        parent::setName($name);
        parent::setCategory("cymbals");
    }
}

$drums = new DrumSet("tama maple set");
$drums->add(new SnareDrum("snare drum"));
$drums->add(new BaseDrum("large bass drum"));

$cymbals = new Cymbal("zildjian cymbal set");
$cymbals->add(new Cymbal("small crash"));
$cymbals->add(new Cymbal("large high hat"));
$drums->add($cymbals);

$guitar = new Guitar("gibson les paul");

echo "List of Instruments: <p>";
$drums->getDescription();
$guitar->getDescription();

?>

</body>
</html>
```

请注意，所有具体乐器（例如 DrumSet 和 Guitar）都派生自 AbstractInstrument 类。同时还要注意，所有子类都继承了抽象类中的已实现方法。要实现 getDescription() 方法，需要检查当前乐器是否有子对象。如果有，则递归调用该方法，直到遍历完整个树。图 4-4 显示了 composite.php 的输出。

![](img/a1b732997d9cb194dceec0570dc79710_93_0.png)

图 4-4：composite.php 的输出

此代码清单展示了多个类定义的组合、演示这些类用法的代码以及内联 HTML。这样做纯粹是为了避免本书过于冗长。
在你的代码中，希望为每个类建立单独的文件，并将业务逻辑与类定义分开。你将在第 13 章了解有关这种做法的设计模式。

历史上（在 PHP 4 中），& 符号会导致对象（在此示例中，类型为 AbstractInstrument）按引用传递：

```php
public function add(AbstractInstrument &$instrument) {
}
```

这一点很重要，否则函数内部将使用完全新的本地副本。
但是，由于 PHP 6 自动按引用传递对象，因此不需要 &。出于本次讨论的目的，这种行为是我们想要的，因为你确实想操作原始对象，而不是它的副本。图 4-5 显示了在组装好乐器及其子乐器后，先前代码的对象图。对象图与类图类似，不同之处在于它们显示带有下划线名称的对象实例。此外，它们表示系统在某一时刻的对象关系。

![](img/a1b732997d9cb194dceec0570dc79710_94_0.png)

图 4-5：对象图

在此示例中，具体乐器类之间并没有太大差异，只是在 Guitar 类中重写了 getDescription() 方法。不过，请考虑一下，如果你需要添加方法来联系制造商以获取库存信息会怎样。如果每个制造商都有偏好的系统联系方式，你可以在 contact() 方法中指定。你首先需要向 AbstractInstrument 添加一个抽象方法，然后在每个子类中实现它。添加抽象方法可确保你不会忘记在子类中实现它。如果不这样做，将会报错。

如果你确定不需要向乐器添加其他功能，可以直接创建一个继承自 AbstractInstrument 的 GenericInstrument 类。这样，当你创建（例如）一个镲片时，会使用如下代码：

```php
$cymbals = new GenericInstrument("zildjian cymbal set");

```

