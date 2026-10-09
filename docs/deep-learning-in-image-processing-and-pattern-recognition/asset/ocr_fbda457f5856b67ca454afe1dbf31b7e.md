Article

# # A Coverage Hole Patching Algorithm for Heterogeneous Wireless Sensor Networks

**Xinmiao Lu 1,\*, Yuhao Wei 1, Qiong Wu 2, Cunfang Yang 1, Dongyuan Li 1, Liyu Zhang 1 and Ying Zhou 2**

+   1 School of Measurement-Control Technology and Communications Engineering, Harbin University of Science and Technology, Harbin 150080, China
2 Heilongjiang Network Space Research Center, Harbin 150090, China
\* Correspondence: lvxinmiao0611@hrbust.edu.cn; Tel.: +86-187-0462-8841

**Abstract:** The improvement of coverage is a critical issue in the coverage hole patching of sensors. Traditionally, VOPR and VORCP algorithms improve the coverage of the detection area by improving the original VOR algorithm, but coverage hole patching algorithms only target homogeneous networks. In the real world, however, the nodes in the wireless sensor network (WSN) are often heterogeneous, *i.e.*, the sensors have different sensing radii. The VORPH algorithm uses the VOR in a hybrid heterogeneous network and improves the original algorithm. The patched nodes are better utilized, and the detection range is enlarged. However, the utilization rate of the patched nodes is not optimized, making it impossible to patch the coverage holes to the maximum degree. In the environment of hybrid heterogeneous WSN, we propose a coverage hole patching algorithm with a priority mechanism. The algorithm determines the patching priority based on the size of the coverage holes, thereby improving network coverage, reducing node redundancy, and balancing resource allocation. The proposed algorithm was compared under the same environment by simulation and analysis. The results show that our algorithm is superior to the traditional coverage hole patching algorithms in coverage rate, and can reduce node redundancy.

**Keywords:** coverage hole; hybrid heterogeneous wireless sensor network (WSN); priority mechanism; patching

# ## 1. Introduction

Classic harmful gas detection mainly uses wired fixed devices and portable instruments and other detection methods with poor flexibility, low real-time, inaccurate leakage point positioning and other shortcomings. A wireless sensor network with low cost, high real-time, good cooperation and other characteristics to achieve remote detection of harmful gases is a new idea. However, the wireless sensor network is a resource-limited network. How to use limited sensor nodes to improve network coverage performance in the wireless sensor network in the application of harmful gas detection has technical difficulties.

The deployment of network nodes determines the coverage performance of the network [1]. In the natural environment, it is impossible to predetermine the specific situation of the WSN in many monitoring applications due to the inaccessibility of personnel and the complexity and randomness of the environment [2]. Therefore, the sensors are often deployed randomly, without pre-determining the location of nodes in the monitoring area. Random deployment may greatly reduce the WSN coverage of the monitoring area, leaving coverage holes [3]. What is worse, wireless sensor nodes have a limited lifetime, and when energy is exhausted, the node fails, creating a coverage hole. Wireless sensors may fail due to various reasons, such as high temperature, malicious attacks, harsh environments, overuse, and lack of energy. Coverage holes appear right after the failure [4].

Once generated, the coverage holes affect the service quality of the entire network, making the network unable to capture the data of the object accurately, or to realize the intended