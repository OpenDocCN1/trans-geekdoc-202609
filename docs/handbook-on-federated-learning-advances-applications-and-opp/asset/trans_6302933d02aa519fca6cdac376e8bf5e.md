

![](images/coverpage.jpg)

![Cover: Handbook on FEDERATED LEARNING Advances, Applications and Opportunities, edited by Saravanan Krishnan, A. Jose Anand, R. Srinivasan, R. Kavitha, S. Suresh, published by CRC Press](images/coverpage.jpg)

First edition published 2024

by CRC Press

2385 NW Executive Center Drive, Suite 320, Boca Raton FL 33431

and by CRC Press

4 Park Square, Milton Park, Abingdon, Oxon, OX14 4RN

© 2024 Saravanan Krishnan, A. Jose Anand, R. Srinivasan, R. Kavitha and S. Suresh

*CRC Press is an imprint of Taylor & Francis Group, LLC*

Reasonable efforts have been made to publish reliable data and information, but the author and publisher cannot assume responsibility for the validity of all materials or the consequences of their use. The authors and publishers have attempted to trace the copyright holders of all material reproduced in this publication and apologize to copyright holders if permission to publish in this form has not been obtained. If any copyright material has not been acknowledged please write and let us know so we may rectify in any future reprint.

Except as permitted under U.S. Copyright Law, no part of this book may be reprinted, reproduced, transmitted, or utilized in any form by any electronic, mechanical, or other means, now known or hereafter invented, including photocopying, microfilming, and recording, or in any information storage or retrieval system, without written permission from the publishers.

For permission to photocopy or use material electronically from this work, access [www.copyright.com](http://www.copyright.com) or contact the Copyright Clearance Center, Inc. (CCC), 222 Rosewood Drive, Danvers, MA 01923, 978-750-8400. For works that are not available on CCC please contact [mpkbookspermissions@tandf.co.uk](http://mpkbookspermissions@tandf.co.uk)

*Trademark notice*: Product or corporate names may be trademarks or registered trademarks and are used only for identification and explanation without intent to infringe.

*Library of Congress Cataloging-in-Publication Data (applied for)*

ISBN: 978-1-032-47162-4 (hbk)

ISBN: 978-1-032-47163-1 (pbk)

ISBN: 978-1-003-38485-4 (ebk)

DOI: [10.1201/9781003384854](https://dx.doi.org/10.1201/9781003384854)

Typeset in Palatino Linotype

by Radiant Productions

# 前言

联邦学习（FL）是一种分布式机器学习模型，目前已应用于许多领域。它由 Google Inc 和 Apple Inc 等公司首创，作为一种在不牺牲隐私的前提下，利用分布式数据集创建性能更优机器学习模型的技术。目前，Apple Inc 利用联邦学习提升 Face ID 和 Siri 的准确性，Google 则利用它为 Gboard 的键盘预测提供支持。其解决传统 ML 模型引发的隐私问题的能力，使其极具吸引力。因此，联邦学习目前是 AI 领域最引人入胜、最具前景的研究方向之一。它近期改变了我们收集、分析和使用数据的方式。联邦学习在工业 4.0、医疗保健和机器人技术等领域有着广泛的应用。本书从各个方面为联邦学习提供了全面的方法论。

本书包含四个部分，分别为：概念与类型、学习过程与优化、工具与技术、应用与用例。本书的目的是结合实时用例，详细阐述各种应用中的概念、工具和技术。

第 1 部分讨论联邦学习的定义、架构以及联邦学习框架的应用，并对现有工作进行了全面综述。

第 2 部分提供了关于 FL 在数据安全、数据多样性、实时持续学习、硬件效率等方面优势的章节。然而，当某些参与者不被认为完全诚实时，会带来新的隐私风险，如成员推理攻击和数据投毒攻击。此外，自私的参与者可能会获取他人的集体数据，却隐瞒甚至提供关于其本地数据的虚假信息。因此，现代隐私和公平机制已被纳入 FL 系统，相关章节也讨论了区块链概念。它解决了数据隐私、数据安全、数据访问等方面的挑战。在第 3 部分，章节从技术角度探讨了联邦强化学习的演变，并强调了其相较于以往强化学习算法的优势。

第 4 部分讨论了一种学习范式，旨在通过协作训练算法而不交换数据本身，来解决数据治理和隐私问题。它近期因在医疗保健领域的应用而受到关注，相关章节对此进行了讨论。FL 使协作获取洞察成为可能（例如以共识模型的形式），而无需将患者数据移出其所在机构的防火墙之外。本书从各个方面为联邦学习提供了全面的方法论。

# 第 1 章 联邦学习方法与分类简介

*Shashikiran Venkatesha*^([¹](#fn1))

Email: [lramanathan@vit.ac.in](mailto:lramanathan@vit.ac.in)

## 1. 动机与简介

正如近期所观察到的，推荐系统、自然语言处理、计算机视觉和自动语音识别等不同领域的应用与工具的进步，是机器学习（ML）算法快速发展的结果 [[1]](#ch1.xhtml#ref1_1)、[[2]](#ch1.xhtml#ref1_2) 和 [[3]](#ch1.xhtml#ref1_3)。由深度学习（DL）调优的 ML 平台所取得的强大且有利的成果，得益于从数据存储库（也称为“数据仓库”或“数据中心”）获取的海量合法数据或“大数据” [[2]](#ch1.xhtml#ref1_2)、[[3]](#ch1.xhtml#ref1_3) 和 [[4]](#ch1.xhtml#ref1_4)。DL 平台执行的各项任务的终极性能有时可与人类认知卓越性相媲美。例如，利用数十亿张图像训练的、经 DL 调优的人脸识别系统，能够产生有效且可商业化的成果。例如，从 Instagram 获取的 35 亿张图像 [[5]](#ch1.xhtml#ref1_5) 被用于名为 Detectron 的目标检测系统训练，这是一个可扩展分布式系统框架的经典示例，也是 Facebook 不可或缺的一部分。软件架构师、ML 研究人员和开发人员面临许多挑战，例如创建、开发、运营和维护分布式计算框架。这些挑战枚举如下。

*   **数据所有权**：在 21 世纪，人们在涉及其数据及其在构建 ML 平台中的使用时，已意识到自己的所有权。在推荐服务等现代 ML 驱动产品中，对于消费者购买模式和汇款方式的所有权主张存在模糊地带；这与产品数据和供应商交易不同，后者的所有权由服务提供商主张。

*   **遵守数据保护法案**：2018 年，欧盟通过了名为“通用数据保护条例”（GDPR）的法案，这是数据保护法律与合规的一个著名范例 [[6]](#ch1.xhtml#ref1_6)。2020 年，美国加利福尼亚州颁布的《加利福尼亚消费者隐私法案》（CCPA）为数据保护和使用提供了法律框架 [[7]](#ch1.xhtml#ref1_7)。GDPR 为数据保护采用的基本准则，在发生私人数据泄露时提供法律救济。

