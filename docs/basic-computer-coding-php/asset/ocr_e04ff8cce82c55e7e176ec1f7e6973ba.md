```
$data = getrusage();
echo "User time: ".
($data['ru_utime.tv_sec'] +
data['ru_utime.tv_use'] / 1000000)
echo "System time: ".
($data['ru_stime.tv_sec'] +
data['ru_stime.tv_use'] / 1000000);
```

```
/* prints
User time: 0.011552
System time: 0
*/
```

Even though the script took about 3 seconds to run, the CPU usage was very low. Because during the sleep operation, the script actually does not consume CPU resources. There are many other tasks that may take real time, but may not use CPU time, like waiting for disk operations. So as you see, the CPU usage and the actual length of the runtime are not always the same.

Here is another example:
// loop 10 million times (busy)
for(i=0;i<10000000;i++) {
}

```
$data = getrusage();
echo "User time: ".
($data['ru_utime.tv_sec'] +
data['ru_utime.tv_use'] / 1000000)
echo "System time: ".
($data['ru_stime.tv_sec'] +
data['ru_stime.tv_use'] / 1000000);
```