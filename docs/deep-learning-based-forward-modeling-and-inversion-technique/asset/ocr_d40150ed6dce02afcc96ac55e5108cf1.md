# Deep Learning-Based Forward Modeling and Inversion Techniques

where $h(t)$ is the impulse response corresponding to the system function. By $z$ transformation of the above equation, it can get

```
$T(z) = Q(z)H(z) \quad (3.12)$
```

where $H(z)$ is the system function. Although this approach quickly obtain the heat flux on the outer surface, it is usually confined to the one-dimensional case. For two-dimensional or three-dimensional problems, where there is a transfer function between each pair of measuring points and predicting points, the calculation of heat flux will be curvy. In addition, the linear assumption is based on the premise that the thermophysical parameters are constant with temperature, which is often not true in real materials, so the use of this method is limited. Compared with off-line methods, the on-line ones less memory or processing unions, hence are able to yield faster predictions. However, since the on-line approaches use partial temperature information, the accuracy can not put on par with the off-line algorithm based on full-time domain.

# 3.2.2 Artificial Neural Network

In recent years, the vigorous development of high-performance scientific computing has promoted the application of deep learning technology in computational physics. Compared with the forward problem, the advantage of deep learning on the inverse problem is more significant. With the help of the powerful parallel acceleration capability of GPU, a fully trained neural network can achieve thousands of times speed increase, realizing real-time heat flux reconstruction. At present, the existing work mainly focuses on simple artificial networks.

For instance, Ghadimi et al. [19] integrated the sequential function method with ANNs to solve the heat inversion of a brake disc (shown in Figure 3.2). Through a simple two-layer fully connected network, he realized the prediction of segmented heat flux. The input of the network is a vector of $L$ elements ($L=nr$), where $n$ and $r$ are the numbers of detectors and feature time steps, respectively. The output is the current heat flux. Here, the commercial software FLUENT 3D and SIM-PLE algorithm are employed to generate the network forward modeling data. It is worth noting that this method can only analyze the heat flux independent of the spatial location, so it has strong limitations.

The temporal-based heat flux was also predicted through temperature by Cortés et al. in [20]. The author adopted a fully connected network structure to extract the time characteristics of the unknown heat flux. It is worth noting that the heat flux in this problem is also even distributed in space. Considering that ANN usually contains only a few neurons, it is difficult to reconstruct complex heat flux. A common application is to use it as a tool to replace the forward modeling process to improve the efficiency of calculation.