# Get

A get operation is usually a request from a manager to an agent or the response from the agent. The get operation does not modify data; it only queries for specific parameters and returns the response for the queries.

# Get Next

Managers often need to collect information about a series of parameters that are at the same level in the data organization hierarchy (we shall see more about this in the next section). A get-next request is similar to a get request, the difference being that it remembers the parameter for which the previous get or get-next request was issued and in effect performs a get request for the subsequent parameter in the hierarchy.

# Set

This is the update counterpart of a get request. It sets a given value to a specified parameter. The set operation is often used implicitly to perform actions or activate triggers on an agent. For example, to reboot an agent machine, a parameter like NextRebootTime can be set to 0. Since the instrumentation module on the agent is monitoring this parameter, it triggers an immediate reboot.

# Trap

With the above operations we noticed that the managers always issue queries to the agents and the agents respond. Such a model does not take care of the case where agents might need to asynchronously report some critical event that has occurred. As an example, a critical failure could have occurred on the system monitored by the agent. The agent needs a mechanism to communicate this to the manager. In such cases the agent sends a trap message to the manager. The means by which a trap message is handled is not dictated by SNMP and is left to the discretion of particular implementations.

# SNMP Data Organization

Since SNMP attempts to manage and propagate information about a vast set of parameters pertaining to the various classes of devices it supports, there is a need for a structured data organization framework. At a basic level, SNMP defines fundamental types that are used to construct the parameters that hold the information. An example of this type is Integer, which is the data type used for declaring counters and state of parameters. For example, a certain protocol can have a counter for the number of packets that it has processed so far.

The Object Identifier (OID) type is used to define a hierarchy of the various parameters. This representation of the parameters is often called an OID tree. The OID tree has various branches for protocols and classes of parameters: