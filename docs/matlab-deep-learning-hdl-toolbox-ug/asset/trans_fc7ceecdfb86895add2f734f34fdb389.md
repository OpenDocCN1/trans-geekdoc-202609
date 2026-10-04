

## 性示例

## 将深度学习网络部署到 FPGA

在部署网络之前，你必须首先建立与 FPGA 板板的连接。`dhdl1.Target` 对象代表了主机计算机与 FPGA 之间的连接。创建两个目标对象，一个通过 JTAG 接口连接，另一个通过以太网接口连接。要使用 JTAG 连接，请安装 Xilinx™ Vivado™ Design Suite 2019.2，如果尚未设置，请将路径指向你已安装的 Xilinx Vivado 可执行文件。

```matlab
% hdlsettooltipath('ToolName', 'Xilinx Vivado', 'ToolPath', 'C:\Xilinx\Vivado\2019.2\bin\vivado.exe')
hTargetJAG = dhdl1.Target('Xilinx', 'Interface', 'JTAG')
```

hTargetJAG =
Target 属性:

- Vendor: 'Xilinx'
  Interface: JTAG

hTargetEthernet = dhdl1.Target('Xilinx', 'Interface', 'Ethernet')
Target 属性:

- Vendor: 'Xilinx'
  Interface: Ethernet
  IPAddress: '192.168.1.100'
  Username: 'root'
  Port: 22

要部署网络，将目标对象分配给 `dhdl1.Workflow` 对象并执行 `deploy` 方法。部署分为两个阶段。首先，将位流固化到 FPGA。然后，将网络传输到板载内存中。

选择 JTAG 接口并对操作计时。此操作可能需要几分钟。

```matlab
hW.Target = hTargetJAG;
tic;
hW.deploy();
### 正在使用 JTAG 编程 FPGA 位流...
### FPGA 位流编程已完成。
### 正在加载权重到 FC 控制器
### 0% 完成，当前时间为 29-Jun-2020 16:33:14.
### 17% 完成，当前时间为 29-Jun-2020 16:34:20.
### 25% 完成，当前时间为 29-Jun-2020 16:35:38.
### 33% 完成，当前时间为 29-Jun-2020 16:36:56.
### 42% 完成，当前时间为 29-Jun-2020 16:38:13.
### 50% 完成，当前时间为 29-Jun-2020 16:39:31.
### 58% 完成，当前时间为 29-Jun-2020 16:40:48.
### 67% 完成，当前时间为 29-Jun-2020 16:42:02.
### 75% 完成，当前时间为 29-Jun-2020 16:43:10.
### 83% 完成，当前时间为 29-Jun-2020 16:44:23.
### 91% 完成，当前时间为 29-Jun-2020 16:45:39.
### FC 权重已加载。当前时间为 29-Jun-2020 16:46:31
elapsedTimeJTAG = toc
elapsedTimeJTAG = 1.0614e+03
```

## 使用以太网加速大型网络的原型开发工作流

通过将 `dhdl.Workflow` 目标对象设置为 `hTargetEthernet` 并运行 `deploy` 函数使用以太网接口。当我们使用以太网将位流和网络部署到 FPGA 时，网络部署速度将显著加快。

```bash
### 正在使用以太网编程 FPGA 位流...
正在通过以太网将目标 FPGA 设备配置下载到 SD 卡中 ...
# 已复制 /tmp/hdlcoder 到 /mnt/hdlcoder_rd
# 正在复制位流 hdlcoder_system.bit 到 /mnt/hdlcoder_rd
# 设置位流为 hdlcoder/hdlcoder_system.bit
# 正在复制设备 dhdl.bit 到 /mnt/hdlcoder_rd
# 设置设备为 hdlcoder/device dhdl.bit
# 正在设置启动: "AXI-Stream DDR Memory Access : 3-AXIM"
```

正在通过以太网将 FPGA 设备配置下载到 SD 卡。系统现在

```bash
系统正在重启
### FPGA 位流编程已完成。
### 正在加载权重到 FC 控制器。
### 0% 完成，当前时间为 29-Jun-2020 16:47:08.
### 17% 完成，当前时间为 29-Jun-2020 16:47:08.
### 25% 完成，当前时间为 29-Jun-2020 16:47:08.
### 33% 完成，当前时间为 29-Jun-2020 16:47:08.
### 42% 完成，当前时间为 29-Jun-2020 16:47:08.
### 50% 完成，当前时间为 29-Jun-2020 16:47:08.
### 58% 完成，当前时间为 29-Jun-2020 16:47:08.
### 67% 完成，当前时间为 29-Jun-2020 16:47:08.
### 75% 完成，当前时间为 29-Jun-2020 16:47:08.
### 83% 完成，当前时间为 29-Jun-2020 16:47:08.
### 91% 完成，当前时间为 29-Jun-2020 16:47:08.
### FC 权重已加载。当前时间为 29-Jun-2020 16:46:31
```

