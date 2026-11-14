![](bbox=[0.136, 0.083, 0.26, 0.162])

NOTE See the “For Further Reading” section for a reference to setting up Ubuntu 16.04 on Amazon AWS, but user beware: do not violate any user agreements of Amazon or your hosting service. You have been warned.

# Open Source Honeypots

In this section, we demonstrate several open source honeypots.

# Lab 21-1: Dionaea

In this lab, we investigate the Dionaea honeypot, a lightweight honeypot that emulates several services.<sup>15</sup>

![](bbox=[0.136, 0.434, 0.26, 0.513])

NOTE The labs in this chapter require 64-bit Linux, as Docker does not support 32-bit operating systems. We use 64-bit Kali 2017.1, if you want to follow along.

First, set up a folder to transfer files off the Docker:

```
root@kali:~# mkdir data
```

Pull down and run the Dionaea Docker image:

```
docker run -it -p 21:21 -p 42:42 -p 69:69/udp -p80:80 -p 135:135 -p 443:443 -p 445:445 -p 1433:1433 -p 1723:1723 -p 1883:1883 -p 1900:1900/udp -p 3306:3306 -p 5060:5060 -p 5060:5060/udp -p 5061:5061 -p 11211:11211 -v `pwd`/data:/data dinotools/dionaea-docker:latest /bin/bash
```

Now, from the new shell of the container, let’s make some changes and enable logging:

```
[container hash id]# sed -i 's/#default./default./' /opt/dionaea/etc/dionaea/dionaea.cfg
```

Next, let’s enable stream capture of sessions in the dionaea.cfg file: