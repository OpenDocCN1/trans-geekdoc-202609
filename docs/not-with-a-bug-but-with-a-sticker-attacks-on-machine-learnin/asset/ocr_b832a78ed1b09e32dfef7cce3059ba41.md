The generated adversarial noise works beyond the digital domain. Google researchers confused a deep learning system by printing an adversarial patch of a toaster and placing it on a table with a banana (see Figure 3-8). A picture of the banana with the adversarial patch was sufficient to confuse the deep learning system into thinking it was a picture of a toaster.

MIT researchers took it a step further. In lieu of stickers, they 3D printed a turtle with a specific texture. Humans would instantly recognize it as a turtle. It has a turtle shape and, for all intents and purposes, looks like a turtle. In 2017, Google’s AI system quite confidently misrecognized the turtle as a rifle. Imagine the consequences if the reverse played out where an adversary 3D prints guns that are misrecognized as something benign.

![](bbox=[0.12, 0.45, 0.88, 0.75])

Figure 3.8 Adversarial noise can be printed on a physical patch to confuse AI systems. Courtesy of Tom B. Brown and Dandelion Mané

Thus far, we have assumed the attacker knows everything about the ML model—its parameters, inputs, and outputs needed to attack it. Indeed, many ML models are built upon open-source software, with their internal parameters published for academic transparency