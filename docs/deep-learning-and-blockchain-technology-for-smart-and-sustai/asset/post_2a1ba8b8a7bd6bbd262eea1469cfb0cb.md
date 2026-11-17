
gangue, imaging technology is integrated with image processing processes (such as enhancement and feature extraction) and a classifier that successfully addresses the drawbacks of the current techniques (pollution, radiation, etc.). On the other hand, environmental factors like light and dust have a significant impact on ordinary image detection. We introduce an innovative approach to coal and gangue detection by leveraging multispectral imaging, a cutting-edge optical non-destructive testing technology that is less susceptible to illumination variations. Initially, we employed GS-SVM, GA-SVM, and PSO-SVM classifiers to evaluate the classification performance of various image feature extraction methods.

The results revealed that Local Binary Pattern (LBP) stands out as the most effective feature extraction technique. Subsequently, through a thorough examination of classification effects across different wavelengths, we identified the ninth wavelength, particularly at 773.776 nm, as optimal for achieving the greatest imaging contrast between gangue and coal. In the final phase, our proposed model underwent rigorous testing to assess its proficiency in accurately distinguishing between coal and gangue.

The potential of using NIRS by Lianget Zou [10] in conjunction with ML approaches to identify block gangue from coal was studied. We proposed a distinctive strategy for identifying outliers to enhance performance, especially in scenarios involving two or more outliers within the dataset. The aim is to mitigate the adverse impact of aberrant observations on the accuracy of classifiers. The results of the investigation suggest that the modified MD approach is very much effective compared to the traditional MD algorithm at reducing outliers. Furthermore, the output-layer weights for the broad structure were optimized using lasso regression. The proposed L-BL method outperformed the regular BL algorithm in terms of classification accuracy and testing time. The suggested method has a promising future despite not having been applied extensively in practical settings due to its high accuracy in differentiating between coal and gangue. It can improve coal-gangue classification performance and lessen the threats to human health and the environment that come with low-quality coal. Still, there's potential for development in terms of time management.

This paper investigates a fresh deep learning and feature extraction coal categorization model. This research proposes to integrate features extraction with Convolutional Neural Network (CNN) to tackle the classification issue with coal and to further increase the classification accuracy in light of the traits of spectral data, which include high dimensionality, strong correlation, and significant redundancy. The model’s construction and training parameters are enhanced and optimized using an upgraded classification method and an enhanced deep learning algorithm. Lastly, consider the findings in terms of the accuracy parameter and execution time.

## 10.3 Proposed Methodology

### 10.3.1 Convolutional Neural Network

A CNN is a type of feed-forward neural network that possesses an understanding of topological information within the input image. Its functionality involves utilizing a classifier to extract features from the raw image and subsequently classify them. CNNs exhibit insensitivity to distortions or basic geometric alterations such as translation, scaling, rotation, or squeezing. To achieve partial shift, scale, and distortion invariance, CNNs employ three architectural strategies: local receptive fields, shared weights, and spatial or temporal sub-sampling. Similar to the training process of a conventional neural network, CNNs utilize backpropagation for network education. The Convolutional layer specifically plays a crucial role in extracting local receptive fields from the underlying layer. Feature map, which are planes of neurons responsible for identifying a certain feature and retrieving various forms of data, makes up a Convolutional layer local data. A 5×5 convolution kernel connects 25 in a network and inputs the local receptive field from the preceding layer into a 5×5 area.

Neuron can extract fundamental visual elements like edges using local receptive fields. Neurons in different parts of the brain may use the same connection structure and weights to extract the same visual feature. The result is a feature map, which is a representation of collection of neurons. This is equivalent to using a tiny kernel to convolution the input image. CNN’s structure that we propose is as follows:

The CNN Model function:

```
INITCNNMODEL (, [n1-5]) INITCNNMODEL (, [n1-5])
INITCNNMODEL (,[tanh()], max(), tanh(),
softmax()]
layerActivation = [tanh(), max(), tanh(),
softmax()]; layerActivation = [tanh(), max(),
fully-connected, fully-connected];

layerType = [convolution, max-pooling,
fully-connected, fully-connected];
layerActivation = [tanh(), max(),
fully-connected, fully-connected]
return model;
end function;
```

```
neuron [ni+1];
layer.params = I model.addLayer(layer);
return model;
end function;
```

```
neuron [ni+1];
layer.inputSize = ni layer.neurons = new Layer();
layer.type = layerType[i];
layer.inputSize = ni layer.neurons = new Layer();
layer.type = layerType[i];
```

### 10.3.2 Training CNN Model

Training batches, learning rate, minimal error rate (ERRmin), and maximum number of iterations (ITERmax), batch size SIZEtach, batch training, and other parameters have been set to train the model. n2, n3, n4, k1, and k2 have been calculated by using the values of n1 and n5 (Figures 10.2 and 10.3).

![](img/96b9fa3db3bfeef3ca6e7362a69b2849_239_0.png)
Figure 10.2 Coal image, gray scale image, inverted image, and noise removed image.

![](img/96b9fa3db3bfeef3ca6e7362a69b2849_240_0.png)
Figure 10.3 Training accuracy and loss.

```
cnnModel = InitCNNModel(, [n1-5]);
iter = 0;
err = +inf;
while err >ERRmin and iterITERmax do err = 0;
for bach = 1 to BATCHEStrining do
[J(), J()]] = cnnModel.train (TrainingDatas,
TrainingLabels), (4) and (8) respectively;
cnnModel = InitCNNModel(, [n1-5]);
Using (7), update the CNN's parameters;
err = err + mean(J()); end for err = err/
BATCHEStrining;
iter++;
Using (7), update the CNN's parameters; err =
err + mean(J());
end for err = err/BATCHEStrining;
```

## 10.4 Results and Discussion

All types of coal are classified as minerals, constituting rocks with a substantial carbon content. Approximately 25% of the world's primary energy and 40% of its power have been harnessed from this fossilized coal. The classification of coal is contingent upon its carbon composition, with its grade determined by the quantity of carbon it contains. Distinct variations exist between low-grade and high-grade coal. Notably, high-grade coals produce less smoke, while low-grade coals emit more. The combustion of high-grade coal is more complete and yields significantly greater energy compared to low-grade coal. In Table 10.1, the energy densities and carbon content of coal are listed. Together with the moisture content prior to drying, it also lists the amount of volatile content after drying.

### Table 10.1 Coal Types

| Coal | Dry, Carbon Content (%) | Moisture Content before Drying (%) | Dry, Volatile Content (%) | Heat Content (MJ/kg) |
|---|---|---|---|---|
| Anthracite | 86–92 | 7–10 | 3–14 | 32–33 |
| Bituminous coal | 76–86 | 8–18 | 14–46 | 23–33 |
| Lignite | 65–70 | 35–55 | 53–63 | 17–18 |
| Peat | <60 | 75 | 63–69 | 15 |

### 10.4.1 Peat

Peat, characterized by its soft, crumbly, and dark-brown composition, consists of partially decomposed and deceased organic material. Serving as the initial stage in coal formation, peat undergoes transformation into lignite as pressure and temperature increase and sediment accumulates atop the partially decomposing organic elements. To complete its evolution into coal, peat necessitates burial at depths ranging from 4 to 10 km beneath the surface by sedimentary processes. Peat boasts the lowest carbon content, measuring below 60%, and the highest energy density, registering at 15 MJ/kg (Figure 10.4).

![](img/96b9fa3db3bfeef3ca6e7362a69b2849_241_0.png)
