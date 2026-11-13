
15. [Ying, Zhen, et al.](#ch8.xhtml#R_ref8_15) “An overview of computational models for industrial internet of things to enhance usability.” Complexity (2021).

16. [Sharma, Durga Prasad, et al.](#ch8.xhtml#R_ref8_16) “Emerging paradigms and practices in cloud resource management.” Autonomic Computing in Cloud Resource Management in Industry 4.0. Springer, Cham, 2021. 17–39.

17. [Indoria, Mayank, et al.](#ch8.xhtml#R_ref8_17) “Implementation of industry 4.0 to achieve sustainable manufacturing in steel industry: A case study.” Systematic Literature Review and Meta-Analysis Journal 2.1 (2021): 1–9.

18. [Zuo, Yanjun](#ch8.xhtml#R_ref8_18). “Making smart manufacturing smarter–a survey on blockchain technology in Industry 4.0.” Enterprise Information Systems 15.10 (2021): 1323–1353.

19. [Cots, Ainhoa, et al.](#ch8.xhtml#R_ref8_19) “Energy efficient smart plasmochromic windows: properties, manufacturing and integration in insulating glazing.” Nano Energy 84 (2021): 105894.

20. [Bermeo-Ayerbe, Miguel Angel, Carlos Ocampo-Martinez, and Javier Diaz-Rozo](#ch8.xhtml#R_ref8_20). “Data-driven energy prediction modeling for both energy efficiency and maintenance in smart manufacturing systems.” Energy 238 (2022): 121691.

21. [Krishnan, Priya R., and Josephkutty Jacob](#ch8.xhtml#R_ref8_21). “An IOT based efficient energy management in smart grid using DHOCSA technique.” Sustainable Cities and Society 79 (2022): 103727.

22. [Saleem, M. Usman, et al.](#ch8.xhtml#R_ref8_22) “Design, deployment and performance evaluation of an IoT based smart energy management system for demand side management in smart grid.” IEEE Access 10 (2022): 15261–15278.

23. [Sedhom, Bishoy E., et al.](#ch8.xhtml#R_ref8_23) “IoT-based optimal demand side management and control scheme for smart microgrid.” International Journal of Electrical Power & Energy Systems 127 (2021): 106674.

24. [Gerekli, İsa, Tarık Ziyad Çelik, and İbrahim Bozkurt](#ch8.xhtml#R_ref8_24). “Industry 4.0 and smart production.” TEM Journal 10.2 (2021): 799–805.

25. [Kotsiopoulos, Thanasis, et al.](#ch8.xhtml#R_ref8_25) “Machine learning and deep learning in smart manufacturing: The smart grid paradigm.” Computer Science Review 40 (2021): 100341.

# 9 The Role of Cybersecurity in Smart Cities

Azeem Khan and Noor Zaman Jhanjhi

Taylor’s University, Subang Jaya, Selangor, Malaysia

Mamoona Humayun

Jouf University, Al Jouf, Saudi Arabia

DOI: [10.1201/9781003203087-9](https://dx.doi.org/10.1201/9781003203087-9)

## 9.1 Introduction

Cities have been centers of civilization, symbolizing human progress ever since the beginning; due to this individuals and masses have been migrating toward cities in search of the betterment of living and this process is still in continuum and will be in the continuum due to opportunities that make human lives better in terms of economic and professional growth. The rural economy is primarily agrarian; hence, after the process of industrialization had begun, it paved the way for mass production, creating huge employment opportunities in cities; henceforth, people started flooding toward cities globally increasing the population in cities. With the advent of Information and Communication Technologies (ICTs), the process of automation started, which is still in continuum [[1](#ch9.xhtml#ref9_1) and [2](#ch9.xhtml#ref9_2)]. The application of ICT technologies in cities provisioned all the stakeholders involved in this ecosystem in tackling the problems associated with the administration of cities pertaining to basic infrastructures such as mobility, health, housing, education, public safety, environment, and energy thus paving the way for the emergence of cities that are interconnected and embedded with intelligent devices and were termed as smart cities. Smart cities are cities that are surrounded by a plethora of devices [[3](#ch9.xhtml#ref9_3), [4](#ch9.xhtml#ref9_4) and [5](#ch9.xhtml#ref9_5)] that are interconnected and intelligent. These technologies have eased the local governments in terms of increased efficiency in administration by improvising the basic facilities required by the inhabitants of the cities. Though civilian lives have been improved a lot and contributed to an enhanced quality of life, they have created many other challenges that are at the cost of compromised security and privacy. To address these challenges and to provide better solutions, cybersecurity has been proven to be of utmost significance and can’t be undermined. To simplify this concept of smart cities, we have summarized it with conceptual layers and the risks associated with them, as illustrated in [Figure 9.1](#ch9.xhtml#fig9_1).

![Figure 9.1 Cybersecurity attacks on various smart city infrastructure layers.](images/fig9_1_B.jpg)

[Figure 9.1 Cybersecurity attacks on various smart city infrastructure layers.](#ch9.xhtml#R_fig9_1)

The smart city architecture is envisioned as four layers. Each layer is connected with a distinct set of technologies and numerous possible cyber-attacks associated with them, which can’t be undermined at any cost; these are labeled above concerning each layer. Thus, succinctly, smart city provides digital infrastructure comprising ubiquitous sensing enabled through sensors, and communication among these is enabled with communication technologies such as WSN, 4G, Zigbee, Bluetooth, Z-wave, Near Field Communication (NFC), 5G, etc., and processing of the enormous data generated by this plethora of connected devices, which is termed as Big Data, is facilitated with cloud computing technology through data analytics by implementing sophisticated machine learning algorithms which are helpful in providing meaningful insights with the existing data generated on a real-time basis. This has empowered all the participants of this smart city environment by availing them to take intelligent decisions on time and improving the lives of citizens dwelling in cities who are able to access all the smart city infrastructure via applications in the form of apps [[6](#ch9.xhtml#ref9_6), [7](#ch9.xhtml#ref9_7) and [8](#ch9.xhtml#ref9_8)].

Each layer of this infrastructure is associated with the risks as well; at the application layer, the users’ systems can be compromised with cyber-attacks that may be cross-site scripts or injection attacks; apart from it, a common trap is gaining access to the system through authentication and authorization; there are also many other security risks at various layers, such as intrusion of viruses, worms, jamming, DDoS attacks at processing and communication layer, and last but not least, at the sensing layers, possible attacks and physical tampering of the devices typically leading to malfunction if they are deployed on unprotected and unsupervised physical environments [[9](#ch9.xhtml#ref9_9)].

The remaining part of the chapter is arranged as follows. [Section 9.2](#ch9.xhtml#sec9_2) throws light on the emerging state-of-the-art technologies for smart cities; [Section 9.3](#ch9.xhtml#sec9_3) is focused on expounding various applications and their cybersecurity threats associated with them; Sections [9.4](#ch9.xhtml#sec9_4) and [9.5](#ch9.xhtml#sec9_5) are dedicated to elaborating the proposed framework, open issues, and challenges pertaining to the cybersecurity of smart cities. Lastly, it is concluded with a note on possible future works.

## 9.2 Emerging State-of-the-Art Technologies for Smart Cities

There are several technologies involved in maintaining managing and securing the whole smart city ecosystem; to name a few are the emerging state-of-the-art technologies such as cloud computing, Big Data, and the Internet of Things (acronymized as IoT) [[10](#ch9.xhtml#ref9_10)], and among the communication technologies are the technologies such as RFIDs, WSN, Bluetooth, NFC, Zigbee, Z-wave, 4G, and 5G. They are summarized as follows.

### 9.2.1 Cloud Computing
