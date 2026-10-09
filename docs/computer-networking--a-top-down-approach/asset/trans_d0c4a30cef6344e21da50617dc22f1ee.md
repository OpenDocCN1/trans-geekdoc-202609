

虽然 MIB 相关的 RFC 读起来相当枯燥乏味，但研究一个 MIB 对象的示例仍然很有教育意义（也就是说，就像吃蔬菜一样，这对你是“有益的”）。来自 [RFC 4293] 的 `ipSystemStatsInDelivers` 对象类型定义定义了一个 32 位只读计数器，用于跟踪在受管设备上接收到的 IP 数据报的数量，这些数据报已成功传递给上层协议。在下例中，`Counter32` 是 SMI 中定义的基本数据类型之一。

```text
ipSystemStatsInDelivers OBJECT-TYPE
    SYNTAX Counter32
    MAX-ACCESS read-only
    STATUS current
    DESCRIPTION
        "The total number of datagrams successfully delivered to IP user-protocols (including ICMP).
        When tracking interface statistics, the counter of the interface to which these datagrams
        were addressed is incremented. This interface
        might not be the same as the input interface
        for some of the datagrams.
        Discontinuities in the value of this counter can
        occur at re-initialization of the management
        system, and at other times as indicated by the
        value of ipSystemStatsDiscontinuityTime."
    ::= { ipSystemStatsEntry 18 }
```

### 5.7.3 网络配置协议 (NETCONF) 和 YANG

NETCONF 协议运行在管理服务器与受管网络设备之间，提供消息机制以：(i) 在受管设备上获取、设置和修改配置数据；(ii) 查询受管设备的运行数据和统计数据；以及 (iii) 订阅由受管设备生成的通知。管理服务器通过向受管设备发送配置（这些配置在结构化 XML 文档中指定）并在受管设备上激活配置来主动控制该设备。NETCONF 使用远程过程调用 (RPC) 范式，其中协议消息也以 XML 编码，并通过诸如基于 TLS（传输层安全）协议（在第 8 章中讨论）的 TCP 上的安全、面向连接的会话在管理服务器和受管设备之间交换。

![](img/059c6683459cb0a4f802be65ff31bb03_457_0.png)

图 5.22 展示了一个 NETCONF 会话示例。首先，管理服务器与受管设备建立安全连接。（在 NETCONF 术语中，管理服务器实际上被称为“客户端”，而受管设备被称为“服务器”，因为管理服务器是建立与受管设备连接的一方。但为了与图 5.20 中展示的传统网络管理服务器/客户端术语保持一致，我们将在这里忽略这种称呼。）一旦建立安全连接，管理服务器和受管设备将交换 `<hello>` 消息，声明它们的“能力”——即补充 [RFC 6241] 中基础 NETCONF 规范的 NETCONF 功能。管理服务器和受管设备之间的交互采用远程过程调用的形式，使用 `<rpc>` 和 `<rpc-response>` 消息。这些消息用于获取、设置、查询和修改设备配置、运行数据和统计数据，以及订阅设备通知。设备通知本身是受管设备主动使用 NETCONF `<notification>` 消息发送给管理服务器的。会话通过 `<session-close>` 消息关闭。

表 5.3 展示了一些管理服务器可以在受管设备上执行的重要 NETCONF 操作。与 SNMP 的情况类似，我们看到用于获取运行状态数据（`<get>`）和事件通知的操作。然而，`<get-config>`、`<edit-config>`、`<lock>` 和 `<unlock>` 操作展示了 NETCONF 对设备配置的特殊强调。使用表 5.3 中所示的基本操作，还可以创建一组更复杂的网络管理事务，这些事务要么在*一组*设备上原子地（即作为一组）且成功地完成，要么完全反转并使设备恢复到交易前的状态。这种多设备事务——“使[运营商]能够专注于*整个*网络的*配置*，而不是单个设备”——是 [RFC 3535] 中提出的重要运营商需求。

NETCONF 的完整描述超出了本文的范围；[RFC 6241, RFC 5277, Claise 2019; Schonwalder 2010] 提供了更深入的覆盖。

但由于这是我们要首次看到格式化为 XML 文档的协议消息（而不是具有报头字段和消息体的传统消息，例如图 5.21 中所示的 SNMP PDU），让我们以两个示例来结束我们对 NETCONF 的简要研究。

在第一个示例中，从管理服务器发送到受管设备的 XML 文档是一个 NETCONF `<get>` 命令，请求所有设备配置和运行数据。通过此命令，服务器可以了解设备的配置。

```xml
<?xml version="1.0" encoding="UTF-8"?>
<rpc message-id="101"
     xmlns="urn:ietf:params:xml:ns:netconf:base:1.0">
  <get/>
</rpc>
```

虽然很少有人能完全直接解析 XML，但我们看到 NETCONF 命令相对易读，并且比我们在图 5.21 中看到的 SNMP PDU 格式更像 HTTP 和 HTML。RPC 消息本身跨越第 02–05 行（我们在此处添加了行号以用于教学目的）。该 RPC 的消息 ID 值为 101，在第 02 行中声明，并包含单个 NETCONF `<get>` 命令。来自设备的回复包含匹配的 ID 号（101），以及设备的所有配置数据（当然是 XML 格式），从第 04 行开始，最终以闭合的 `<rpc-reply>` 结束。

```xml
<?xml version="1.0" encoding="UTF-8"?>
<rpc-reply message-id="101"
     xmlns="urn:ietf:params:xml:ns:netconf:base:1.0">
  <!-- . . all configuration data returned... -->
</rpc-reply>
```

在下方的第二个示例中（改编自 [RFC 6241]），从管理服务器发送到受管设备的 XML 文档将名为“Ethernet0/0”的接口的最大传输单元 (MTU) 设置为 1500 字节：

```xml
<?xml version="1.0" encoding="UTF-8"?>
<rpc message-id="101"
     xmlns="urn:ietf:params:xml:ns:netconf:base:1.0">
  <edit-config>
    <target>
      <running/>
    </target>
    <config>
      <top xmlns="http://example.com/schema/1.2/config">
        <interface>
          <name>Ethereal0/0</name>
          <mtu>1500</mtu>
        </interface>
      </top>
    </config>
  </edit-config>
</rpc>
```

**表 5.3 选定的 NETCONF 操作**

| NETCONF 操作 | 描述 |
| :--- | :--- |
| `<get-config>` | 获取给定配置的全部或部分。设备可能有多个配置。始终有一个*运行中*的配置，描述设备的*当前*（运行中）配置。 |
| `<get>` | 获取配置状态和运行状态数据的全部或部分。 |
| `<edit-config>` | 更改受管设备上指定配置的全部或部分。如果指定了*运行中*配置，则设备的*当前*（运行中）配置将被更改。如果受管设备能够满足请求，则发送包含 `<ok>` 元素的 `<rpc-reply>`；否则返回 `<rpc-error>` 响应。发生错误时，设备的配置状态可以回滚到其先前状态。 |
| `<lock>`, `<unlock>` | `<lock>`（或 `<unlock>`）操作允许管理服务器锁定（或解锁）受管设备的整个配置数据系统。锁旨在是短期的，允许客户端进行更改，而不必担心与其他来源的 NETCONF、SNMP 或 CLI 命令发生交互。 |
| `<create-subscription>`, `<notification>` | 此操作发起事件通知订阅，将从受管设备向管理服务器发送针对指定感兴趣事件的*异步*事件 `<notification>`，直到订阅终止。 |

