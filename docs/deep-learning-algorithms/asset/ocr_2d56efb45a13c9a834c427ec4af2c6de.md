experience of one task extension in the area of fish detection. Because most
of the embedded systems have been improved by fast growing computing
and sensing technologies, which makes them possible to incorporate more
and more complicated algorithms. In an AUV, after acquiring surrounding
information from sensors, how to perceive and analyze corresponding
information for better judgment is one of the challenges. The processing
procedure can mimic human being’s learning routines. An advanced system
with more computing power can facilitate deep learning feature, which
exploit many neural network algorithms to simulate human brains. In this
paper, a convolutional neural network (CNN) based fish detection method
was proposed. The training data set was collected from the Gulf of Mexico by
a digital camera. To fit into this unique need, three optimization approaches
were applied to the CNN: data augmentation, network simplification, and
training process speed up. Data augmentation transformation provided more
learning samples; the network was simplified to accommodate the artificial
neural network; the training process speed up is introduced to make the
training process more time efficient. Experimental results showed that the
proposed model is promising, and has the potential to be extended to other
underwear objects.

# INTRODUCTION

The ocean is full of mystery and the underwater exploration has always
been an exciting topic. Nowadays, robotics has been widely adopted into
our daily lives. The AUV is one type of robot, which is gaining more and
more attention [1, 2]. It must be equipped with a sophisticate onboard
computer, Inertial Measurement Unit (IMU), and other sensors to be able to
support a preprogrammed navigation system [1]. Authors have experience
design and function of an AUV [3, 4] for competitions. The AUV, as
shown in Figure 1, is featured with an i7-based industrial motherboard plus
an ARM microcontroller. Detail hardware layout and mechanical balancing
scheme are introduced in [3, 4]. It passed the qualification and became one
of the eleven finalists at the 2017 IEEE Singapore AUV Challenge [5]. This
competition was hosted in a swimming pool of clear water. The tasks did
not need a high-resolution camera, so the major processor was not chosen
to be of high performance. After this the AUV retired from the competition,
authors realized it was time to revise the system to conquer real life tasks.
As of now, most of the robot control platforms were shifting to Systems-
On-Chip (SOC) [6, 7]. To move forward and add more functionalities to