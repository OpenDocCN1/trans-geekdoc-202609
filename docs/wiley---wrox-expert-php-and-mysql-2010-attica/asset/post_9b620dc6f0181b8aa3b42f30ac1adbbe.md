
Of course casByKey() has as its first argument the server key. Just like set(), cas() also returns a Boolean true if successful, false if failure.

The following simple example shows how CAS works. In this example, assume that there are two Memcached instances, each a client connected to the same memcached pool of servers. The reason for two clients is to give an example that distills down to the most basic concept of why you would want to use CAS.

```php
// set a value
if ($memc->set('t1', 'initially set value')) {
    // if true, success setting
    echo "t1 initially set.\n";
}
else {
    // if false, failed to set
    echo "failed to set t1\n";
}

// now fetch t1
if ($t1= $memc->get('t1', null, $cas)) {
    print "t1 value is '$t1'\n";
}
elseif ($memc->getResultCode() == Memcached::NOT_FOUND) {
    print "t1 not found\n";
}
echo "cas value $cas\n";

// did anyone else change it since?
sleep(2);
if ($memc->cas($cas, 't1', 'a new value using cas')) {
    echo "t1 set with cas\n";
}
else {
    echo "t1 not set with cas\n";
}
// now fetch t1 again
if ($t1= $memc->get('t1', null, $cas)) {
    echo "t1 value is '$t1'\n";
}
elseif ($memc->getResultCode() == Memcached::NOT_FOUND) {
    echo "t1 not found\n";
}
echo "cas value $cas\n";

sleep(2);
// another client, t2 is setting
echo "memc2 is setting t1\n";
$memc2->set('t1', 'memc2 changed me');
sleep(2);
// did anyone else change it since?
sleep(2);

// this should not succeed
if ($memc->cas($cas, 't1', 'check if cas can set')) {
    echo "t1 set with cas\n";
}
else {
    echo "t1 not set with cas\n";
}
```

Code snippet cas.php

This example shows how CAS succeeds if another client hasn’t modified the item since you last fetched it and then how CAS fails if another client ($memc2) did modify it in between the last fetch. The sleep() calls are for accentuating the central point of the example when running the program. The following output verifies that the second client, $memc2, having modified t1 since it was last fetched by $memc, causes the second cas() call to fail:

```
t1 initially set.
t1 value is 'initially set value'
cas value 14
t1 set with cas
t1 value is 'a new value using cas'
cas value 15
memc2 is setting t1
t1 not set with cas
```

Also note in this output that the CAS token increments each time there is a successful CAS operation.

## Statistics

You may, in fact, want to write internal utility applications to monitor memcached and provide information about how your memcached server pool is functioning. This includes information such as how much memory is being used, how many items have been stored, how many cache hits and misses there have been, and so on. The method for this information is getStats():

```php
public array Memcached::getStats( void )
```

The following code, if run with the previous connection to the pool of three memcached servers:

```php
$stats_ar = $memc->getStats();

print_r($stats_ar);
```

Code snippet memc_stats.php

produces the output showing three servers’ stats:

```
Array
(
    [192.168.1.106:11211] => Array
        (
            [pid] => 45035
            [uptime] => 75925
            [threads] => 4
            [time] => 1256400151
            [pointer_size] => 32
            [rusage_user_seconds] => 0
            [rusage_user_microseconds] => 729726
            [rusage_system_seconds] => 1
            [rusage_system_microseconds] => 519083
            [curr_items] => 0
            [total_items] => 0
            [limit_maxbytes] => 67108864
            [curr_connections] => 10
            [total_connections] => 12
            [connection_structures] => 11
            [bytes] => 0
            [cmd_get] => 0
            [cmd_set] => 0
            [get_hits] => 0
            [get_misses] => 0
            [evictions] => 0
            [bytes_read] => 20
            [bytes_written] => 745
            [version] => 1.4.1_25_g2c7bfeb
        )
    [127.0.0.1:11211] => Array
        (
            [pid] => 743
            [uptime] => 75921
            [threads] => 1
            [time] => 1256400151
            [pointer_size] => 64
            [rusage_user_seconds] => 0
            [rusage_user_microseconds] => 70000
            [rusage_system_seconds] => 0
            [rusage_system_microseconds] => 10000
            [curr_items] => 2
            [total_items] => 9
            [limit_maxbytes] => 67108864
            [curr_connections] => 2
            [total_connections] => 13
            [connection_structures] => 3
            [bytes] => 329
            [cmd_get] => 10
            [cmd_set] => 9
            [get_hits] => 10
            [get_misses] => 0
            [evictions] => 0
            [bytes_read] => 956
            [bytes_written] => 1491
            [version] => 1.2.6
        )
    [192.168.1.125:11211] => Array
        (
            [pid] => 11596
            [uptime] => 75889
            [threads] => 2
            [time] => 1256399615
            [pointer_size] => 32
            [rusage_user_seconds] => 0
            [rusage_user_microseconds] => 8000
            [rusage_system_seconds] => 0
            [rusage_system_microseconds] => 12000
            [curr_items] => 1
            [total_items] => 5
            [limit_maxbytes] => 67108864
            [curr_connections] => 4
            [total_connections] => 10
            [connection_structures] => 5
            [bytes] => 66
            [cmd_get] => 5
            [cmd_set] => 5
            [get_hits] => 4
            [get_misses] => 1
            [evictions] => 0
            [bytes_read] => 260
            [bytes_written] => 733
            [version] => 1.2.8
        )
)
```

> *For information on what each statistic means, please consult the memcached project web site at http://memcached.org.*

## Server List

One other useful informational method is the getServers() method, which returns a list of servers as an array that the server pool is composed of — just like the server list shown previously, used in creating a connection:

```
public array Memcached::getServerList ( void )
```

This simple snippet shows how this works:

```
$server_ar = $memc->getServerList();
print_r($server_ar);
```

## Error Handling

Throughout these examples, you have seen various ways of dealing with errors. In some cases, for instance, a set operation is performed as the conditional to an if-else block. If true, the value was set; if false, something failed. This is one way of dealing with an error of a set. For get, you sometimes use the simple check that a value was fetched to conditionally determine if there was an error. However, as shown in some examples, you might want to know what the specific error was or use
a condition of a specific error in an if-else block. To retrieve the specific error of something that failed, you can use the following methods:

```
public string Memcached::getResultMessage(void)
public int Memcached::getResultCode(void)
```

The first method, getResultMessage(), returns a string message from the particular operation that was performed. The method getResultCode() returns a numeric code from the server. You can find the result codes and what they mean at http://us2.php.net/manual/en/memcached.constants.php. The following example shows how you can use these two methods:

```
// set a value
if ($memc->set('t1', 'initially set value')) {
    echo "success setting\n";
}
elseif ($memc->getResultCode() == Memcached::RES_NOTSTORED) {
    echo "'t1' was not set\n";
}

echo "return message from set operation was: " . $memc->getResultMessage() . "\n";

$t1= $memc->get('t1', null, $cas);
echo "return message from get operation was: " . $memc->getResultMessage() . "\n";

if ($memc->add('t1', 'added value should not work')) {
    echo "success adding\n";
}
elseif ($memc->getResultCode() == Memcached::RES_NOTSTORED) {
    echo "'t1' was not added\n";
}
echo "return message from get operation was: " . $memc->getResultMessage() . "\n";

$memc->delete('t1');
$t1= $memc->get('t1', null, $cas);
echo "return message from get operation was: " . $memc->getResultMessage() . "\n";
```

Code snippet result.php

The output of this code gives you:

```
success setting
return message from set operation was: SUCCESS
return message from get operation was: SUCCESS
't1' was not added
return message from add operation was: NOT STORED
return message from get operation was: NOT FOUND
```

Interestingly, if you were to shut down your memcached servers within the pool (just for testing — don’t do this in a production environment!) all calls to getResultMessage() would return:

```
return message from set operation was: SYSTEM ERROR
return message from get operation was: SYSTEM ERROR
return message from add operation was: SYSTEM ERROR
return message from get operation was: SYSTEM ERROR
```
