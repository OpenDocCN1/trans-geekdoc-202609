# 118: Does PHP support multithreading?

Answer:
PHP does not have a built-in support for multithreading. One can fake a fork in PHP. Forking is one method of multitasking and there exists an extension called Process Control Extension to handle this. There are also command line PHP commands that will allow for an process to run outside of PHP and return the output to PHP.

# 119: Can you lookup domain name using PHP?

Answer:
PHP has a function gethostbyname() that can be used to look up the domain name.

# 120: Are the host names returned by gethostbyaddr() correct always?

Answer:
This may not be true always. A malicious user may configure the DNS server to reply with incorrect hostnames. A combination of gethostbyname() and gethostbyaddr() can be used to verify the correctness of the results.

# 121: Can you ping a host using PHP?

Answer:
One can use PEAR's Net_Ping package to ping a host to see if it is reachable.

```
$ping = new Net_Ping;
if ($ping->checkhost('www.vibrantpublishers.com')) {
  print 'Reachable';
} else {
  print 'Not reachable';
}
```

# 122: Does PHP have support for FTP? Can you list some of the FTP functions offered by PHP?

Answer: