```
access-list 111 permit tcp 192.168.13.0 0.0.0.255 any eq www
access-list 111 deny tcp any any eq telnet
access-list 111 deny icmp any any
interface ethernet0
ip access-group 111 in
```

> **ExamAlert**
> 
> Although some people use the terms *access control list* and *capability table* interchangeably, they are not the same. Capability tables are bound to subjects; ACLs are bound to objects.

# Other Types of Access Control

Content-dependent access control (CDAC) is based on the content of a resource. CDAC is primarily used to protect databases that contain potentially sensitive data. CDAC is also used to filter out unauthorized traffic and is typically used by proxies or firewalls. For example, you may be able to log in to your organization’s SharePoint page and see the number of days you will be expected to travel next month but unable to see when or where the CEO will be traveling during the same period.

Lattice-based access control (LBAC) is a MAC-based type of access control that defines the least upper and greatest lower bounds. An upper bound is called a *join*, and a lower bound is called a *meet*. LBAC deals with access in complex situations. It allows access only if the subject’s capability is greater than or equal to that of the object being accessed. For example, Figure 6.14 demonstrates the boundaries in LBAC. If you were cleared for top secret, you could read the level below, which is secret.