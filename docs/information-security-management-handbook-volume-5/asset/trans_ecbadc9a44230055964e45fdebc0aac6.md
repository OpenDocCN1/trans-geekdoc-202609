

## 1. 缓冲区溢出

Buffer overflow 是软件中最常见的安全漏洞来源之一。C 或 C++ 等编程语言不是内存安全的。换句话说，输入的长度没有被检查。攻击者可以引入故意更长的输入，写出缓冲区之外。由于程序控制数据通常位于数据缓冲区相邻的内存区域，缓冲区溢出可能导致程序执行任意代码。由于大量标签具有严重的存储限制，资源丰富的标签模拟设备可以被利用 \[84\]。

## 2. 代码插入

攻击者可能使用任何脚本语言（即，通用网关接口、Java、Perl 等）将恶意代码注入应用程序。用脚本语言写入数据的 RFID 标签可能执行此类攻击。想象一下，机场用于跟踪行李的标签在其数据字段中包含机场目的地。每次读取标签时，后端系统都会触发查询，“ select \* from location\_table where airport =<tag data>。”想象一下，攻击者在一件行李中存储“MAD;shutdown”。当这些数据被读取时，数据库将被关闭，行李系统将崩溃。

## 3. 结构化查询语言（SQL）注入

这是一种代码插入攻击，在数据库中执行非预期的 SQL 代码。这些攻击的主要目标如下：枚举数据库结构、检索授权数据、进行未经授权的修改或删除等。RFID 标签可能包含用于 SQL 注入攻击的数据。存储限制不是问题，因为可以用非常少量的 SQL 造成很大危害。例如，SQL “drop table <*tablename*\>” 将删除指定的数据库表。

总结来说，RFID 标签是一个不安全且不可信的数据库。因此，从这些设备获得的信息应在有足够证据证明数据准确之前进行分析。然而，这并不是一个新概念，因为在所有信息系统中，输入数据都应被检查以确保它不会造成问题。

# 参考文献

1. L. Bolotnyy 和 G. Robins. 基于物理不可克隆函数的 RFID 系统安全与隐私。在 *PerCom’07 论文集*，第 211–220 页。IEEE Computer Society Press, Washington, DC, 2007.

2. J. Cichon, M. Klonowski, 和 M. Kutylowski. 基于 RFID 标签的动态系统中的隐私保护。在 *PerSec’07 论文集*，第 235–240 页。IEEE Computer Society Press, Washington, DC, 2007.

3. T. Heydt-Benjamin, H.-J. Chae, B. Defend, 和 K. Fu. 公共交通的隐私。在 *PET’06, LNCS* 论文集，4258，第 1–19 页。Springer-Verlag, Cambridge, U.K., 2006.

4. T. Hjorth. RFID 系统中的隐私支持。硕士论文，丹麦技术大学，Lyngby, Denmark, 2004.

5. A. Juels 和 R. Pappu. 尖叫欧元：RFID 启用银行券中的隐私保护。在 *FC’03, LNCS* 论文集，2742，第 103–121 页。Springer-Verlag, Guadeloupe, French West Indies, 2003.

6. S. Kinoshita, M. Ohkubo, F. Hoshino, G. Morohashi, O. Shionoiri, 和 A. Kanai. 隐私增强型主动 RFID 标签。在 *ECHISE’05 论文集*，Munich, Germany, 2005.

7. E. Kosta, M. Meints, M. Hensen, 和 M. Gasson. RFID 启用电子护照相关的安全和隐私问题分析。在 *Sec’07, IFIP* 论文集，232，第 467–472 页。Springer, Sandton, South Africa, 2007.

8. D. Ranasinghe, D. Engels, 和 P. Cole. 安全与隐私：低成本 RFID 系统的温和建议。在 *Auto-ID Labs Research Workshop 论文集*，Zurich, Switzerland, 2004.

9. M. Rieback, B. Crispo, 和 A. Tanenbaum. 将立法与 RFID 隐私增强技术相结合。在 *Security and Protection of Information 论文集*，Brno, Czech Republic, 2005.

10. M. Rieback, G. Gaydadjiev, B. Crispo, R. Hofman, 和 A. Tanenbaum. RFID 安全和隐私管理平台。在 *LISA’06 论文集*，Washington, DC, 2006.

11. S.E. Sarma, S.A. Weis, 和 D.W. Engels. RFID 系统及其安全和隐私影响。在 *CHES’02, LNCS* 论文集，2523，第 454–470 页。Springer-Verlag, Redwood City, CA, 2002.

12. S. Spiekermann 和 H. Ziekow. RFID：确保隐私的 7 点计划。在 *ECIS’05 论文集*，Regensburg, Germany, 2005.

13. 《世界人权宣言》，第 12 条，1948 年。

14. 欧盟指令 95/46/EC—数据保护指令。《欧洲共同体官方杂志》，1995 年 11 月 23 日。

15. M. Weiser. 21 世纪的计算机。《科学美国人》，265(3):94–104，1991 年 9 月。

16. J.-H. Hoepman, E. Hubbers, B. Jacobs, M. Oostdijk, 和 R. Wichers Schreur. 跨越边界：欧洲电子护照的安全和隐私问题。在 *IWSEC’06, LNCS* 论文集，4266，第 152–167 页。Springer-Verlag, Kyoto, Japan, 2006.

17. A. Juels, D. Molnar, 和 D. Wagner. 电子护照中的安全和隐私问题。在 *SecureComm’05 论文集*。IEEE Computer Society, Athens, Greece, 2005.

18. 机读旅行文件的高级安全机制—扩展访问控制（EAC）版本 1.0.1。技术指南 TR-03110，联邦信息安全办公室，Bonn, Germany, 2006.

19. CASPIAN. `http://www.nocards.org/`, 2005 年 10 月 1 日.

20. FoeBuD. `http://www.foebud.org/rfid`, 2005 年 10 月 5 日.

21. Boycott Benetton. `http://www.boycottbenetton.com/`, 2003 年 4 月 9 日.

22. *RFID Journal*. Behind the benetton brouhaha. `http://www.rfidjournal.com`, 2003 年 4 月 14 日.

23. Boycott Tesco. `http://www.boycotttesco.com/`, 2005 年 1 月 26 日.

24. Boycott Guillette. `http://www.boycottguillette.com/`, 2003 年 9 月 2 日.

25. K. Albrecht 和 L. McIntyre. *SPYCHIPS: 公司和政府如何计划利用 RFID 追踪你的一举一动*。Nelson Communications, Inc., Nashville, TN, 2005.

26. 加州参议院法案 682。`http://www.epic.org/privacy/rfid/`, 2005 年 2 月 22 日.

27. 加州拟议的 RFID 法案包含什么？`http://www.rfidproductsnew.com`, 2006 年 1 月 20 日.

28. S. Garfinkel. 权利法案。`http://www.technologyreview.com`, 2002 年 10 月.

29. G. Danezis, S. Lewis, 和 R. Anderson. 位置隐私值多少钱。在 *Workshop of Economics of IS’05 论文集*，Cambridge, MA, 2005.

30. A. Beresfor 和 F. Stajano. 普适计算中的位置隐私。《IEEE Pervasive Computing》，2(1):1536–1268, 2003.

31. S. Weis, S. Sarma, R. Rivest, 和 D. Engels. 低成本无线射频识别系统的安全和隐私方面。在 *SPC’03 论文集*，*LNCS*，2802，第 454–469 页。Springer-Verlag, 2003.

32. 识别卡–非接触式集成电路卡–近距离卡。`http://www.wg8.de/sdi.html`, 2001.

33. 机读旅行文件，Doc. 9303。`http://www.mrtd.icao.int`, 2006 年 7 月 8 日.

34. M. Brown, E. Zeisel, 和 R. Sabella. *RFID*+*Exam Cram*。Que Publishing, Indianapolis, IN, 2006.

35. D.C. Ranasinghe 和 P.H. Cole. 应对现代 RFID 系统中的安全和隐私威胁。在 *ACSSC 06 论文集*，第 2058–2064 页，Pacific Grove, CA, 2006.

36. Z. Kfir 和 A. Wool. 利用非接触式智能卡系统中的中继攻击掏虚拟口袋。在 *SecureComm’05 论文集*。IEEE Computer Society, Athens, Greece, 2005.

37. J. Atkinson. 非接触式信用卡消费者报告。`http://www.findcreditcards.org`, 2006 年 4 月 3 日.

