

只有当 factories.yml 中的 auto_start 参数设置为 true 时（默认情况下即为此值），会话才会启动（使用 PHP 函数 session_start()）。如果你想手动启动用户会话，请禁用存储工厂的此设置。

Symfony 的会话处理基于 PHP 会话。这意味着，如果你希望客户端的会话管理由 URL 参数而非 Cookie 处理，只需更改 php.ini 中的 use_trans_sid 设置即可。请注意，不推荐这样做。

```
session.use_trans_sid = 1
```

在服务器端，Symfony 默认将用户会话存储在文件中。你可以通过更改 factories.yml 中 class 参数的值将它们存储在数据库中，如清单 6-18 所示。

### 清单 6-18 - 更改服务器会话存储，位于 apps/frontend/config/factories.yml

```yaml
all:
  storage:
    class: sfMySQLSessionStorage
    param:
      db_table: session  # Name of the table storing the sessions
      database: propel   # Name of the database connection to use
      # Optional parameters
      db_id_col: sess_id   # Name of the column storing the session id
      db_data_col: sess_data  # Name of the column storing the session data
      db_time_col: sess_time  # Name of the column storing the session timestamp
```

database 设置定义要使用的数据库连接。Symfony 随后将使用 databases.yml（参见第 8 章）来确定此连接的连接设置（主机、数据库名、用户和密码）。

可用的会话存储类包括 sfCacheSessionStorage、sfMySQLSessionStorage、sfMySQLiSessionStorage、sfPostgreSQLSessionStorage 和 sfPDOSessionStorage；推荐使用后者。要完全禁用会话存储，可以使用 sfNoStorage 类。

会话过期会在 30 分钟后自动发生。此默认设置可以在同一个 factories.yml 配置文件中为每个环境进行修改，但这次是在用户工厂中，如清单 6-19 所示。

### 清单 6-19 - 更改会话生存期，位于 apps/frontend/config/factories.yml

```yaml
all:
  user:
    class: myUser
    param:
      timeout: 1800     # Session lifetime in seconds
```

要了解有关工厂的更多信息，请参阅第 19 章。

## 动作安全

执行动作的能力可以限制为具有特定权限的用户。Symfony 为此目的提供的工具允许创建安全的应用程序，用户在访问某些功能或应用程序的某些部分需要先进行身份验证。保护应用程序需要两个步骤：为每个动作声明安全要求，并登录具有权限的用户，以便他们可以访问这些安全动作。

### 访问限制

在执行之前，每个动作都会通过一个特殊的过滤器，该过滤器检查当前用户是否有权访问请求的动作。在 Symfony 中，权限由两部分组成：

- 安全动作要求用户经过身份验证。
- 凭据是命名的安全权限，允许按组织分组管理安全。

限制对动作的访问只需在模块 config/ 目录中创建和编辑名为 security.yml 的 YAML 配置文件即可。在此文件中，你可以指定用户必须为每个动作或所有动作满足的安全要求。清单 6-20 显示了一个示例 security.yml。

### 清单 6-20 - 设置访问限制，位于 apps/frontend/modules/mymodule/config/security.yml

```yaml
read:
    is_secure: false    # All users can request the read action

update:
    is_secure: true    # The update action is only for authenticated users

delete:
    is_secure: true    # Only for authenticated users
    credentials: admin    # With the admin credential

all:
    is_secure: false    # false is the default value anyway
```

动作默认不安全，因此当没有 security.yml 或其中未提及某个动作时，所有用户都可以访问该动作。如果存在 security.yml，Symfony 会查找请求动作的名称，如果存在，则检查安全要求是否满足。当用户尝试访问受限动作时会发生什么取决于其凭据：

- 如果用户已通过身份验证并具有适当的凭据，则执行该动作。
- 如果用户未经过身份识别，他将被重定向到默认的登录动作。
- 如果用户已通过身份识别但没有适当的凭据，他将被重定向到默认的安全动作，如图 6-1 所示。

默认的登录和安全页面非常简单，你可能希望对其进行自定义。你可以在应用程序的 settings.yml 中更改清单 6-21 所示属性的值，以配置在权限不足时应调用哪些动作。

### 图 6-1 - 默认安全动作页面

![](img/0f886a7f4cbcc3939be96e985ca35ff4_88_0.png)

### 清单 6-21 - 默认安全动作定义在 apps/frontend/config/settings.yml 中

```yaml
all:
  .actions:
    login_module:  default
    login_action:  login

    secure_module: default
    secure_action: secure
```

### 授予访问权限

要访问受限动作，用户需要经过身份验证和/或具有特定的凭据。你可以通过调用 sfUser 对象的方法来扩展用户的权限。用户的身份验证状态由 setAuthenticated() 方法设置，并可使用 isAuthenticated() 进行检查。清单 6-22 显示了用户身份验证的简单示例。

### 清单 6-22 - 设置用户的身份验证状态

```php
class myAccountActions extends sfActions
{
  public function executeLogin($request)
  {
    if ($request->getParameter('login') == 'foobar')
    {
      $this->getUser()->setAuthenticated(true);
    }
  }

  public function executeLogout()
  {
    $this->getUser()->setAuthenticated(false);
  }
}
```

凭据的处理稍微复杂一些，因为你可以检查、添加、删除和清除凭据。清单 6-23 描述了 sfUser 类的凭据方法。

### 清单 6-23 - 在动作中处理用户凭据

```php
class myAccountActions extends sfActions
{
    public function executeDoThingsWithCredentials()
    {
        $user = $this->getUser();

        // Add one or more credentials
        $user->addCredential('foo');
        $user->addCredentials(array('foo', 'bar'));

        // Check if the user has a credential
        echo $user->hasCredential('foo');               =>  true

        // Check if the user has both credentials
        echo $user->hasCredential(array('foo', 'bar'));   =>  true

        // Check if the user has one of the credentials
        echo $user->hasCredential(array('foo', 'bar'), false); =>  true

        // Remove a credential
        $user->removeCredential('foo');
        echo $user->hasCredential('foo');               =>  false

        // Remove all credentials (useful in the logout process)
        $user->clearCredentials();
        echo $user->hasCredential('bar');               =>  false
    }
}
```

如果用户具有 foo 凭据，则该用户将能够访问 security.yml 要求该凭据的动作。凭据也可用于在模板中仅显示授权内容，如清单 6-24 所示。

### 清单 6-24 - 在模板中处理用户凭据

```php
<ul>
  <li><?php echo link_to('section1', 'content/section1') ?></li>
  <li><?php echo link_to('section2', 'content/section2') ?></li>
  <?php if ($sf_user->hasCredential('section3')): ?>
    <li><?php echo link_to('section3', 'content/section3') ?></li>
  <?php endif; ?>
</ul>
```

与身份验证状态一样，凭据通常在登录过程中授予用户。这就是为什么 sfUser 对象经常被扩展以添加登录和注销方法，以便在一个集中的位置设置用户的安全状态。

> 在 Symfony 插件中，sfGuardPlugin<sup>34</sup> 和 sfDoctrineGuardPlugin<sup>35</sup> 扩展了会话类以简化登录和注销。有关更多信息，请参阅第 17 章。

34. http://www.symfony-project.org/plugins/sfGuardPlugin
35. http://www.symfony-project.org/plugins/sfDoctrineGuardPlugin

