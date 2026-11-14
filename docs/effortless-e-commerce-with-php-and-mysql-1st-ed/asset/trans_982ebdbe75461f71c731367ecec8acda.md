

需要更新两次：一次在 thanks.php 中，一次在 ipn.php 中。要修复此问题，请删除或注释掉以下代码行：

```php
redirect_invalid_user('reg_user_id');
$q = "UPDATE users SET date_expires = ADDDATE(date_expires, INTERVAL 1 YEAR) WHERE id={$_SESSION['reg_user_id']}";
$r = mysqli_query ($dbc, $q);
unset($_SESSION['reg_user_id']);
```

现在你可以通过重复本章“测试网站”部分中概述的步骤来测试新系统。

## 续订账户

网站上必须创建的最后一个功能是续订账户的功能。鉴于 PayPal 中已设置定期付款系统，客户可能需要续订其账户的情况只有两种：

- 客户已注册但在 PayPal 上未完成付款。
- 客户已注册并在 PayPal 上完成了付款，但后来取消了定期付款，现在想在账户过期一段时间后续订账户。

续订页面应仅对已登录用户可访问，并且应显示与注册页面相同的 PayPal 按钮代码。流程的其他部分完全相同。以下是 renew.php：

### renew.php

```php
<?php
require ('./includes/config.inc.php');
redirect_invalid_user();
$page_title = 'Renew Your Account';
include ('./includes/header.html');
require (MYSQL);
?><h3>Thanks!</h3><p>Thank you for your interest in renewing your account! To complete the process, please now click the button below so that you may pay for your renewal via PayPal. The cost is $10 (US) per year.</p>
<form action="https://www.sandbox.paypal.com/cgi-bin/webscr"
method="post">
<input type="hidden" name="cmd" value="_s-xclick">
11 <input type="hidden" name="custom" value="<?php echo $_SESSION ['user_id']; ?>">
12 <input type="hidden" name="hosted_button_id" value="8YW8FZDELF296">
13 <input type="submit" name="submit_button" value="Renew &rarr;" id="submit_button" class="formbutton" />
14 </form>
15 <?php include ('./includes/footer.html'); ?>
```

为了向你展示一些不同之处并使按钮更像网站的其他部分，我将按钮本身从指向 PayPal 服务器上文件的 <IMG> 标签更改为使用电子商务网站上其他提交按钮所用相同类的提交输入。图 6.18 显示了结果。此更改根本不会影响 PayPal 系统，因为按钮仅用作用户点击的内容；真正的功能在隐藏输入中。话说回来，你应该注意，在这种情况下，自定义值来自会话。

![](img/4f47e47c67bd619ac73250f11c9fc7ce_175_0.png)

图 6.18

## 上线运行

当你彻底测试了网站与 PayPal 的协作方式，并准备使整个项目上线时，只需执行几个简单步骤。

- 1. 如果你还没有，创建一个真实的 Premiere 或 Business PayPal 账户。
- 2. 自定义 PayPal 体验（请参见侧边栏）。
- 3. 使用真实的 PayPal 账户，创建要用于你电子商务网站的按钮代码。
- 4. 用新的、真实的 PayPal 生成的按钮代码替换 register.php 和 renew.php 中的按钮代码（相同代码的变体可用于两者）。
- 5. 同样在 PayPal 中，为账户启用 IPN（请参见本章前面的步骤）。
- 6. 更新 ipn.php 脚本。

你需要：

- 将 fsockopen() 行更改为连接到真实的 PayPal。
- 确保用于与 `$_POST['receiver_email']` 比较的电子邮件地址正确。
- 确保用于与 `$_POST['mc_gross']` 比较的付款金额正确。
- 确保用于与 `$_POST['mc_currency']` 比较的货币缩写正确。

上述列出的四个 ipn.php 因素可以改在配置文件中定义。

- 7. 将 `config.inc.php` 中 `$live` 变量的值更改为 true。

就我而言，做完所有这些之后，我可能会执行几笔真实交易，以确认系统正常工作。这样做会让你花掉几美元（在交易费中，因为钱是从你付给你自己），但你会内心安定。另外，请务必定期将 PayPal 历史记录中的交易与订单表中的交易进行比较，以确保没有客户被欺骗或在欺骗你。

## 自定义 PayPal 体验

尽管使用 PayPal 的网站付款标准系统意味着客户会离开你的网站并在 PayPal 上花费一些时间，但体验不必过于突兀。如果你登录 PayPal 并点击个人资料，在销售偏好横幅下你可以做很多事情。你可以在那里建立税收和运输政策。你还可以在那里查看和更新按钮。更重要的是，从客户体验的角度来看，你可以创建特定的客户服务消息并定义模板作为自定义支付页面。自定义支付页面可以在一定程度上使用你自己的图片和颜色，使 PayPal 界面看起来类似于你自己的网站。如何操作在 PayPal 的自定义支付页面文档中找到的链接中有详细说明。

## 第三部分
销售实体产品

![](img/4f47e47c67bd619ac73250f11c9fc7ce_177_0.png)

## 7 第二个网站：结构与设计

你将在本书的帮助下开发的第二个电子商务网站将销售实体产品：咖啡（咖啡豆，不是冲泡过的！）以及咖啡相关的小商品。_Coffee_ 网站将具有这些主要功能：

- HTML、PHP 和 MySQL 使用的复杂度更高
- 可浏览的目录，包含销售信息
- 用户购物车和愿望清单功能
- 通过 Authorize.net 进行内联支付处理
- 创建产品、折扣商品、管理库存和处理订单的管理功能

本书第三部分“销售实体产品”的五章将带你了解这些常见电子商务功能和更高级技术的组合。作为一种保险措施，我将为你可能觉得混乱或超出服务器能力的某些更复杂的代码提供替代方案。

## 关于网站

因为这个咖啡店示例将比内容管理示例复杂得多，在进入实际实现之前，我想详细谈谈它的目标和功能。

## 出售的商品

本书的目的是展示进行电子商务所含义的最广泛范围，因此 Coffee 网站示例的第一个目标是销售实体产品，这与销售虚拟内容需要不同的方法。一个含义是，Coffee 网站需要谨慎处理客户被收取订单费用的时间与订单实际发货的时间之间的关系。销售实体产品还需要使用 SKU（库存单位）：每件商品的唯一标识符。没有 SKU，就没有库存管理，也无法确定客户收到的是他们想要的准确商品。

销售虚拟产品也可能需要 SKU，但你不需要考虑库存管理。

实体产品分为两大类：

- 单独的、不相关的物品，例如艺术品
- 一款主题下的不同版本，例如有平装、精装或电子版可供选择的书

这些类别之间的区别很重要。例如，如果你在销售书籍，你会希望客户能够在同一页面的可用选项中选择格式。但是，每个可用格式仍然需要自己的唯一标识符。相反，艺术品或任何没有不同格式或属性的产品，更容易向客户展示并作为库存进行管理。如你所见，处理 SKU 和其他产品属性的方式在这两种类型之间有所不同，因此 Coffee 电子商务商店销售这两类实体产品：一类是杯子、饼干等小商品（图 7.1），它们被单独处理；另一类是咖啡，具有共同的通用属性，但以特定格式购买（例如尺寸或研磨与整豆，图 7.2）。

![](img/4f47e47c67bd619ac73250f11c9fc7ce_179_0.png)

图 7.1

![](img/4f47e47c67bd619ac73250f11c9fc7ce_179_1.png)

图 7.2

本书这一部分的大部分工作和代码将涉及在数据库、显示的产品目录、购物车和管理界面中使用 SKU。在你自己的电子商务项目中，你可以应用这些相同的理论和代码来销售不同格式的音乐、不同尺寸和颜色的衣物等等。

为了简化示例，我决定忽略一些咖啡豆变量，并完全忽略销售易腐商品所涉及的问题。

支持以折扣价提供产品的功能进一步使数据库和代码复杂化。这是一个不错的功能，并且可以大大有助于增加业务。

