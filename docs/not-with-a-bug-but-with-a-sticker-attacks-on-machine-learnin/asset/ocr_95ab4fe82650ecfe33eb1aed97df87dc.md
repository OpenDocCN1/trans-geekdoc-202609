![](bbox=[0.364, 0.101, 0.663, 0.215])

**Figure 2-11**  Simply cropping and rotating the image causes the AI system to misrecognize images. Courtesy of Logan Engstrom, Brandon Tran, and Dimitris Tsipras

*Why should I care?* you ask.

Take AI for medicine. In 2018, Scott Gottlieb, then FDA commissioner, wrote that AI “holds enormous promise for the future of medicine” when approving one of the early trials of AI in medical diagnosis. But that promise may be in peril if ML systems’ brittle nature leaves them susceptible to attack.

Researchers from Harvard and MIT showed that the mere act of rotating an image of a lesion can cause the AI system to change the diagnosis—very confidently. Not only can it lead to a missed cancer diagnosis, rotating the image can also flip the diagnosis from benign to malignant (see Figure 2-12). Why would anyone do that? Insurance fraud. Imagine a dermatologist holding the camera at a weird angle to take pictures to bilk the insurance company. It brings new meaning to the phrase, “The diagnosis is in the doctor’s hands.”

![](bbox=[0.155, 0.64, 0.753, 0.708])

**Figure 2-12**  All it takes to attack a state-of-the-art AI healthcare algorithm is to rotate the image. Courtesy of Samuel G. Finlayson

The core of the problem is that machine learning systems use shortcuts to learn. They latch onto backgrounds, clutch to color, turn to texture—and are simply conditioned on cues.