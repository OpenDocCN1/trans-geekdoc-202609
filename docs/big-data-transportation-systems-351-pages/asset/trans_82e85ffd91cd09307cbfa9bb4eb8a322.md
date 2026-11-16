

![](img/64ac2ad4e2782dff8c190440ca455c6a_0_0.png)

## 大数据交通系统

赵光辉 • 朱古生

## 大数据交通系统

### 赵光辉

中国贵州财经大学，中国 & 中国交通部运输科学研究院信息技术研究所，中国

### 朱古生

中国曲靖师范大学，中国

Published by
World Scientific Publishing Co. Pte. Ltd.
5 Toh Tuck Link, Singapore 596224
USA office: 27 Warren Street, Suite 401-402, Hackensack, NJ 07601
UK office: 57 Shelton Street, Covent Garden, London WC2H 9HE

### 美国国会图书馆出版前编目数据

Names: Zhao, Guanghui, 1976– author. | Zhu, Gusheng, 1963– author.
Title: Big data transportation systems / Guanghui Zhao, The Guizhou Transportation and Economy Technology Institute, China, Gusheng Zhu, Qujing Normal University, China.
Description: Hackensack, NJ : World Scientific, [2021] | Includes bibliographical references and index.
Identifiers: LCCN 2021009807 | ISBN 9789811235993 (hardcover) | ISBN 9789811236006 (ebook for institutions) | ISBN 9789811236013 (ebook for individuals)
Subjects: LCSH: Intelligent transportation systems. | Big data.
Classification: LCC TE228.3 .Z43 2021 | DDC 388.3/12028557--dc23
LC record available at https://lccn.loc.gov/2021009807

### 大英图书馆出版前编目数据

A catalogue record for this book is available from the British Library.

大数据交通：从认知升级到应用实例
Originally published in Chinese by China Machine Press
Copyright © China Machine Press, 2018

Copyright © 2021 by World Scientific Publishing Co. Pte. Ltd.

All rights reserved. This book, or parts thereof, may not be reproduced in any form or by any means, electronic or mechanical, including photocopying, recording or any information storage and retrieval system now known or to be invented, without written permission from the publisher.

For photocopying of material in this volume, please pay a copying fee through the Copyright Clearance Center, Inc., 222 Rosewood Drive, Danvers, MA 01923, USA. In this case permission to photocopy is not required from the publisher.

For any available supplementary material, please visit
https://www.worldscientific.com/worldscibooks/10.1142/12250#t=suppl

Desk Editors: Jayanthi Muthuswamy/Yu Shan Tay
Typeset by Stallion Press
Email: enquiries@stallionpress.com

Printed in Singapore

## 前言

2017年5月10日，我的学生赵光辉博士和我在杭州AIMS讨论了与智能交通发展相关的问题。后来，他计划写一些关于交通大数据的内容。我告诉他，密歇根大学拥有世界领先的智能交通实验室。他们花了几年时间试图优化密歇根大学旁边的几个交通信号灯。随后，他们来到中国的一座大城市，开始通过大数据管理交通信号灯来开展交通大数据实验。借助传统摄像头和感应线圈，通过人工操作，每90秒切换一次信号灯。通过分析发送到监控室的拥堵数据，利用人工智能调整交通信号灯。两个月后，该城市高峰时段的拥堵缓解了20%。未来，世界上更多城市将通过大数据优化交通信号灯，这将有助于最大限度地利用有限的道路资源，节省大量时间和交通资源。此外，中国拥有1.5亿至2亿辆私家车。这些汽车每天约有95%的时间停放在停车场里闲置。它们占用大量空间，浪费资源，并造成拥堵。借助大数据，这些闲置资源可以被调动起来，为需要乘车的人提供服务。这一实践将做出多大的贡献啊！

在阅读了赵光辉博士和朱古生教授撰写的本书手稿后，我深信大数据技术已推动了中国交通的发展。例子包括交通大数据源的收集、交通大数据平台的应用、交通物流、公共交通和交通安全的痛点、案例和商业模式、运营经验，以及其他国家交通大数据的现状、战略和行动。赵博士提出，交通大数据已改变了中国社会的出行模式，从过去的“人找车”转变为现在的“为想乘车的人安排车辆”。通过分析雨天、晴天、高峰时段、正常时段、工作日和节假日的数据，可以预测这些情况下特定地点未来的出行状况和乘客数量。准确率目前已达到85%–90%。可提前15分钟做出决策，将车辆送往指定地点。通过提前15分钟进行分配、路线规划和定位，网约车为人们带来了巨大便利，这在以前是不可想象的。现在人们已经非常习惯了。

匹配乘客和车辆的努力并非唯一的应用。由于大数据，匹配人员和物资的努力也发生了巨大变化。2017年11月11日24:00，当天天猫销售额达到1682亿元。其中，网上购物贡献了90%，卖家和买家覆盖222个国家和地区。在11月11日之前，卖家通过大数据预测，快递包裹量将比2016年增加30%以上，大数据预测11月11日的包裹量将达到1.4亿件，超过170万名快递员将参与物流。通过加强协作和数据共享以改善物流服务，运单已覆盖整个行业的80%以上。这是大数据预测首次覆盖行业超过一半的快递包裹，效率通过大数据与社会协作的连接得以提高。在物流预警雷达升级的基础上，大数据平台已从时间间隔预测全面提升至实时预测，覆盖中国超过50%的快递包裹。算法优化使更多维度的大数据得以使用。结果是，提供了每日投递包裹数量的实时预测，准确率超过90%。这些数据可以帮助快递合作伙伴部署运力，企业可以根据预测数据提前准备运力。因此，提前增加了4000名临时工人和5240辆卡车，并提前增加了飞机租赁吨位。“大数据配送路线”可以根据运单上的信息自动计算配送路径，并将包裹分配给离买家最近的网点。超过50%的包裹通过大数据配送路线更快地送达买家。卖家利用大数据对各类畅销商品进行预测，并管理全国各地仓库的库存，使包裹能尽可能靠近买家。通过使用大数据预测包裹量，商品能尽早送达买家。模式从“买家等待包裹”转变为“包裹寻找买家”。

《大数据交通系统》为我们提供了一种全新的视角来观察和利用大数据，这要感谢赵光辉博士从密歇根大学回国后的辛勤工作，以及朱古生教授对中国交通的持续关注。我之前为他们写过的一本书《互联网+交通》写了序言。本书《大数据交通系统》描绘了交通发展的新阶段。在中国致力于建设交通强国的战略背景下，这种前瞻性研究、学者与交通领域从业者的互动，以及学者对世界交通发展的贡献变得更加必要。每个人都必须有人生目标，因为你的存在会对社会和你周围的人产生影响。无论扮演什么角色，每个人都能对世界产生影响。我希望赵博士继续努力工作，保持勤奋，掌握世界上的重大技术变革，顺应世界潮流，以其国际视野、胸襟和非凡智慧为交通强国梦想提供更多研究成果，并向读者奉献更多作品。

我相信，得益于中国交通领域人才的智慧和全球各地人才的贡献，中国的交通大数据在未来一定会更加先进。中国将更接近成为世界交通强国的目标，中国借助大数据发展交通的前景也将更加光明。

