
```c
// FT2232C extensions

UCHAR Rev5;              // FT2232C chip? yes (non-zero), no (0)
UCHAR IsoInA;            // "A" channel IN endpoint:
                         //   bulk (0), isochronous (non-zero)
UCHAR IsoInB;            // "B" channel IN endpoint:
                         //   bulk (0), isochronous (non-zero)
UCHAR IsoOutA;           // "A" channel OUT endpoint:
                         //   bulk (0), isochronous (non-zero)
UCHAR IsoOutB;           // "B" channel OUT endpoint:
                         //   bulk (0), isochronous (non-zero)
UCHAR PullDownEnable5;   // pull-down mode:
                         //   not enabled (0), enabled (1)
UCHAR SerNumEnable5;     // serial number:
                         //   enabled (non-zero), not enabled (0)
UCHAR USBVersionEnable5; // USBVersion enabled?
                         //   yes (non-zero), no (0)
WORD USBVersion5;        // USB version (BCD) (0x0200 = USB2.0)
UCHAR AIsHighCurrent;    // "A" channel is high current?
                         //   yes (non-zero), no (0)
UCHAR BIsHighCurrent;    // "B" channel is high current?
                         //   yes (non-zero), no (0)
UCHAR IFAIsFifo;         // "A" channel is 245 FIFO?
                         //   yes (non-zero), no (0)
UCHAR IFAIsFifoTar;      // "A" channel is 245 FIFO CPU target?
                         //   yes (non-zero), no (0)
UCHAR IFAIsFastSer;      // "A" channel is Fast Serial?
                         //   yes (non-zero), no (0)
UCHAR AIsVCP;            // "A" channel uses VCP driver?
                         //   yes (non-zero), no (0)
UCHAR IFBIsFifo;         // "B" channel is 245 FIFO?
                         //   yes (non-zero), no (0)
UCHAR IFBIsFifoTar;      // "B" channel is 245 FIFO CPU target?
                         //   yes (non-zero), no (0)
UCHAR IFBIsFastSer;      // "B" channel is Fast Serial?
                         //   yes (non-zero), no (0)
UCHAR BIsVCP;            // "B" channel uses VCP driver?
                         //   yes (non-zero), no (0)
} FT_PROGRAM_DATA, *PFT_PROGRAM_DATA;
```

清单14-3：FTDI Chip设备的EEPROM数据结构。粗体文本表示默认值。改编自FTDI Chip的D2XX程序员指南。（共2页，第2页）

为了能够在具有默认厂商ID和产品ID并使用VCP驱动程序的设备上运行MPROG，FTDI Chip提供了一个应用程序，可将产品ID更改为特殊的“D2XX Recovery”产品ID（6006h），以及一个INF文件，该文件为具有该产品ID的设备指定D2XX驱动程序。然后您可以运行MPROG并将最终的厂商ID和/或产品ID存储在EEPROM中。另一种方法是在将EEPROM连接到控制器之前，使用其他方法对其编程。

## 15 集线器：设备与主机之间的连接

每个USB外设都必须连接到集线器。正如第1章所述，集线器是一种智能设备，为设备提供连接点，并管理每个设备与总线的连接。直接插入PC的设备连接到根集线器。其他设备则连接到根集线器下游的外部集线器。

集线器的主要工作是管理其设备的连接和电源，以及向主机传递流量和从主机接收流量。管理连接包括帮助新连接的设备启动并进行通信，以及阻止行为异常设备的通信，使其不干扰总线上的其他通信。管理电源包括向连接的设备提供所请求的总线电流。集线器在向主机传递流量和从主机接收流量方面的作用取决于主机、设备以及它们之间的集线器的速度。集线器可能只是重复接收到的内容，也可能将流量转换为不同的速度并管理与该设备的事务。

![](img/3955d77b6be34048e3bc722d0b15c2a9_454_0.png)

图15-1：集线器有一个上行端口和一个或多个下行端口。

本章介绍有关集线器通信的基本知识。设计USB外设时，您不需要了解集线器的每个细节。主机应用程序、设备驱动程序和设备固件不必知道或关心主机与设备之间有多少个集线器。但是，对集线器功能的些许了解有助于理解设备在总线上的检测和通信方式。

### 集线器基础知识

每个外部集线器都有一个端口或连接点，用于向上游方向（朝向主机）连接（图15-1）。该上行端口可以直接连接到主机的根集线器，也可以连接到另一个外部集线器上的下行端口。每个集线器还拥有一个或多个位于主机下游的端口。大多数下行端口都有一个用于连接电缆的连接器。例外情况是作为复合设备一部分的集线器，其端口连接到设备内嵌的功能。具有一个、两个、四个和七个下行端口的集线器很常见。集线器可以是自供电或总线供电的。正如第16章所述，总线供电的集线器是有限的，因为无法向它们连接高功率设备。

1.x集线器将从主机接收到的所有低速和全速数据包（包括已经过一个或多个额外集线器的数据）重复到所有已启用的全速下行端口。已启用端口包括所有连接了设备并准备好从集线器接收通信的端口。端口未启用的设备包括：因错误或其他问题而主机控制器已停止与其通信的设备、处于挂起状态的设备，以及因刚刚连接或正在退出挂起状态而尚未准备好通信的设备。

集线器中继器不会以任何方式转换、检查内容或处理往返全速端口的流量。集线器中继器只是重新生成信号转换的边沿并将其传递过去。

低速设备永远不会看到全速流量。1.x集线器只向低速设备重复低速数据包。集线器通过数据包前面的PRE数据包标识符来识别低速数据包。集线器将低速数据包（且仅这些数据包）重复到任何已启用的低速端口。集线器还将低速数据包重复到其全速下行端口，因为全速端口可能连接到集线器，而该集线器又连接到低速设备。为了让集线器有时间使它们的低速端口准备好接收数据，主机在PRE数据包和低速数据包之间添加了至少四个全速位宽度的延迟。

与全速相比，低速电缆段中的流量不仅速度不同，边沿速率和极性也不同。距离低速设备最近的集线器在与该设备通信时使用低速的边沿速率和极性。当向上游通信时，集线器使用全速的更快的边沿速率和与低速相比反转的极性。集线器中继器根据需要转换边沿速率和极性。第18章将详细介绍信号极性，第19章将详细介绍边沿速率。

### 高速中继器

当集线器的上行端口连接到高速总线段时，2.0集线器使用高速中继器。在这种情况下，集线器以高速发送和接收所有上游流量，即使流量发往低速或全速设备或来自这些设备。

流量通过具有高速中继器的集线器所走的路径取决于所连接设备的速度。集线器中的路由逻辑确定往返下行端口的流量是否通过事务转换器。

与低速和全速中继器不同，高速中继器对接收到的数据重新计时，以最大限度地减少累积抖动。换句话说，高速中继器不仅仅是重复接收到的转换，而是提取数据，并在重传时使用自己的本地时钟来定时转换。边沿速率和极性保持不变。弹性缓冲区允许两个时钟频率之间存在微小差异。当缓冲区半满时，接收到的数据开始被时钟输出。

高速设备不使用事务转换器。流量从集线器上的接收端口通过高速中继器路由到集线器的发送端口。

对于往返低速和全速设备的流量，高速中继器与事务转换器通信，后者管理这些设备的事务。从上游接收的流量被路由到高速中继器，然后经过事务转换器，以适当的速度与下行端口通信。在另一个方向上，来自低速和全速设备的流量被路由到事务转换器，事务转换器处理接收的数据并采取下一节所述的适当操作。

### 事务转换器

每个2.0集线器必须有一个事务转换器来管理低速和全速设备的通信。事务转换器以高速向上游通信，但使1.x设备能够以低速和全速通信，方式与它们与1.x主机通信完全相同。事务转换器存储接收到的数据，然后以不同的速度将数据转发到目的地。

事务转换器通过允许其他总线通信在设备完成低速或全速事务的同时发生，从而释放总线时间。
