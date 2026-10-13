
`prints` 表中的所有列都是必需的，除了 `size` 和 `description` 字段。`artist_id`、`print_name` 和 `price` 字段上都有索引，每个字段都可能在查询中使用。

每个印刷品将与一张图片关联。图片将存储在服务器上，文件名与 `print_id` 相同。在 Web 浏览器中显示图片时，将使用其原始名称，因此该名称需要存储在该表中。

您可以向该表添加 `in_stock` 或 `qty_on_hand` 字段，以指示产品的可用性。

**4.** 创建 `customers` 表 ![Image](graphics/circle-d.jpg)：

```
CREATE TABLE customers (

customer_id INT UNSIGNED NOT NULL AUTO_INCREMENT,

email VARCHAR(60) NOT NULL,

pass CHAR(40) NOT NULL,

PRIMARY KEY (customer_id),

UNIQUE (email), INDEX login (email, pass)

) ENGINE=MyISAM;
```

![Image](graphics/19_figure_04_d.jpg)

![Image](graphics/circle-d.jpg) 创建 `customers` 表的基础版本。在真正的电子商务网站中，您需要扩展此表以存储更多信息。

这是用于创建 `customers` 表的代码。您可以加入其他合适的字段（姓名、地址、电话号码、注册日期等）。由于本章不会使用这些值——甚至完全不涉及用户管理——因此将其省略。

**5.** 创建 `orders` 表 ![Image](graphics/circle-e.jpg)：

```
CREATE TABLE orders (

order_id INT UNSIGNED NOT NULL AUTO_INCREMENT,

customer_id INT UNSIGNED NOT NULL,

total DECIMAL(10,2) UNSIGNED NOT NULL,

order_date TIMESTAMP,

PRIMARY KEY (order_id),

INDEX (customer_id),

INDEX (order_date)

) ENGINE=InnoDB;
```

![Image](graphics/19_figure_05_e.jpg)

![Image](graphics/circle-e.jpg) 创建 `orders` 表。

`orders` 表的所有字段都是必需的，并创建了三个索引。请注意，此处的外键列（如 `customer_id`）与其对应的主键（`customers` 表中的 `customer_id`）类型完全相同。`order_date` 字段将存储订单录入的日期和时间。由于被定义为 `TIMESTAMP`，当插入记录时，它将自动被赋予当前值（因此它不需要正式声明为 `NOT NULL`）。

最后，因为事务将用于 `orders` 和 `order_contents` 表，所以两者都必须使用 InnoDB 存储引擎。

**6.** 创建 `order_contents` 表 ![Image](graphics/circle-f.jpg)：

```
CREATE TABLE order_contents (

oc_id INT UNSIGNED NOT NULL AUTO_INCREMENT,

order_id INT UNSIGNED NOT NULL,

print_id INT UNSIGNED NOT NULL,

quantity TINYINT UNSIGNED NOT NULL DEFAULT 1,

price DECIMAL(6,2) UNSIGNED NOT NULL,

ship_date DATETIME DEFAULT NULL,

PRIMARY KEY (oc_id),

INDEX (order_id),

INDEX (print_id),

INDEX (ship_date)

) ENGINE=InnoDB;
```

![Image](graphics/19_figure_06_f.jpg)

![Image](graphics/circle-f.jpg) 为 `ecommerce` 数据库创建最后一张表。

为了拥有规范化的数据库结构，每个订单被分离为其通用信息——客户、订单日期和总金额——以及其具体信息——实际订购的商品及其数量。该表具有指向 `orders` 和 `prints` 表的外键。`quantity` 有一个设定的默认值 1。`ship_date` 被定义为 `DATETIME`，以便它可以拥有 `NULL` 值，表示该商品尚未发货。同样，此表必须使用 InnoDB 存储引擎才能参与事务。

您可能会好奇，为什么此表要存储商品价格，而该信息已存在于 `prints` 表中。原因很简单：产品价格可能会变动。`prints` 表指示商品的当前价格；`order_contents` 表指示商品的购买价格。

***

提示

根据网站销售的内容，底层数据库将用不同的表来替代 `artists` 和 `prints`。任何电子商务数据库最重要的属性是存在一个“产品”表，该表列出正在销售的单个商品，并为每个商品关联一个产品 ID。因此，一件大号红色 polo 衫将拥有一个 ID，这与大号蓝色 polo 衫的 ID 不同，后者又与中号蓝色 polo 衫的 ID 不同。如果没有唯一的、单独的产品标识符，将无法跟踪订单和产品数量。

***

***

提示

如果您想为用户存储多个地址——家庭、账单、朋友等——请创建一个单独的地址表。在该表中存储所有这些信息，包括地址类型，并使用客户 ID 作为主外键将这些记录关联回 `customers` 表。

***

***

### 安全性

就电子商务网站而言，有四大安全考量。第一是数据如何存储在服务器上。您需要保护 MySQL 数据库本身（通过设置适当的访问权限）以及存储会话信息的目录（有关可更改的设置，请参见[第 12 章](#ch12.html#ch12)“[Cookie 和会话](#ch12.html#ch12)”）。就这些问题而言，使用非共享主机托管肯定能提高您网站的安全性。

第二个安全考量涉及保护对敏感信息的访问。网站的管理端（具有查看订单和客户记录的能力）必须得到最高级别的保护。这意味着要求进行身份验证才能访问，限制知晓访问信息的人员，使用安全连接，等等。

第三个因素是保护传输过程中的数据。当客户进入结账流程（涉及信用卡和送货信息）时，*必须*使用安全交易。为此需要在服务器上建立带有有效证书的安全套接字层 (SSL)，然后切换到 `https://` URL。还要注意通过电子邮件发送的信息，因为这些消息通常不通过安全途径传输。

第四个问题涉及支付信息的处理。您**真的、真的、真的、真的（真的！）**不希望以任何方式保留这些信息。理想情况下，让第三方资源处理支付，使您的网站名正言顺地“两袖清风”。我在本章末尾的一个名为“结账流程”的侧边栏中对此进行了一些讨论。

这个广泛的电子商务主题，包含大量具体细节和大量真实代码，在我的著作 *Effortless E-Commerce with PHP and MySQL*（New Riders, 2011）中得到了详尽阐述。

***

### 管理端

电子商务应用的管理端主要用于管理三大核心组件：

• 产品（待售商品）

• 客户

• 订单

在本章中，您将创建两个脚本用于向目录添加产品。由于待售产品是艺术品，一个脚本将用于填充 `artists` 表，第二个脚本将用于填充 `prints` 表（该表具有指向 `artists` 的外键）。

受篇幅限制，且由于没有支付系统，这无论如何都不是一个完整的电子商务示例，因此本章无法详述客户和订单方面的内容。然而，客户管理与用户管理相同，已在上一章中介绍，您将看到许多关于订单管理的建议。
