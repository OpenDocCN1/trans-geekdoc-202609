

![](1264277989.jpg)

## 关于作者

**Bobby Rogers**（他/他的/他本人）是一名网络安全专业人士，在信息技术和网络安全领域拥有超过 30 年的经验。他目前在阿拉巴马州亨茨维尔的一家大型工程公司工作，帮助保障其客户的网络安全并管理网络风险。Bobby 的客户包括美国陆军、NASA、田纳西州以及私营/商业公司和组织。他的专长是网络安全工程、安全合规性和网络风险管理，但他几乎在网络安全的每个领域都有工作经验，包括网络防御、计算机取证和事件响应以及渗透测试。

Bobby 是美国空军退役军士长，服役超过 21 年。他在美国、乍得、乌干达、南非、德国、沙特阿拉伯、巴基斯坦、阿富汗以及其他几个偏远地区建立并保障了网络安全。他的勋章包括两枚功绩勋章、三枚空军嘉奖勋章、国防服务勋章以及多枚空军成就勋章。他于 2006 年退役。

Bobby 拥有信息保障理学硕士学位和计算机信息系统理学学士学位（俄语双专业），以及两个理学副学士学位。他的众多认证包括 CISSP-ISSEP、CRISC、CySA+、CEH 和 MCSE: Security。

Bobby 为多家培训公司讲解并制作了超过 30 部计算机培训视频，目前为 Pluralsight ([https://www.pluralsight.com](https://www.pluralsight.com)) 制作此类视频。他也是 `CompTIA Mobility+ All-in-One Exam Guide (Exam MB0-001)`、`CRISC Certified in Risk and Information Systems Control All-in-One Exam Guide` 和 `Mike Meyers’ CompTIA Security+ Certification Guide (Exam SY0-401)` 的作者，并担任畅销书 `CISSP All-in-One Exam Guide, Ninth Edition` 的撰稿作者/技术编辑，上述书籍均由 McGraw Hill 出版。

### 关于技术编辑

**Nichole O’Brien** 是一位富有创造力的商业领袖，在网络安全和 IT 领导力、项目管理以及商业开发方面拥有超过 25 年的经验，涵盖商业、教育以及联邦、州和地方商业市场。她对创新解决方案的关注体现在开发了一个商业网络安全和 IT 业务集团，她目前在一家财富 500 强公司管理该集团，并获得了该公司年度杰出客户服务奖。她目前担任 Cyber Huntsville 的外联副主席，是国家网络安全峰会基金会董事会成员，并支持网络安全教育计划，如 USSRC Cyber Camp。Nichole 拥有工商管理学士和硕士学位，并持有 CISSP 认证。

![](title.jpg)

Copyright © 2023 by McGraw Hill. All rights reserved. Except as permitted under the United States Copyright Act of 1976, no part of this publication may be reproduced or distributed in any form or by any means, or stored in a database or retrieval system, without the prior written permission of the publisher, with the exception that the program listings may be entered, stored, and executed in a computer system, but they may not be reproduced for publication.

ISBN: 978-1-26-427798-8  

MHID: 1-26-427798-9

The material in this eBook also appears in the print version of this title: ISBN: 978-1-26-427797-1, MHID: 1-26-427797-0.

eBook conversion by codeMantra  

Version 1.0

All trademarks are trademarks of their respective owners. Rather than put a trademark symbol after every occurrence of a trademarked name, we use names in an editorial fashion only, and to the benefit of the trademark owner, with no intention of infringement of the trademark. Where such designations appear in this book, they have been printed with initial caps.

McGraw Hill eBooks are available at special quantity discounts to use as premiums and sales promotions or for use in corporate training programs. To contact a representative, please visit the Contact Us page at [www.mhprofessional.com](http://www.mhprofessional.com).

Information has been obtained by McGraw Hill from sources believed to be reliable. However, because of the possibility of human or mechanical error by our sources, McGraw Hill, or others, McGraw Hill does not guarantee the accuracy, adequacy, or completeness of any information and is not responsible for any errors or omissions or the results obtained from the use of such information.

TERMS OF USE

This is a copyrighted work and McGraw-Hill Education and its licensors reserve all rights in and to the work. Use of this work is subject to these terms. Except as permitted under the Copyright Act of 1976 and the right to store and retrieve one copy of the work, you may not decompile, disassemble, reverse engineer, reproduce, modify, create derivative works based upon, transmit, distribute, disseminate, sell, publish or sublicense the work or any part of it without McGraw-Hill Education’s prior consent. You may use the work for your own noncommercial and personal use; any other use of the work is strictly prohibited. Your right to use the work may be terminated if you fail to comply with these terms.

THE WORK IS PROVIDED “AS IS.” McGRAW-HILL EDUCATION AND ITS LICENSORS MAKE NO GUARANTEES OR WARRANTIES AS TO THE ACCURACY, ADEQUACY OR COMPLETENESS OF OR RESULTS TO BE OBTAINED FROM USING THE WORK, INCLUDING ANY INFORMATION THAT CAN BE ACCESSED THROUGH THE WORK VIA HYPERLINK OR OTHERWISE, AND EXPRESSLY DISCLAIM ANY WARRANTY, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO IMPLIED WARRANTIES OF MERCHANTABILITY OR FITNESS FOR A PARTICULAR PURPOSE. McGraw-Hill Education and its licensors do not warrant or guarantee that the functions contained in the work will meet your requirements or that its operation will be uninterrupted or error free. Neither McGraw-Hill Education nor its licensors shall be liable to you or anyone else for any inaccuracy, error or omission, regardless of cause, in the work or for any damages resulting therefrom. McGraw-Hill Education has no responsibility for the content of any information accessed through the work. Under no circumstances shall McGraw-Hill Education and/or its licensors be liable for any indirect, incidental, special, punitive, consequential or similar damages that result from the use of or inability to use the work, even if any of them has been advised of the possibility of such damages. This limitation of liability shall apply to any claim or cause whatsoever whether such claim or cause arises in contract, tort or otherwise.

`I’d like to dedicate this book to the cybersecurity professionals who tirelessly, and sometimes, thanklessly, protect our information and systems from all who would do them harm.`

`I also dedicate this book to the people who serve in uniform as military personnel, public safety professionals, police, firefighters, and medical professionals, sacrificing sometimes all that they are and have so that we may all live in peace, security, and safety.`

—Bobby Rogers

## 内容概览

[1.0 安全与风险管理](#ch01.xhtml#ch01)

[2.0 资产安全](#ch02.xhtml#ch02)

[3.0 安全架构与工程](#ch03.xhtml#ch03)

[4.0 通信与网络安全](#ch04.xhtml#ch04)

[5.0 身份与访问管理 (IAM)](#ch05.xhtml#ch05)

[6.0 安全评估与测试](#ch06.xhtml#ch06)

[7.0 安全运营](#ch07.xhtml#ch07)

[8.0 软件开发安全](#ch08.xhtml#ch08)

[A 关于在线内容](#app.xhtml#app)

[索引](#index.xhtml#index)

## 目录

[致谢](#ack.xhtml#ack)

[简介](#intro.xhtml#intro)

[1.0 安全与风险管理](#ch01.xhtml#ch01)

[目标 1.1 理解、遵守并推广职业道德](#ch01.xhtml#lev1-1)


