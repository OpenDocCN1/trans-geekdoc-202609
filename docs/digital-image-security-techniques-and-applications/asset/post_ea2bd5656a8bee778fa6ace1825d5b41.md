
[15] Swaraja, K., Meenakshi, K., & Kora, P. (2021). Hierarchical multilevel framework using RDWT-QR optimized watermarking in telemedicine. *Biomedical Signal Processing and Control*, 68, 102688.

[16] Anand, A., & Singh, A. K. (2020). An improved DWT-SVD domain watermarking for medical information security. *Computer Communications*, 152, 72–80.

[17] Anand, A., & Singh, A. K. (2022). A hybrid optimization-based medical data hiding scheme for industrial Internet of Things security. *IEEE Transactions on Industrial Informatics*, 19(1), 1051–1058

[18] Thakur, S., Singh, A. K., Kumar, B., & Ghrera, S. P. (2020). Improved DWT-SVD-based medical image watermarking through hamming code and chaotic encryption. In *Advances in VLSI, Communication, and Signal Processing* (pp. 897–905). Springer, Singapore.

[19] Singh, O. P., Kumar, C., Singh, A. K., Singh, M. P., & Ko, H. (2021). Fuzzy-based secure exchange of digital data using watermarking in NSCT-RDWT-SVD domain. *Concurrency and Computation: Practice and Experience*, 35(16), e6251.

[20] Singh, O. P., & Singh, A. K. (2021). Data hiding in encryption–compression domain. *Complex & Intelligent Systems*, 9(11), 1–14.

[21] Thanki, R., Kothari, A., & Trivedi, D. (2019). Hybrid and blind watermarking scheme in DCuT–RDWT domain. *Journal of Information Security and Applications*, 46, 231–249.

[22] Singh, A. K., Kumar, B., Dave, M., & Mohan, A. (2015). Robust and imperceptible dual watermarking for telemedicine applications. *Wireless Personal Communications*, 80(4), 1415–1433.

[23] Prabha, K., & Sam, I. S. (2022). An effective robust and imperceptible blind color image watermarking using WHT. *Journal of King Saud University–Computer and Information Sciences*, 34(6, Part A), 2982–2992.

[24] Mahapatra, D., Amrit, P., Singh, O. P., Singh, A. K., & Agrawal, A. K. (2022). Autoencoder-convolutional neural network-based embedding and extraction model for image watermarking. *Journal of Electronic Imaging*, 32(2), 021604.

[25] Anand, A., & Singh, A. K. (2021). SDH: Secure data hiding in fused medical image for smart healthcare. *IEEE Transactions on Computational Social Systems*, 9(4), 1265–1273.

[26] Singh, O. P., Singh, A. K., Agrawal, A. K., & Zhou, H. (2022). SecDH: Security of COVID-19 images based on data hiding with PCA. *Computer Communications*, 191, 368–377.

[27] Singh, O. P., Anand, A., Agrawal, A. K., & Singh, A. K. (2022). Electronic health data security in the Internet of Things through watermarking: An introduction. *IEEE Internet of Things Magazine*, 5(2), 55–58.

[28] https://medpix.nlm.nih.gov/home

[29] https://commons.wikimedia.org/wiki

[30] Navas, K. A., Thampy, S. A., & Sasikumar, M. (2008). EPR hiding in medical images for telemedicine. *International Journal of Biomedical Sciences*, 3(1), 44–47.

[31] Khare, P., & Srivastava, V. K. (2021). A novel dual image watermarking technique using homomorphic transform and DWT. *Journal of Intelligent Systems*, 30(1), 297–311.

## Scalable edge computing architecture for multimedia data management
### Challenges and research avenues

Jaya Sinha
Galgotias College of Engineering and Technology, Greater Noida, India

Nivedita Palia
Vivekananda Institute of Professional Studies–Technical Campus,
Delhi, India

## 7.1 INTRODUCTION TO THE EDGE COMPUTING ECOSYSTEM

Expansion and development in the domain of Internet of things and achievement of cloud services have seen the rise of the innovative computing archetype known as Edge Computing. Edge computing means processing data nearer to the edge of the network, where it is generated. It enables the user to process a large amount of the data at high speed with a faster response time. Currently, Internet of things connects a wide variety of electronic and electrical devices that generate a huge volume of data. Data volumes will increase substantially as a result of technologies like 5G.

Today, digitalization is sweeping the globe, and an abundance of data is generated in various arenas. In most cases, processing of data needs to be done quickly to support real-time applications. Cloud computing technologies gradually reduce the requirement for small-scale and medium-scale industry to own their own system to perform computation tasks. Still, the end user requires transmitting and acquiring data to and from where the machine is located. Cloud computing is not always efficient to process data produced at the edge of the network, so micro data center [1, 2], fog computing [3], and Cloudlet [4] have been introduced. In the following paragraphs, we will present several reasons for the emergence of edge computing, along with a comparative study between them.

### 7.1.1 Dig into edge computing: drive from cloud computing, wrench from Internet of Things, data consumer to data producer

In terms of computation, cloud computing has proven to be efficient, but in some cases due to the large volume of data generated at the edge, cloud-based computing experiences a bottleneck in the speed of data transmission. For example, a Boeing 787 will generate 5 Gigabytes (GBs) data per second, and transmitting this data between the airplane to a satellite or a base station on the ground is inefficient for data processing [5]. Consider another example of autonomous vehicles—it will generate 1 GB data every second and requires data processing in real time for the vehicle to make the right decisions [6]. Also, as per reports by Data Age 2025, approximately more than 5 billion customers are presently interacting with data owing to extensive usage of social media services, among others, which is expected to increase up to 6 billion, i.e., about 75% of the global populace in 2025. An enormous rise in worldwide data is again expected in 2025 from 33 zettabytes in 2018 to 175 zettabytes with a very significant contribution by IoT instruments in terms of data produced globally [7]. It is, therefore, not feasible to send all the data to the cloud for processing, as the network bandwidth is a bottleneck. Moreover, edge computing processes data efficiently at the edge for shorter response time by consuming less energy as compared to cloud technology.

Currently, all electronic devices like LEDs, voice controllers, cameras, activity trackers, etc., are parts of the IoT, and they will act as data producers as well as consumers. Even more electronic gadgets will be linked to the IoT in the future. It is impractical for cloud computing to process lots of data efficiently due to bandwidth and latency. This indicates most of the data produced by IoT needs to be processed at the edge of devices.

Figures 7.1 and 7.2 show the roadmap of cloud and edge computing concepts respectively. In a cloud computing paradigm, raw data is generated and transmitted to the cloud, and the consumer accesses the data from the cloud by sending a request. This structure is not optimal for IoT devices functioning in the cloud environment due to the aforementioned reasons. Firstly, a large amount of data needs to be transmitted. Secondly, data privacy, and thirdly, energy consumption. To overcome these drawbacks, edge computing is the solution, as it maintains data privacy by processing data at edges, which could be further energy efficient [8], as shown in Figure 7.2.

![](img/6e4271af21d9a195003ab8711aa79d27_146_0.png)
Figure 7.1 Cloud computing concept.

![](img/6e4271af21d9a195003ab8711aa79d27_147_0.png)
Figure 7.2 Edge computing concept.

Previously, in the cloud computing paradigm, devices at the edge usually act as a data consumer, such as watching a YouTube video on a smart phone. Today, end users act as data producers by creating and uploading a reel to YouTube by a smart phone. This change of role from data consumer to data producer, and vice versa, forces more functions to the edge. When the edge user tries to upload images or videos clips, it could be reasonably large due to high resolution and occupy more bandwidth for the uploading. In that case, images and video clips need to be resized and transformed to the appropriate resolution at the edge before being uploaded to the cloud. Consider one example of wearable health devices where data is collected at the edge of network that is private. Therefore, it needs to process the data at edges to protect the user's privacy rather than uploading it to the cloud [8]. An exemplar layered infrastructure in this regard for edge computing has been presented in Figure 7.3.

The differences between cloud computing and edge computing are presented in Table 7.1. The distinctive features of edge computing include its widespread geographic distribution, mobility support, closeness to the end users. Edge computing aims to provide low latency and quick response time for real-time application as compared to cloud computing [1–4, 9, 10].

### 7.1.2 Contribution and novelty of the work

A voluminous rise in multimedia content over the internet has become clearly evident in recent years; with this comes challenges to handle and
