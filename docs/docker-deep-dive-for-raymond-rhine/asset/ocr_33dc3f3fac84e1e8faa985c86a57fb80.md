+   - Linux containers: `/var/lib/docker/<storage-driver>/...`

+   - Windows containers:
  C:\ProgramData\Docker\windowsfilter\...

Even though the local storage layer allows you to update live containers, you should never do this. Instead, you should treat containers as immutable objects and never change them once deployed. For example, if you need to fix or change the configuration of a live container, you should create and test a new container with the changes and then replace the live container with the new one.

To be clear, applications like databases can change the data they manage. But users and configuration tools should never change the container’s *configuration*, such as its network or application configuration. You should always make changes like these in a new container and then replace the old container with the new one.

If your containers don’t create persistent data, this thin writable layer of local storage will be fine, and you’ll be good to go. However, if your containers create persistent data, you need to read the next section.