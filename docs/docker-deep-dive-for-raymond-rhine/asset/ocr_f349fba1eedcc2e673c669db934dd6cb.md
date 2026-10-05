of RAM. If your machine doesn’t have those resources, go to Play with Docker and build your lab there.

Name three of the nodes as mgr1, mgr2, and mgr3, and name the other two wrk1 and wrk2 . Yours will get different IPs, but that doesn't matter. It can take a minute or two to create each VM.

```
$ multipass launch docker --name mgr1
Launched: mgr1

$ multipass launch docker --name mgr2
Launched: mgr2

$ multipass launch docker --name mgr3
Launched: mgr3

$ multipass launch docker --name wrk1
Launched: wrk1

$ multipass launch docker --name wrk2
Launched: wrk2
```

Run the following command and note the node IP addresses. Yours will have different addresses, and you're only interested in the 192.168.x.x address for each.

| Name | State | IPv4 | Image |
| mgr1 | Running | 192.168.64.61 | Ubuntu 22.04 |