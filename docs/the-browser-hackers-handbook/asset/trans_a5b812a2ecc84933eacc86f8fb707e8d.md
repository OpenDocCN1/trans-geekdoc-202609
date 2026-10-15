
在这段示例中，第一个测试会检查隐藏变量，并根据浏览器将平台设置到浏览器变量中。随后，在确定为浏览器平台后，会检查 Firefox 中使用模板 HTML 元素的情况。该特性在 Firefox 22 中引入，因此其存在表明版本至少为 22。或者，如果没有模板元素，则可以推断版本早于 22。

可见性特性是在 IE 10 中添加的，因此可以确认被测试的浏览器至少为 IE 10。撰写本文时，IE 11 尚未发布，但这里是一个很好的位置来添加 IE 11 测试，或者选择仅在 IE 9 或 8 中存在的其他特性并在此添加额外的测试。

像 [http://caniuse.com](http://caniuse.com) 和 [http://html5test.com](http://html5test.com) 这样的网站是非常好的资源。它们允许你比较浏览器版本和平台版本，以帮助创建这类检查。

# 绕过 Cookie 防护

和它们美味的同类一样，Cookie 是让使用网页变得更甜蜜的小吃。Cookie 对于 Web 开发者有许多好处，但同样也是攻击者的优势。本节更深入地探讨 Cookie，探讨它们为何有用，它们的工作原理以及它们在 Web 事务中呈现的样子。你还可以了解如何在更复杂的浏览器攻击中滥用 Cookie。

Cookie 是一个简单的机制，用于在浏览器内存储数据。Cookie 所存储的数据正是它们有趣的所在。Cookie 用于多种场景，从存储会话标识符（这样当你访问网站时，网站会记住你是谁）到存储最近操作的会话数据。Cookie 还包含一个有效期属性，指示其有效时间，范围从秒到遥远的未来。

Cookie 可以跨浏览器重启保持存在，也可以在浏览器关闭时立即删除。Cookie 存储区（Cookie jar）负责维护所有这些 Cookie，它是由 Web 应用程序维护的本地浏览器数据库，其中包含应用程序设置的 Cookie 信息。

Web 应用请求浏览器在特定时间内存储一段信息。当浏览器重新访问在 Cookie 作用域内的页面时，浏览器会在每次 HTTP 请求中携带 Cookie。这使得浏览器能够识别重复访问的特定用户，并用于广告跟踪、记住你的姓名并在你访问时向你打招呼等用途。

## 理解结构

Cookie 数据在浏览器和 Web 应用之间双向传输。要在浏览器中设置 Cookie，应用必须发送一个 Set-Cookie 响应头，其中包含 Cookie 的详细信息，包括：

*   Cookie 的名称

*   Cookie 的值

*   Cookie 失效的时间

*   Cookie 适用的路径

*   Cookie 适用的域

*   其他 Cookie 属性

本节将探讨 Set-Cookie 请求的不同属性，帮助你理解随后的 Cookie 攻击。

在开始之前，我们编写一个示例 Ruby 页面，它会设置两个 Cookie，然后在屏幕上打印它们的值。下面的代码设置了两个 Cookie：一个会话 Cookie（没有设置失效日期），以及一个持久 Cookie（失效时间为 7 小时）。代码还为每个 Cookie 设置了 HttpOnly 标志，并且 Cookie 适用于整个 browserhacker.com 域：

```
require 'rubygems'
require 'thin'
require 'rack'
require 'sinatra'
require 'json'

class CookieDemo < Sinatra::Base
  get "/" do
    response.set_cookie "session_cookie", {:value => 'yes',
      :domain => 'browserhacker.com', 
      :path => '/' ,  :httponly => true}
    response.set_cookie "persistent_cookie", {:value => 'yes',
      :domain => 'browserhacker.com', 
      :path => '/' , :httponly => true ,
      :expires => Time.now + (60 * 60 * 7) }
    "\n" +  request.cookies.to_json + "\n\n"
  end
end

@routes = {
    "/" => CookieDemo.new
}

@rack_app = Rack::URLMap.new(@routes)
@thin = Thin::Server.new("browserhacker.com", 4000, @rack_app)

Thin::Logging.silent = true
Thin::Logging.debug = false

puts "[#{Time.now}] Thin ready"
@thin.start
```

你可以使用 curl 查看 Cookie 如何被发送。例如：

```
curl -c cookiejar -b cookiejar -v http://browserhacker.com 
```

执行后，Cookie 会被存储在 cookiejar 文件中，随后的请求会使用该文件。下面的图示（Figure 6-11）展示了如果多次发送相同请求会发生什么：

 start figure 

[**Figure 6-11:**](#c06.html#figureanchor6-11) 设置并发送 Cookie

![c06f011.tif](image_fi/662090c06/c06f011.png)

 end figure 

如所示，Cookie 以 `cookiename=value` 形式在请求中发送，字段之间用分号（;）分隔。当应用发送 Cookie 时，每个 Set-Cookie 都占据单独一行。会话 Cookie（session_cookie）和持久 Cookie（persistent_cookie）几乎相同，唯一的区别是会话 Cookie 没有 Expires 属性，而持久 Cookie 的 Expires 时间比会话 Cookie 晚 7 小时。

## 理解属性

Cookie 属性帮助确定 Cookie 何时应返回到服务器以及 Cookie 应该存活多久。这些属性的组合旨在限制用户受到攻击的暴露时间，并确保数据在需要时不再保留。正如开发者需要理解这些属性如何影响用户与应用的交互一样，你也需要了解它们的功能。

### 理解 Expires 属性

Expires 属性帮助浏览器确定 Cookie 应保留多久。Cookie 可以跨浏览器重启保持存在，也可以在浏览器关闭时立即自毁。若不设置 Expires 属性，则可以保证 Cookie 永不会写入磁盘，浏览器关闭后数据即被销毁。这常用于登录会话等不希望数据跨重启保存的场景。

在用户跟踪场景中，会话 Cookie 并不理想。如果应用希望每次用户返回时都能识别其身份，持久 Cookie 更合适。持久 Cookie 设置一个在未来某一时刻失效的日期，失效时间可从几秒后到非常遥远的未来，使 Cookie 存活时间长于用户。

了解 Cookie 类型在进行会话窃取攻击时尤为重要。会话时长和会话超时值决定了你可以维持访问的时间长度。短的会话超时即使 Cookie 生命周期较长，也会限制其可用性。对于浏览器攻击，理解这些细节很重要。

### 理解 HttpOnly 标志

HttpOnly 标志可以防止 Cookie 被 JavaScript 和其他脚本语言访问。该标志告诉浏览器仅通过 HTTP 协议传输 Cookie，且不在文档对象模型（DOM）中可访问。这能够阻止 XSS 攻击将 Cookie 数据发送到外部，也能防止在渲染的 HTML 代码中修改 Cookie。我们在此基础上延伸之前的代码示例，进一步探讨该标志。

