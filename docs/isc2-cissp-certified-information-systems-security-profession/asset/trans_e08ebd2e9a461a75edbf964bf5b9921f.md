
## 3. 系统性能测试

## 4. 测试系统漏洞

## 8. 关于主机入侵检测系统（HIDS）的以下哪项陈述是正确的？

1. 它监控整个网络。

2. 它监控单个系统。

3. 它对攻击者和授权用户不可见。

4. 它无法检测恶意代码。

## 9. 哪个以下选项是一个假网络，旨在诱骗入侵者，提供未修补和未受保护的安全漏洞以及虚假数据？

1. IDS

2. Honeynet

3. Padded cell

4. Pseudo flaw

## 10. 在以下选项中，哪种是最佳的防病毒保护形式？

1. 每个系统上多种解决方案

2. 组织范围内的单一解决方案

3. 在多个位置进行防病毒保护

4. 在所有边界网关处进行100%内容过滤

## 11. 在使用渗透测试验证安全策略强度时，以下哪项是**不推荐**的？

1. 模拟之前针对您系统的攻击

2. 在没有管理层知识的情况下进行攻击

3. 使用手动和自动化攻击工具

4. 重新配置系统以解决任何发现的漏洞

## 12. 在认证到系统时，用于让主体对其行为负责的手段是什么？

1. 身份验证

2. 监控

3. 账户锁定

4. 用户权限审查

## 13. 审计日志属于哪种类型的安全控制？

1. 行政

2. 侦测

3. 纠正

4. 物理

## 14. 哪个以下选项是对环境进行系统性的检查或审查，以确保符合法规并检测异常、未经授权的事件或犯罪行为？

1. 渗透测试

2. 审计

3. 风险分析

4. 诱捕

## 15. 哪种方法可以通过非统计手段减少记录或审计数据的量？

1. 削减级别

2. 抽样

3. 日志分析

4. 警报触发

## 16. 哪个选项更关注数据的模式和趋势，而不是实际内容？

1. 键盘监控

2. 流量分析

3. 事件日志

4. 安全审计

## 17. 哪种方式可以检测用户拥有超过其需要的特权？

1. 账户管理

2. 用户权限审计

3. 记录

4. 报告

*   请参考下面的情景回答问题 18 至 20。

*   一个组织有一个事件响应计划，要求在验证后报告事件。为了安全考虑，组织未公开该计划。只有事件响应团队成员知道该计划及其内容。最近，一名服务器管理员发现他管理的 Web 服务器运行速度比正常慢。经过快速排查后，他意识到攻击来自特定 IP 地址。他立即重启了 Web 服务器以重置连接并停止攻击。随后，他使用从互联网上找到的工具对该 IP 地址发起了持续数小时的攻击。由于该 IP 地址的攻击停止，他没有报告该事件。

## 18. 在重启 Web 服务器之前，应该做什么？

1. 审查事件

2. 执行修复步骤

3. 采取恢复步骤

4. 收集证据

## 19. 哪个选项表明服务器管理员在本次事件中犯了最严重的错误？

1. 重启服务器

2. 未报告事件

3. 攻击 IP 地址

4. 重置连接

## 20. 本次事件完全遗漏了什么？

1. 经验教训

2. 检测

3. 响应

4. 恢复

# Chapter 18  

Disaster Recovery Planning

**THE CISSP EXAM TOPICS COVERED IN THIS CHAPTER INCLUDE:**

*   **![images](images/correction.png) Domain 6: Security Assessment and Testing** 

    *   6.3 Collect security process data 

        *   6.3.5 Training and awareness

        *   6.3.6 Disaster Recovery (DR) and Business Continuity (BC)

*   **![images](images/correction.png) Domain 7: Security Operations** 

    *   7.11 Implement recovery strategies 

        *   7.11.1 Backup storage strategies

        *   7.11.2 Recovery site strategies

        *   7.11.3 Multiple processing sites

        *   7.11.4 System resilience, high availability, Quality of Service ( QoS ), and fault tolerance

    *   7.12 Implement Disaster Recovery (DR) processes 

        *   7.12.1 Response

        *   7.12.2 Personnel

        *   7.12.3 Communications

        *   7.12.4 Assessment

        *   7.12.5 Restoration

        *   7.12.6 Training and awareness

    *   7.13 Test Disaster Recovery Plans (DRP) 

        *   7.13.1 Read-through/tabletop

        *   7.13.2 Walkthrough

        *   7.13.3 Simulation

        *   7.13.4 Parallel

        *   7.13.5 Full interruption

![images](images/clogo.jpg) In Chapter 3, “Business Continuity Planning,” you learned the essential elements of business continuity planning (BCP)—the art of helping your organization assess priorities and design resilient processes that will allow continued operations in the event of a disaster.

Disaster recovery planning (DRP) is the technical complement to the business-focused BCP exercise. It includes the technical controls that prevent disruptions and facilitate the restoration of service as quickly as possible after a disruption occurs.

Together, the disaster recovery and business continuity plans kick in and guide the actions of emergency-response personnel until the end goal is reached—which is to see the business restored to full operating capacity in its primary operations facilities.

While reading this chapter, you may notice many areas of overlap between the BCP and DRP processes. Our discussion of specific disasters provides information on how to handle them from both BCP and DRP points of view. Although the (ISC)² CISSP curriculum draws a distinction between these two areas, most organizations simply have a single team and plan to address both business continuity and disaster recovery concerns. In many organizations, the single discipline known as business continuity management (BCM) encompasses BCP, DRP, and crisis management under a single umbrella.

## The Nature of Disaster

Disaster recovery planning brings order to the chaos that surrounds the interruption of an organization’s normal activities. By its very nature, a *disaster recovery plan* is designed to cover situations where tensions are already high and cooler heads may not naturally prevail. Picture the circumstances in which you might find it necessary to implement DRP measures—a hurricane destroys your main operations facility; a fire devastates your main processing center; terrorist activity closes off access to a major metropolitan area. Any event that stops, prevents, or interrupts an organization’s ability to perform its work tasks (or threatens to do so) is considered a disaster. The moment that information technology (IT) becomes unable to support mission-critical processes is the moment DRP kicks in to manage the restoration and recovery procedures.

A disaster recovery plan should be set up so that it can almost run on autopilot. The DRP should also be designed to reduce decision-making activities during a disaster as much as possible. Essential personnel should be well trained in their duties and responsibilities in the wake of a disaster and also know the steps they need to take to get the organization up and running as soon as possible. We’ll begin by analyzing some of the possible disasters that might strike your organization and the particular threats that they pose. Many of these are mentioned in Chapter 3, but we’ll now explore them in further detail.

