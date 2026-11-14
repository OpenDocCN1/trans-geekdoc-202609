
使用高级集成方法（AIM）时需要这四个项目。第一个指示正在使用的 AIM 版本。第二个说明返回的响应数据应当是分隔的。第三个规定要使用的分隔字符（这里是竖线）。relay_response 由 Authorize.net 的 SIM 系统使用，因此对于 AIM 连接应将其设置为 false（这是 Authorize.net 的建议）。

### 5. 指示交易方法:

```
$data['x_method'] = 'CC';
```

方法值 CC 表示这是一笔信用卡交易。另一种选择是 ECHECK。

### 6. 添加订单信息:

```
$data['x_amount'] = $Order_total;
$data['x_invoice_num'] = $Order_id;
$data['x_cust_id'] = $Customer_id;
```

金额值显然是其中最重要的之一。发票号和客户 ID 值不是必需的，但提供它们后，该信息将存储在 Authorize.net 系统中，从而方便在此站点相关订单上查询该处的信息。

对于这些值中的每一个，都将使用在 billing.php 中创建的变量。在第 11 章中，将调用同一脚本，但这三个值将来自在管理脚本中定义的变量。

### 7. 将数据转换为一系列 name=value 键值对:

```
$post_string = '';
foreach($data as $k => $v) {
  $post_string .= "$k=". urlencode($v) ."&";
}
$post_string = rtrim($post_string, '& ');
```

使用 foreach 循环，$data 中的每个元素将转换为 name=value 格式。每个值都经过 URL 编码，以便在请求中安全使用，每个 name=value 对之间用与号分隔。最后一步会去掉末尾的与号。结果将是类似这样的字符串：

```
x_type=AUTH_ONLY&x_card_num=455610523894&x_exp_date=
062010&x_card_code=890&x_first_name=Larry&x_last_name=
Ullman&x_address=100+Main+Street+Apt+2B&x_state=NH
&x_city=Anytown&x_zip=65894&x_login=75sq9Q9qHEP8
&x_tran_key=7r83Sb4HUd58Tz5p&version=3.1&x_delim_data=
TRUE&x_delim_char=%7C&x_relay_response=FALSE&x_method=
CC&x_amount=309.82&x_invoice_num=21&x_cust_id=27
```

### 8. 设置 cURL 请求:

```
$request = curl_init(GATEWAY_API_URL);
curl_setopt($request, CURLOPT_HEADER, 0);
curl_setopt($request, CURLOPT_RETURNTRANSFER, 1);
curl_setopt($request, CURLOPT_POSTFIELDS, $post_string);
curl_setopt($request, CURLOPT_SSL_VERIFYPEER, FALSE);
```

第一行初始化一个 cURL 请求，并提供要通信的 URL。第二行表示响应中应省略标头信息（只需要数据）。第三行，将 CURLOPT_RETURNTRANSFER 设置为 1，确认应将实际数据作为响应返回。在第四行中，$post_string 数据作为 CURLOPT_POSTFIELDS 添加。

有关 cURL 选项的完整列表，请参见 www.php.net/curl_setopt。

在最后一行中，禁用了验证服务器 SSL 连接的选项。这样做可以提高连接成功的几率。如果不包含此行且 cURL 在网关证书的有效性上出现问题，请求将失败。这并不意味着交易不安全，只是更有可能成功。

### 9. 执行 cURL 请求:

```
$response = curl_exec($request);
curl_close($request);
```

### 10. 将响应转换为数组:

```
$response_array = explode($data["x_delim_char"], $post_response);
```

cURL 响应将作为一长串数据返回。为了更易于使用，可以通过在分隔字符（之前设置为竖线）上拆分字符串将其转换为数组。

### 11. 保存文件。

同样，未使用结束 PHP 标记。

## 检查服务器响应

在更新账单脚本以使用网关脚本之前，让我们快速查看一下 Authorize.net 响应。使用 AIM 时，服务器响应将是以下格式的一长串数据（实际分隔符由您选择）：

```
1l1l11This transaction has been approved.ljUUAmIY1239ol ..
```

因为数组从零开始索引，表 10.1 从零开始列出字段。

对该响应应用 explode() 函数后，字符串将被拆分为数组。该数组中的前 68 个元素保留给 Authorize.net 用途；大多数元素没有值。表 10.1 列出了其中的许多字段。

### 表 10.1 一些 Authorize.net 响应字段

| 字段 | 名称 |
|---|---|
| 0 | 响应代码 |
| 1 | 响应子代码 |
| 2 | 响应原因代码 |
| 3 | 响应原因文本 |
| 4 | 授权代码 |
| 5 | AVS 响应 |
| 6 | 事务 ID |
| 7 | 发票号 |
| 8 | 描述 |
| 9 | 金额 |
| 10 | 方法 |
| 11 | 事务类型 |
| 12 | 客户 ID |
| 13–31 | 客户信息 |
| 38 | CCV/CVV 响应代码 |
| 50 | 卡号后四位 |
| 51 | 卡片类型 |

完整的明细可在 Authorize.net 手册中找到。其中最重要的是 *响应代码*。可能的值为：

- 已批准
- 被拒绝
- 错误
- 审核中

简而言之，如果响应返回的第一个元素值为 1，则付款已获授权。如果不是 1，则发生了问题。具体问题类型将由 *响应原因代码* 和 *响应原因文本* 反映。同样，Authorize.net AIM 手册和在线文档列出了所有可能的代码和消息。

## 更新 billing.php

既然两个与支付相关的脚本已编写完成，应将其合并到 billing.php 中。通过包含这两个脚本，将处理支付事务。之后，事务应记录到数据库中，脚本应相应响应（图 10.14 中的项目 4）。

- 1. 如果尚未打开，请在文本编辑器或 IDE 中打开 billing.php。

- 2. 在 isset($_SESSION['order_id']) IF-ELSE 之后，检查是否设置了订单 ID 和总额:

```
if (isset($Order_id, $Order_total)) {
```

应在该行之前的 IF-ELSE 条件语句通过从会话中检索或执行存储过程来创建这两个变量。只要这两个变量都存在，就可以处理付款请求。

- 3. 将客户 ID 值赋给变量:

```
$Customer_id = $_SESSION['customer_id'];
```

客户 ID 当前存储在会话中，但 gateway_process.php 期望它位于名为 $Customer_id 的变量中。（我这样编写是因为另一个也使用 gateway_process.php 的管理脚本不会在会话中拥有客户 ID。）

- 4. 包含两个脚本:

```
require_once(BASE_URI . 'gateway_setup.php');
require_once(BASE_URI . 'gateway_process.php');
```

脚本必须按此顺序包含。第一个脚本建立 $data 数组，并用针对特定事务类型的一些信息填充它。第二个脚本向 $data 添加更多信息，然后联系 Authorize.net。

您需要更改对脚本的引用，以便路径与您的设置准确匹配。

- 5. 将 addslashes 添加到两个文本字段中:

```
$reason = addslashes($response_array[3]);
$response = addslashes($response);
```

原因文本和完整响应可能包含有问题的字符（即单引号），因此在将这些值用于存储过程之前需要应用 addslashes()。

- 6. 在数据库中记录事务:

```
$r = mysqli_query($dbc, "CALL add_transaction($order_id,
 '${$data['x_type']}', $response_array[9], $response_array[0], 'Reason',
 $response_array[6], '$response')");
```

要在数据库中记录事务，请调用 add_transaction() 存储过程。其第一个参数是订单 ID。第二个是事务类型。第三个是涉及的金额，可在 $response_array[9]（或 $order_total）中找到。第四个参数是响应代码。该值为 1、2、3 或 4，是解析后的 $response_array 中的第一个元素。下一个参数是事务 ID。这是由 Authorize.net 返回的、反映其系统中该事务的值。最后，完整的 cURL 响应作为字符串存储在表中。诚然，该响应包含所有这些其他信息，但以一种不易访问的方式。

- 7. 如果交易成功，将响应代码存储在会话中:

```
if ($response_array[0] == 1) {
$_SESSION['response_code'] = $response_array[0];
}
```

该值将由流程中的最后一个脚本所需。

- 8. 重定向用户:

```
$location = 'https://' . BASE_URL . 'final.php';
header("Location: $location");
exit();
```

final.php 脚本是结账流程中的最后一页。它应向客户指示成功、发送电子邮件、创建收据，等等。

- 9. 如果交易不成功，请相应响应:

```
} else {
if ($response_array[0] == 2) { // Declined
$message = $response_array[3] . 'Please fix the error or try another
card.';
} elseif ($response_array[0] == 3) { // Error
$message = $response_array[3] . 'Please fix the error or try
another card.';
} elseif ($response_array[0] == 4) { // Held for review
$message = "The transaction is being held for review. You
will be contacted ASAP about your order. We apologize for any
inconvenience.";
}
}
```

