snmpwalk() is useful for browsing entire branches of an OID tree. It fetches all the objects below the node specified by the object_id argument. If a null string is used as an object_id argument, then the entire OID tree for the agent is returned. The result is returned as an array of SNMP objects; false is returned in case of an error:

```
<?php
$tcpObjs = snmpwalk("localhost", "public", "tcp");

echo("The list of TCP objects are:<br>");
for ($i = 0; $i < count($tcpObjs); ++$i) {
    echo($tcpObjs[$i]);
}
?>
```

# snmpwalkoid()

# array snmpwalkoid(string hostname, string community, string object_id [, int timeout [, int retries]])

This function serves the same purpose as snmpwalk(), the only difference being that the returned list is an associative array:

```
<?php
$tcpObjs = snmpwalkoid("localhost", "public", "tcp");

echo("The list of TCP objects are:<br>");
do {
    echo($tcpObjs[key($tcpObjs)]);
} while(next($tcpObjs));
?>
```

# snmp_get_quick_print() and snmp_set_quick_print()

# boolean snmp_get_quick_print
void snmp_set_quick_print (boolean quick_print)

By default, SNMP functions return the name of the object, its type, and other information describing the object (subject to the object type) when a get request is issued. This is useful when the return value is directly displayed. However, it might be necessary to use the actual value of the object in our script. In such cases, the "quick print" feature can be turned on which would result in only the value being returned.

The snmp_get_quick_print() function returns false if "quick print" is disabled and true otherwise. The snmp_set_quick_print() function can be passed an argument of true to enable the "quick print" feature and false to disable it:

```
<?php
if (snmp_get_quick_print() == false) {
    echo("Quick print is currently disabled <br>");
    $udpOut = snmpget("localhost", "public", "udp.udpOutDatagrams.0");
```