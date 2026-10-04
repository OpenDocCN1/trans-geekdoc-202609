
购买。信息需要通过相对安全的连接进行收集，然后这些信息需要由有资质的机构进行验证。这将需要一些配置以及一些自定义工具的使用。

## 你需要什么？

由于你是在目录的基础上构建此应用程序，因此大部分代码和信息对你来说非常熟悉。每个页面都要检查的一个显著特征是一个允许人们直接进入结账页面的按钮。图 14-1 显示了一个示例。

![](img/245156cc770929860a3ede93c01f9981_391_0.png)

图 14-1：带有结账按钮的分类页面

在列出项目的页面上，必须有一组表单，允许人们指示他们想要购买的项目。图 14-2 显示了一个允许人们通过点击 `Order!` 按钮将商品添加到购物车的页面。

然后必须有一个页面列出当前购物车中所有的商品。该页面应该允许人们增加或减少某个商品的数量，或者完全删除商品。图 14-3 中的页面就可以胜任了。

![](img/245156cc770929860a3ede93c01f9981_392_0.png)

图 14-2：带有订单按钮的项目页面

![](img/245156cc770929860a3ede93c01f9981_392_1.png)

图 14-3：购物车页面

## 第 14 章：购物车

流程结束后，会有一个页面用于收集用户信息和偏好。根据你的具体需求，你可能需要比本章显示的更复杂的结构。图 14-4 中显示的字段是一个很好的开始。该页面应该在信用卡授权被机构拒绝时指示错误。

![](img/245156cc770929860a3ede93c01f9981_393_0.png)

图 14-4：结账页面

最后，应该有一个收据——一个确认订单并告诉用户订单号的页面。

对你重要的信息没有包含在代码中。例如，没有添加或删除配送方式的管理页面。到目前，你可能已经看到了足够的页面来了解如何创建一个。

## 你需要防止什么？

这里基本上两点需要注意。第一是确保你可以从页面到页面跟踪用户。第二是将信用卡号和其他个人信息远离窥探。

## 数据

这里使用的数据库将添加到目录数据库。关于商品的信息将存储在这些表中，而图 14-5 所示的数据结构提供了一些惊喜。

| addresses | items |
| :--- | :--- |
| address_id | order_id |
| user_id | item_id |
| address | product_id |
| address2 | style_id |
| city | subtitle_id |
| state | qty |
| zip | price |
| phone | total_price |

| users | orders |
| :--- | :--- |
| user_id | order_id |
| email | user_id |
| firstname | address_id |
| lastname | status_id |
| | total_price |
| | shipping |
| | ship_cost |
| | cc_number |
| | cc_exp_yr |
| | cc_exp_mon |
| | cc_type_code |
| | create_dt |

| status | cc_types |
| :--- | :--- |
| status_id | cc_type_code |
| status | cc_type |

| shipping | |
| :--- | :--- |
| shipping_id | |
| shipping | |
| per_order | |
| per_item | |

图 14-5：购物车结构

这里有几点值得注意。首先注意订单确实是工作的中心。每个表以某种方式都与订单相关。订单表存储了 `user_id`、`address_id` 以及所有支付信息。注意 order 表与 items 表之间一对多的关系。这是因为每个订单可以有多个商品，这是合理的。

![](img/245156cc770929860a3ede93c01f9981_394_0.png)

考虑一下你是否想在数据库中存储信用卡号。我们包含了一个信用卡号列，但这并不意味着你应该使用它。首先考虑你的设备是否足够安全。如果你不确定答案，那么答案是否定的。如果你使用的是共享服务器（可能是 ISP 提供的安全服务器），你应该认为存储信用卡号是不安全的。其他人将访问该设备，并能够看到你写入数据库的内容。请记住，并没有要求你在任何地方存储信用卡号。你只需验证号码并将其从内存中删除。如果它从未写入磁盘，它将很难被盗取。

注意用户和地址信息是分开的。这样做是为了允许单个用户（通过电子邮件地址识别身份）提供两个地址——工作和家里。shipping 表将存储移动货的选项。如果你选择，它可能包含 UPS、USPS 和 FedEx 的选项。我将在“代码概述”中详细讨论这些选项。status 表将让你知道订单是缺货、已发货还是取消，而 cc_types 表存储你愿意接受的信用卡。

```
# 表 'addresses' 的结构
#
```

```
CREATE TABLE addresses (
address_id int(11) NOT NULL auto_increment,
user_id int(11) NOT NULL,
address varchar(40),
address2 varchar(40),
city varchar(40),
state char(2),
zip varchar(10),
phone varchar(20),
PRIMARY KEY (address_id),
KEY address_user_key (user_id);
```

```
);
#
```

```
# 表 'cc_types' 的结构
#
```

```
CREATE TABLE cc_types (
cc_type_code char(3) NOT NULL,
cc_type varchar(30) NOT NULL
```

```
);
#
```

```
# 表 'orders' 的结构
#
```

```
CREATE TABLE orders (
order_id int(11) NOT NULL auto_increment,
user_id int(11) NOT NULL,
address_id int(11) NOT NULL,
status_id tinyint(4) NOT NULL,
total_price decimal(10,2) DEFAULT '0.00' NOT NULL,
shipping_id tinyint(4) NOT NULL,
cc_number varchar(16),
cc_exp_yr int,
cc_exp_mon int,
cc_type_code char(3),
create_dt timestamp,
PRIMARY KEY (order_id)
);
```

