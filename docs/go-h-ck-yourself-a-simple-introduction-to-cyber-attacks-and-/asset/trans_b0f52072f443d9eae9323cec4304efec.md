

对于此黑客攻击，我们将安装一个名为 `Instrument Cluster Simulator (ICSim)` 的软件包，这是一个虚拟仪表板，可让你像在实际车辆中一样查看和交互速度表、转向灯和车门锁。Craig Smith（又名 zombieCraig）和 OpenGarages 团队构建了 ICSim，以帮助黑客和研究人员安全且合乎道德地学习如何处理汽车网络，而不会损坏或摧毁实际车辆或无辜行人。

1. 打开终端窗口并更新 Kali 的软件包列表：

```
kali@kali:~$ sudo apt update
```

2. 现在通过输入以下内容安装 ICSim 的依赖项：

```
kali@kali:~$ sudo apt install libsdl2-dev libsdl2-image-dev can-utils
```

请注意，两个 `libsdl2` 包都在数字 2 之前使用小写字母 `L` 拼写。

3. 这样安装 ICSim：

```
kali@kali:~$ cd ~ 
kali@kali:~$ git clone https://github.com/zombieCraig/ICSim.git 
```

4. 在你的机器上设置 can-utils：

```
kali@kali:~$ cd ~
kali@kali:~$ git clone https://github.com/linux-can/can-utils
kali@kali:~/can-utils$ make
kali@kali:~/can-utils$ sudo make install
```

5. 使用这些命令设置 ICSim 仪表板模拟器软件：

```
kali@kali:~/can-utils$ cp lib.o ~/ICSim
kali@kali:~/can-utils$ cd ~/ICSim
kali@kali:~/ICSim$ make clean
kali@kali:~/ICSim$ make
```

现在运行我们的虚拟汽车仪表盘并开始黑客攻击！

## 准备虚拟 CAN 总线网络

汽车的网络被称为 `CAN bus`，或者简称 `CAN`。自 20 世纪 90 年代以来，CAN 总线一直用于大多数汽车，以控制各种系统和传感器，例如转向和制动、收音机、空调和娱乐中心。你刚刚安装的 ICSim 软件创建了一个 `virtual CAN (VCAN)` 总线网络，我们将学习攻击该网络。我们现在创建该网络并完成汽车黑客环境的设置。

1. 要设置 VCAN，请在 ICSim 文件夹内的终端中输入此命令：

```
kali@kali:~/ICSim$ sh setup_vcan.sh
```

2. 通过在终端中输入 `ip addr` 确保 VCAN 设置正确。你应该能看到自己的 IP 地址以及一个名为 `vcan0` 的新网络。

```
kali@kali:~/ICSim$ ip addr
--snip--
3: vcan0: <NOARP,UP,LOWER_UP> mtu 72 qdisc noqueue state UNKNOWN group default qlen 1000 link/can
```

3. 在终端中输入以下内容，指示它先使用我们刚刚创建的 vcan0 网络运行 ICSim，然后等待我们的命令：

```
kali@kali:~/ICSim$ ./icsim vcan0 &
```

你应该会看到一个模拟的仪表板，如 [图 10-1](#c10.xhtml#figure10-1) 所示。

![图 10-1：ICSim 程序显示带有速度表、转向灯等的模拟汽车仪表板！](image_fi/502000c10/f10001.png)

图 10-1：ICSim 程序显示带有速度表、转向灯等的模拟汽车仪表板！

4. 在 vcan0 上启动控制器应用程序：

```
kali@kali:~/ICSim$ ./controls vcan0 &
```

CANBus 控制面板窗口应该会打开。它看起来很像视频游戏控制器。

5. 通过单击窗口的任何角并拖动，调整控制面板的大小，使 ICSim 窗口可见。

6. 右键单击控制面板窗口的顶部栏并选择 `Always on Top`，如 [图 10-2](#c10.xhtml#figure10-2) 所示。

![图 10-2：保持控制器应用程序可见且易于访问](image_fi/502000c10/f10002.png)

图 10-2：保持控制器应用程序可见且易于访问

要驾驶虚拟汽车，请单击 CANBus 控制面板窗口，然后使用键盘发送命令。可用命令列在 [表 10-1](#c10.xhtml#table10-1) 中。按上箭头加速，使用左箭头和右箭头控制转向灯，依此类推。

表 10-1：CANBus 控制面板的键盘控制

| `Function` || `Key(s)` |

| --- | --- |

| `Accelerate` || 按住上箭头 (↑) |

| --- | --- |

| `Signal a left or right turn` || 按住左箭头或右箭头 (←/→) |

| `Unlock front-left or front-right door` || right\-SHIFT\-A 或 right-SHIFT\-B |

| `Unlock back-left or back-right door` || right\-SHIFT\-X 或 right-SHIFT\-Y |

| `Lock all doors` || 按住 right\-SHIFT + 轻按 left\-SHIFT |

| `Unlock all doors` || 按住 left\-SHIFT + 轻按 right\-SHIFT |

控制器应用程序是与 VCAN 交互的唯一方式——除非我们对其进行黑客攻击。

## 黑客攻击汽车

我们的汽车黑客攻击冒险将遵循测试大多数 IoT 设备安全性时使用的相同步骤：

1. 使用程序查看和记录控制器应用程序与仪表板之间 vcan0 网络上的流量。这种程序称为 `packet sniffer`，因为发送到网络上的消息称为 `packets`。

2. 识别哪些网络数据包和命令控制哪些汽车系统或功能。

3. 通过将捕获的数据包重新发送到 vcan0 网络，或从终端编写自己的命令来控制汽车。

### 查看数据包

我们将使用 `cansniffer`，即 can-utils 内置的数据包嗅探器，来监听我们的模拟汽车网络。

1. 在终端窗口中，使用以下命令启动 `cansniffer`：

```
kali@kali:~/ICSim$ cansniffer -c vcan0
```

2. 将终端窗口调整为又高又窄（如 [图 10-3](#c10.xhtml#figure10-3) 所示），以便更容易查看 `cansniffer` 消息。你可能还需要按 CTRL 和 − 几次来减小字体大小。

3. 单击 CANBus 控制面板窗口并向虚拟汽车发送一些命令。尝试加速、使用转向灯等。

`cansniffer` 工具拦截在控制器应用程序和仪表板之间在 vcan0 上发送的数据包，并在终端窗口中显示它们。窗口中的每一行代表一个数据包。网络每秒传输几百个数据包，因此它们会很快闪过。

让我们看一个示例数据包，看看可以找到什么信息。以下是 [图 10-3](#c10.xhtml#figure10-3) 中显示的数据包之一：

```
10.204188 2244 300 00 00 01 06 4.....
```

![图 10-3：`cansniffer` 数据包嗅探器显示我们 vcan0 网络上的消息。](image_fi/502000c10/f10003.png)

图 10-3：`cansniffer` 数据包嗅探器显示我们 vcan0 网络上的消息。

第一列是一个 `timestamp`，表示发送数据包的时间。第二列是消息发送到或来自的系统的 ID 号。正如我们将发现的那样，CAN ID# 244 代表速度表。第三列是 CAN 消息数据，由十六进制值表示，第四列包含以可打印字符表示的相同数据。

经验丰富的黑客知道如何分析数据包嗅探器捕获的流量，以确定不同数据包的含义。这需要练习和耐心。目前，尝试在控制器应用程序中按几次上箭头加速，同时留意终端窗口中的 ID# 244。随着加速和减速，查找消息数据列中变化的值。识别此模式是 ID #244 指代速度表的线索。

现在按转向灯（左箭头和右箭头）并留意 ID# 188。当你触动转向灯时，它应该出现，并在关闭几秒钟后消失。使用左 SHIFT 和右 SHIFT 键，或右 SHIFT 键加 X、Y、A 和 B 键来锁定和解锁车门，并观察 ID# 19B 旁边的数据变化。锁定或解锁车门时，19B 的行应该只出现片刻。

