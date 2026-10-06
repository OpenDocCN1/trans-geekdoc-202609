

# 第三部分：使用 PHP 实战

此外，请注意 Member 的 `joinDate` 字段被设置了：

```php
"joinDate" => date("Y-m-d")
```

PHP 的 `date()` 函数用于生成一个格式为 YYYY-MM-DD 的当前日期字符串。该字符串随后被存储在 `joinDate` 字段中，反映成员已完成注册。

你可以在第 16 章找到更多关于 `date()` 的信息。

现在 Member 已经创建并填充了提交的表单，脚本会对数据进行各种检查。首先，它会遍历必填字段列表；如果任何字段未填写，其名称将被添加到 `$missingFields` 数组中：

```php
foreach ($requiredFields as $requiredField) {
    if (!$Member->getValue($requiredField)) {
        $missingFields[] = $requiredField;
    }
}
```

如果遇到任何缺失字段，将向 `$errorMessages` 数组添加相应的错误消息：

```php
if ($errorMessages) {
    $errorMessages[] = '<p class="error">您提交的表单中缺少某些字段。请填写下方高亮的字段并点击“详情”以重新提交表单。</p>';
}
```

如果密码字段不匹配，或者用户名或邮箱地址已被占用，也会生成错误消息。对于用户名检查，会带用户名调用 `Member::getUsername()`；如果它返回一个 `Member` 对象，脚本就会知道该用户名已被占用并生成错误消息。同样，对于邮箱地址，会调用 `Member::getByEmailAddress()` 来确定输入的邮箱地址是否存在于数据库中。

最后，如果没有提出任何错误，脚本将调用 `displayForm` 向用户显示表单，并传入错误列表、缺失字段列表（如果有）以及包含用户输入数据的填充 `Member` 对象，以便重新显示表单。另一方面，如果提交的数据正确，将通过调用 `Member` 对象的 `insert()` 方法将成员记录记录在 `members` 表中：

```php
if ($errorMessages) {
    displayForm($errorMessages, $missingFields, $member);
} else {
    $member->insert();
    displayThanks();
}
```

脚本中的最后一个函数 `displayThanks()` 仅仅是向注册的成员显示一条感谢信息。

# 第 14 章：使用 PHP 纵 MySQL 数据

## 测试应用程序

一旦你创建了 `register.php` 脚本，打开 Web 浏览器并输入脚本的 URL 来测试注册流程。尝试在表单中输入几个值并提交，看看会发生什么。图 14-1 显示了脚本运行的情况；在这个示例中，用户忘记输入他们的邮箱地址。注意脚本如何提示他们重新输入密码（在表单中重新显示已输入的密码永远不是个好主意）。

![](img/ede05b7b77968b82cbd9a513122fb183_454_0.png)

图 14-1

你现在扩展了你的书俱乐部应用程序，允许新成员加入俱乐部。在此过程中，你学习了如何使用 PHP 和 PDO 向 `members` 表中添加新的成员记录。

## 创建成员区域

现在成员可以注册你的书俱乐部了，你将为他们在你的网站内提供一个成员区域，他们可以用它来查看即将进行的活动、查看当前阅读列表等。就本章而言，你的成员区域将只包含几个虚拟页面，但希望当你读完这一章时，你已经掌握了在需要时为成员区域添加一些真实世界功能的技能。

成员需要登录成员区域，因此你将创建一个脚本让他们执行此操作。该过程涉及显示一个登录表单，请求他们的用户名和密码。当你提交表单时，你会将他们的详细信息与 `members` 表中的记录进行比对。如果匹配，你将显示一个欢迎页面欢迎他们进入成员区域；否则，你将提示他们检查登录详情并重试。

同样，你将创建一个脚本允许成员从成员区域退出。你将包含代码来检查他们是否确实已登录，如果没有，则将他们重定向到登录页面。同时，你将增强 `LogEntry` 类，以便应用程序可以将成员区域内的访问情况记录到 `accessLog` 数据库表。。

##为 Member 类添加身份验证方法

首要任务。为了让成员能够登录成员区域，你需要在 `Member` 类中添加一个方法，检查提供的用户名和密码以确保它们是正确的。该脚本将被登录脚本使用，并在他们登录时通过 `authenticate()` 方法进行身份验证。

打开你的 `Member.class.php` 文件，在类的末尾、`insert()` 方法之后添加 `authenticate()` 方法：

```php
public function authenticate() {
    $conn = $this->connect();
    $sql = "SELECT * FROM TBL_MEMBERS WHERE username = :username\nAND password = :password";

    try {
        $stmt = $conn->prepare($sql);
        $stmt->bindValue("username", $this->data['username'], PDO::PARAM_STR);
        $stmt->bindValue("password", $this->data['password'], PDO::PARAM_STR);
        $stmt->execute();
        $row = $stmt->fetch();
        parent::disconnect($conn);
        if ($row) return new Member($row);
    } catch (PDOException $e) {
        parent::disconnect($conn);
        die("Query failed: " . $e->getMessage());
    }
}
```

该方法获取存储在对象 `username` 和 `password` 字段中的用户名和密码，并在 `members` 表中查找记录。注意，对象中存储的密码需要加密，以便能与表中的密码进行比较。如果找到记录，则返回一个 `Member` 对象。否则不返回任何内容。

## 增强 LogEntry 类以记录页面访问

每当成员查看成员区域内的页面时，你都会在 `accessLog` 表记录该事件。为此，你需要为 `LogEntry` 类添加一个方法。打开 `LogEntry.php` 文件，在类的末尾、`getEntries()` 方法之后添加以下 `record()` 方法：

```php
public function record() {
    $conn = parent::connect();
    $sql = "SELECT * FROM TBL_ACCESS_LOG WHERE memberId = :memberId\nAND pageUrl = :pageUrl";

    try {
        $stmt = $conn->prepare($sql);
        $stmt->bindValue(":memberId", $this->data["memberId"], PDO::PARAM_INT);
        $stmt->bindValue(":pageUrl", $this->data["pageUrl"], PDO::PARAM_STR);
        $stmt->execute();

        if ($stmt = $stmt->fetch()) {
            $sql = "UPDATE TBL_ACCESS_LOG SET numVisits = numVisits + 1\nWHERE memberId = :memberId AND pageUrl = :pageUrl";
            $stmt = $conn->prepare($sql);
            $stmt->bindValue(":memberId", $this->data["memberId"], PDO::PARAM_INT);
            $stmt->bindValue(":pageUrl", $this->data["pageUrl"], PDO::PARAM_STR);
            $stmt->execute();
        } else {
            $sql = "INSERT INTO TBL_ACCESS_LOG (memberId, pageUrl, numVisits) VALUES (:memberId, :pageUrl, 1)";
            $stmt = $conn->prepare($sql);
            $stmt->bindValue(":memberId", $this->data["memberId"], PDO::PARAM_INT);
            $stmt->bindValue(":pageUrl", $this->data["pageUrl"], PDO::PARAM_STR);
            $stmt->execute();
        }
    } catch (PDOException $e) {
        parent::disconnect();
        die("Query failed: " . $e->getMessage());
    }
}
```

