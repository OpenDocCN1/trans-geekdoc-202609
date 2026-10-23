Large Scale Visual Recognition Challenge (ILSVRC) held each year. A dramatic moment in the meteoric rise of deep learning came when a convolutional network won this challenge for the first time and by a wide margin, bringing down the state-of-the-art top-5 error rate from 26.1 percent to 15.3 percent (Krizhevsky et al., 2012), meaning that the convolutional network produces a ranked list of possible categories for each image, and the correct category appeared in the first five entries of this list for all but 15.3 percent of the test examples. Since then, these competitions are consistently won by deep convolutional nets, and as of this writing, advances in deep learning have brought the latest top-5 error rate in this contest down to 3.6 percent, as shown in figure 1.12.

Deep learning has also had a dramatic impact on speech recognition. After improving throughout the 1990s, the error rates for speech recognition stagnated starting in about 2000. The introduction of deep learning (Dahl et al., 2010; Deng et al., 2010b; Seide et al., 2011; Hinton et al., 2012a) to speech recognition resulted in a sudden drop in error rates, with some error rates cut in half. We explore this history in more detail in section 12.3.

Deep networks have also had spectacular successes for pedestrian detection and image segmentation (Sermanet et al., 2013; Farabet et al., 2013; Couprie et al., 2013) and yielded superhuman performance in traffic sign classification (Ciresan et al., 2012).

At the same time that the scale and accuracy of deep networks have increased,

![](bbox=[0.2, 0.54, 0.7, 0.74])

Figure 1.12: Decreasing error rate over time. Since deep networks reached the scale necessary to compete in the ImageNet Large Scale Visual Recognition Challenge, they have consistently won the competition every year, yielding lower and lower error rates each time. Data from Russakovsky et al. (2014b) and He et al. (2015).