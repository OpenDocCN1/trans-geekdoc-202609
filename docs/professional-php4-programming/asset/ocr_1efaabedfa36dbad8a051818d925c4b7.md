```
$entry = yp_next("wrox.com", "hosts.byname", "joe");
if ($entry == FALSE) {
 echo("No more entries");
} else {
 echo("Key: " . $entry["key"] . "Value: " . $entry["value"]);
}
?>
```

This script displays the entry in the hosts.byname map after the entry whose key is "joe".

# yp_order()

```
int yp_order(string domain, string map)
```

This function returns the order number for the map (second argument) belonging to the domain specified by the first argument. In the event of an error false is returned. An order number is assigned to a map by the system when it is created for the first time and every time the map is updated. Using the order number it is possible to establish if a map has been modified. The yppoll command on UNIX systems can be used to get the order number of a map:

```
<\?php
$ordNum = yp_order("wrox.com", "hosts.byname");
if ($ordNum != FALSE) {
 echo("The order number for the hosts map is: $ordNum <br>");
} else {
 echo("Order number could not be found. <br>");
}
?>
```

# Simple Network Management Protocol

In a medium to large-scale network, the task of managing a large number of devices can be an arduous task, considering the myriad of vendors for a given class of devices and the idiosyncrasies of configuring each of these devices. Each router, switch, and repeater has its own unique properties that need to be configured and tuned. The Simple Network Management Protocol (SNMP) aims to provide an open and secure framework to make these tasks more manageable.

# Agents and Managers

The SNMP model is a client-server model in which the managed devices have an agent, which speaks the SNMP protocol. The agent in effect acts as a server to which managers can connect using the SNMP protocol.

The agents usually have a protocol module which handles protocol interactions and an instrumentation module which is concerned with gathering and setting various device specific parameters. Since the agent requires intimate knowledge of the configuration interfaces available on the managed device for gathering and setting parameters, these are usually provided by the device vendor or by third-party software which implements the instrumentation module.