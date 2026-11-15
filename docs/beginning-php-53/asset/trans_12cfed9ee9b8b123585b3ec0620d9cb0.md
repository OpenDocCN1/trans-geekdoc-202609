

```
return true;
}

public function brake() {
    if ( $this->_speed <= 0 ) return false;
    $this->_speed -= 10;
    return true;
}

public function getSpeed() {
    return $this->_speed;
}
}

class CarTest extends PHPUnit_Framework_TestCase
{
    public function testInitialSpeedIsZero()
    {
        $car = new Car();
        $this->assertEquals( 0, $car->getSpeed() );
    }

    public function testAccelerate()
    {
        $car = new Car();
        $car->accelerate();
        $this->assertEquals( 10, $car->getSpeed() );
    }

    public function testMaxSpeed()
    {
        $car = new Car();
        for ( $i=0; $i < 10; $i ++ ) {
            $car->accelerate();
        }

        $this->assertEquals( 100, $car->getSpeed() );
        $car->accelerate();
        $this->assertEquals( 100, $car->getSpeed() );
    }
}

$testSuite = new PHPUnit_Framework_TestSuite();
$testSuite->addTest( new CarTest( "testInitialSpeedIsZero" ) );
$testSuite->addTest( new CarTest( "testAccelerate" ) );
$testSuite->addTest( new CarTest( "testMaxSpeed" ) );

PHPUnit_TextUI_TestRunner::run( $testSuite );

?>
</pre>
</body>
</html>
```

在Web浏览器中运行此脚本。如果一切顺利，你应该会看到类似图20-3的页面，表示所有测试都已通过。

![](img/1ddec54918a4802eb9b4febec3d4e7f6_706_0.png)

图20-3

## 工作原理

脚本首先显示XHTML页面页头并包含两个PHPUnit库文件：

- PHPUnit/Framework.php 是PHPUnit的主要框架库。包含此文件会加载创建测试所需的所有类
- PHPUnit/TextUI/TestRunner.php 提供PHPUnit_TextUI_TestRunner类，用于运行测试套件中的测试并显示结果

脚本的主要部分包含三个部分：要测试的类（Car）、包含要运行的测试的测试用例类（CarTest）以及运行测试的过程代码。CarTest继承自PHPUnit_Framework_TestCase类，该类用于创建由PHPUnit运行的测试用例。

> 在实际情况中，你通常会将测试用例类与要测试的类放在不同的文件中。然后你的测试文件会使用include()来包含要测试的类文件。

这个简单的测试用例仅包含三个测试方法：

- testInitialSpeedIsZero() 确保新创建的Car对象报告的速度为零
- testAccelerate() 对静止的汽车进行加速，然后检查新速度是否为10英里每小时
- testMaxSpeed() 将汽车加速至最大速度（100英里每小时），然后检查无法再加速

每个方法都会创建一个新的Car类，执行适当的操作（例如加速汽车），并测试结果。测试是通过调用PHPUnit_Framework_TestCase::assertEquals()来完成的，该方法检查两个值是否匹配（如果不匹配，测试失败）。其他常用的断言方法包括：

| 断言方法 | 测试成功条件 ... |
|---|---|
| `assertNotEquals( $a, $b )` | `$a 和 $b 不相等` |
| `assertGreaterThan( $a, $b )` | `$b 大于 $a` |
| `assertGreaterThanOrEqual( $a, $b )` | `$b 大于或等于 $a` |
| `assertLessThan( $a, $b )` | `$b 小于 $a` |
| `assertLessThanOrEqual( $a, $b )` | `$b 小于或等于 $a` |
| `assertTrue( $x )` | `$x 计算结果为 true` |
| `assertFalse( $x )` | `$x 计算结果为 false` |
| `assertContains( $a, $b )` | `$a 是数组 $b 的一个元素` |

对于所有断言方法，你可以包含一条作为字符串的说明性消息（通常作为最后一个参数）。如果测试失败，将显示或记录此消息。在处理大型测试用例时，这有助于识别失败的测试。例如：

```
$this->assertEquals( 0, $car->getSpeed(), "Car's initial speed is not 0" );
```

定义Car和CarTest类后，脚本会创建一个新的测试套件（即一组测试），将这三个测试添加到套件中，并运行该套件：

```
$testSuite = new PHPUnit_Framework_TestSuite();
$testSuite->addTest( new CarTest( "testInitialSpeedIsZero" ) );
$testSuite->addTest( new CarTest( "testAccelerate" ) );
$testSuite->addTest( new CarTest( "testMaxSpeed" ) );

PHPUnit_TextUI_TestRunner::run( $testSuite );
```

此示例仅涉及了PHPUnit的表面内容。它是一个功能强大的框架，允许你进行诸如以下的高级操作：

- [ ] 创建专门用于测试数据库代码的自包含环境
- [ ] 使用模拟对象来测试应用程序中是否正确调用了方法
- [ ] 生成代码覆盖率报告，列出应用程序中未被测试的任何代码行

使用PHPUnit创建单元测试可能看起来工作量很大，但从长远来看可以节省时间。例如，编写测试用例后，每次开发新版本的代码时都可以针对应用程序运行该测试用例，以确保代码仍然按预期工作（这称为_回归测试_）。与往常一样，开始学习PHPUnit的好地方是文档，可在http://www.phpunit.de/wiki/Documentation上在线查阅。

## 总结

本章介绍了多种有助于你编写更好代码的技术。高质量的代码很重要，因为它对你（和其他人）来说更快速、更易于维护；它在处理问题和错误时更加健壮；并且能更好地防范不法用户的攻击。你探索了以下主题：

- **如何编写模块化代码**：这涉及将你的代码拆分为小的、易于维护的块，这些块通常可以被不同的应用程序重复使用。你简要回顾了函数和类，查看了PHP的`include()`、`require()`、`include_once()`和`require_once()`函数，这些函数允许你将应用程序拆分到不同的脚本文件中，并简要了解了使用命名空间以避免代码模块之间的函数、方法和常量名称冲突

- **如何创建和使用编码标准**：编码标准有助于你编写格式统一、易于阅读且更易于维护的代码。你查看了PHP和其他语言中使用的一些约定

- **创建代码文档**：你了解了为什么注释和代码文档是编写良好的应用程序不可或缺的一部分，并学习了如何编写好的注释以及使用phpDocumentor生成文档

- **应用程序安全**：这一重要且常被忽视的Web编程方面是任何健壮应用程序的关键部分。你学习了如何检查和过滤用户输入以确保其完整性，以及如何对应用程序的输出进行编码或转义，以确保其仅包含安全数据

- **错误处理**：为了让你的应用程序尽可能可靠地运行，它需要优雅地处理问题。你学习了如何使用PHP的错误处理和日志记录函数来处理错误，以及如何利用异常类的强大功能来创建灵活、健壮的错误处理代码

- **分离应用程序代码和表现层代码**：你学习了如何将表现层标记移动到单独的模板文件中，从而在应用程序的业务逻辑和其可视化界面之间建立清晰的划分。这样做使你的应用程序代码对设计师和程序员来说都更容易使用

- **单元测试**：你了解了代码测试（尤其是单元测试）的好处。尽早且经常地测试代码可以节省以后的许多麻烦。你简要了解了PHPUnit，这是一个测试框架，可让你轻松编写自己的自动化单元测试

读完本书所有章节后，你不仅知道如何编写PHP代码，还知道如何编写优质的PHP代码。创建高质量的代码需要时间、精力和纪律，但结果是健壮、易于维护和扩展的应用程序。任何处理你代码的人——包括你自己——都会感谢你！既然你了解编写高质量代码所涉及的概念，请尝试以下两个练习来测试你创建错误处理程序和使用PHPUnit的技能。你可以在附录A中找到这些练习的解答。

希望你觉得这本PHP 5.3入门指南既有用又有趣。祝你开发Web应用程序顺利，玩得开心！
