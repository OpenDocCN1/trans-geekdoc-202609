
> 提示
>
> 在表单的第一部分中，您还可以更改按钮的文本和外观。

![](img/4f47e47c67bd619ac73250f11c9fc7ce_160_0.png)

### 图 6.6

按钮类型应自动选择（作为订阅）。您可能也想更改货币，也可能不想。

- 6. 在表单步骤 1 下方，输入账单金额和计费周期（图 6.7）。

![](img/4f47e47c67bd619ac73250f11c9fc7ce_160_1.png)

账单金额显然是最重要的考虑因素。计费周期是指该账单金额覆盖的时间长度。您可以选择在两个或更多周期后停止自动计费，或者永不停止。

### 图 6.7

- 7. 选择使用您的安全商户帐户 ID（参见图 6.7）。
- 8. 在表单步骤 2 下，确保 PayPal 选项中的“保存”按钮已选中（图 6.8）。

> 提示
>
> 如果您使用 PayPal 帐户保存按钮，则会更安全且更易于更新。

![](img/4f47e47c67bd619ac73250f11c9fc7ce_160_2.png)

### 图 6.8

- 9. 在表单步骤 3 下，表明您不需要客户的送货地址。

如果您销售的是实物产品，则希望用户在 PayPal 中确认送货地址。然后，您可以使用 PayPal 为您生成运送标签，并从已转入您帐户的款项中扣除费用。

![](img/4f47e47c67bd619ac73250f11c9fc7ce_160_3.png)

### 图 6.9

- 10. 同样在表单步骤 3 下，提供“取消”和“完成”URL，并选择相应的复选框（图 6.9）。

这两个值必须指向您服务器上可通过 HTTPS 访问的页面。本章稍后将创建这两个脚本，分别命名为 cancel.php 和 thanks.php。

- 11. 单击“创建按钮”。
- 12. 在下一页中，复制生成的代码（图 6.10）。

![](img/4f47e47c67bd619ac73250f11c9fc7ce_161_0.png)

### 图 6.10

这是要集成到网站中的代码，您将在下一步执行该操作。

## 集成 PAYPAL

创建测试帐户和 PayPal 按钮后，您可以将网站与测试版 PayPal 关联。这样做非常简单：

- 1. 在适当位置添加按钮代码。
- 2. 创建 thanks.php 页面。
- 3. 创建 cancel.php 页面。

不过，会有一些棘手的问题，因此在集成并测试 PayPal 后，您将学习改进系统的方法。

## 更新注册页面

> 提示
>
> 请记住，您可以从 www.DMCinsights.com/ecom/ 下载本示例的所有源代码。

对于此特定网站，用户在成功完成注册流程后应前往 PayPal（单击按钮）。要实现此目的，首先更改 register.php 中的感谢消息，使其告知用户下一步该做什么：

```
echo "<h3>Thanks!</h3><p>Thank you for registering! To complete the
process, please now click the button below so that you may pay for your
site access via PayPal. The cost is $10 (US) per year. <strong>Note: When
you complete your payment at PayPal, please click the button to return to
this site.</strong></p>";
```

接下来，插入由 PayPal 生成的代码以添加按钮（图 6.11）：

![](img/4f47e47c67bd619ac73250f11c9fc7ce_161_1.png)

### 图 6.11

```
echo '<form action="https://www.sandbox.paypal.com/cgi-bin/webscr"'
     method="post">
<input type="hidden" name="cmd" value="_s-xclick">
<input type="hidden" name="hosted_button_id" value=
     "8YW8FZDELF296">
<input type="image" src="https://www.sandbox.paypal.com/en_US/i/
     btn/btn_subscribeCC_LG.gif" border="0" name="submit" alt="PayPal -
     The safer, easier way to pay online!">
<img alt="" border="0" src="https://www.sandbox.paypal.com/en_US/i/
     scr/pixel.gif" width="1" height="1">
</form>';
```

上述代码应放在感谢消息之后、包含页脚之前。

还需要进行两项更改。首先，原始 INSERT 查询为新用户提供了下个月的访问权限。现在应将其更改为用户的访问权限有效期至昨天（即，其帐户未激活）：

```
$q = "INSERT INTO users (username, email, pass, first_name, last_name,
     date_expires) VALUES ('$u', '$e', '" . get_password_hash($p) . "', '$fn',
     '$ln', SUBDATE(NOW(), INTERVAL 1 DAY ))";
```

其次，让我们将用户的新 ID 值存储在会话中，以便在用户从 PayPal 返回时可以更新其记录。为此，请在确认 `mysqli_affected_rows($dbc)` 等于 1 之后的任意位置添加以下代码：

```
$uid = mysqli_insert_id($dbc);
$_SESSION['reg_user_id'] = $uid;
```

我特意将其命名为 `reg_user_id` 而不是 `user_id`，以免系统误以为用户已登录（实际上未登录；登录过程会创建 `$_SESSION['user_id']`）。您将在 thanks.php 中看到 `$_SESSION['reg_user_id']` 的使用情况。

## 创建 thanks.php

客户在完成 PayPal 订单并单击按钮返回本网站后，会进入 thanks.php 页面。此页面需要更新数据库，为用户帐户增加一年的访问权限（图 6.12）。其定义方式可能如下：

![](img/4f47e47c67bd619ac73250f11c9fc7ce_163_0.png)

### 图 6.12

### thanks.php

```
1 <?php
2 require ('./includes/config.inc.php');
3 redirect_invalid_user('reg_user_id');
4 require (MYSQL);
5 $page_title = 'Thanks!';
6 include ('./includes/header.html');
7 $q = "UPDATE users SET date_expires = ADDDATE(date_expires,
 INTERVAL 1 YEAR) WHERE id={$_SESSION['reg_user_id']}";
8 $r = mysqli_query ($dbc, $q);
9 unset($_SESSION['reg_user_id']);
10 ?><h3>Thank You!</h3>
11 <p>Thank you for your payment! You may now access all of the site's
 content for the next year! <strong>Note: Your access to the site will
 automatically be renewed via PayPal each year. To disable this feature,
 or to cancel your account, see the "My preapproved purchases" 
 section of your PayPal Profile page.</strong></p>
12 <?php include ('./includes/footer.html'); ?>
```

有三行关键代码被突出显示。首先，仅当会话中存在 reg_user_id 元素时才应访问此脚本，这意味着页面仅在注册后才可访问。

其次，该查询对 users 表运行 UPDATE 命令，为该用户的到期日期增加一年。

第三，查询后会取消设置 $_SESSION['reg_user_id'] 元素。采取此步骤后，页面只能加载一次。此检查可防止黑客仅通过重新加载此页面就为自己的帐户添加年限。

从安全角度来看，此脚本存在一个问题：它假设用户已付款，但您并不确定这一点。如果您注册新帐户，然后不经过 PayPal 直接将 URL 更改为 thanks.php，结果将是一样的。这非常糟糕。

> 出于礼貌，会告知客户付款将自动定期扣除，以及他们可以采取什么措施来防止这种情况。

从客户角度来看，存在三个问题。首先，只有在客户返回此页面时，才会将其购买记入其账户。这将责任推卸给了客户，而确保客户获得已付款的服务其实是您的责任。其次，没有确认 UPDATE 查询是否正常工作（即，是否影响了一行）。第三，没有任何记录将客户的 PayPal 订单与其在本网站上的帐户关联起来。

本章后续页面将使用一种称为 IPN 的机制来解决上述所有四个问题。

## 创建 cancel.php

如果客户取消了 PayPal 交易，他们将进入 cancel.php 页面。此页面应仅指示客户其帐户的当前状态（图 6.13）。该脚本的示例如下：

![](img/4f47e47c67bd619ac73250f11c9fc7ce_164_0.png)

### 图 6.13

### cancel.php

```
<?php
require ('./includes/config.inc.php');
require (MYSQL);
$page_title = 'Oops!'; include ('./includes/header.html');
?><h3>Oops!</h3>
<p>The payment through PayPal was not completed. You have a valid membership at this site, but you will not be able to view any content until you complete the PayPal transaction. You can do so by clicking on the Renew link after logging in.</p>
<?php include ('./includes/footer.html'); ?>
```

此脚本的重要之处在于表明：

- 1. 客户已成功在网站上注册。
- 2. 客户仍然无法访问任何内容。
- 3. 要更改第 2 点，客户应登录并单击“续订”。

续订流程将在本章末尾实现。
