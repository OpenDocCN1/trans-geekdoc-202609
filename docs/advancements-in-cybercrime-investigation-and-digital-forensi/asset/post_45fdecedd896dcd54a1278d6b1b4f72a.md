
Kamlesh, G., & Sanjay, S., (2011). New approach for fast color image encryption using chaotic map. *Journal of Information Security*, 2, 139–150.

Monisha, S., & Manoj, K. K., (2010). Image encryption techniques using chaotic schemes: A review. *International Journal of Engineering Science and Technology*, 2(6), 2359–2363.

Nguyen, P. B., Marie, L., & Azeddine, B., (2010). Statistical analysis of image quality metrics for watermark transparency assessment. *Lecture Notes in Computer Science*, 685–696. doi: 10.1007/978-3-642-15702-8_63.

Pooja, M., & Biju, T., (2013). A survey on various encryption and key selection techniques. *International Journal of Engineering and Innovative Technology (IJEIT)* (Vol. 2, No. 7). ISSN: 2277-3754.

Priya, R. S., & Vijaya, P. A., (2021). Performance evaluation of nested watermarked scheme using objective image quality metrics. *Journal of University of Shanghai for Science and Technology*, 23(6), 306–314. ISSN:1007-6735.

Sakthidasan, S. K., & Santhosh, K. B. V., (2011). A new chaotic algorithm for image encryption and decryption of digital color images. *International Journal of Information and Education Technology*, 1(2).

Sankpal, P. R., & Vijaya, P. A., (2014). Image encryption using chaotic maps: A survey. In: *2014 Fifth International Conference on Signal and Image Processing* (pp. 102–107). doi: 10.1109/ICSIP.2014.80.

Shima, R. M., & Supriya, M., (2011). An uncompressed image encryption algorithm based on DNA Sequences. *Computer Science & Information Technology (CS & IT)* (pp. 258–270). CCSEA, CS & IT 02.

Silpa, K., & Aruna, M. S., (2012). Comparison of image quality metrics. *International Journal of Engineering Research & Technology (IJERT)*, 1(4). ISSN: 2278-0181.

Somaya, A. M., Afnan, A. A. A., & Turki, A. (2012). A new chaos-based image-encryption and compression algorithm. Hindawi Publishing Corporation. *Journal of Electrical and Computer Engineering* (Vol. 2012). Article ID 179693.

Wang, Z., Bovik, A., & Sheikh, H., (2005). *Structural Similarity Based Image Quality Assessment*. Digital video image quality and perceptual coding, Ser. Series in Signal Processing and Communications. 10.1201/9781420027822.ch7.

## CHAPTER 4

### Wearable Devices Forensic Investigation

DEEPIKA DUBEY¹ and RICHA ROHATGI²

¹Research Scholar, Department of Forensic Science, Amity School of Applied Sciences, Amity University, Haryana, India

²Assistant Professor, Forensic Science, LNJN NICFS, National Forensic Science University, Delhi Campus, Rohini, New Delhi, India

### ABSTRACT

Wearable devices have become an integral part of our daily lives, and their adoption is increasing rapidly. Considering the importance and potential of these types of devices as evidence, the authors attempted to present a comprehensive sketch of wearable device forensics and its future directions. The chapter provides a comprehensive examination of the ways in which wearable technology is changing our daily lives and its potential implications for forensic investigations. It delves deep into the advantages of wearable devices for various user groups, including busy professionals, fitness enthusiasts, and the elderly and infirm. The chapter also provides an in-depth analysis of the types of data collected by these devices and their significance in forensic investigations. The various types of wearable devices available, including those worn as accessories, embedded in clothing, and even implanted in the human body are also covered in the chapter. The design principles, challenges, and opportunities of wearable device forensics, the admissibility of wearable devices as digital evidence, the digital forensics investigation process, and data extraction methods are also discussed in the chapter. The chapter concludes with a summary of key findings and recommendations for future research in wearable device forensics, providing a comprehensive and meaningful understanding of the technical, legal, and operational challenges and opportunities presented by this rapidly evolving technology.

### 4.1 INTRODUCTION

The adoption of wearable devices is increasing widely, and it is undoubtedly becoming an integral part of our lives. Wearable devices are revolutionizing the way we track our daily life activities. Such type of technology is very advantageous for busy professionals to stay informed with notifications while on the go, fitness enthusiasts track their workouts, and even the elderly and infirm by alerting emergency personnel if the device senses an unpleasant medical event. However, in order for these gadgets to function properly, they must collect information about the wearer, such as their location, biometric data, social media, calendar, and other information.

The geographical information, user’s physical and health statistics, different activity logs (e.g., sleeping, walking, calories burnt, etc.), and other sensitive information such as account details of social media communication and notifications of instant messaging applications, media files, etc., that are collected by these devices can play a huge role in forensic investigations (Kasukurtu & Patil, 2019). The devices are worn as accessories, embedded in clothing, and might even be implanted in human bodies and are a new emerging class of technology. These devices incorporate sensors, operating systems (OS), communications interfaces and numerous software applications that provide rich features like human-biometric monitoring, location tracking, video recording, navigation, calling, messaging, secretarial tasks, cardless payments and music streaming, among others. Such devices need to be connected to either a Wi-Fi or a cellular data network so that the recorded information can be synchronized with the cloud. The types of sensitive user information that may possibly be extracted from wearable devices are expected to play an important role in the future of digital forensics. The users have a close connection to the wearable devices which is continuously keeping track of what the user is doing, with large amounts of personally identifiable data being stored to a device to which it is relayed after being generated.

### 4.1.1 WEARABLE DEVICE TECHNOLOGY

Wearable device technology is a class of electronic device, which is used to track, analyze, and transmit personal data. These devices are physically carried as accessories, fixed somewhere in the body wear, implanted in the users’ body or sometimes may even be tattooed on the skin in order. Such smart technology can track heart rates, sleep patterns, calls, e-mails, messages, etc. Some of the most commonly used wearable devices are– Apple Watches, Fitbit, Samsung Galaxy Watch, Garmin Activity Tracker, Huawei Watch, etc. (Hayes, 2020).

These wearable devices usually rely on a short-range wireless technology such as Bluetooth, Wi-Fi or a login account to pair with a companion device. During setup, a wearable device is registered with the manufacturer and may be linked to a cloud server account, which is used to back up the user’s configuration, on board sensor data and logged activities. A smartphone application may also be used to manipulate the local configuration settings of the wearable device, update its firmware, load additional features, synchronize data with the cloud and visualize the collected data.

There is a wide range of wearable devices. However, the devices characteristically have similar engineering design constraints due to their small form factors. Without the assistance of paired devices, they may be unable to operate for long hours, store large quantities of data or provide rich applications and features. To mitigate these downsides, manufacturers design wearables with custom chips that consume low amounts of energy, and their sensors and applications are usually put in a standby mode when they are not needed. Storage capacity limitations are usually resolved by compressing and offloading data to cloud servers or paired smartphones. Strong transport protocols are engaged to increase the synchronization speed of the data. Some wearable devices even slot in cellular chipsets for increased mobility and performance (Loomis, 2019).

Smart glasses, fitness trackers and smartwatches collect large amounts of user data and store the data across the wearable devices, companion smartphones and cloud storage. Since these devices collect data continuously, they contain considerable amounts of digital evidence that are valuable in forensic investigations. A wearable OS is designed to work seamlessly across various wearable devices. It varies based on the type of wearable device and its specifications. These wearable devices are typically operated using two predominant operational methods. Some wearable devices operate unaided in an autonomous mode, whereas the others typically require internet-connected smartphones.

For instance, most smartwatches have built-in features that allow them to connect to the user’s smartphone to create a web interface. In such cases, the wearable OS acts similar to a mobile OS. This OS is designed to enable the
