

这段代码与注册脚本中的代码几乎完全相同，只是错误被分配给了`$pass_errors`数组。

- 6. 如果一切正常，请根据数据库验证当前密码：

  ```php
  if (empty($pass_errors)) { // If everything's OK.
  $q = "SELECT id FROM users WHERE pass='" . get_password_hash($current) . "' AND id={$_SESSION['user_id']}";
  $r = mysqli_query($dbc, $q);
  if (mysqli_num_rows($r) == 1) { // Correct
  ```

要确认当前密码正确，会运行一个数据库查询，与登录查询类似，只是它使用用户的 ID（来自会话），而不是他们的电子邮件地址。

- 7. 用新密码更新数据库：

  ```php
  $q = "UPDATE users SET pass='" . get_password_hash($p) . "' WHERE id={$_SESSION['user_id']} LIMIT 1";
  if ($r = mysqli_query($dbc, $q)) { // If it ran OK.
  ```

这个查询与 `forgot_password.php` 中的查询几乎完全相同。

- 8. 向用户指示更改成功：

  ```php
  echo '<h3>Your password has been changed.</h3>';
  include ('./includes/footer.html');
  exit();
  ```

消息会被打印，包含页脚，然后脚本使用 `exit()` 终止，这样表单就不会再次显示（图 4.19）。你还可能想给用户发送电子邮件以指示密码更改（但不要真的将新密码发送给他们）。

![](img/4f47e47c67bd619ac73250f11c9fc7ce_118_0.png)

- 9. 如果出现问题，触发错误：

  ```php
  } else { // If it did not run OK.
  trigger_error('Your password could not be changed due to a system error. We apologize for any inconvenience.');
  }
  ```

如果数据库更新失败，则适用此 `else` 子句，在真实且经过测试的站点上，这确实不应该发生。

- 10. 完成脚本的处理部分：

  ```php
  } else {
  $pass_errors['current'] = 'Your current password is incorrect!';
  } // End of current password ELSE.
  } // End of $p IF.
  } // End of the form submission conditional.
  ```

如果提供的当前密码与数据库中当前用户的密码不匹配，则适用此 `else` 子句。在这种情况下，会添加一个错误，该错误将显示在当前密码输入框旁边。

- 11. 显示表单：

  ```php
  require ('./includes/form_functions.inc.php');
  ?><h3>Change Your Password</h3>
  <p>Use the form below to change your password.</p>
  <form action="change_password.php" method="post" accept-charset="utf-8">
  <p><label for="pass1"><strong>Current Password</strong></label>
  <br /><?php create_form_input('current', 'password', $pass_errors); ?></p>
  <p><label for="pass1"><strong>New Password</strong></label>
  <br /><?php create_form_input('pass1', 'password', $pass_errors); ?><small>Must be between 6 and 20 characters long, with at least one lowercase letter, one uppercase letter, and one number.</small></p>
  <p><label for="pass2"><strong>Confirm New Password</strong></label>
  <br /><?php create_form_input('pass2', 'password', $pass_errors); ?></p>
  <input type="submit" name="submit_button" value="Change &raquo;" id="submit_button" class="formbutton" />
  </form>
  ```

表单有三个密码输入字段。每个字段都是使用 `create_form_input()` 函数生成的。

- 12. 完成页面：

  ```php
  <?php
  include ('./includes/footer.html');
  ?>
  ```

- 13. 保存并测试更改密码脚本。

## 提高安全性

本示例中的用户账户系统展示了一种良好的安全方法。首先，用户被要求在密码中同时使用字母和数字，并且每种字母大小写至少包含一个。你可以通过要求至少包含一个非字母数字字符并增加最小长度来提高安全性。安全性与便利性成反比，因此只有在知道这些更改会惹恼一些潜在客户的情况下，你才会做出这些更改。我还选择不实现“记住我”选项，因为要求用户每次访问网站时都登录可以提供更好的安全性（当然，这同样是一种不便）。

作为另一道防线，密码在发送到数据库之前会被安全哈希处理，并在数据库中以二进制格式存储。通过注册流程可以创建的唯一用户账户类型是普通会员；无法诱骗系统创建管理员账户。

改善网站安全性的另一种显而易见且相对简单的方法是为注册和登录流程实现 SSL。为此，请将注册页面的链接更改为：`'https://' . BASE_URL . 'register.php'`。该表单将通过 HTTPS 加载，表单数据也将通过 HTTPS 发布回服务器。事实上，如果网站中仅使用相对链接，则一切都将是 HTTPS，直到你创建一个返回到 HTTP 连接的链接。

> **提示**
> 书中第三部分“销售实体产品”将演示根据需要切换 SSL 的使用。

通过 HTTPS 提供登录表单更棘手，因为表单被其他页面包含。你的选择是通过 HTTPS 提供每个页面，这不是理想的做法，或者创建一个单独的登录页面。

如前所述，你可以将激活流程作为注册的一部分来实现，在这种情况下，客户在激活账户后（而不是在首次注册后）会被发送到 PayPal。你也可以在请求更改密码时发送一封电子邮件，只有点击该邮件中的链接，用户才能重置密码。现在，任何人都可以重置其他用户的密码，这很烦人，即使它不会对安全性产生不利影响。

> **提示**
> 从安全性角度来看，将会话 ID 存储在 Cookie 中优于将其存储在链接和表单中。

由于此系统依赖登录来验证用户，因此其安全性很大程度上依赖于使用会话和 Cookie（用于在浏览器中存储会话 ID）。限制 Cookie 的生命周期、更改会话名称（也是 Cookie 的名称）以及调整其他 Cookie 参数都可以提高网站的安全性。你甚至可以仅通过 SSL 发送 Cookie，但这将要求用户登录后对每个页面都使用 SSL。

就会话本身而言，我在第 2 章“安全基础”中提出的一项建议是，如果使用共享主机，请更改会话存储目录。你还可以缩短会话过期的速度，以及会话 Cookie 过期的速度。

这些都是 *潜在* 更改。你应该实施的一项建议是更改管理员用户的会话 ID。通过这样做，你可以防止 *会话固定攻击*。

*会话固定攻击* 是指恶意用户 Alice 在你的网站上完全合法地启动她自己的会话。然后她让管理员 Bob 使用同一个会话 ID 访问网站，通常是诱使 Bob 点击一个嵌入了会话 ID 的链接。当 Bob 登录网站时，该会话现在将与一个管理员账户关联，从而让 Alice 通过她的浏览器和现有会话获得管理员访问权限。防止这种情况非常简单：使用 *session_regenerate_id()* 函数更改会话 ID。通过这样做，当 Bob 登录时，他的会话 ID 会更改，这意味着 Alice 的合法会话不会更新以反映 Bob 的管理员身份。

要将此技术添加到 *login.inc.php* 脚本中，请更改会话中数据的存储方式为：

```php
if ($row[2] == 'admin') {
  session_regenerate_id(true);
  $_SESSION['user_admin'] = true;
}
$_SESSION['user_id'] = $row[0];
$_SESSION['username'] = $row[1];
if ($row[3] == 1) $_SESSION['user_not_expired'] = true;
```

你需要在存储任何会话数据之前调用 *session_regenerate_id()*，因为将 *true* 作为第一个参数传递给该函数时，任何现有会话数据也会被销毁。

最后，在本示例中，对网站内容的访问将由没有时间的日期决定。使用编写的会话，最坏的情况是，一个今天账户过期的用户被允许继续访问网站内容几分钟或几小时到明天。但即便如此，只有在用户保持会话活动的情况下才成立。在我看来，这不算大问题。

![](img/4f47e47c67bd619ac73250f11c9fc7ce_121_0.png)

