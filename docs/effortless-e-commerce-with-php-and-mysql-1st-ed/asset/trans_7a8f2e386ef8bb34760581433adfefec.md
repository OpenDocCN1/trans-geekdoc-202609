

## 添加产品

当客户请求将产品添加到购物车时，将调用 `add_to_cart()` 存储过程。该过程需要获取四个信息——唯一用户 ID、产品类型（`coffee` 或 `other`）、产品 ID 和要添加的数量。作为额外的逻辑，如果产品尚未存在于购物车中，则该过程应将其 `add` 到购物车；如果产品已在购物车中，则应 `add` 更多数量的产品。以下是该存储过程，我将在随后解释其逻辑：

```
DELIMITER $$
CREATE PROCEDURE add_to_cart (uid CHAR(32), type VARCHAR(6), pid MEDIUMINT, qty TINYINT)
BEGIN
DECLARE cid INT;
SELECT id INTO cid FROM carts WHERE user_session_id=uid AND
product_type=type AND product_id=pid;
IF cid > 0 THEN
UPDATE SET quantity=quantity+qty, date_modified=NOW()
WHERE id=cid;
ELSE
INSERT INTO carts (user_session_id, product_type, product_id,
quantity) VALUES (uid, type, pid, qty);
END IF;
END$$
DELIMITER ;
```

> 有关在数据库中创建存储过程的说明，请参见第 8 章。

> 您可以从 www.DMCInsights.com/ecom/ 下载本项目的所有 SQL 和文件。

首先，与存储过程的创建方式保持一致，分隔符立即更改为两个美元符号的组合。接下来，创建过程的 `signature`，即其名称和参数的组合。第一个参数是用户的会话 ID，长度将正好为 32 个字符。接下来是产品类型，长度为五或六个字符（`other` 或 `coffee`）。最后两个参数是产品的 ID 和要添加的数量。

> 分隔符只需更改为分号以外的内容即可。

为了加入检查产品是否已在购物车中的逻辑，需要一个内部变量。可以使用 `DECLARE` 创建一个变量，后跟变量名及其 MySQL 数据类型。创建名为 `cid` 的变量，即 `cart ID` 的缩写。

接下来，`SELECT` 查询会检查 `carts` 表中的提交产品。如果产品已在表中表示，则其 `id` 值将赋给 `cid` 变量，得益于 `SELECT...INTO` 语法。

**查询** 查询之后，IF-ELSE 条件语句将根据 cid 的值运行 **更新** 或 **插入** 查询。如果 cid 大于零，则产品已在表中，应将提交的数量添加到现有数量中。否则，将插入新记录。仅对 **更新** 查询将 **修改日期** 列更新为当前时刻。

> **提示**
> 传递给存储过程的参数可以在查询内部使用，仿佛查询是预处理语句，这意味着字符串不需要加引号。

## 移除产品

从购物车中移除产品的存储过程是四个过程中最简单的一个。它需要 **添加到购物车()** 使用的四个参数中的三个（显然，移除物品时无需指定数量）。该过程仅运行一个 **删除** 查询：

```
DELIMITER $$
CREATE PROCEDURE remove_from_cart (uid CHAR(32), type VARCHAR(6),
    pid MEDIUMINT)
BEGIN
    DELETE FROM carts WHERE user_session_id=uid AND product_type=type
    AND product_id=pid;
END$$
DELIMITER ;
```

## 更新购物车

> **提示**
> 网站提供两种从购物车中移除商品的方式：点击链接和将数量输入为零。

用户点击购物车页面上的更新按钮后（图 9.1），将调用用于更新购物车的存储过程。该过程采用与 **添加到购物车()** 相同的四个参数，但无需确认产品已存在于数据库中（除非用户使用了某种技巧，否则产品必须存在才能出现在购物车表单中）。然而，如果用户将商品的数量设为零，则该过程应直接将其从购物车中移除。与其将移除功能写入此过程，不如在数量为零时让该过程调用已经定义好的 remove_from_cart() 过程。

```
DELIMITER $$
CREATE PROCEDURE update_cart (uid CHAR(32), type VARCHAR(6), pid MEDIUMINT, qty TINYINT)
BEGIN
	If qty > 0 THEN
		UPDATE carts SET quantity=qty, date_modified=NOW() WHERE
		user_session_id=uid AND product_type=type AND product_id=pid;
	ELSEIF qty = 0 THEN
		CALL remove_from_cart (uid, type, pid);
	END IF;
END$$
DELIMITER ;
```

> 只要 carts 或 wish_lists 表中商品的数量发生变化（未移除商品），该商品的 修改日期 值也会随之更新。

## 获取购物车内容

第四个也是最后一个存储过程（针对购物车）会运行一个 SELECT 查询，以检索购物车的所有内容。此 SELECT 查询有多复杂，取决于您想显示多少信息，但就其基本形式而言，该查询与第 8 章中与销售相关的查询非常相似。该查询是两个 SELECT 语句的 UNION：第一个是四个表的 JOIN，第二个是五个表的 JOIN。在过程中，我将查询分成了多行以提高清晰度。此过程只需要用户的会话 ID 作为参数。

```
DELIMITER $$
CREATE PROCEDURE get_shopping_cart_contents (uid CHAR(32))
BEGIN
	SELECT CONCAT("O", ncp.id) AS sku, c.quantity, ncc.category,
	ncp.name, ncp.price, ncp.stock, sales.price AS sale_price
	FROM carts AS c
	INNER JOIN non_coffee_products AS ncp ON c.product_id=ncp.id
	INNER JOIN non_coffee_categories AS ncc ON ncc.id=ncp.non_coffee_category_id
	LEFT OUTER JOIN sales ON
	(sales.product_id=ncp.id AND sales.product_type='other' AND
	((NOW() BETWEEN sales.start_date AND sales.end_date) OR (NOW() >
	sales.start_date AND sales.end_date IS NULL))) )
	WHERE c.product_type="other" AND c.user_session_id=uid
	UNION
SELECT CONCAT("C", sc.id), c.quantity, gc.category,
CONCAT_WS(" - ", s.size, sc.caf_decaf, sc.ground_whole), sc.price,
sc.stock, sales.price
FROM carts AS c
INNER JOIN specific_coffees AS sc ON c.product_id=sc.id
INNER JOIN sizes AS S ON s.id=sc.size_id
INNER JOIN general_coffees AS gc ON gc.id=sc.general_coffee_id
LEFT OUTER JOIN sales ON
(sales.product_id=sc.id AND sales.product_type='coffee' AND
((NOW() BETWEEN sales.start_date AND sales.end_date) OR (NOW() >
sales.start_date AND sales.end_date IS NULL)))
WHERE c.product_type="coffee" AND c.user_session_id=uid;
END$$
DELIMITER ;
```

图 9.1

![](img/4f47e47c67bd619ac73250f11c9fc7ce_248_0.png)

图 9.2 显示调用此过程的结果。您会发现，该查询返回默认价格（标题为 _价格_）、库存数量以及促销价格（如有）。此信息将在稍后用到。

![](img/4f47e47c67bd619ac73250f11c9fc7ce_250_0.png)

图 9.2

## 定义辅助函数

在深入购物车本身之前，本章代码中有两个辅助函数会很有用。第一个函数接受两个可能的价格——常规价格和促销价格——并返回产品的适当价格：

```
function get_just_price($regular, $sales) {
if ((0 < $sales) && ($sales < $regular)) {
return number_format($sales, 2);
} else {
return number_format($regular, 2);
}
}
```

这与第 8 章中已定义的 get_price() 函数类似，但仅返回数字价格（get_price() 返回的是特定上下文中的价格）。

第二个函数将解析 SKU，即将类似 C12 的值转换为对应的 coffee 和 12。这种转换通常很有必要，因为数据库分别使用每个产品的类型和 ID 号。解析 SKU 的函数接受一个参数——SKU 本身——并返回一个包含两个元素的数组：

```
function parse_sku($sku) {
// Grab the first character:
$type_abbr = substr($sku, 0, 1);

// Grab the remaining characters:
$pid = substr($sku, 1);

// Validate the type:
if ($type_abbr == 'C') {
$sp_type = 'coffee';
} elseif ($type_abbr == 'O') {
$sp_type = 'other';
} else {
$sp_type = NULL;
}

// Validate the product ID:
$pid = (filter_var($pid, FILTER_VALIDATE_INT, array('min_range' => 1)))
? $pid : NULL;

// Return the values:
return array($sp_type, $pid);
} // End of parse_sku() function.
```

substr() 的两次调用将 SKU 拆分为各个部分。接下来，根据 SKU 的第一个字符验证产品类型，该字符必须是 C（表示 coffee）或 O（表示 other）。如果都不是，则将 $sp_type 变量赋值为 NULL。

其余字符必须是大于 1 的整数。filter_var() 函数可以进行此测试。如果该值是大于 1 的整数，则将其赋给 $pid。否则，将赋值 NULL。

