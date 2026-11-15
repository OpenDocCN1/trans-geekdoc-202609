
Thirdly, the motion estimation was proposed to generate across-frame consistent motions via proposing a triplet-based cycle consistency constraint. Extensive examinations conducted on KITTI, Cityscape, and Make3D datasets indicated the supremacy of this method.

According to Eigen et al., 15, the calculating depth is an indispensable constituent in realizing the 3D geometry depicted in a certain scene. Furthermore, the task is characteristically abstruse, with a great source of uncertainty from the unknown scale. In this paper, the authors have presented a novel technique that discusses this assignment by retaining two deep network stacks: making a coarse universal estimation established on the basis of entire image and additional that enhances this prediction locally.

According to Ponce et al., 16, fruit grading is a necessary post-harvest task in the olive industry. The combination is based on size, shape, and mass in the processing of high-quality table olives. The study presents a technique focused on assisting olive grading by computer vision techniques and feature modeling. The sum total of 3600 olive fruits from nine varieties was captured, stochastically distributing the individuals on the scene, using an improvised imaging chamber. Then, an image analysis algorithm was invented to divide olives and extract descriptive characteristics to evaluate their minor and major axes; and their mass. Determining the accurate performance for the individual division of the olive fruits, the algorithm was proven through 117 captures containing 11,606 fruits, producing only six fruit-segmentation mistakes.

According to Ege et al., 17, analysis comprises the estimation of images of food for precise food calorie estimation comprises three prevailing techniques with two new methods: (1) CalorieCam—it evaluates real food size based on a reference object, (2) Region Segmentation—it employs food calorie estimation, (3) AR DeepCalorieCamV2—it is about visual-inertial odometry built-in the iOS ARKit library, (4) DepthCalorieCam—it is based on camera (stereo) such as iPhone X/XS, and (5) RiceCalorieCam—it utilizes rice grains as reference objects. The last two approaches attained 10% or less estimation error, which is good for estimating food calorie.

## 9.3 METHODOLOGY

The proposed methodology adopted is described in Figure 9.1:

![](img/08e33f9814ed09d3c1bb11cd99f09e86_176_0.png)

FIGURE 9.3 Proposed methodology.

### 9.3.1 DATASET

The dataset has been obtained from Karlsruhe Institute of Technology. They have used autonomous driving platform known as Annieway for the development of unique and inspiring real-world computer vision benchmarks. Annieway is equipped with two high-resolution color and grayscale video cameras on its hood. The accurate and precise ground truth is supplied by a Velodyne laser scanner and a GPS localization system. All the datasets are captured by driving around the mid-size city of Karlsruhe, Germany.

![](img/08e33f9814ed09d3c1bb11cd99f09e86_176_1.png)

FIGURE 9.4 Autonomous driving platform for KITTI.

Source: Reprinted with permission from Ref. [19].

The dataset used for this work is Data Scene Flow 2015/Stereo 2015 which has been downloaded from KITTI Dataset and consists of 200 training scenes and 200 test scenes (four color images per scene, saved in lossless PNG format). The estimation server calculates the proportion of bad pixels intermediated over all ground truth pixels of all 200 test images. In the dataset, the images contain up to 15 cars and 30 pedestrians. Sample images from the dataset are as follows:

![](img/08e33f9814ed09d3c1bb11cd99f09e86_177_0.png)

![](img/08e33f9814ed09d3c1bb11cd99f09e86_177_1.png)

![](img/08e33f9814ed09d3c1bb11cd99f09e86_177_2.png)

### 9.3.2 ALGORITHM

- 1. Creation of table of natural objects in the image.
- 2. Detecting natural objects in an image.
- 3. Once the objects are detected the table is prepared.
- 4. The subsequent stage is to calculate HPP which is height per pixel. Its unit is cm/pix. This can be calculated by applying = \(\frac{Real Height}{No. of Pixels}\)
- 5. \(k\) is calculated by applying the formula \(k = \frac{HPP}{depth}\).
- 6. Then \(Real Height = k * Depth * Pixel Height\) is calculated which is Predicted Height.

### 9.3.3 STEPS

- 1. **Preparing the list of natural objects:** The images were perused and the natural objects were noted. After that, the standard height of these objects was appropriated from reliable web sources like websites of construction companies, Wikipedia, car manufacturing websites. <sup>20,23-25</sup> For trees, the average height was taken from research paper.<sup>21</sup> Then the list was processed along with the mean height of the objects.

| Sr no. | Natural objects | Mean height (cm) |
|---|---|---|
| 01 | Train | 402 |
| 02 | Car | 170 |
| 03 | Person | 172 |
| 04 | Traffic signal | 210 |
| 05 | Truck | 280 |
| 06 | Wheel | 83 |

*The mean height is taken in cm.*

- 2. **Detecting natural objects in an image:** Amazon Rekognition tool is brought in usage to detect objects in the KITTI images. It is provided by AWS.

![](img/08e33f9814ed09d3c1bb11cd99f09e86_179_0.png)

FIGURE 9.6 Object detection working on image from dataset.

From Figure 9.6, it is evident that it is detecting objects predominant in KITTI dataset image. The bounding box appears on some items for determining the image scale.

- 3. **Finding height of the object in image (in pix):** This step is carried out by the help of bounding box. When AWS recognition is used, the responses include numerical data pertaining to width, height, left, and top. 22,32

![](img/08e33f9814ed09d3c1bb11cd99f09e86_179_1.png)

FIGURE 9.7 Snapshot of the AWS developers guide explaining bounding box calculations. 22

Source: Adapted from Ref. [22]

It is to procure the needed information. The bounding box returns the quantity of image elements to express an object. Only height will be considered for further calculations as it indicates the ratio of overall image height which is the requirement of this stage.

```
{
 "Labels": [
 {
 "Name": "Car",
 "Confidence": 99.9004135131836,
 "Instances": [
 {
 "BoundingBox": {
 "Width":
 0.1577451378107071,
 "Height":
 0.2390778809785843,
 "Left":
 0.05361174792051315,
 "Top":
 0.5120320916175842
 },
 "Confidence":
 99.9004135131836
 },
 }
 ]
 },
 ]
}
```

FIGURE 9.8 The response after image (in Figure 9.5(i)) was uploaded in Amazon Rekognition Object Detection.

The real height of the object will remain same irrespective of its position in the illustration which is understandable. The formula which is applicable in this step is as follows:

- **HPP** = \(\frac{\text{Real Height}}{\text{No. of Pixels}}\) (9.1)

Real height is taken from the table created in Step 1.

- **HPP** \( \propto \frac{1}{\text{No. of Pixels}} \). This indicates that if HPP (height per pixel) is increased then no. of pixels will decrease and vice versa.

![](img/08e33f9814ed09d3c1bb11cd99f09e86_181_0.png)

FIGURE 9.9 Understanding the real height of the object.

Irrespective of the location of the object in the photograph, its real height or natural height remains same. The only modification is the pixel representation of the interested object. In the above Figure 9.7, it’s unmistakably noticeable that the closer the object is to the camera more number of pixels will be used to represent it, hence the height per pixel will decrease and vice versa.

**Relation between k, HPP, and depth:** Through step 4 and from eq 9.1, we can say that,

- *HPP* ∝ *depth* (9.2)
- *HPP* = *k* * *depth*; *k* is a constant which is to be calculated.
- $k = \frac{HPP}{depth}$ (9.3)

According to eq 9.2, height per pixel will increase with increase in depth and will decrease with a decrease in depth. This is done to evaluate k which is an important component of this whole research. 37 k remains constant throughout the image and is different for different images. Also, through availability of k, the calculation of the scale of unknown substances in the image has become easy.
