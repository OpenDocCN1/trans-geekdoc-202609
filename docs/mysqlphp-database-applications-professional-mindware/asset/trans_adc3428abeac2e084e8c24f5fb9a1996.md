
```
, date_format(p.entry_dt, '%Y-%c-%e %l:%i %p') as entry_dt
    , p.source_id, p.summary, p.entered_by
    , s.status
    , so.source
    , p.entry_dt as real_entry_dt
    from customers c, problems p, status s, sources so
    where p.status_id = s.status_id and s.status = 'Opened'
        and p.customer_id = c.customer_id
        and p.source_id = so.source_id
    order by real_entry_dt desc
";
display_call_list($query, "Unowned Calls");
```

上面的查询检索标记为“Opened”的呼叫列表。请注意，“Opened”仅对未分配的呼叫才是状态。一旦有人执行操作，状态就会改变。display_call_list() 函数会打印查询结果（如果有的话）。

如果你还记得《定义数据库》部分，我们不得不使用一些技巧来获取属于特定用户的呼叫的最新条目列表。我们需要创建我们谈到的那个临时表，但在这样做之前，我们需要清除其中可能存在的旧数据。

```
safe_query("delete from calls where username = '$PHP_AUTH_USER'");
```

然后我们用连接所需的数据填充临时表。

```
safe_query("insert into calls (username, problem_id, entry_dt)
    select p.owner
        , h.problem_id
        , max(h.entry_dt) as entry_dt
    from problems p, history h
    where p.problem_id = h.problem_id
        and p.owner = '$PHP_AUTH_USER'
    group by p.problem_id
");
```

最后，我们在新加载的表上执行以下操作。

```
$query = "select c.customer_id, c.firstname, c.lastname
    , p.problem_id, p.source_id, p.entered_by
    , date_format(h.entry_dt, '%Y-%c-%e %l:%i %p') as entry_dt
    , h.notes as summary
    , s.status
    , so.source
    , h.entry_dt as real_entry_dt
from customers c, problems p, status s, sources so
, history h, calls m
where p.status_id = s.status_id and s.status != 'Closed'
    and p.customer_id = c.customer_id
    and p.source_id = so.source_id
    and p.problem_id = h.problem_id
    and p.owner = m.username
    and h.entry_dt = m.entry_dt
    and h.problem_id = m.problem_id
    and m.username = '$PHP_AUTH_USER'
order by real_entry_dt desc
";
display_call_list($query, "Open Calls");

// print out a link to allow the user to create a new call
print paragraph(anchor_tag("call_entry.php?use_staff_name=yes","Call Entry"));

include "end_page.php";

### EDIT_PROBLEM.PHP

这是该应用程序中的最后一个文件。它相当简短，CD-ROM 上的源代码应该可以阅读。

### 摘要

本章介绍的应用程序非常有用，因为几乎每个公司的信息服务部门都会有某种系统来跟踪用户投诉。正如我们在本章开头所说，这里介绍的问题跟踪系统相当通用。然而，它绝对可以作为你在工作场所定制的更详细应用程序的基础。

## 第14章

### 购物车

### 本章内容

- 创建一个安全站点
- 使用 PHP 会话
- 与信用卡授权服务通信

好吧，朋友们。这就是本书中的最后一个应用程序。我不知道你怎么样，但我有点想哭。确实有艰难的时光。但总的来说，我对我们取得的成就感到很棒，我希望你也是。

但在我们开始回忆之前，还有一些工作要做。你将学习使用 PHP 和 MySQL 创建购物车应用程序所需的知识。但与本书中的其他应用程序不同，如果不深入探讨其他主题，几乎不可能谈论这个应用程序所需的知识。除了理解模式和 PHP 代码之外，你还需要基本了解如何在页面之间维护状态。（如果你不知道这意味着什么，不用担心，我稍后会讲到。）此外，你还需要知道如何安全地处理信用卡交易。

![](img/de0823012275cf4ceebdb822a56e6b71_389_0.png)

> 如果你还没有读完第10章，就不要再读下一句话了。在着手之前，你必须了解目录的工作原理。出于不难理解的原因，我们在目录之上构建了购物车。

### 确定应用程序的范围和目标

任何熟悉网络的人都知道购物车的作用。但如果我明确说明购物车的一些目标，就更容易理解该应用程序的代码在做什么。

首先，应用程序必须展示你的商品；为此你将重用第10章的代码。此外，用户必须能够选择他们想要购买的商品。显而易见，我知道。请注意用户选择商品后必须发生的事情：必须记录确切的商品，并且用户应有继续购物的机会。服务器必须记住已订购的内容。随着用户继续浏览，服务器必须跟踪用户并允许他/她使用所请求的商品结账。

这要求你使用某种方法来维护状态。也就是说，Web 服务器需要在用户从一个页面移动到另一个页面时记住用户是谁。现在，如果你还记得《导言》，Web 以及 Web 使用的 HTTP 协议是无状态的。也就是说，在响应 HTTP 请求后，服务器完全彻底地忘记了它向谁提供了什么服务。服务器按顺序处理请求的信息——请求到来时一次处理一个。没有持久性，没有在页面提供后持续的连接。

为了让你的网站具有记忆功能，以便在这种情况下购物车能够记住谁订购了什么，必须在每次页面请求中发送一些可以识别用户的信息。在 Web 上，存储此信息恰好有三种方法：

- 你可以设置一个 cookie，然后每次发出请求时，存储在 cookie 中的信息都会发送到服务器。请注意，浏览器将 cookie 信息存储在小型文本文件中，并在每次请求时将信息发送到服务器。

![](img/de0823012275cf4ceebdb822a56e6b71_390_0.png)

setcookie() 函数在第6章中介绍。

- 你可以在每个页面上放置隐藏的表单元素，然后设计页面，使导航通过表单提交按钮完成。
- 或者你可以将某种唯一标识符附加到查询字符串上，这样每次页面请求时 URL 都会识别用户。

但是，正如他们在 PHP 的其他一切中所做的那样，开发人员使维护状态相对轻松。与 ColdFusion 和 ASP 一样，他们包含了会话功能。（只有 PHP 中的会话好得多。）如果你不熟悉这个术语，会话会自动跟踪用户在访问期间的过程。它们将在本章后面更详细地讨论。

该应用程序的另一个主要挑战是安全地从用户那里收集用户信息——具体来说是允许信用卡授权的数据。信息需要在相对安全的连接上收集，然后这些信息需要由合格的机构验证。这将需要一些新的配置和一些自定义工具的使用。

### 你需要什么？

由于你是在目录之上构建此应用程序，大部分代码和信息应该非常熟悉。唯一值得注意的是，将在每个页面上添加一个按钮，让人们直接进入结账。图14-1显示了一个示例。

![](img/de0823012275cf4ceebdb822a56e6b71_391_0.png)

图14-1：带结账按钮的分类页面

在列出商品的页面上，必须有一组表单，让人们能够指出他们想要购买的商品。图14-2显示了一个页面，允许人们通过按下“Order!”按钮将商品添加到购物车中。

然后必须有一个页面列出购物车中当前的所有商品。该页面应允许人们增加或减少商品的数量，或完全删除商品。图14-3中的页面应该可以解决问题。
