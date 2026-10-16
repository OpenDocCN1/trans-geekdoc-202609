![](bbox=[0.13, 0.12, 0.88, 0.42])

Fig. 8.4. Illustration of the application framework of the DCNN in creating the salt probability volume.

# 2.2.1 Simplified Architecture of Residual U-net

The ResU-net architecture used in this study serves as the backbone of the DCNN architecture employed. The ResU-net capitalises on the power of deep residual learning to overcome encoder challenges by transferring information between layers, resulting in a deep neural network that effectively deals with degradation issues. Figure 8.5 depicts a simplified schematic illustration of the ResU-net, which utilises complete pre-activation deep residual units to train the model. Using bypass connections inside networks aids information propagation without degradation, enhancing the convolutional neural network’s architecture by reducing parameters while maintaining or improving the transfer learning function’s efficiency.

![](bbox=[0.1, 0.78, 0.9, 0.9])

Fig. 8.5. A simplified end-to-end U-network architecture for 3D salt mapping.