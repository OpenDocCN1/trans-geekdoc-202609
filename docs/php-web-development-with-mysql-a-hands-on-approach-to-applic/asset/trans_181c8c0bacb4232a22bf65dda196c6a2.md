

## 26. PHP 中的面向对象编程简介

上述示例含义清晰，代码意图明确，不会让人产生歧义。它并不依赖那些无法强制执行的实例变量命名方案，而这些方案完全是为了应对“不必使用 this 关键字”的情况。在任何编程语言中，直接引用实例变量时，你都应该始终使用 this 关键字。谢天谢地，PHP 将其设为强制要求！

### 通用方法

除了 getter 和 setter 之外，你的类还可以包含用于执行各种任务的工具方法。例如，许多收音机都有扫描按钮，用于查找信号强的下一个频道。这些方法不必改变对象的状态（即修改属性），但它们可能会根据你的属性进行计算或执行某些操作，如代码清单 26.5 所示。

代码清单 26.5。

```php
class Radio
{
  public function scanChannels()
  {
    // find the next channel with a strong signal
  }

  public function getCurrentSong()
  {
    // reads live metadata from current channel about current song
    // being played and returns song title, etc...
  }
}
```

### 实例化并使用类

将类实例化为对象，并从该类创建多个实例，这展示了 OOP 的另一个强大概念。同理，你可以拥有多个字符串、整数等类型的变量；类则是一种更复杂的数据类型，也可以这样使用。

要使用我们的类，首先需要在 PHP 脚本中包含它：

```php
require_once('Radio.php');
```

要实例化或创建类的新实例，我们必须使用 new 关键字：

```php
require_once('Radio.php');

$car_radio = new Radio();
```

现在，$car_radio 引用了一个新实例，该实例是 Radio 类的对象。注意，类名 Radio 后面的 () 是默认构造函数（稍后会详细介绍）。如前所述，我们可以从单个 Radio 类创建多个实例：

```php
require_once('Radio.php');

$car_radio = new Radio();
$boat_radio = new Radio();
```

最好将类视为制作饼干之类的配方，而类的对象则是按照该配方制作出来的成品（例如一批巧克力曲奇饼干——好吃！）。接下来，我们可以使用我们的对象：

```php
$car_radio->setVolume(4);

echo 'My car radio\'s volume is set to: ' . $car_radio->getVolume() . '.';
```

再次注意，我们使用对象运算符（->）来引用 setVolume() 方法。我们可以引用任何具有公有可见性的属性或方法。OOP 是一个深奥的话题。请参阅 PHP 手册关于类和对象的说明[3]。

[3] 类与对象：https://php.net/language.oop5

### Radio.php（v1）完整代码清单

代码清单 26.6。

```php
<?php
class Radio
{
    private $powered;    // true or false
    private $volume;     // 0 - 10
    private $channel;    // 535kHz - 1700kHz, 87.5MHz - 108MHz

    // Getters
    public function getPowered()
    {
        return $this->powered;
    }

    public function getVolume()
    {
        return $this->volume;
    }

    public function getChannel()
    {
        return $this->channel;
    }

    // Setters
    public function setPowered($powered)
    {
        $this->powered = $powered;
    }

    public function setVolume($volume)
    {
        $this->volume = $volume;
    }

    public function setChannel($channel)
    {
        $this->channel = $channel;
    }
}
```

### UseRadio.php（v1）完整代码清单

代码清单 26.7。

```php
<?php
require_once('Radio.php');

$car_radio = new Radio();
$boat_radio = new Radio();

$car_radio->setPowered(true);
$car_radio->setVolume(4);
$car_radio->setChannel(88.6);

$boat_radio->setPowered(true);
$boat_radio->setVolume(7);
$boat_radio->setChannel(1640);

echo 'My car radio is ';
if ($car_radio->getPowered())
{
    echo 'turned on';
}
else
{
    echo 'turned off';
}

echo ' with the volume set to ' . $car_radio->getVolume() . ', ';
echo ' and the channel set to ' . $car_radio->getChannel() . '.<br /><br />';
echo 'My boat radio is ';

if ($boat_radio->getPowered())
{
    echo 'turned on';
}
else
{
    echo 'turned off';
}

echo ' with the volume set to ' . $boat_radio->getVolume() . ', ';
echo ' and the channel set to ' . $boat_radio->getChannel() . '.';
```

### 验证 Setter 方法的输入

通常，我们需要限制方法的输入。例如，在我们的 Radio 类中，音量设置会有上限和下限。许多家庭娱乐系统的音量设置都在 0 到 10 之间。让我们为 Radio 类添加一些类常量[4]：

```php
<?php
class Radio
{
    const MIN_VOLUME = 0;
    const MAX_VOLUME = 10;

    // ...
}
```

在我们的 setVolume() 方法中，我们可以通过 self:: 访问这些类常量。self 代表类自身，:: 被称为范围解析运算符[5]。在类内部引用常量时需要用到它。在引用外部变量时，你也会使用 ::，但此时要使用类名而不是 self。例如，我们可以更新 setVolume()，以确保用户无法将其设置为允许范围之外的值，如代码清单 26.8 所示。

[4] 类常量：https://php.net/language.oop5.constants
[5] 范围解析运算符：https://php.net/language.oop5.paamayim-nekudotayim

代码清单 26.8。

```php
<?php
class Radio
{
    const MIN_VOLUME = 0;
    const MAX_VOLUME = 10;
    // ...

    public function setVolume($volume)
    {
        if ($volume < self::MIN_VOLUME)
        {
            $volume = self::MIN_VOLUME;
        }
        else if ($volume > self::MAX_VOLUME)
        {
            $volume = self::MAX_VOLUME;
        }

        $this->volume = $volume;
    }

    // ...
}
```

### Radio.php（v2）完整代码清单

代码清单 26.9 是我们 Radio 类的完整代码清单，它会在设置频率时强制执行频率限制。

代码清单 26.9。

```php
<?php
class Radio
{
    const  MIN_VOLUME = 0;
    const  MAX_VOLUME = 10;

    const  MIN_AM_FREQ = 535;
    const  MAX_AM_FREQ = 1700;

    const  MIN_FM_FREQ = 87.5;
    const  MAX_FM_FREQ = 108;

    private $powered;    // true or false
    private $volume;     // 0 - 10
    private $channel;    // 535kHz - 1700kHz, 87.5MHz - 108MHz

    // Getters
    public function getPowered()
    {
        return $this->powered;
    }

    public function getVolume()
    {
        return $this->volume;
    }

    public function getChannel()
    {
        return $this->channel;
    }

    // Setters
    public function setPowered($powered)
    {
        $this->powered = $powered;
    }

    public function setVolume($volume)
    {
        if ($volume < self::MIN_VOLUME)
        {
            $volume = self::MIN_VOLUME;
        }
        else if ($volume > self::MAX_VOLUME)
        {
            $volume = self::MAX_VOLUME;
        }

        $this->volume = $volume;
    }

    public function setChannel($channel)
    {
        if ($channel < self::MIN_FM_FREQ)
        {
            $channel = self::MIN_FM_FREQ;
        }
        else if ($channel > self::MAX_FM_FREQ && $channel < self::MIN_AM_FREQ
                && $channel < (self::MIN_AM_FREQ - self::MAX_FM_FREQ))
        {
            $channel = self::MAX_FM_FREQ;
        }
        else if ($channel > self::MAX_FM_FREQ && $channel < self::MIN_AM_FREQ
                && $channel >= (self::MIN_AM_FREQ - self::MAX_FM_FREQ))
        {
            $channel = self::MIN_AM_FREQ;
        }
        else if ($channel > self::MAX_AM_FREQ)
        {
            $channel = self::MAX_AM_FREQ;
        }

        $this->channel = $channel;
    }
}
```

### UseRadio.php（v2）完整代码清单

代码清单 26.10。

```php
<?php
require_once('Radio.php');

$car_radio = new Radio();
$boat_radio = new Radio();

$car_radio->setPowered(true);
$car_radio->setVolume(4);
$car_radio->setChannel(88.6);

$boat_radio->setPowered(true);
$boat_radio->setVolume(11);
$boat_radio->setChannel(430);

echo 'My car radio is ';

if ($car_radio->getPowered())
{
    echo 'turned on';
}
else
{
    echo 'turned off';
}

echo ' with the volume set to ' . $car_radio->getVolume() . ', ';
echo ' and the channel set to ' . $car_radio->getChannel() . '.<br /><br />';
echo 'My boat radio is ';

if ($boat_radio->getPowered())
{
    echo 'turned on';
}
else
{
    echo 'turned off';
}

echo ' with the volume set to ' . $boat_radio->getVolume() . ', ';
echo ' and the channel set to ' . $boat_radio->getChannel() . '.';
```

