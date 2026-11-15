

Country 在 Country 中关于 CountryName 的内部唯一性约束可以通过将谓词声明为函数来声明，如下所示：

```
ic () requires function(hasCountryName)
```

![](img/1344db3eba3d550e6edb009556fcd95c_949_0.png)

图 17.17 一些唯一性和强制角色约束。

Country has CountryName 中 CountryName 角色的唯一性约束可以这样声明：

```
ic (c1, c2, n) requires (hasCountryName(c1,n) and hasCountryName(c2,n)) implies c1 = c2
```

假设三元事实类型已声明，其组合唯一性约束可以如下声明：

```
ic (c, y, p1, p2) requires
(inYearHadPopulation(c, y, p1) and inYearHadPopulation(c, y, p2)) implies p1 = p2
```

State 的组合引用方案中的外部唯一性约束可以这样声明：

```
ic (s1, s2, c, sc) requires
(isInCountry(s1,c) and hasStateName(s1,sc) and
isInCountry(s2,c) and hasStateName(s2,sc))
implies s1 = s2
```

![](img/1344db3eba3d550e6edb009556fcd95c_949_1.png)

图 17.18 更多约束。

图 17.18 中的 ORM 架构包含几种其他类型的约束。示例 (a) 中的包含-或约束确保每个求职者要么合格，要么有推荐人（或两者兼有）。这可以用 Rel 这样表达：

```
ic (p) requires JobApplicant(p) implies (isQualified(p) or hasReference(p))
```

示例 (b) 中的异或约束确保我们太阳系中的每个行星要么是内行星，要么是外行星，但不能两者皆是。这可以用 Rel 这样表达：

```
ic (p) requires Planet(p) implies (isAnInnerPlanet(p) xor isAnOuterPlanet(p))
```

示例 (c) 中的值约束限制了底层引用类型 Gender has GenderCode 中 GenderCode 的值。示例 (d) 中的值约束将 IQ 值限制在 0..300 范围内。这些约束可以这样制定：

```
ic (g, gc) requires hasGenderCode(g,gc) implies (gc = "M" or gc = "F")
ic (x, y) requires hasIQNr(x,y) implies (x >= 0 and x <= 300)
```

示例 (e) 和 (f) 中的排斥约束表明，没有人可以同时撰写和评审同一本书，也没有人可以评审由在同一大学任教的人所撰写的论文（评审者也在该大学任教）。(f) 中关于连接路径上排斥约束的图表是 NORMA 工具的截图。这些约束可以这样制定：

```
ic (p, b) requires reviews(p, b) implies not authors(p, b)
```

```
ic (p1, p2, u, pr) requires (authors(p1, pr) and lecturesAt(p1, u) and reviews(p2, pr)) implies not lecturesAt(p2,u)
```

图 17.19 中的 ORM 架构包含更多约束。示例 (a) 中的等价约束确保患者有舒张压读数当且仅当患者有收缩压读数。这可以使用匿名变量在 Rel 中这样表达：

```
ic (p) requires hasDiastolicBP(p, _) iff hasSystolicBP(p,_)
```

示例 (b) 中的内部频率约束确保每个评审者最多被分配三篇论文进行评审。它可以这样制定：

```
ic (r, n) requires isAssignedNrPapers(r, n) implies n <= 3
```

示例 (c) 中的组合频率约束确保没有学生可以在同一课程中注册超过两次。可以这样制定。这里，“def”前置了 inCourseHasNrEnrollments 关系的定义或推导规则，该规则使用内置 count 函数。约束使用了派生的三元关系。

```
def inCourseHasNrEnrollments(s, c, n):
n = count[{e}: isanEnrollmentByStudent(s, e) and isanEnrollmentInCourse(e, c)]
ic (s, c, n) requires inCourseHasNrEnrollments(s, c, n) implies n <= 2
```

![](img/1344db3eba3d550e6edb009556fcd95c_951_0.png)

示例 (d) 中的外部频率约束确保对于每个国家，最多有两位政客既在其政府中又是摄政者。这个约束可以使用 count 函数来制定，或者也可以简单地这样制定：

```
ic (p1, p2, p3) requires
(isaCoregent(p1) and servesOnGovtOf(p1, c) and isaCoregent(p2)
and servesOnGovtOf(p2, c) and isaCoregent(p3) and servesOnGovtOf(p3, c))
implies p1 = p2 or p1 = p3 or p2 = p3
```

环约束在 Rel 中易于指定。人们认识自己的自反环约束可以表示为：ic(p) requires Person(p) implies knows(p,p)。没有人是自己父母的非自反环约束可以表示为：ic (p) requires not isaParentOf(p, p)。兄弟姐妹关系的对称约束可以这样指定：ic (p1,p2) requires isaSiblingOf(p1, p2) implies isaSiblingOf(p2, p1)。没有人是自己父母的非对称环约束可以这样表示：ic (p1,p2) requires isaParentOf(p1, p2) implies not isaParentOf(p2, p1)。

isOlderThan 关系的传递性可以这样制定：ic (p1, p2, p3) requires (isOlderThan(p1, p2) and isOlderThan(p2, p3)) implies isOlderThan(p1, p3)。直接优先关系上的非传递性约束可以这样制定：ic (e1,e2,e3) requires (directlyPrecedes(e1, e2) and directlyPrecedes(e2, e3)) implies not directlyPrecedes(e1, e3)。

祖先关系可以这样定义：def isanAncestorOf(p1, p2): isaParentOf(p1, p2) or isaParentOf(p1, p3) and isanAncestorOf(p3, p2)。祖先关系上的非循环约束可以这样指定：ic (p) requires not isanAncestorOf(p, p)。

图 17.20(a) 中的成对子集约束确保每个通过课程的学生也注册了该课程。这可以用 Rel 这样表达：ic (s, c) requires passedCourse(s, c) implies enrolledInCourse(s, c)。

图 17.20 中连接路径上的子集约束确保每个在某个国家任职的顾问必须至少会说一种在该国使用的语言。这个约束可以这样表达：

```
ic (a, c) requires servesInCountry(a, c) implies
(speaksLanguage(a, l) and isaLanguageUsedBy(l, c))
```

![](img/1344db3eba3d550e6edb009556fcd95c_952_0.png)

这些简单示例大致展示了 Rel 在建模 ORM 约束方面的表达能力。大型、高度复杂的 ORM 模型也可以映射到 Rel 结构中。

## 其他数据库品种

专用数据库品种有时被用来处理某些类型的应用程序。_空间数据库_ 需要高效管理空间数据，例如地图（道路、土地等）、二维设计（电路、城镇规划等）和三维设计（医疗操作可视化、分子结构、航路等）。它们为空间数据类型（点、线、多边形等）、空间运算符（重叠、包含、相交等）和空间索引（R 树、四叉树等）提供内置支持。这允许高效地制定和处理空间查询，例如，拟议购物中心 5 公里内有多少房屋？哪些航班飞越大洛杉矶地区？哪些图表与图表 37 相似？

以前，专用系统用于空间数据，而关系型 DBMS 用于字母数字数据。当前趋势是在同一系统中管理标准数据和空间数据。地理信息系统 (GIS) 的典型应用可能按以下方式进行：输入交通事故的标准数据；显示道路地图以突出事故地点；然后用此来确定需要采取额外预防措施的区域（例如，雷达测速）。

历史上，GIS 厂商采用了三种主要方法：混合方法（空间文件存储中的地理关系对象被赋予可以在关系表中引用的标识符）；集成方法（空间和非空间数据存储在关系表中）；面向对象方法（所有数据存储在 ODB 中）。更近期，许多空间数据库应用程序以及使用非标准数据的其他应用程序已使用对象关系技术实现。

