+   - 7.2.2.3 Attack Examples on Existing CBA Schemes....................185
+   - 7.2.2.4 Summary and Remarks........................................187
+   - 7.2.2.5 Conclusions..................................................188
+   - 7.3 Encryption of Scalable Video Coding...................................188
+   - 7.3.1 A Scalable and Format-Compliant Encryption Scheme for H.264/SVC Bitstreams................................................188
+   - 7.3.1.1 Structure of NALU..............................................189
+   - 7.3.1.2 Scalable and Format-Compliant Encryption....................191
+   - 7.3.1.3 Conclusions....................................................194
+   - 7.3.2 Efficient Block-Based Transparent Encryption for H.264/SVC Bitstreams.......................................................194
+   - 7.3.2.1 Motivation......................................................194
+   - 7.3.2.2 Proposed Transparent Encryption Scheme......................195
+   - 7.3.2.3 Experiments and Evaluation....................................196
+   - 7.3.2.4 Conclusions....................................................199
+   - 7.4 Authentication of Scalable Video Coding...............................199
+   - 7.4.1 A Hybrid Scheme for Authenticating Scalable Video Codestreams...................................................200
+   - 7.4.1.1 Motivation......................................................201
+   - 7.4.1.2 Hybrid Authentication Scheme of Scalable Video Coding......201
+   - 7.4.1.3 Experiments and Comparison....................................203
+   - 7.4.1.4 Conclusions....................................................205
+   - 7.5 Conclusion...........................................................205
+   - References..............................................................206

# 7.1 Scalable Video Coding

Digital video is pervasive and has applications in diversified areas such as remote education, telemedicine, surveillance, IP TV and video-on-demand. In order to cater for heterogeneous networks and various terminal devices, many video coding schemes (e.g., [1,2]) have been designed. However, few of them are widely deployed due to low compression efficiency and/or non-scalability. Fortunately, after at least 20 years of research and experiments, SVC (Scalable Video Coding) [3,4] was finally adopted as an international standard for video coding in 2007. Generally speaking, due to its high improvement in coding efficiency and scalability, SVC is attractive in today’s ubiquitous networking environments.

SVC possess the so called “compress once, decompress many times” properties, hence it automatically adapts to network bandwidth as well as capabilities of end user devices. For the sake of scalability, Internet-based multimedia content dissemination increasingly resorts to autonomous proxies to distribute, transcode and aggregate information from content servers to end users, Where multimedia content