86 Blockchain for Cybersecurity and Privacy

+   5.5.5 Access Control ................................................................................ 100

+   5.5.6 Authentication ........................................................................ 101

+   5.6 Open Issues and Future Directions ........................................................ 106

+   5.6.1 Identity Management ................................................................... 106

+   5.6.2 Access Control Management ........................................................ 106

+   5.6.3 Trust Management ....................................................................... 106

+   5.6.4 Intrusion Detection System ........................................................ 107

+   5.6.5 Hardware Security ....................................................................... 107

+   5.6.6 Privacy ................................................................................. 107

+   5.6.7 Protocols and Standards ............................................................ 108

+   5.7 Conclusion ................................................................................ 108

+   References ....................................................................................... 109

# 5.1 INTRODUCTION

# 5.1.1 BACKGROUND

The shift of computing paradigm closer to the end devices has enabled Internet of Things (IoT) to create a wide-open network. This open network has enabled diverse sensitive-applications such as smart cities (Awad et al. 2019), transportation (Battula et al. 2019), healthcare (Yang and Xu 2018), and disaster-related services (Uijwal et al. 2019). This open network facilitates the addition of devices into the information space, where the users not only consume the services but also contribute different kinds of resources for other applications. Moreover, the resources of IoT devices can currently be accessed by other devices as well network is based on centralized principles, which are prone to cyberattacks (Abonmah 2015). The limited resources in IoT devices and highly distributed nature and heterogeneity of the devices further add constraints in securing the open IoT network. Given the rise of IoT and its application in our daily lives, it is imperative to secure the network to prevent any security - privacy-related attacks.

Few security architectures and solutions have been proposed to address the security and privacy issues at each layer in the IoT paradigm. Khan and Salah (2018) proposed a taxonomy of IoT security solutions and discussed various types of threats on the application, communication channel, and hardware level. Similarly, Arias et al. (2015), Malina et al. (2016), and Chen et al. (2017) proposed multiple types of security solutions to address the security and privacy challenges in IoT networks. However, most of the security frameworks are purely based on a centralized architecture, which is not suitable for a widely distributed and decentralized IoT environment. Moreover, conventional algorithms proposed for wireless networks are not suitable for constrained IoT environments, where IoT network demand scalable, distributed security, and lightweight protocols. As such, ensuring the high level of security in a wide-open network as IoT network is still an open challenge owing to inherent features of IoT devices – limited resources, high distribution, and heterogeneity (Zhou et al. 2018).