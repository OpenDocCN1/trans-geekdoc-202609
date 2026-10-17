
Heitz, Jakob, Keyur Patel, Job Snijders, Ignas Bagdonas, and Nick Hilliard. “BGP Large Communities.” Internet-Draft. Internet Engineering Task Force, January 2017. [`tools.ietf.org/html/draft-ietf-idr-large-community-12`](https://tools.ietf.org/html/draft-ietf-idr-large-community-12).

“Intermediate System to Intermediate System Intra-Domain Routing Information Exchange Protocol for Use in Conjunction with the Protocol for Providing the Connectionless-Mode Network Service.” Standard. Geneva: International Organization for Standardization, 2002. [`standards.iso.org/ittf/PubliclyAvailableStandards/`](http://standards.iso.org/ittf/PubliclyAvailableStandards/).

Katz, Dave. “OSPF and IS-IS: A Comparative Anatomy.” Presented at the NANOG19, Albuquerque, NM, June 12, 2000. [`nanog.org/meetings/abstract?id=1084`](https://nanog.org/meetings/abstract?id=1084).

McPherson, Danny R., and Keyur Patel. *Experience with the BGP-4 Protocol*. Request for Comments 4277. RFC Editor, 2006. doi:10.17487/rfc4277.

Meyer, David, and Keyur Patel. *BGP-4 Protocol Analysis*. Request for Comments 4274. RFC Editor, 2006. doi:10.17487/rfc4274.

Mirtorabi, Sina, Abhay Roy, Acee Lindem, and Fred Baker. “OSPFv3 LSA Extendibility.” Internet-Draft. Internet Engineering Task Force, October 2016. [`tools.ietf.org/html/draft-ietf-ospf-ospfv3-lsa-extend-13`](https://tools.ietf.org/html/draft-ietf-ospf-ospfv3-lsa-extend-13).

Moy, John. “OSPF Version 2.” Request for Comments 2328. RFC Editor, April 1998. doi:10.17487/RFC2328.

Parker, Jeff. *Recommendations for Interoperable Networks Using Intermediate System to Intermediate System (IS-IS)*. Request for Comments 3719. RFC Editor, 2004. doi:10.17487/rfc3719.

Przygienda, Dr. Antoni B. *中间系统到中间系统中的可选校验和 (ISIS)*. Request for Comments 3358. RFC Editor, 2002. doi:10.17487/rfc3358.

Ramachandra, Srihari S., and Yakov Rekhter. *BGP 扩展社区属性*. Request for Comments 4360. RFC Editor, 2006. doi:10.17487/rfc4360.

Raszuk, Robert, Christian Cassar, Bruno Decraene, Stephane Litkowski, Kevin Wang, and Erik Aman. “BGP 最优路由反射 (BGP-ORR).” Internet-Draft. Internet Engineering Task Force, January 2017. [`tools.ietf.org/html/draft-ietf-idr-bgp-optimal-route-reflection-13`](https://tools.ietf.org/html/draft-ietf-idr-bgp-optimal-route-reflection-13).

Rekhter, Yakov, Susan Hares, and Tony Li. *边界网关协议 4 (BGP-4)*. Request for Comments 4271. RFC Editor, 2006. doi:10.17487/rfc4271.

Retana, Alvaro, and Russ White. “BGP 自定义决策过程.” Internet-Draft. Internet Engineering Task Force, February 2017. [`tools.ietf.org/html/draft-ietf-idr-custom-decision-08`](https://tools.ietf.org/html/draft-ietf-idr-custom-decision-08).

Roy, Abhay, Yi Yang, and Alvaro Retana. *在 OSPF 中隐藏仅为转发的网络*. Request for Comments 6860. RFC Editor, 2013. doi:10.17487/rfc6860.

Shand, Mike, Stefano Previdi, Les Ginsberg, and Danny R. McPherson. *IS-IS 链路状态 PDU (LSP) 空间的简化扩展*. Request for Comments 5311. RFC Editor, 2009. doi:10.17487/rfc5311.

Suurballe, J. W. “网络中的不相交路径.” *Networks* 4, no. 2 (1974): 125–45. doi:10.1002/net.3230040204.

Vohra, Quaizar, and Enke Chen. *BGP 对四字节自治系统号 (AS) 号码空间的支持*. Request for Comments 6793. RFC Editor, 2012. doi:10.17487/rfc6793.

Walton, Daniel, Alvaro Retana, Enke Chen, and John Scudder. *BGP 持续路由振荡的解决方案*. Request for Comments 7964. RFC Editor, 2016. doi:10.17487/rfc7964.

Wang, Lili, Zhaohui (Jeffrey) Zhang, and Nischal Sheth. *OSPF 混合广播和点到多点接口类型*. Request for Comments 6845. RFC Editor, 2013. doi:10.17487/rfc6845.

“What Are the Differences between NP, NP-Complete and NP-Hard? Stack Overflow.” Accessed September 24, 2017. [`stackoverflow.com/questions/1857244/what-are-the-differences-between-np-np-complete-and-np-hard`](https://stackoverflow.com/questions/1857244/what-are-the-differences-between-np-np-complete-and-np-hard).

White, Russ. *中间系统到中间系统 (IS-IS) 路由协议 LiveLessons*. Video. LiveLessons. Cisco Press, 2016. [`www.ciscopress.com/store/intermediate-system-to-intermediate-system-is-is-routing-9780134465326?link=text&cmpid=2017_02_02_CP_RussWhiteVideo`](http://www.ciscopress.com/store/intermediate-system-to-intermediate-system-is-is-routing-9780134465326?link=text&cmpid=2017_02_02_CP_RussWhiteVideo).

White, Russ. “iSPF Versus PRC.” *Rule 11 Reader*, June 7, 2017. [`rule11.tech/ispf-verse-prc/`](https://rule11.tech/ispf-verse-prc/).

White, Russ, Danny McPherson, and Srihari Sangli. *Practical BGP*. Boston, MA: Addison-Wesley Professional, 2004.

White, Russ, and Alvaro Retana. *IS-IS: Deployment in IP Networks*. 1st edition. Boston, MA: Addison-Wesley, 2003.

## Review Questions

1. Read through the additional material on DFS numbering systems. The concept of the low point was left out of the main text for brevity. Can you expand on this concept and the importance of finding the low point in determining disjoint paths through the network?

2. Compare the operation of Bellman-Ford and Dijkstra in a network with negative cost links; draw a small network of six or seven routers, set one of the links so it has a negative cost in both directions, and determine the set of loop-free paths through the network using both algorithms. You do not need to run the algorithm to do this in a formal way; just describe which paths the Dijkstra algorithm will have a problem with and how the Bellman-Ford algorithm will react to these same paths.

3. Run MRT across the network shown in Figure 13-19 and show the resulting disjoint topologies.

4. Run Dijkstra’s SPF across the network shown in Figure 13-19 from the perspective of A, using a cost of 1 for each link. Show the resulting shortest paths.

5. Using the network shown in Figure 13-19, assuming all link costs are 1, what would be the best path toward G? Would D have an LFA or rLFA in this network?

6. Is there any way you can think of to ensure connectivity exists with a unidirectional connectivity problem, such as the submarine example given in the note?

1. Dijkstra, “A Note on Two Problems in Connexion with Graphs.”

2. Suurballe, “Disjoint Paths in a Network.”

### Chapter 14 Reacting to Topology Changes

#### Learning Objectives

After reading this chapter, you should be able to understand:

![Image](img/bull.jpg)收敛过程的四个步骤

![Image](img/bull.jpg)使用轮询和事件驱动机制进行拓扑变化检测

![Image](img/bull.jpg)双向转发检测

![Image](img/bull.jpg)记录级复制和泛洪

![Image](img/bull.jpg)微环路

![Image](img/bull.jpg)逐跳控制平面状态分发

![Image](img/bull.jpg)CAP 定理及其与控制平面的交互

You might have noticed that very few of the mechanisms described in Chapter 12 “Unicast Loop-Free Paths (1),” and Chapter 13, “Unicast Loop-Free Paths (2),” considered changes in the topology. Most of these solutions are focused on computing loop-free paths through an apparently stable network, as discovered by the mechanisms described in Chapter 11, “Topology Discovery.” But what happens when the topology changes? Returning to the introduction of Part II:

**How do network devices build the tables needed to forward packets along loop-free paths through the network?**

Now it is time to consider one more of the subproblems of this overarching problem:

**How do control planes detect and react to changes in the network?**

This question will be answered by examining two components of the convergence process in a control plane. The convergence process in a network can be described in four stages. Figure 14-1 is used for reference in describing these four stages.

![Image](img/14fig01.jpg)

**Figure 14-1** *The Convergence Process*

Once the `[C,E]` link fails, the four stages that must occur are *detection, distribution, computation*, and *installation.*

1. **Detecting the change:** Whether the inclusion of a new device or link, or the removal of a device or link, regardless of the reason, the change must be detected by any connected devices. In Figure 14-1, devices C and E must detect the failure of the `[C,E]` link; when the link is brought back up, they must also detect the inclusion of this (apparently new) link in the topology.
