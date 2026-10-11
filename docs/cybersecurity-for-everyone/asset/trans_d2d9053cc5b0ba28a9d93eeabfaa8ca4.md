

![](images/cover.jpg)

首版于 2021 年出版

由 CRC Press 出版

6000 Broken Sound Parkway NW, Suite 300, Boca Raton, FL 33487-2742

以及 CRC Press

2 Park Square, Milton Park, Abingdon, Oxon, OX14 4RN

© 2021 Taylor & Francis Group, LLC

CRC Press 是 Taylor & Francis Group, LLC 的一个品牌

已尽合理努力以发布可靠的数据和信息，但作者和出版商不对所有材料的有效性或其使用后果承担责任。作者和出版商已尝试追踪本出版物中所复制材料的版权持有者，如未获得以此形式出版的许可，向版权持有者致歉。如有任何版权材料未被确认，请告知我们，以便我们在未来的再版中更正。

除美国版权法允许的情况外，未经出版商书面许可，本书任何部分不得以任何电子、机械或其他已知或日后发明的手段（包括复印、缩微胶片和录制）或以任何信息存储或检索系统的形式重印、复制、传播或使用。

如需复印或以电子方式使用本书材料，请访问 [www.copyright.com](http://www.copyright.com) 或联系版权许可中心 (CCC)，地址：222 Rosewood Drive, Danvers, MA 01923，电话：978-750-8400。对于 CCC 上不可用的作品，请联系 [mpkbookspermissions@tandf.co.uk](mailto:mpkbookspermissions@tandf.co.uk)

*商标声明*：产品或公司名称可能是商标或注册商标，仅用于识别和说明，无侵权意图。

*美国国会图书馆预编目数据*

ISBN: 9780367642785 (精装)

ISBN: 9781003124030 (电子书)

采用 Computer Modern 字体排版

由 KnowledgeWorks Global Ltd. 排版

# 目录

1.  [前言](#preface01.xhtml#preface)

2.  [1 简介](#01chap_01.xhtml#chapter1)

3.  [2 网络空间如何运作](#02chap_02.xhtml#chapter2)

    1.  [2.1 与网络空间的邂逅](#02chap_02.xhtml#sec2_1)

    2.  [2.2 什么是网络空间？](#02chap_02.xhtml#sec2_2)

    3.  [2.3 节点](#02chap_02.xhtml#sec2_3)

    4.  [2.4 人员](#02chap_02.xhtml#sec2_4)

    5.  [2.5 管道](#02chap_02.xhtml#sec2_5)

    6.  [2.6 配置](#02chap_02.xhtml#sec2_6)

    7.  [2.7 流量类型](#02chap_02.xhtml#sec2_7)

    8.  [2.8 深网](#02chap_02.xhtml#sec2_8)

    9.  [2.9 暗网](#02chap_02.xhtml#sec2_9)

    10.  [2.10 万维网](#02chap_02.xhtml#sec2_10)

    11.  [2.11 社会层面](#02chap_02.xhtml#sec2_11)

    12.  [2.12 治理](#02chap_02.xhtml#sec2_12)

    13.  [2.13 安全问题](#02chap_02.xhtml#sec2_13)

    14.  [2.14 网络空间的非善意使用](#02chap_02.xhtml#sec2_14)

4.  [3 加密与哈希](#03chap_03.xhtml#chapter3)

    1.  [3.1 私钥加密](#03chap_03.xhtml#sec3_1)

    2.  [3.2 公钥加密](#03chap_03.xhtml#sec3_2)

    3.  [3.3 数字签名与数字哈希](#03chap_03.xhtml#sec3_3)

    4.  [3.4 加密的应用](#03chap_03.xhtml#sec3_4)

5.  [4 节点安全](#04chap_04.xhtml#chapter4)

    1.  [4.1 获取节点访问权限](#04chap_04.xhtml#sec4_1)

    2.  [4.2 恶意软件](#04chap_04.xhtml#sec4_2)

    3.  [4.3 恶意软件有什么作用？](#04chap_04.xhtml#sec4_3)

    4.  [4.4 直接攻击](#04chap_04.xhtml#sec4_4)

6.  [5 管道安全](#05chap_05.xhtml#chapter5)

    1.  [5.1 IP](#05chap_05.xhtml#sec5_1)

    2.  [5.2 TCP](#05chap_05.xhtml#sec5_2)

    3.  [5.3 UDP](#05chap_05.xhtml#sec5_3)

    4.  [5.4 利用协议的攻击](#05chap_05.xhtml#sec5_4)

    5.  [5.5 对策](#05chap_05.xhtml#sec5_5)

7.  [6 配置安全](#06chap_06.xhtml#chapter6)

    1.  [6.1 互联网控制报文协议](#06chap_06.xhtml#sec6_1)

    2.  [6.2 域名服务](#06chap_06.xhtml#sec6_2)

    3.  [6.3 交换机漏洞](#06chap_06.xhtml#sec6_3)

    4.  [6.4 发起攻击](#06chap_06.xhtml#sec6_4)

    5.  [6.5 抵御攻击](#06chap_06.xhtml#sec6_5)

    6.  [6.6 恢复](#06chap_06.xhtml#sec6_6)

8.  [7 应用安全](#07chap_07.xhtml#chapter7)

    1.  [7.1 电子邮件](#07chap_07.xhtml#sec7_1)

    2.  [7.2 Web 流量](#07chap_07.xhtml#sec7_2)

    3.  [7.3 区块链](#07chap_07.xhtml#sec7_3)

9.  [8 总结](#08chap_08.xhtml#chapter8)

10.  [索引](#ind01.xhtml#index)

1.  [封面](cover.xhtml)

2.  [半标题页](#halfpage.xhtml#halftitle)

3.  [标题页](#titlepage.xhtml)

4.  [版权页](#copy.xhtml)

5.  [目录](#contents.xhtml)

6.  [前言](#preface01.xhtml#preface)

7.  [1 简介](#01chap_01.xhtml#chapter1)

8.  [2 网络空间如何运作](#02chap_02.xhtml#chapter2)

    1.  [2.1 与网络空间的邂逅](#02chap_02.xhtml#sec2_1)

    2.  [2.2 什么是网络空间？](#02chap_02.xhtml#sec2_2)

    3.  [2.3 节点](#02chap_02.xhtml#sec2_3)

    4.  [2.4 人员](#02chap_02.xhtml#sec2_4)

    5.  [2.5 管道](#02chap_02.xhtml#sec2_5)

    6.  [2.6 配置](#02chap_02.xhtml#sec2_6)

    7.  [2.7 流量类型](#02chap_02.xhtml#sec2_7)

    8.  [2.8 深网](#02chap_02.xhtml#sec2_8)

    9.  [2.9 暗网](#02chap_02.xhtml#sec2_9)

    10.  [2.10 万维网](#02chap_02.xhtml#sec2_10)

    11.  [2.11 社会层面](#02chap_02.xhtml#sec2_11)

    12.  [2.12 治理](#02chap_02.xhtml#sec2_12)

    13.  [2.13 安全问题](#02chap_02.xhtml#sec2_13)

    14.  [2.14 网络空间的非善意使用](#02chap_02.xhtml#sec2_14)

9.  [3 加密与哈希](#03chap_03.xhtml#chapter3)

    1.  [3.1 私钥加密](#03chap_03.xhtml#sec3_1)

    2.  [3.2 公钥加密](#03chap_03.xhtml#sec3_2)

    3.  [3.3 数字签名与数字哈希](#03chap_03.xhtml#sec3_3)

    4.  [3.4 加密的应用](#03chap_03.xhtml#sec3_4)

10.  [4 节点安全](#04chap_04.xhtml#chapter4)

     1.  [4.1 获取节点访问权限](#04chap_04.xhtml#sec4_1)

     2.  [4.2 恶意软件](#04chap_04.xhtml#sec4_2)

     3.  [4.3 恶意软件有什么作用？](#04chap_04.xhtml#sec4_3)

     4.  [4.4 直接攻击](#04chap_04.xhtml#sec4_4)

11.  [5 管道安全](#05chap_05.xhtml#chapter5)

     1.  [5.1 IP](#05chap_05.xhtml#sec5_1)

     2.  [5.2 TCP](#05chap_05.xhtml#sec5_2)

     3.  [5.3 UDP](#05chap_05.xhtml#sec5_3)

     4.  [5.4 利用协议的攻击](#05chap_05.xhtml#sec5_4)

     5.  [5.5 对策](#05chap_05.xhtml#sec5_5)

12.  [6 配置安全](#06chap_06.xhtml#chapter6)

     1.  [6.1 互联网控制报文协议](#06chap_06.xhtml#sec6_1)

     2.  [6.2 域名服务](#06chap_06.xhtml#sec6_2)

     3.  [6.3 交换机漏洞](#06chap_06.xhtml#sec6_3)

     4.  [6.4 发起攻击](#06chap_06.xhtml#sec6_4)

     5.  [6.5 抵御攻击](#06chap_06.xhtml#sec6_5)

     6.  [6.6 恢复](#06chap_06.xhtml#sec6_6)

13.  [7 应用安全](#07chap_07.xhtml#chapter7)

     1.  [7.1 电子邮件](#07chap_07.xhtml#sec7_1)

     2.  [7.2 Web 流量](#07chap_07.xhtml#sec7_2)

     3.  [7.3 区块链](#07chap_07.xhtml#sec7_3)

14.  [8 总结](#08chap_08.xhtml#chapter8)

15.  [索引](#ind01.xhtml#index)

1.  [i](#halfpage.xhtml#page_i)

2.  [ii](#halfpage.xhtml#page_ii)

3.  [iii](#titlepage.xhtml#page_iii)

4.  [iv](#copy.xhtml#page_iv)

5.  [v](#contents.xhtml#page_v)

6.  [vi](#contents.xhtml#page_vi)

7.  [vii](#preface01.xhtml#page_vii)

8.  [viii](#preface01.xhtml#page_viii)

9.  [1](#01chap_01.xhtml#page_1)

10.  [2](#01chap_01.xhtml#page_2)

11.  [3](#01chap_01.xhtml#page_3)

12.  [4](#01chap_01.xhtml#page_4)

13.  [5](#01chap_01.xhtml#page_5)

14.  [6](#01chap_01.xhtml#page_6)

15.  [7](#02chap_02.xhtml#page_7)

16.  [8](#02chap_02.xhtml#page_8)

17.  [9](#02chap_02.xhtml#page_9)

18.  [10](#02chap_02.xhtml#page_10)

19.  [11](#02chap_02.xhtml#page_11)

