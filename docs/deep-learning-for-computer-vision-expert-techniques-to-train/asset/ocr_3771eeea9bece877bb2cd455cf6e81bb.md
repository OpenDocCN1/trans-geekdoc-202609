# Algorithm for VDM

The algorithm discussed here is proposed by Lu et al (https://research.fb.com/wp-content/uploads/2017/11/camera_ready_nips2017.pdf). Lu et al proposed a GAN-based VDM. The generator generates answers and the discriminator counts those answers. The following is a schematic representation of the process:

![](bbox=[0.149, 0.252, 0.85, 0.517])

The history of chat, the current question and image are fed as an input to the generator. Next, we will see how the generator works.