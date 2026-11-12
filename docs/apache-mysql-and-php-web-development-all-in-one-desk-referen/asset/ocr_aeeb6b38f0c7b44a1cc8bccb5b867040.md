![](bbox=[0.26, 0.125, 0.69, 0.635])

Figure 1-1:
Secure LAN
configuration.

# Getting a Handle on TCP and UDP Services

When you finish your Linux installation and before installing any other software, you need to remove the default network services that won’t be used.
By default, the services running on your new Linux installation are providing
what the install package’s creator deems commonly used services. Because
your system will provide Web services (exclusively if possible) and because
it may be directly connected to the Internet, you will want to remove many
of the default services. Any service can provide an unscrupulous remote
user with a potential avenue into your system. If the service is available to
network users and is running, you should consider it a potential weakness.
Even though many hours are spent testing and identifying flaws in the Linux
system, testing can’t catch everything. However, you can minimize potential
threats by removing unneeded services.