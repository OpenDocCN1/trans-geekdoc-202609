when Joe tries to disconnect without the check box selected. If Darryl is working at the computer, he can see this connection attempt and click Cancel to block it. Otherwise, the request will automatically disconnect Darryl's session after 30 seconds and allow Joe session.

# FIGURE 17.13
Disconnect request

![](bbox=[0.336, 0.203, 0.643, 0.318])

If Darryl was active and clicked Cancel, Joe would receive a notification indicating that the logged-on user denied the disconnect request.

# ACTIVE CONNECTIONS FOR INACTIVE SESSIONS

This method of closing an inactive administrator session provides a real-world solution to a common problem. We've worked in some large environments where administrators connect remotely to a server, but instead of logging off, they simply disconnect by closing the RDC application.

When this happens, the inactive session is left open on the server. If the server has reached the maximum number of sessions, other administrators can't log into a remote session. These inactive sessions would stay open until they out (if time-out settings were configured), the user logged back in and closed the session, or the session was closed in Remote Desktop Services Manager.

With the features now available in RDC, you can easily see who's connected, whether the session is active or idle, and even choose to disconnect the session.

# INSTALLING REMOTE DESKTOP SERVICES WITH SESSION HOST SERVICE

For the next few sections of this chapter you will need the Remote Desktop Services role installed on the server.
To install this role, do the following:

+   - Open the Server Manager Dashboard, and click Add Roles and Features.
- Click Next to get past the “Before you begin” screen.
- On the next screen (Figure 17.14) select “Role-based or feature-based installation.”