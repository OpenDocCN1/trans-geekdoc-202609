

## Chapter 30

## Application of Video-Based Face Recognition for Mobile Security Using Machine Learning Techniques

Emir Kremić and Abdulhamit Subasi

## Contents

- 30.1 Introduction ... 888
- 30.2 Background ... 890
- 30.3 Material and Method ... 891
  - 30.3.1 Overview ... 893
  - 30.3.2 Human Biometric System ... 893
  - 30.3.3 Connection of Brain ... 895
  - 30.3.4 Module of Visual Protection ... 896
  - 30.3.5 Method ... 896
- 30.4 Operational Concept ... 897
  - 30.4.1 Machine Learning Methods and Techniques ... 898
- 30.5 Android Established Biometrics’ Security System ... 904
  - 30.5.1 What is Android and Why Use It? ... 905
    - 30.5.1.1 Android: Application Architecture ... 906
    - 30.5.1.2 The Dalvik Virtual Machine ... 906
    - 30.5.1.3 Biometric System and Application ... 906
    - 30.5.1.4 Running and Testing Application ... 907
    - 30.5.1.5 Mobile Security ... 908
- 30.6 Architecture ... 908
- 30.7 Testing and Results ... 910
- 30.8 Conclusion ... 912
- 30.9 Summary ... 912
- References ... 913

### 30.1 Introduction

With an increasing dependence on smartphones, mobile phones went beyond communication’s purpose. Nowadays, smartphones are used to implement a wide range of daily tasks such as: banking, shopping, ordering food, etc. Moreover, mobile phones are becoming more complex to meet consumer’s needs (Zualkernan, Aloul, Shapsough, Hesham, & El-Khorzaty, 2017).

The smartphone is a pervasive device used to simplify daily activities, such as storing personal information related to credit cards, user passwords, e-mail addresses or other credentials which may increase the severity and risk of identity theft (Sidek, Mai, & Khalil, 2014).

In this era, the reliability of real-time personal identification in mobile devices is a crucial requirement. The automatic identification of individuals built on their physical characteristics is called as biometric authentication, such as keystroke, voice, iris, gait, face and fingerprint. Although biometric identification systems can eliminate the limitations relevant to the use of passwords, they are vulnerable to spoofing attacks (Jain, Nandakumar, & Ross, 2016; Jain, Ross, & Nandakumar, 2011). Actually, gait and keystroke identification techniques are not very secure in terms of identification accuracy. Similarly, a face which is exposed as an artificial mask, a voice which might be imitated, a fingerprint which might be falsified by a gummy fingerprint, and an iris which might be duplicated by means of contact lenses, are also not robust against falsifications (Sidek et al., 2014). Recently, face recognition based on video was proposed as a potential biometric identification technique due to the robustness (Kremić & Subasi, 2016).

Mobility is a significant element of mobile biometrics. In order to keep personal information on mobile devices, for improved security the feasibility of person identification techniques on mobile devices is imperative. To confirm voters in elections, to identify customers in financial institutions, or to identify automobile drivers are possible by recognizing video-based biometric applications. In order to protect private information and individual identity against unauthorized access, these applications need to be consistent, reliable, and easy to implement for identification (Sidek et al., 2014). Nowadays, mobile devices and applications are increasing quickly, and the necessity for security in storing business and personal data or accessing web data is to use innovative biometric authentication techniques.

In addition, traditional mobile login methods, like numerical or graphical passwords, and face recognition are vulnerable to passive attacks. Biometric characteristics such as voice recognition, iris scans, or fingerprints etc. can be changed easily and replaced if they are stolen. Video-based biometric authentication system can eliminate this problem (Kremić & Subasi, 2016).

Facial recognition from video is focused on the analysis and retention building that are the skills for self-learning and training in future artificial models of human recognition systems. The intention of this chapter is to syndicate the area of theory and practice. The model denoted and developed for face recognition from video for the mobile phone is implemented on an Android platform. The system is designed to work for *client–server* architecture. Research in the field of pattern recognition, machine learning, artificial intelligence, etc., are enabling us to apply and use such a novel mobile application development system. Such application does not aggregate the subject of machine learning, nor pattern recognition for video to still image face recognition, yet it combines the skills of software development integrated into smart applications by extending the human security as a future model of authentication. Such a problem does not only include achieving higher accuracy, but it involves building a stable model that will be referenced for its extended version in future development.

A very common verification method applied on mobile phone is the *Personal Identification Number (PIN)*. In this chapter, we present the work related to the implementation of face authentication. Therefore, we will stress on theoretical approaches, accuracy of the methods and implementation. The aim is to present the client–server model for video to still image that works on Android Samsung Galaxy Note 10.1, as well as on Samsung Galaxy S. Even biometry inherits advantages over the traditional model. The problem of ensuring the security and integrity of biometric data is critical (Alhussain, Drew, & Alfarraj, 2010). Individuals have a good sense for recognizing and identifying known faces. However, humans are not proficient when they are transacting a multifarious number of faces that are unfamiliar. Even today, video recognition is not a fully solved problem in face recognition. A great deal of aforementioned research related to biometric has examined the fusion of modalities at score and decision levels (Mian, 2011). Actually, Woodrow W. Bledsoe, back in 1960s, was initially the first engineer who started working in the area of face recognition (Bledsoe, 1966). Bledsoe’s work was for an intelligence agency and very few papers were published related to the area of his work. Chan and Bisson, besides Bledsoe, have worked by applying the computer for recognition of the human faces (Mian, 2011). Development of a semi-automatic system was used as a prototype for the facial recognition system. Computers were using information for face recognition from the semi-automatic system, where data of collected faces was determined by face coordinates input by humans.

Even now face recognition is an undeveloped area of video-based work; however, research has grown in recent years. It represents an innovative obstacle to explore, and that is recognizing face images from video signals. In near future, modern laptops will be replaced by mobile phones. Consequently, the goal is to develop and design a constant security structure determined by application of facial recognition from video signal and to empower better security advancements. Determination is important, since almost all the main businesses are running on mobile phones these days. Hence, it is decisive to design a mobile phone with a developing biometric system for automated face recognition. It is very difficult to distinguish if it is easy for humans to extract facial expressions independently from the identity of the subject. How can a biological implementation of a computerized face recognition system identify faces? Sinha et al. (2006) have presented the key goal of computer vision for creating automated face recognition which is divided to nineteen parts, all based upon biometric facial security implemented on mobile devices (Kremić, 2011). Today we have come to an extent where we are presenting the face recognition from video still image for Android mobile phones. In this chapter, we will present our work as well as the accomplished work of Kremić and Subasi (2016) vis a vis facial recognition solutions.

### 30.2 Background

In the recent years, smartphones play an important role for the adaptation of security mechanisms based on biometrics. Different types of modalities have been used to implement mobile based biometric recognition such as the use of face, gait and iris (Derawi, Nickel, Bours, & Busch, 2010; Kurkovsky, Carpenter, & MacDonald, 2010; Kwapisz, Weiss, & Moore, 2010; Tao & Veldhuis, 2010), electrocardiogram (ECG), (Biel, Pettersson, Philipson, & Wide, 2001; Choi, Lee, & Yoon, 2016; Islam, Alajlan, Bazi, & Hichri, 2012; Kang, Lee, Cho, & Park, 2016; Merone, Soda, Sansone, & Sansone, 2017; Odinaka et al., 2012; Odinaka, O’Sullivan, Sirevaag, & Rohrbaugh, 2015; Safie, Soraghan, & Petropoulakis, 2011; Sidek & Khalil, 2013; Sidek et al., 2014; Venugopalan, Savvides, Grioafa, & Cohen, 2014) and electroencephalogram (EEG) (Campisi & La Rocca, 2014; Chen et al., 2016; Fraschini, Hillebrand, Demuru, Didaci, & Marcialis, 2015; Klonovs, Petersen, Olesen, & Hammershoj, 2013; Kumari & Vaish, 2015; Rodrigues, Silva, Papa, Marana, & Yang, 2016). Face, fingerprint, iris and DNA determine biological and/or behavioural characteristics of the individual used for biometric identification (Da Silva, Fred, Lourenço, & Jain, 2013). Therefore, principles of uniqueness, universality and acceptability are achieved by these personalities (Jain, Bolle, & Pankanti, 2006). Furthermore, research for the development of a biometric identification system based on an individual’s characteristics with uniqueness, universality, and acceptability is needed for biometric applications to achieve biometric identification tasks through user-friendly systems.

The potential solutions by implementing a biometric security system for authentication can play a positive role, because necessity of security is needed to secure

