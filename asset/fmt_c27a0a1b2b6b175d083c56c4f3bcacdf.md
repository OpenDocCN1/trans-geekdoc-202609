
```c
__writedr(2u, 0); // mov dr2, 0

__writedr(3u, 0); // mov dr3, 0

return _ProtoHandler(&this->struct43, a1);

}
```

*Listing 2-3: Clearing debugging registers in Festi code*

The highlighted `writedr` instructions perform write operations on the debugging registers. As you can see, Festi writes zeros to these registers before executing the `_ProtoHandler` routine, which is responsible for handling the communication protocol between the malware and C&C servers.

#### The Method for Hiding the Malicious Driver on Disk

To protect and conceal the image of the malicious kernel-mode driver stored on the hard drive, Festi hooks the filesystem driver so that it can intercept and modify all requests sent to the filesystem driver to exclude evidence of its presence.

A simplified version of the routine for installing the hook is shown in Listing 2-4.

```c
NTSTATUS __stdcall SetHookOnSystemRoot(PDRIVER_OBJECT DriverObject,
                                       int **HookParams)
{
    RtlInitUnicodeString(&DestinationString, L"\\SystemRoot");
    ObjectAttributes.Length = 24;
    ObjectAttributes.RootDirectory = 0;
    ObjectAttributes.Attributes = 64;
    ObjectAttributes.ObjectName = &DestinationString;
    ObjectAttributes.SecurityDescriptor = 0;
    ObjectAttributes.SecurityQualityOfService = 0;

    // ➊
    NTSTATUS Status = IoCreateFile(&hSystemRoot, 0x80000000, &ObjectAttributes,
                                   &IoStatusBlock, 0, 0, 3u, 1u, 1u, 0, 0, 0, 0,
                                   0x100u);
    if (Status < 0)
        return Status;

    // ➋
    Status = ObReferenceObjectByHandle(hSystemRoot, 1u, 0, 0,
                                       &SystemRootFileObject, 0);
    if (Status < 0)
        return Status;

    // ➌
    PDEVICE_OBJECT TargetDevice = IoGetRelatedDeviceObject(SystemRootFileObject);
    if (!TargetDevice)
        return STATUS_UNSUCCESSFUL;

    ObfReferenceObject(TargetDevice);

    Status = IoCreateDevice(DriverObject, 0xCu, 0, TargetDevice->DeviceType,
                            TargetDevice->Characteristics, 0, &SourceDevice);
    if (Status < 0)
        return Status;

    // ➍
    PDEVICE_OBJECT DeviceAttachedTo = IoAttachDeviceToDeviceStack(SourceDevice,
                                                                  TargetDevice);
    if (!DeviceAttachedTo)
    {
        IoDeleteDevice(SourceDevice);
        return STATUS_UNSUCCESSFUL;
    }

    return STATUS_SUCCESS;
}
```

*Listing 2-4: Hooking the filesystem device driver stack*

The malware first tries to obtain a handle to the special system file `SystemRoot`, which corresponds to the Windows installation directory ➊. Then, by executing the `ObReferenceObjectByHandle` system routine ➋, Festi obtains a pointer to the `FILE_OBJECT` that corresponds to the handle for `SystemRoot`. The `FILE_OBJECT` is a special data structure used by the operating system to manage access to device objects and so contains a pointer to the related device object. In our case, since we opened a handle for `SystemRoot`, the `DEVICE_OBJECT` is related to the operating system filesystem driver. The malware obtains the pointer to the `DEVICE_OBJECT` by executing the `IoGetRelatedDeviceObject` system routine ➌, then creates a new device object and attaches it to the acquired device object pointer by calling `IoAttachDeviceToDeviceStack` ➍, as shown in the layout of the filesystem device stack in Figure 2-8. Festi's malicious device object is located on top of the stack, meaning the I/O requests intended for the filesystem are rerouted to the malware. This allows Festi to conceal itself by altering request and return data to and from the filesystem driver.

![image](img/02fig08.jpg)

*Figure 2-8: Layout of the filesystem device stack hooked by Festi*

At the very bottom of Figure 2-8, you can see the filesystem driver object and the corresponding device object that handles OS filesystem requests. Some additional filesystem filters might be attached here too. Toward the top of the figure, you can see the Festi driver attached to the filesystem device stack.

This design uses and closely follows the Windows stacked I/O driver design, reproducing the design pattern of the native OS. By now, you probably see the trend: the rootkit aims to blend with the OS cleanly and reliably, emulating winning OS design patterns for its own modules. In fact, you can learn a lot about OS internals from analyzing aspects of rootkits, such as Festi's handling of input/output requests.

In Windows, a filesystem I/O request is represented as an `IRP`, which goes through the stack from top to bottom. Every driver in the stack can observe and modify the request or returned data. This means that, as shown in Figure 2-8, Festi can modify `IRP` requests addressed to the filesystem driver and any corresponding returned data.

Festi monitors the `IRPs` using the `IRP_MJ_DIRECTORY_CONTROL` request code, used to query the contents of the directory, watching for queries related to where the malware's kernel-mode driver is located. If it detects such a request, Festi modifies the returned data from the filesystem driver to exclude any entry corresponding to the malicious driver file.

#### The Method for Protecting the Festi Registry Key

Festi also hides a registry key corresponding to the registered kernel-mode driver using a similar method. Located in `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services`, the registry key contains Festi's driver type and the path to the driver's image on the filesystem. This makes it vulnerable to detection by security software, so Festi must hide the key.

To do so, Festi first hooks the `ZwEnumerateKey`, a system service that queries information on a specified registry key and returns all of its subkeys, by modifying the `System Service Descriptor Table (SSDT)`, a special data structure in the operating system kernel that contains addresses of the system service handlers. Festi replaces the address of the original `ZwEnumerateKey` handler with the address of the hook.

##### WINDOWS KERNEL PATCH PROTECTION

It's worth mentioning that this hooking approach—modifying `SSDT`—works only on 32-bit Microsoft Windows operating systems. As mentioned in Chapter 1, the 64-bit editions of Windows implement `Kernel Patch Protection` (also known as PatchGuard) technology to prevent software from patching certain system structures, including `SSDT`. If PatchGuard detects a modification of any of the monitored data structures, it crashes the system.

The `ZwEnumerateKey` hook monitors requests addressed to the `HKLM\System\CurrentControlSet\Service` registry key, which contains subkeys related to kernel-mode drivers installed on the system, including the Festi driver. Festi modifies the list of subkeys in the hook to exclude the entry corresponding to its driver. Any software that relies on `ZwEnumerateKey` to obtain the list of installed kernel-mode drivers will not notice the presence of Festi's malicious driver.

If the registry is discovered by security software and removed during shutdown, Festi is also capable of replacing the registry key. In this case, Festi first executes the system routine `IoRegisterShutdownNotification` in order to receive shutdown notifications when the system is turned off. It checks the shutdown notification handler to see if the malicious driver and the corresponding registry key are present in the system, and if they're not (that is, if they've been removed), it restores them, guaranteeing that it will persist through reboot.

### The Festi Network Communication Protocol

- 与 C&C 服务器通信并执行恶意活动时，Festi 使用了一个自定义的网络通信协议，该协议必须防止窃听。在我们对 Festi 僵尸网络的调查过程中，^([2)我们获得了它通信的 C&C 服务器列表，发现虽然有些服务器专注于发送垃圾邮件，有些则进行 DDoS 攻击，但两者都实现了同一个通信协议。Festi 通信协议包含两个阶段：初始化阶段，用于获取 C&C IP 地址；工作阶段，用于请求任务描述。

#### 初始化阶段

在初始化阶段，恶意软件从僵尸二进制文件中获取 C&C 服务器的 IP 地址，这些域名已被存储其中。有趣的是，恶意软件手动从域名解析出 C&C 服务器的 IP 地址。具体做法是构造一个 DNS 请求报文，用于解析 C&C 服务器域名，并将该报文发送到两个 Google DNS 服务器 `8.8.8.8` 或 `8.8.4.4` 的 53 端口。回复中，Festi 获得可以用于后续通信的 IP 地址。

手动解析域名使僵尸网络对清除尝试更具韧性。如果 Festi 依赖本地 ISP 的 DNS 服务器进行域名解析，运营商可能会通过修改 DNS 信息阻止访问 C&C 服务器（例如，执法机构发出禁令阻止特定域名）。但通过手动构造 DNS 请求并发送至 Google 服务器，恶意软件绕过了 ISP 的 DNS 基础设施，使清除更加困难。

#### 工作阶段

工作阶段是 Festi 向 C&C 服务器请求任务信息的过程。通信通过 TCP 协议进行。发送给 C&C 服务器的网络数据包请求结构（如图 2-9 所示）由消息头和插件特定数据数组组成。

![image](img/02fig09.jpg)

*图 2-9：发送至 C&C 服务器的网络数据包布局*

消息头由配置管理插件生成，包含以下信息：

*   Festi 版本信息
*   是否存在系统调试器
*   是否存在虚拟化软件（VMWare）
*   是否存在网络流量监控软件（WinPcap）
*   操作系统版本信息

插件特定数据由一系列 `tag-value-term` 条目组成：

**Tag** 一个 16 位整数，指定后续值的类型  
**Value** 特定数据，可为字节、字、双字、以空字符终止的字符串或二进制数组  
**Term** 终止字，`0xABDC`，标识条目结束  

`tag-value-term` 方案为恶意软件提供了便捷的方式，将插件特定数据序列化为发送至 C&C 服务器的网络请求。

数据在发送前通过简单加密算法进行混淆。加密算法的 Python 实现如第 2-5 条所示。

```python
key = (0x17, 0xFB, 0x71, 0x5C)  # ➊

def decr_data(data):
    for ix in xrange(len(data)):
        data[ix] ^= key[ix % 4]
```

*第 2-5 条：网络加密算法的 Python 实现*

恶意软件使用固定 4 字节键的滚动异或算法。

### 绕过安全与取证软件

为在网络上与 C&C 服务器通信、发送垃圾邮件、进行 DDoS 攻击同时规避安全软件，Festi 依赖于在 Windows 内核模式下实现的 TCP/IP 栈。

发送和接收数据包时，恶意软件会根据协议类型打开 `\Device\Tcp` 或 `\Device\Udp` 设备的句柄，采用一种不引起安全软件注意的技巧获取句柄。在设计此技巧时，Festi 的作者再次展现了对 Windows 系统内部机制的卓越理解。

为控制主机的网络访问，部分安全软件通过拦截 `IRP_MJ_CREATE` 请求来监控对这些设备的访问，这些请求在有人尝试打开设备对象以进行网络通信时发送给传输驱动程序。这使得安全软件能够确定哪个进程在尝试通过网络通信。安全软件常用的监控方式包括：

*   捕获 `ZwCreateFile` 系统服务句柄，拦截所有尝试打开设备的请求
*   直接附加到 `\Device\Tcp` 或 `\Device\Udp`，拦截所有发送的 `IRP` 请求

Festi 巧妙规避了这两种监控手段，从而建立网络连接。

首先，Festi 不使用系统实现的 `ZwCreateFile` 系统服务，而是自行实现功能几乎相同的自定义系统服务。图 2-10 展示了自定义 `ZwCreateFile` 例程。

![image](img/02fig10.jpg)

*图 2-10：自定义 ZwCreateFile 例程*

可以看到，Festi 手动创建文件对象以与被打开的设备进行通信，并直接向传输驱动程序发送 `IRP_MJ_CREATE` 请求。因此，所有挂载在 `\Device\Tcp` 或 `\Device\Udp` 下的设备均不会在请求中被观察到，操作对安全软件不可见，如图 2-11 所示。

图左侧展示了 `IRP` 的正常处理流程：数据包会经过完整的驱动堆栈，堆栈内的所有驱动（包括安全软件）都会收到并检查数据包内容。图右侧展示了 Festi 绕过所有中间驱动，直接向目标驱动发送 `IRP` 数据包的方式。

![image](img/02fig11.jpg)

*图 2-11：绕过网络监控安全软件*

Festi 同样巧妙地规避了第二种安全软件技术。要直接向 `\Device\Tcp` 或 `\Device\Udp` 发送请求，恶意软件需要指向对应设备对象的指针。实现此操作的代码片段如第 2-6 条所示。

```c
RtlInitUnicodeString(&DriverName, L"\\Driver\\Tcpip");
RtlInitUnicodeString(&tcp_name, L"\\Device\\Tcp");
RtlInitUnicodeString(&udp_name, L"\\Device\\Udp");

// ➊
if (!ObReferenceObjectByName(&DriverName, 64, 0, 0x1F01FF,
                             IoDriverObjectType, 0, 0, &TcpipDriver))
{
    DevObj = TcpipDriver->DeviceObject;

    // ➋
    while (DevObj)  // 遍历 DEVICE_OBJECT 链表
    {
        if (!ObQueryNameString(DevObj, &Objname, 256, &v8))
        {
            // ➌
            if (RtlCompareUnicodeString(&tcp_name, &Objname, 1u))
            {
                // ➍
                if (!RtlCompareUnicodeString(&udp_name, &Objname, 1u))
                {
                    ObfReferenceObject(DevObj);
                    this->DeviceUdp = DevObj;  // 保存 \Device\Udp 指针
                }
            }
            else
            {
                ObfReferenceObject(DevObj);
                this->DeviceTcp = DevObj;  // 保存 \Device\Tcp 指针
            }
        }
        DevObj = DevObj->NextDevice;  // 获取下一个 DEVICE_OBJECT
    }
    ObfDereferenceObject(TcpipDriver);
}
```

*第 2-6 条：实现规避网络监控安全软件的技术*

Festi 通过执行 `ObReferenceObjectByName` 例程 ➊（一个未文档化的系统例程），并将指向目标驱动程序名称的 Unicode 字符串指针作为参数，获取 `tcpip.sys` 驱动对象的指针。随后恶意软件遍历与该驱动对象关联的设备对象列表 ➋，并将它们的名称与 `\Device\Tcp` ➌ 与 `\Device\Udp` ➍ 进行比较。

当恶意软件通过这种方式获得已打开设备的句柄后，它会利用该句柄在网络上发送和接收数据。尽管 Festi 能够规避安全软件，但仍可通过在比 Festi 更低层级（例如在 Network Driver Interface Specification，NDIS 层）运行的网络流量过滤器查看到它发送的数据包。

### The Domain Generation Algorithm for C&C Failure

Festi 的另一项显著特征是实现了域名生成算法（DGA），在 bot 配置数据中的 C&C 服务器域名不可达时作为后备机制使用。例如，当执法机构下架 Festi C&C 服务器的域名时，恶意软件可能无法下载插件和指令。该算法以当前日期为输入，输出一个域名。

Table 2-2 列出了 Festi 样本的 DGA 域名。可以看出，所有生成的域名都是伪随机的，这是 DGA 生成域名的典型特征。

**Table 2-2:** Festi 生成的 DGA 域名列表

| **Date** | **DGA domain name** |
| --- | --- |
| 07/11/2012 | `fzcbihskf.com` |
| 08/11/2012 | `pzcaihszf.com` |
| 09/11/2012 | `dzcxifsff.com` |
| 10/11/2012 | `azcgnfsmf.com` |
| 11/11/2012 | `bzcfnfsif.com` |

实现 DGA 功能使 botnet 对下线尝试具有弹性。即使执法机构成功关闭了主 C&C 服务器域名，恶意软件的 master 仍可通过 DGA 回退，继续掌控 botnet。

### Malicious Functionality

在介绍完根包根功能后，我们来看从 C&C 服务器下载的恶意插件。调查过程中，我们获得了这些插件的样本，并识别出三种类型：

*   `BotSpam.sys` 用于发送垃圾邮件
*   `BotDos.sys` 用于发起 DDoS 攻击
*   `BotSocks.sys` 用于提供代理服务

我们发现，不同的 C&C 服务器倾向于提供不同类型的插件：有些服务器只提供带有垃圾邮件插件的 bot，而其他服务器只提供 DDoS 插件，这表明恶意功能取决于 bot 向其注册的 C&C 服务器。Festi botnet 并非单一体，而是由针对不同目标的子 botnet 组成。

#### The Spam Module

`BotSpam.sys` 插件负责发送垃圾邮件。C&C 服务器会向它发送垃圾邮件模板以及收件人邮箱列表。Figure 2-12 展示了垃圾邮件插件的工作流程。

![image](img/02fig12.jpg)

*Figure 2-12: Festi 垃圾邮件插件工作流程图*

首先，插件通过加密连接向 C&C 服务器下载包含收件人邮箱、发件人参数以及实际垃圾邮件模板的列表。随后，它将垃圾邮件分发给收件人。与此同时，恶意软件会向 C&C 服务器报告状态，并请求更新邮箱列表和垃圾邮件模板。

插件随后通过扫描 SMTP 服务器的响应来检查已发送邮件的状态，寻找特定字符串以判断是否出现问题 —— 例如，若没有该地址的收件人，邮件未送达，或邮件被标记为垃圾邮件。若在 SMTP 服务器的响应中发现这些字符串，插件会优雅地结束与 SMTP 服务器的会话，并转到列表中的下一个地址。此举帮助恶意软件避免其发送 IP 被 SMTP 服务器拉入黑名单，从而阻止其继续发送垃圾邮件。

#### The DDoS Engine

`BotDos.sys` 插件允许 bot 对指定目标进行 DDoS 攻击。插件支持多种 DDoS 攻击类型，涵盖不同架构和软件环境的远程主机。攻击类型由 C&C 服务器下发的配置数据决定，包括 TCP 洪水、UDP 洪水、DNS 洪水和 HTTP 洪水攻击。

##### TCP Flood

在 TCP 洪水攻击中，bot 会向目标机器的端口发起大量连接。每次 Festi 连接到目标端口，服务器都会为处理该连接分配资源。很快服务器资源耗尽，停止响应客户端请求。

默认端口是 HTTP 端口 80，但可根据 C&C 服务器提供的配置信息进行修改，从而攻击监听在除 80 端口之外的 HTTP 服务器。

##### UDP Flood

在 UDP 洪水攻击中，bot 会发送长度随机（256 至 1,024 字节）且内容随机的 UDP 包。目标端口也随机生成，通常不开放。攻击导致目标主机大量发送 ICMP Destination Unreachable 响应，使目标机器不可用。

##### DNS Flood

bot 还能够进行 DNS 洪水攻击，向 DNS 服务端口 53 发送大量 UDP 包，包含请求解析 `*.com` 域名的随机生成域名的请求。

##### HTTP Flood

针对 Web 服务器的 HTTP 洪水攻击中，bot 的二进制文件包含大量不同的 User-Agent 字符串，用于创建大量 HTTP 会话，从而耗尽远程主机资源。Listing 2-7 展示了构建 HTTP 请求的代码片段。

```cpp
```
