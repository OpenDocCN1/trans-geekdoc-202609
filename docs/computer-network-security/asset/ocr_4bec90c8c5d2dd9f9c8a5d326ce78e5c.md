AAA strategies enable the integration of users in the “Active directory” database in order to benefit from centralized management.

Authentication using a server may be summarized as follows:

+   1) the user establishes a connection with the router via a username and password;
+   
+   2) the router passes along the user’s identifiers to an external AAA server;
+   
+   3) the AAA server validates the data;
+   
+   4) the router sends back the result of the connection and validates the data.

![](bbox=[0.18, 0.32, 0.82, 0.49])

# Figure 4.2. Authentication based on a server

In order to configure a router to use AAA authentication on a server, proceed as follows:

| Command | Description |
|---|---|
| R1(config)# tacacs-server host { hostname | host-ip-address } [ key string ] [ port [ integer ] ] [ single-connection ] [ timeout [ seconds ] ] | Configures the IP address (or hostname) of the TACACS+ server. The other parameters are optional. |
| R1(config)# radius-server host { hostname | host-ip-address } [ auth-port port-number ] [ acct-port port-number ] [ key password ] | Configures the IP address (or hostname) of the RADIUS server. The other parameters are optional. |

Optionally, servers may be grouped together to accelerate the process of authenticating users or to ensure load redundancy or balancing.