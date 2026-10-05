# Yoga pose estimation using PoseNet model 277

various levels of difficulty, making them crucial for comprehensive pose classification and feedback mechanisms within the model.

**Pose a: Mountain Pose (Tadasana):** A fundamental pose allows one to feel grounded and gain balance. Stand tall, feet together, pull in the core, and the body is neutrally aligned that one's weight is distributed.

**Pose b: Tree Pose (Vrikshasana):** For balance and stability, this posture requires sharp concentration as one remains poised at this point. Stand on one leg with the other foot resting on the inner thigh or calf.

**Pose c: Down Dog (Adho Mukha Svanasana):** Strengthens the arms, shoulders, and legs while stretching the spine. Stand on all fours, lift the hips, strengthening the legs to form an upside-down V

**Pose d: Warrior I (Virabhadrasana I):** Builds strength in the legs and opens the chest. Stand in a lunge, raise arms overhead, and square the hips frontward.

**Pose e: Warrior II (Virabhadrasana II):

Focuses on the strength and stability of this pose, with hands on either side and hips open. This pose is strong and channels all energy into the body.

**Pose f: Chair Pose (Urkatasana):** Strengthens thighs and glutes to create stamina and concentration. Raise knees with lowering the lower of the body at the back, as if sitting on a chair, by moving arms upwards.

# 13.4 RESULTS AND DISCUSSION

The proposed model is designed to detect body poses and train on these detected poses for accurate recognition. Utilizing ultralight depthwise separable convolutions, as seen in architectures MobileNet, the model efficiently handles body pose detection. This sequence of layers processes images through a variety of convolutions and normalizations in the detection of body poses, ultimately classifying the key points with a final dense layer.

Figure 13.3 represents the PoseNet model used for yoga pose estimation. The neural network begins with a series of layers that progressively decrease in size, for the initial extraction of features from the input image. As the layers narrow towards the output, these features are further refined to achieve accurate yoga pose estimation. The architecture's depth and complexity enable effective pose estimation even in challenging conditions.

The interactive system provides the user with a systematic way of learning six fundamental yoga poses—Mountain, Tree, Down Dog, Warrior I, Warrior II, and Chair. The user interface offers three modes—Learn, Practice, and About Yoga. In Learn Mode, users are guided through each