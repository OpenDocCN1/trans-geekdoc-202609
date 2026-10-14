+   10.5 Receiver Process ........................................................ 278
+   10.5.1 Reception of the Encrypted Message ................................ 279
+   10.5.2 Decryption Stage .................................................... 279
+   10.5.2.1 Reverse Process of Confusion Method............................ 279
+   10.5.2.2 Reverse Process of Diffusion Method............................ 280
+   10.5.3 Transmission of Recovered Message................................ 280
+   10.6 Experimental Results ................................................. 281
+   10.6.1 Proposal of Simple Operative System Based in Chaos............. 281
+   10.6.2 Experimental Results on the ES.................................... 283
+   10.6.2.1 Time Complexity of the Algorithms.............................. 283
+   10.6.2.2 First Test: Sensitivity of Secret Keys.......................... 285
+   10.6.2.3 Second Test: Animation of the Chaotic Oscillator as Message m₁(t) ................ 285
+   10.6.2.4 Third Test: MP3 Audio File as Voice Message m₂(t)... 286
+   10.7 Conclusions .......................................................... 290
+   Acknowledgments .......................................................... 290
+   References ............................................................... 290
+   Appendix A: DNA Sequence Matrix .......................................... 292

# 10.1 Introduction

Embedded systems (ES) are used to develop and integrate a large number of electronic devices for wired and wireless communication. Audio and video applications with graphic interfaces in smart displays have been increasing such as in Liquid Cristal Display (LCD) monitors, tablets, and smart-phones. It is indispensable that the use of output data allows the designer to observe the behavior of the systems and validate in a smart-display [1]. Indeed, the smart display is one device able to adapt its behavior and its structure following the semantic of data output produced by the development of some application by using internal hardware peripherals of ES. Depending on the application, it is more convenient and economical to use some communication protocol that allows the use of fewer communication lines in the internal peripherals of an ES, where the link is secure [2]. The Inter-Integrated Circuit (I2C) protocol was created by Philips Semiconductors [3,4], and the Serial Peripheral Interface (SPI) protocol was created by Motorola Inc. [5]. Both types of protocols coexist in modern digital electronic systems, and probably these protocols will continue complementing each other in the future because they are inexpensive of implementation [6].

The SPI protocol allows communication between peripherals and electronic devices. The mode of connection of these devices can be assigned in master and slave modes. The SPI protocol has been adopted by many manufacturers of integrated circuits (ICs) in wired and wireless communications since SPI protocol requires fewer communication lines and low cost of implementation. Recently, the literature reports some applications of the SPI protocol in ES with secure link [7].