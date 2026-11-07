
```
<?php
class Test extends PHPUnit_Framework_TestCase
{
    public function testAlphaMunge()
    {
        $mockFoo = $this->getMockBuilder('Foo')
            ->disableOriginalConstructor()
            ->getMock();
        $mockFoo->expects($this->atLeastOnce())
            ->method('getDetails')
            ->will($this->returnValue('1->2'));
        $mockFoo->expects($this->atLeastOnce())
            ->method('getId')
            ->will($this->returnValue('1'));

        $mockBar = $this->getMockBuilder('Bar')
            ->disableOriginalConstructor()
            ->getMock();
        $mockBar->expects($this->atLeastOnce())
            ->method('getStartDate')
            ->will($this->returnValue('2012-03-27'));
        $mockBar->expects($this->atLeastOnce())
            ->method('getEndDate')
            ->will($this->returnValue('2012-04-09'));

        $source = "1|1->2|2012-03-27|2012-04-09";
        $expectedMunge = md5('rocksalt' . $source);
        
        $testAlpha = new Alpha();
        $munge = $testAlpha->getMunge($mockFoo, $mockBar);

        $this->assertEquals(
            $expectedMunge,
            $munge,
            'Munge value should match expected'
        );
    }
}
```

就是这样！这是一个针对特定方法的测试，它使用模拟对象来正确隔离测试工作所需的[content]
```
<?php
class Test extends PHPUnit_Framework_TestCase
{
    public function testAlphaMunge()
    {
        $mockFoo = $this->getMockBuilder('Foo')
            ->disableOriginalConstructor()
            ->getMock();
        $mockFoo->expects($this->atLeastOnce())
            ->method('getDetails')
            ->will($this->returnValue('1->2'));
        $mockFoo->expects($this->atLeastOnce())
            ->method('getId')
            ->will($this->returnValue('1'));

        $mockBar = $this->getMockBuilder('Bar')
            ->disableOriginalConstructor()
            ->getMock();
        $mockBar->expects($this->atLeastOnce())
            ->method('getStartDate')
            ->will($this->returnValue('2012-03-27'));
        $mockBar->expects($this->atLeastOnce())
            ->method('getEndDate')
            ->will($this->returnValue('2012-04-09'));

        $source = "1|1->2|2012-03-27|2012-04-09";
        $expectedMunge = md5('rocksalt' . $source);
        
        $testAlpha = new Alpha();
        $munge = $testAlpha->getMunge($mockFoo, $mockBar);

        $this->assertEquals(
            $expectedMunge,
            $munge,
            'Munge value should match expected'
        );
    }
}
```

就是这样！这是一个针对特定方法的测试，它使用模拟对象来正确隔离测试工作所需的[content]
```
<?php
class Test extends PHPUnit_Framework_TestCase
{
    public function testAlphaMunge()
    {
        $mockFoo = $this->getMockBuilder('Foo')
            ->disableOriginalConstructor()
            ->getMock();
        $mockFoo->expects($this->atLeastOnce())
            ->method('getDetails')
            ->will($this->returnValue('1->2'));
        $mockFoo->expects($this->atLeastOnce())
            ->method('getId')
            ->will($this->returnValue('1'));

        $mockBar = $this->getMockBuilder('Bar')
            ->disableOriginalConstructor()
            ->getMock();
        $mockBar->expects($this->atLeastOnce())
            ->method('getStartDate')
            ->will($this->returnValue('2012-03-27'));
        $mockBar->expects($this->atLeastOnce())
            ->method('getEndDate')
            ->will($this->returnValue('2012-04-09'));

        $source = "1|1->2|2012-03-27|2012-04-09";
        $expectedMunge = md5('rocksalt' . $source);
        
        $testAlpha = new Alpha();
        $munge = $testAlpha->getMunge($mockFoo, $mockBar);

        $this->assertEquals(
            $expectedMunge,
            $munge,
            'Munge value should match expected'
        );
    }
}
```

就是这样！这是一个针对特定方法的测试，它使用模拟对象来正确隔离测试工作所需的
功能。

我希望这篇博文能让大家在理解创建单元测试时模拟对象的角色时变得清晰很多。

## 来自一位暴躁程序员的16条建议

我知道本指南中有很多内容需要你考虑。编写测试很容易，但创建一套真正有助于防止回归和其他问题的测试套件却很困难。

做到这一点所需的知识范围非常广。本指南只是触及了测试、自动化、持续集成和部署主题的表面。有很多种方法可以达到目标，所以不要因为选择太多而气馁。

慢慢开始，先构建你真正需要的部分。像 [IMVU](http://www.startuplessonslearned.com/2009/06/why-continuous-deployment.html) 和 [Etsy](http://codeascraft.etsy.com/) 这样的公司使用的花哨的东西不是一夜之间建成的。花了几年时间才达到那一步，而且他们在寻找适合自己的工具和实践组合的过程中犯了很多错误。

花时间找到适合你需求的正确工具组合。要达到持续部署的极乐境界，你只需要以下几点：

*   一个覆盖率足够捕获回归的测试套件
*   能够自动运行测试的能力
*   能够自动部署到指定目标的能力

就是这样。你的旅程始于使用一套工具编写一个测试的决定，并且永远不会真正结束。你会发现，当你坚持“测试先行”的理念时，你的代码会比以前更模块化、更简单。这就是你能真正要求的全部了。
