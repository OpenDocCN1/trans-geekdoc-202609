| 32 | End of all speed and passing limits | 241 |
| 33 | Turn right ahead | 690 |
| 34 | Turn left ahead | 421 |
| 35 | Ahead only | 1201 |
| 36 | Go straight or right | 391 |
| 37 | Go straight or left | 211 |
| 38 | Keep right | 2071 |
| 39 | Keep left | 301 |
| 40 | Roundabout mandatory | 361 |
| 41 | End of no passing | 241 |
| 42 | End of no passing by vehicles over 3.5 metric tons | 241 |

Obviously, the signs, our regions of interest (ROI), are not centered within the images, whose sizes unfortunately vary. As a result, we need to separate the ROI from the image and standardize its size (resizing it to 32*32 as most researchers have done) before we can analyze and classify the data. We resort to the annotations provided along with the images. Each class folder contains an annotation file, for example, GT-00000.csv located at 00000. Each annotation file contains the following useful fields:

+   * Filename: The filename of the image
+   * ROI.X1: The x coordinate of the top-left corner of the ROI bounding box
+   * ROI.Y1: The y coordinate of the top-left corner of the ROI bounding box
+   * ROI.X2: The x coordinate of the bottom-right corner of the ROI bounding box
+   * ROI.Y2: The y coordinate of the bottom-right corner of the ROI bounding box