

# 使用 PHP 构建简单的 ORM 系统

## 用户实体类

```php
<?php
namespace Entity;

class User
{
    private $id;
    private $firstName;
    private $lastName;
    private $gender;
    private $namePrefix;

    const GENDER_MALE = 0;
    const GENDER_FEMALE = 1;

    const GENDER_MALE_DISPLAY_VALUE = "Mr.";
    const GENDER_FEMALE_DISPLAY_VALUE = "Mrs.";

    public function assembleDisplayName()
    {
        $displayName = '';

        if ($this->gender == self::GENDER_MALE) {
            $displayName .= self::GENDER_MALE_DISPLAY_VALUE;
        } else if ($this->gender == self::GENDER_FEMALE) {
            $displayName .= self::GENDER_FEMALE_DISPLAY_VALUE;
        }

        if ($this->namePrefix) {
            $displayName .= ' ' . $this->namePrefix;
        }

        $displayName .= ' ' . $this->firstName . ' ' . $this->lastName;

        return $displayName;
    }

    public function setFirstName($firstName)
    {
        $this->firstName = $firstName;
    }

    public function getFirstName()
    {
        return $this->firstName;
    }

    public function setGender($gender)
    {
        $this->gender = $gender;
    }

    public function getGender()
    {
        return $this->gender;
    }

    public function setId($id)
    {
        $this->id = $id;
    }

    public function getId()
    {
        return $this->id;
    }

    public function setLastName($lastName)
    {
        $this->lastName = $lastName;
    }

    public function getLastName()
    {
        return $this->lastName;
    }

    public function setNamePrefix($namePrefix)
    {
        $this->namePrefix = $namePrefix;
    }

    public function getNamePrefix()
    {
        return $this->namePrefix;
    }
}
```

**Listing 1.1**

这里有趣的是方法 `assembleDisplayName()`。它根据用户的数据为用户创建“显示名称”。显示名称用于打印帖子的作者。代码

```php
<?php
include('../entity/User.php');

$user = new Entity\User();
$user->setFirstName('Max');
$user->setLastName('Mustermann');
$user->setGender(0);
$user->setNamePrefix('Prof. Dr');

echo $user->assembleDisplayName();
```

**Listing 1.2**

结果为

```
1 Mr. Prof. Dr. Max Mustermann
```

因此，方法 `assembleDisplayName()` 定义了 `User` 对象的特定行为。

如果用户的主数据从数据库中检索，则必须以一种方式进行转换，使上述行为附加到它上面。换句话说：从数据库中检索的用户主数据必须转换为 `User` 对象，因为在应用程序中，我们主要总是想要处理我们领域的对象，并通过简单调用其 `assembleDisplayName()` 方法来轻松创建用户的显示名称。让我们将此构建到我们的 ORM 工具中。

首先，我们设置数据库结构：

```sql
CREATE TABLE users(
	id int(10) NOT NULL auto_increment, 
	first_name varchar(50) NOT NULL,
	last_name varchar(50) NOT NULL, 
	gender ENUM('0','1') NOT NULL,
	name_prefix varchar(50) NOT NULL,
	PRIMARY KEY (id)
);
```

然后，让我们为“Max Mastermann”（顺便说一句，这是德国的“John Doe”）添加虚拟数据：

```sql
INSERT INTO users (first_name, last_name, gender, name_prefix)
VALUES('Max', 'Mustermann', '0', 'Prof. Dr.');
```

现在，如果我们想要从数据库重建 `User` 对象，可以这样做：

```php
<?php
include('../entity/User.php');

$db = new \PDO('mysql:host=localhost;dbname=app', 'root', '');
$userData = $db->query('SELECT * FROM users WHERE id = 1')->fetch();

$user = new Entity\User();
$user->setId($userData['id']);
$user->setFirstName($userData['first_name']);
$user->setLastName($userData['last_name']);
$user->setGender($userData['gender']);
$user->setNamePrefix($userData['name_prefix']);

echo $user->assembleDisplayName();
```

| ![information](images/leanpub_information.png) || 

#### 数据库凭据在生产系统中

在生产系统中，你使用强关键字并且不使用用户“root”，对吧？上面显示的代码只是一个示例 … |

| --- | --- |

通过这些代码行，我们开始实现自己的 ORM 系统，该系统允许通过从数据库获取数据来重建领域对象。让我们进一步改进它。

为了封装上面显示的“数据映射”，我们将代码移动到其自己的类中：

```php
<?php
namespace Mapper;

class User
{
	private $mapping = array(
		'id' => 'id',
		'firstName' => 'first_name',
		'lastName' => 'last_name',
		'gender' => 'gender',
		'namePrefix' => 'name_prefix'
	);

	public function populate($data, $user)
	{
		$mappingsFlipped = array_flip($this->mapping);

		foreach($data as $key => $value) {
			if(isset($mappingsFlipped[$key])) {
				call_user_func_array(
					array($user, 'set'. ucfirst($mappingsFlipped[$key])),
					array($value)
				);
			}
		}

		return $user;
	}
}
```

它并不完美，但能完成工作。现在，我们的调用代码看起来像这样：

```php
<?php
include_once('../entity/User.php');
include_once('../mapper/User.php');

$db = new \PDO('mysql:host=localhost;dbname=app', 'root', '');
$userData = $db->query('SELECT * FROM users WHERE id = 1')->fetch();

$user = new Entity\User();
$userMapper = new Mapper\User();
$user = $userMapper->populate($userData, $user);

echo $user->assembleDisplayName();
```

但是，我们可以通过将 SQL 语句移动到其自己的对象（即所谓的 *repository*）来使其更加简单：

```php
<?php
namespace Repository;

include_once('../entity/User.php');
include_once('../mapper/User.php');

use Mapper\User as UserMapper;
use Entity\User as UserEntity;

class User
{
	private $em;
	private $mapper;

	public function __construct($em)
	{
		$this->mapper = new UserMapper;
		$this->em = $em;
	}

	public function findOneById($id)
	{
		$userData = $this->em
			->query('SELECT * FROM users WHERE id = ' . $id)
			->fetch();
    
		return $this->mapper->populate($userData, new UserEntity());
	}
}
```

最后，我们将连接到数据库的代码移动到名为 `EntityManager` 的类中，并通过它使新的 `User` 仓库可用：

```php
<?php

include_once('../repository/User.php');

use Repository\User as UserRepository;

class EntityManager
{
	private $host;
	private $db;
	private $user;
	private $pwd;
	private $connection;
	private $userRepository;

	public function __construct($host, $db, $user, $pwd)
	{
		$this->host = $host;
		$this->user = $user;
		$this->pwd = $pwd;

		$this->connection = new \PDO(
			"mysql:host=$host;dbname=$db", 
			$user, 
			$pwd);

		$this->userRepository = null;
	}

	public function query($stmt)
	{
		return $this->connection->query($stmt);
	}

	public function getUserRepository()
	{
		if (!is_null($this->userRepository)) {
			return $this->userRepository;
		} else {
			$this->userRepository = new UserRepository($this);
			return $this->userRepository;
		}
	}
}
```

实体管理器现在充当主入口点——它打开数据库连接并使数据库查询可用于客户端代码。重构后，结果仍然保持不变：

```
1 Mr. Prof. Dr. Max Mustermann
```

