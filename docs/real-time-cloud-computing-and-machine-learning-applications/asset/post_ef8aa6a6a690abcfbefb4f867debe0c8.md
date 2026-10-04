
[27] Luo, Fa-Long., (Editor), Machine Learning for Future Wireless Communications, Wiley-IEEE Press (2020), ISBN: 978-1-119-56225-2, https://www.wiley.com/en-us/Machine+Learning+for+Future+Wireless+Communications-p-9781119562252.

[28] Kria, M. G., Nguyen, K., Villardi, G.P., Zhao, O., Ishizu, K and Kojiima, F. Big Data Analytics, Machine Learning, and Artificial Intelligence in Next-Generation Wireless Networks, in IEEE Access, vol. 6, p. 32328-32338, 2018, doi: 10.1109/ACCESS.2018.2837692.

[29] Hong, W., et al., Multibeam Antenna Technologies for 5G Wireless Communications, IEEE Trans. Antennas Propag., vol. 65, no. 12, p. 6231-6249, Dec. 2017.

[30] Black, E. J., al., Broadband Surface Scattering Antennas, US2017/081723A1, Jun. 2017.

[31] Wang, C., Renzo, M.D., Stanczak, S., Wang, S., and Larsson, E.G., Artificial Intelligence Enabled Wireless Networking for 5G and Beyond: Recent Advances and Future Challenges, in IEEE Communications, vol. 27, no. 1, pp. 16-23, February 2020, doi: 10.1109/MWC.001.1900292.

[32] Chen, Jiagang, Chunhua S, Zheng Yan, AI-Driven Cyber Security Analytics and Privacy Protection, Security and Communication Networks, vol. 2019, Article ID 1859143, 2 pages, 2019. https://doi.org/10.1155/2019/1859143.

[33] Fowdur, T. P., Beaherry, Y., Hurbungs, V., Bassso, V and Ramarnain-Seetohul, V. and Chan Moo Lun, E., Performance analysis and implementation of an adaptive real-time weather forecasting system, ELSEVI, Internet of Things 3–4 (2018) 12–33, https://doi.org/10.1016/j.iot.2018.09.002.

[34] https://cloud.google.com.

[35] https://aws.amazon.com/machine-learning/

[36] https://www.ibm.com/machine-learning.

[37] https://azure.microsoft.com/en-us/services/machine-learning/.

[38] https://azure.microsoft.com/en-us/services/cognitive-services/.

# Chapter 2

# CLOUD COMPUTING FUNDAMENTALS

In this chapter the fundamentals of cloud computing, basic definitions, terminologies, paradigms, architectures and service classes are described. A brief overview of two cloud computing platforms, namely Firebase and IBM Cloud is given. Basic configurations for storing data on real-time databases as well as hosting applications are for both cloud platforms. Moreover, the development of mobile, desktop and web applications that can send and receive data to the cloud are also fully elaborated.

# 2.1. DEFINITIONS OF CLOUD COMPUTING

Cloud computing has been referred to as a paradigm that encompasses a class of advanced computational facilities primarily provided on an on-demand basis by common providers, such as Amazon, Google, and Microsoft. It can be considered as a model which provides a powerful scalable computing system framework as a “cloud,” which provides applications and services on a demand basis with worldwide outreach to organisations and personal users [1]. The fundamental basis of this paradigm is the delivery of three main types of services which are processing power, storage, and software. The term 'cloud computing' and its specific characteristics have been defined by several researchers and professionals. Some of the most common definitions are quoted next [2].

The National Institute of Standards and Technology (NIST) [3] characterizes cloud computing as a “pay-per-use model for enabling available, convenient, on-demand network access to a shared pool of configurable computing resources (e.g. networks, servers, storage, applications, services) that can be rapidly provided and released with minimal management effort or service provider.”

A recent McKinsey and Co. report [4] claims that “Clouds are hardware based services offering compute, network, and storage capacity where: Hardware 20 T. P. Fowdur, L. Babooram, M. N-D-Ibn Nazir Rosun and M. Indoonondon management is highly abstracted from the buyer, buyers incur infrastructure costs as variable OPEX, and infrastructure capacity is highly elastic.

Buyya et al. [1] have defined it as: Cloud is a parallel and distributed computing system consisting of a collection of inter-connected and virtualised computers that are dynamically provisioned and presented as one or more unified computing resources based on service-level agreements (SLA) established through negotiation between the service provider and consumers.

In essence cloud computing can be viewed as a service infrastructure with the following five capabilities [5]:

- i. **Massive scalability** – Computation and/or storage services can be requested by the consumer as required. There is no need for the consumer to produce additional hardware and encounter all the issues associated with same cloud providers can cater for a fast provisioning of virtual servers, standardized hardware and persistent cloud storage.

- ii. **Universal access** – Worldwide accessibility from any place where the internet is a prominent feature of cloud computing. Similar to email, internet protocols can be used to provide pervasive access to cloud computing facilities.

- iii. **Granular usage management and charges** – One of the main factors driving the adoption of cloud computing is its associated economic advantages. The main characteristic that leads to this is granular usage management and charges. With cloud computing, users can lease processing power and storage based on requirements and a pay as you go by. For example, if a specific peak period, a high processing power is required, then it is only necessary to pay for that high processing power for for predefined period.

- iv. **Standardized resources** – Cloud computing provides uniform hardware, virtualization, and application platforms. However, the hardware and software need not necessarily be homogeneous and there is a lot of flexibility in terms of server configurations, application stacks such as Linux or Microsoft.Net, and programming languages such as Java, Python and C++. Maintenance and expansion costs are significantly reduced for cloud service providers when they restrict the range of options. Nonetheless the right balance between customer requirements and the available options must be maintained so that the limitations do not outweigh the business benefits from a customer satisfaction standpoint.

- v. **Management support services** – Management support services are an essential component in making cloud computing a comprehensive service. The operational and management facets of cloud computing are able to acquire the facilities they require without extra assistance from technical operators, to manage operational services. Management support services enhance the usage of cloud services by providing the necessary informative reports. CPU utilization reports, for instance, can allow the detection of unnecessary deployment of additional servers for tasks that could have been performed with fewer servers. Similarly, storage and bandwidth reports could help cloud users to optimize the use of these resources.

# 2.2. COMPUTING PARADIGMS

The cloud computing paradigm emerged as a result of the maturity and convergence of several of its supporting models and technologies which evolved in eight main phases. The first four phases shown in Figure 2.1 consists of mainframe computing, PC computing, network computing and internet computing.

![](img/2b52fde0e707e8c2f05a10309cf8982_32_0.png)
(a) Phase 1 : Mainframe Computing

![](img/2b52fde0e707e8c2f05a10309cf8982_32_1.png)
(b) Phase 2 : PC Computing

![](img/2b52fde0e707e8c2f05a10309cf8982_32_2.png)
(c) Phase 3 : Network Computing

![](img/2b52fde0e707e8c2f05a10309cf8982_32_3.png)
(d) Phase 4 : Internet Computing

Figure 2.1. The first four phases in cloud computing evolution.

Phase 1 involved the sharing of high-performing mainframes by several users using access terminals which could only provide an interface for the user to connect to the mainframe. All the processing, storage and software resources were found on the mainframe. In phase 2, stand-alone PCs had sufficient power to satisfy the requirements of the majority of users in terms of storage and processing power [6, 7].

Phase 3, termed as network computing, consisting of interconnected PCs and servers, which could share resources on a local network to improve performance. With the advent of the internet, local networks around the globe could be termed as interconnected to each other and share resources under certain restrictions. This was termed internet computing and constituted the fourth evolutionary phase. Figure 2.2 shows the last phases (phase 5 to phase 8) of the evolution to cloud computing.

The fifth phase which is termed as Grid Computing consists of a network of devices with processing power that are controlled by a specialized software such as middleware, which allows resources to be accessed and used externally via the
