
## 实用缓存

现在你已经看到了 PECL/memcached 提供的众多操作，了解如何修改一个简单的基于数据库的类以利用缓存将会很有用。首先要考虑的是你想要缓存什么数据。缓存数据与数据库或其他持久存储中的数据必须保持多大的匹配度？它是可以延迟缓存或从缓存复制到持久存储的数据，还是必须在没有缓存未命中风险的情况下读取，或写入时只要数据库有数据写入就同时缓存？这些问题将决定你在应用程序中如何构建缓存层——而应用程序的性质和功能需求很可能在很大程度上提供这些问题的答案。

另一件需要考虑的是你希望对缓存项的键使用什么类型的值。最重要的是它要有意义——保持简单！对键进行分类或组织的一种方法是使用某种命名空间。在本例中，键将由数据库表名作为键的第一部分组成，用冒号分隔，然后是存储项的唯一 ID——在本例中为用户 ID。

以下示例非常简单，是一种标准的读穿和写穿缓存示例。它包含一个 User 对象。这是一个你实例化的对象。如果在实例化时提供用户 ID，则使用该 ID 从数据库检索用户数据，然后将每个 User 类属性设置为检索到的数据，这些数据可通过类的 get 和 set 方法访问。所需的是一个缓存层。这将在多个地方实现：

> 你可以使用作者随源代码提供的程序运行本节中展示的代码片段。

- 在检索用户数据时检查缓存。如果数据在缓存中，则使用从缓存检索到的数据设置用户属性。无需检查数据库，可以继续。如果数据不在缓存中，则从数据库检索它，然后缓存检索到的数据。

> 你不想缓存数据库的原始结果集。你希望以某种即用形式缓存数据。在本例中，使用关联数组。

- 每当向数据库插入或更新数据时写入缓存。
- 如果用户从数据库中删除，则从缓存中删除。

在以下示例中，为清晰起见，添加缓存逻辑的代码以粗体显示。第一个方法当然是构造函数。构造函数接受两个参数——用户 ID（$uid）或用户名。最初，类仅通过私有类成员 $dbh 建立了对数据库的连接。如粗体所示，为添加缓存，创建了到 memcached 的连接句柄（成员 $memc）。这是各种方法用于缓存的连接。

```php
require "globals.php";

class User {
    static $userAttribs = array(
        'uid',
        'username',
        'firstname',
        'lastname',
        'password',
        'email',
        'address',
        'city',
        'state',
        'age',
        'zip',
    );

    private $dbh, $memc;

    private $uid, $username, $firstname, $lastname, $password, $email,
        $address, $city, $state, $age;

    private $_user_loaded;

    public function __construct( $uid = 0, $username = '' ) {

        $this->uid = intval($uid);
        $this->username = $username;

        // database connection
        $this->dbh = new mysqli($MYSQL_HOST, $MYSQL_USER, $MYSQL_PASS, $SCHEMA);

        // handle error connecting
        if (mysqli_connect_errno() != 0) {
            printf("Can't connect to MySQL Server. Errorcode: %s\n",
                mysqli_connect_error());
            exit;
        }

        if (!$this->dbh) {
            printf("Can't connect to MySQL Server. Errorcode: %s\n",
                mysqli_connect_error());
            exit;
        }

        // memcached server pool connection
        $serverlist = $MEMCACHED_SERVER_LIST;

        // set the memc private member
        $this->memc = new Memcached();
    }
}
```

```php
$this->memc->AddServers($serverlist);

// this loads the user data for the instantiated class to be able to use
$this->load();
}
```

代码片段 User.php 和 user_client.php

load() 方法由构造函数调用，因此使用给定的用户 ID 或用户名进行实例化将导致实例化的 User 对象的各种用户属性（私有属性，列在静态数组 $userAttribs 中）被设置为给定用户的数据，可通过 get 和 set 方法访问（本示例中未显示）。对 load() 的更改只是简单地添加一个条件，检查用户数据是否在 memcached 中找到，如果是，则方法返回而无需访问数据库。如果数据未在 memcached 中找到，则必须从数据库检索它，然后缓存到 memcached 中。这是一个读穿缓存。

```php
public function load() {
    // if the user data has been loaded, no need to do so again
    if ( $this->_user_loaded ) {
        return true;
    }

    // get the UID from the database
    if (! $this->uid) {
        $this->uid = $this->uidFromName($this->username);
    }
    // still no UID, this is a new user
    if (! $this->uid) {
        $this->loadNewUser( $this->username);
    }

    // if user is in cache
    if ( ! $this->getFromCache() ) {
        // if user wasn't in DB, return false
        if (! $this->getFromDB()) {
            // not in database nor memcached, return false, no such user exists
            return false;
        }
        // if user was in DB, read-through cache
    } else {
        $this->setToCache();
        return true;
    }
    return true;
}
```

save() 方法同时处理新用户的插入和现有用户的更新。此处实现的缓存是一个非常简单的写穿缓存，通过 setToCache() 方法实现：

```php
public function save() {
    if ($this->uid) {
        $this->update();
    }
}
```

```php
else {
    $this->insert();
}
// write to cache, regardless (write-through)
$this->setToCache();
}
```

由于数据库删除所需的代码很少，因此向此数据库方法添加 deleteFromCache() 方法调用同样简单。

```php
/*
 * delete existing user object from the database
 */
function delete () {

    $this->load();

    $delete = 'DELETE FROM users WHERE uid = ?';

    $sth = $this->dbh->prepare($delete);
    $sth->bind_param('i', $this->uid);

    $sth->execute();

    $rows = $sth->affected_rows;

    $sth->close();

    // delete from cache
    $this->deleteFromCache();

    return $rows ? true: false;
}
```

接下来展示缓存方法。getFromCache() 方法 simply 从 memcached 中检索给定键 $key 的序列化数组，然后遍历每个属性，将类属性设置为从检索到的数组中获取的值：

```php
private function getFromCache() {
    $key = "user:$this->uid";
    $user = $this->memc->get($key);
    if ($user) {
        // set object attribs from $user fetched
        foreach (self::$userAttribs as $attrib) {
            print "$attrib $user[$attrib]\n";
            $this->$attrib = $user[$attrib];
        }
        $this->_user_loaded  = true;
        return true;
    }
    else {
        return false;
    }
}
```

setToCache() 方法对每个属性执行与 getToCache() 类似的循环，不同之处在于要序列化的数组的值被设置为类属性的值，然后使用 $key 指定的键将数组序列化后存储：

```php
private function setToCache() {
    $key = "user:$this->uid";
    $user = array();
    // set $user array with each attrib for object
    foreach (self::$userAttribs as $attrib) {
        $user[$attrib] = $this->$attrib;
    }

    // use return value of set
    return ($this->memc->set($key, $user));
}
```

deleteFromCache() 方法是一个极其简单的方法，它从 memcached 中删除给定键 $key 的项：

```php
private function deleteFromCache() {
    $key = "user:$this->uid";
    // use return value of set
    return ($this->memc->delete($key));
}
```

现在，一个简单的程序来验证这个类是否工作。此外，如果你运行 memcached -vvv，并 tail MySQL 查询日志，你可以看到数据正在从 memcached 和 MySQL 适当写入和检索：

```php
<?php

require "User.php";

// instantiate with uid 12345
$user = new User(12345);

print "age: " . $user->getAge() . "\n";
print "email: " . $user->getEmail() . "\n";
print "current address: " . $user->getAddress() . "\n";
print "city: " . $user->getCity() . "\n";
print "state: " . $user->getState() . "\n";
print "zip: " . $user->getZip() . "\n";

// change email address
$user->setEmail("patg@northscale.com");

// why not shave off a decade or so?!
$user->setAge(30);

// move to Portsmouth, NH
$user->setCity("Portsmouth");
$user->setAddress("33 Concord St.");
```
