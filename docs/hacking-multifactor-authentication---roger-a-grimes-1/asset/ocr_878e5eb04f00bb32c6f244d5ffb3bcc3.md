# Chapter 16 Attacks Against Biometrics 349

individual papers on the subject here: (www.researchgate.net/scientific-contributions/2059653303-Daksha_(Yadav)) or download one of his relevant papers: (www.researchgate.net/publication/326915028_Fusion_of_Handcrafted_and_Deep_Learning_Features_for_Large-Scale_Multiple_Iris_Presentation_Attack_Detection/download. If you spend just a little time researching each and iris presentation attacks, you will see there are plenty and lots of researchers who have great success performing them and deceiving the others (and themselves) who try to prevent them.

# Facial Recognition Attacks

Next we will look at some example facial spoof attacks.

# Spoofing Windows Hello

As stated, Microsoft Windows Hello is one of the more difficult general public fingerprint and facial recognition technologies to fool, and this is true. That doesn't mean it can't be hacked. At the end of 2017, some German hackers (www.sysde.net/pentest-blog/2017/sys-2017-027-biometrics:bypassing-an-enterprise-grade-biometric-face-authentication-system/) although the article starts out in German, there is an English version that they found could take a picture of someone using a near-infrared camera and place that 1D image in front of Windows Hello, and it would accept it. You can see a video of how they did here: www.youtube.com/watch?v=OaqBwQlxSkGs&feature=youtube.be. More details can be found here well: selists.org/fulldisclosure/2017/Dec/77.

Part of the reason it worked is because Microsoft did not enable the enhanced anti-spoofing feature by default in Windows Hello. So, what is "enhanced anti-spoofing" and why doesn't Microsoft enable it by default? I could not find exact details of the Microsoft requirements for a biometric device to be branded as supporting Windows Hello enhanced anti-spoofing, but there are differences between the facial recognition cameras that can support enhanced anti-spoofing and those that do not. The best I can tell is that cameras supporting enhanced anti-spoofing support more pixels of infrared resolution and try their best to determine the difference between a spoofed face (2D—pictures and videos and 3D masks and objects) and real faces—liveness detection. Hardware and software with enhanced anti-spoofing capabilities likely do by this combination of one or more of the following:

+   * Checks ensure submitted image is 3D and real checking for depth, height, and texture differences. Paper and masks are likely to be far more uniform across all these checks.
* Checks if eyes are moving
* Checks to see if it is moving
* Checks to see if the area around the face is distinctly (i.e., not just a picture of a face held up on a piece of paper)