
## Metasploit sunrpc Scanner (continued)

| Service | ID | Col3 | Port | Protocol |
|---|---|---|---|---|
| mountd | 100005 | 2 | 50405 | tcp |
| mountd | 100005 | 3 | 49030 | udp |
| mountd | 100005 | 3 | 50553 | tcp |
| nfs | 100003 | 3 | 2049 | tcp |
| nfs | 100003 | 4 | 2049 | tcp |
| nfs | 100003 | 3 | 2049 | udp |
| nfs_acl | 100227 | 3 | 2049 | tcp |
| nfs_acl | 100227 | 3 | 2049 | udp |
| nlockmgr | 100021 | 1 | 34578 | udp |
| nlockmgr | 100021 | 3 | 34578 | udp |
| nlockmgr | 100021 | 4 | 34578 | udp |
| nlockmgr | 100021 | 1 | 39297 | tcp |
| nlockmgr | 100021 | 3 | 39297 | tcp |
| nlockmgr | 100021 | 4 | 39297 | tcp |
| rpcbind | 100000 | 4 | 111 | tcp |
| rpcbind | 100000 | 3 | 111 | tcp |
| rpcbind | 100000 | 2 | 111 | tcp |
| rpcbind | 100000 | 4 | 111 | udp |
| rpcbind | 100000 | 3 | 111 | udp |
| rpcbind | 100000 | 2 | 111 | udp |

[*] Scanned 1 of 1 hosts (100% complete)
[*] Auxiliary module execution completed

As we are scanning the same host, it’s not unexpected that we’d get the same results using the Metasploit module as we got from rpcinfo. Since all that is happening is querying the portmapper process, we can use whatever tool makes you the most comfortable. There are a couple of advantages to using these tools over nmap. The first is that you’ll get the process name by checking with portmapper. The second is that you won’t get all of the ports using nmap unless you specifically indicate that you want to scan all ports. The range of ports handed out by portmap isn’t in the list of well-known ports that nmap scans.

### Remote Method Invocation

Java programs are very popular, especially when it comes to web applications. Java provides a lot of assistance to programmers, especially when it comes to libraries and interfaces that can be implemented with your own functionality. Java includes its own capability for remote procedure calls, though in Java it’s called remote method invocation (RMI). In order to have a program that uses RMI, the system needs a version of the portmapper for Java called the rmiregistry. The program using RMI registers itself with the rmiregistry program. This means that anyone can check with the rmiregistry to see what services are offered. The rmiregistry program will respond in a similar way to what we saw when we checked with the portmapper.

It's said that RMI is the object-oriented version of RPC. This means objects get passed between the server and the client. The client implements a stub through an interface. An interface is an object-oriented term indicating a definition of a class. The stub communicates with a skeleton on the server. When a programmer is creating a program that uses RMI, they use an RMI compiler (the program rmic). The programs we use to connect to an RMI registry to enumerate services that are registered don't need to know the specific interfaces needed to pass objects between the skeleton and the stub because the only thing the enumeration is doing is identifying the skeletons or services on the remote system. We'll start with Metasploit to run a scan on a system that has RMI. You can see an example of using Metasploit for RMI enumeration here:

### Running RMI Scanner in Metasploit

```
msf > use auxiliary/gather/java_rmi_registry
msf auxiliary(gather/java_rmi_registry) > show options
```

Module options (auxiliary/gather/java_rmi_registry):

| Name | Current Setting | Required | Description |
|---|---|---|---|
| RHOST | | yes | The target address |
| RPORT | 1099 | yes | The target port (TCP) |

```
msf auxiliary(gather/java_rmi_registry) > set RHOST 192.168.86.62
RHOST => 192.168.86.62
msf auxiliary(gather/java_rmi_registry) > run
[*] 192.168.86.62:1099 - Sending RMI Header...
[*] 192.168.86.62:1099 - Listing names in the Registry...
[+] 192.168.86.62:1099 - 1 names found in the Registry
[+] 192.168.86.62:1099 - Name HelloServer (HelloImpl_Stub) found on 127.0.1.1:38371
[*] Auxiliary module execution completed
```

The options required to run the java_rmi_registry module are simple. The remote port defaults to 1099, which is the port rmiregistry listens on. If you think there is another port listening, you can set the RPORT variable. The one that is essential, though, is RHOST. We set this variable to the IP address of the system where there is a very simple Java program that implements an RMI server. You can see the result of the scan according to the RMI registry, there is a server named HelloServer. It even tells us that the stub is named HelloImpl. Even though it's a server, the registry calls it a stub because the difference between a stub and a skeleton is the end of the conversation that’s happening. The rmic generates stubs for both servers and clients. It’s just that referring to the server end as a skeleton differentiates between the two.

Metasploit is not the only way you can scan for RMI services. If you look around a little, you can find additional programs. One of these is called Barmie, stylized as BaRMIe to highlight the RMI in the name. You can grab the source code as well as a precompiled implementation of BaRMIe through Github. Running the program is straightforward. Since it’s a Java program, you have to run the intermediate code file through the Java program used to create a Java virtual machine. Since it’s stored as a Java archive (JAR), you have to tell Java that it is going to be running from one of those. The program does need to know what host it’s scanning, so you pass in the IP address of your target. You can see a run of BaRMIe next.

The program javac is used to compile Java source code to an intermediate code file. The program java is used to execute an intermediate code file.

### Using BaRMIe

```
root@quiche:~# java -jar BaRMIe_v1.01.jar 192.168.86.62
```

![](img/421171b17a0c0dfae0aacde15d9831c1_234_0.png)

v1.0
Java RMI enumeration tool.
Written by Nicky Bloor (@NickstaDB)

Warning: BaRMIe was written to aid security professionals in identifying the insecure use of RMI services on systems which the user has prior permission to attack. BaRMIe must be used in accordance with all relevant laws. Failure to do so could lead to your prosecution. The developers assume no liability and are not responsible for any misuse or damage caused by this program.

Scanning 1 target(s) for objects exposed via an RMI registry...

```
[--] An exception occurred during the PassThroughProxyThread main loop.
java.net.SocketException: Socket closed
[--] An exception occurred during the ReplyDataCapturingProxyThread main loop.
java.net.SocketException: Socket closed
RMI Registry at 192.168.86.62:1099
Objects exposed: 1
Object 1
Name: HelloServer
Endpoint: 127.0.0.1:38371
[+] Object is bound to localhost, but appears to be exposed remotely.
Classes: 3
Class 1
Classname: java.rmi.server.RemoteStub
Class 2
Classname: java.rmi.server.RemoteObject
Class 3
Classname: HelloImpl_Stub

1 potential attacks identified (+++ = more reliable)
[---] Java RMI registry illegal bind deserialization

0 deserialization gadgets found on leaked CLASSPATH
[~] Gadgets may still be present despite CLASSPATH not being leaked

Successfully scanned 1 target(s) for objects exposed via RMI.
```

We see a couple of things from running this program. It’s a little more verbose than Metasploit is. We get the name of the server, HelloServer. Just as with Metasploit, we see that the server is bound to the localhost on port 38371, which was dynamically allocated by the rmiregistry. We also see the inheritance tree from this. We can see references to the classes java.rmi.server.RemoteStub, java.rmi.server.RemoteObject, and HelloImpl_Stub. According to BaRMIe, the service is exposed remotely but is only available to localhost. This means we have information leakage. In order to attempt to identify vulnerabilities with that RMI server and potentially exploit those vulnerabilities, we need to gain access to the system.

In identifying the RMI registry and the additional services, we have also identified the existence of another piece of software on the target system. It may seem obvious now but if you find an RMI registry and RMI services, you have found a system that at least has a Java runtime engine (JRE) on it, if not a Java development kit (JDK). What we don’t know from the output here is the version of the JRE or JDK. However, there have been vulnerabilities in Java implementations over the last few years. Knowing there is at least a JRE on the system may have given you a lead to vulnerabilities.
