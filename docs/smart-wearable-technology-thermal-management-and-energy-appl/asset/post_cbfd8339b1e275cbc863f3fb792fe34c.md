
Figure 1. A schematic of the proposed work.

## 2. Materials and Methods

### 2.1. Respiration Measurement System

### 2.1.1. Breathing Mechanism

Understanding the mechanism of breathing is essential for accurate respiratory measurement. Equally important is the selection of a sensor measurement method that effectively corresponds to this mechanism. Various methods exist for measuring respiration, including monitoring airflow through the nose, capturing respiratory sounds, and tracking abdominal movement. Among these, this study focuses on measuring abdominal movement. This approach was chosen because it is the most suitable for wearable sensor applications and can be easily implemented in daily life.

In this method, respiration is measured using capacitive values (C) derived from abdominal movement (Equation (1)). The principle of measurement is as follows: when inhaling, air enters the lungs, causing the lungs to expand. This expansion leads to the spreading of the ribcage and the subsequent expansion of the thorax and abdomen. Conversely, when exhaling, air exits the lungs, the ribcage contracts, and the abdomen compresses. This process results in variations in abdominal volume, which correspond to changes in the distance between electrodes in a capacitive sensing system. By analyzing these differences in capacitive values, respiration can be assessed.

The two sensors were placed on the front and back of the body near the xiphoid process, where the abdominal movements caused by breathing can be most effectively measured. When the abdomen expands, the distance between the electrodes (d) is denoted as $d_0$, and during contraction, it is $d_f$. The difference between these distances, $\Delta d$, is used to analyze respiration (Equation (2)). The measurement principle and the breathing mechanism are illustrated in Figure 2 [23].

$$C = \frac{\varepsilon A}{d}$$

$$\Delta d = d_f - d_0$$

Figure 2. Abdominal movement in response to breathing [23].

### 2.1.2. Fabrication of Wearable Sensors

The electrodes were designed to have a rectangular shape with dimensions of 100 mm in width and 50 mm in height. The connectors for measurement were circular, measuring 20 mm × 20 mm. The stitch connecting the sensors to the connector was made in a zigzag pattern with a total length of 335 mm. The placement of the sensors is shown in Figure 3a, where the distances relative to reference points can also be observed. The area density of the embroidery (line/mm) was set to 6 for the sensor electrodes and 4.5 for the connectors. As the connection line consists of stitch lines, it does not have an embroidery area density. Regarding the stitch pattern, the electrodes and connectors were designed with a running stitch for the top thread and a fill stitch for the bobbin thread, while the connection line used a zigzag stitch.

![](img/c1925febd7dde400183c23c14d668ef0_149_0.png)

Figure 3. (a) Wearable sensors in the shape of a finished garment [23]; (b) the effect of single-ply and triple-ply thread length on the resistance value.

The stitch length for the electrodes and connectors was set to a width of 2 mm and a height of 4 mm, whereas the connection line had a width of 5 mm and a height of 1 mm. Finally, the total amount of thread used was 9526 stitches for the electrodes and 606 stitches for the connectors. This information is provided only for embroidered area measurements. Detailed specifications of the sensors are provided in Table 1 [24].

Table 1. Specifications of the wearable sensors.

| Parameter | Electrodes | Connection Line | Connectors |
| :--- | :--- | :--- | :--- |
| Dimension (width × height) | 100 × 50 (mm²) | 335 (mm²) | 20 × 20 (mm²) |
| Density (line/mm) | 6 | - | 4.5 |
| Shape of stitch | Running, fill | Zigzag | Running, fill |
| Length of stitch (mm) | 2, 4 | 5/1 (width/height) | 2, 4 |
| Number of stitches | 9526 | - | 606 |

The electrodes of the sensors were directly embroidered onto fabric (87% polyester, 13% spandex) (Sunmfit, Seoul, Republic of Korea) using silver-coated thread (AMANN, Bönnigheim, Germany) and an embroidery machine (BROTHER, Bridgewater, NJ, USA). Silver-coated thread was used as the top thread, while 100% rayon embroidery thread was used as the bobbin thread. The top thread was placed on the inner side of the garment, which encounters the body, while the bobbin thread remained on the outer side. To protect the outer side, a polyurethane (PU) film was heat-bonded onto the surface.

As shown in Figure 3a [23], rectangular electrodes were directly embroidered onto the front and back of the garment near the xiphoid process. The electrode placement was chosen to align with the areas of the abdomen that exhibit the most significant volume changes during respiration. To prevent any obstruction to breathing during measurements, the connector was positioned at the bottom hem of the garment, allowing seamless connection to the measurement device. The connectors were symmetrically aligned on both the front and back of the garment. To connect the electrodes and the connectors, a zigzag stitch was used, creating a straight pathway from the rectangular electrodes to the circular connectors.

The silver-coated thread consists of 34 twisted nylon filaments. This thread is widely used in wearable applications due to its compatibility with embroidery [25] and sewing machines. It has also been evaluated as safe in cytotoxicity tests following the biological evaluation standard for medical devices (DIN EN ISO 10993-5) [26]. Therefore, it is suitable for placement on the inner side of garments where it comes into direct contact with the skin. In this regard, ply refers to the unit indicating the number of strands twisted together to form a thread. A single-ply thread consists of one twisted strand, while a triple-ply thread consists of three twisted strands. As shown in Figure 3b [27], the resistance of the thread decreases as the number of twists increases, demonstrating that the thread used in this study minimizes measurement errors caused by resistance.

### 2.2. Experimental Setup and Acquisition

The experiment was conducted to measure breathing under different intensity levels through cycling. The measurement process involved wearing a garment-based sensor and using an indoor cycling apparatus (XAMEN KANGTO FITNESS FOUPWENT CO, Xiamen, China). For precise measurements, an LCR meter (KEYSIGHT, Santa Rosa, CA, USA) and the Keysight Benchvue program (KEYSIGHT, Santa Rosa, CA, USA) were employed instead of simple devices.

The intensity levels were divided into four categories: resting state (no activity), low intensity, moderate intensity, and high intensity. Low intensity corresponded to an average speed of 15–20 km/h, moderate intensity to 20–30 km/h, and high intensity to 30–40 km/h. Each intensity level was measured for 5 min, followed by a 1 min rest period before proceeding to the next measurement. The schematic diagram of the measurement setup is shown in Figure 4a [23], and the actual measurement process is illustrated in Figure 4b. The temperature was measured at room temperature (18 °C to 20 °C), and the experiment was conducted at approximately 60% humidity.

![](img/c1925febd7dde400183c23c14d668ef0_150_0.png)

Figure 4. (a) Schematic of LCR meter [23]; (b) measurement of wearable sensors.

### 2.3. Signal Processing with Deep Learning

Signal processing was conducted using MATLAB R2023a. The data, representing the capacitive values of the sensor corresponding to respiration, were normalized to a range between –3 and 3 to enhance model generalization and improve training stability. Using the normalized data, classification results were analyzed with CNN and ResNet to determine the most suitable algorithm for the dataset used in this study. Figure 5 illustrates the hierarchical structures of the networks, where 5a represents the CNN architecture and 5b depicts the ResNet architecture.

![](img/c1925febd7dde400183c23c14d668ef0_151_0.png)

Figure 5. (a) CNN architecture; (b) ResNet architecture.

A CNN is an algorithm that processes multiple layers sequentially. The CNN used in this study consists of seven convolutional blocks, each containing convolution, normalization, ReLU, and dropout layers. After repeating these blocks seven times, the network concludes with a global pooling layer and a fully connected layer for final classification. Through the pooling layer, features can be directly extracted, and hierarchical learning makes it effective for capturing complex data. However, as mentioned in the introduction, issues such as neuron death and non-recovery occasionally occur during this process. To address these limitations, ResNet, which has a similar structure but overcomes such challenges, is one of the alternative algorithms.

The structure of ResNet consists of two residual blocks, each containing two sets of convolutional blocks. A distinguishing feature of ResNet is its ability to learn the
