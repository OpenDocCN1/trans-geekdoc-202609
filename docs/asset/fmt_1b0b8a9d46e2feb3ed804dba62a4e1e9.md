
# 第 14 章 网络战：一种威慑架构

被用作并发访问的黑板，用于表示有关网络、服务器和攻击者的任意信息。该知识库可以进行自动分析，并以多种方式利用，例如归属判定。

这些 IP 地址的某些 whois 记录似乎属于合法的企业，他们可能不知道自己被指参与了“Aurora”攻击。这些互联网地址（以及它们与 Aurora 的关联）处于公共领域，并于 2010 年 3 月 13 日从 US-CERT 网站 `www.us-cert.gov/cas/techalerts/TA10-055A.html` 下载。

# 列表 14-1：原型知识库的示例输出

```
RECORD: 1
'IPv4 Address': '173.201.21.161', 'FTP Open on Port': '21', 'RDP Open on Port': '3389', 'Ping Response': 'Alive', 'Attack Organization': 'Aurora', 'Attack Role': 'Control Server'
RECORD: 2
'IPv4 Address': '69.164.192.46', 'Ping Response': 'Alive', 'Attack Organization': 'Aurora', 'Attack Role': 'Control Server'
RECORD: 3
'IPv4 Address': '168.95.1.1', 'Ping Response': 'Alive', 'Attack Organization': 'Aurora', 'Attack Role': 'Control Server'
RECORD: 4
'IPv4 Address': '203.69.66.1', 'Ping Response': 'Alive', 'Attack Organization': 'Aurora', 'Attack Role': 'Control Server'
```

# 架构原型

接下来的章节展示了多线程和类僵尸网络分布式扫描的一些架构原型。我们测量了一些性能基准并将其用于校准僵尸网络性能的确定性预测。这些实验提供了一些有趣的见解，包括技术的局限性，以及用于军事僵尸网络生产实现的改进架构。示例使用了 Python 2.6 版本。

僵尸网络的 Python 代码将线程概念与分布式处理相结合，包括改编自 Python.org 在线文档（`http://docs.python.org`）。Python 基础语言和内置库中有约 1,500 个函数，以及许多附加代码库。对这些函数进行高效搜索是网络取证的一项关键技能。在 Python 2.6 中进行编程时，结合 Google 进行搜索非常有帮助，因为可以过滤掉 Python 3.1 和 3.2 的冲突文档。

## 基准代码：并发扫描

这些原型是增量式开发的，从 Linux/Unix Bash 脚本中的串行扫描开始。这些扫描随后使用 Python 中的多线程进行实现（参见列表 14-2）。使用线程代码观察到性能剧增，这表明这种形式的扫描在渗透测试中具有实际应用。

# 列表 14-2：快速多线程扫描的 Python 源代码

```python
Thread.py
#!/usr/bin/python
import os
from threading import Thread
import time
start=time.ctime()
print start

scan="ping -n -w 100 " # windows
scan="ping -c -w 1 " # linux/unix
scan="nmap -AF " 
scan="nmap -p 22,23,80,445 " 
max=65

class threadclass(Thread):
    def __init__(self,ip):
        Thread.__init__(self)
        self.ip = ip
        self.status = None
    def run(self):
        result = os.popen(scan+self.ip,"r")
        self.status=result.read()

threadlist = []

for host in range(1,max):
    ip = "192.168.1."+str(host)
    current = threadclass(ip)
    threadlist.append(current)
    current.start()

for t in threadlist:
    t.join()
    print("Status from",t.ip,"is",repr(t.status))
```

在 `Thread.py` 的 Python 代码中，每个并行线程都是类的实例。在第一个循环中，线程被初始化并赋予了一个要扫描的 IP 地址，然后启动线程。这些线程在单个主机上并行执行扫描。在第二个循环中，线程重新回到主进程并打印结果。

## 用于分布式扫描的僵尸网络

下面的 Python 架构原型实现了一个简单的僵尸网络，它可以执行几种类型的并行扫描，如 ping 探测和 nmap 扫描。该架构是图 14-5 所示通用僵尸网络的子集，包括一个控制服务器和多个僵尸节点。该原型有两个源代码列表：僵尸代码（`Server.py`）和命令服务器代码（`Master.py`）。

首先，在每个僵尸机器上运行 `Server.py` 代码（参见列表 14-3）。`Server.py` 导入了一个与平台相关的文件（`platform_windows.py`、`platform_linux.py` 或 `platform_solaris.py` 之一），该文件包含了扫描命令的 Windows 或 Linux 语法（测试了五个操作系统）。`Server.py` 显示了代码，注册了请求处理程序和命令函数，然后等待来自控制服务器 `Master.py` 的远程过程调用（使用 XMLRPC）。

# 列表 14-3：僵尸节点的 Python 源代码

```python
Server.py
#!/usr/bin/python
import os
from SimpleXMLRPCServer import SimpleXMLRPCServer
from SimpleXMLRPCServer import SimpleXMLRPCRequestHandler
from platform_linux import * # import platform_linux

class RequestHandler(SimpleXMLRPCRequestHandler):
    pass

server = SimpleXMLRPCServer(("localhost", 8000), requestHandler=RequestHandler)

def command(key):
    output = os.popen(scan+key, "r")
    return output.read()

server.register_function(command, "command")
server.serve_forever()
```

串行扫描中重量级的操作系统（OS）进程创建与线程扫描中轻量级、高度并行的线程创建之间存在重大的理论性能差异，这将在下一节中进行探讨。

| 配置 | Ping -c1 -w1 (分钟/秒) | 异常 | Nmap -p 22,23,35,80,445 (分钟/秒) | 异常 |
|---|---|---|---|---|
| 扫描端口数 | 1 | | 5 | |
| 扫描 IP 数 | 65 | | 65 | |
| 范围内的目标机器数 | 6 | | 6 | |
| 串行 Python 扫描（Bash 时间相似） | 1:00 | | 0:18 | |
| 线程化 Python | 0:01 | | 0:01 | |
| 包含 2 个肉鸡的僵尸网络 | 0:34 | 20% | 0:25 | 0% |
| 包含 3 个肉鸡的僵尸网络 | 0:26 | 6% | 0:13 | 0% |
| 包含 4 个肉鸡的僵尸网络 | 0:16 | 0% | 0:07 | 0% |

**图 14-7：** 僵尸网络实现的性能基准比较

曾尝试基准大量并行运行线程引起的抖动影响。图 14-8 中的曲线横轴表示线程数（0..300），垂直轴显示 `ping -c1 -w1` 扫描的秒数（0..12）。在 Windows Vista 机器上，该曲线在 150 个线程左右有一个明显的转折点。在预测中，最大线程被限制在 25 个左右以抑制这种影响。

![](img/58b756e5b149184e369c845a987fc3a2_326_0.png)

**图 14-8：** 多线程的可扩展性影响

## 性能的确定性模型

扫描性能需要用一组确定性方程进行建模，以便进行时间估计。

假设有 N 次扫描要执行，每次扫描耗时为 `t(i)`，并伴有相关的开销 `h(j)`。在这些模型中，`h(j)` 被假设为常数，但实际上，它们会随着网络利用率、内存利用率、进程抖动等因素而变化。在生产实现中，需要对这些其他因素进行管理和限制。

### 串行扫描

在原型中，Unix/Linux Bash 脚本和 Python 串行扫描的性能几乎相同。

```
T(s) = sum(t(i)) from i=1..N + N*h(s) + h(r)
```

`h(s)` 是单次扫描开销，`h(r)` 是最终报告开销。

### 并行（线程）扫描

此模型模拟了 `Thread.py` 中所示线程扫描代码。

```
T(p) = max(t(i)) from i=1..N + N*h(p) + h(r)
```

`h(p)` 是每个线程扫描的开销。注意串行方程是 Order(N)，随扫描次数缩放；而并行方程是 Order(1)，或仅取决于最长任务的常数时间（理论上假设线程无限）。“性能基准”小节涵盖了线程抖动影响。

### 分布式串行扫描

此模型模拟了使用 `Server.py` 和 `Master.py` 实现的僵尸网络。

```
T(ds) = max(sum(t(i)) from i=k*m+1..(k+1)*m + m*h(s)) from i=L..N + (N/m)*h(d) + h(r)
```

其中 `m` 是每个肉鸡机器人扫描次数，`k` 是扫描批大小，`h(d)` 是每个批次的开销——例如分布式消息、应用程序代码、输入/输出 (IO) 和操作系统。该方程与 Order(N/m) 成正比。

### 分布式并行（线程）扫描

这是我们尚未实现的理论僵尸网络，但通过将线程移动到肉鸡并使用限制和管理故障的主代码，可能代表了最佳架构选择之一。

```
T(dp) = max(t(i)+m*h(p)) + (N/m)*h(d) + h(r)
```
