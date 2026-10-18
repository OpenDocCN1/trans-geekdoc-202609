

33. [KARNBULSUK](#ch10.xhtml#Cref10_33). (2009). Taking the first step with PDCA. Retrieved on 17th October 2019.

34. [Dionach](#ch10.xhtml#Cref10_34). (2011). Update to ISO 27001 Planned for 2013. Retrieved on 20th October 2019.

35. Retrieved from [`https://en.wikipedia.org/wiki/Security_controls`](https://en.wikipedia.org) on November 2019.

36. [Sinha M.](#ch10.xhtml#Cref10_36), & Gillies A. (2011). Improving the quality of information security management systems with iso27000. The TQM Journal, 23(4), 367–376.

37. [ISO](#ch10.xhtml#Cref10_37). (2015). The ISO survey of management system standard certifications. Retrieved from [`http://www.iso.org/iso/the_iso_survey_of_management_system_standard_certi_cations_2015.pdf`](http://www.iso.org) on 16th November 2019.

38. [TUV](#ch10.xhtml#Cref10_38). ISO 27001 information security. Retrieved from [`https://www.tuv.com/philippines/en/iso-27001-certification.html`](https://www.tuv.com) on 21st November 2019.

39. [Ashenden D.](#ch10.xhtml#Cref10_39) (2008). Information security management: A human challenge? Information Security Technical Report, 13(4), 195–201.

# 11 基于行人和车辆检测的自动路灯控制

R Sujatha, J Gitanjali, R. Pradeep Kumar, Mustansar Ali, Ghazanfar, Baibhav Pathy, and Jyotir Moy Chatterjee

DOI: [`10.1201/9780367808228-11`](https://doi.org/10.1201/9780367808228-11)

## 11.1 引言

自动路灯控制系统旨在节能，并在不需要时高效利用路灯。在日常生活中，传统路灯消耗的能源造成了巨大的能源需求。在传统路灯夜间照明中，无论是否有车辆移动，还是车辆交通量大但光照强度低，路灯都会以高光强度开启。为了解决这个问题，我们在基于红外信号车辆检测的路灯自动化研究中采用了先进的路灯控制系统技术，使用微控制器代替微处理器。

灯光检测通过道路的车辆，在车辆几乎被感应到时开启，在未检测到车辆时关闭。这样做可以节省电力消耗，而不是在没有车辆通过时保持照明。

高强度放电（HID）灯常用于街道。与 LED 相比，HID 灯虽然是电气气体放电灯，但能效较低。红外 LED 向 8051 微控制器 AT89S52 发送和接收信号，以执行开启、关闭或在未检测到车辆时将光强度调暗 20%。LED 灯正在被应用于街道布置中，其中红外传感器和光二极管感应行人或车辆通过。控制逻辑在 8051 微控制器中实现，以根据车辆检测调节灯光，在街道内有检测或无检测时，采用亮光和暗光两种模式。

该项目使用 AT89S52 微控制器读取一系列红外发射和接收信号的输入。当您将任何物体通过红外装置时，每个红外装置都会感应物体/车辆并向微控制器发送信号。根据车辆存在情况，8051 将开启一组白色 LED，这些 LED 充当路灯。当物体通过其他红外装置时，只开启一定数量的 LED，将能源消耗降至最低。

一旦车辆通过最后一个红外装置，所有 LED 都会关闭。该系统主要集中在基于红外传感器检测到的行人或车辆的节能上，具有暗光、亮光和关闭等不同运行阶段。通过采用这项技术，我们可以克服传统路灯系统。

该拟议模型的工作原理很简单，因为当行人或车辆通过带有蓝色和黑色 LED 的红外装置时，会将信息传递给 AT89S52 微控制器，微控制器响应信号并传递指令来控制 LED 是否发光。

## 11.2 发明背景

本发明基于微控制器和红外传感器，用于检测行人和车辆。通过本项目，我们可以最大限度地减少电力浪费，使用 8051 微控制器、红外装置和 LED 进行实现。红外装置感应车辆和行人，并将接收到的信号发送到 8051 微控制器。然后，这有助于根据红外装置的信号控制 LED 灯是否发光，决定是否发光。

## 11.3 文献综述

该系统基于模块设计，这些模块有助于检测系统中的故障路灯，并自动响应路灯 \[[1](#ch11.xhtml#ref11_1)\]。在这个自动化路灯系统中，它纯粹基于模块，有助于远程控制路灯。本文介绍了通过自动化跟踪对路灯的研究，系统可以激活太阳能发电系统的电源管理增加 \[[2](#ch11.xhtml#ref11_2)\]。该系统的输出基于太阳能跟踪传感器感应设备感知的太阳光密度进行放大。该系统以自动方式运行，根据亮度和黑暗实例化路灯 \[[3](#ch11.xhtml#ref11_3)\]。该系统的输出基于车辆移动情况进行调查，并控制灯光开启/关闭。该系统在红外传感器和 Raspberry Pi 的帮助下工作 \[[4](#ch11.xhtml#ref11_4)\]。红外传感器将检测车辆或行人，然后向 Raspberry Pi 发送响应，决定是否开启/关闭路灯。在这篇论文中，作者提出了 LED 灯和 Zig Bee 模块作为路灯的节能机制 \[[5](#ch11.xhtml#ref11_5)\]。他们使用 LED 而不是传统路灯，以实现更高的效率和更低的能源消耗。

在这篇论文中，作者提出了一种基于物联网的交通管理系统，因为物联网如今被广泛使用 \[[6](#ch11.xhtml#ref11_6)\]。物联网是未来技术进步的驱动链。基于物联网概念的新交通管理方法。在这篇论文中，作者提出了一种利用红外传感器技术的智能路灯 \[[7](#ch11.xhtml#ref11_7)\]。在夜间或黑暗中，路灯会自动亮起几秒钟，然后变暗。它采用动态控制系统，响应暗光和亮光运行模式。在这篇论文中，作者提出在路灯照明中使用 Arduino 技术以实现高效运行 \[[8](#ch11.xhtml#ref11_8)\]。部署 Arduino 技术对传统路灯系统进行改造，使该系统更加节能高效。拟议系统主要在高峰交通和降雨时有用 \[[9](#ch11.xhtml#ref11_9)\]。他们使用 RTC，在高峰交通时间路灯将以 100% 强度发光，交通量低时强度较低。他们使用光传感器检测交通和天气。该系统的主要目标是当未检测到物体时不点亮路灯 \[[10](#ch11.xhtml#ref11_10)\]。该系统基本上通过检测自行车、汽车、卡车和人类的移动来工作，并根据情况行动。在夜间未检测到物体时，系统进入关机状态，当检测到物体时，它将执行路灯点亮操作。

