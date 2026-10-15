
## 9.5.6 传感器

这些传感器用于使系统完全自动化、安全且互联：

- **心率传感器**—血液波动可以通过放置在患者指尖周围的传感技术检测到。信号可以进一步传输给树莓派或其他设备。
- **温度传感器**—它们将用于通过相当于以摄氏度测量的温度的电脉冲来测量体温。
- **气泡探测器**—这些设备检测含有流体的容器或瓶子中的气泡。它们在包括医疗技术、过程控制、制药和石油工业在内的许多领域发挥重要作用。
- **湿度传感器**—这些传感器测量手术室内空气的湿度和温度。
- **睡眠监测仪**—它们将感知患者的睡眠时间，并同时感知患者当前是否正在睡眠。

## 9.5.7 后续阶段：移动应用程序的开发

这将是一个移动应用程序，将发送来自以下来源的警报信号：

Patient -> nurse, nurse -> doctor in emergency situations. 它将发送警报信号，这些信号将以振动的形式在接收者设备上接收到。此外，设备将与物联网平台连接，这些平台将收集数据并将其存储在云中；数据将从云中检索用于分析，并且紧急通知也将从 firebase 和 cloud functions 本身发送到其他互联设备。这将使对患者的护理质量更高效。因此，该应用程序将使患者更安全，并与护士和医生保持联系。图 9.5 表示智能医疗移动应用程序的人机交互。

## 9.6 医生平台

正如我们所知，我们项目中的医生平台与医生有关。一位医生可能有多名危重患者，而且医生还有大量进行常规检查的患者，因此医生不可能将全部时间都用于危重患者。因此，医生让护士记录他们的情况，护士会更频繁地探访患者。护士给医生的记录不是实时的，因为它是手动的。因此，我们创建了一个系统，排除了上述问题，允许医生与其他卫生线工作人员之间进行快速高效的沟通。

## 9.7 护士平台

同样，在开发的系统中也有一个专门为护士设计的平台。由于护士也有很多患者需要处理，而且他们的

![](img/7bb239370082cb34554bae1e45e2b0d7_182_0.png)

FIGURE 9.5 智能医疗移动应用程序的人机交互 [31]。

职责也经常发生变化，他们不可能对每个患者都给予充分关注。因此需要护士平台，使护士能够轻松管理他们的工作。他们还必须跟踪每位患者。在轻重不同的危急情况下，他们不能忽视病情较轻的患者。他们还需要对每个患者给予充分关注，因此拥有护士平台至关重要。护士平台的工作方式是，在危急情况下数据会与医生共享，但在不需要医生或患者需求常见的情况下，数据不会与医生共享。在平台的护士端，系统会振动，所有患者信息以及相关医生的姓名将显示在屏幕上通知，任何值班护士都可以照看他们。患者的特定需求也会在屏幕上提及。在紧急情况下，护士只需简单地传递数据并呼叫医生。

## 9.8 患者平台

在任何与健康相关的系统中，都必须拥有患者平台。在患者平台中，病情较轻且没有陪护人员的患者可以轻松照顾自己，因为他们在需要时可以轻松呼叫护士。但对于病情更危重且意识不清的患者，他们的陪护人员/亲属可以使用此平台在需要时呼叫护士。该患者平台非常有用，因为他们的实时健康

状况将被记录并与护士和医生共享。这将证明非常有帮助，因为它允许危重患者高效沟通。

## 9.9 智能医院系统的布局：设计未来医疗保健

在此框架中，患者平台可以向护士和医生发送警报信号，这将在设备上表现为振动。此外，在传感器的帮助下，患者的健康状况可以实时监测。

在危急情况下，护士本身可以实时向医生发送警报信号，以便患者能够立即接受治疗。传感器发送的信息将被存储在云中，并有助于对患者进行有效检查，包括患者的健康史和早期诊断。布局可在图 9.6–9.9 中表示。

![](img/7bb239370082cb34554bae1e45e2b0d7_183_0.png)

FIGURE 9.6 从各种传感器向患者平台收集信息。

![](img/7bb239370082cb34554bae1e45e2b0d7_183_1.png)

FIGURE 9.7 患者平台与护士平台和医生平台相连。

![](img/7bb239370082cb34554bae1e45e2b0d7_183_2.png)

FIGURE 9.8 护士平台与医生平台的互联。

![](img/7bb239370082cb34554bae1e45e2b0d7_184_0.png)

FIGURE 9.9 紧急情况下的蜂鸣信号。

## 9.10 结论

该项目能够以最小的成本监测并生成警报信号，以高警报振动和紧急通知的形式通知护士和医生患者的健康状况。Android 应用程序用于提供一个平台，以简单的 GUI 通知护士和医生患者的警报情况。

## 参考文献

- [1]. Khubchandani, P., Jha, K., Bijani, R., Lala, S. and Saindane, P., Medical prediction using artificial intelligence. International Journal of Engineering Science, 4898–4900 (2017).
- [2]. Svanström, A., IoT communication protocols in healthcare (Master’s thesis) (2016).
- [3]. Balasubramaniam, M. R., Sathya, R., Ashicka, S. and SenthilKumar, S., An analysis of RFID authentication schemes for Internet of Things (IOT) in healthcare environment using Elgamal Elliptic Curve cryptosystem. International Journal of Recent Trends in Engineering & Research (IJRTER), 2 (3) (2016).
- [4]. Rizwan, P., Rajasekhara Babu, M. and Suresh, K., Design and development of low investment smart hospital using internet of things through innovative approaches. Biomedical Research-Tokyo, 28, 4979–4985 (2017).
- [5]. Babu, R. and Dr. K. Jayashree, Prominence of IoT and cloud in health care. International Journal of Advanced Research in Computer Engineering & Technology (IJARCET), 5(2), 420–424 (2016).
- [6]. Alex, G., Varghese, B., Jose, J.G. and Abraham, A., A modern health care system using IoT and Android. International Journal on Computer Science and Engineering (IJCSE), 8(4) 98–101 (2016).
- [7]. B. Sobhan Babu, K. Srikanth, T. Ramanjaneyulu and I. Lakshmi Narayana, IoT for Healthcare. International Journal of Engineering Science and Research (IJSR), 2 (5), 322–326 (2016).
- [8]. Jiang, M., Gia, T. N., Anzanpour, A., Rahmani, A. M., Westerlund, T., Salanterä, S., Liljeberg, P. and Tenhunen, H., IoT-based remote facial expression monitoring system with sEMG signal. In 2016 IEEE sensors applications symposium (SAS) (pp. 1–6). IEEE (2016, April).
- [9]. Baker, S. B., Xiang, W. and Atkinson, I., 2017. Internet of things for smart healthcare: Technologies, challenges, and opportunities. IEEE Access, 5, pp. 26521–26544.
- [10]. S. Reddy, Use of artificial intelligence in healthcare delivery, eHealth – making health care smarter, Thomas F. Heston, IntechOpen (November 5th 2018). 10.5772/intechopen.74714.
- [11]. K. Patel, Benefits of IOT for hospitals and healthcare (2016).
- [12]. Christopher, G., Internet of things in healthcare: What’s next for IoT technology in the health sector (2016).
- [13]. B. Anderson, How mobile apps are improving access to healthcare services (2020).
- [14]. J. Burton, Smart cities solving today’s healthcare challenges (2020).
- [15]. Chiuchisan, I., Costin, H. and Geman, O., Adopting the internet of things technologies in health care systems (2014). 10.1109/ICEPE.2014.6969965.
- [16]. Tyagi, S., Agarwal, A. and Maheshwari, P., A conceptual framework for IoT-based healthcare system using cloud computing. In 2016 6th International Conference- Cloud System and Big Data Engineering (Confluence) (pp. 503–507). IEEE (2016, January).
- [17]. R. R. Biswas, Calibrating wastewater hydraulic model during post earthquake rapid rebuild works, Volume 5, Issue VI, International Journal for Research in Applied Science and Engineering Technology (IJRASET), pp. 461–470, ISSN: 2321-9653.
- [18]. Banka, S., Madan, I. and Saranya, S. S., Smart healthcare monitoring using IoT. International Journal of Applied Engineering Research, 13 (15), 11984–11989 (2018).
- [19]. Pandharkame and Hrishikesh P., Smart Hospitals using Internet of Things (IoT) (2017).
- [20]. P. Salunke and R. Nerkar, IoT driven healthcare system for remote monitoring of patients. International Journal for Modern Trends in Science and Technology, 3 (6), 100–103 (2017).
- [21]. Bharathan, M. P., Nadar, M. V. and Wayal, M. S. Remote health monitoring using IoT. International Journal of Advance Research, Ideas and Innovations in Technology (2017).
- [22]. Yu, L., Lu, Y. and Zhu, X., Smart hospital based on internet of things. Journal of Networks, 7 (10), 1654 (2012).
- [23]. Deshpande, U. and Kulkarni, M. (2017). IoT based real time ECG monitoring system using cypress WICED. 10.15662/IJAREEIE.2017.0602035.
- [24]. Rahman, H., Begum, S. and Ahmed, M. U., Ins and outs of big data: A review. In International Conference on IoT Technologies for HealthCare (pp. 44–51). Springer: Cham (2016, October).
- [25]. Kanase, P. and Gaikwad, S., Smart hospitals using internet of things (IoT). International Research Journal of Engineering and Technology (IRJET), 3 (03), 1735–1737 (2016).
- [26]. Nayak, S. S., Gupta, P., Upasana, A. B. W. and Wani, A. B., Wheel Chair with Health Monitoring System Using IoT. International Research Journal of Engineering and Technology (IRJET), 4 (05) (2017).
- [27]. S. M. W. Shah, and M. Pasha, IoT-based smart health unit. Journal of Software, 12 (1), 45–52 (2017).
- [28]. Gupta, P., Agrawal, D., Chhabra, J. and Dhir, P. K., IoT based smart healthcare kit. In 2016 International Conference on Computational Techniques in Information and Communication Technologies (ICCTICT) (pp. 237–242). IEEE (2016, March).
- [29]. Holzinger, A., Röcker, C. and Zieffle, M., From smart health to smart hospitals. In: Smart health (pp. 1–20). Springer: Cham (2015).
- [30]. Budida, D. A. M. and Mangrulkar, R. S., Design and implementation of smart HealthCare system using IoT. In 2017 International Conference on Innovations in
