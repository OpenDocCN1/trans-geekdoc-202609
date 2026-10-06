
![](img/Figure-6.4.jpg)

**图 6.4：** 登录时的 Session ID 创建流程

在`图 6.4`中，注意我们使用`JSESSIONID`作为会话 ID 的 cookie 名称。这是 Java HTTP 会话 cookie 中常用的名称。其他常用的会话令牌 cookie 名称是 PHP 的`PHPSESSID`或 Express 的`connect.sid`。然而，所有服务器都允许你配置此 cookie 的名称。

在客户端接收到成功身份验证的响应后，他们负责在每个请求中传递包含会话 ID 的 session cookie。如果请求中缺少 cookie，服务器将其视为未身份验证的请求。然而，大多数浏览器或网络查看器会自动记住并往返传递所有设置过的 cookie。`图 6.5`显示了这一过程的视觉示例：

![](img/Figure-6.5.jpg)

**图 6.5：** 登录时的 Session ID 创建流程

## 注意搜索词：HTTP cookies

Cookies 是在客户端浏览器和服务器之间往返的小型数据。Cookies 通常用于存储需要在每个请求中发送的信息，例如会话 cookie、授权令牌或语言等用户偏好。

某些服务器选择直接将用户数据存储在 cookie 中，而另一些则倾向于将用户数据存储在数据库中，并仅使用 cookie 存储会话 ID 以检索记录。这些方法存在多种权衡，但大多数情况下，在 cookie 中存储所有会话数据是困难的，因为这涉及到对其进行加密签名以确保恶意用户没有篡改，并且需要限制其能存储的数据量，以免通过在每个请求中添加过多的信息来减慢流量。

在大多数后端库中，在用户会话中存储信息是直观的。例如，我们可以如下代码片段所示，在 Java servlet 服务器中访问用户会话：

```java
import javax.servlet.http.HttpServletRequest;
import javax.servlet.http.HttpServletResponse;

//
// public void doGet(HttpServletRequest request, HttpServletResponse response){
//   // …
//   String uname=request.getParameter("userName");
//   HttpSession session=request.getSession();
//   session.setAttribute("uname", uname);
// }
```

我们可以使用 Node 的 Express 库`express-session`执行同样的操作，如下代码片段所示：

```javascript
app.get('/',(req,res) => {
    session=req.session;
    if(session.userid){
        res.send("Welcome! The user is logged in");
    }else
    res.sendFile('views/index.html',{root:__dirname})
```

在这些示例中，会话存储作为键值存储工作，允许我们设置和读取简单的字符串值。

## 应用权限控制

无论如何存储，用户会话数据都可以包含识别用户所需的所有信息：用户名、电子邮件、姓名、个人资料链接等。在这些会话数据中，应该包含特定的权限数据。

## 将分级权限映射映射到实现细节

到目前为止，我们定义的所有权限都是操作+资源的高级描述，例如`创建订单`或`更新菜单`。我们需要这些抽象权限转换为实际的实现细节。

我们可以将权限映射到特定的内容，如 URL、路由和函数。

权限到 URL 或路由的映射发生在应用程序的前端。例如，只有具有管理员或经理角色的用户才能访问`/update-menu.html`或移动应用中的相应路由。

如果前端有一个代理所有请求的 Web 服务器，只有授权用户才能成功向它们发送请求。这种方法的示例可以在`图 6.6`中看到，想要更新菜单的客户端可以通过 HTML 表单发送`POST` `/update-menu.html`请求，而不是直接向 API 发送`PATCH` `/api/menu/123321`。来自未授权角色用户的请求应被拒绝，如`图 6.6`所示：

![](img/Figure-6.6.jpg)

**图 6.6：** URL 级别的授权

某些服务器提供了管理员可以更新的配置，以强制这种映射。例如，使用 Java Web 应用程序，我们可以创建以下服务器配置来定义资源、其 URL、HTTP 方法以及访问这些资源的角色：

```xml
<security-constraint>
  <web-resource-collection>
    <web-resource-name>Protected Area</web-resource-name>
    <url-pattern>/jsp/update-menu.html</url-pattern>
    <http-method>PUT</http-method>
    <http-method>DELETE</http-method>
    <http-method>GET</http-method>
    <http-method>POST</http-method>
  </web-resource-collection>
  <auth-constraint>
    <role-name>admin</role-name>
  </auth-constraint>
</security-constraint>
<security-role>
  <role-name>customer</role-name>
</security-role>
<security-role>
  <role-name>admin</role-name>
</security-role>
```

此类配置允许我们对 URL 和单个 HTTP 方法进行配置访问控制：我们可以允许所有用户对大多数页面执行`GET`请求，但除非他们拥有正确的角色和权限，否则不允许`DELETE`、`POST`或`PATCH`请求。

然而，并不是所有的访问控制检查都直接映射到 URL 或路由。如果授权逻辑更加复杂，并要求你检查角色之外的多个事项（例如，用户在访问功能之前必须完成的操作，如验证其电子邮件），我们始终可以在代码中进行手动授权检查。以下代码展示了如何为 Python Web 框架 Django 手动对函数调用授权：

```python
from django.core.exceptions import PermissionDenied

def updateMenu(request, pk):
    if not user.has_perm('pizzaplace.change_menu'):
        raise PermissionDenied
#…
```

访问控制也可以在 API 级别完成，如`图 6.7`所示。虽然在前端级别验证访问是一项良好的做法，但大多数 API 端点都应该执行自己的访问控制检查。

![](img/Figure-6.7.jpg)

**图 6.7：** URL 级别的授权

我们将在本章稍后部分详细讨论对 API 资源的授权。

通常，每个应用程序模块或服务器都应该将所有传入的请求视为可能是未经授权的，即使它们本应来自信任的资源（如前端 Web 服务器）。

## 使用范围（scopes）检查授权

除了角色赋予用户的权限外，我们还可以赋予该用户对特定资源的权限。例如，一个`manager`用户可能希望某些`admin`用户能够访问会议的财务报告。在这种情况下，我们不想将`admin`用户升级为`manager`，因为该角色可能包含我们不想赋予给他们的其他权限。

在这种情况下，我们可以直接为用户分配范围或权限：

```json
{
  "country": "United States",
  "timezone": "America/Chicago",
  "roles": [
    "admin"
  ],
  //…
  "permissions": [
    "read:finantial_report",
    // …
  ]
}
```
