

# 捉灵敢卫队

// 在控制器内部

```php
if ($_POST['accept_terms']) {
  $user = new User();
  $user->setEmail($_POST['email']);
  $user->setPassword($_POST['password']);

  if ($user->save()) {
    $email = new Email();
    $email->setSubject('Please verify..');

    if ($email->send()) {
      $this->flashMsg('Congrats');
      $this->redirect('/login.php');
    } else {
      // 关于邮件失败的处理
    }
  } else {
    // 关于用户保存失败的处理
  }
}
```

看起来眼熟吗？我认识许多 PHP 开发者在职业生涯中都做过这种事情，当注册过程涉及的步骤比简单的创建用户记录和发送邮件要多时。我们已经看到，在控制器方法内部进行这种数据弄乱会导致代码重复；这是一种完全可以避免的情况。

Lizzie 会怎么做？她的第一次尝试可能是将整个过程封装到单个对象中，从而产生一个看起来像这样的控制器方法。

// 在控制器内部

```php
$accepted = filter_input(INPUT_POST, 'accept_terms');
if ($accepted) {
  $reg = new UserRegistration();
  if ($reg->addUser($_POST)) {
    $this->flashMsg('Congrats');
    $this->redirect('/login.php');
  } else {
    $errors = $reg->getErrors();
    // 显示错误
  }
}
```

# 捉灵敢卫队 213

从我们控制器的角度来看，这是一个巨大的改进。我们不再被大量杂乱的 `if` 语句填充（其中有些甚至是嵌套的），现在我们只需要对 `UserRegistration` 实例调用一次 `addUser()` 方法。

这里的假设是，`UserRegistration` 对象协调了验证用户数据、哈希密码、创建用户记录以及任何相关行并最后发送到电子邮件的整个过程。

乍一看，这看起来完全令人满意。毕竟，我们现在拥有了一个对象，只需要向它传入一个结构适当的数据数组即可创建用户账户，结果是一个更精简、更简洁的控制器。更好的是，我们似乎遵循了“执行，不要询问”（Tell, Don’t Ask）原则，尽管我们还没有读过相关内容。

所以，这是向正确方向迈的一步，但我们完成这段特定的旅程了吗？这取决于 `UserRegistration` 类及其 `addUser()` 方法。如果只是只是把那些嵌套的 `if` 移动到了方法里，那么我们实际上什么都没有实现。

```php
<?php
class UserRegistration
{
    public function addUser(array $data) {
        $user = new User();
        $user->setEmail($data['email']);

        if ($user->save()) {
            $email = new Email();
            $email->setSubject('Please verify...');

            if ($email->send()) {
                return true;
            } else {
                return false;
            }
        } else {
            return false;
        }
    }
}
```

# 捉灵敢卫队 214

此外，如果我们所做的只是将整个过程放在一个方法调用之后，那么我们实际上是将自己限制在了一种“全有全无”的方法上。我们将所有必要的数据都丢给该方法；如果它成功了，那就太好了。如果不成功，呢？再重试一遍？

即使没有功能完好的水晶球，我们也可以相当确定，我们的用户至少会有一个人欢迎再次发送邮件，特别是当我们要求他们验证电子邮箱地址以激活账户时。

考虑到这一点，我们至少可以确定需要将该过程分为两个部分。此外，由于我们已经考虑过这些执行者实际上是服务候选人，那么让 Lizzie 在适当的服务类上通过实现方法调用的方式来实现这两个过程将是完全合理的。

这可能会导致我们得到类似这样的代码。

```php
<?php
class UserRegistration
{
    public function addUser(array $data)
    {
        $userService = new UserService();
        $user = $userService->addUser($data);

        if($instance instanceof User) {
            $emailService = new EmailService();
            $emailService->send($user, 'welcome.email.tpl');
        }
    }
}
```

现在我们完全拥有了 `UserService` 和 `EmailService` 类。太棒了。

然而，如果一个灵体（poltergeist）是由一个几乎或没有任何内部状态的对象泛化出来的，且其表面目的仅仅是触发其他系统对象的方法调用，那么这正是我们这里拥有的东西。

诚然，这是我们为了得到灵体而采取的一种高度刻意的路线，但对于我们那些经验较少的同胞来说，仅仅将一系列按键操作封装到一个似乎在为我们“自动化”事情的对象中，其实并不罕见。创建一个显式意图为了自动化一个……

# 捉灵敢卫队 215

复杂的过程看起来似乎是一个完全有效的方法，但如果这个对象本身没有带来任何实质内容，那么它很可能就是一个灵体。

幸运的是，修复我们现有的代码非常简单且直接。像任何“灵体”（Poltergeist）反模式的实例一样，它都可以通过重构来驱逐。驱逐灵体只需要将逻辑从执行体移动到调用者。由于它们本身没有实质内容，这一点在它们作为触发器时是显而易见的。驱逐我们的灵体只需将这些服务移回控制器即可。

```php
// 在控制器内部
```

$accepted = filter_input(INPUT_POST, 'accept_terms');
if ($accepted) {
    $userService = new UserService();
    $emailService = new EmailService();
    try {
        $user = $userService->addUser($data);
        $emailService->send($user, 'welcome.email.tpl');
        $this->flashMsg('Congrats!');
        $this->redirect('/login.php');
    } catch (UserService $use) {
        // 错误处理
    } catch (EmailService $ese) {
        // 错误处理
    } catch (Exception $e) {
        // 未知错误处理
    }
}

通过这些更改，我们现在消除了代码中的灵体，允许安全地删除 `UserRegistration` 类。此外，两个服务类的加入让我们能够访问创建账户和发送欢迎邮件这两个独立的过程。

这在许多方面都有意义。

# 捉灵敢卫队 216

将账户创建过程从控制器解耦，使得在 Web 环境之外创建用户成为可能。这样做有什么好处？如果我们在一个大型组织中部署，或者我们需要从旧应用程序迁移用户到新的应用程序中，批量创建用户账户的能力对我们来说将非常有益。从上传的 CSV 文件生成用户帐户变得轻而易举。

