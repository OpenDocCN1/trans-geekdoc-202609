# ## 9.3.2 ALGORITHM

+   1. Creation of table of natural objects in the image.
+   2. Detecting natural objects in an image.
+   3. Once the objects are detected the table is prepared.
+   4. The subsequent stage is to calculate HPP which is height per pixel.
+      Its unit is cm/pix. This can be calculated by applying = \(\frac{Real Height}{No. of Pixels}\)
+   5. \(k\) is calculated by applying the formula \(k = \frac{HPP}{depth}\).
+   6. Then \(Real Height = k * Depth * Pixel Height\) is calculated which
+      is Predicted Height.

# ## 9.3.3 STEPS

+   1. **Preparing the list of natural objects:** The images were perused
+      and the natural objects were noted. After that, the standard height
+      of these objects was appropriated from reliable web sources like
+      websites of construction companies, Wikipedia, car manufacturing
+      websites. <sup>20,23-25</sup> For trees, the average height was taken from
+      research paper.<sup>21</sup> Then the list was processed along with the mean
+      height of the objects.

| Sr no. | Natural objects | Mean height (cm) |
|---|---|---|
| 01 | Train | 402 |
| 02 | Car | 170 |
| 03 | Person | 172 |
| 04 | Traffic signal | 210 |
| 05 | Truck | 280 |
| 06 | Wheel | 83 |

_The mean height is taken in cm._

+   2. **Detecting natural objects in an image:** Amazon Rekognition
+      tool is brought in usage to detect objects in the KITTI images. It is
+      provided by AWS.