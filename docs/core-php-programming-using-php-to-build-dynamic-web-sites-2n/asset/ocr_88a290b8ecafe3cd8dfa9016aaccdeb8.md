```
<?
class animal {
    var $name;
}

class dog extends animal {
    var $owner;
    function speak() {
        print("woof!");
    }
}

$gus = new dog;
$gus->name = "Gus";

if(method_exists($gus, "speak")) {
    $gus->speak();
}
?>
```

# openlog identifier, integer option, integer facility

The openlog function begins a connection to the system log and calls C's openlog function. It is not strictly required to call openlog before syslog, but it may be used to change the behavior of the syslog function. You may wish to refer to the man page for openlog for more details. On Windows, emulation code used to mimic UNIX functionality.

The identifier argument will be added to the beginning of any messages sent to the system log. This is usually the name of the process or task being performed.

The option argument is a logical-or operator to combine the options. Table 8.10 lists the values available. Only the LOG_PID option has any effect under Windows.

Table 8.10. openlog Options

| Constant | Description |
| --- | --- |
| LOG_PID | Add process to each message. |
| LOG_CONS | If a message cant be sent to the log, send it to the system console. |
| LOG_ODELAY | Delay logging until the first call to syslog. This is true by default. |
| LOG_NDELAY | Open the log immediately. Do not wait for first call to syslog. |
| LOG_NOWAIT | Do not wait for child processes. The use of this flag is discouraged. |
| LOG_PERROR | Log all messages to stderr as well. |