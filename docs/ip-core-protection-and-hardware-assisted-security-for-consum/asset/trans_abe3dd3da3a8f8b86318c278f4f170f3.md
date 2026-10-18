

工作量证明（Proof-of-work）最初是由区块链开发者中本聪（Satoshi）提出的一种去中心化共识协议，用于保障比特币（Bitcoin）的一致性和安全性。作为比特币区块链上的交易，它们需要共识来验证区块。网络中存在不同的节点，其中几个节点相互竞争以计算新添加区块的哈希值。一旦某个节点计算出哈希值，它会等待其他节点完成并共同验证这些值。然后，生成的哈希值被添加到区块链中。如果多个节点找到了合适的解决方案，那么网络中可能会生成多个区块，这可能导致临时分支。在这种情况下，所有区块都是可接受的，且更接近矿工的节点会接受其接收到的解决方案并将其转发给其他对等节点。在任何时候，网络中的用户都接受最长的链。权益证明（Proof of stake）已被开发出来，以避免比特币中工作量证明（Proof Of Work）带来的高功耗问题。以太坊（Etherium）使用权益证明（Proof of Stake）作为共识机制。在权益证明（POS）中，加密货币被购买并用于网络中，从而减少了计算哈希值所需的高功耗。

## 2.9.4 区块链 – 问题

如前所述，区块链技术具有多种优势。但也存在一些缺点，其中主要问题是可扩展性。还需要整个区块链，即迄今为止发生的所有交易的完整列表，用于共识和验证。这需要巨大的存储容量。限制区块大小可以减少整个可扩展性问题。但这也会降低交易速度并增加交易费用。但使用大区块大小时，整个交易执行可能需要很长时间。比特币-NG（Bitcoin-NG）被提出，它具有减小的区块大小和增加的安全性。这可以通过将区块分为两个不同的部分来实现。

当区块链中创建分叉（Fork）时，所有节点需要等待很长时间来确认哪条链是最长且正确的分支。这会导致整个交易出现更高的延迟。区块链中还存在51%攻击问题，即50%的节点可以伪造区块并撤销交易。在这种情况下，计算能力掌握着所有权力，合法用户可能会面临问题。比特币矿工的功耗非常高。挖取一个比特币需要非常大的计算能力，这也会显著增加功耗。这可能导致投资高于回报的问题。

## 2.10 结论

本章讨论了物联网（IoT）设备和模块的不同安全缺陷。还为每个模块的安全问题提出了适当的解决方案。仍然有许多安全问题需要解决。还可能存在一些尚未发现的零日漏洞。发现安全缺陷的攻击者可以利用它们，无需将缺陷公之于众。可能存在许多安全缺陷和漏洞，它们存在但未被安全社区所知，且未在解决方案中得到解决。在这个领域，未来研究有着广阔的前景，可以提高安全性，并在物联网环境中实施强健的设计。

## 2.11 练习

1. 什么是物联网（IoT）？

2. 讨论物联网（IoT）的不同架构。

3. 讨论物联网（IoT）的三个应用。

4. 什么是可信消费电子系统？

5. 讨论物联网（IoT）的五个挑战？

6. 物联网（IoT）的驱动技术是什么？什么是事物（THING）？事物（THING）的属性是什么？

7. 什么是安全？什么是隐私？

8. 讨论物联网环境中攻击的分类法。

9. 可信消费电子系统的不同属性是什么？

10. 讨论消费电子系统安全 – 感知设计权衡。

11. 讨论安全的不同方面。

12. 讨论隐私的不同方面。

13. 什么是内存？嵌入式系统中存在多少种不同类型的内存？

14. 讨论内存系统上的两种安全攻击以及如何保护它们？

15. 什么是RFID？它在不同物联网应用中如何使用？

16. 讨论不同的RFID信道威胁和系统威胁。

17. 列出解决RFID安全问题的不同方案，并讨论其中三个。

18. 什么是法拉第笼（Faraday cage）？它如何工作？

19. 什么是近场通信（NFC）？它的优势是什么？在物联网环境中实施它的劣势是什么？

20. 讨论近场通信（NFC）中的四个安全问题。

21. 讨论近场通信（NFC）模块上的中继攻击和窃听攻击。

22. 什么是加密标签（Crypta tag）？它如何帮助保护近场通信（NFC）模块？

23. 自动驾驶汽车的不同部件有哪些？哪些组件受到欺骗攻击的影响？

24. 列出并讨论智能汽车上的不同攻击？

25. 什么是决策链？讨论智能汽车的决策链？

26. 讨论智能汽车安全问题的不同解决方案。

27. 什么是无人机（UAV）？它的应用有哪些？

28. 讨论无人机（UAV）安全的整体情况。

29. 安全性提高对无人机（UAV）有哪些不同影响？它如何影响飞行？

30. 讨论欺骗攻击是如何执行的？如何检测和缓解它？

31. 讨论智能医疗安全的整体情况。

32. 什么是HIPAA及其功能是什么？

33. 详细讨论智能医疗中的三个安全问题。

34. 描述胰岛素输送系统以及它如何受到攻击。

35. 讨论胰岛素输送系统的安全性。如何检测和缓解攻击？

36. 什么是固件（Firmware）？操作系统和固件之间有什么区别？

37. 讨论系统固件上的静态攻击和动态攻击。

38. 讨论固件安全解决方案。

39. 什么是区块链？是什么导致了区块链技术的发明？

40. 讨论新区块如何添加到当前区块链中。

41. 区块链有哪些不同的应用？

42. 阻碍区块链技术广泛采用的问题是什么？

## 参考文献

Ahmadi M., Rajamani R., and Sezen, S., ‘Transparent flexible active Faraday cage enables in vivo capacitance measurement in assembled microsensor,’ *IEEE Sensors Letters,* 2017, **vol. 1** (5), pp. 1–4.

Al-Kuwari M., Ramadan A., Ismael Y., Al-Sughair L., Gastli A., and Benammar M., ‘Smart-home automation using IoT-based sensing and monitoring platform,’ In: 2018 IEEE 12th International Conference on Compatibility, Power Electronics and Power Engineering (CPE-POWERENG 2018), pp. 1–6 (2018).

Alamri A., ‘Monitoring system for patients using multimedia for smart healthcare,’ *IEEE Access,* 2018, **vol. 6** (23), pp. 271–23, 276.

Almajali S., Salameh H. B., Ayyash M., and Elgala H., ‘A framework for efficient and secured mobility of IoT devices in mobile edge computing,’ In: 2018 Third International Conference on Fog and Mobile Edge Computing (FMEC), pp. 58–62 (2018).

Alrabady A. I. and Mahmud S. M., ‘Analysis of attacks against the security of keyless-entry systems for vehicles and suggestions for improved designs,’ *IEEE Transactions on Vehicular Technology,* 2005, **vol. 54** (1), pp. 41–50.

Andrews C., ‘Cyber car crime: Thieves turn to high tech \[Transport car crime\],’ *Engineering Technology,* 2017, **vol. 12** (2), pp. 32–35.

Asplund M. and Nadjm-Tehrani S., ‘Attitudes and perceptions of IoT security in critical societal services,’. *IEEE Access,* 2016, **vol. 4**, pp. 2130–2138.

