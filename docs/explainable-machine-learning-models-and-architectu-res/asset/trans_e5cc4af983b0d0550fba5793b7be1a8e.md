

- 26. Z. Hong, “人工神经网络初步研究,” 第6届 IEEE 联合国际信息技术与人工智能会议, vol. 2, pp. 336–338, 2011.

- 27. V. Vapnik, “统计学习理论。信号处理的自适应与学习系统,” Commun Control, vol. 2, pp. 1–740, 1998.

- 28. Balasundaram S., and Gupta, D., “基于函数迭代方法的原始优化极端学习机用于回归与分类,” Int J Mach Learn Cybern, vol. 7, pp. 707–728, 2016.

- 29. Varatharajan R., Manogaran G. and Priyan M.K., “基于改进 SVM 方法的云计算中 ECG 信号的 LDA 大数据分类方法,” Multimedia Tools Appl, vol. 77, pp. 10195–10215, 2018.

- 30. Murphy, K. P. “机器学习：概率视角,” MIT Press, pp. 492–493, 2012.

- 31. Y. Hua, Z. Zhao, R. Li, X. Chen, Z. Liu and H. Zhang, “基于长短期记忆网络的时间序列预测深度学习,” IEEE Commun. Mag., vol. 57(6), pp. 114–119, 2019.

- 32. Thanh-Phuong Nguyen, Chao-Tsung Yeh, Ming-Yuan Cho, Chun-Lung Chang, Meng-Jie Chen, “卷积神经网络双向长短期记忆网络用于配电绝缘体泄漏电流的在线分类,” Elsevier.

- 33. Javier Mata, Ignacio de Miguel, Ramon J. Duran, Naomi Merayo, Sandeep Kumar Singh, Admela Jukan, Mohit Chamania, “光网络中的人工智能（AI）方法：全面综述,” Optical Switching Networking, Elsevier, vol. 28, pp. 43–57, 2018.

- 34. H. Chai, S. Yin, H. Liu, B. Guo, X. Li and S. Huang, “基于柔性光网络中 OSNR 损伤模型的路由与频谱分配算法研究,” 第16届光通信与网络国际会议（IOCON）, 2017.

- 35. T. D. Vo et al., “使用硫系光子芯片对 640 Gb/s 光信号进行全光多损伤性能监测,” 光纤通信会议（OFC/NFOEC）, 与国家光纤工程师大会同期举办, 2010.

- 36. Sharma, K., Gupta, A., Sharma, B., & Tripathi, S.L. (Eds.). (2021). 智能通信与自动化系统（第1版）. CRC Press, ISBN: 9781003104599 https://doi.org/10.1201/9781003104599

## 基于 Django Web 框架的网站开发

Sanmukh Kaur*, Anuranjana 和 Yashasvi Roy

印度诺伊达 Amity 乌塔尔邦大学 Amity 工程与技术学院

## 摘要

本章探讨了 Django Web 框架的研究、该框架的特性以及其内置工具在 Web 开发中的应用。进一步地，它通过设计基本网站的架构以及开发该网站（具有用户注册、登录-登出和通过 Django 框架在后端进行用户活动跟踪等功能）来展示该框架的实际实现。它重点介绍了使用 Bootstrap 开源 CSS 和 JavaScript 基础设计模板进行用户友好型网页的前端开发、其定制化以及这些模板与 Django 框架的集成。

关键词：Django, Python, HTML, CSS, MVT 架构, bootstrap

### 9.1 引言

Python 是一种通用编程语言，可用于开发 GUI 应用程序、桌面应用程序以及 Web 应用程序 [1]。它也用于数据分析和可视化。其简单的语法规则使其代码比其他语言更易读、更易维护。由于有多种开源 Python 框架、库和开发工具可用，它显著降低了软件开发成本，任何开发者都可以使用这些框架进行产品开发并进行集成。

*通信作者：sanmukhkaur@gmail.com

Web 开发的开源 Python 框架之一是 Django [2]。它是一个高级 Python Web 框架，可快速开发可维护且安全的网站。它是免费开源的 Web 框架，拥有活跃的开发者社区、优秀的文档以及多种免费技术支持选项 [3]。

Django 最初于 2003 年至 2005 年间由一个网站开发小组开发，该小组负责开发和维护一个新闻网站。该小组创建不同网站的过程导致重复使用相同的代码和设计模式，在进一步开发后形成了一个通用 Web 开发框架，并于 2005 年 7 月作为“Django”项目开源。

### 9.2 Django 的主要特性

下文讨论了 Django 的一些主要特性。

#### 9.2.1 完整性

Django 基于“全包含”理论工作，几乎提供了软件工程师开发所需的所有“开箱即用”内容。由于只需要这一个“产品”，一切都能完美协同工作，遵循稳定的计划标准，并拥有广泛而详细的文档。

#### 9.2.2 多功能性

Django 可用于开发任何类型的网站，无论是内容管理系统、社交网络还是新闻网站。它可以与任何框架集成，并可以以几乎任何配置传输或显示内容（包括 HTML、JSON、XML、RSS 频道等）。

#### 9.2.3 安全性

Django 通过提供旨在自动保护网站的系统，协助设计师避免许多常见的安全漏洞。例如，Django 提供了管理用户账户和密码详细信息的安全方法，消除了诸如将会话信息放入 cookie 中造成漏洞，或直接以原始形式存储密码而不是将其转换为哈希码（单向）再保存到数据库中等常见缺陷。Django 默认提供对众多漏洞的防护，例如 SQL 注入、跨站请求伪造、点击劫持和跨站脚本。

#### 9.2.4 可扩展性

Django 遵循基于组件/模型的“无共享”架构（即，架构的每个组件独立运行且不互相干扰，因此可根据需求进行定制）。由于其不同组件之间有适当的分离，可以通过在任何位置添加硬件（服务器，如缓存服务器、应用服务器或数据库服务器）来扩展以应对不断增长的流量。像 Instagram 这样的高流量网站已成功使用 Django 进行扩展以满足其需求。

#### 9.2.5 可维护性

Django 代码使用明确定义的设计原则和模式编写，有助于开发易于维护且可重用的代码。它采用 DRY（不要重复自己原则），因此没有不必要的重复，从而减少了代码量。Django 还鼓励将相关功能分组为可重用的应用程序，并在较低级别下，在 MVC（模型-视图-控制器）模式下将相关代码分组到模块中。

#### 9.2.6 可移植性

Django 使用 Python 编写，支持多种平台。这意味着开发者不必绑定到特定的服务器平台，可以使用 Linux、Mac OS X 和 Windows 等多种系统。此外，Django 还受到各种 Web 托管云服务的支持，这些服务通常提供 Django 特定的服务。

### 9.3 UI 设计

Django 是一个高级 Python Web 框架。它具有易于使用的 UI。它具有实用的设计，以鼓励快速 Web 开发。它支持 HTML、CSS 和 JavaScript。它还包含多种模板，因为它遵循模型–模板–视图架构模式。

#### 9.3.1 HTML

超文本标记语言（HTML）是用于在 Web 浏览器中显示的各种组件设计的标准标记语言，并由 CSS 和 JavaScript 进一步协助以增强用户体验。

#### 9.3.2 CSS

层叠样式表（CSS）是一种样式表语言，用于描述调用它的 HTML 文件中的内容将在浏览器屏幕上如何显示。CSS 是万维网的最重要技术之一，与 JavaScript 和 HTML 并列。

#### 9.3.3 Bootstrap

Bootstrap 是一种免费开源的 CSS 框架，用于开发响应式、移动优先的前端 Web 开发 [4]。它包含基于 CSS 和 JavaScript 的设计模板，用于排版、表单、按钮、导航和其他界面组件。

### 9.4 方法论

对于 Web 开发，第一步是设计其架构，如图 9.1 所示。这是在开发前对网站的技术、功能和可视化组件进行规划。我们的基本网站包含主页、登录页、重新登录页、注册页、经过身份验证的用户控制台、注销以及用户跟踪表。

本网站开发采用模型-视图-模板架构。在此方法中，用户以 URL 形式向 Django 框架 [5]（充当控制器）请求资源/操作，Django 框架会在 urls.py 中查找用户请求的相同 URL，并在 view.py 中查找其对应的视图；该视图包含用于前端操作的模板，以及从 models.py 获取的用于后端操作的模型实例（用于数据库管理），如图 9.2、9.3、9.4、9.5、9.6 和 9.7 所示。

### 9.5 UI 设计

Bootstrap 是一个开源 CSS 框架，提供基于 CSS 和 JavaScript 的各种 Web 开发设计模板，可通过自定义平台提供的模板代码用于网页设计 [6]。

