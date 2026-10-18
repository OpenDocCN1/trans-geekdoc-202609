

# University RWP

Rawalpindi, Pakistan

**Kashif Sattar**

助理教授

University Institute of Information Technology

PMAS-Arid University Rawalpindi

Rawalpindi, Pakistan

**Rakhi Seth**

National Institute of Technology

Raipur, India

**Shahida**

Arid Agriculture University Barani Institute of Sciences

Sahiwal, Pakistan

**Khurram Shahzad**

Department of Computer Science and Information Technology

The University of Lahore

Islamabad, Pakistan

**Aakanksha Sharaff**

National Institute of Technology

Raipur, India

**Awadhesh Kumar Shukla**

School of Computer Science and Engineering

Lovely Professional University

Phagwara, India

**Monica Sood**

Department of Computer Science & Engineering

Chandigarh University

Mohali, Punjab, India

**R Sujatha**

副教授

School of nformation Technology Engineering

Vellore Institute of Technology University

Vellore, India

**M N Talib**

Papua New Guinea University of Technology

Lae, PNG

**Imran Taj**

高级团队负责人，项目管理办公室

Information Systems Branch

Ministry of Attorney General and Public Safety Sector

BC Public Service

British Colombia, Canada

**Noor ul-Ain**

Barani Institute of Sciences Sahiwal Campus

JV of PMAS Arid Agriculture University RWP

Rawalpindi, Pakistan

**Hina Umbrin**

Barani Institute of Sciences Sahiwal Campus

JV of PMAS Arid Agriculture University RWP

Rawalpindi, Pakistan

**Khalid Hussain Usmani**

教授

Department of Computer Science

Barani Institute of Sciences

Sahiwal, Pakistan

**Sahil Verma**

Department of Computer Science and Engineering

Chandigarh University

Mohali, India

**N.S. Vishnu**

School of Computer Science and Engineering

Lovely Professional University

Phagwara, India

**Sobia Wassan**

Department of Business School

Nanjing UniversityJiangsu, China

**Sana Yasin**

Department of CS

UO Okara

Punjab, Pakistan

# 1 SC-MCHMP: Score-Based Cluster Level Hybrid Multi-Channel MAC Protocol for Wireless Sensor Network

Sowjanya Ramisetty, Divya Anand, Kavita, Sahil Verma, and Abdulellah A. Alaboudi

## CONTENTS

1. [1.1 Introduction](#ch01.xhtml#sec1_1)

2. [1.2 Literature Survey](#ch01.xhtml#sec1_2)

3. [1.3 Proposed Work](#ch01.xhtml#sec1_3)

4. [1.3.1 Procedure of Routing Mechanism](#ch01.xhtml#sec1_003_001)

5. [1.3.1.1 1-Hop Discovery](#ch01.xhtml#sec1_003_001_001)

6. [1.3.1.2 Metric Calculation](#ch01.xhtml#sec1_003_001_002)

7. [1.3.1.3 Link Score Calculation](#ch01.xhtml#sec1_003_001_003)

8. [1.3.1.4 Source Selection](#ch01.xhtml#sec1_003_001_004)

9. [1.3.2 CSMA/CA](#ch01.xhtml#sec1_003_002)

10. [1.3.3 TDMA](#ch01.xhtml#sec1_003_003)

11. [1.3.4 FDMA](#ch01.xhtml#sec1_003_004)

12. [1.4 Results and Discussion](#ch01.xhtml#sec1_4)

13. [1.5 Conclusion](#ch01.xhtml#sec1_5)

14. [References](#ch01.xhtml#chapter1_RL_1)

DOI: [10.1201/9780367808228-1](https://doi.org/10.1201/9780367808228-1)

## 1.1 Introduction

能源效率在传统的WSN中起着重要作用，旨在提高网络寿命，同时满足服务质量（QoS）的要求，例如延迟和带宽条件，这些要求不太重要。然而，现有的WSN多媒体实现（例如高速公路上的车辆流量，用于战场情报）需要可靠性和现实地检测事件的能力。大量信息在短时间内产生，导致更高的信道竞争程度和更高的数据包碰撞可能性。然而，WSN是为各种MAC协议设计的，旨在提高能源效率、可扩展性和吞吐量。WSN的各种医疗保健实现产生突发流量，产生更低的延迟、更高的吞吐量和更高的交付率。WSN无法使用单信道提供可靠且准时的数据传输，因为存在碰撞和受限带宽，且具有更高的数据速率要求。因此，过去几年中支持WSN内突发流量的研究人员被多信道通信所吸引。

当WSN的实施全面时，节点密度（单位面积内的节点数）会增加。这种方法在设计MAC层协议时带来了新的挑战。使用单一频率（信道），单个性能受到使用各种传统MAC协议的单信道限制的影响。此外，通过提出各种多信道MAC层协议，提高了WSN性能。与整个交通条件集内的单信道MAC协议相比，发现多信道MAC协议能源效率较低。由于网络密度增加时发生的干扰，单信道协议无法提供有效的实质性结果。为了在各种交通条件下实现更高的性能和能源效率，设计有效的多信道MAC协议至关重要。干扰的影响以及通过在各种频率信道上调度干扰传输来断言无线介质的影响，通过有效的方法（即多信道通信）得到缓解，以提高吞吐量。

WSN在能源消耗方面面临重大挑战，这影响了WSN的寿命。因此，数据收集、数据聚合和数据传输需要额外的能量。即使传感器节点处于睡眠状态且未处理时，能量也会耗尽。因此，通过要求高效的节能路由方法，构建了考虑端到端延迟和成本函数的低功耗平衡集群。集群成员接收到的数据由集群内部通信中的每个簇头（CH）聚合，然后通过中继节点将数据转发到沉节点。集群内部通信在集群中进行，其中每个节点收集数据并将其发送到相应的CH。感知到的聚合数据通过路由过程传输到沉节点，其中找到预定路径。

WSN面临着名为能源消耗的重大挑战，这影响了WSN的寿命。因此，数据收集、数据聚合以及数据传输需要额外的能量。即使传感器节点处于睡眠状态或未处理时，能量也会耗尽。因此，通过要求高效的节能路由方法，构建了考虑端到端延迟和成本函数的低功耗平衡集群。集群成员接收到的数据由集群间通信中的每个簇头（CH）聚合，然后通过中继节点将数据转发到沉节点。集群内部通信在集群中进行，其中每个节点收集数据并将其发送到相应的CH。感知到的聚合数据通过路由过程传输到沉节点，其中找到预定路径。

