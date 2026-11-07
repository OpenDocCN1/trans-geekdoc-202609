
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

And there you have it! A test for a specific method that uses mocks to properly isolate functionality that is required for the test to work.

I hope this blog post makes things a lot clearer when it comes to understanding the role of mocks when creating unit tests.

## 16 Advice From a Grumpy Programmer

I know there is a lot of stuff in this guide for you to consider. Writing tests is easy but creating a suite of tests that really helps protect you from regressions and other problems is hard.

The scope of knowledge required to do this is vast. This guide is really just scratching the surface of the topic of testing, automation, continuous integration and deployment. There are numerous ways for you to get there so don’t get discouraged that you have so many options.

Start slow and build out the pieces you really need first. The fancy stuff that companies like [IMVU](http://www.startuplessonslearned.com/2009/06/why-continuous-deployment.html) and [Etsy](http://codeascraft.etsy.com/) use didn’t get built overnight. It took years to get there, and they made lots of mistakes along the way to find the right set of tools and practices that worked for them.

Take the time and find the right set of tools for what you need. To reach the nerdvanna of continuous deployment, all you need is this:

*   a testing suite with enough coverage to catch regressions
*   ability to automatically run tests
*   ability to do automated deployments to a specified target

That’s really it. Your journey towards this starts with the decision to write one test using one set of tools, and it never really ends. You will find that when you make the commitment to a “test-first” mentality that your code ends up being more modular and simpler than before. That’s all you can really ask for.
