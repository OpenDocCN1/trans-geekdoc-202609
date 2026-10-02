
## 设置客户端行为

PECL/memcached 具有客户端行为函数，允许你设置和检索众多设置，这些设置决定了客户端的行为，例如分发、网络超时、序列化器、键的自动前缀、使用的哈希算法。你在连接之前设置这些行为或选项。你可以在 PHP 网站 http://us2.php.net/manual/en/memcached.constants.php 上找到你可以使用的众多选项。

以下示例展示了如何同时设置和检索一些客户端选项。在此例中，首先打印默认的分发方式（即 DISTRIBUTION_MODULA），然后将其更改为 DISTRIBUTION_CONSISTENT。接着将序列化器更改为使用 JSON 进行编码。服务器数组被存储然后检索。

```php
$memc = new Memcached();

// find out the current distribution type
$distribution = $memc->getOption(Memcached::OPT_DISTRIBUTION);

// since the value is numeric, set to a text value
$distribution = $distribution == Memcached::DISTRIBUTION_CONSISTENT ?
                "CONSISTENT, KETAMA": "MODULA";

echo "The distribution is currently: $distribution\n";

$memc->setOption(Memcached::OPT_DISTRIBUTION, Memcached::DISTRIBUTION_CONSISTENT);

$distribution = $memc->getOption(Memcached::OPT_DISTRIBUTION);
$distribution = $distribution == Memcached::DISTRIBUTION_CONSISTENT ?
                "CONSISTENT, KETAMA": "MODULA";

echo "The distribution is now set to: $distribution\n";

// a very cool feature is setting the serializer to JSON
$memc->setOption(Memcached::OPT_SERIALIZER, MEMCACHED_SERIALIZER_JSON);

# two servers in the pool
$servers = array (
    array ('192.168.1.106', 11211),
    array ('127.0.0.1', 11211)
);

# now add the servers
$memc->addServers($servers);
$memc->addServer('192.168.1.125', 11211);

// set a value
if ($memc->set('t1', $servers)) {
    // if true, success setting
    echo "t1 was set.\n";
}
else {
    // if false, failed to set
    echo "failed to set t1\n";
}

// now fetch t1
$t1= $memc->get('t1');

$result_code= $memc->getResultCode();
if ($result_code == Memcached::RES_SUCCESS) {
    print_r($t1);
}
elseif ($result_code == Memcached::RES_NOTFOUND) {
    print "t1 not found\n";
}
```

代码片段 memc_behaviors.php

只是为了看看将序列化器更改为使用 JSON 的效果，telnet 到缓存 t1 的 memcached 服务器的 11211 端口，你会看到它实际上是使用 JSON 序列化的！如果你的存储数据可以直接通过 JavaScript 在应用程序中获取和显示，这会非常有用。它还使得能够与其他组件或可能用其他语言编写的应用程序共享数据。

```
get t1
VALUE t1 4 95
a:2:
{i:0;i:a:2:{i:0;s:13:"192.168.1.106";i:1;i:1;i:11211;}
 i:1;a:2:{i:0;s:9:"127.0.0.1";i:1;i:1;i:11211;}}
END
```

## 放置和检索数据

现在你已经建立了 memcached 客户端连接，接下来要演示的是如何将数据缓存到 memcached 以及从 memcached 检索数据。在 memcached 中缓存项目时，值可以是字符串、数字，或序列化的 PHP 变量或对象。关于对象，PECL/memcached 会自动处理序列化——例如，如果你缓存一个 PHP 对象，比如数组。执行此操作的 Memcached 类方法有：

- **add:** 方法 `add()` 使用 `$key` 作为键添加给定项目，值为 `$value`，可选的整数 `$expiration`（秒）。方法 `addByKey()` 的第一个值为 `$server_key` 变量。这是一个你在代码中通用的任意字符串值，会导致项目被缓存到特定服务器，而不是使用分发算法。需要注意的是，你不能指定特定的服务器——为服务器键选择的服务器是一致性哈希的函数。此方法在你希望确保特定项目位于一台服务器上时很有用。可选的数值过期时间（以秒为单位）可由 `$expiration` 指定。成功时返回 true，失败时返回 false。add 操作失败包括服务器错误或尝试为已存在的键添加项目。

```php
public bool Memcached::add(
    string $key,
    mixed $value
    [, int $expiration ] )

public bool Memcached::addByKey(
    string $server_key,
    string $key,
    mixed $value
    [, int $expiration ] )
```

set: 方法 set() 会设置给定项目，无论其是否已存在，以 $key 为键，值为 $value，可选的过期时间为秒。方法 setByKey() 会将给定项目设置到由任意字符串值 $server_key 指定的特定服务器，无论其是否存在。

```php
public bool Memcached::set(
    string $key,
    mixed $value [, int $expiration ] )
```

```php
public bool Memcached::setByKey(
    string $server_key,
    string $key,
    mixed $value
    [, int $expiration ] )
```

replace: 方法 replace() 用 $value 的值替换以 $key 为键的现有项目的值。你可以指定一个可选的数值过期时间（以秒为单位）。方法 replaceByKey() 的第一个参数是你应用程序中指定的任意字符串值，以确保项目存储在特定服务器上。该方法在成功时返回 true，失败时返回 false。replace 操作可能的失败原因包括服务器错误或尝试替换不存在的项目。

```php
public bool Memcached::replace(
    string $key, mixed $value
    [, int $expiration ] )
```

```php
public bool Memcached::replaceByKey(
    string $server_key,
    string $key,
    mixed $value
    [, int $expiration ] )
```

get: 方法 get() 和 getByKey() 从 memcached 中为给定键获取项目。正如你所能假设的，getByKey() 允许你将服务器键指定为第一个参数。此外，就像 set* 方法自动序列化 PHP 对象一样，get 方法也会反序列化 PHP 对象。

```php
public mixed Memcached::get(
    string $key
    [, callback $cache_cb
    [, double &$cas_token ] ] )
```

```php
public mixed Memcached::getByKey(
    string $server_key,
    string $key
    [, callback $cache_cb
    [, double &$cas_token ]] )
```

get() 的参数首先是项目的键，字符串值 $key。下一个可选参数是读穿缓存回调，即你在项目不存在于 memcached 时指定的获取请求项目数据的函数。最后一个参数是可选的引用变量，用于获取项目 CAS 令牌值以用于 CAS 操作。对于 getByKey()，与其它 *ByKey 方法一样，第一个参数是字符串 $server_key 值，其后参数的顺序和数量与 get() 相同。

以下是使用这些方法的一些简单示例。假设在这些示例中，先前显示的连接已经建立。第一个示例是一个简单的 set 和 get：

```php
// set a value
if ($memc->set('t1', 'some value')) {
    // if true, success setting
    echo "t1 was set.\n";
}
else {
    // if false, failed to set
    echo "failed to set t1\n";
}

// now fetch t1
$t1= $memc->get('t1');
// Obtain the result code
$result_code= $memc->getResultCode();
if ($result_code == Memcached::RES_SUCCESS) {
    print "t1 is $t1\n";
}
elseif ($result_code == Memcached::RES_NOTFOUND) {
    print "t1 not found\n";
}
```

代码片段 memc.php

如你所见，这个示例非常简单。你有一个键和一个值。你使用键设置值，然后可以使用键检索它。这就是 memcached！当然不仅仅是 get 和 set。下一个示例展示了你可以根据项目是否已存在于 memcached 中来添加和替换。

```php
// if $val exists, then it can be replaced
if ($val = $memc->get('t2')) {
    // if successful replace, then print so
    if ($memc->replace('t2', 'replaced value')) {
        echo "replaced t2's value\n";
    }
    else {
        // otherwise, print that replace failed
        echo "failed to replace t2's value\n";
    }
}
// if the value didn't exist, then add it
else {
```
