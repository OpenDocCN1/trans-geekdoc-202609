

因此，你的第一个目标是创建客户联系报告，并为销售人员配备完整的登录和通知功能。完成联系报告并完成第一次迭代后，你将从以下几个方面看到估计的效果如何：

- 相互之间
- 与你的原始估计相比
- 与时间或你每周的点数相比

每次迭代结束时，你需要后退一步，衡量进度，获取客户的反馈，并根据客户不断变化的需求和目标调整计划。不要太担心；此过程旨在灵活且能响应你和你的客户的需求。

到目前为止，你已经学会了如何将问题空间划分为用户定义的故事，以及如何创建故事并将其拆分为更多故事，或合并为大小大致相同的更少数量的故事。故事估算是一个持续的过程，反馈（例如相关的尖峰）将有助于解决技术问题。

与客户合作确定对他们最重要的事情非常重要，并且要就每个请求功能的难度向他们提供诚实的反馈。这样可以让你做出更好、更及时的估计。这也能让客户看到系统的实际运行情况，并就系统的当前状态做出明智的决策。

## 开始工作

现在，你和你的客户确切地知道第一次迭代（即客户联系报告）中将实现什么：

- 故事 9：身份验证和授权，4 点
- 故事 1：客户联系报告，3 点
- 故事 6：销售经理通知，3 点
- 故事 8：邮件室通知，2 点

## 概述故事 9 的详细信息

> “每个销售人员都需要有自己的私有登录。”

首先，这假设“销售人员”作为一个逻辑实体存在（不一定是 PHP 类，至少目前不是），因此让我们概述它的需求。

存在对基本可读用户信息的需求：

```
First Name
Last Name
```

是的，你既是名字也是数字：
员工 ID

由于用户必须登录系统，让我们允许他或她选择登录名和密码：

登录名
登录密码

你还需要知道该人员访问系统时的角色。虽然一个人的角色可能与职位相关，但职位往往是短暂的。此外，你必须确定三种角色之一：销售人员、会计师或销售经理。

公司角色

这引发了一些好问题。某人是否可以同时身兼多职？某人既可以是会计师又可以是销售经理吗？那销售人员和销售经理呢？温迪回答说：“可能不行；韦德和埃德温娜的职责不重叠。”探头看向韦德整洁的隔间证实了你的假设，给埃德温娜打电话也是如此。因此，角色是互斥的。

由于你负责身份验证，让我们决定如何使用系统。

## 编写测试

问自己几个问题：

- [ ] 你希望如何启用登录？
- [ ] 登录应该用于什么目的？应该是简单的身份验证吗？
- [ ] 谁应该使用登录功能？

你知道用户包含什么：

员工 ID
名
姓
公司角色

你还知道身份验证需要什么：

登录名
登录密码

回忆第 12 章中的 HTTPSession 类。现在不用去查找它；你现在不需要它——但这与两个尚未定义的类 WidgetSession 和 WidgetUser 一起使用是一个合理的选择：

```
<?php
$session = new WidgetSession(); // inherited from HTTPSession
$session->impress();
// authentication
$session->login("ed","12345");
if ($session->isLoggedIn() == false) exit;
$user = $session->getUser(); // returns WidgetUser
print $user->first_name;
print $user->last_name;
print $user->email;
// authorization
print $user->role;
print $user->isSalesPerson();
print $user->isSalesManager();
print $user->isAccountant();
?>
```

请记住，前面的代码片段只是“一种合理的场景”。它尚未成为正式的测试或可运行的代码。这仅仅是你脑海中关于使用新类的设想。当你对这种“假设”场景感到满意时，你会在测试中正式化其使用。让我们继续编写一些测试！

## PHPUnit

这里的想法是编写测试，以模拟你计划使用与当前故事相关的软件的方式。这被称为测试驱动开发，除了开发优势之外，你最终还会获得一套出色的测试。你在第 13 章查看应用程序架构时第一次接触到它。希望你仍然安装了 PHPUnit。

> 以你将要使用应用程序的相同方式进行测试，迫使你查看函数或对象并确定参数和其他元素。
> 这可以避免创建未使用的功能，或在错误的位置使用功能。

与“束缚你的手脚”恰恰相反，拥有一套测试为你提供了很大的自由度，因为你可以立即知道通过添加新功能或修改现有代码是否意外破坏了系统的遥远部分。

以下是一些旨在反映常见使用场景的新测试。将以下内容保存为 test.widgetsession.php：

```
<?php
require_once ("widgetsession.php3");
require_once ("lib/phpunit/phpunit.php");
class TestWidgetSession extends TestCase {
private $_session;
function setUp() {
$dsn = array ('phptype' => "pgsql", 'hostspec' => "localhost",
		'database' => "widgetworld",
		'username' => "wuser",
		'password' => "foobar");
	$this->_session = new WidgetSession($dsn, true);
}

function testValidLogin() {
	$this->_session->login("ed", "12345");
	$this->assertEquals(true, $this->_session->isLoggedIn());
}

function testInvalidLogin() {
	$this->_session->login("ed", "54321"); // fail
	$this->assertEquals(false, $this->_session->isLoggedIn());
}

function testUser() {
	$user = $this->_session->getUser();
	$this->assertEquals("Lecky-Thompson", $user->last_name);
	$this->assertEquals("Ed", $user->first_name);
	$this->assertEquals("ed@lecky-thompson.com", $user->email);
}

function testAuthorization () {
	$user = $this->_session->getUser();
	$this->assertEquals("Sales Person", $user->role);
	$this->assertEquals(true, $user->isSalesPerson());
	$this->assertEquals(false, $user->isSalesManager());
	$this->assertEquals(false, $user->isAccountant());
}
}

$suite = new TestSuite;
$suite->addTest(new TestWidgetSession("testValidLogin"));
$suite->addTest(new TestWidgetSession("testInvalidLogin"));
$suite->addTest(new TestWidgetSession("testUser"));
$suite->addTest(new TestWidgetSession("testAuthorization"));
$testRunner = new TestRunner();
$testRunner->run( $suite );
?>
```

但是，运行前面的代码时，你会得到以下错误：

找不到类 'WidgetSession'，位于 test.widgetsession.php 第 16 行

目前，让我们模拟适当的虚拟 WidgetSession 和 WidgetUser 类，以便测试至少可以运行。将以下代码插入 test.widgetsession.php 前一个列表的顶部：

```
class WidgetSession {
    public function __construct($one, $two) {}
    public function login() {}
    public function isLoggedIn() { return null; }
    public function getUser() {
        return new WidgetUser();
    }
}

class WidgetUser {
    public $first_name = "";
    public $last_name = "";
    public $email = "";

    public function isSalesPerson() { return null; }
    public function isSalesManager() { return null; }
    public function isAccountant() { return null; }
}
```

现在在 test.widgetsession.php 中再次运行测试。以下是 PHPUnit 的相应输出：

```
TestWidgetSession - testValidLogin FAIL
TestWidgetSession - testInvalidLogin FAIL
TestWidgetSession - testUser FAIL
TestWidgetSession - testAuthorization FAIL
4 tests run.
9 failures.
0 errors.
Failures
1. testValidLogin
   true type:boolean
   null type:NULL
2. testInvalidLogin
   false type:boolean
   null type:NULL
3. testUser
   Lecky-Thompson type:string
   type:string
4. testUser
   Ed type:string
   type:string
5. testUser
   ed@lecky-thompson.com type:string
   type:string
6. testAuthorization
   Sales Person type:string
   type:string
7. testAuthorization
   true type:boolean
   null type:NULL
```

