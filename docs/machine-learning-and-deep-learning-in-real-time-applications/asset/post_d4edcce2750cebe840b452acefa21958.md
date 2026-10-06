
# Text Separation From Document Images

Oliveira, S. A., Seguin, B., & Kaplan, F. (2018) addressed the issue of extracting text, baseline, layout and photographs in the document image. They proposed a CNN based model for predicting the output after segmentation.

Chen, K., Seuret, M., Liwicki, M., Hennebet, J., & Ingold, R. (2015) used an unsupervised approach for feature learning in page segmentation of handwritten color document images. Page segmentation is considered as the pixel labeling problem, i., semantic segmentation that labels each pixel of the input image as such. Chen, K. et al. used a convolutional autoencoder that learns the features automatically. These features are then used to train SVM to get high-quality results.

Belabiod, A., & Belaid, A. (2018) suggested that extracting lines and words is the most important step before any recognition task. The proposed segmentation of Arabic document images using the deep learning approach. The line is segmented using the RU-net structure, and further, the words are segmented by BLSTM when applied on the segment image. Belabiod, A., & Belaid, A. (2018) tested their results on the KHATT Arabic database. The deep learning model was able to achieve 96.7% correct lines and 80.1% correct words.

# Summary

There has not much work done in OCR research of the Indic script, and even the accuracy level has not improved compared to the Latin script. Text separation is one of the pre-processing steps of an OCR system. Literature review shows that text separation from the document images can be classified as a top-down approach, bottom-up approach, hybrid technique, and deep learning methods. The first three approaches (i.e., top-down, bottom-up approach, and hybrid technology) under traditional methods for text separation. Literature shows that conventional methods require many steps for hand-coding features and then performing text and non-text segmentation.

On the other hand, deep learning is an end-to-end system. It does not require any pre-processing or hand-coded feature extraction and learns features automatically. Deep learning has different models for classification, segmentation, object detection, and various other applications. Deep learning gives state-of-the-art results on these applications compared to traditional methods. Text separation with deep learning methods improves accuracy. The literature survey shows that not much work has been done in the field of text separation using image processing and deep learning methods.

# METHODS FOR TEXT SEGMENTATION/EXTRACTION

# Dataset

The authors have created a dataset for the chapter from different Marathi books. Color images are scanned and cropped to the size of 256x256 in Microsoft Office 2010. There are 1300 images in total in the dataset. The whole dataset of 1300 images is used to train the deep learning models, while the traditional image processing methods require each image to be processed separately.

# Text Separation From Document Images

# TRADITIONAL IMAGE PROCESSING METHODS

This section discusses text separation from a Devanagari printed document image using one of the traditional image processing methods proposed by Priti P. Regge and Chanchal A. Chandrakant (2013) (using a top-down approach) on Devanagari document images.

# Pre-Processing

- 1. Key Features of the Implemented Method
  a. It mainly performs two tasks:
      i. To convert the input color image (document image) to a gray-scale image.
      ii. To convert the gray-scale image to a binary image.
  b. Use of Otsu's method for automatically setting the threshold value for binarization.
- 2. Description of the Method

The methodology used to pre-process the input Devanagari document image is given by Algorithm 1. The first step in the algorithm is the conversion of the input color image to a gray-scale image. The methodology converts three-channel input to a single channel (gray-scale image) with each pixel ranging in value from 0-255. If the input is not a color image and a gray-scale image, then it is directly given to the next step. The second step is to convert the gray-scale image obtained in the first step to a binary image. Each pixel in the binary image has a value of 0 or 1 by applying a specific threshold value. Algorithm 1 uses Otsu's method to get a binary image.

# Algorithm 1. Pre-Processing of Document Images

```
Input: Devanagari text document image.
Output: Pre-processed image.
Begin
1. Read the input image.
2. If the image is a color image, convert to a gray-scale image else go to the next step.
3. Binarize the gray-scale image using Otsu's method of thresholding.
End
```

# Results and Discussion

The input color image of size 256x256 is first converted to a gray-scale image. The image is further binarized to separate the foreground pixels in the image from the background pixels by selecting a suitable threshold. Instead of using a trial and error approach for threshold selection, a well-known method of binarization Otsu's method is implemented. Otsu selects the threshold automatically using an image histogram and foreground and background pixels by maximizing the discriminate measure. Thus, an optimum threshold is obtained. Figures 1(a) and (b) show the original document image with Devanagari text, and Figure 1(b) is the binary image for the given input. The binary image has sharp characters compared to the original text. Different images are used for the various results in the chapter.

# Text Separation From Document Images

Figure 1. (a) Original Image (b) Binary
img/c5bbc72cd5e4d392079eac36d68f5c309.png

# BLOCK EXTRACTION

# Key Features of the Implemented Method

- a. Extraction of pixels belonging to the same type.
- b. Grouping the pixels using Run-Length Encoding (RLE).
- c. Combination of horizontal and vertical smearing operations.

# Description of the Method

RLSA is used to extract blocks of text or non-text. The value of C helps link the region belonging to the same data. Thus, RLSA can tie together neighboring pixels separated by less than C. The algorithm applies vertical and horizontal smearing operations on the document. It creates two bitmaps; these combined with a logical operation result in the final segmentation. Sometimes additional smoothing with RLSA is applied to get more accurate results.

# Algorithm 2. Pre-processing of Document Images

Input: Pre-processed image.
Output: Block extracted image.
Begin
- 1. Initialize the pre-processed binary image and the threshold value for horizontal and vertical smearing operations as CHer and CVer to 4 and 2 respectively.
- 2. Compute horizontal smearing operation on the binarized image.
- 3. Start with the first row in the image and count the number of 0's and 1's in the first row sequentially
- 4. If (count number 0's in input < CHer = 4) change the 0's to 1's in the output else keep as the sequence unchanged
- 5. 1's in the input remain unchanged in the output.
- 6. Continue step 3 for every row in the image to create a horizontal bitmapped image.
- 7. Compute the vertical smearing operation on the pre-processed binary image with the same method defined in step 3 and continue the action for every column.
- 8. Create another bitmapped image using a vertical smearing operation.
- 9. Combine the bitmapped images obtained in step 4 and 6 by a logical AND operation to produce meaningful blocks.
- 10. Set the threshold value (CHers and CVers) to 5, for both, the additional horizontal and vertical smearing operations.
- 11. Compute horizontal and vertical smearing operations on the resulting image obtained by the logical AND operation.
- 12. Combine the two images to obtain the resultant block extracted image.
End
