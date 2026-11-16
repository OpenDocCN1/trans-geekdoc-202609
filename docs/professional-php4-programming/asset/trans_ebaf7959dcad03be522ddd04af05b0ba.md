

在编译 PHP 二进制文件时，要包含 SNMP 功能，我们需要确保在配置时使用 --with-snmp 标志。另外，在编译 PHP 时需要使用 --enable-ucd-snmp-hack 选项，以确保已纳入针对 UCD SNMP 错误的变通方案。在 Microsoft Windows 平台上，除 Windows NT 以外的操作系统可能不提供这些函数。

## snmpget()

```
string snmpget(string hostname, string community, string object_id
[, int timeout [, int retries]])
```

此函数通过查询由 hostname 参数指定的主机，返回由 object_id 参数指定的 SNMP 对象的值。community 参数指定需要考虑的社区，可选的 timeout 参数指定函数等待响应的时间。可选的 retries 参数指定在发生超时后执行 get 请求的尝试次数：

```php
<?php
$udpOut = snmpget("localhost", "public", "udp.udpOutDatagrams.0");
echo("The number of UDP datagrams that have been sent out is $udpOut <br>");
?>
```

上述脚本打印从本机发出的 UDP 数据包总数。

## snmpset()

```
boolean snmpset(string hostname, string community, string object_id,
string type, mixed value [, int timeout [, int retries]])
```

此函数将由 object_id 参数指定的 SNMP 对象设置为由 value 参数指定的值。type 参数指定 object_id 参数的类型。timeout 和 retries 参数分别指定响应的超时值以及在发生超时后重试 set 请求的尝试次数：

```php
<?php
echo("Attempting to enable IP forwarding<br>");
if (snmpset("localhost", "public", "system.sysLocation.0", "s",
    "North Conference Room") == false) {
    echo("IP forwarding could not be enabled. <br>");
} else {
    echo("IP forwarding is now enabled. <br>");
}
```

此函数在 localhost 上启用 IP 转发。主机需要启用 IP 转发才能充当 IP 路由器。

## snmpwalk()

```
array snmpwalk(string hostname, string community, string object_id
[, int timeout [, int retries]])
```

snmpwalk() 用于浏览 OID 树的整个分支。它获取由 object_id 参数指定的节点下的所有对象。如果将空字符串用作 object_id 参数，则返回代理的整个 OID 树。结果作为 SNMP 对象数组返回；出错时返回 false：

```php
<?php
$tcpObjs = snmpwalk("localhost", "public", "tcp");

echo("The list of TCP objects are:<br>");
for ($i = 0; $i < count($tcpObjs); ++$i) {
    echo($tcpObjs[$i]);
}
?>
```

## snmpwalkoid()

```
array snmpwalkoid(string hostname, string community, string object_id [, int timeout [, int retries]])
```

此函数的用途与 snmpwalk() 相同，唯一的区别在于返回的列表是关联数组：

```php
<?php
$tcpObjs = snmpwalkoid("localhost", "public", "tcp");

echo("The list of TCP objects are:<br>");
do {
    echo($tcpObjs[key($tcpObjs)]);
} while(next($tcpObjs));
?>
```

## snmp_get_quick_print() and snmp_set_quick_print()

```
boolean snmp_get_quick_print
void snmp_set_quick_print (boolean quick_print)
```

默认情况下，发出 get 请求时，SNMP 函数返回对象名称、类型以及描述对象的其他信息（取决于对象类型）。当直接显示返回值时，这很有用。但是，在脚本中可能需要使用对象的实际值。在这种情况下，可以打开“快速打印”功能，这样只返回值。

如果“快速打印”被禁用，snmp_get_quick_print() 函数返回 false，否则返回 true。snmp_set_quick_print() 函数可以传入 true 参数来启用“快速打印”功能，传入 false 参数来禁用它：

```php
<?php
if (snmp_get_quick_print() == false) {
    echo("Quick print is currently disabled <br>");
    $udpOut = snmpget("localhost", "public", "udp.udpOutDatagrams.0");
    echo("No. of outbound UDP packets = $udpOut");
    snmp_set_quick_print(true);
    echo("Quick print is enabled now <br>");
    $udpOut = snmpget("localhost", "public", "udp.udpOutDatagrams.0");
    echo("No. of outbound UDP packets = $udpOut");
} else {
    echo("Quick print is currently enabled <br>");
    $udpOut = snmpget("localhost", "public", "udp.udpOutDatagrams.0");
    echo("No. of outbound UDP packets = $udpOut");
    snmp_set_quick_print(false);
    echo("Quick print is disabled now <br>");
    $udpOut = snmpget("localhost", "public", "udp.udpOutDatagrams.0");
    echo("No. of outbound UDP packets = $udpOut");
}
?>
```

该脚本说明了启用和禁用“快速打印”功能的效果。

## Summary

在本章中，我们探讨了 PHP 中可用的各种网络功能，以及支撑这些功能的某些底层技术。尽管 TCP/IP 协议的大部分内部工作机制并未向应用程序开发者公开，但我们仍需了解该协议套件的某些方面。IP 网络中资源的命名便是其中之一。DNS 是可用的事实上的“名称到 IP 地址”解析机制，PHP 支持相当多的函数来访问 DNS 资源。
YP/NIS 是另一种此类机制，尽管大多局限于内网环境。PHP 提供了 YP/NIS 函数来执行资源查找。

截至 4.0.6 版本，PHP 中的 Socket 支持尚处于初级阶段，但我们仍将探讨可用的接口，以使用套接字实现客户端-服务器应用程序之间的通信。在本章过程中，我们还开发了一个邮件客户端应用程序，以综合我们对套接字和 DNS API 的理解。SNMP 协议用于管理网络资源，PHP 对 SNMP 代理操作提供了一些基本支持。

## 14 LDAP

LDAP（轻量级目录访问协议）已发展成为近年来最流行的开放目录访问机制。基本上，这意味着信息可以存储在可从远程位置访问的层次结构中。良好的示例包括电子邮件地址查找表、白页和公司结构信息。

在本章中，我们将探讨：

- 目录服务的概念，特别是 LDAP
- LDAP 术语和 LDAP 模型
- LDAP 的实际应用
- PHP 提供的用于编程 LDAP 客户端应用程序的 API
- 使用 PHP LDAP 客户端 API 访问 LDAP 服务器的示例应用程序

## Overview of Directories

目录的典型示例是电话簿或地址簿。当我们需要查找关于某人或某企业的特定信息（例如我们知道该人的姓名或企业名称等区分特征）时，我们会使用白页目录。当我们需要查找关于某群体的更一般信息，例如我们需要查找所有专门销售可重复使用小部件的本地商家列表时，我们会参考黄页目录。

当我们使用电子邮件或 Web 浏览器时，会使用目录。电子邮件客户端将邮件发送到邮件服务器。邮件服务器查找内部表以定位收件人拥有帐户的主机。同样，当网站名称输入浏览器时，浏览器会联系域名系统（DNS）服务器。DNS 服务器查找维护 DNS 名称与托管网站的计算机 IP 地址之间映射的内部表。服务器将映射返回给浏览器，浏览器随后使用其 IP 地址直接与 Web 服务器通信。理想情况下，此类信息可以存储在目录中，并可由任何能够使用目录协议的客户端访问。事实上，现在有很多安装使用 DNS-to-LDAP 网关实现了启用目录的 DNS 查找。

## LDAP

LDAP 发展源于对现有 X.500 协议提供的目录服务进行补充的需求。X.500 协议是**重量级**的，这是由于各种事务开销，以及它使用笨重的 OSI 网络堆栈进行底层网络传输的事实。尽管 LDAP 最初是作为 X.500 目录的网关起步的，使用 TCP/IP 协议进行网络传输，但此后它发展为一个具有全局范围的独立联网目录服务器协议。因此，在需要大量数据来有效管理我们的工作和生活时，LDAP 充当了数据管理者的角色，且不带不必要的开销。在版本 3 中，LDAP 以 LDAP 控件的形式提供广泛的自定义和可扩展性功能。

## LDAP vs. Traditional Databases

LDAP 的设计和优化是为了处理简单数据，这些数据一旦写入，很少会被修改。传统数据库的设计和优化是为了处理数据的查询和更新操作，旨在处理高度复杂的数据，而 LDAP 基本上是一种基于文本的目录存储系统。

此外，传统数据库是为事务完整性和一致性而构建的。对于 LDAP 来说，这并非真正的优先事项，因为 LDAP 中的数据大多是读多于写。因此，LDAP 的轻量化源于它是一种处理简单数据的简单协议。

LDAP 服务器通常使用相当简化的后端数据库，例如 Berkeley 数据库或 GDBM（GNU 数据库管理器）。这些数据库仅提供必要的功能，没有额外的开销。事实上，Berkeley 数据库的维护人员针对 OpenLDAP 和 Netscape Directory Server 对数据库进行了优化，以便将其用作后端数据存储。然而，许多商业供应商选择使用传统数据库作为数据存储来实现 LDAP 服务器，最著名的是 Oracle 的 OID 和 Microsoft 的 ICL i.500。当使用平面文件或简化数据库作为数据存储的 LDAP 服务器无法扩展以处理非常高的查询量时，这种解决方案通常是可取的。

目录组织数据的方式与传统数据库组织数据的方式有很大不同。这种差异在以下几个方面表现得很明显：

- 数据库通常在记录中只具有名称唯一的字段；例如，员工记录中有一个名为 `telephonenumber` 的字段。LDAP 目录并非如此。例如，数据库中的员工记录可能有一个名为 `telephonenumber` 的字段，就记录而言，只有一个且仅有一个具有此名称的字段。

