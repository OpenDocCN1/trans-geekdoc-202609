

```python
urlpatterns = [
    path('demo/', include('demo.urls')),
    path('admin/', admin.site.urls),
]
```

完成后续步骤后，你将让系统引导你的服务器在 URL 中搜索 `demo` 关键字。然后，将 URL 指向 demo 应用目录下的 `urls.py` 文件。

# 4. 构建 views.py 文件

最后，你将为 Django 项目创建 `views.py` 文件。该文件将在浏览器上创建一个视图。

直接使用这段代码段即可，它已经存在于 demo 目录的 views.py 文件中了。

```python
from django.http import HttpResponse
def index(request=None):
    return HttpResponse("Dataflair Django Tutorial<<html><body><h1>Hello World Dataflair Django tutorials</h1></body></html>")
```

顾其名，这就是你创建浏览器渲染视图的文件。

如你所见，你将导入 `HttpResponse` 函数，并创建一个名为 `index` 的函数，该函数已 `urls.py` 文件中使用。该函数接受请求的方式与服务器与服务器交互的方式相同。你将返回 `HttpResponse()`，在该函数的参数中包含的任何内容都将由浏览器部署。

除了 `HttpResponse` 之外没有额外的响应，你将来可能还会使用到它。

如果你已经遵循了目前的所有步骤，那么你刚刚创建了你的第一个 Django 应用和网页。

如果你愿意，可以继续打开 admin 应用，那将在下一节中介绍。

如果你的应用没有启动，你需要在 URL 中运行以下命令：

> localhost:8000/demo/

这一节让你学习了更多关于 Django 文件结构以及如何创建你的第一个应用。如果应用启动失败，不要担心，可能存在错误。请重新阅读这一节。

# Django Admin Interface

Django Admin界面是 Django 框架最显著的特性，它为网站维护者提供的便利是非常强大的。此外，它是 Django 框架的重要部分，将从许多方面让你受益。

首先，让我们探索网站的 Admin界面。

顾其名，Admin界面是你项目的引擎。网站管理员用它来添加、删除和修改网站上的内容。此外，它还用于维护开发者创建的其他功能。

嗯，这是一个棘手的部分，Admin界面是主控制器，需要由开发者单独进行编码。你需要处理从数据库连接到增强Admin界面安全性的一切事务，因为任何使用它的人都是控制器，任何留下的漏洞都会对你的网站造成灾难性的影响。

# 与 Django Admin界面交互

Django Admin 是一种为了满足开发者所有需求而设计的界面。它的语言比较通用。

Django Admin 拥有完整的界面，你现在不需要担心为你的项目编写界面。从开始，最好掌握设置 Django Admin 站点的流程，因为你将在未来的项目中心需要它。

# 准备 Django Admin站点

以下是你应该遵循的步骤，用于设置 Django Admin站点并运行用户模型

- 启动 Django 服务器，然后在 URL 栏中搜索：
  localhost:8000/admin/
  你应该能看到一个出现，网站会提示你输入用户名和密码。现在，你可以继续创建一个。
- 打开 PowerShell 或终端，并按 CTRL + C 停止服务器。
  接下来，输入以下命令：

```bash
python manage.py createsuperuser
```

- 运行上述命令后，它会要求你输入用户名，这应该是你的首选。然后它会要求你输入邮箱 ID 和密码。因此，你应该能够毫无问题地完成这些细节。

存在某些内置的安全功能，例如如果你的密码是纯数字，它将生成一个复杂的密码，并且许多此类安全问题已经为用户修复。

# Superuser (超级管理员)

superuser指的是你网站管理员的详情，它可以完成任何与你网站相关的数据操作和内容操作。

此外，你绝不要向任何人透露或共享superuser信息，因为它是你网站的核心驱动器。当网站运行时，它对于管理和控制你的网站至关重要。

成功构建superuser后，你将登录该管理员页面以再次启动你的 Django 服务器。

- 1. 使用你创建的信息登录 admin。
  你将看到选项和一个精美的界面：

由于自定义应用没有在 Django admin 界面中注册，它将不会显示其中任何一个。这里只有两个字段，每个字段都有两个选项。

- 3. 现在选择 users 字段，你应该看到类似这样的内容。

![](img/43582740ac1227a817786ef73e0f3772_394_0.png)

在这里，你应该只能看到一个用户以及你在内部插入的。尽管你无法看到密码。这是 Django 的优势，所有密码都使用 `settings.py` 文件中的唯一密钥进行加密。

- 3. 确认你创建的用户已保存。
4. 现在打开 phpadmin 并打开你所开发的 Django 项目数据库。接下来，如果你打开 `auth_users` 表，你会发现密码之外的细节都是相同的。

你还会看到数据库中存在你没有创建的额外表。嗯，不要担心，这些都是 `django.contrib` 包导入的模型表。`Django.contrib` 指的是 Django 的一个包，类似于 Python 使用标准库的关系。几乎所有所需的功能都在 `django.contrib` 包中。

- 5. 返回 Django 项目的首页。

- 6. 接下来，打开你应用的 `admin.py` 文件。目录结构看起来如下：

![](img/43582740ac1227a817786ef73e0f3772_395_0.png)

- 7. 打开 `admin.py` 文件并输入以下两行：

```python
from .models import Student
```

```python
admin.site.register(Student)
```

第一语句用于导入 `Student` 类或创建的自定义模型。

第二行将模型传递或注册模型到 Django Admin 界面。

- 8. 现在打开 admin 并打开 Django Admin 界面。你会看到一个学生列表。

![](img/43582740ac1227a817786ef73e0f3772_396_0.png)

在这里，你应该只能看到一个用户以及你在内部插入的。尽管你无法看到密码。这是 Django 的优势，所有密码都使用 `settings.py` 文件中的唯一密钥进行加密。

- 3. 接下来，点击任意学生

![](img/43582740ac1227a817786ef73e0f3772_396_1.png)

在这里，你可以直接访问并修改信息，而无需进入数据库。

此外，你应该看到各种选项，如保存和删除。

看看它赋予你的力量吧，无需输入任何内容，你只需要选择。

添加新学生将在你的数据库中创建新记录；这一切都是 Django ORM 的作用。

