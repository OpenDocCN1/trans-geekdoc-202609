
```php
public function processSource(
    $wordSource, $minWordLength, $cacheDir)
{
    foreach ($wordSource as $html) {
        $hashKey = md5($html);
        $sourceFile = $cacheDir . '/' . $hashKey . '.'
            . self::SOURCE_SUFFIX;
        $this->sourceList[] = $sourceFile;
    }
}
```

### 4.
如果文件不存在，或者是零字节文件，我们处理其内容。如果源是 HTML，我们只接受 `<body>` 标签内部的内容。然后我们使用 `str_word_count()` 从字符串中提取单词列表，同时使用 `strip_tags()` 移除任何标记：

```php
if (!file_exists($sourceFile) || filesize($sourceFile) == 0) {
    echo 'Processing: ' . $html . PHP_EOL;
    $contents = file_get_contents($html);
    if (preg_match('/<body>(.*)<\/body>/i',
        $contents, $matches)) {
        $contents = $matches[1];
    }
    $list = str_word_count(strip_tags($contents), 1);
}
```

### 5.
然后我们删除任何过短的单词，并使用 `array_unique()` 去除重复项。最终结果存储在一个文件中：

```php
foreach ($list as $key => $value) {
    if (strlen($value) < $minWordLength) {
        $list[$key] = 'xxxxxxx';
    } else {
        $list[$key] = trim($value);
    }
}
       $list = array_unique($list);
        file_put_contents($sourceFile, implode("\n",$list));
        }
    }
    return TRUE;
}
```

### 6.
接下来，我们定义一个方法，该方法将单词中的随机字母转换为大写：

```php
public function flipUpper($word)
{
    $maxLen     = strlen($word);
    $numFlips = random_int(1, $maxLen - 1);
    $flipped = strtolower($word);
    for ($x = 0; $x < $numFlips; $x++) {
        $pos = random_int(0, $maxLen - 1);
        $word[$pos] = strtoupper($word[$pos]);
    }
    return $word;
}
```

### 7.
最后，我们准备定义一个从我们的源中选择单词的方法。我们随机选择一个单词源，并使用 `file()` 函数从相应的缓存文件中读取：

```php
public function word()
{
    $wsKey     = random_int(0, count($this->sourceList) - 1);
    $list     = file($this->sourceList[$wsKey]);
    $maxList = count($list) - 1;
    $key     = random_int(0, $maxList);
    $word = $list[$key];
    return $this->flipUpper($word);
}
```

### 8.
为了避免始终生成具有相同模式的密码，我们定义一个方法，该方法允许我们将密码的各个组件放置在最终密码字符串的不同位置。算法被定义为此类中可用的方法调用的数组。因此，例如，算法 `['word', 'digits', 'word', 'special']` 最终可能看起来像 hEiL0123aUTol：

```php
public function initAlgorithm()
{
    $this->algorithm = [
        ['word', 'digits', 'word', 'special'],
        ['digits', 'word', 'special', 'word'],
        ['word', 'word', 'special', 'digits'],
```

# 工作原理……

首先，你需要将前一个配方中描述的代码放入 `Application\Security` 文件夹中名为 `PassGen.php` 的文件中。现在你可以创建一个名为 `chap_12_password_generate.php` 的调用程序，该程序设置自动加载，使用 `PassGen`，并定义缓存目录的位置：

```php
<?php
define('CACHE_DIR', __DIR__ . '/cache');
require __DIR__ . '/../Application/Autoload/Loader.php';
Application\Autoload\Loader::init(__DIR__ . './../');
use Application\Security\PassGen;
```

接下来，你需要定义一个网站数组，该数组将作为密码生成中使用的词库的来源。在本例中，我们将选择 Project Gutenberg 文本 *Ulysses*（J. Joyce）、*War and Peace*（L. Tolstoy）和 *Pride and Prejudice*（J. Austen）：

```php
$source = [
    'https://www.gutenberg.org/files/4300/4300-0.txt',
    'https://www.gutenberg.org/files/2600/2600-h/2600-h.htm',
    'https://www.gutenberg.org/files/1342/1342-h/1342-h.htm',
];
```

接下来，我们创建 `PassGen` 实例，并运行 `generate()`：

```php
$passGen = new PassGen($source, 4, CACHE_DIR);
echo $passGen->generate();
```

以下是 `PassGen` 生成的一些示例密码：

![](img/39390f6d56c5a83b28db083a8bd5185c_482_0.png)

## 另请参阅

一篇关于攻击者如何破解密码的优秀文章可在 http://arstechnica.com/security/2013/05/how-crackers-make-minced-meat-out-of-your-passwords/ 查看。要了解有关暴力破解攻击的更多信息，你可以参考 https://www.owasp.org/index.php/Brute_force_attack。有关 oclHashcat 的信息，请参见此页面：http://hashcat.net/oclhashcat/。

## 使用验证码保护表单

**CAPTCHA** 实际上是 **Completely Automated Public Turing Test to Tell Computers and Humans Apart**（完全自动化公开图灵测试，用于区分计算机和人类）的缩写。该技术类似于前面配方中介绍的 *使用令牌保护表单*。不同之处在于，令牌不再存储在隐藏表单输入字段中，而是渲染成一种图形，使自动化攻击系统难以破解。此外，验证码的意图与表单令牌略有不同：它旨在确认网页访问者是人类，而不是自动化系统。

# 操作方法……

- 1. 验证码有几种方法：提出只有人类才知道的问题、文字技巧，以及需要解释的图形图像。
- 2. 图像方法向网页访问者展示包含严重扭曲字母和/或数字的图像。然而，这种方法可能很复杂，因为它依赖于 GD 扩展，而该扩展可能并非在所有服务器上都可用。GD 扩展可能难以编译，并且严重依赖宿主服务器上必须存在的各种库。
- 3. 文字方法是展示一系列字母和/或数字，并给网页访问者一个简单的指令，例如 *请反向输入此内容*。另一种变体是使用 ASCII“艺术”来形成人类网页访问者能够解释的字符。
- 4. 最后，你可以采用问答方法，问题如 *头部通过身体哪个部位连接到躯干*，答案如 *Arm*（手臂）、*Leg*（腿）和 *Neck*（脖子）。这种方法的缺点是自动化攻击系统有 1/3 的机会通过测试。

## 生成文本验证码

- 1. 为了说明这一点，我们将从文字方法开始，然后介绍图像方法。无论哪种情况，我们首先需要定义一个类来生成要展示给网页访问者（并由其解码）的短语。为此，我们定义了一个 `Application\Captcha\Phrase` 类。我们还定义了短语生成过程中使用的属性和类常量：

```php
namespace Application\Captcha;

class Phrase
{
    const DEFAULT_LENGTH    = 5;
    const DEFAULT_NUMBERS   = '0123456789';
    const DEFAULT_UPPER     = 'ABCDEFGHJKLMNOPQRSTUVWXYZ';
    const DEFAULT_LOWER     = 'abcdefghijklmnopqrstuvwxyz';
    const DEFAULT_SPECIAL   = '!"\'#$%&*()_+[]{}@\^~<,>.?/\';
    const DEFAULT_SUPPRESS  = ['0', 'l'];

    protected $phrase;
    protected $includeNumbers;
    protected $includeUpper;
    protected $includeLower;
    protected $includeSpecial;
    protected $otherChars;
    protected $suppressChars;
    protected $string;
    protected $length;
}
```

- 2. 构造函数，正如你所期望的，接受各种属性的值，并分配默认值，以便在不指定任何参数的情况下创建实例。`$include*` 标志用于指示哪些字符集将存在于从中生成短语的基础字符串中。例如，如果你希望只有数字，则 `$includeUpper` 和 `$includeLower` 都将设置为 FALSE。`$otherChars` 提供了额外的灵活性。最后，`$suppressChars` 表示一个将被从基础字符串中移除的字符数组。默认情况下移除大写 0 和小写 1：

```php
public function __construct(
        $length = NULL,
        $includeNumbers = TRUE,
        $includeUpper = TRUE,
        $includeLower = TRUE,
        $includeSpecial = FALSE,
        $otherChars = NULL,
        array $suppressChars = NULL)
    {
        $this->length = $length ?? self::DEFAULT_LENGTH;
        $this->includeNumbers = $includeNumbers;
        $this->includeUpper = $includeUpper;
        $this->includeLower = $includeLower;
        $this->includeSpecial = $includeSpecial;
        $this->otherChars = $otherChars;
        $this->suppressChars = $suppressChars
                ?? self::DEFAULT_SUPPRESS;
        $this->phrase = $this->generatePhrase();
    }
```

- 3. 然后我们定义了一系列 getter 和 setter，每个属性对应一个。请注意，为了节省空间，我们只展示了前两个。

```php
public function getString()
{
    return $this->string;
}

public function setString($string)
{
    $this->string = $string;
}

// other getters and setters not shown
```

- 4. 接下来我们需要定义一个方法来初始化基础字符串。它由一系列简单的 if 语句组成，这些语句检查各种 `$include*` 标志，并根据情况将相应内容附加到基础字符串中。最后，我们使用 `str_replace()` 来移除 `$suppressChars` 中表示的字符：

```php
public function initString()
{
    $string = '';
    if ($this->includeNumbers) {
        $string .= self::DEFAULT_NUMBERS;
    }
    if ($this->includeUpper) {
        $string .= self::DEFAULT_UPPER;
    }
    if ($this->includeLower) {
        $string .= self::DEFAULT_LOWER;
    }
    if ($this->includeSpecial) {
        $string .= self::DEFAULT_SPECIAL;
    }
    if ($this->otherChars) {
        $string .= $this->otherChars;
    }
    if ($this->suppressChars) {
        $string = str_replace(
            $this->suppressChars, '', $string);
    }
    return $string;
}
```

![](img/39390f6d56c5a83b28db083a8bd5185c_486_0.png)

## 最佳实践

去除那些可能与数字混淆的字母（即字母 **O** 可能与数字 **0** 混淆，小写字母 **l** 可能与数字 **1** 混淆）。

- 5. 我们现在准备定义核心方法，该方法生成验证码向网站访问者展示的随机短语。我们设置一个简单的 `for()` 循环，并使用新的 PHP 7 `random_int()` 函数在基础字符串中随机跳转：

```php
public function generatePhrase()
{
    $phrase = '';
    $this->string = $this->initString();
    $max = strlen($this->string) - 1;
    for ($x = 0; $x < $this->length; $x++) {
        $phrase .= substr(
            $this->string, random_int(0, $max), 1);
    }
    return $phrase;
}
```

- 6. 现在我们将注意力从短语转移到生成文本验证码的类上。为此，我们首先定义一个接口，以便将来我们可以创建额外使用 `Application\Captcha\Phrase` 的验证码类。注意 `getImage()` 将根据我们决定使用哪个类返回文本、文字艺术或实际图像：

```php
namespace Application\Captcha;

interface CaptchaInterface
{
    public function getLabel();
    public function getImage();
    public function getPhrase();
}
```

- 7. 对于文本验证码，我们定义了一个 `Application\Captcha\Reverse` 类。之所以这样命名，是因为该类产生的不仅是文本，而是反向文本。`__construct()` 方法构建一个 `Phrase` 实例。注意 `getImage()` 返回反向的短语：

```php
namespace Application\Captcha;

class Reverse implements CaptchaInterface
{
    const DEFAULT_LABEL = 'Type this in reverse';
    const DEFAULT_LENGTH = 6;
```

## 生成图像验证码

- 1. 正如你所能想象的那样，图像方法要复杂得多。短语生成过程是相同的。主要区别在于，我们不仅要将在短语印在图形上，还需要对每个字母进行不同的变形，并以随机点噪点形式引入干扰。
- 我们定义了一个实现 `CaptchaInterface` 的 `Application\Captcha\Image` 类。该类的常量和属性不仅包括短语生成所需的项，还包括图像生成所需的内容：
