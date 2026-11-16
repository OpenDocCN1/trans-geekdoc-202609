

用于识别您可能感兴趣的工作。看来人力资源人员，特别是招聘人员，通常使用 LinkedIn 来寻找人员以填补职位，无论是内部招聘人员还是为招聘公司工作的人。

由于 LinkedIn 收集的商业信息量很大，我们可以将其作为猎头平台来利用。尤其是针对付费会员，LinkedIn 会对使用它的企业以及网站上的人员进行大量分析。如果您正在寻找关于某个目标的信息，LinkedIn 提供大量细节。以 Figure 4.9 为例，它显示了通过网站 Jobs 部分发布的某个空缺职位的申请者统计数据。我们可以看到，该职位吸引了受过教育的申请人。您可以通过查看多个职位的这些统计数据，开始了解劳动力的情况。

### FIGURE 4.9 LinkedIn 职位统计

| 类别 | 详情 |
| :--- | :--- |
| 资历级别 | 98 名总监级别申请人<br>76 名高级别申请人<br>38 名经理级别申请人<br>37 名副总裁级别申请人 |
| 教育程度 | 50% 拥有学士学位<br>31% 拥有工商管理硕士学位<br>11% 拥有硕士学位<br>8% 拥有其他学位 |
| 地点 | 大丹佛地区：182 名申请人<br>大纽约市地区：6–10 名申请人<br>美国其他地区：6–10 名申请人 |

![](img/421171b17a0c0dfae0aacde15d9831c1_133_0.png)

职位列表是除了申请者和整体劳动力统计数据之外，寻找详细信息的另一个地方。我们可以从这些列表中看到组织内可能存在的技术。网络安全工程师职位的列表中有可以在 Figure 4.10 中看到的要求。虽然其中一些要求是通用的，但也有一些对网络中使用的技术非常具体。例如，该公司似乎可能正在使用 CheckPoint 和 Palo Alto Networks 防火墙。此外，其网络中还有 Cisco 路由器和交换机。这是一个立足点。我们现在可以 starts you can get。

### 员工搜索的 InSpy 结果

```
$ ins --empspy title-list-small.txt Wiley

InSpy 2.0.3

2018-07-02 16:00:52 59 Employees identified
2018-07-02 16:00:52 Felix R Cabral Sr. Avaya Voice Engineer – Voice Infrastructure
2018-07-02 16:00:52 Uta Goebel Deputy Editor at Wiley VCH
2018-07-02 16:00:52 Janice Cruz (L.I.O.N.) Quality Assurance Analyst at Wiley
Education Solut
2018-07-02 16:00:52 Coral Nuñez Puras Financial Planning and Analyst in Wiley
2018-07-02 16:00:52 Jamie Wielgus Editor at John Wiley and Sons
2018-07-02 16:00:52 Stacy Gerhardt Engineer in Training at Wiley|Wilson
2018-07-02 16:00:52 Martin Graf-Utzmann Editor at Wiley VCH
2018-07-02 16:00:52 James Smith, EIT Mechanical Engineer at Wiley|Wilson
2018-07-02 16:00:52 Mohammad Karazoun Software Test Engineer (Product Analyst)
at John W
2018-07-02 16:00:52 Robert Vocile Strategic Market Analyst at Wiley
2018-07-02 16:00:52 Misha Davidof Senior Business Analyst Consultant at Wiley
2018-07-02 16:00:52 Aleksandr Lukashevich Automation Testing Engineer at John
Wiley and Sons
2018-07-02 16:00:52 Ekaterina Perets, Ph.D. Assistant editor at Wiley
2018-07-02 16:00:52 Guangchen Xu Editor @ Wiley
2018-07-02 16:00:52 Ralf Henkel Editor in Chief at Wiley-Blackwell
2018-07-02 16:00:52 sonal jain Wiley India
2018-07-02 16:00:52 Abhinay Kanneti QA Automation Engineer at Wiley Publishing
2018-07-02 16:00:52 Olga Roginkin, PMP Business Analyst at John Wiley and Sons
2018-07-02 16:00:52 Razi Gharaybeh Senior Quality Assurance Engineer at John
Wiley an
2018-07-02 16:00:52 Daniel Bleyer Senior SCCM Systems Engineer at Wiley
2018-07-02 16:00:52 John Coughlan Senior Project Engineer at Wiley
2018-07-02 16:00:52 Stephanie Hill Production Editor at Wiley
2018-07-02 16:00:52 Jörn Ritterbusch Editor-in-Chief bei Wiley-VCH
2018-07-02 16:00:52 Alden Farrar Assistant Editor at Wiley
2018-07-02 16:00:52 Gilat Mandelbaum Strategy Analyst Intern at Wiley
2018-07-02 16:00:52 Chelsea Meade Pricing Analyst at Wiley
2018-07-02 16:00:52 Babak Mostaghaci Associate Editor at Wiley-VCH
2018-07-02 16:00:52 Vibhushita Misra Testing Analyst/Testing Team Lead at Wiley
2018-07-02 16:00:52 Mohammed Mnayyes Quality Engineer at John Wiley and Sons
2018-07-02 16:00:52 David Kim Associate Editor | Society Journals | Wiley
2018-07-02 16:00:52 Lauren Ellis Project Engineer at Wiley
2018-07-02 16:00:52 Amit Wawdhane Data Analyst at Wiley | Masters in Information Sys
```

InSpy 不是我们可以用来在 LinkedIn 上进行自动搜索的唯一实用程序。我们也可以使用 theHarvester，就像之前所做的那样。我们不再搜索 Google 或 Bing 等网站，而是可以指定 LinkedIn 作为要搜索的数据来源。幸运的是，theHarvester 可以做到这一点而不需要 API 密钥。许多网站将需要 API 密钥来

