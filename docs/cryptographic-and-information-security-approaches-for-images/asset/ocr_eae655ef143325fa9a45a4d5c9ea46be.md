# 24.1 Introduction

There has been a tremendous rise in the rate of cyber crimes related to multimedia content in recent times with the advancement of technology. Multimedia content, especially digital images on the internet have always been the target of visual content manipulation attacks due to the ease of modification with the availability of powerful image manipulation programs. Malicious visual content manipulation, also known as image tampering, has become common. Digital images have become the part and parcel of information sharing on the internet in a plethora of forms like memes, infographics and photos by citizen-photojournalists. Concerns over the trustworthiness of such images have become alarmingly high with their quick proliferation.

Image tampering detection is a sub problem of image forensics. Tamper detection, along with integrity verification and source identification, help accomplish the task of evidence authentication. Evidence authentication is in itself one of the major tasks of image forensics.

Copy-move attack is the most common image tampering technique and has been around for many years. This forgery technique is synonymous with region duplication and cloning, as they share more or less similar modus operandi. It involves copying of an image region and pasting within the same. The attack is mostly done to conceal something in the image while exploiting the fact that certain parameters of the image remain the same, thereby, making it difficult for the analyzer to distinguish if the image is tampered or not. An example of this attack is presented in Figure 24.1a, wherein a region showing a tree is copied and pasted side by side.

Image splicing or mosaicing which is the next common type of tampering, involves copy pasting of image regions from different images to create a new image. An example of this attack is presented in Figure 24.1b, wherein the imagery of a helicopter and a shark belonging to different images are combined together to give a feel that a shark is attacking a man climbing down on a ladder from the helicopter.

![](bbox=[0.2, 0.7, 0.48, 0.82])

![](bbox=[0.5, 0.7, 0.78, 0.82])

Figure 24.1 Examples of images which are subjected to a copy-move and splicing attacks. (a) Copy-move attack: The trees in the foreground of the image are clones of each other. (b) Image splicing attack: The imagery of the helicopter and the shark belong to different images, they have been combined together to give a feel that a shark is attacking a man climbing down a ladder from a helicopter.