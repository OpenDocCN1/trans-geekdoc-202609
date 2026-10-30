![](bbox=[0.163, 0.142, 0.793, 0.737])

**Figure 21-1**  RADIUS communication sequence

# RADIUS Authorization

In the RADIUS protocol, the authentication and authorization steps are performed together in response to a single Access-Request message, although they are sequential steps, as shown in Figure 21-1. Once an identity has been established, either known or default, the authorization process determines what parameters are returned to the client. Typical authorization parameters include the service type allowed (shell or framed).