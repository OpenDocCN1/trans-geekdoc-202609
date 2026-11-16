


```php
if ($request[$index] != "") {
array_push (
$this->items,
new TravelExpenseItem (
array ('emp_id' => $this->emp_id,
'expense_date' =>
$this->addDays($this->week_start, $daynum),
'description' => $description,
'amount' => (float) $request[$index]),
$this->dbh));
})
}
```

```php
/**
* This function bridges the gap between the day-based DB and the
* week-based view
*/
public function parse(&$request) {
foreach ($this->getExpensesMetaArray() as $sectionlist) {
for ($i=0; $i < count ($sectionlist['persist']); $i++) {
$daynum = 0;
foreach ($this->getWeekArray() as $day) {
$index = $sectionlist['code'].".".$day.".".$i;
$this->createByRequest (
$sectionlist['persist'][$i], $daynum,
$index, $request);
$daynum++;
}
}
}
// arg, mitr is an exception
$daynum = 0;
foreach ($this->getWeekArray() as $day) {
$this->createByRequest ("trans_miles_traveled", $daynum,
"mitr_".$day, $request);
$daynum++;
}
}
```

一个新的函数 TravelExpenseWeek->createByRequest() 让你免于代码重复，因为它在正常处理和里程计算中都会被调用。

所有测试都通过了，你的客户很满意，屏幕也能正常工作。现在你已完成用户故事 4：“差旅费报告作为电子表格”，如图 19-10 所示。

## Widget 世界

## 差旅费报告

员工姓名：Ed Lecky-Thompson	部门：sales
编号：1	起始周：2004 07 04
工作区域：worked

| | 周日 | 周一 | 周二 | 周三 | 周四 | 周五 | 周六 | 总计 |
|---|---|---|---|---|---|---|---|---|
| 住宿 | | | | | | | | |
| 住宿与酒店 | 1.00 | 2.00 | 3.00 | | | | | 6 |
| 其他 | 2.00 | | | | | | | 2 |
| 小费 | 3.00 | | | | | | | 3 |
| 住宿合计 | 6 | 2 | 3 | 0 | 0 | 0 | 0 | 11 |
| 餐饮 | | | | | | | | |
| 早餐 | 4.00 | | | | | | | 4 |
| 午餐与小吃 | 5.00 | | | | | | | 5 |
| 晚餐 | 6.00 | | | | | | | 6 |
| 小费 | 7.00 | | | | | | | 7 |
| 娱乐 | 8.00 | | | | | | | 8 |
| 餐饮合计 | 30 | 0 | 0 | 0 | 0 | 0 | 0 | 30 |
| 交通 | | | | | | | | |
| 机票 | 9.00 | | | | | | | 9 |
| 汽车租赁 | 10.00 | | | | | | | 10 |
| 车辆维护/汽油 | 11.00 | | | | | | | 11 |
| 当地交通 | 12.00 | | | | | | | 12 |
| 过路费/停车费 | 13.00 | | | | | | | 13 |
| 交通小计 | 55 | 0 | 0 | 0 | 0 | 0 | 0 | 55 |
| 行驶里程数 | 19.00 | | | | | | | 19 |
| 每英里 0.36 的里程费 | 6.84 | 0 | 0 | 0 | 0 | 0 | 0 | 6.84 |
| 交通总计 | 61.84 | 0 | 0 | 0 | 0 | 0 | 0 | 61.84 |
| 杂项 | | | | | | | | |
| 礼品 | 14.00 | | | | | | | 14 |
| 电话与传真 | 15.00 | | | | | | | 15 |
| 办公用品 | 16.00 | | | | | | | 16 |
| 邮费 | 17.00 | | | | | | | 17 |
| 其他 | 18.00 | | | | | | | 18 |
| 杂项合计 | 80 | 0 | 0 | 0 | 0 | 0 | 0 | 80 |

小计 182.84
减去预付现金 20.00
应付员工 162.04
应付公司

重新计算

评论：评论

保存报告

## 图 19-10: 作为电子表格的差旅费报告

现在，不再是“仅仅工作”，你拥有一个经过良好测试的系统和一个能够演化的框架的开端。

你已经了解 PHP、JavaScript 和浏览器如何（以及如何不）交互，每个如何负责其层，以及如何在它们之间移动信息。创建类似电子表格的复杂行为，虽然不容易，但可以用相对较少的代码完成。

接下来你要去哪里？只是机械地完成剩余的用户故事？继续读下去，因为还有另一个重要教训需要学习。

## 模拟对象

有时在测试期间，你必须与一个确定性对象交互，但出于各种原因，你在测试环境中无法访问它。例如，考虑以下情况：

- 实际对象是非确定性的，例如实时股票或天气数据馈送。
- 实际对象对于你的测试套件来说太慢，例如负载过高的事务生产数据库。
- 你需要测试异常情况，例如入侵警报或系统宕机。
- 实际对象不存在。这可以从无法访问所需对象到必要的对象内部功能的任何事情。

基本上，模拟对象是一个伪装出足够功能或所需功能的对象，以便你能够完全测试你的系统。

例如，如果你想测试会话超时、错误或恶意破解，你可能会导入 mock-widgetsession.php，它包含以下内容：

```
class MockWidgetSession extends WidgetSession {
    public function getUserObject() {
        return new WidgetUser(
            array (
                'id' => 1,
                'username' => 'ed',
                'md5_pw' => '827ccb0eea8a706c4c34a16891f84e7b',
                'first_name' => "Ed",
                'last_name' => "Lecky-Thompson",
                'email' => "ed@lecky-thompson.com",
                'role' => "s",
                'department' => "sales"));
    }
}
```

不论编码细节，这个 MockWidgetSession 示例将使你的测试环境能够出于任何你需要的原因模拟登录。

Smarty 也可以用于模拟 HTML 屏幕。除了将 HTML 显示到屏幕上，你还可以将 HTML 保存在变量中，并随意处理。

例如，用户故事 6 需要销售经理通知，因此你只需在保存联系人时向经理发送电子邮件。听起来很简单，但你面临着希望在多大程度上进行测试的问题，特别是他们希望电子邮件内容包含输入屏幕的 HTML。

获取屏幕 HTML 不是问题。基本上，你必须测试浏览器输出，这很好，因为直到现在你还没有测试过浏览器看到的内容。为了端到端的完整性，以下测试将使用正则表达式引用 HTML 输出：

```
function testContactEmail () {
    $u = new WidgetUser(
        array ('id' => 1,
            'username' => "ed",
            'first_name' => "Ed",
            'last_name' => "Lecky-Thompson",
            'email' => "ed@lecky-thompson.com",
            'role' => "s",
            'department' => "sales"));
    $cv = new ContactVisit (
        array ('emp_id' => "1",
            'week_start' => "1980-01-01",
            'company_name' => "test one",
            'contact_name' => "Big One",
            'city' => "Columbus",
            'state' => "OH",
            'accomplishments' => "phone call",
            'followup' => "",
            'literature_request' => ""));
    $c = new Contact (
        array ("emp_id" => "1",
            "week_start" => "1980-01-01",
            "shop_calls" => 2,
            "distributor_calls" => 3,
            "engineer_calls" => 4,
            "mileage" => 50,
            "territory_worked" => "Central Ohio",
            "territory_comments" => "Buckeyes are great. "),
        $this->_session->getDatabaseHandle()));
}
```

```
list ($email, $from, $subject, $message, $headers) =
    generateContactEmail($u, $c, array ($cv), false);
```

```
// test screen capture, requires 7bit ascii encoding (read: none)
```

```
$this->assertEquals(1, preg_match ("/Employee Name.........Ed Lecky-Thompson/", $message), "employee name");
$this->assertEquals(1, preg_match("/company_name_0........................test one/", $message), "company name");
$this->assertEquals(1, preg_match ("/shop_calls........................./", $message), "shop calls");
$this->assertEquals(1, preg_match ("/To: ed@lecky-thompson.com/", $headers), "email");
```

```
// test base64 encoding
list ($email_from, $subject, $message, $headers) =
           generateContactEmail($u, $c, array ($cv));
```

```
$this->assertEquals(0, preg_match ("/Employee Name................Ed Lecky-Thompson/", $message), "employee name");
$this->assertEquals(1, preg_match ("/To: ed@lecky-thompson.com/", $headers), "email");
```

如果你要手动输入上述代码，请确保不要在正则表达式中间换行；它们应该在一行中输入。

generateContactEmail() 函数旨在返回 PHP mail() 函数所需的内容：mail($email_address, $subject, $message, $headers);。

在这个示例中，你正在测试浏览器看到的内容。你不是测试 100% 的 HTML 输出，而是确保表单包含你期望的信息。因此，简单的正则表达式

```
"/Employee Name............Ed Lecky-Thompson/"
```

将完美匹配以下生成的 HTML：

```
<tr><td><b>Employee Name:</b></td><td>Ed Lecky-Thompson</td>
<td><b>Department:</b></td><td>sales</td></tr>
```

由于 base64 编码人类无法读取，base64 编码的测试仅检查电子邮件标题中是否存在电子邮件地址，而不是员工姓名，因为员工姓名（在消息中且经过 base64 编码）通常无法读取。

以下是可能放置在你的 lib/common-functions.php 中的函数：

```
function mimeifyContent ($content, $mime_boundary,
           $filename, $flagBase64=true) {
$message = "";
$message .= " \r\n";
$message .= "--".$mime_boundary."\r\n";
$message .= "Content-Type: text/html;\r\n";
$message .= "name=\"".$filename.".html\"\r\n\r\n";
// default is 7bit ascii

if ($flagBase64) {
    $message .= "Content-Transfer-Encoding: base64\r\n";
}

$message .= "Content-Disposition: attachment;\r\n";
$message .= " filename=\"".$filename.".html\"\r\n";
$message .= "\r\n";
if ($flagBase64) {     $message .= base64_encode($content);
} else {
    $message .= $content;
}
```


