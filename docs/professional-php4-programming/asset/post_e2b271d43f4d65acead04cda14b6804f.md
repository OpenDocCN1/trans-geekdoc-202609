
```php
$entry = yp_next("wrox.com", "hosts.byname", "joe");
if ($entry == FALSE) {
 echo("No more entries");
} else {
 echo("Key: " . $entry["key"] . "Value: " . $entry["value"]);
}
?>
```

This script displays the entry in the hosts.byname map after the entry whose key is "joe".

## yp_order()

```
int yp_order(string domain, string map)
```

This function returns the order number for the map (second argument) belonging to the domain specified by the first argument. In the event of an error false is returned. An order number is assigned to a map by the system when it is created for the first time and every time the map is updated. Using the order number it is possible to establish if a map has been modified. The yppoll command on UNIX systems can be used to get the order number of a map:

```php
$ordNum = yp_order("wrox.com", "hosts.byname");
if ($ordNum != FALSE) {
 echo("The order number for the hosts map is: $ordNum <br>");
} else {
 echo("Order number could not be found. <br>");
}
?>
```

## Simple Network Management Protocol

In a medium to large-scale network, the task of managing a large number of devices can be an arduous task, considering the myriad of vendors for a given class of devices and the idiosyncrasies of configuring each of these devices. Each router, switch, and repeater has its own unique properties that need to be configured and tuned. The Simple Network Management Protocol (SNMP) aims to provide an open and secure framework to make these tasks more manageable.

### Agents and Managers

The SNMP model is a client-server model in which the managed devices have an agent, which speaks the SNMP protocol. The agent in effect acts as a server to which managers can connect using the SNMP protocol.

The agents usually have a protocol module which handles protocol interactions and an instrumentation module which is concerned with gathering and setting various device specific parameters. Since the agent requires intimate knowledge of the configuration interfaces available on the managed device for gathering and setting parameters, these are usually provided by the device vendor or by third-party software which implements the instrumentation module.

The common aspect of all agents is the ability to speak the SNMP protocol and to support Management Information Bases (MIBs), which we shall come to later. Often there are devices that do not have an SNMP agent supplied with them or may come with a proprietary management interface. In such cases a proxy agent arbitrates the protocol interaction between the SNMP managers and the actual agent:

![](img/9cf7789dba9b16ef3f8576d5aea89186_497_0.png)

On the contrary, manager software only needs to implement the protocol part of SNMP and support for MIBs. Most often SNMP managers are encapsulated into much larger network management software, which provides a higher-level abstraction of the managed devices and the network as a whole. For example, the SNMP protocol by itself does not provide any inherent mechanism for discovery of the various agents in a network; nor does it provide a mechanism for detecting the topology of the network. Such higher-level abstraction of network entities is provided by manager software that uses SNMP functionality as building blocks.

More often than not, management software provides a user interface that supports different views of a network with GUI support for changing and querying various parameters either automatically or manually. It may also have the capacity to handle critical conditions as reported by the agents and the ability to perform pre-programmed tasks such as data collection.

## SNMP Protocol

The SNMP protocol is an ASCII-based protocol implemented over UDP that allows SNMP agents and managers to talk to each other. The protocol supports four simple operations.

### Get

A get operation is usually a request from a manager to an agent or the response from the agent. The get operation does not modify data; it only queries for specific parameters and returns the response for the queries.

### Get Next

Managers often need to collect information about a series of parameters that are at the same level in the data organization hierarchy (we shall see more about this in the next section). A get-next request is similar to a get request, the difference being that it remembers the parameter for which the previous get or get-next request was issued and in effect performs a get request for the subsequent parameter in the hierarchy.

### Set

This is the update counterpart of a get request. It sets a given value to a specified parameter. The set operation is often used implicitly to perform actions or activate triggers on an agent. For example, to reboot an agent machine, a parameter like NextRebootTime can be set to 0. Since the instrumentation module on the agent is monitoring this parameter, it triggers an immediate reboot.

### Trap

With the above operations we noticed that the managers always issue queries to the agents and the agents respond. Such a model does not take care of the case where agents might need to asynchronously report some critical event that has occurred. As an example, a critical failure could have occurred on the system monitored by the agent. The agent needs a mechanism to communicate this to the manager. In such cases the agent sends a trap message to the manager. The means by which a trap message is handled is not dictated by SNMP and is left to the discretion of particular implementations.

## SNMP Data Organization

Since SNMP attempts to manage and propagate information about a vast set of parameters pertaining to the various classes of devices it supports, there is a need for a structured data organization framework. At a basic level, SNMP defines fundamental types that are used to construct the parameters that hold the information. An example of this type is Integer, which is the data type used for declaring counters and state of parameters. For example, a certain protocol can have a counter for the number of packets that it has processed so far.

The Object Identifier (OID) type is used to define a hierarchy of the various parameters. This representation of the parameters is often called an OID tree. The OID tree has various branches for protocols and classes of parameters:

![](img/9cf7789dba9b16ef3f8576d5aea89186_499_0.png)

The leaf nodes represent the actual parameters, for example, iso.org.dod.internet.mgmt.mib.udp.udpOutDatagrams defines the number of IP datagrams that have been sent out. The naming convention for an OID parameter is either a dot-separated list of names, such as iso.org.dod.internet.mgmt.mib.udp.udpOutDatagrams, or the equivalent list of dot-separated numbers that lead to a particular node, such as 1.3.6.1.2.1.7.4. Internally, SNMP uses the dot-separated list of numbers for data representation since the textual names are only for human convenience.

The MIB is the part of the OID tree which all SNMP agents should implement. It has sub-nodes for various TCP/IP protocols and system information for the host on which the agent is running. MIBs can be extended (and often in a proprietary manner) to support a list of parameters, which might be specific to a device, or an application that is being managed.

Community decides the scope and level of access, that is, it determines if a certain manager can access a certain piece of information and whether it can modify information. An agent and a manager that wishes to poll it should be configured to support a given community. The manager contacts an agent supplying the community name. If the community name and IP address of the manager does not match the list of permitted managers, then the agent rejects the SNMP request.

For further reading on the same, read http://www.snmp-products.com/RFC/rfc1212.txt and http://www.snmp-products.com/RFC/rfc1213.txt.

## SNMP Functions in PHP

PHP provides a minimal set of SNMP functions that can be used to implement manager functionality. However, it is not possible to use these functions to build agent functionality into PHP scripts. To use the functions, we need to install the UCD SNMP package which is available at http://ucd-snmp.ucdavis.edu/.
