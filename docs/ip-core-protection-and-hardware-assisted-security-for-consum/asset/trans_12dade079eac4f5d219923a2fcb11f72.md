

# IP Core Protection and Hardware-Assisted Security for Consumer Electronics

Anirban Sengupta 和 Saraju P. Mohanty

The Institution of Engineering and Technology

由 The Institution of Engineering and Technology 出版，伦敦，英国

The Institution of Engineering and Technology 在英格兰和威尔士注册为慈善机构（编号 211014）和苏格兰（编号 SC038698）。

© The Institution of Engineering and Technology 2019

首次出版 2019 年

本出版物受伯尔尼公约和万国版权公约版权保护。版权所有。除 1988 年《版权、设计和专利法》允许的研究或私人学习、批评或评论等合理使用外，未经出版商事先书面许可，或在符合版权许可局颁发的许可条款的复印复制情况下，本出版物不得以任何形式或任何方式复制、存储或传输。关于超出上述条款的复制事宜，请发送至以下地址的出版商：

The Institution of Engineering and Technology

Michael Faraday House

Six Hills Way, Stevenage

Herts, SG1 2AY United Kingdom

[www.theiet.org](http://www.theiet.org)

作者和出版商认为本著作中的信息和指导是正确的，但各方在使用时必须依靠自身的技能和判断。作者和出版商不对因本作品中的任何错误或遗漏（无论是疏忽还是其他原因）造成的任何损失或损害承担任何责任。任何此类责任均被否认。

作者作为本作品作者被识别的道德权利已根据 1988 年《版权、设计和专利法》由他们主张。

**British Library Cataloguing in Publication Data**

本产品的目录记录可从大英图书馆获取

**ISBN 978-1-78561-799-7 (精装)**

**ISBN 978-1-78561-800-0 (PDF)**

由 MPS Limited 在印度排版

由 CPI Group (UK) Ltd, Croydon 在英国印刷

# Contents

[关于作者](#preface.html#ST2)

[致谢](#preface_1.html#ST3)

[Thomas M. Coughlin 序言](#preface_2.html#ST4)

[Pradipta Patra 序言](#preface_3.html#ST5)

[Swarup Bhunia 序言](#preface_4.html#ST6)

[Peter Corcoran 序言](#preface_5.html#ST7)

[前言](#preface_6.html#ST8)

[缩略语列表](#preface_7.html#ST9)

[符号列表](#preface_8.html#ST10)

[1 消费电子产品 IP 核保护和硬件辅助安全简介](#Chapter1.html#c01)

[1.1 消费电子产品与安全视角](#Chapter1.html#ST12)

[1.2 硬件辅助安全和 IP 核保护](#Chapter1.html#ST13)

[1.3 知识产权 (IP) 核/硬件](#Chapter1.html#ST14)

[1.3.1 IP 核在 CE 设备中的实用性](#Chapter1.html#ST15)

[1.3.2 为什么需要硬件/IP 核的安全和保护？](#Chapter1.html#ST16)

[1.3.3 传统的 IP 保护形式是否不够？](#Chapter1.html#ST17)

[1.4 CE 设备—DSP 核的 IP 核保护和硬件辅助安全](#Chapter1.html#ST18)

[1.4.1 IP 核/硬件可用的安全和保护方法](#Chapter1.html#ST19)

[1.4.2 不同 IP 核保护和硬件辅助安全机制：优点和缺点](#Chapter1.html#ST20)

[1.4.3 HLS（架构综合）作为实现 DSP IP 核安全算法的设计骨干](#Chapter1.html#ST24)

[1.5 硬件辅助媒体保护](#Chapter1.html#ST25)

[1.6 物理不可克隆函数](#Chapter1.html#ST26)

[1.7 本书组织结构](#Chapter1.html#ST27)

[1.8 结论](#Chapter1.html#ST28)

[1.9 练习](#Chapter1.html#ST29)

[参考文献](#Chapter1.html#ST30)

[2 消费电子产品和物联网 (IoT) 安全](#Chapter2.html#c02)

[2.1 物联网 (IoT) – 广泛概述](#Chapter2.html#ST32)

[2.1.1 IoT – 架构](#Chapter2.html#ST33)

[2.1.2 IoT – 驱动技术](#Chapter2.html#ST34)

[2.1.3 IoT – 应用](#Chapter2.html#ST35)

[2.1.4 IoT – 挑战](#Chapter2.html#ST36)

[2.2 IoT 和消费电子系统中的安全、隐私、IPR – 全景图](#Chapter2.html#ST37)

[2.2.1 IoT 安全 – 攻击和对策](#Chapter2.html#ST38)

