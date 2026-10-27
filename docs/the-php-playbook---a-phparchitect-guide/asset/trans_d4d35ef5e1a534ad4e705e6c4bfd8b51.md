
```php
return FALSE;
}
}
```

此代码示例包含许多可以改进之处。它是一个很好的例子，说明代码可能已进入生产环境，但应重构以更紧密地遵循标准、最佳实践和已被充分理解的原则。

坦白说，这段代码也存在许多问题：它缺乏连贯的编码标准，抽象不佳，无法测试，将测试和生产代码混在同一代码库中，未分离关注点，并且包含一些可疑的逻辑。要重构它，必须改进和更改多个方面。

## 开发编码标准

在我们的代码示例中，最先显而易见的就是它难以阅读。这由两个原因共同造成：首先，代码很复杂，事实上是不必要的复杂（我们将在后续章节中讨论），其次，代码没有遵循一致的标准。

编码标准是人们经常争论的话题。我一个朋友的轶事是，每当团队中的开发者不想工作一周时，他们就会挑剔编码标准中的某些细节，导致为期一周的争论，完全阻碍代码的生产。但编码标准不必如此尖锐。事实上，让我们在这里重新定义“编码标准”的含义。

在本节中，我们所说的“编码标准”是指代码遵循一致的标准——无论该标准具体是什么。这是一个重要的观点：开发者遵循 PEAR 规范还是 Zend Framework 风格并不重要。

为了本节的目的，重要的是实现三个要素：代码的一致性、添加注释以提高理解，以及在推进过程中防止引入错误。

我们将在此代码中添加一些注释（Docblocks），原因有两个：首先，它能提高我们对 API 的理解，至少可以记录参数和方法，其次，它迫使我们通读代码并理解其工作原理。

这是重构的一个重要方面。在重构之前，你必须知道自己在处理什么。最后，我们将检查并确保我们的编码约定不会无意中引入错误，通过确保诸如带括号的条件语句和循环、命名恰当的函数，以及变量被正确初始化等事项。

从示例顶部开始，我们看到开发者使用类似 PEAR 风格的方式，在“if”之后留一个空格，并在同一行放置左括号。他们使用四个空格进行缩进，我们也将使用这种缩进方式。

```php
// DO NOT RUN THIS SCRIPT STANDALONE (HAS PASSWORD)
if (count(get_included_files()) < 2) {
    header("HTTP/1.1 301 Moved Permanently"); header("Location: /"); exit;
}
```

然而，我们注意到在第 64 行，开发者使用了单行条件语句。这违反了我们似乎正在使用的编码标准，应该予以修正。此外，条件语句未使用括号，使得引入错误变得很容易。例如：

```php
if($var == true)
    echo "PARTY!";
```

在示例中，只有当 $var 变量等于 true 时，我们才会输出“PARTY！”这个词。然而，想象一下我们正在调试这个调用，并在 echo 命令前插入了一些内容：

```php
if($var == true)
    echo "I made it here!";
    echo "PARTY!";
```

糟糕！现在无论 $var 变量是否为 true，我们都会每次都开派对！这是因为 PHP 允许在未用括号包裹的条件语句后只跟随单行代码。循环也适用同样的规则。这意味着所有条件语句和循环都应始终用括号包围：

```php
if ($var == true) {
    echo "PARTY!";
}
```

在我们的代码示例中，我们需要在整个代码中做同样的处理。此问题出现在第 64、66、68、75、76、89、96 和 97 行。此外，第 79 行开始的条件语句存在不一致，括号位于新行。由于我们决定使用类似 PEAR 的标准，我们也需要修正这一点：

```php
// class_Twitter.php - NPC TWITTER AUTO-FEED
error_reporting(E_ALL);

// SEND AN AUTOMATED TWEET
// USAGE EXAMPLE
// require_once('class_Twitter.php');
// $status = 'Hello World';
// $t = new Twitter;
// $t->tweet($status);
// unset($t);

// DO NOT RUN THIS SCRIPT STANDALONE (HAS PASSWORD)
if (count(get_included_files()) < 2) {
    header("HTTP/1.1 301 Moved Permanently"); header("Location: /"); exit;
}

class Twitter {
    private $ch;
    private $you;
    private $user;
    private $pass;
    private $test;
    private $host;
    private $done; // ALREADY TWEETED?
    public  $res;

    public function __construct() {
        $this->user = "??? TWITTER USERNAME";
```

```php
    // POST A MESSAGE TO TWITTER
    public function tweet($message) {
        if(strlen($message) < 1) {
            return FALSE;
        }

        if ($this->already_tweeted($message)) {
            $this->done = TRUE;
        }

        // IF ONLY A TEST, JUST EMAIL THE INFORMATION - DO NOT TWEET
        if ($this->test) {
            $msg = '';
            if ($this->done) $msg .= "ALREADY DONE ";
            $msg .= "TWEET: $message";
            mail($this->you, 'What We Would Have Tweeted', $msg);
            return TRUE;
        }

        // DO NOT REPEAT YOURSELF
        if ($this->done) {
            return TRUE;
        }
        // STATUS UPDATE ON TWITTER
        $this->host .= "statuses/update.xml?status=".urlencode(stripslashes(
            urldecode($message)));
        curl_setopt($this->ch, CURLOPT_URL, $this->host);
        $xxx = curl_exec($this->ch);
        $this->res = curl_getinfo($this->ch);
        if ($this->res['http_code'] == 0) {
            return TRUE;
        }
        if ($this->res['http_code'] == 200) {
            return TRUE;
        }
        return FALSE;
    }
```

很好。现在我们已为应用程序增加了一些一致性，并移除了任何没有自动带括号的条件语句或循环。下一步是为代码添加注释，以便更好地理解其行为和功能。

关于注释是否有很大意义存在大量争论。我认为它们非常有帮助。如果没有编写注释，编写注释会迫使开发者理解他们正在处理的代码，这是理解并正确重构代码段的关键组成部分。我倾向于使用 Docblocks（本文即使用），它们与行内注释不同，而是记录每个方法，而不是记录代码运行时的情况。以下是经过 Docblocks 记录的相同代码：

```php
// class_Twitter.php - NPC TWITTER AUTO-FEED
error_reporting(E_ALL);

// DO NOT RUN THIS SCRIPT STANDALONE (HAS PASSWORD)
if (count(get_included_files()) < 2) {
  header("HTTP/1.1 301 Moved Permanently"); header("Location: /"); exit;
}

/**
 * Twitter Class
 * @author Anonymous
 *
 */
class Twitter {
    /**
     * @var resource Curl connection
     */
    private $ch;

    /**
     * @var string Email address for administrator/tester
     */
    private $you;

    /**
     * @var string The username for the Twitter account.
     */
    private $user;

    /**
     * @var string The password for the Twitter account.
     */
    private $pass;

    /**
     * @var bool The flag for test mode
     */
    private $test;

    /**
     * @var string The URL for the API call
     */
    private $host;

    /**
     * @var bool Flag for whether or not this tweet has been sent today
     */
    private $done;

    /**
     * Object constructor.
     */
    public function __construct() {
        $this->user = "??? TWITTER USERNAME";
        $this->pass = "??? TWITTER PASSWORD";
        $this->you = "??? YOUR EMAIL ADDRESS";

        $this->host = "http://twitter.com/";
        $this->done = FALSE; // DEFAULT - NOT ALREADY TWEETED
        $this->test = FALSE; // DEFAULT - THIS IS LIVE, NOT A TEST

        $this->ch  = curl_init();
        curl_setopt($this->ch, CURLOPT_VERBOSE, 1); curl_setopt($this->ch,
            CURLOPT_RETURNTRANSFER, 1); curl_setopt($this->ch, CURLOPT_USERPWD,
            "$this->user:$this->pass"); curl_setopt($this->ch,
            CURLOPT_HTTP_VERSION, CURL_HTTP_VERSION_1_1); curl_setopt($this->ch,
            CURLOPT_POST, 1);
    }

    /**
     * A destructor.
     * @return void
     */
    public function __destruct() {
        curl_close($this->ch);
    }

    /**
     * Method sets a flag as to whether the object is in test mode
     * @return void
     */
    public function test() {
        $this->test = TRUE;
    }
}
```
