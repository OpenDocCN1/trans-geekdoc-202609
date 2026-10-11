
![](images/bk978-0-7503-6244-3ch7uf20a_pr.gif)

![](images/bk978-0-7503-6244-3ch7uf20b_pr.gif)

### References

Everingham M, Gool L V, Williams C, Winn J and Zisserman A 2012 The PASCAL visual object classes challenge 2012 (VOC2012) results [http://www.pascal-network.org/challenges/VOC/voc2012/workshop/index.html](http://www.pascal-network.org/challenges/VOC/voc2012/workshop/index.html)

Girshick R 2015 Fast R-CNN *Proc. of the IEEE Int. Conf. on Computer Vision* pp 1440–8

Girshick R, Donahue J, Darrell T and Malik J 2014 Rich feature hierarchies for accurate object detection and semantic segmentation *Proc. of the IEEE Conf. on Computer Vision and Pattern Recognition* pp 580–7

Ioffe S and Szegedy C 2015 Batch normalization: accelerating deep network training by reducing internal covariate shift *Int. Conf. on Machine Learning* (PMLR) pp 448–56

Liu W, Anguelov D, Erhan D, Szegedy C, Reed S, Fu C-Y and Berg A C 2016 Ssd: Single shot multibox detector *European Conf. on Computer Vision* (Berlin: Springer) pp 21–37

Redmon J, Divvala S, Girshick R and Farhadi A 2016 You only look once: unified, real-time object detection *Proc. of the IEEE Conf. on Computer Vision and Pattern Recognition* pp 779–88

Redmon J and Farhadi A 2018 Yolov3: an incremental improvement *arXiv preprint* arXiv:[1804.02767](http://arxiv.org/abs/1804.02767)

Ren S, He K, Girshick R and Sun J 2015 Faster R-CNN: towards real-time object detection with region proposal networks *Adv. Neural Inform. Process. Syst.* [**28** 91–9](http://dx.doi.org/10.5555/2969239.2969250)

Roboflow, 2001. Chess Pieces Dataset [https://public.roboflow.com/object-detection/chess-full](https://public.roboflow.com/object-detection/chess-full)

Wang C-Y, Bochkovskiy A and Liao H-Y M 2022 YOLOv7: trainable bag-of-freebies sets new state-of-the-art for real-time object detectors *arXiv preprint* arXiv:[2207.02696](http://arxiv.org/abs/2207.02696)

* * *

# IOP Publishing

# Mastering Computer Vision with PyTorch and Machine Learning

# Caide Xiao

* * *

# Chapter 8

## YOLOv7, YOLOv8, YOLOv9 and YOLO-World

The subjects covered in this chapter are `YOLOv7` and `YOLOv8`. Because `YOLOv8` is easy to install and very fast, readers can just focus on `YOLOv8`. For a project of reading digits on images in a custom dataset `MNIST4yolo` constructed in this chapter, the model training time with `YOLOv8`, `YOLOv7` and `YOLO-NAS` is 0.5, 12 and 4.0 h respectively. Pre-trained `YOLOv8` models are used for object detection, image segmentation, image classification, human pose estimation, object tracking and counting.

After Wang *et al* [2022](#Chapter_8.xhtml#bk978-0-7503-6244-3ch8bib2) published their `YOLOv7` paper in July of 2023, we have faster and more accurate tools for real-time object detection. We can implement them without writing codes because `YOLOv7` source codes can be downloaded and cloned from WongKinYiu's GitHub website to our computers. Kin-Yiu Wong is the first author of the `YOLOv7` paper. It is easy to set an environment in VS Code with Python v3.9 by installing libraries and modules listed in a text file named `requirements.txt` from the website. Running the code in a VS Code cell: `!python detect.py --conf 0.4 --nosave --view-img --source 0`, you will see yourself on your computer's screen with a bounding box. Holding a cellphone in front of your camera, you will see two bounding boxes on your screen. If you wanting to save the object detection video to a file, just delete the `--nosave` option from the code. When you want to terminate the video recording of your camera, just press the `q` key on your keyboard. Replacing number 0 after the source by a video file name with its absolute path, such as `d:/traffic.mp4`, you will see cars with bounding boxes while you are playing the video file downloaded from YouTube. Of course, you can record the video with bounding boxes. On my laptop, `YOLOv7` finishes these jobs about 10 times faster than `YOLOv3`. Changing the source to a single image file name or a batch of image files with an absolute path, such as `d:/*.jpg`, you will see objects with bounding boxes on your images. There is a small issue for the image object detection. Images with bounding boxes disappear on your screen too soon. Since the `YOLOv7` codes were written in PyTorch, we can open the `detect.py` file in our VS Code editor. By replacing the waiting time of 1 millisecond in the `waitKey()` with 3000 millisecond on line 138 of the file, you would be able to watch those images comfortably. You need to changed the waiting time in `waitKey()` back to 1 millisecond for video, otherwise, your video playing speed will be very slow.

### 8.1 YOLOv7 for object detection for a custom dataset: MNIST4yolo

It is no surprise that we get very good object detection results with `YOLOv7` applied to many well-known datasets. We also need `YOLOv7` models to have the same ability to give us excellent results for custom datasets. Although Hugging Face, Roboflow and Kaggle provide many free public computer vision datasets, I would like to create and use my own dataset: `MNIST4yolo`. The resolution of each black and white image in the `MNIST4yolo` dataset is 448 × 448. The codes in Cells 01–04 of project [8.1](#Chapter_8.xhtml#bk978-0-7503-6244-3ch8ueqn1) can generate samples based on MNIST images for `YOLOv7`. As usual, Cell 01 is used to import libraries and set hyperparameters for the project. On the last line of Cell 01, A string named `xml_path` is just a folder name to save files of synthesized images and their plain text files for bounding boxes. Codes in Cell 02 should be familiar to us. From them, we get a MNIST train dataloader and a MNIST test dataloader.

Each batch of a MNIST dataloader has 256 MNIST images which are randomly picked out from a MNIST dataloader. In a 16 × 16 array, a total of 256 MNIST images are used to synthesize a bigger image with a resolution of 448 × 448 for the `MNIST4yolov7` dataset. Then using a for-loop starting from line 06 in Cell 03, we mask around 245/256 MNIST images, and only about 10 digits are visible on a synthesized image in the new dataset. The location and the label of each visible MNIST digit are recorded for bounding box information: `[label, x_c, y_c, w, h]`. The image width and height of each MNIST image are the same: 28/448. A for-loop in Cell 05 calls the above functions to save 560 bigger images for a training dataset and 80 bigger images for a test dataset respectively. Of course, each image has a text file about bounding boxes. It is not necessary for us to encode those bigger images with their bounding boxes to construct datasets, because a pre-trained `YOLOv7` model will take care of this work. Codes in Cells 01–05 should work in Python v3.6. Otherwise, each synthesized image would have a white border around it.

![](images/bk978-0-7503-6244-3ch8uf1_pr.gif)

![](images/bk978-0-7503-6244-3ch8uf2_pr.gif)

I created two sub-folders in a folder named `MNIST4yolov7`, one is named `train` and the other is named `test`. Each of them has two sub-folders: `images` and `labels`. The synthesized images and their text files generated in Cell 05 (in the `xml_path` folder) were moved to `MNIST4yolov7`'s sub-folders respectively. The `MNIST4yolov7` folder are then moved to a `YOLOv7` folder cloned from WongKinYiu's GitHub website. Copy a `data.yaml` file in the `YOLOv7` folder and paste it to the `train` folder of the `MNIST4yolov7` folder. The file can be edited by MS Notepad or the VS Code with the following information.

*   `train`: `C:/Users/xiaoc/Python/Exercises/yolov7/MNIST4yolov7/train/images`
*   `val`: `C:/Users/xiaoc/Python/Exercises/yolov7/MNIST4yolov7/test/images`
*   `nc`: `10`
*   `names`: `['0', '1', '2', '3', '4', '5', '6', '7', '8', '9']`
