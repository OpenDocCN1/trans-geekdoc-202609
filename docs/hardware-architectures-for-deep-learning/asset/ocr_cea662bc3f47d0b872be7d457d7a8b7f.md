# Chapter 6

# Hardware and software techniques for sparse deep neural networks

Ali Shafee$^1$, Liu Liu$^1$, Lei Wang$^1$, and Joseph Hassoun$^1$

# 6.1 Introduction

Over the past four decades, every generation of processors has delivered $2×$ performance boost, as predicted by Moore's law [1]. Ironically, the end of Moore's law occurred at almost the same time as computationally intensive deep learning algorithms were emerging. Deep neural networks (DNNs) offer state-of-the-art solutions for many applications, including computer vision, speech recognition, and natural language processing. However, this is just the tip of the iceberg. Deep learning is taking over many classic machine-learning applications and also creating new markets, such as autonomous vehicles, which will tremendously amplify the demand for ever powerful computation.

Hardware specialization was an effective response to meet the computational demands by devising efficient hardware architectures rather than relying on transistors' characteristics improvement. In the last decade, many startups have emerged to make specialized hardware accelerators for running DNNs efficiently [2]. The market also emerges these changes, e.g., the sale of Application Specific Integrated Circuits, ASICs, and Field Programmable Gate Arrays, FPGAs, in the global data centers for deep learning increased from almost 0% in 2016 to 25% in 2018 [3]. However, there is still a need to further accelerate the hardware for two main reasons. In the next decade, the rise of internet of things will significantly increase the number of smart devices and sensors on the edge and the service requirements in the cloud, and DNN algorithms are expected to be heavily employed in. Second, the main incentive for hardware buyers is the minimum of 2× improvement, in terms of performance and power efficiency, and if the hardware designers cannot deliver 2x performance improvements, the demand for new hardware may gradually diminish. Thus, there is a compelling need for computer architects to devise architectures that soon become the de facto standard of DNN hardware accelerator.

Another form of hardware optimization leverages the property of DNNs that most of operations for DNN are over-parameterized. In fact, a huge network is needed only

$^1$Samsung Semiconductor Inc., San Jose, CA, USA