![](bbox=[0.09, 0.09, 0.93, 0.46])

The leaf nodes represent the actual parameters, for example,
iso.org.dod.internet.mgmt.mib.udp.udpOutDatagrams defines the number of IP datagrams
that have been sent out. The naming convention for an OID parameter is either a dot-separated list of
names, such as iso.org.dod.internet.mgmt.mib.udp.udpOutDatagrams, or the equivalent list
of dot-separated numbers that lead to a particular node, such as 1.3.6.1.2.1.7.4. Internally, SNMP
uses the dot-separated list of numbers for data representation since the textual names are only for
human convenience.

The MIB is the part of the OID tree which all SNMP agents should implement. It has sub-nodes for
various TCP/IP protocols and system information for the host on which the agent is running. MIBs can
be extended (and often in a proprietary manner) to support a list of parameters, which might be specific
to a device, or an application that is being managed.

Community decides the scope and level of access, that is, it determines if a certain manager can access a
certain piece of information and whether it can modify information. An agent and a manager that
wishes to poll it should be configured to support a given community. The manager contacts an agent
supplying the community name. If the community name and IP address of the manager does not match
the list of permitted managers, then the agent rejects the SNMP request.

For further reading on the same, read http://www.snmp-products.com/RFC/rfc1212.txt and
http://www.snmp-products.com/RFC/rfc1213.txt.

# SNMP Functions in PHP

PHP provides a minimal set of SNMP functions that can be used to implement manager functionality.
However, it is not possible to use these functions to build agent functionality into PHP scripts. To use
the functions, we need to install the UCD SNMP package which is available at
http://ucd-snmp.ucdavis.edu/.