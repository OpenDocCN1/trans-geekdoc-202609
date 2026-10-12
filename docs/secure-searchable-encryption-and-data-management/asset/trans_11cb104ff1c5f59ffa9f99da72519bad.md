
ABE 方案面临共谋攻击的安全威胁。例如：一份招聘启事已根据某策略加密，只有同时拥有硕士学位**且**至少两年工作经验的用户才能解密。可能存在两个用户，他们各自仅拥有其中一个属性。因此，拥有硕士学位但无经验的用户不应能解密。同理，有经验但无学位的用户也不应能解密。我们要防止这两个用户以某种方式结合他们的密钥，并试图冒充一个拥有所有必需属性的用户。因此，ABE 方案的开发应防止用户结合他们的密钥并获知他们各自本不应获知的信息，否则 ABE 的初衷将落空。

## 2.5 章节小结

在本章中，我们涵盖了从密码学原语的历史开端到当今使用的最新技术。我们描述了标准 PKE 技术是如何被推广和放宽以获得其他公钥密码技术的。我们主要讨论了与公钥密码学相关的方面，因为在后续章节中，我们的重点是基于公钥密码学原语构建可搜索加密方案。在 PKE 技术中，详细讨论了基于身份的加密和基于属性的加密，因为它们在可搜索加密中有应用。

# 参考文献

1. A. J. Menezes, J. Katz, P. C. Van Oorschot, and S. A. Vanstone, *应用密码学手册*. CRC Press, 1996.
2. W. Stallings, *密码学与网络安全*, 4/E. Pearson Education India, 2006.
3. K. H. Rosen, “密码学导论,” ISBN-10, pp. 1–58488, 2007.
4. C. Paar, and J. Pelzl, *理解密码学：面向学生和从业者的教科书*. Springer Science & Business Media, 2009.
5. O. Goldreich, *密码学基础：第 2 卷，基本应用*. Cambridge University Press, 2009.
6. W. Diffie, and M. Hellman, “密码学新方向,” *IEEE Trans. Inf. Theory*, vol. 22, no. 6, pp. 644–654, 1976.
7. B. B. Gupta, and M. Quamara, “基于智能卡的物联网环境下分布式云计算服务的身份基访问控制和相互认证框架”, *Procedia Comput. Sci*, vol. 132, pp. 189–197, 2018.
8. A. Tewari, and B. B. Gupta, “一种面向物联网设备的基于 ECC 的轻量级认证协议”, *Int. J. High Perform. Comput. Networking*, vol. 15, no. 1–2, pp. 106–120, 2019.
9. Q. Zheng, X. Wang, M. K. Khan, W. Zhang, B. B. Gupta, and W. Guo, “一种基于混沌 SCML 的轻量级认证加密方案，用于铁路云服务”, *IEEE Access*, vol. 6, pp. 711–722, 2017.
10. B. B. Gupta, and T. Aakanksha. *物联网安全入门指南：攻击、应用、认证与基础*. CRC Press, 2020.
11. B. B. Gupta, G. M. Perez, D. P. Agrawal, and D. Gupta. *计算机网络与网络安全手册*. Springer Science and Business Media LLC, 2020.
12. T. ElGamal, “一种基于离散对数的公钥密码系统和签名方案,” *IEEE Trans. Inf. Theory*, vol. 31, no. 4, pp. 469–472, 1985.
13. D. Khader, “基于 K-弹性 IBE 的带关键字搜索公钥加密,” in *国际计算科学及其应用会议*, 2007, pp. 1086–1095.
14. D. Boneh, and X. Boyen, “无随机预言机的安全身份基加密,” in *年度国际密码学会议*, 2004, pp. 443–459.
15. D. Boneh, X. Boyen, and E.-J. Goh, “常量大小密文的分层身份基加密,” in *密码技术理论与应用年度国际会议*, 2005, pp. 440–456.
16. S. Kaushik, and C. Gandhi, “确保云环境中分层身份基数据安全,” *Int. J. Cloud Appl. Comput*, vol. 9, no. 4, pp. 21–36, 2019.
17. J. Bethencourt, A. Sahai, and B. Waters, “密文策略属性基加密,” in *2007 IEEE 安全与隐私研讨会 (SP'07)*, 2007, pp. 321–334.
18. V. Goyal, A. Jain, O. Pandey, and A. Sahai, “有界密文策略属性基加密,” in *国际自动机、语言与编程学术会议*, 2008, pp. 579–591.
19. V. Goyal, O. Pandey, A. Sahai, and B. Waters, “用于加密数据细粒度访问控制的属性基加密,” in *第 13 届 ACM 计算机与通信安全会议论文集*, 2006, pp. 89–98.
20. Y. Jiang, W. Susilo, Y. Mu, and F. Guo, “抗密钥委托滥用的雾计算密文策略属性基加密,” *Futur. Gener. Comput. Syst*, vol. 78, pp. 720–729, 2018.
21. M. Chase, and S. S. M. Chow, “改进多授权中心属性基加密中的隐私与安全,” in *第 16 届 ACM 计算机与通信安全会议论文集*, 2009, pp. 121–130.
22. P. K. Premkamal, S. K. Pasupuleti, and P. J. A. Alphonse, “用于云端大数据存储的高效无托管 CP-ABE，具有常量大小的密文和私钥,” *Int. J. Cloud Appl. Comput*, vol. 10, no. 1, pp. 28–45, 2020.
23. Z. Zhou, and D. Huang, “论高效的密文策略属性基加密和广播加密,” in *第 17 届 ACM 计算机与通信安全会议论文集*, 2010, pp. 753–755.
24. C. Delerablée, “常量大小密文和私钥的身份基广播加密,” in *密码学与信息安全理论及应用国际会议*, 2007, pp. 200–215.
25. C. Gentry, “基于理想格的全同态加密,” in *In Proc. STOC*, 2009, pp. 169–178.
26. S. Agrawal, X. Boyen, V. Vaikuntanathan, P. Voulgaris, and H. Wee, “基于格的阈值函数函数加密（或模糊 IBE）,” in *公钥密码学国际研讨会*, 2012, pp. 280–297.
27. D. Boneh, A. Raghunathan, and G. Segev, “函数隐私身份基加密：在函数加密中隐藏函数,” in *年度密码学会议*, 2013, pp. 461–478.
28. D. Boneh, A. Sahai, and B. Waters, “函数加密：定义与挑战,” in *密码理论会议*, 2011, pp. 253–273.
29. N. Attrapadung, and B. Libert, “内积函数加密：实现自适应安全的常量大小密文或支持否定,” in *公钥密码学国际研讨会*, 2010, pp. 384–402.
30. D. Boneh, and M. Franklin, “基于 Weil 配对的身份基加密,” in *年度国际密码学会议*, 2001, pp. 213–229.

# 第 3 章

# 可搜索加密与数据管理
