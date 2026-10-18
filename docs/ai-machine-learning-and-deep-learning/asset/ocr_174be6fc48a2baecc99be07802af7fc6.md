b. *Data service layer:* This is the core layer of IoTSE, where the search engine is deployed. At this layer, the requests from the users are processed based on the request’s needs in data storage. It is then forwarded to the upper layer for any advanced requirements or sent back to the users.

c. *Application layer:* This layer analyzes the requested data to extract insightful patterns and generate further decisions.

3. *Data source:* IoT devices generate data and send the data back to the data storage of IoTSE. In general, the user posts a request to IoTSE at the beginning. If the requested data exists in data storage, the IoTSE then returns it to the user. Otherwise, IoTSE requests data from IoT devices and sends it back to the user.

The most popular IoTSE is the web-crawler-based system that uses the TCP/IP network structure to transmit data. This type of website-based configuration raises some issues:

+   1. *Domain name system (DNS) issue:* As the number of connected IoT devices grows, so does the number of required IP assignments. The IP management is needed in both public and private networks, which significantly increases demands for network address translation (NAT) and DNS management.
+   2. *Network transferring issue:* Since TCP/IP is an end-to-end communication protocol, if a packet loss occurs during the process, the end user can only discover this issue after the time-out, and the end-user may not resend the request again until then.
+   3. *Vulnerability to IP-based flooding attack:* If the adversaries can spoof the IP address of interest, they can quickly launch a flooding attack to pollute the whole network by continuously transmitting junk data. Furthermore, the adversaries can even send crafted malicious data to a specific target to cause critical damage in the system.

To mitigate performance degradation caused by attacks, machine learning (ML) provides promising solutions. Even for high volumes of data traffic, ML can extract the key structures and features by analyzing internal relationships between data features [5]. This differs from traditional