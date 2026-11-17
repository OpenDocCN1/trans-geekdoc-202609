# First-Order Motion Model

The main component that allows the avatar to imitate the user’s expressions and movements is called the first-order motion model. This model is trained on a dataset known as VoxCeleb2 which includes a collection of videos showcasing people speaking. The dataset offers a wealth of expressions, lip movements and head movements that are vital for creating realistic animations for the avatar.

The first-order motion model utilizes an encoder-decoder architecture. The encoder analyzes each video frame at the pixel level to extract representations of the features and movements. This latent representation captures the essence of the user’s expressions and movements allowing it to drive the avatar’s animation. The encoder comprises a convolutional neural network (CNN) that examines various elements of the image including facial landmarks, edges, and texture details. These features are then processed through connected layers to form a representation of the facial characteristics and movements. The decoder utilizes this latent representation to generate a video frame where the avatar replicates the user’s expressions and movements. It includes a CNN that creates an image based on the latent representation, which is then refined through upsampling and activation layers to produce the final video frame output.

The first-order motion model takes the user’s captured video frames as input and generates corresponding output frames with the avatar imitating the user’s movements. The model runs in real time, processing each input frame and generating the corresponding output frame with minimal latency.

# Enhancing Privacy

The development in the field of virtual communication is increasingly causing doubts concerning data protection and privacy issues while people are holding online meetings through video conferencing. However, this is an innovative project aimed at completely transforming privacy within the video conferencing process.

![](bbox=[0.23, 0.665, 0.76, 0.89])

Fig. 2 Privacy protection process