

## 创建“添加到愿望单”链接

对网站可以做的一个简单改动是在产品旁边包含 *添加到愿望单* 链接，就像 *加入购物车* 链接一样。

按照当前编写的 wishlist.php 脚本，您只需创建一个“add”操作条件，就像 cart.php 中的那样。

## 运输替代方案

运输，就像选择支付处理器本身一样，是一个如此庞大的主题，我完全可以花整整一章来讨论处理订单这部分的各种方法。最简单但显然也不是最好的处理运输方式就是根本不收取任何额外费用：只需在每件商品的售价中包含足够的利润来覆盖运费即可。采用这种方式的网站将面临失去业务的风险，因为其他网站对同一商品表面收费更低，尽管这些网站稍后会加上运费。此外，这种方法不允许提供不同的运输选项（例如送货速度），也不便于随着时间的推移轻松调整运费。

此处实现的第二种最简单的计算运输方式是：根据订单总额按比例收取费用。这种方法易于管理、易于修改，对商家和客户来说都很合理。

要根据订单重量计算运费，您需要修改数据库，以便将商品重量与其他产品详细信息一起记录。取决于您销售什么，最好将所有重量都用相同的单位表示：克、千克、盎司、磅，等等。然后购物车需要检索每个产品的重量，生成重量总和，然后使用总重量计算运费。

类似地，您可以在数据库中创建一个代表额外运费的列。这可以是添加到特定产品表（相应地为 non_coffee_products 和 specific_coffees）中的一列，在这种情况下，预期会有大量 NULL 值，这并不理想。或者，您可以创建一个新表，将每个具有额外运费的产品表示为一行：

```sql
CREATE TABLE `extra_shipping` (
  `id` INT UNSIGNED NOT NULL AUTO_INCREMENT,
  `product_type` ENUM('coffee','other') NOT NULL,
  `product_id` MEDIUMINT UNSIGNED NOT NULL,
  `extra_charge` DECIMAL(4,2) UNSIGNED NOT NULL,
  `date_created` TIMESTAMP NOT NULL DEFAULT CURRENT_TIMESTAMP,
  `date_modified` TIMESTAMP NOT NULL DEFAULT '0000-00-00 00:00:00',
  PRIMARY KEY (`id`),
  KEY `product_type` (`product_type`, `product_id`),
) ENGINE=MyISAM DEFAULT CHARSET=utf8;
```

不幸的是，这意味着许多 SELECT 查询中都需要连接另一个表。

计算运费最复杂的方式是基于距离（以及可能的重量或尺寸）。要实现这一点，您需要客户的邮政编码，对于国际订单，还需要国家。然后，您将与所选承运商开发的系统对接。例如，UPS 和 FedEx 都提供应用程序编程接口 (API)，您可以通过这些接口根据距离、重量、尺寸和送货速度获得精确的运费。这些 API 与支付网关 API 的工作方式非常相似。有关更多信息，请参阅您所选承运商的文档。

## 改进购物车显示

网站的成功在一定程度上取决于用户对购物车的反应。如果购物车界面友好、吸引人，并让客户感到舒适，他们就更有可能完成购买。考虑到这一点，您可能愿意投入一些精力来改进该界面。例如，您可能应该考虑从购物车中的产品创建指向网站上产品图片和描述的链接。客户通常喜欢能够重新查看他们正在购买的商品。

其次，您可以在购物车页面添加消息，以指示最新操作的结果。消息可以简单到像“购物车已更新。”这样，也可以具体到像“马克杯：红龙已从您的购物车中移除。”这样。要做到这一点，HTML 视图文件需要检查并显示消息：

```php
if ($message) echo $message;
```

然后 PHP 脚本会为每个操作给 $message 赋值。如果您想按名称引用特定产品，还需要创建一个存储过程，用于检索给定产品类型和 ID 的产品信息。在执行 INSERT、UPDATE 或 DELETE 查询后，可以调用此类存储过程。

> 在 *nix 系统上，可以使用 cron 自动定期执行 PHP 脚本。此类脚本可用于执行维护操作。

## 调整数据库

网站的基础是数据库，因此我不提一下那里的替代方案就不太合适了。首先，当前编写的系统会产生大量“碎片”：永远不会被购买的愿望单和购物车项目。您可能需要创建一个 PHP（或命令行）脚本，定期清理数据库中的旧数据。如果记录的修改日期超过（比如说）六个月，或者其创建日期超过六个月且修改日期仍为 0000-00-00 00:00:00（表示该记录从未被更新），则该记录视为旧记录。

其次，如果您正在使用存储过程并喜欢它们的工作方式，您可能应该阅读有关如何在存储过程中处理错误的内容。虽然这并不难做，但该主题足够庞大且技术性强，以至于我不得不将其从书中省略，以免分散对更重要内容的注意力。

最后，您可以通过利用 VIEW 表从数据库中获得更好的性能。VIEW 表是一条已保存的 SELECT 查询，您可以像操作真实表一样在其上运行其他查询。创建 VIEW 的语法是：

```sql
CREATE VIEW view_name AS <SELECT QUERY>
```

例如，用于检索每个购物车或愿望单项目的存储过程中使用的 UNION 查询非常耗费资源。您可以创建一个执行所有 JOIN 操作的 VIEW，实际上将数据库表中的 product_type 和 product_id 值替换为您想要在 Web 浏览器中显示的实际信息。该视图还将存储关联的用户会话 ID 值。

```sql
CREATE VIEW cart_view AS
SELECT user_session_id, CONCAT("O", ncp.id) AS sku, c.quantity,
ncc.category, ncp.name, ncp.price, ncp.stock, sales.price AS sale_price
FROM carts AS c INNER JOIN non_coffee_products AS ncp ON
c.product_id=ncp.id INNER JOIN non_coffee_categories AS ncc ON
ncc.id=ncp.non_coffee_category_id LEFT OUTER JOIN sales ON (
sales.product_id=ncp.id AND sales.product_type='other' AND ((NOW())
BETWEEN sales.start_date AND sales.end_date) OR (NOW() >
sales.start_date AND sales.end_date IS NULL))) WHERE
c.product_type="other" UNION SELECT user_session_id,
CONCAT("C", sc.id), c.quantity, gc.category, CONCAT_WS(" - ", s.size,
sc.caf_decaf, sc.ground_whole), sc.price, sc.stock, sales.price FROM
carts AS c INNER JOIN specific_coffees AS sc ON c.product_id=sc.id
INNER JOIN sizes AS s ON s.id=sc_size_id INNER JOIN general_coffees
AS gc ON gc.id=sc.general_coffee_id LEFT OUTER JOIN sales ON
(sales.product_id=sc.id AND sales.product_type='coffee' AND ((NOW()
BETWEEN sales.start_date AND sales.end_date) OR (NOW()) >
sales.start_date AND sales.end_date IS NULL))) WHERE
c.product_type="coffee";
```

确切地说，SELECT...UNION...SELECT 查询与 get_shopping_cart_contents() 存储过程中的查询相同，只是 user_session_id 值现在是选择的一部分，而不是 WHERE 条件的一部分。图 9.11 显示了在这个 VIEW 表上运行的两个 SELECT 查询，后者会自动反映 carts 表中的变化（由客户操作引起）。

![](img/4f47e47c67bd619ac73250f11c9fc7ce_399_0.png)

图 9.11

定义此视图后，get_shopping_cart_contents() 查询只需对这一个表执行 SELECT，且只有一个条件：匹配用户的会话 ID：

```sql
SELECT * FROM cart_views WHERE user_session_id=uid;
```

VIEW 表是在 MySQL 5.0 版本中添加的。

