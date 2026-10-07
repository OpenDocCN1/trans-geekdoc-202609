

而且要偏于组合（Composition）。

只需要确保它获取适当的状态实例即可。对于一个繁忙的应用来说，这是一个巨大的优势。

在编写本文时，我们正处于一个令人兴奋的时刻，有几个项目正尝试攻克状态化的 PHP 应用。与普通 PHP 脚本的 `boot->shutdown` 生命周期不同，在生产能够维持多个请求上下文和状态的 PHP 应用程序服务器方面取得了巨大进展。我们需要关注如 Appserver.io* 和 ReactPHP* 之类的项目，因为它们很可能消除我们目前所知的对缓存的需求。

> http://appserver.io
http://reactphp.org/

## 策略模式（Strategy Pattern）

与状态模式（State Pattern）密切相关的是策略模式。在某些情况下，它们的关系如此紧以难以区分。想象一下 Lizzie 有一个双胞胎姐姐 Lottie。她们长得一模一样，衣服也一模一样。区分它们的唯一方法是她们吃冰淇淋的时候，因为 Lizzie 会是那个激烈守护开心果味、巧克力和薄荷口味的人；而另一方面，Lottie 则相当偏爱 Ben & Jerry's "Pish Food"。

噢，抱歉。

幸运的是，状态模式和策略模式并没有那么难以区分。同样地，到此为止，我们将注入一些封装的行为，该行为将代表一种在外部（通常是外部数据）上运行的自定义算法。

这是状态模式和策略模式区别的关键部分。状态模式根据实现者内部状态的某些概念提供了可交换的行为，而策略模式则根据我们希望这些行为如何处理事物的概念提供了可交换的行为。

*

而且要偏于组合。

显然，我们在这里讨论的是执行者（doers），在这种情况下我们需要一个接口。一个能够保证方法或多个方法存在的接口，这些方法将是我们接入目标行为的钩子（hooks）。

这相当方便，因为策略模式的非正式定义如下：定义一组相关的算法，将每一个算法封装为自己的对象，并用通用接口将它们统一起来，确保它们是可交换的。

从上面这段话中产生了一个有趣的点。定义由通用接口统一的一组相关对象，听起来它们似乎可能是抽象类和一组相关子类的类的候选者。

在某些情况下，这确实是合适的，但仅当你可以确定每个封装的策略将管理其自身的对象状态时才如此。

对于大多数用例来说，每个策略将操作的状态将存在于策略被注入的消费者对象内部，或者存在于与策略及其消费者完全分离的数据或对象上。

在我们深陷理论之前，让我们启动一个例子让旅程变得顺畅一点。

```php
<?php
class ReportData
{
    private $data;

    public function getOutput($format = 'csv')
    {
        switch ($format) {
            case 'csv':
                $lines = [];
                foreach ($this->data as $row) {
                    $lines[] = '' . implode(',', $row) . '';
                }
                return implode("\n", $lines);
                break;
            case 'array':
                return $this->data;
```

而且要偏于组合。

235

```php
break;
}
}
```

这里没什么特别的——一个定义对象的类，该对象似乎持有着报告数据。显然，这个对象是从传递到模型层的请求中被发出的，一次又一次，我们似乎有一个条件结构来决定报告数据的检索格式。

无论这个条件结构是我们在之前在状态模式中看到的 if/else 子句堆，还是像这里的 switch 语句，并不重要。如果我们发现自己在根据条件语句选择要运行的代码块，我们几乎肯定会从将这些代码块抽象为代表可注入行为的独立对象中获益。

尽管如此，我们这里的示例说明了报告数据如何作为（构建得糟糕的）CSV 字符串或原始数据数组返回。尽管业务团队一直在催促我们提供 HTML 表格、PDF 和用于 API 的 JSON 字符串。

我们要向 switch 语句中再添加三个情况吗？不，我们当然不这样做。

我们也不会创建一个由抽象父类链接起来的 `ReportData` 类族，这正是是因为我们在上一节的订单（Order）示例中看到的原因。如果这个对象代表报告数据，那么可以假设生成结果至少花费了成本。因此，通过缓存这些数据可能会节省大量的资源，即使是短时间内。

为什么呢？

业务团队要求数据能够以 HTML 表格以及 PDF/CSV 的形式可用。无论他们的大脑有时运行得有多么奇异，我们至少可以假设他们的愿望包括在浏览器中显示这些数据，并提供指向下载文件的链接。

这些输出格式要求是表示为可注入行为的完美候选者，每种所需的输出格式都由一个单一的、封装良好的算法表示，用于相应地转换报告数据。

而且要偏于组合。

考虑到这一点，让我们先看看我们可能如何修改 `ReportData` 类。

```php
class ReportData
{
    private $data;
    private $formatter;

    public function setFormatter(ReportFormatStrategy $formatter)
    {
        $this->formatter = $formatter;
    }
    public function getOutput()
    {
        if (isset($this->formatter)) {
            return $this->formatter->formatData($this->data);
        }
        return $this->data;
    }
}
```

我们在这里做了什么？首先，我们极大地简化了 `getOutput()` 方法，只有两个选择可以适应对数据的每可能的请求——要么是对原始数据数组的请求，要么是在返回之前对该数组进行格式化的请求。

第二点是，我们的 `ReportData` 对象现在接受一个用于 `setFormatter()` 方法的格式器。具体来说，该方法类型提示了一个佩有 `ReportStrategy` 接口的对象。

> 在为策略模式实现提供接口时，通常在接口名称后面加上“Strategy”一词非常有用。这使得接口的意图变得完全清晰。

结果，我们现在有了一个 `ReportData` 类，它会简洁得多，但能够以团队现在和未来可以想象的任何格式输出其数据，而不需要要求我们进一步修改 `ReportData` 类。

而且要偏于组合。

我们需要快速看一眼剩余的代码来看看它是如何实现的。首先，统一接口看起来像这样：

```php
<?php
interface ReportFormatStrategy {
    public function formatData(array $data);
}
```

嗯，这不能更简单了。具体的策略又是怎样的？

```php
<?php
class JsonFormatStrategy implements ReportFormatStrategy {
    public function formatData(array $data) {
        return json_encode($data);
    }
}
```

使用 JSON 总是总是简单得多。其他格式呢？

```php
<?php
class CsvFormatStrategy implements ReportFormatStrategy {
    public function formatData(array $data) {
        $csv = fopen('php://temp', 'r+');
        $filesize = 0;
        foreach ($data as $row) {
            $filesize += fputcsv($csv, $row);
        }
        fseek($csv, 0);
        $csvData = fread($csv, $filesize);
        fclose($csv);
        return $csvData;
    }
}
```

