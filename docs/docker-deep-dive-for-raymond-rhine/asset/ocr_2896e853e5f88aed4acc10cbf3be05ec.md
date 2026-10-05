Under the hood, the Linux root user is a combination of a long list of capabilities. Some of these capabilities include:

+   - CAP_CHOWN: lets you change file ownership
- CAP_NET_BIND_SERVICE: lets you bind a socket to low-numbered network ports
- CAP_SETUID: lets you elevate the privilege level of a process
- CAP_SYS_BOOT: lets you reboot the system.

The list goes on and is long.

Docker leverages capabilities so that you can run containers as root but strip out all the capabilities you don't need. For example, suppose the only capability your container needs is the ability to bind to low-numbered network ports. In that case, Docker can start the container as root, drop all root capabilities, and then add back the CAP_NET_BIND_SERVICE capability.

This is a good example of implementing the principle of least privilege as you end up with a container that only has the capabilities it needs. Docker also sets restrictions to prevent containers from re-adding dropped capabilities.

Docker ships with sensible out-of-the-box capabilities, but you should configure your own for your production apps and