

```php
} catch(\Exception $e) {
    print json_encode({
        'success' => false,
        'error' => $e->getMessage()
    });
}
```

我们通过调用 `session_start()` 和 `ob_start()` 函数启用会话和输出缓冲，以此启动聊天服务器。然后，我们设置一个值为 `application/json` 的 `Content-Type` 响应头，以确保请求客户端知道我们将返回一个 JSON文档作为响应。为了确保超时时间对齐，我们使用 `date_default_timezone()` 来匹配我们服务器的时区。

在完成基础工作后，我们随后打开与 MySQL 的数据库连接并检查连接是否正常——如果连接失败，我们将立即退出，因为在这一阶段缺少数据库意味着聊天将非常无聊，没有任何消息可以显示给任何用户。

然而，一旦数据库连接准备就绪，我们就可以准确判断脚本应该如何响应当前的请求。在我们的案例中，我们将根据从用户界面收到的请求性质来定义所采取的操作。对于 HTTP GET 请求，我们将获取用户可见的消息列表并将其返回到屏幕上。对于 HTTP POST 请求（表单提交），我们将接受一条新消息并广播给所有其他用户。

无论请求的性质如何，此脚本始终返回一个 JSON 对象，其中包含一个名为 `success` 的键，根据操作的成功与返回 `true` 或 `false`。如果失败，我们还会提供一个带有错误信息的 `error` 键。如果我们正在处理 HTTP GET 请求，我们额外返回一个包含客户端应该渲染的消息列表的 `messages`。

列表 23.2 是一个简单的 PHP 脚本，它利用了你在整个过程中见过的几个概念来从数据库中插入或检索信息。然而，该脚本的关键在于它的执行方式。其意图是让用户的浏览器通过 AJAX 定期执行此脚本，以使用收到的任何消息来更新界面。目前，浏览器界面还将提供使用 AJAX 向服务器发送消息的能力，以便广播给其他正在查看聊天的人。现在，让我们通过查看应用程序的客户端以及我们将将使用的 AJAX 方法来继续后续。

## jQuery AJAX 方法

在为我们的应用程序构建简单的用户界面之前，让我们回到关于 jQuery 的讨论，介绍用于执行 AJAX 请求的各种可用方法。从根本上说，你将在接几节中学习到的 AJAX 方法都是单一 API 方法——`$.ajax()` 方法的简化版本。

## jQuery $.ajax() 方法

从原型的角度来看，$.ajax() 方法相当简单：

```javascript
$.ajax(string url, object settings);
```

该方法的第一个参数是你想执行异步请求的 URL，第二个参数包含了针对该请求的任何设置。除非你想检查用于控制基本上该请求及其响应的几乎每个细节的众多可用设置，否则该方法的复杂性并体现出来。由于所有这些不同的设置在 jQuery 关于该方法的文档中都有详尽的记录，我们在这里不会讨论其中的每一种——请随时使用 /api.jquery.com/jquery/ajax/ 或在日后的某个日期查看。相反，我们将介绍几个案例以及如何使用 $.ajax() 方法实现它们。

第一个示例执行一个 HTTP GET 请求。`success` 属性是一个在请求成功时调用的函数，它将用在请求期间获取的数据、请求的文本状态以及 jQuery 请求本身进行填充。

```javascript
// 执行一个 HTTP GET 请求
$.ajax('/example.php', {
  'method': 'GET',
  'success': function(data, textStatus, jqXHR) {
    console.log(data);
  }
});
```

下一个示例执行一个 HTTP POST 请求，并向服务器发送一些数据。成功后，正如我们之前的 GET 请求一样，绑定到 `success` 属性的函数会被调用。然而，在这种情况下，我们还有一个绑定到 `error` 属性的函数。该函数在发生错误（例如服务器返回 HTTP 500 状态）时被调用，其结果可以告知用户界面：

```javascript
// 执行带有错误处理的 HTTP POST 请求
$.ajax('/example.php', {
  'method': 'POST',
  'data': {
    'myBoolean': true,
    'myString': 'This is some sample data.'
  },
  'success': function(data, textStatus, jqXHR) {
    console.log(data);
  },
  'error': function(jqXHR, textStatus, errorThrown) {
    console.log("An error occurred: " + errorThrown);
  }
});
```

如果你想为 HTTP 请求添加头部（例如添加身份验证值），可以使用 `headers` 并指定你想要发送的头部的键值对，如下所示：

```javascript
// 在 GET 请求中发送头部
$.ajax('/example.php', {
  'method' : 'GET',
  'headers' : {
    'X-my-auth' : 'SomeAuthValue'
  },
  success: function (data, textStatus, jqXHR) {
    console.log(data);
  }
});
```

在现代版本的 jQuery 中，当在 AJAX 请求期间专门使用 HTTP 身份验证协议时，你不再需要在发送之前使用 HTTP 身份验证头部。你可以直接使用 `username` 和 `password` 设置来指定 HTTP 身份验证凭据：

```javascript
// 使用 HTTP 进行请求
$.ajax('/example.php', {
  'method' : 'GET',
  'username' : 'myusername',
  'password' : 'mypassword',
  'success' : function (data, textStatus, jqXHR) {
    console.log(data);
  }
});
```

根据请求的性质以及你对请求控制的紧密程度，你可以使用辅助方法来代替 $.ajax() 方法。

## jQuery 辅助方法

在许多情况下，上述由 $.ajax() 方法提供的灵活性对于开发者来说有些大材小用。因此，jQuery 提供了封装了常用功能的辅助方法。方便使用这些方法是有代价的，因为它们缺乏 $.ajax() 方法内置的错误处理功能。

```javascript
// 简化的 GET 请求
$.get('/example.php', {
  'queryParam' : 'paramValue',
  function (data, textStatus, jqXHR) {
    console.log(data);
  }
});
```

## 集成 JavaScript 和 PHP

$.ajax 方法是内置的。对于 $.get() 方法，我们只需传递请求的 URL（以 JavaScript 对象的形式）以及成功返回时使用的回调函数。如果在执行请求时发生错误，$.get() 方法将静默失败。

人们可能会认为对应的 $.post() 方法功能相同（只是执行 HTTP POST）：

```javascript
// 简化的 POST 请求
$.post('/example.php', {
  'postParam' : 'paramValue',
  function(data, textStatus, jqXHR) {
    console.log(data);
  }
});
```

除了简单的 HTTP 和 HTTP POST 之外，还有两种额外的方法在某些情况下非常有用。第一个是 $.getJSON() 方法，它可以从服务器动态加载 JavaScript 文档并执行它：

```javascript
$.getJSON('/path/to/my.js', function() {
  // my.js 已加载，现在可以使用定义的任何函数
});
```

类似地，$.JSON() 方法对指定的 URI 执行 HTTP GET 请求，将返回值解析为 JSON 文档，并将其传递给回调函数：

```javascript
// 通过 HTTP 加载 JSON文档
$.JSON('/example.php', {
  'jsonParam' : 'paramValue',
  function(data, textStatus, jqXHR) {
    console.log(data.status);
  }
});
```

## 聊天客户端/jQuery 

我们已经准备好了后端脚本（列表 23.3 中的 chat.php），现在我们需要构建一个基于 jQuery 的前端，为最终用户显示一个有意义的用户界面——一个既允许输入也允许检索消息的界面。为了这些目的，我们将首先使用 Bootstrap CSS 框架构建一个简单的 HTML 界面，并使用一些自定义 CSS 为我们显示的每条聊天消息渲染流行的“气泡”样式的小部件（见列表 23.4）。

注意

> 对于渲染精美聊天气泡所使用的 CSS 样式，我们使用了由 John Clifford 开发的一个非常棒在线工具 Bubbler，其地址为：http://likepixels.co.uk/drop/bubbler/。

