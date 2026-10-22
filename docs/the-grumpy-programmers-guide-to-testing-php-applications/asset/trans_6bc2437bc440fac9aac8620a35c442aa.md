
- L -> 50
- C -> 100

有些数字以不同的方式表示，因此我们还需要考虑这些情况：

- IV -> 4
- IX -> 9

那么，让我们创建一个空测试来验证：当我们传入 1 时，返回的是 I。

```
<?php
declare(strict_types=1);

class NumeralConverterTest extends PHPUnit\Framework\TestCase
{
    /**
     * @test
     */
    public function converts1ToRomanNumeral(): void
    {
        $this->assertTrue(false);
    }
}
```

这是能够在 PHP 或 PHPUnit 不抱怨配置错误的情况下运行的最简测试类。

我喜欢在测试方法的文档块中使用 @test 注解，而不是在每个测试方法前都加上 test 前缀。这样我可以使用更接近英文描述的方式命名测试方法。

如果我运行这个测试，它会失败：

```
Failed asserting that false is true.
/Users/chartjes/grumpy-guide/test/NumeralConverterTest.php:11

Time: 188 ms, Memory: 12.00 MB
```

## 6. 测试驱动开发示例

### 第一个测试

第一个测试总是最难的，因为我们要为之后的所有代码搭建舞台。我确实会花一些时间进行原型设计或思考我想让接口和参数长什么样。在这个例子中，我从一开始就很清楚我希望它们是什么样。我会编写第一个测试用例：

```
public function converts1ToRomanNumeral() : void
{
    // Arrange
    $nc = new NumeralConverter();
    $input = 1;
    $output = 'I';

    // Act
    $result = $nc->arabicToRoman($input);

    // Assert
    $this->assertEquals($output, $result);
}
```

在深入细节之前，我想谈谈一个多年前有人教给我的测试设计模式，我经常使用它来保持测试用例的组织性。它被称为 Arrange-Act-Assert 模式。

### 安排

这个部分是我创建测试场景所需依赖的地方。在这个例子中，我创建了一个 NumeralConverter 对象，以及传给方法的输入和期望输出。在更高级的测试用例中，我需要创建的测试替身也放在安排部分。在大多数测试用例中，安排步骤包含的代码最多。

### 操作

这是我们使用被测代码生成输出，然后验证输出是否符合预期的地方。在我们的例子中，我们执行 arabicToRoman() 方法，传入所选输入并将输出存储在一个变量中。

这部分代码可能很多，也可能只有一行，就像我们的例子一样。它完全取决于测试场景。需要注意的一点是，确保该部分的操作与使用被测代码的应用代码一致。你在测试中对代码的使用方式偏离它在生产环境中的使用方式越远，你就越可能得到测试通过但应用程序并不按预期工作的结果。

### 断言

测试的最后一部分是我们进行所有断言或其他验证语句的地方，用来确认代码的行为符合我们的预期。有些人遵循“每个测试一个断言”的规则，而另一些人遵循“需要多少断言就用多少断言”的做法。没有正确答案，但一个没有某种断言的测试用例实际上没有测试任何东西。在我们的例子中，我们验证预期输出与 arabicToRoman() 方法返回的结果一致。

回到我们的示例；测试失败是因为我还没有创建 NumeralConverter 对象。

```
Error : Class 'NumeralConverter' not found
    /Users/chartjes/grumpy-guide/test/NumeralConverterTest.php:11
```

让我为这个对象创建一个空壳。

```
<?php
declare(strict_types=1);

class NumeralConverter
{
}
```

然后，我更新测试，添加一行加载这个对象的代码：

```
require __DIR__ . '/../src/NumeralConverter.php';
```

最后，我再次运行测试，它失败了，因为我要测试的方法还不存在。

```
Error : Call to undefined method NumeralConverter::arabicToRoman()
    /Users/chartjes/grumpy-guide/test/NumeralConverterTest.php:16
```

是的，这正是我进行测试工作的方式。我缓慢而稳定地推进，确保不遗漏任何东西。我们都有自己的习惯和喜欢使用的编程技巧；刻意而为能最大限度地降低我跳过步骤或犯下很容易避免的错误的风险。

现在，我编写刚好足够的代码来满足我们测试的行为。

## 6. 测试驱动开发示例

```
1. public function arabicToRoman($value) : string
2. {
3.     $result = '';
4.
5.     if ($value === 1) {
6.         $result .= 'I';
7.     }
8.
9.     return $result;
10. }
```

测试通过了。

OK (1 test, 1 assertion)

### 下一个测试

当然，我的解决方案非常简单，并且做了一些显然会改变的假设。我没有从一开始就尝试构建最优解决方案，而是决定想清楚我想要做什么。对于下一个测试，验证我们正确处理 2 和 3 的转换（我决定把它们放在一组），我将引入数据提供器（data provider）的概念。

数据提供器是一个向测试方法传入数据集的方法。在实现上，它是一个返回数组的数组的方法。我首先创建数据提供器方法。命名约定并不重要——尽量起一个描述性强、能让以后阅读测试代码的人理解其含义的名字。

```
public function dataSetsForConversion() : array
{
    return [
        [2, 'II'],
        [3, 'III']
    ];
}
```

然后，我创建一个使用该数据提供器的失败测试方法。

```
/**
 * @dataProvider dataSetsForConversion
 * @test
 */
public function converts2and3ToRomanNumeral($input, $expected)
{
    $this->assertTrue(false);
}
```

要告诉 PHPUnit 某个测试用例使用哪个数据提供器，你需要为测试方法提供一个 DocBlock（如果你还没有使用的话），然后在其中添加 @dataProvider 注解。注意大小写！然后，你的测试方法需要接受与传入数据值数量相同的参数。

对于这个测试，我决定提供我要测试的输入以及期望的结果。

现在我来验证测试会失败。

```
Failed asserting that false is true.
/Users/chartjes/grumpy-guide/test/NumeralConverterTest.php:34

Failed asserting that false is true.
/Users/chartjes/grumpy-guide/test/NumeralConverterTest.php:34
```

不，我没有重复复制粘贴结果。使用这个数据提供器的测试方法会对每一组数据执行一次。

第一步完成后，我开始编写代码，让第二个测试用例通过。

```
```php
public function arabicToRoman($value) : string
{
    $currentValue = $value;
    $result = '';

    while ($currentValue > 0) {
        if ($currentValue % 1 === 0) {
            $result .= 'I';
            $currentValue--;
        }
    }

    return $result;
}
```
```

测试通过了。

### 构建更多测试用例

我为验证 2 和 3 能正确转换而写的实现让我觉得应该继续以类似方式扩展代码来处理其他情况。我会添加一个测试用例来验证 4、5 和 9 被正确处理。这些情况代表了非标准行为。

首先，失败的测试。

```
```php
/**
 * @dataProvider exceptionDataSets
 * @test
 */
public function convertsSingleDigitExceptions($input, $expected)
{
    $this->assertTrue(false);
}
```
```

它如预期那样失败了。

```
Failed asserting that false is true.
/Users/chartjes/grumpy-guide/test/NumeralConverterTest.php:53

Failed asserting that false is true.
/Users/chartjes/grumpy-guide/test/NumeralConverterTest.php:53

Failed asserting that false is true.
/Users/chartjes/grumpy-guide/test/NumeralConverterTest.php:53
```

这里有三个失败，因为我使用了三组数据。

然后，我修改代码以正确处理这种新行为。

```
```php
1. public function arabicToRoman($value) : string
2. {
3.     $currentValue = $value;
4.     $result = '';
5. 
6.     while ($currentValue > 0) {
7.         switch ($currentValue) {
8.             case $currentValue % 9 === 0:
9.                 $result .= 'IX';
10.                $currentValue -= 9;
11.                break;
```

