# Basic Computer Coding: PHP

```
/* prints
User time: 1.4245992
System time: 0.004204
*/
```

That took about 1.4 seconds of CPU time, almost all of which was user time, since there were no system calls.

System Time is the amount of time the CPU spends performing system calls for the kernel on the program's behalf. Here is an example of that:

```
$start = microtime(true)
// keep calling microtime for about 3 seconds
while(microtime(true) - $start < 3) {

}
```

```
$data = getrusage();
echo "User time: " . 
($data['ru_utime.tv_sec'] + $data['ru_utime.tv_use'] / 1000000)
echo "System time: " . 
($data['ru_stime.tv_sec'] + $data['ru_stime.tv_use'] / 1000000)
```

```
/* prints
User time: 1.088171
System time: 1.675315
*/
```

Now we quite a bit of system time usage. This is because the script calls the microtime() function many times, which performs a request through the operating system to fetch the time.

Also you may notice the numbers do not quite add up to 3 seconds. This is because there were probably other processes on the server as well, and the script was not using 100% CPU for the whole