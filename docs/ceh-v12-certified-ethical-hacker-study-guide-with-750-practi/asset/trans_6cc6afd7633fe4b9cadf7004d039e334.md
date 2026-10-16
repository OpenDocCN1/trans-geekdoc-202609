
-   [进程间通信](https://example.org/interprocess_communication)已经存在数十年。几十年来出现了多种请求-响应协议的实现。Java 的远程方法调用（RMI）是最近的一个例子。在此之前，还有独立于语言实现的通用对象请求框架（CORBA）。有时，使用 RPC 时，你需要本质上是一个目录服务，用于指示不同服务在动态端口上运行的端口。

-   远程过程调用（RPC）的一个常见实现是程序 `portmap`，也称为 `rpcbind`。该程序用于提供已向端口映射服务注册的程序信息，从而提供这些远程过程。端口映射器为服务分配监听端口，并在查询时返回该信息。常见的使用 `rpcbind`/`portmap` 的服务示例包括网络文件服务器（NFS）。

-   提供 `portmap` 或 `rpcbind` 服务的包可能还包含可以通过 RPC 进行通信的实用工具。这通过端口 111 实现。要识别远程系统上的程序及其关联端口，可以使用程序 `rpcinfo`。下面展示了 `rpcinfo` 的使用示例。使用的命令 `rpcinfo -p` 让 `rpcinfo` 探测提供的主机（这里是 IP 地址而非主机名）。

#### rpcinfo 列表

```
kilroy@bobbie $ rpcinfo -p 192.168.86.52
    program vers proto   port  service
     100000    4   tcp    111  portmapper
     100000    3   tcp    111  portmapper
     100000    2   tcp    111  portmapper
     100000    4   udp    111  portmapper
     100000    3   udp    111  portmapper
     100000    2   udp    111  portmapper
     100005    1   udp  43939  mountd
     100005    1   tcp  58801  mountd
     100005    2   udp  46384  mountd
     100005    2   tcp  50405  mountd
     100005    3   udp  49030  mountd
     100005    3   tcp  50553  mountd
     100003    3   tcp   2049  nfs
     100003    4   tcp   2049  nfs
     100227    3   tcp   2049  nfs_acl
     100003    3   udp   2049  nfs
     100227    3   udp   2049  nfs_acl
     100021    1   udp  34578  nlockmgr
     100021    3   udp  34578  nlockmgr
     100021    4   udp  34578  nlockmgr
     100021    1   tcp  39297  nlockmgr
     100021    3   tcp  39297  nlockmgr
     100021    4   tcp  39297  nlockmgr
 
```

-   前面提到的程序若已在 `rpcbind` 中注册了远程过程，则与 NFS 文件共享服务器关联。`portmapper` 是主要查询的服务，而 `mountd`、`nfs`、`nlockmgr` 等则是 NFS 所必需的组件。NFS 由 Sun Microsystems 开发，`portmapper` 是 Sun 关联的 RPC 实现，有时也称为 sunrpc。例如 Metasploit 中的扫描器可以利用 sunrpc 来识别端口映射器分配的程序端口。

#### Metasploit sunrpc 扫描器

```
 msf> use auxiliary/scanner/misc/sunrpc_portmapper
  
 msf auxiliary(scanner/misc/sunrpc_portmapper)> set RHOSTS 192.168.86.52
 RHOSTS => 192.168.86.52
 msf auxiliary(scanner/misc/sunrpc_portmapper)> run
  
 [+] 192.168.86.52:111 - SunRPC Programs for 192.168.86.52
 =================================
  
 Name      Number  Version  Port   Protocol
 ----      ------  -------  ----   --------
 mountd    100005  1        43939  udp
 mountd    100005  1        58801  tcp
 mountd    100005  2        46384  udp
 mountd    100005  2        50405  tcp
 mountd    100005  3        49030  udp
 mountd    100005  3        50553  tcp
 nfs       100003  3        2049   tcp
 nfs       100003  4        2049   tcp
 nfs       100003  3        2049   udp
 nfs_acl   100227  3        2049   tcp
 nfs_acl   100227  3        2049   udp
 nlockmgr  100021  1        34578  udp
 nlockmgr  100021  3        34578  udp
 nlockmgr  100021  4        34578  udp
 nlockmgr  100021  1        39297  tcp
 nlockmgr  100021  3        39297  tcp
 nlockmgr  100021  4        39297  tcp
 rpcbind   100000  4        111    tcp
 rpcbind   100000  3        111    tcp
 rpcbind   100000  2        111    tcp
 rpcbind   100000  4        111    udp
 rpcbind   100000  3        111    udp
 rpcbind   100000  2        111    udp
  
 [*] Scanned 1 of 1 hosts (100% complete)
 [*] Auxiliary module execution completed
 
```

-   由于我们正在扫描同一主机，使用 Metasploit 模块得到的结果与 `rpcinfo` 的结果相同是合理的。所有操作仅是向端口映射器进程查询。你可以使用最舒适的工具进行查询。相较于 `nmap`，这些工具有两个优势：第一，通过查询端口映射器可以得到进程名称；第二，除非你明确指定扫描所有端口，否则 `nmap` 会返回所有端口，而 `portmap` 分配的端口范围并不在 `nmap` 默认扫描列表中。

### 远程方法调用（RMI）

Java 程序尤其在 Web 应用领域非常流行。Java 为程序员提供了大量库和接口，可以在自身实现中使用这些库和接口。Java 自身提供了远程过程调用功能，但在 Java 中称为 *remote method invocation*。要让一个程序使用 RMI，系统需要一个名为 `rmiregistry` 的 Java 版端口映射器。使用 RMI 的程序会向 `rmiregistry` 注册自己。这意味着任何人都可以通过 `rmiregistry` 查看提供的服务。`rmiregistry` 程序的响应方式与我们在查询端口映射器时所见类似。

-   RMI 被认为是面向对象的 RPC 版本，这意味着对象在服务器和客户端之间传递。客户端通过实现一个接口（面向对象的类定义）来实现桩（stub）。桩负责与服务器上的骨架（skeleton）通信。编写使用 RMI 的程序时，会使用 RMI 编译器（程序 `rmic`）。用于连接 RMI 注册表并枚举已注册服务的程序不需要知道具体的桩和骨架之间的对象传递细节，因为枚举的目的仅是识别远程系统上的骨架或服务。

-   下面展示了在 Metasploit 中运行 RMI 扫描的示例。你可以看到如何使用 Metasploit 对运行 RMI 的系统进行枚举。

**运行 RMI 扫描器（Metasploit）**

```
 msf> use auxiliary/gather/java_rmi_registry
 msf auxiliary(gather/java_rmi_registry)> show options
  
 Module options (auxiliary/gather/java_rmi_registry):
  
    Name   Current Setting  Required  Description
    ----   ---------------  --------  -----------
    RHOST                   yes       The target address
    RPORT  1099             yes       The target port (TCP)
  
 msf auxiliary(gather/java_rmi_registry)> set RHOST 192.168.86.62
 RHOST => 192.168.86.62
 msf auxiliary(gather/java_rmi_registry)> run
  
 [*] 192.168.86.62:1099 - Sending RMI Header…
 [*] 192.168.86.62:1099 - Listing names in the Registry…
 [+] 192.168.86.62:1099 - 1 names found in the Registry
 [+] 192.168.86.62:1099 - Name HelloServer (HelloImpl_Stub) found on 127.0.1.1:38371
 [*] Auxiliary module execution completed
 
