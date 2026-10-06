# FIGURE 23.12

Configuring constraints for a network policy

![](bbox=[0.313, 0.096, 0.876, 0.473])

# ### Policy 1

+   - Condition: Sales group, Allow access

+   - Constraints: None

# ### Policy 2

+   - Constraints: Day and time restrictions (7 a.m. to 5 p.m. Monday through Friday)

If in the Sales group access the server, they will use Policy 1 based on the Sales group condition and the constraints will not restrict their access. If any domain user thats not in the Sales group access the server, they will use Policy 2 based on the Domain users condition. If they access the server between 7 a.m. and 5 p.m. Monday through Friday, the connection will complete. However, if they access it at any other time, they'll still use Policy 2, but the constraint will prevent the connection.

The two constraints are as follows:

**Idle Timeout** You can configure this to close the connection if the session is idle for a period of time, just as a screen saver can be configured to start if a system is idle.

**Session Time-out** The total connection time can be configured to control how long a user connects. For example, enabling this and setting it to 60 will disconnect users after they've connected for 60 minutes.