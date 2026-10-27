over APC, namely that Memcached can be configured with a group of servers, Memcached can be served from a completely different server from the application (unlike APC which only writes to the memory on the same machine as the application), and Memcached is designed for high level use (it is used by Facebook, Yahoo, Digg, etc.).

Memcached can also be used to store sessions in PHP. To do this, one need only change the following lines in the php.ini file (assuming that PHP Memcached support is installed):

```
```php
session.save_handler = memcache
session.save_path = "tcp://127.0.0.1:11211"
```
```

It’s also very easy to create a Memcached caching class, which will do simple caching operations. Memcached has been used to do some extremely complicated caching, up to and including serving the entire webpage, bypassing PHP altogether.

Note in the listing below that the Memcached extension in PHP is already object-oriented. The wrapper is provided to demonstrate the functionality, but the Memcached object can be used directly if the developer prefers:

```
```php
class Memcache_Cache {
    protected $memcacheObj;

    public function __construct($host, $port) {
        $this->memcacheObj = new Memcache();
        $this->addConnection($host, $port);
    }

    public function addConnection($host, $port) {
        $this->memcacheObj->connect($host, $port);
    }

    public function write($key, $data, $expires = 0, $flag = false) {
        return $this->memcacheObj->set($key, $data, $flag, $expires);
    }

    public function read($key, $flags = false) {
        return $this->memcacheObj->get($key, $flags);
    }
}
```
```