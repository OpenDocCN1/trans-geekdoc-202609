- **read-write (RW)**: this option gives Read and Write access to MIB objects. This method provides the ability to modify the configuration of a network element.

– **SNMPv3**: this version has signification improvements, aimed at addressing the security vulnerabilities present in the earlier versions. The concept of the community chain gave way to new security features. However, even though this version offers better security, SNMPv2c still remains the most frequently used version.

# 3.4.2.4. SNMP messages

SNMP messages makes it possible to carry out the following operations:

+   - **searching for data related to the SNMP agent**: SNMP makes it possible to search for data that is linked to an agent using the messages:

+   - **GET**: this makes it possible to extract a value from a MIB element;

+   - **GetNext**: it makes it possible to retrieves the next value of the MIB element;

+   - **GetBulk**: (from version SNMPv2c and higher) this operation is used by the SNMP manager to efficiently retrieve large amounts of data from the SNMP agent;

+   **– the modification of data connected to the SNMP agent**: SNMP makes it possible to modify data connected to the agent by using the message:

+   - **SET**: this makes it possible to define a value for a MIB element;

+   **– Sending alerts and notifications**: SNMP also provides different notification (rerouting) operations that can be used by SNMP to warn the SNMP manager about an important event:

+   - **Trap**: this notification is used to send a message that does not need a read-receipt from the SNMP agent to the SNMP manager (NMS) when a preset condition is fulfilled;

+   - **Inform**: is used to send a message with read-receipt to the SNMP manager now. This feature was introduced in SNMPv2c to address the read-receipt problem when using Trap.

# 3.4.3. SNMP configuration

To configure a router to use SNMP, proceed as follows: