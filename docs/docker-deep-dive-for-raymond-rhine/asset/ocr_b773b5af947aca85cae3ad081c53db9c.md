Run the following command to create a new VM called **node1** based on the **docker** image. The docker image has Docker preinstalled and ready to go.

```
$ multipass launch docker --name node1
```

It'll take a minute or two to download the image and launch the VM.

List VMs to make sure yours launched properly.

| Name | State | IPv4 | Image |
|---|---|---||
| node1 | Running | 192.168.64.37<br>172.17.0.1<br>172.18.0.1 | | Ubuntu |

You'll use the **192** IP address when working with the examples later in the book.

Connect to the VM with the following command.

```
$ multipass shell node1
```