

```php
'persist' => array('meals_breakfast', 'meals_lunch',
    'meals_dinner', 'meals_tips',
    'meals_entertainment')),
array('name' => 'Transportation', 'code' => 'trans', 'data' =>
    array('Airfare', 'Auto Rental', 'Auto Maint./Gas',
    'Local Transportation', 'Tolls/Parking'),
    'persist' => array ('trans_airfare',
    'trans_auto_rental', 'trans_auto_maint', 'trans_local',
    'trans_tolls', 'trans_miles_traveled')),
array('name' => 'Miscellaneous', 'code' => 'misc', 'data' =>
    array('Gifts', 'Telephone &amp; Fax', 'Supplies',
    'Postage', 'Other'),
    'persist' => array('misc_gifts', 'misc_phone',
    'misc_supplies', 'misc_postage', 'misc_other'))));
```

第一层是一个节数组，这意味着每个节都会有一个小计，并且每个节包含行项目。

每个节都有一个 data 数组（即人类可读的描述），以及其计算机对应项 `persist`（这可能是数据库中每个项目的名称）。关联数组中的 code 项存在的目的是为了自动创建每个节都必须计算的半语义 JavaScript 变量（例如，用于餐饮、住宿和交通的变量）。这个数据结构将是将 HTML、JavaScript 数学、数据库和 PHP 对象粘合在一起的部分胶水；它是你的路线图。

## 更多交通费周测试

从 PHP 的交通费表单响应到数据库是一个重要步骤。这就是你定义期望从页面接收的内容的地方。请记住，你需要一种方法来获取整个响应，并从中轻松创建 TravelExpenseItem。这似乎是 TravelExpenseWeek 容器的合适工作。

回想一下，确定每个单元格唯一值的命名约定是 lodging_sun_0，它代表“节”+“天”+“行项目”。由于描述相同列/行、垂直/水平、电子表格单元格关系的方法几乎无穷无尽，这个命名约定相当合适。

此外，你可以根据其节偏移量（lodging_sun_0 中的“0”）轻松确定你正在处理的水平行。天和行项目是不同类型，这是有原因的：为了你的理智。在不同维度中操作数据已经很困难了；跟踪哪个对哪个更困难，而记住它们基于什么是在找麻烦。在其他条件相同的情况下，lodging_sun_0 包含的语义信息比 lodging_0_0 更多。

这是解析请求的测试：

```php
function testTravelExpenseWeekContainerParseRequest() {
    $response = array ( 'lodging_sun_0' => "1.1",
        'meals_sun_0' => "2.2",
        'misc_sun_2' => "3.3",
        'lodging_mon_0' => "4.4",
        'meals_mon_0' => "5.5",
        'misc_mon_2' => "6.6",
        'lodging_tue_0' => "7.7",
        'meals_tue_0' => "8.8",
        'misc_tue_2' => "9.9" );
    $week = new TravelExpenseWeek (
        array ( 'emp_id' => "1",
            'week_start' => "1980-01-06" ));
    $week->parse($response);
    $this->assertEquals(1.1, $week->getExpenseAmount(0, 'lodging_and_hotel'));
    $this->assertEquals(2.2, $week->getExpenseAmount(0, 'meals_breakfast'));
    $this->assertEquals(3.3, $week->getExpenseAmount(0, 'misc_supplies'));
    $this->assertEquals(4.4, $week->getExpenseAmount(1, 'lodging_and_hotel'));
    $this->assertEquals(5.5, $week->getExpenseAmount(1, 'meals_breakfast'));
    $this->assertEquals(6.6, $week->getExpenseAmount(1, 'misc_supplies'));
    $this->assertEquals(7.7, $week->getExpenseAmount(2, 'lodging_and_hotel'));
    $this->assertEquals(8.8, $week->getExpenseAmount(2, 'meals_breakfast'));
    $this->assertEquals(9.9, $week->getExpenseAmount(2, 'misc_supplies')); }
```

$response 数组模拟了你将从表单输入接收到的内容，请记住，$response 的值和 persist 元值反映在你的路线图数据结构中。

为持久化容器再创建一个测试。它与交通费项目测试非常相似：

```php
function testTravelExpenseWeekContainerWrite () {
    $this->session->getDatabaseHandle()->query("delete FROM
        travel_expense_item WHERE emp_id = 1 and
        expense_date >= '1980-01-06' and expense_date
        <= '2001-09-15'");
    $response = array (
        'lodging_sun_0'=>"1.1",'meals_sun_0'=>"2.2",'misc_sun_2'=>"3.3",
        'lodging_mon_0'=>"4.4",'meals_mon_0'=>"5.5",'misc_mon_2'=>"6.6",
        'lodging_tue_0'=>"7.7",'meals_tue_0'=>"8.8",'misc_tue_2'=>"9.9" );
    $week = new TravelExpenseWeek (
        array ('emp_id' => "1",
            'week_start' => "1980-01-06",
            'territory_worked' => "Midwest",
            'comments' => "comment",
            'cash_advance' => "0",
            'mileage_rate' => "0.31"));
    $this->session->getDatabaseHandle();
    $week->readWeek();
    $this->assertEquals(1.1, (float)
        $week->getExpenseAmount(0, 'lodging_and_hotel'));
    $this->assertEquals(2.2, (float)
        $week->getExpenseAmount(0, 'meals_breakfast'));
    $this->assertEquals(3.3, (float)
        $week->getExpenseAmount(0, 'misc_supplies'));
    $this->assertEquals(4.4, (float)
        $week->getExpenseAmount(1, 'lodging_and_hotel'));
    $this->assertEquals(5.5, (float)
        $week->getExpenseAmount(1, 'meals_breakfast'));
    $this->assertEquals(6.6, (float)
        $week->getExpenseAmount(1, 'misc_supplies'));
    $this->assertEquals(7.7, (float)
        $week->getExpenseAmount(2, 'lodging_and_hotel'));
    $this->assertEquals(8.8, (float)
        $week->getExpenseAmount(2, 'meals_breakfast'));
    $this->assertEquals(9.9, (float)
        $week->getExpenseAmount(2, 'misc_supplies')); }
```

在这个测试中（作为额外方法添加到 test.widgetsession.php），TravelExpenseWeek 解析 $response，在 $week->persist() 中持久化 TravelExpenseItem，从数据库中重新读取 $week->readWeek()，并最终验证读取的内容。

请注意，这些测试大量使用了复制粘贴编程。保持整洁是一条通用规则，因此如果大多数测试需要相同的设置，请将它们放入设置中，但不要过早重构你的测试。你的测试通常是更改的第一个位置，因此它们应该易于阅读和修改。

## 满足交通费周测试

到现在，满足 TravelExpenseWeek 的有效性和持久性测试应该可以预见地很容易：

```php
class TravelExpenseWeek extends PersistableObject {
    public $items = array();

    function __construct($results, $dbh = null) {
        parent::__construct($results, $dbh);
    }

    public function isValid() {
        if ($this->isEmpty("emp_id") == true) return false;
        if ($this->isEmpty("week_start") == true) return false;
        if ($this->isEmpty("territory_worked") == true) return false;
        if ($this->isEmpty("mileage_rate") == true) return false;
        return true;
    }

    public function persist() {
        return $this->persistWork("travel_expense_week",
            array ( "emp_id",
                "week_start",
                "comments",
                "territory_worked",
                "cash_advance",
                "mileage_rate"));
    }

    public function getSqlWhere() {
        return " emp_id = ".$this->emp_id." and week_start = ".$this->week_start."";
    }

    public function parse(&$request) { }
    public function readWeek() { }
    public function getExpenseAmount($offset, $description) { }
}
```

parse、readWeek 和 getExpenseAmount 函数由 TravelExpenseWeekContainerParseRequest 和 TravelExpenseWeekContainerWrite 测试要求；因此，它们只是语法存根。

## 满足解析请求测试

TravelExpenseWeekContainerParseRequest 测试可能有点棘手，因为它涉及数据操作。你的首要任务是处理依赖项，这是你之前考虑过的元数组路线图的一部分。将此函数添加到 lib/expense.php 中的 TravelExpenseWeek 类将完成这项工作：

```php
public function getExpensesMetaArray () {
    return array(
        array('name' => 'Lodging', 'code' => 'lodging', 'data' =>
            array('Lodging &amp; Hotel','Other','Tips'), 'persist' =>
            array('lodging_amp_hotel', 'lodging_laundry',
            'lodging_tips')),
        array('name' => 'Meals', 'code' => 'meals', 'data' =>
            array('Breakfast', 'Lunch &amp; Snacks',
            'Dinner', 'Tips', 'Entertainment'), 'persist' =>
            array('meals_breakfast', 'meals_lunch',
            'meals_dinner', 'meals_tips',
            'meals_entertainment')),
        array('name' => 'Transportation', 'code' => 'trans', 'data' =>
            array('Airfare', 'Auto Rental', 'Auto Maint./Gas',
            'Local Transportation',
            'Tolls/Parking'), 'persist' =>
            array ('trans_airfare', 'trans_auto_rental',
            'trans_auto_maint', 'trans_local',
            'trans_tolls', 'trans_miles_traveled')),
        array('name' => 'Miscellaneous', 'code' => 'misc', 'data' =>
            array('Gifts', 'Telephone &amp; Fax', 'Supplies',
            'Postage', 'Other'), 'persist' =>
            array('misc_gifts', 'misc_phone',
            'misc_supplies', 'misc_postage',
            'misc_other')));
    }
}
```

