

最后，切换到包含本章代码的目录。现在你可以运行一个包含引导文件的单元测试，该测试还涉及自动加载和命名空间，步骤如下：

```php
phpunit -c tests_with_autoload/phpunit.xml
```

输出结果应如下所示：

![](img/39390f6d56c5a83b28db083a8bd5185c_540_0.png)

## 另请参阅...

- 关于编写 PHPUnit 测试套件的更多信息，请参阅此[文档页面](https://phpunit.de/manual/current/en/phpunit-book.html#organizing-tests.xml-configuration)。

## 生成虚假测试数据

测试和调试过程的一部分涉及引入逼真的测试数据。在某些情况下，特别是当测试数据库访问并生成基准测试时，需要大量的测试数据。实现这一点的一种方法是引入一个从网站抓取数据的过程，然后将这些数据组合成逼真但随机的组合，以便插入到数据库中。

### 如何操作...

1.  第一步是确定测试应用程序所需的数据。另一个需要考虑的问题是，该网站是否面向国际受众，还是市场主要来自单一国家？
2.  为了生成一致的虚假数据工具，将数据从其源转移到可用的数字格式至关重要。首选方案是一系列数据库表。另一种吸引力稍差的替代方案是 CSV 文件。
3.  你可能需要分阶段转换数据。例如，你可以从列出国家代码和国家名称的网页中提取数据到文本文件中。

| 代码 | 名称 | 代码 | 名称 | 代码 | 名称 |
| :--- | :--- | :--- | :--- | :--- | :--- |
| AJ | 阿富汗 | AM | 阿尔及利亚 | AN | 阿塞拜疆 |
| AL | 阿尔巴尼亚 | AM | 亚美尼亚 | AN | 安道尔 |
| AO | 安哥拉 | AR | 阿根廷 | AS | 澳大利亚 |
| AT | 阿什莫尔和卡特利特群岛 | AU | 奥地利 | AV | 安圭拉 |
| AX | 阿克罗蒂里 | AY | 南极洲 | BA | 巴林 |
| BB | 巴巴多斯 | BC | 博茨瓦纳 | BD | 百慕大 |
| BE | 比利时 | BF | 巴哈马 | BG | 孟加拉国 |
| BH | 伯利兹 | BK | 波斯尼亚和黑塞哥维那 | BL | 玻利维亚 |
| BM | 缅甸 | BN | 贝宁 | BO | 白俄罗斯 |
| BP | 所罗门群岛 | BR | 巴西 | BS | 英属印度 |
| BT | 不丹 | BU | 保加利亚 | BV | 布韦岛 |
| BX | 文莱 | BY | 布隆迪 | CA | 加拿大 |
| CB | 柬埔寨 | CD | 乍得 | CE | 斯里兰卡 |
| CF | 刚果 | CG | 刚果（民主共和国/扎伊尔） | CH | 中国 |
| CI | 智利 | CI | 开曼群岛 | CK | 库克群岛（基林群岛） |
| CM | 喀麦隆 | CN | 科摩罗 | CO | 哥伦比亚 |
| CR | 珊瑚海群岛 | CS | 哥斯达黎加 | CT | 中非共和国 |
| CU | 古巴 | CV | 佛得角 | CW | 库克群岛 |

4.  由于这个列表很短，可以将其直接剪切并粘贴到文本文件中。
5.  然后我们可以搜索 " " 并替换为 "\n"，这将给我们以下内容：

   1. AA 阿鲁巴
   2. AC 安提瓜和巴布达
   3. AE 阿拉伯联合酋长国
   4. AF 阿富汗
   5. AG 阿尔及利亚
   6. AJ 阿塞拜疆
   7. AL 阿尔巴尼亚
   8. AM 亚美尼亚
   9. AN 安道尔
   10. AO 安哥拉
   11. AR 阿根廷
   12. AS 澳大利亚
   13. AT 阿什莫尔和卡特利特群岛
   14. AU 奥地利
   15. AV 安圭拉
   16. AX 阿克罗蒂里
   17. AY 南极洲

6.  然后可以将其导入电子表格，进而让你导出为 CSV 文件。从那里，将其导入数据库只是件简单的事。例如，phpMyAdmin 就具备这样的功能。
7.  为了说明起见，我们假设我们生成的数据最终将存入 prospects 表中。以下是用于创建此表的 SQL 语句：

```sql
CREATE TABLE `prospects` (
  `id` int (11) NOT NULL AUTO_INCREMENT,
  `first_name` varchar (128) NOT NULL,
  `last_name` varchar (128) NOT NULL,
  `address` varchar (256) DEFAULT NULL,
  `city` varchar(64) DEFAULT NULL,
  `state_province` varchar(32) DEFAULT NULL,
  `postal_code` char(16) NOT NULL,
  `phone` varchar(16) NOT NULL,
  `country` char(2) NOT NULL,
  `email` varchar(250) NOT NULL,
  `status` char(8) DEFAULT NULL,
  `budget` decimal(10,2) DEFAULT NULL,
  `last_updated` datetime DEFAULT NULL,
  PRIMARY KEY (`id`),
  UNIQUE KEY `UNIQ_35730C0E67927C74` (`email`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```

8.  现在是创建能够生成虚假数据的类的时候了。然后，我们将创建方法为上面显示的每个字段生成数据，除了 id，它是自动生成的：

```php
namespace Application\Test;

use PDO;
use Exception;
use DateTime;
use DateInterval;
use PDOException;
use SplFileObject;
use InvalidArgumentsException;
use Application\Database\Connection;

class FakeData
{
    // 数据生成方法在此处
}
```

9.  接下来，我们定义将在过程中使用的常量和属性：

```php
const MAX_LOOKUPS   = 10;
const SOURCE_FILE   = 'file';
const SOURCE_TABLE  = 'table';
const SOURCE_METHOD = 'method';
const SOURCE_CALLBACK = 'callback';
const FILE_TYPE_CSV = 'csv';
const FILE_TYPE_TXT = 'txt';
const ERROR_DB      = 'ERROR: unable to read source table';
const ERROR_FILE    = 'ERROR: file not found';
const ERROR_COUNT   = 'ERROR: unable to ascertain count or ID column missing';

const ERROR_UPLOAD = 'ERROR: unable to upload file';
const ERROR_LOOKUP = 'ERROR: unable to find any IDs in the source table';

protected $connection;
protected $mapping;
protected $files;
protected $tables;
```

10. 然后我们定义用于生成随机字母、街道名称和电子邮件地址的属性。你可以将这些数组视为种子，可以根据需要对其进行修改和/或扩展。例如，你可能为法国受众替换巴黎的街道名称片段：

```php
protected $alpha = 'ABCDEFGHIJKLMNOPQRSTUVWXYZ';
protected $street1 = ['Amber','Blue','Bright','Broad','Burning','Cinder','Clear','Dewy','Dusty','Easy']; // 等等。
protected $street2 = ['Anchor','Apple','Autumn','Barn','Beacon','Bear','Berry','Blossom','Bluff','Cider','Cloud']; // 等等。
protected $street3 = ['Acres','Arbor','Avenue','Bank','Bend','Canyon','Circle','Street'];
protected $mail1 = ['northern','southern','eastern','western','fast','midland','central'];
protected $mail2 = ['telecom','telco','net','connect'];
protected $mail3 = ['com','net'];
```

11. 在构造函数中，我们接受一个用于数据库访问的 Connection 对象，以及一个映射到虚假数据的数组：

```php
public function __construct(Connection $conn, array $mapping)
{
    $this->connection = $conn;
    $this->mapping = $mapping;
}
```

12. 为了生成街道名称，与其尝试创建数据库表，使用一组种子数组来生成随机组合可能更高效。以下是这样做的示例：

```php
public function getAddress($entry)
{
    return random_int(1,999)
        . ' ' . $this->street1[array_rand($this->street1)]
        . ' ' . $this->street2[array_rand($this->street2)]
        . ' ' . $this->street3[array_rand($this->street3)];
}
```

13. 根据所需的真实程度，你还可以构建一个将邮政编码与城市匹配的数据库表。邮政编码也可以随机生成。以下是为英国生成邮政编码的示例：

```php
public function getPostalCode($entry, $pattern = 1)
{
    return $this->alpha[random_int(0,25)]
        .$this->alpha[random_int(0,25)]
        .random_int(1, 99)
        . ' '
        .random_int(1, 9)
        .$this->alpha[random_int(0,25)]
        .$this->alpha[random_int(0,25)];
}
```

14. 虚假电子邮件的生成也可以使用一组种子数组来产生随机结果。我们甚至可以编程使其接收现有的 $entry 数组，带有参数，并使用这些参数创建地址的名称部分：

```php
public function getEmail($entry, $params = NULL)
{
    $first = $entry[$params[0]] ?? $this->alpha[random_int(0,25)];
    $last = $entry[$params[1]] ?? $this->alpha[random_int(0,25)];
    return $first[0] . '.' . $last
        .'@'
        .$this->mail1[array_rand($this->mail1)]
        .$this->mail2[array_rand($this->mail2)]
        . '.'
        . $this->mail3[array_rand($this->mail3)];
}
```

15. 对于日期生成，一种方法是接受现有的 $entry 数组作为参数，带有参数。参数将是一个数组，其中第一个值是起始日期。第二个参数是从起始日期中减去的最大天数。这实际上允许你从一个范围内返回一个随机日期。注意，我们使用 `DateTime::sub()` 减去随机天数。`sub()` 需要一个 `DateInterval` 实例，我们使用 `P`、随机天数，然后使用 `'D':` 来构建它：

```php
public function getDate($entry, $params)
{
    list($fromDate, $maxDays) = $params;
    $date = new DateTime($fromDate);
    $date->sub(new DateInterval('P' . random_int(0, $maxDays) . 'D'));
    return $date->format('Y-m-d H:i:s');
}
```

