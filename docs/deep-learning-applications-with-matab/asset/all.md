   

**DEEP LEARNING. APPLICATIONS WITH MATAB **

**K. TAYLOR**

 

CONTENTS

[DEEP LEARNING INTRODUCTION.. 11](#part0000_split_002.html#_Toc482349224)

[1.1 DEEP LEARNING.. 11](#part0000_split_003.html#_Toc482349225)

[1.2 DEEP LEARNING WITH MATLAB: NEURAL NETWORK TOOLBOX.. 13](#part0000_split_004.html#_Toc482349226)

[1.3 DEEP LEARNING AND MATLAB CODE.. 15](#part0000_split_005.html#_Toc482349227)

[START DEEP LEARNING FASTER USING TRANSFER LEARNING.. 17](#part0000_split_006.html#_Toc482349228)

[2.1 TRANSFER LEARNING.. 17](#part0000_split_007.html#_Toc482349229)

[2.2 TRANSFER LEARNING USING ALEXNET.. 18](#part0000_split_008.html#_Toc482349230)

[2.2.1 Pretrained Convolutional Neural Networks. 18](#part0000_split_009.html#_Toc482349231)

[2.2.2 Function alexnet 19](#part0000_split_010.html#_Toc482349232)

[2.2.3 Classify an Image Using AlexNet 21](#part0000_split_011.html#_Toc482349233)

[2.2.4 Feature Extraction Using AlexNet 23](#part0000_split_012.html#_Toc482349234)

[2.2.5 Transfer Learning Using AlexNet 25](#part0000_split_013.html#_Toc482349235)

[2.3 Transfer Learning and Fine-Tuning of Convolutional Neural Networks  29](#part0000_split_014.html#_Toc482349236)

[2.3.1 Load Pretrained Network. 29](#part0000_split_015.html#_Toc482349237)

[2.3.2 Load Training Data. 30](#part0000_split_016.html#_Toc482349238)

[2.3.3 Transfer Layers to Target Network. 31](#part0000_split_017.html#_Toc482349239)

[2.4 Deep Dream Images Using AlexNet.. 33](#part0000_split_018.html#_Toc482349240)

[2.4.1 Load Pretrained Network. 34](#part0000_split_019.html#_Toc482349241)

[2.4.2 Generate Image. 34](#part0000_split_020.html#_Toc482349242)

[2.4.3 Generate More Detailed Images. 36](#part0000_split_021.html#_Toc482349243)

[DEEP LEARNING NETWORK FOR CLASSIFICATION AND REGRESSION.. 39](#part0000_split_022.html#_Toc482349244)

[3.1 Create Simple Deep Learning Network for Classification.. 39](#part0000_split_023.html#_Toc482349245)

[3.1.1 Load and Explore the Image Data. 39](#part0000_split_024.html#_Toc482349246)

[3.1.2 Specify Training and Test Sets. 41](#part0000_split_025.html#_Toc482349247)

[3.1.3 Define the Network Layers. 41](#part0000_split_026.html#_Toc482349248)

[3.1.4 Specify the Training Options. 42](#part0000_split_027.html#_Toc482349249)

[3.1.5 Train the Network Using Training Data. 42](#part0000_split_028.html#_Toc482349250)

[3.1.6 Classify the Images in the Test Data and Compute Accuracy. 43](#part0000_split_029.html#_Toc482349251)

[3.2 Train a Convolutional Neural Network for Regression.. 44](#part0000_split_030.html#_Toc482349252)

[3.2.1 Load Training Data. 44](#part0000_split_031.html#_Toc482349253)

[3.2.2 Create Network Layers. 45](#part0000_split_032.html#_Toc482349254)

[3.2.3 Train Network. 45](#part0000_split_033.html#_Toc482349255)

[3.2.4 Test Network. 47](#part0000_split_034.html#_Toc482349256)

[3.2.5 Correct Digit Rotations. 49](#part0000_split_035.html#_Toc482349257)

[DEEP LEARNING AND VISUALIZATION.. 51](#part0000_split_036.html#_Toc482349258)

[4.1 Visualize Activations of a Convolutional Neural Network.. 51](#part0000_split_037.html#_Toc482349259)

[4.1.1 Load Pretrained Network and Data. 51](#part0000_split_038.html#_Toc482349260)

[4.1.2 View Network Architecture. 52](#part0000_split_039.html#_Toc482349261)

[4.1.3 Show Activations of First Convolutional Layer. 53](#part0000_split_040.html#_Toc482349262)

[4.1.4 Investigate the Activations in Specific Channels. 54](#part0000_split_041.html#_Toc482349263)

[4.1.5 Find the Strongest Activation Channel 54](#part0000_split_042.html#_Toc482349264)

[4.1.6 Investigate a Deeper Layer. 55](#part0000_split_043.html#_Toc482349265)

[4.1.7 Test Whether a Channel Recognizes Eyes. 57](#part0000_split_044.html#_Toc482349266)

[4.2 Visualize Features of a Convolutional Neural Network.. 58](#part0000_split_045.html#_Toc482349267)

[4.2.1 Load Pretrained Network. 59](#part0000_split_046.html#_Toc482349268)

[4.2.2 Visualize Convolutional Layers. 59](#part0000_split_047.html#_Toc482349269)

[4.2.3 Visualize Fully Connected Layers. 63](#part0000_split_048.html#_Toc482349270)

[4.3 Train a Convolutional Neural Network Using Data in ImageDatastore   65](#part0000_split_049.html#_Toc482349271)

[4.3.1 Construct and Train a Convolutional Neural Network. 68](#part0000_split_050.html#_Toc482349272)

[4.4 Label Images for Classification Model Training.. 72](#part0000_split_051.html#_Toc482349273)

[4.4.1 Description. 72](#part0000_split_052.html#_Toc482349274)

[4.4.2 Open the Training Image Labeler. 73](#part0000_split_053.html#_Toc482349275)

[4.4.3 App Controls. 73](#part0000_split_054.html#_Toc482349276)

[4.5 Training Image Labeler.. 76](#part0000_split_055.html#_Toc482349277)

[4.5.1 Description. 76](#part0000_split_056.html#_Toc482349278)

[4.5.2 Open the Training Image Labeler App. 77](#part0000_split_057.html#_Toc482349279)

[DEEP LEARNING. OBJECT DETECTION AND RECOGNITION.. 79](#part0000_split_058.html#_Toc482349280)

[5.1 INTRODUCTION.. 79](#part0000_split_059.html#_Toc482349281)

[5.1.1 Deep Learning for Computer Vision. 80](#part0000_split_060.html#_Toc482349282)

[5.1.2 Deep Learning And Convulitional Neural Network. 81](#part0000_split_061.html#_Toc482349283)

[5.2 Create New Deep Network.. 82](#part0000_split_062.html#_Toc482349284)

[5.2.1 Specify Layers of Convolutional Neural Network. 82](#part0000_split_063.html#_Toc482349285)

[5.2.2 Image Input Layer. 83](#part0000_split_064.html#_Toc482349286)

[5.2.3 Convolutional Layer. 83](#part0000_split_065.html#_Toc482349287)

[5.2.4 ReLU Layer. 85](#part0000_split_066.html#_Toc482349288)

[5.2.5 Cross Channel Normalization (Local Response Normalization) Layer. 85](#part0000_split_067.html#_Toc482349289)

[5.2.6 Max- and Average-Pooling Layers. 85](#part0000_split_068.html#_Toc482349290)

[5.2.7 Dropout Layer. 86](#part0000_split_069.html#_Toc482349291)

[5.2.8 Fully Connected Layer. 86](#part0000_split_070.html#_Toc482349292)

[5.2.9 Softmax and Classification Layers. 87](#part0000_split_071.html#_Toc482349293)

[5.2.10 Regression Layer. 87](#part0000_split_072.html#_Toc482349294)

[5.2.11 Set Up Parameters and Train Convolutional Neural Network. 87](#part0000_split_073.html#_Toc482349295)

[5.2.12 Set Up Training Parameters Using trainingOptions. 87](#part0000_split_074.html#_Toc482349296)

[5.2.13 Set Up Parameters in Convolutional and Fully Connected Layers. 89](#part0000_split_075.html#_Toc482349297)

[5.2.14 Initialize Weights in Convolutional and Fully Connected Layers. 90](#part0000_split_076.html#_Toc482349298)

[5.2.15 Train Your Network. 90](#part0000_split_077.html#_Toc482349299)

[5.3 Resume Training from a Checkpoint Network.. 90](#part0000_split_078.html#_Toc482349300)

[5.3.1 Load Sample Data. 90](#part0000_split_079.html#_Toc482349301)

[5.3.2 Define Layers of Network. 91](#part0000_split_080.html#_Toc482349302)

[5.3.3 Specify Training Options with Checkpoint Path and Train Network. 92](#part0000_split_081.html#_Toc482349303)

[5.3.4 Load Checkpoint Network and Resume Training. 93](#part0000_split_082.html#_Toc482349304)

[5.4 Object Detection Using Deep Learning.. 94](#part0000_split_083.html#_Toc482349305)

[5.4.1 Overview.. 94](#part0000_split_084.html#_Toc482349306)

[5.4.2 Download CIFAR-10 Image Data. 95](#part0000_split_085.html#_Toc482349307)

[5.4.3 Create A Convolutional Neural Network (CNN). 96](#part0000_split_086.html#_Toc482349308)

[5.4.4 Train CNN Using CIFAR-10 Data. 100](#part0000_split_087.html#_Toc482349309)

[5.4.5 Validate CIFAR-10 Network Training. 101](#part0000_split_088.html#_Toc482349310)

[5.4.6 Load Training Data. 102](#part0000_split_089.html#_Toc482349311)

[5.4.7 Train R-CNN Stop Sign Detector. 103](#part0000_split_090.html#_Toc482349312)

[5.4.8 Test R-CNN Stop Sign Detector. 105](#part0000_split_091.html#_Toc482349313)

[5.4.9 Debugging Tips. 106](#part0000_split_092.html#_Toc482349314)

[5.5 Object Detection Using Faster R-CNN Deep Learning.. 108](#part0000_split_093.html#_Toc482349315)

[5.5.1 Overview.. 108](#part0000_split_094.html#_Toc482349316)

[5.5.2 Load Dataset 109](#part0000_split_095.html#_Toc482349317)

[5.5.3 Create a Convolutional Neural Network (CNN). 110](#part0000_split_096.html#_Toc482349318)

[5.5.4 Configure Training Options. 112](#part0000_split_097.html#_Toc482349319)

[5.5.5 Train Faster R-CNN.. 113](#part0000_split_098.html#_Toc482349320)

[5.5.6 Evaluate Detector Using Test Set 115](#part0000_split_099.html#_Toc482349321)

[5.6 Object Detectors. 116](#part0000_split_100.html#_Toc482349322)

[5.7 Train a Cascade Object Detector.. 117](#part0000_split_101.html#_Toc482349323)

[5.7.1 Why Train a Detector?. 117](#part0000_split_102.html#_Toc482349324)

[5.7.2 What Kinds of Objects Can You Detect?. 117](#part0000_split_103.html#_Toc482349325)

[5.7.3 How Does the Cascade Classifier Work?. 117](#part0000_split_104.html#_Toc482349326)

[5.7.4 Create a Cascade Classifier Using the  trainCascadeObjectDetector. 118](#part0000_split_105.html#_Toc482349327)

[5.7.5 Troubleshooting. 122](#part0000_split_106.html#_Toc482349328)

[5.7.6 Examples. 123](#part0000_split_107.html#_Toc482349329)

[5.7.7 Train Stop Sign Detector. 128](#part0000_split_108.html#_Toc482349330)

[5.8 Image Retrieval with Bag of Visual Words. 130](#part0000_split_109.html#_Toc482349331)

[5.8.1 Retrieval System Workflow.. 131](#part0000_split_110.html#_Toc482349332)

[5.8.2 Evaluate Image Retrieval 131](#part0000_split_111.html#_Toc482349333)

[5.9 Image Classification with Bag of Visual  Words. 132](#part0000_split_112.html#_Toc482349334)

[5.9.1 Step 1: Set Up Image Category Sets. 132](#part0000_split_113.html#_Toc482349335)

[5.9.2 Step 2: Create Bag of Features. 132](#part0000_split_114.html#_Toc482349336)

[5.9.3 Step 3: Train an Image Classifier With Bag of Visual Words. 133](#part0000_split_115.html#_Toc482349337)

[5.9.4 Step 4: Classify an Image or Image Set 134](#part0000_split_116.html#_Toc482349338)

[5.10 Digit Classification Using HOG Features. 134](#part0000_split_117.html#_Toc482349339)

[5.10.1 Digit Data Set 135](#part0000_split_118.html#_Toc482349340)

[5.10.2 Using HOG Features. 138](#part0000_split_119.html#_Toc482349341)

[5.10.3 Train a Digit Classifier. 139](#part0000_split_120.html#_Toc482349342)

[5.10.4 Evaluate the Digit Classifier. 140](#part0000_split_121.html#_Toc482349343)

[5.10.5 Summary. 141](#part0000_split_122.html#_Toc482349344)

[5.11 Image Category Classification Using Bag of Features. 141](#part0000_split_123.html#_Toc482349345)

[5.11.1 Download Caltech101 Image Set 141](#part0000_split_124.html#_Toc482349346)

[5.11.2 Load Image Sets. 142](#part0000_split_125.html#_Toc482349347)

[5.11.3 Prepare Training and Validation Image Sets. 143](#part0000_split_126.html#_Toc482349348)

[5.11.4 Create a Visual Vocabulary and Train an Image Category Classifier. 144](#part0000_split_127.html#_Toc482349349)

[5.11.5 Evaluate Classifier Performance. 146](#part0000_split_128.html#_Toc482349350)

[5.11.6 Try the Newly Trained Classifier on Test Images. 147](#part0000_split_129.html#_Toc482349351)

[5.12 Image Retrieval Using Customized Bag of Features. 148](#part0000_split_130.html#_Toc482349352)

[5.12.1 Introduction. 148](#part0000_split_131.html#_Toc482349353)

[5.12.2 Step 1 - Select the Image Features for Retrieval 149](#part0000_split_132.html#_Toc482349354)

[5.12.3 Step 2 - Create a Bag Of Features. 152](#part0000_split_133.html#_Toc482349355)

[5.12.4 Step 3 - Index the Images. 153](#part0000_split_134.html#_Toc482349356)

[5.12.5 Step 4 - Search for Similar Images. 153](#part0000_split_135.html#_Toc482349357)

[5.12.6 Conclusion. 156](#part0000_split_136.html#_Toc482349358)

[LOCAL FEATURES, PATTERN MATCHING AND OPTICAL CHARACTER RECOGNITION   157](#part0000_split_137.html#_Toc482349359)

[6.1 Local Feature Detection and Extraction.. 157](#part0000_split_138.html#_Toc482349360)

[6.1.1 What Are Local Features?. 157](#part0000_split_139.html#_Toc482349361)

[6.1.2 Benefits and Applications of Local Features. 158](#part0000_split_140.html#_Toc482349362)

[6.1.3 What Makes a Good Local Feature?. 158](#part0000_split_141.html#_Toc482349363)

[6.1.4 Feature Detection and Feature Extraction. 159](#part0000_split_142.html#_Toc482349364)

[6.1.5 Choose a Feature Detector and Descriptor. 159](#part0000_split_143.html#_Toc482349365)

[6.1.6 Use Local Features. 160](#part0000_split_144.html#_Toc482349366)

[6.1.7 Image Registration Using Multiple Features. 164](#part0000_split_145.html#_Toc482349367)

[6.2 Pattern Matching.. 168](#part0000_split_146.html#_Toc482349368)

[6.2.1 Introduction. 168](#part0000_split_147.html#_Toc482349369)

[6.2.2 Initialization. 168](#part0000_split_148.html#_Toc482349370)

[6.2.3 Video Processing Loop. 170](#part0000_split_149.html#_Toc482349371)

[6.2.4 Summary. 172](#part0000_split_150.html#_Toc482349372)

[6.3 Optical Character Recognition (OCR) 172](#part0000_split_151.html#_Toc482349373)

[6.3.1 Train Optical Character Recognition for Custom Fonts. 172](#part0000_split_152.html#_Toc482349374)

[6.3.2 Open the OCR Trainer App. 173](#part0000_split_153.html#_Toc482349375)

[6.3.3 Train OCR.. 173](#part0000_split_154.html#_Toc482349376)

[6.3.4 App Controls. 174](#part0000_split_155.html#_Toc482349377)

[6.3.5 Install OCR Language Data Files. 175](#part0000_split_156.html#_Toc482349378)

[6.4 Automatically Detect and Recognize Text in Natural Images. 175](#part0000_split_157.html#_Toc482349379)

[6.4.1 Step 1: Detect Candidate Text Regions Using MSER.. 176](#part0000_split_158.html#_Toc482349380)

[6.4.2 Step 2: Remove Non-Text Regions Based On Basic Geometric Properties. 177](#part0000_split_159.html#_Toc482349381)

[6.4.3 Step 3: Remove Non-Text Regions Based On Stroke Width Variation. 178](#part0000_split_160.html#_Toc482349382)

[6.4.4 Step 4: Merge Text Regions For Final Detection Result 181](#part0000_split_161.html#_Toc482349383)

[6.4.5 Step 5: Recognize Detected Text Using OCR.. 184](#part0000_split_162.html#_Toc482349384)

[6.5 Recognize Text Using Optical Character Recognition (OCR). 185](#part0000_split_163.html#_Toc482349385)

[6.5.1 Text Recognition Using the ocr Function. 185](#part0000_split_164.html#_Toc482349386)

[6.5.2 Information Returned By the ocr Function. 186](#part0000_split_165.html#_Toc482349387)

[6.5.3 Challenges Obtaining Accurate Results. 187](#part0000_split_166.html#_Toc482349388)

[6.5.4 Image Pre-processing Techniques To Improve Results. 189](#part0000_split_167.html#_Toc482349389)

[6.5.5 ROI-based Processing To Improve Results. 192](#part0000_split_168.html#_Toc482349390)

[6.5.6 Summary. 195](#part0000_split_169.html#_Toc482349391)

[6.6 Start Deep Learning Faster Using Transfer Learning.. 195](#part0000_split_170.html#_Toc482349392)

[6.7 Train Classifiers Using Features Extracted from Pretrained Networks  196](#part0000_split_171.html#_Toc482349393)

[6.8 Deep Learning with Big Data on GPUs and in Parallel. 196](#part0000_split_172.html#_Toc482349394)

[DEEP LEARNING IN THE CLOUD. PARALLEL COMPUTING.. 199](#part0000_split_173.html#_Toc482349395)

[7.1 DEEP LEARNING AND MULTIPLE GPUs. 199](#part0000_split_174.html#_Toc482349396)

[7.2 Transfer Learning.. 201](#part0000_split_175.html#_Toc482349397)

[7.3 Test the Network.. 202](#part0000_split_176.html#_Toc482349398)

[7.4 Training with Multiple GPUs. 202](#part0000_split_177.html#_Toc482349399)

[7.4.1 Increased GPU Memory. 202](#part0000_split_178.html#_Toc482349400)

[7.4.2 Reduced Training Time. 203](#part0000_split_179.html#_Toc482349401)

[7.5 Scale Up to Deep Learning in the Cloud.. 203](#part0000_split_180.html#_Toc482349402)

[7.5.1 Connecting to Amazon EC2 Using MathWorks Cloud Center. 204](#part0000_split_181.html#_Toc482349403)

[7.6 Training with a GPU Cluster.. 206](#part0000_split_182.html#_Toc482349404)

[7.7 Use Data in Amazon S3 Storage.. 206](#part0000_split_183.html#_Toc482349405)

[7.8 Results. 207](#part0000_split_184.html#_Toc482349406)

[7.9 Conclusions. 209](#part0000_split_185.html#_Toc482349407)

[7.10 Appendix – MATLAB Code.. 209](#part0000_split_186.html#_Toc482349408)

[CONVOLUTIONAL Neural NetworkS WITH MATLAB. FUNCTIONS. 213](#part0000_split_187.html#_Toc482349409)

[8.2.1 Create an image input layer: imageInputLayer. 214](#part0000_split_188.html#_Toc482349410)

[8.2.2 Create 2-D convolutional layer: convolution2dLayer. 216](#part0000_split_189.html#_Toc482349411)

[8.2.3 Create a Rectified Linear Unit (ReLU) layer: reluLayer. 219](#part0000_split_190.html#_Toc482349412)

[8.2.4 Create a local response normalization layer: crossChannelNormalizationLayer  220](#part0000_split_191.html#_Toc482349413)

[8.2.5 Create an average pooling layer: averagePooling2dLayer. 221](#part0000_split_192.html#_Toc482349414)

[8.2.6 Create max pooling layer: maxPooling2dLayer. 222](#part0000_split_193.html#_Toc482349415)

[8.2.7 Create fully connected layer: fullyConnectedLayer. 223](#part0000_split_194.html#_Toc482349416)

[8.2.8 Create a dropout layer: dropoutLayer. 224](#part0000_split_195.html#_Toc482349417)

[8.2.9 Create a softmax layer softmaxLayer. 225](#part0000_split_196.html#_Toc482349418)

[8.2.10 Create a classification output layer: classificationLayer. 225](#part0000_split_197.html#_Toc482349419)

[8.3.1 Train network: trainNetwork. 226](#part0000_split_198.html#_Toc482349420)

[8.3.2 Options for training neural network. trainingOptions. 232](#part0000_split_199.html#_Toc482349421)

[8.4 Extract Features and Predict Outcomes. FUNCTIONS. 233](#part0000_split_200.html#_Toc482349422)

[8.4.1 Compute network layer activations: activations. 233](#part0000_split_201.html#_Toc482349423)

[8.4.2 Predict responses using a trained network: predict 236](#part0000_split_202.html#_Toc482349424)

[8.4.3 Classify data using a trained network: classify. 239](#part0000_split_203.html#_Toc482349425)

[CONVOLUTIONAL Neural NetworkS WITH MATLAB. CLASSES. 243](#part0000_split_204.html#_Toc482349426)

[9.2.1 Network layer: layer. 243](#part0000_split_205.html#_Toc482349427)

[9.3.1 Series network class: SeriesNetwork. 251](#part0000_split_206.html#_Toc482349428)

[9.3.2 Training options for stochastic gradient descent with momentum. TrainingOptionsSGDM    253](#part0000_split_207.html#_Toc482349429)

[9.4.1 ImageInputLayer class. 255](#part0000_split_208.html#_Toc482349430)

[9.4.2 Convolution2DLayer class. 256](#part0000_split_209.html#_Toc482349431)

[9.4.3 ReLULayer class. 258](#part0000_split_210.html#_Toc482349432)

[9.4.4 CrossChannelNormalizationLayer class. 258](#part0000_split_211.html#_Toc482349433)

[9.4.5 AveragePooling2DLayer class. 260](#part0000_split_212.html#_Toc482349434)

[9.4.6 MaxPooling2DLayer class. 262](#part0000_split_213.html#_Toc482349435)

[9.4.7 FullyConnectedLayer class. 264](#part0000_split_214.html#_Toc482349436)

[9.4.8 DropoutLayer class. 265](#part0000_split_215.html#_Toc482349437)

[9.4.9 SoftmaxLayer class. 267](#part0000_split_216.html#_Toc482349438)

[9.4.10 ClassificationOutputLayer class. 267](#part0000_split_217.html#_Toc482349439)

[Image Category Classification Using Deep Learning.. 271](#part0000_split_218.html#_Toc482349440)

[10.1 Overview... 271](#part0000_split_219.html#_Toc482349441)

[10.2 Check System Requirements. 272](#part0000_split_220.html#_Toc482349442)

[10.3 Download Image Data.. 272](#part0000_split_221.html#_Toc482349443)

[10.4 Load Images. 272](#part0000_split_222.html#_Toc482349444)

[10.5 Download Pre-trained Convolutional Neural Network (CNN). 274](#part0000_split_223.html#_Toc482349445)

[10.5.1 Load Pre-trained AlexNet Network. 275](#part0000_split_224.html#_Toc482349446)

[10.6 Load Pre-trained CNN.. 277](#part0000_split_225.html#_Toc482349447)

[10.7 Pre-process Images For CNN.. 279](#part0000_split_226.html#_Toc482349448)

[10.8 Prepare Training and Test Image Sets. 279](#part0000_split_227.html#_Toc482349449)

[10.9 Extract Training Features Using CNN.. 280](#part0000_split_228.html#_Toc482349450)

[10.10 Train A Multiclass SVM Classifier Using CNN Features. 282](#part0000_split_229.html#_Toc482349451)

[10.11 Evaluate Classifier.. 282](#part0000_split_230.html#_Toc482349452)

[10.12 Try the Newly Trained Classifier on Test Images. 283](#part0000_split_231.html#_Toc482349453)

[10.13 References. 283](#part0000_split_232.html#_Toc482349454)

[Transfer Learning Using Convolutional Neural Networks AND PRETRAINED Convolutional Neural Networks. 285](#part0000_split_233.html#_Toc482349455)

[11.1 Transfer Learning Using Convolutional Neural Networks. 285](#part0000_split_234.html#_Toc482349456)

[11.2 Pretrained Convolutional Neural Network.. 291](#part0000_split_235.html#_Toc482349457)

[AUTOENCODERS. 295](#part0000_split_236.html#_Toc482349458)

[12.1 Autoencoder class. 295](#part0000_split_237.html#_Toc482349459)

[12.2 Autoencoder FUNCTIONS. 296](#part0000_split_238.html#_Toc482349460)

[12.2.1 Functions. 296](#part0000_split_239.html#_Toc482349461)

[12.2.2 trainAutoencoder. 296](#part0000_split_240.html#_Toc482349462)

[12.2.3 decode. 300](#part0000_split_241.html#_Toc482349463)

[12.2.4 encode. 301](#part0000_split_242.html#_Toc482349464)

[12.2.5 predict 302](#part0000_split_243.html#_Toc482349465)

[12.2.6 stack. 303](#part0000_split_244.html#_Toc482349466)

[12.2.7 generateFunction. 305](#part0000_split_245.html#_Toc482349467)

[12.2.8 generateSimulink. 306](#part0000_split_246.html#_Toc482349468)

[12.2.9 plotWeights. 307](#part0000_split_247.html#_Toc482349469)

[12.2.10 view.. 309](#part0000_split_248.html#_Toc482349470)

[12.3 Construct Deep Network Using Autoencoders. 310](#part0000_split_249.html#_Toc482349471)

[AUTOENCODERS. EXAMPLES. 313](#part0000_split_250.html#_Toc482349472)

[13.1 Train Stacked Autoencoders for Image Classification.. 313](#part0000_split_251.html#_Toc482349473)

[13.1.1 Data set 313](#part0000_split_252.html#_Toc482349474)

[13.1.2 Training the first autoencoder. 314](#part0000_split_253.html#_Toc482349475)

[13.1.3 Visualizing the weights of the first autoencoder. 324](#part0000_split_254.html#_Toc482349476)

[13.1.4 Training the second autoencoder. 325](#part0000_split_255.html#_Toc482349477)

[13.1.5 Training the final softmax layer. 325](#part0000_split_256.html#_Toc482349478)

[13.1.6 Forming a stacked neural network. 326](#part0000_split_257.html#_Toc482349479)

[13.1.7 Fine tuning the deep neural network. 328](#part0000_split_258.html#_Toc482349480)

[13.1.8 Summary. 329](#part0000_split_259.html#_Toc482349481)

[13.2 Transfer Learning Using Convolutional Neural Networks. 329](#part0000_split_260.html#_Toc482349482)

 

  

1Chapter 1

DEEP LEARNING INTRODUCTION 

# 1.1 DEEP LEARNING

#  

*Deep learning* is a branch of machine learning that teaches computers to do what comes naturally to humans: learn from experience. Machine learning algorithms use computational methods to "learn" information directly from data without relying on a predetermined equation as a model. Deep learning is especially suited for image recognition, which is important for solving problems such as facial recognition, motion detection, and many advanced driver assistance technologies such as autonomous driving, lane detection, pedestrian detection, and autonomous parking. 

 

Deep learning (also known as *deep structured learning*, *hierarchical learning* or *deep machine learning*) is a branch of [machine learning](https://en.wikipedia.org/wiki/Machine_learning "Machine learning") based on a set of [algorithms](https://en.wikipedia.org/wiki/Algorithm "Algorithm") that attempt to model high level abstractions in data. In a simple case, there might be two sets of neurons: ones that receive an input signal and ones that send an output signal. When the input layer receives an input it passes on a modified version of the input to the next layer. In a deep network, there are many layers between the input and output (and the layers are not made of neurons but it can help to think of it that way), allowing the algorithm to use multiple processing layers, composed of multiple linear and non-[linear transformations](https://en.wikipedia.org/wiki/Linear_transformation "Linear transformation").

 

Deep learning is part of a broader family of machine learning methods based on learning representations of data. An observation (e.g., an image) can be represented in many ways such as a vector of intensity values per pixel, or in a more abstract way as a set of edges, regions of particular shape, etc. Some representations are better than others at simplifying the learning task (e.g., face recognition or facial expression recognition). One of the promises of deep learning is replacing handcrafted  features with efficient algorithms for [unsupervised](https://en.wikipedia.org/wiki/Unsupervised_learning "Unsupervised learning") or semi-supervised feature learning  and hierarchical feature extraction. Research in this area attempts to make better representations and create models to learn these representations from large-scale unlabeled data. Some of the representations are inspired by advances in  neuroscience  and are loosely based on interpretation of information processing and communication patterns in a nervous system, such as neural coding which attempts to define a relationship between various stimuli and associated neuronal responses in the brain. 

 

Various deep learning architectures such as deep neural networks,  convolutional deep neural networks, deep belief networks and recurrent neural networks have been applied to fields like computer vision, automatic speech recognition, natural language processing, audio recognition and bioinformatics where they have been shown to produce state-of-the-art results on various tasks.

 

Deep learning has been characterized as a buzzword, or a rebranding of neural networks.

 

Deep learning is characterized as a class of [machine learning](https://en.wikipedia.org/wiki/Machine_learning "Machine learning") [algorithms](https://en.wikipedia.org/wiki/Algorithm "Algorithm") that:

·       Use a cascade of many layers of nonlinear processing units for feature extraction and transformation. Each successive layer uses the output from the previous layer as input. The algorithms may be supervised  or unsupervised and applications include pattern analysis (unsupervised) and classification (supervised).

·       Are based on the (unsupervised) learning of multiple levels of features or representations of the data. Higher level features are derived from lower level features to form a hierarchical representation.

·       Are part of the broader machine learning field of learning representations of data.

·       Learn multiple levels of representations that correspond to different levels of abstraction; the levels form a hierarchy of concepts.

 

These definitions have in common multiple layers of nonlinear processing units and the supervised or unsupervised learning of feature representations in each layer, with the layers forming a hierarchy from low-level to high-level features. The composition of a layer of nonlinear processing units used in a deep learning algorithm depends on the problem to be solved. Layers that have been used in deep learning include hidden layers of an artificial neural network and sets of complicated  propositional formulas. They may also include latent variables organized layer-wise in deep generative models such as the nodes in Deep Belief Networks and Deep Boltzmann Machines.

 

Deep learning algorithms are based on distributed representations. The underlying assumption behind distributed representations is that observed data are generated by the interactions of factors organized in layers. Deep learning adds the assumption that these layers of factors correspond to levels of abstraction or composition. Varying numbers of layers and layer sizes can be used to provide different amounts of abstraction. Deep learning exploits this idea of hierarchical explanatory factors where higher level, more abstract concepts are learned from the lower level ones. These architectures are often constructed with a greedy layer-by-layer method. Deep learning helps to disentangle these abstractions and pick out which features are useful for learning.

 

For supervised learning tasks, deep learning methods obviate feature engineering, by translating the data into compact intermediate representations akin to principal components, and derive layered structures which remove redundancy in representation. Many deep learning algorithms are applied to unsupervised learning tasks. This is an important benefit because unlabeled data are usually more abundant than labeled data. Examples of deep structures that can be trained in an unsupervised manner are neural history compressors and deep belief networks. 

 

Deep ñearning is used in various facets of science. The most common applications are the following:

 

·        Automatic speech recognition

·        Image recognition

·        Natural language processing

·        Drug discovery and toxicology

·        Customer relationship management

·        Recommendation systems

·        Biomedical informatics

 

# 1.2 DEEP LEARNING WITH MATLAB: NEURAL NETWORK TOOLBOX

 

MATLAB has the tool Neural Network Toolbox that provides algorithms, functions, and apps to create, train, visualize, and simulate neural networks. You can perform classification, regression, clustering, dimensionality reduction, time-series forecasting, and dynamic system modeling and control.

 

The toolbox includes convolutional neural network and autoencoder deep learning algorithms for image classification and feature learning tasks. To speed up training of large data sets, you can distribute computations and data across multicore processors, GPUs, and computer clusters using Parallel Computing Toolbox.

 

The more important features are the following:

 

·        Deep learning, including convolutional neural networks and autoencoders

·        Parallel computing and GPU support for accelerating training (with Parallel Computing Toolbox) 

·        Supervised learning algorithms, including multilayer, radial basis, learning vector quantization (LVQ), time-delay, nonlinear autoregressive (NARX), and recurrent neural network (RNN)

·        Unsupervised learning algorithms, including self-organizing maps and competitive layers

·        Apps for data-fitting, pattern recognition, and clustering

·        Preprocessing, postprocessing, and network visualization for improving training efficiency and assessing network performance

·        Simulink® blocks for building and evaluating neural networks and for control systems applications

 

Neural Network Toolbox provides simple MATLAB commands for creating and interconnecting the layers of a deep neural network. Examples and pretrained networks make it easy to use MATLAB for deep learning, even without knowledge of advanced computer vision algorithms or neural networks.

 
| **What do you want to do?** || **MATLAB Tools** |
| --- | --- |
| Perform transfer learning to fine-tune a network with your data || Start Deep Learning Faster Using Transfer Learning |
| Get pretrained networks to explore and use to classify images || Pretrained Convolutional Neural Networks |
| Create a new deep neural network to perform classification or regression || Create Simple Deep Learning Network for ClassificationTrain a Convolutional Neural Network for Regression |
| Train networks using data sets too large to fit in memory || Train a Convolutional Neural Network Using Data in ImageDatastore |
| Train a network for object detection || Deep Learning, Object Detection and Recognition (Computer Vision System Toolbox) |
| Label your image data automatically based on folder names, or interactively using an app || Train a Convolutional Neural Network Using Data in ImageDatastoreLabel Images for Classification Model Training (Computer Vision System Toolbox) |
| Visualize what features networks have learned || Deep Dream Images Using AlexNetVisualize Activations of a Convolutional Neural Network |
| Train on CPU, GPU, multiple GPUs, in parallel on your desktop or on clusters in the cloud || Deep Learning with Big Data on GPUs and in Parallel |

 

Deep learning uses neural networks to learn useful representations of features directly from data. Neural networks combine multiple nonlinear processing layers, using simple elements operating in parallel and inspired by biological nervous systems. Deep learning models can achieve state-of-the-art accuracy in object classification, sometimes exceeding human-level performance.

You train models using a large set of labeled data and neural network architectures that contain many layers, usually including some convolutional layers. Training these models is computationally intensive and you can usually accelerate training by using a high performance GPU. This diagram shows how convolutional neural networks combine layers that automatically learn features from many images in order to classify new images.

![Descripción: http://es.mathworks.com/help/nnet/ug/deep\_learning\_arch\_crop.png](images/00001.jpeg)

Many deep learning applications use image files, and sometimes millions of image files. To efficiently access many image files for deep learning, MATLAB provides the imageDatastore function. Use this function to:

·        Automatically read batches of images for faster processing in machine learning and computer vision applications

·        Import data from image collections that are too large to fit in memory

·        Label your image data automatically based on folder names

 

# 1.3 DEEP LEARNING AND MATLAB CODE

 

This example shows how to use deep learning to identify objects on a live webcam using only 10 lines of MATLAB code. Try the example to see how simple it is to get started with deep learning in MATLAB.

1.      Run these commands to get the downloads if needed, connect to the webcam, and get a pretrained neural network.

2.                                                                                                         camera = webcam; % Connect to the camera

net = alexnet;   % Load the neural network

If you need to install the webcam and alexnet add-ons, a message from each function appears with a link to help you download the free add-ons using Add-On Explorer. Alternatively, see Neural Network Toolbox Model *for AlexNet Network* and MATLAB Support Package for USB Webcams.

After you install Neural Network Toolbox Model *for AlexNet Network*, you can use it to classify images. AlexNet is a pretrained convolutional neural network (CNN) that has been trained on more than a million images and can classify images into 1000 object categories (for example, keyboard, mouse, coffee mug, pencil, and many animals).

3.      Run the following code to show and classify live images. Point the webcam at an object and the neural network reports what class of object it thinks the webcam is showing. It will keep classifying images until you press **Ctrl**+**C**. The code resizes the image for the network using [imresize](http://es.mathworks.com/help/images/ref/imresize.html).

while true

    im = snapshot(camera);       % Take a picture

    image(im);                   % Show the picture

    im = imresize(im,\[227 227\]); % Resize the picture for alexnet

    label = classify(net,im);    % Classify the picture

    title(char(label));          % Show the class label

    drawnow

end

In this example, the network correctly classifies a coffee mug. Experiment with objects in your surroundings to see how accurate the network is.

![Descripción: http://es.mathworks.com/help/nnet/ug/webcam\_coffeemug.png](images/00002.gif)

 

For next steps in deep learning, you can use the pretrained network for other tasks. Solve new classification problems on your image data with transfer learning or feature extraction.

 

 

  

2Chapter 2

START DEEP LEARNING FASTER USING TRANSFER LEARNING 

# 2.1 TRANSFER LEARNING

#  

Transfer learning is commonly used in deep learning applications. You can take a pretrained network and use it as a starting point to learn a new task. Fine-tuning a network with transfer learning is much faster and easier than training from scratch. You can quickly make the network learn a new task using a smaller number of training images. The advantage of transfer learning is that the pretrained network has already learned a rich set of features that can be applied to a wide range of other similar tasks.

For example, if you take a network trained on thousands or millions of images, you can retrain it for new object detection using only hundreds of images. You can effectively fine-tune a pretrained network with much smaller data sets than the original training data. Transfer learning might not be faster than training a new network if you have a very large dataset.

Transfer learning enables you to:

·        Transfer the learned features of a pretrained network to a new problem

·        Transfer learning is faster and easier than training a new network

·        Reduce training time and dataset size

·        Perform deep learning without needing to learn how to create a whole new network

 

 

# 2.2 TRANSFER LEARNING USING ALEXNET

 

## 2.2.1 Pretrained Convolutional Neural Networks

 

Fine-tuning a pretrained network with transfer learning is typically much faster and easier than training from scratch. You can use previously trained networks for the following purposes.

 
| **Purpose** || **Description** |
| --- | --- |
| Classification || Apply pretrained networks directly to classification problems. |
| Transfer Learning || Take layers from a network trained on a large data set and fine-tune on a new data set.. |
| Feature Extraction || Use a pretrained network as a feature extractor by using the layer activations as features. You can use these activations as features to train another classifier, such as a support vector machine (SVM). |

You can download and install pretrained networks to use for your problems. Use functions such as alexnet to get links to download pretrained networks from the Add-On Explorer.

Use the `alexnet` function to get a link to download a pretrained AlexNet model.

AlexNet has learned rich feature representations for a wide range of images. You can apply this rich feature learning to a wide range of image classification problems using transfer learning and feature extraction. The AlexNet model is trained on more than a million images and can classify images into 1000 object categories (such as keyboard, coffee mug, pencil, and many animals). The training images are a subset of the ImageNet database, which is used in ImageNet Large-Scale Visual Recognition Challenge (ILSVRC). AlexNet won ILSVRC 2012, achieving highest classification performance. The network has 25 layers. There are 8 layers with learnable weights: 5 convolutional layers, and 3 fully connected layers.

*Transfer learning* is commonly used in deep learning applications. You can take a pretrained network and use it as a starting point to learn a new task. Fine-tuning a network with transfer learning is much faster and easier than constructing and training a new network. You can quickly transfer learning to a new task using a smaller number of training images. The advantage of transfer learning is that the pretrained network has already learned a rich set of features. These features can be applied to a wide range of other similar tasks. For example, you can take a network trained on millions of images and retrain it for new object classification using only hundreds of images. If you have a very large data set, then transfer learning might not be faster.

*Feature extraction* is an easy way to use the power of pretrained networks without investing time and effort into training. Feature extraction can be the fastest way to use deep learning. You extract learned features from a pretrained network, and use those features to train a classifier, such as a support vector machine using `fitcsvm` (Statistics and Machine Learning Toolbox™). For example, if an SVM achieves >90% accuracy on your training and validation set, then fine-tuning might not be worth the effort to increase accuracy. If you perform fine-tuning on a small data set, you also risk over-fitting to the training data. If the SVM cannot achieve good enough accuracy for your application, then fine-tuning is worth the effort to seek higher accuracy. 

## 2.2.2 Function alexnet

**Syntax**

net = alexnet

**Description**

[net](http://es.mathworks.com/help/nnet/ref/alexnet.html#outputarg_net) = alexnet returns a pretrained AlexNet model. This model is trained on a subset of the ImageNet database, which is used in ImageNet Large-Scale Visual Recognition Challenge (ILSVRC). The model is trained on more than a million images and can classify images into 1000 object categories. For example, keyboard, mouse, pencil, and many animals. As a result, the model has learned rich feature representations for a wide range of images.

This function requires Neural Network Toolbox Model *for AlexNet Network* support package. If this support package is not installed, the function provides a download link.

**Examples:**

**Download AlexNet Support Package**

 

Download and install Neural Network Toolbox Model *for AlexNet Network* support package.

 

Type alexnet at the command line.

 

alexnet

If Neural Network Toolbox Model *for AlexNet Network* support package is not installed, then the function provides a link to the required support package in the Add-On Explorer. To install the support package, click the link, and then click **Install**. Check that the installation is successful by typing alexnet at the command line.

 

alexnet

ans = 

 

  SeriesNetwork with properties:

 

    Layers: \[25×1 nnet.cnn.layer.Layer\]

If the required support package is installed, then the function returns a SeriesNetwork object.

**Load Pretrained AlexNet Convolutional Neural Network**

 

Load a pretrained AlexNet convolutional neural network and examine the layers and classes.

Load the pretrained AlexNet network using alexnet. The output net is a SeriesNetwork object.

 

net = alexnet

net = 

 

  SeriesNetwork with properties:

 

    Layers: \[25×1 nnet.cnn.layer.Layer\]

 

Using the Layers property, view the network architecture. The network comprises of 25 layers. There are 8 layers with learnable weights: 5 convolutional layers, and 3 fully connected layers.

net.Layers

ans = 

 

  25x1 Layer array with layers:

 

1   'data'     Image Input                   227x227x3 images with 'zerocenter' normalization

2   'conv1'    Convolution                   96 11x11x3 convolutions with stride \[4  4\] and padding \[0  0\]

3   'relu1'    ReLU                          ReLU

4   'norm1'    Cross Channel Normalization   cross channel normalization with 5 channels per element

5   'pool1'    Max Pooling                   3x3 max pooling with stride \[2  2\] and padding \[0  0\]

6   'conv2'    Convolution                   256 5x5x48 convolutions with stride \[1  1\] and padding \[2  2\]

7   'relu2'    ReLU                          ReLU

8   'norm2'    Cross Channel Normalization   cross channel normalization with 5 channels per element

9   'pool2'    Max Pooling                   3x3 max pooling with stride \[2  2\] and padding \[0  0\]

10   'conv3'    Convolution                   384 3x3x256 convolutions with stride \[1  1\] and padding \[1  1\]

11   'relu3'    ReLU                          ReLU

12   'conv4'    Convolution                   384 3x3x192 convolutions with stride \[1  1\] and padding \[1  1\]

13   'relu4'    ReLU                          ReLU

14   'conv5'    Convolution                   256 3x3x192 convolutions with stride \[1  1\] and padding \[1  1\]

15   'relu5'    ReLU                          ReLU

16   'pool5'    Max Pooling                   3x3 max pooling with stride \[2  2\] and padding \[0  0\]

17   'fc6'      Fully Connected               4096 fully connected layer

18   'relu6'    ReLU                          ReLU

19   'drop6'    Dropout                       50% dropout

20   'fc7'      Fully Connected               4096 fully connected layer

21   'relu7'    ReLU                          ReLU

22   'drop7'    Dropout                       50% dropout

23   'fc8'      Fully Connected               1000 fully connected layer

24   'prob'     Softmax                       softmax

25   'output'   Classification Output         crossentropyex with 'tench', 'goldfish', and 998 other classes

You can view the names of the classes learned by the network by viewing the ClassNames property of the classification output layer (the final layer). View the first 10 classes by selecting the first 10 elements.

net.Layers(end).ClassNames(1:10)

ans =

 

  1×10 cell array

 

  Columns 1 through 4

 

    'tench'    'goldfish'    'great white shark'    'tiger shark'

 

  Columns 5 through 9

 

    'hammerhead'    'electric ray'    'stingray'    'cock'    'hen'

 

  Column 10

 

    'ostrich'

 

## 2.2.3 Classify an Image Using AlexNet

 

Read, resize, and classify an image using AlexNet. First, load a pretrained AlexNet model.

net = alexnet;

Read the image using imread.

I = imread('peppers.png');

figure

imshow(I)

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/ClassifyAnImageUsingAlexNetExample\_01.png](images/00003.jpeg)

The pretrained model requires the image size to be the same as the input size of the network. Determine the input size of the network using the InputSize property of the first layer of the network.

 

sz = net.Layers(1).InputSize

sz =

 

   227   227     3

 

Crop the image to the input size of the network. Alternatively, you can resize the image using imresize (Image Processing Toolbox™).

I = I(1:sz(1),1:sz(2),1:sz(3));

figure

imshow(I)

![](images/00004.jpeg)

Classify the image using classify.

label = classify(net,I)

label = 

 

  categorical

 

     bell pepper 

 

Show the image and classification result together.

figure

imshow(I)

title(char(label))

![](images/00005.jpeg)

 

## 2.2.4 Feature Extraction Using AlexNet

 

Extract learned features from a pretrained network, and use those features to train a classifier. Feature extraction is the easiest and fastest way use the representational power of pretrained deep networks. For example, you can train a support vector machine (SVM) using fitcecoc (Statistics and Machine Learning Toolbox™) on the extracted features.

Load a pretrained AlexNet network.

net = alexnet;

Load the sample images. merchImagesTrain and merchImagesTest are ImageDatastore objects.

\[merchImagesTrain,merchImagesTest\] = merchData;

In the sample data, there are 60 training images and 15 test images. Display 20 sample images.

figure

for i = 1:20

    subplot(4,5,i)

 

    I = readimage(merchImagesTrain,i);

    imshow(I)

    drawnow

end

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/FeatureExtractionUsingAlexNetExample\_01.png](images/00006.jpeg)

If the training images differ in size to the image input layer, then you must resize or crop the image data. The images in merchImages are the same size as the input size of AlexNet, so you do not need to resize or crop the new image data.

Get the feature representations of the training and test images. 

 

Use activations on the last fully connected layer ('fc7') with the image data.

 

layer = 'fc7';

trainingFeatures = activations(net,merchImagesTrain,layer);

testFeatures = activations(net,merchImagesTest,layer);

Extract the class labels from the training and test data.

trainingLabels = merchImagesTrain.Labels;

testLabels = merchImagesTest.Labels;

Fit a multiclass support vector machine (SVM) using fitcecoc (Statistics and Machine Learning Toolbox).

 

classifier = fitcecoc(trainingFeatures,trainingLabels);

Classify the test images using predict.

predictedLabels = predict(classifier,testFeatures);

Display four sample test images with their predicted labels.

idx = \[1 4 7 10\];

figure

for i = 1:numel(idx)

    subplot(2,2,i)

 

    I = readimage(merchImagesTest,idx(i));

    label = predictedLabels(idx(i));

 

    imshow(I)

    title(char(label))

    drawnow

end

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/FeatureExtractionUsingAlexNetExample\_02.png](images/00007.jpeg)

Calculate the classification accuracy.

accuracy = sum(predictedLabels==testLabels)/numel(predictedLabels)

accuracy =

 

    0.9333

 

This example SVM has high accuracy. If the accuracy is not high enough using feature extraction, the try transfer learning instead.

## 2.2.5 Transfer Learning Using AlexNet

 

Fine-tune a pretrained convolutional neural network to learn the features on a new collection of images.

Transfer learning is commonly used in deep learning applications. You can take a pretrained network and use it as a starting point to learn a new task. Fine-tuning a network with transfer learning is much faster and easier than training from scratch. You can quickly transfer learning to a new task using a smaller number of training images.

Load the sample images as ImageDatastore objects.

 

\[merchImagesTrain,merchImagesTest\] = merchData;

In the sample data, there are 60 training images and 15 test images. Display 20 sample images.

figure

for i = 1:20

    subplot(4,5,i)

 

    I = readimage(merchImagesTrain,i);

    imshow(I)

    drawnow

end

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/TransferLearningUsingAlexNetExample\_01.png](images/00008.jpeg)

Load a pretrained AlexNet network.

net = alexnet;

The last three layers of the pretrained network net are configured for 1000 classes. These three layers must be fine-tuned for the new classification problem. Extract all the layers except the last three from the pretrained network, net.

layersTransfer = net.Layers(1:end-3);

Transfer the layers to the new task by replacing the last three layers with a fully connected layer, a softmax layer, and a classification output layer. Specify the options of the new fully connected layer according to the new data. Set the fully connected layer to be of the same size as the number of classes in the new data. To speed up training, also increase 'WeightLearnRateFactor' and 'BiasLearnRateFactor' values in the fully connected layer.

Determine the number of classes from the training data.

numClasses = numel(categories(merchImagesTrain.Labels))

numClasses =

 

     5

 

Create the layer array by combining the transferred layers with the new layers.

layers = \[...

    layersTransfer

    fullyConnectedLayer(numClasses,'WeightLearnRateFactor',20,'BiasLearnRateFactor',20)

    softmaxLayer

    classificationLayer\];

If the training images differ in size from the image input layer, then you must resize or crop the image data. The images in merchImages are the same size as the input size of AlexNet, so you do not need to resize or crop the new image data.

Create the training options. For transfer learning, you want to keep the features from the early layers of the pretrained network (the transferred layer weights). Set 'InitialLearnRate' to a low value. This low initial learn rate slows down learning on the transferred layers. In the previous step, you set the learn rate factors for the fully connected layer higher to speed up learning on the new final layers. This combination results in fast learning only on the new layers, while keeping the other layers fixed. When performing transfer learning, you do not need to train for as many epochs. To speed up training, you can reduce the value of the 'MaxEpochs' name-value pair argument in the call to trainingOptions. To reduce memory usage, reduce 'MiniBatchSize'.

 

options = trainingOptions('sgdm',...

    'MiniBatchSize',5,...

    'MaxEpochs',10,...

    'InitialLearnRate',0.0001);

Fine-tune the network using trainNetwork on the new layer array.

netTransfer = trainNetwork(merchImagesTrain,layers,options);

Training on single GPU.

Initializing image normalization.

 

 

 

|=========================================================================================|

|     Epoch    |   Iteration  | Time Elapsed |  Mini-batch  |  Mini-batch  | Base Learning|

|              |              |  (seconds)   |     Loss     |   Accuracy   |     Rate     |

|=========================================================================================|

|            1 |            1 |         0.55 |       2.4120 |       20.00% |       0.0001 |

|            5 |           50 |        18.28 |       0.0002 |      100.00% |       0.0001 |

|            9 |          100 |        34.82 |      -0.0000 |      100.00% |       0.0001 |

|           10 |          120 |        41.36 |       0.0001 |      100.00% |       0.0001 |

|=========================================================================================|

Classify the test images using classify.

predictedLabels = classify(netTransfer,merchImagesTest);

Display four sample test images with their predicted labels.

idx = \[1 4 7 10\];

figure

for i = 1:numel(idx)

    subplot(2,2,i)

 

    I = readimage(merchImagesTest,idx(i));

    label = predictedLabels(idx(i));

 

    imshow(I)

    title(char(label))

    drawnow

end

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/TransferLearningUsingAlexNetExample\_02.png](images/00009.jpeg)

Calculate the classification accuracy.

testLabels = merchImagesTest.Labels;

 

accuracy = sum(predictedLabels==testLabels)/numel(predictedLabels)

accuracy =

 

    0.8667

 

This example has high accuracy. If the accuracy is not high enough using transfer learning, try feature extraction instead.

# 2.3 Transfer Learning and Fine-Tuning of Convolutional Neural Networks

 

This example shows how to classify new image data by fine-tuning an existing, pretrained convolutional neural network.

If you have a small amount of training data, constructing and training a new network can be time consuming and ineffective. Instead, you can fine-tune an existing pretrained network to solve a new problem. This technique, called transfer learning, usually results in faster training. By taking layers from a pretrained network and retraining the layers only at the end of the network, you can finish training much faster.

Neural Network Toolbox provides access to several pretrained networks, including the popular AlexNet. This example uses a simple pretrained network to introduce you to transfer learning. It takes a convolutional neural network trained on letter images and fine-tunes it to classify images of digits.

## 2.3.1 Load Pretrained Network

Load a pretrained network. LettersClassificationNet.mat contains the pretrained network net, which is trained on a large collection of 28-by-28 grayscale letter images. The network classifies images into the three letter classes 'A', 'B', and 'C'.

load(fullfile(matlabroot,'examples','nnet','LettersClassificationNet.mat'))

Examine the details of the network architecture contained in the Layers property of net.

net.Layers

ans = 

 

  7x1 Layer array with layers:

 

     1   'imageinput'    Image Input             28x28x1 images with 'zerocenter' normalization

     2   'conv'          Convolution             20 5x5x1 convolutions with stride \[1  1\] and padding \[0  0\]

     3   'relu'          ReLU                    ReLU

     4   'maxpool'       Max Pooling             2x2 max pooling with stride \[2  2\] and padding \[0  0\]

     5   'fc'            Fully Connected         3 fully connected layer

     6   'softmax'       Softmax                 softmax

     7   'classoutput'   Classification Output   crossentropyex with 'A', 'B', and 1 other classes

The network has seven layers. Layers 2–4 detect features. Layers 5–7 classify the features into letters classes. The 20 outputs (channels) of the convolutional layer correspond to the learned features. You can use these features to predict the classes of the digits data using transfer learning.

The last three layers of the pretrained network net are tuned for the letters data. By replacing the last three layers of the pretrained network, you can fine-tune the network to classify digits instead.

## 2.3.2 Load Training Data

Load the digits sample data as an ImageDatastore object. The imageDatastore function labels the images automatically based on folder names and stores the data as an ImageDatastore object. An ImageDatastore object lets you store large image data, including data that does not fit in memory. The object also lets you efficiently read batches of images during training.

digitDatasetPath = fullfile(matlabroot,'toolbox','nnet','nndemos', ...

    'nndatasets','DigitDataset');

 

digitData = imageDatastore(digitDatasetPath, ...

    'IncludeSubfolders',true,'LabelSource','foldernames');

The data store contains 10000 synthetic images of digits 0–9. The images are generated by applying random transformations to digit images created using different fonts. Each digit image is 28-by-28 pixels.

Split the data set into training and test data sets. Split the data so that each data store has 50% of the images from each category. splitEachLabel splits the image files in digitData into two new data stores: trainDigitData and testDigitData.

\[trainDigitData,testDigitData\] = splitEachLabel(digitData,0.5,'randomize');

Display 20 sample training digits using imshow.

numImages = numel(trainDigitData.Files);

idx = randperm(numImages,20);

for i = 1:20

    subplot(4,5,i)

 

    I = readimage(trainDigitData, idx(i));

 

    imshow(I)

end

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/TransferLearningAndFineTuningOfNetworksExample\_01.png](images/00010.jpeg)

## 2.3.3 Transfer Layers to Target Network

Transfer learning to the new task by replacing and fine-tuning these layers to the digits data. You can use transfer learning since the digits data is similar in content to the letters data. The last three layers of the pretrained network net are tuned for the letters data.

Extract all the layers except the last three from the pretrained network.

layersTransfer = net.Layers(1:end-3);

The digits data set has 10 classes. Add a new fully connected layer for 10 classes, a softmax layer, and a classification output layer. To speed up learning on the new layers only, increase the weight and bias learn rate factors of the fully connected layer.

numClasses = numel(categories(trainDigitData.Labels))

numClasses =

 

    10

 

layers = \[ ...

    layersTransfer

    fullyConnectedLayer(numClasses,'WeightLearnRateFactor',20,'BiasLearnRateFactor',20)

    softmaxLayer

    classificationLayer\];

If the training images differ in size to the image input layer, then you must resize or crop the image data. In this example, the training images are the same size as the input size of the pretrained network (28-by-28). You do not need to resize or crop the new image data.

Create the training options. For transfer learning, you want to keep the features from the early layers of the pretrained network (the transferred layer weights). Set 'InitialLearnRate' to a low value. This low initial learn rate slows down learning on the transferred layers. In the previous step, you set the learn rate factors for the fully connected layer higher to speed up learning on the new final layers. This combination results in fast learning only on the new layers while keeping the other layers fixed. When performing transfer learning, you do not need to train for as many epochs. To speed up training, reduce the value of the 'MaxEpochs' name-value pair argument in the call to trainingOptions.

optionsTransfer = trainingOptions('sgdm', ...

    'MaxEpochs',5, ...

    'InitialLearnRate',0.0001);

Fine-tune the network that consists of the transferred and new layers using trainNetwork.

netTransfer = trainNetwork(trainDigitData,layers,optionsTransfer);

Training on single CPU.

Initializing image normalization.

|=========================================================================================|

|     Epoch    |   Iteration  | Time Elapsed |  Mini-batch  |  Mini-batch  | Base Learning|

|              |              |  (seconds)   |     Loss     |   Accuracy   |     Rate     |

|=========================================================================================|

|            1 |            1 |         0.75 |      10.5459 |        6.25% |     1.00e-04 |

|            2 |           50 |        19.63 |       3.1897 |       70.31% |     1.00e-04 |

|            3 |          100 |        38.44 |       1.1082 |       80.47% |     1.00e-04 |

|            4 |          150 |        58.13 |       0.1465 |       95.31% |     1.00e-04 |

|            5 |          195 |        75.28 |       0.1504 |       96.88% |     1.00e-04 |

|=========================================================================================|

Calculate the classification accuracy: the proportion of correctly classified instances in the test data.

YPred = classify(netTransfer,testDigitData);

YTest = testDigitData.Labels;

 

accuracy = sum(YPred==YTest)/numel(YTest)

accuracy =

 

    0.9288

 

Display sample test images with their predicted labels.

idx = 501:500:5000;

figure

for i = 1:numel(idx)

    subplot(3,3,i)

 

    I = readimage(testDigitData, idx(i));

    label = char(YTest(idx(i)));

 

    imshow(I)

    title(label)

end

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/TransferLearningAndFineTuningOfNetworksExample\_02.png](images/00011.jpeg)

# 2.4 Deep Dream Images Using AlexNet

 

This example shows how to generate images using deepDreamImage with the pretrained convolutional neural network AlexNet.

Deep Dream is a feature visualization technique in deep learning that synthesizes images that strongly activate network layers. By visualizing these images, you can highlight the image features learned by a network. These images are useful for understanding and diagnosing network behavior.

You can generate interesting images by visualizing the features of the layers towards the end of the network.

The example uses Neural Network Toolbox™, Neural Network Toolbox Model *for AlexNet Network* to generate the images. Optionally, you can use Image Processing Toolbox™ to display multiple images together.

## 2.4.1 Load Pretrained Network

Load pretrained AlexNet Network (Neural Network Toolbox for AlexNet Model). If Neural Network Toolbox Model *for AlexNet Network* is not installed, then the software provides a download link.

net = alexnet;

## 2.4.2 Generate Image

To produce images that resemble a given class the most closely, select the final fully connected layer. First, locate the layer index of this layer by viewing the network architecture in the Layers property of the network net.

net.Layers

ans = 

 

  25x1 Layer array with layers:

 

     1   'data'     Image Input                   227x227x3 images with 'zerocenter' normalization

     2   'conv1'    Convolution                   96 11x11x3 convolutions with stride \[4  4\] and padding \[0  0\]

     3   'relu1'    ReLU                          ReLU

     4   'norm1'    Cross Channel Normalization   cross channel normalization with 5 channels per element

     5   'pool1'    Max Pooling                   3x3 max pooling with stride \[2  2\] and padding \[0  0\]

     6   'conv2'    Convolution                   256 5x5x48 convolutions with stride \[1  1\] and padding \[2  2\]

     7   'relu2'    ReLU                          ReLU

     8   'norm2'    Cross Channel Normalization   cross channel normalization with 5 channels per element

     9   'pool2'    Max Pooling                   3x3 max pooling with stride \[2  2\] and padding \[0  0\]

    10   'conv3'    Convolution                   384 3x3x256 convolutions with stride \[1  1\] and padding \[1  1\]

    11   'relu3'    ReLU                          ReLU

    12   'conv4'    Convolution                   384 3x3x192 convolutions with stride \[1  1\] and padding \[1  1\]

    13   'relu4'    ReLU                          ReLU

    14   'conv5'    Convolution                   256 3x3x192 convolutions with stride \[1  1\] and padding \[1  1\]

    15   'relu5'    ReLU                          ReLU

    16   'pool5'    Max Pooling                   3x3 max pooling with stride \[2  2\] and padding \[0  0\]

    17   'fc6'      Fully Connected               4096 fully connected layer

    18   'relu6'    ReLU                          ReLU

    19   'drop6'    Dropout                       50% dropout

    20   'fc7'      Fully Connected               4096 fully connected layer

    21   'relu7'    ReLU                          ReLU

    22   'drop7'    Dropout                       50% dropout

    23   'fc8'      Fully Connected               1000 fully connected layer

    24   'prob'     Softmax                       softmax

    25   'output'   Classification Output         crossentropyex with 'tench', 'goldfish', and 998 other classes

Then, select the final fully connected layer. The final fully connected layer is layer 23.

layer = 23;

You can generate multiple images at once by selecting multiple classes. Select the classes you want to visualize by setting channels to be the indices of those class names.

channels = \[9 188 231 563 855 975\];

The class names are stored in the ClassNames property of the output layer (the last layer). You can view the names of the selected classes by selecting the entries in channels.

net.Layers(end).ClassNames(channels)

ans =

 

  1×6 cell array

 

  Columns 1 through 4

 

    'hen'    'Yorkshire terrier'    'Shetland sheepdog'    'fountain'

 

  Columns 5 through 6

 

    'theater curtain'    'geyser'

 

Generate the images using deepDreamImage. This command uses a compatible GPU, if available. Otherwise it uses the CPU. A CUDA®-enabled NVIDIA® GPU with compute capability 3.0 or higher is required for training on a GPU.

I = deepDreamImage(net,layer,channels);

|============================================|

|    Pyramid   |  Iteration   |  Activation  |

|     Level    |              |   Strength   |

|============================================|

|            1 |            1 |         1.45 |

|            1 |            2 |         3.36 |

|            1 |            3 |         7.13 |

|            1 |            4 |        13.12 |

|            1 |            5 |        18.62 |

|            1 |            6 |        26.64 |

|            1 |            7 |        32.08 |

|            1 |            8 |        38.13 |

|            1 |            9 |        46.56 |

|            1 |           10 |        53.34 |

|            2 |            1 |        10.83 |

|            2 |            2 |        11.94 |

|            2 |            3 |        17.18 |

|            2 |            4 |        18.23 |

|            2 |            5 |        27.07 |

|            2 |            6 |        23.30 |

|            2 |            7 |        28.15 |

|            2 |            8 |        26.15 |

|            2 |            9 |        34.43 |

|            2 |           10 |        35.15 |

|            3 |            1 |        36.07 |

|            3 |            2 |        49.56 |

|            3 |            3 |        52.69 |

|            3 |            4 |        65.31 |

|            3 |            5 |        61.22 |

|            3 |            6 |        68.71 |

|            3 |            7 |        74.45 |

|            3 |            8 |        75.56 |

|            3 |            9 |        82.75 |

|            3 |           10 |        78.51 |

|============================================|

If you have Image Processing Toolbox installed, you can display all the images together using montage. Otherwise, you can display the images individually using imshow.

figure

montage(I)

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/DeepDreamUsingAlexNetExample\_01.png](images/00012.jpeg)

## 2.4.3 Generate More Detailed Images

Increasing the number of pyramid levels and iterations per pyramid level can produce more detailed images at the expense of additional computation.

You can increase the number of iterations using the 'NumIterations' option. Set the number of iterations to 100.

iterations = 100;

Generate a detailed image that strongly activates the 'hen' class (channel 9). Set 'Verbose' to false to suppress detailed information on the optimization process.

channels = 9;

I = deepDreamImage(net,layer,channels, ...

    'Verbose',false, ...

    'NumIterations',iterations);

 

figure

imshow(I)

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/DeepDreamUsingAlexNetExample\_02.png](images/00013.jpeg)

To produce larger and more detailed output images, you can increase both the number of pyramid levels and iterations per pyramid level.

Set the number of pyramid levels to 4.

levels = 4;

Generate a detailed image that strongly activates the 'pot' class (channel 739).

channels = 739;

 

I = deepDreamImage(net,layer,channels, ...

    'Verbose',false, ...

    'NumIterations',iterations, ...

    'PyramidLevels',levels);

 

figure

imshow(I)

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/DeepDreamUsingAlexNetExample\_03.png](images/00014.jpeg)

 

  

3Chapter 3

DEEP LEARNING NETWORK FOR CLASSIFICATION AND REGRESSION

# 3.1 Create Simple Deep Learning Network for Classification

 

This example shows how to create and train a simple convolutional neural network for deep learning classification. Convolutional neural networks are essential tools for deep learning, and are especially suited for image recognition. Learn how to set up network layers, image data, and training options, train the network, and test the classification accuracy.

## 3.1.1 Load and Explore the Image Data

Load the digit sample data as an ImageDatastore object.

digitDatasetPath = fullfile(matlabroot,'toolbox','nnet','nndemos', ...

        'nndatasets','DigitDataset');

digitData = imageDatastore(digitDatasetPath, ...

        'IncludeSubfolders',true,'LabelSource','foldernames');

imageDatastore function labels the images automatically based on folder names and stores the data as an ImageDatastore object. An ImageDatastore object lets you store large image data, including data that do not fit in memory, and efficiently read batches of images during training of a convolutional neural network.

Display some of the images in the datastore.

figure;

perm = randperm(10000,20);

for i = 1:20

    subplot(4,5,i);

    imshow(digitData.Files{perm(i)});

end

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/TrainABasicConvolutionalNeuralNetworkForClassificationExample\_01.png](images/00015.jpeg)

Check the number of images in each category.

CountLabel = digitData.countEachLabel;

CountLabel is a table that contains the labels and the number of images in each label. It shows that the datastore contains 1000 images for each of the digits 0-9, a total of 10000. Hence, there are 10 classes. You can specify the number of classes in the last fully connected layer of your network as the OutputSize parameter. The images are generated by applying random transformations to digit images created using different fonts.

You must specify the size of the images in the input layer of the network. Check the size of the first image in digitData .

img = readimage(digitData,1);

size(img)

ans =

 

    28    28

 

Each digit image is 28-by-28-by-1 pixels.

## 3.1.2 Specify Training and Test Sets

Divide the data into training and test sets, so that each category in the training set has 750 images and the test set has the remaining images from each label.

trainingNumFiles = 750;

rng(1) % For reproducibility

\[trainDigitData,testDigitData\] = splitEachLabel(digitData, ...

                                  trainingNumFiles,'randomize');

splitEachLabel splits the image files in digitData into two new datastores, trainDigitData and testDigitData.

## 3.1.3 Define the Network Layers

Define the convolutional neural network architecture.

layers = \[imageInputLayer(\[28 28 1\])

          convolution2dLayer(5,20)

          reluLayer

          maxPooling2dLayer(2,'Stride',2)

          fullyConnectedLayer(10)

          softmaxLayer

          classificationLayer()\];

**Image Input Layer** An [imageInputLayer](http://es.mathworks.com/help/nnet/ref/imageinputlayer.html) is where you specify the image size, which, in this case, is 28-by-28-by-1. These numbers correspond to the height, width, and the channel size. The digit data consists of gray scale images, hence the channel size (color channel) is 1. For a color image, the channel size would be 3, corresponding to the RGB values. You can also specify any data transformation at this layer, such as data normalization or data augmentation (randomly flip or crop the data). These are usually used to avoid overfitting. You do not need to shuffle the data as trainNetworkautomatically does it at the beginning of the training.

**Convolutional Layer** In the convolutional layer, the first argument is filterSize, which is the height and width of the filters the training function uses while scanning along the images. In this example, the number 5 indicates that the filter size is \[5,5\]. You can also specify different sizes for the height and the width of the filter. The second argument is the number of filters, which is the number of neurons that connect to the same region of the output. This parameter determines the number of the feature maps.

**ReLU Layer** The convolutional layer is followed by a nonlinear activation function. MATLAB uses the rectified linear unit function, specified by [reluLayer](http://es.mathworks.com/help/nnet/ref/relulayer.html).

**Max-Pooling Layer** The convolutional layer (with the activation function) is usually followed by a down-sampling operation to reduce the number of parameters and as another way of avoiding overfitting. One way of down-sampling is max-pooling, which is specified by the [maxPooling2dLayer](http://es.mathworks.com/help/nnet/ref/maxpooling2dlayer.html) function. This layer returns the maximum values of rectangular regions of inputs, specified by the first argument, poolSize. In this example, the size of the rectangular region is \[2,2\]. The optional argument Stride determines the step size the training function takes as it scans along the image. This max-pooling layer takes place between the convolutional layers when there are multiple of them in the network.

**Fully Connected Layer** The convolutional (and down-sampling) layers are followed by one or more fully connected layers. As the name suggests, all neurons in a fully connected layer connect to the neurons in the layer previous to it. This layer combines all of the features (local information) learned by the previous layers across the image to identify the larger patterns. The last fully connected layer combines them to classify the images. That is why, the OutputSize parameter in the last fully connected layer is equal to the number of classes in the target data. In this example the output size is 10, corresponding to the 10 digits.

**Softmax Layer** The fully connected layer usually uses the softmax activation function for classification. You can add the softmax layer by using the [softmaxLayer](http://es.mathworks.com/help/nnet/ref/softmaxlayer.html) function after the last fully connected layer.

**Classification Layer** The final layer is the classification layer, defined by using the [classificationLayer](http://es.mathworks.com/help/nnet/ref/classificationlayer.html) function. This layer uses the probabilities returned by the softmax activation function for each input to assign it to one of the mutually exclusive classes.

## 3.1.4 Specify the Training Options

After defining the layers (network structure), specify the training options. Set the options to default settings for the stochastic gradient descent with momentum. Set the maximum number of epochs at 15 (an epoch is a full training cycle on the whole training data), and start the training with an initial learning rate of 0.0001.

options = trainingOptions('sgdm','MaxEpochs',15, ...

        'InitialLearnRate',0.0001);

## 3.1.5 Train the Network Using Training Data

Train the network you defined in layers, using the training data and the training options you defined in the previous steps.

convnet = trainNetwork(trainDigitData,layers,options);

Training on single GPU.

Initializing image normalization.

|=========================================================================================|

|     Epoch    |   Iteration  | Time Elapsed |  Mini-batch  |  Mini-batch  | Base Learning|

|              |              |  (seconds)   |     Loss     |   Accuracy   |     Rate     |

|=========================================================================================|

|            1 |            1 |         4.38 |       3.0845 |       13.28% |       0.0001 |

|            1 |           50 |         5.44 |       1.0945 |       65.63% |       0.0001 |

|            2 |          100 |         6.17 |       0.7276 |       74.22% |       0.0001 |

|            3 |          150 |         6.92 |       0.4741 |       83.59% |       0.0001 |

|            4 |          200 |         7.66 |       0.3085 |       92.19% |       0.0001 |

|            5 |          250 |         8.41 |       0.2323 |       92.97% |       0.0001 |

|            6 |          300 |         9.16 |       0.1542 |       97.66% |       0.0001 |

|            7 |          350 |         9.90 |       0.1313 |       97.66% |       0.0001 |

|            7 |          400 |        10.64 |       0.0944 |       96.09% |       0.0001 |

|            8 |          450 |        11.40 |       0.0667 |       99.22% |       0.0001 |

|            9 |          500 |        12.16 |       0.0459 |       99.22% |       0.0001 |

|           10 |          550 |        12.93 |       0.0544 |      100.00% |       0.0001 |

|           11 |          600 |        13.68 |       0.0660 |       99.22% |       0.0001 |

|           12 |          650 |        14.43 |       0.0339 |      100.00% |       0.0001 |

|           13 |          700 |        15.17 |       0.0341 |      100.00% |       0.0001 |

|           13 |          750 |        15.89 |       0.0369 |      100.00% |       0.0001 |

|           14 |          800 |        16.62 |       0.0263 |      100.00% |       0.0001 |

|           15 |          850 |        17.37 |       0.0181 |      100.00% |       0.0001 |

|           15 |          870 |        17.66 |       0.0234 |      100.00% |       0.0001 |

|=========================================================================================|

trainNetwork displays the hardware it uses for training in the display window. It uses a GPU by default if there is one available (requires Parallel Computing Toolbox (TM) and a CUDA-enabled GPU with compute capability 3.0 and higher). If there is no available GPU, it uses a CPU. You can also specify the execution environment using the 'ExecutionEnvironment' name-value pair argument in the call to trainingOptions.

The progress window shows the mini-batch loss and the mini-batch accuracy for the first iteration, last iteration and every 50 iterations in between. The mini-batch loss is the Cross Entropy Function for k Mutually Exclusive Classes and the mini-batch accuracy is the percentage of images in the current mini-batch that the network being trained correctly classifies.

It also shows the cumulative time it takes for training and the learning rate at that iteration. In this example, the base learning rate is fixed at 0.0001 through the entire training process. You can also adjust this and reduce the learning rate at certain number of epochs. For more details, see the trainingOptions function reference page.

## 3.1.6 Classify the Images in the Test Data and Compute Accuracy

Run the trained network on the test set that was not used to train the network and predict the image labels (digits).

YTest = classify(convnet,testDigitData);

TTest = testDigitData.Labels;

Calculate the accuracy.

accuracy = sum(YTest == TTest)/numel(TTest)

accuracy =

 

    0.9812

Accuracy is the ratio of the number of true labels in the test data matching the classifications from classify, to the number of images in the test data. In this case about 98% of the digit estimations match the true digit values in the test set.

# 3.2 Train a Convolutional Neural Network for Regression

 

This example shows how to fit a regression model using convolutional neural networks to predict the angles of rotation of handwritten digits.

Convolutional neural networks (CNNs or ConvNets) are essential tools for deep learning, and are especially suited for analyzing image data. For example, you can use CNNs to classify images. To predict continuous data such as angles and distances, you can include a regression layer at the end of the network.

The example constructs a convolutional neural network architecture, trains a network, and uses the trained network to predict angles of rotated, handwritten digits. These predictions are useful for optical character recognition.

Optionally, you can use imrotate (Image Processing Toolbox™) to rotate the images, and boxplot (Statistics and Machine Learning Toolbox™) to create a residual box plot.

## 3.2.1 Load Training Data

The network is trained on a collection synthetic handwritten digits containing 5000 images of digits with corresponding angles of rotation.

Load the digit training set as 4-D array data using digitTrain4DArrayData.

\[trainImages,~,trainAngles\] = digitTrain4DArrayData;

Display 20 random sample training digits using imshow.

numTrainImages = size(trainImages,4);

 

figure

idx = randperm(numTrainImages,20);

for i = 1:numel(idx)

    subplot(4,5,i)

 

    imshow(trainImages(:,:,:,idx(i)))

    drawnow

end

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/TrainAConvolutionalNeuralNetworkForRegressionExample\_01.png](images/00016.jpeg)

## 3.2.2 Create Network Layers

To solve the regression problem, create the layers of the network and include a regression layer at the end of the network.

The first layer defines the size and type of the input data. The input images are 28-by-28-by-1. Create an image input layer of the same size as the training images.

The middle layers of the network define the core architecture of the network. Create a 2-D convolutional layer with 25 filters of size 12 followed by a ReLU layer.

The final layers define the size and type of output data. For regression problems, a fully connected layer must precede the regression layer at the end of the network. Create a fully connected output layer of size 1 and a regression layer.

Combine all the layers together in a Layer array.

layers = \[ ...

    imageInputLayer(\[28 28 1\])

    convolution2dLayer(12,25)

    reluLayer

    fullyConnectedLayer(1)

    regressionLayer\];

## 3.2.3 Train Network

Create the network training options. Set the initial learn rate to 0.001. To reduce training time, lower the value of 'MaxEpochs'.

options = trainingOptions('sgdm','InitialLearnRate',0.001, ...

    'MaxEpochs',15);

Create the network using trainNetwork. This command uses a compatible GPU if available. Otherwise, trainNetworkuses the CPU. A CUDA®-enabled NVIDIA® GPU with compute capability 3.0 or higher is required for training on a GPU. Training can take a few minutes, especially when training on a CPU.

net = trainNetwork(trainImages,trainAngles,layers,options)

Training on single CPU.

Initializing image normalization.

|=========================================================================================|

|     Epoch    |   Iteration  | Time Elapsed |  Mini-batch  |  Mini-batch  | Base Learning|

|              |              |  (seconds)   |     Loss     |     RMSE     |     Rate     |

|=========================================================================================|

|            1 |            1 |         1.04 |     392.5880 |        28.02 |       0.0010 |

|            2 |           50 |        40.97 |      96.0224 |        13.86 |       0.0010 |

|            3 |          100 |        80.61 |      55.5511 |        10.54 |       0.0010 |

|            4 |          150 |       120.15 |      64.4054 |        11.35 |       0.0010 |

|            6 |          200 |       158.61 |      36.2762 |         8.52 |       0.0010 |

|            7 |          250 |       196.01 |      53.0097 |        10.30 |       0.0010 |

|            8 |          300 |       238.67 |      35.7707 |         8.46 |       0.0010 |

|            9 |          350 |       281.16 |      35.0280 |         8.37 |       0.0010 |

|           11 |          400 |       324.23 |      24.9089 |         7.06 |       0.0010 |

|           12 |          450 |       366.40 |      33.0280 |         8.13 |       0.0010 |

|           13 |          500 |       409.12 |      27.0606 |         7.36 |       0.0010 |

|           15 |          550 |       446.05 |      18.1960 |         6.03 |       0.0010 |

|           15 |          585 |       471.13 |      18.9572 |         6.16 |       0.0010 |

|=========================================================================================|

 

net = 

 

  SeriesNetwork with properties:

 

    Layers: \[5×1 nnet.cnn.layer.Layer\]

 

Examine the details of the network architecture contained in the Layers property of net.

net.Layers

ans = 

 

  5x1 Layer array with layers:

 

     1   'imageinput'         Image Input         28x28x1 images with 'zerocenter' normalization

     2   'conv'               Convolution         25 12x12x1 convolutions with stride \[1  1\] and padding \[0  0\]

     3   'relu'               ReLU                ReLU

     4   'fc'                 Fully Connected     1 fully connected layer

     5   'regressionoutput'   Regression Output   mean-squared-error with response 'Response'

## 3.2.4 Test Network

Test the performance of the network by evaluating the prediction accuracy of held out test data.

Load the digit test set.

\[testImages,~,testAngles\] = digitTest4DArrayData;

Use predict to predict the angles of rotation of the test images.

predictedTestAngles = predict(net,testImages);

**Evaluate Performance**

Evaluate the performance of the model by calculating:

1.      The percentage of predictions within an acceptable error margin

2.      The root-mean-square error (RMSE) of the predicted and actual angles of rotation

Calculate the prediction error between the predicted and actual angles of rotation.

predictionError = testAngles - predictedTestAngles;

Calculate the number of predictions within an acceptable error margin from the true angles. Set the threshold to be 10 degrees. Calculate the percentage of predictions within this threshold.

thr = 10;

numCorrect = sum(abs(predictionError) < thr);

numTestImages = size(testImages,4);

 

accuracy = numCorrect/numTestImages

accuracy =

 

    0.8488

 

Use the root-mean-square error (RMSE) to measure the differences between the predicted and actual angles of rotation.

squares = predictionError.^2;

rmse = sqrt(mean(squares))

rmse =

 

  single

 

    7.3441

 

If the accuracy is too low, or the RMSE is too high, then try increasing the value of 'MaxEpochs' in the call to trainingOptions.

**Display Box Plot of Residuals for Each Digit Class**

Calculate the residuals.

residuals = testAngles - predictedTestAngles;

The boxplot function requires a matrix where each column corresponds to the residuals for each digit class.

The test data groups images by digit classes 0–9 with 500 examples of each. Use reshape to group the residuals by digit class.

residualMatrix = reshape(residuals,500,10);

Each column of residualMatrix corresponds to the residuals of each digit. Create a residual box plot for each digit using boxplot (Statistics and Machine Learning Toolbox).

figure

boxplot(residualMatrix, ...

    'Labels',{'0','1','2','3','4','5','6','7','8','9'})

 

xlabel('Digit Class')

ylabel('Degrees Error')

title('Residuals')

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/TrainAConvolutionalNeuralNetworkForRegressionExample\_02.png](images/00017.jpeg)

The digit classes with highest accuracy have a mean close to zero and little variance.

## 3.2.5 Correct Digit Rotations

You can use functions from Image Processing Toolbox to straighten to straighten the digits and display them together. Rotate 49 sample digits according to their predicted angles of rotation using imrotate (Image Processing Toolbox).

idx = randperm(numTestImages,49);

for i = 1:numel(idx)

    image = testImages(:,:,:,idx(i));

    predictedAngle = predictedTestAngles(idx(i));

 

    imagesRotated(:,:,:,i) = imrotate(image,predictedAngle,'bicubic','crop');

end

Display the original digits with their corrected rotations. You can use montage (Image Processing Toolbox) to display the digits together in a single image.

figure

subplot(1,2,1)

montage(testImages(:,:,:,idx))

title('Original')

 

subplot(1,2,2)

montage(imagesRotated)

title('Corrected')

![](images/00018.jpeg)

 

  

4Chapter 4

DEEP LEARNING AND VISUALIZATION 

# 4.1 Visualize Activations of a Convolutional Neural Network

 

This example shows how to feed an image to a convolutional neural network and display the activations of different layers of the network. Examine the activations and discover which features the network learns by comparing areas of activation with the original image. Find out that channels in earlier layers learn simple features like color and edges, while channels in the deeper layers learn complex features like eyes. Identifying features in this way can help you understand what the network has learned.

The example requires Neural Network Toolbox™, Image Processing Toolbox™ and the Neural Network Toolbox™ Model *for AlexNet Network*.

## 4.1.1 Load Pretrained Network and Data

Load the popular pretrained network *AlexNet*. If Neural Network Toolbox™ Model *for AlexNet Network* is not installed, then the software provides a download link.

net = alexnet;

Read and show an image. Save its size for future use.

im = imread(fullfile(matlabroot,'examples','nnet','face.jpg'));

imshow(im)

imgSize = size(im);

imgSize = imgSize(1:2);

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/VisualizeActivationsOfAConvolutionalNeuralNetworkExample\_01.png](images/00019.jpeg)

## 4.1.2 View Network Architecture

Display the layers of the network to see which layers you can look at. The convolutional layers perform convolutions with learnable parameters. The network learns to identify useful features, often with one feature per channel. Observe that the first convolutional layer has 96 channels.

net.Layers

ans = 

 

  25x1 Layer array with layers:

 

     1   'data'     Image Input                   227x227x3 images with 'zerocenter' normalization

     2   'conv1'    Convolution                   96 11x11x3 convolutions with stride \[4  4\] and padding \[0  0\]

     3   'relu1'    ReLU                          ReLU

     4   'norm1'    Cross Channel Normalization   cross channel normalization with 5 channels per element

     5   'pool1'    Max Pooling                   3x3 max pooling with stride \[2  2\] and padding \[0  0\]

     6   'conv2'    Convolution                   256 5x5x48 convolutions with stride \[1  1\] and padding \[2  2\]

     7   'relu2'    ReLU                          ReLU

     8   'norm2'    Cross Channel Normalization   cross channel normalization with 5 channels per element

     9   'pool2'    Max Pooling                   3x3 max pooling with stride \[2  2\] and padding \[0  0\]

    10   'conv3'    Convolution                   384 3x3x256 convolutions with stride \[1  1\] and padding \[1  1\]

    11   'relu3'    ReLU                          ReLU

    12   'conv4'    Convolution                   384 3x3x192 convolutions with stride \[1  1\] and padding \[1  1\]

    13   'relu4'    ReLU                          ReLU

    14   'conv5'    Convolution                   256 3x3x192 convolutions with stride \[1  1\] and padding \[1  1\]

    15   'relu5'    ReLU                          ReLU

    16   'pool5'    Max Pooling                   3x3 max pooling with stride \[2  2\] and padding \[0  0\]

    17   'fc6'      Fully Connected               4096 fully connected layer

    18   'relu6'    ReLU                          ReLU

    19   'drop6'    Dropout                       50% dropout

    20   'fc7'      Fully Connected               4096 fully connected layer

    21   'relu7'    ReLU                          ReLU

    22   'drop7'    Dropout                       50% dropout

    23   'fc8'      Fully Connected               1000 fully connected layer

    24   'prob'     Softmax                       softmax

    25   'output'   Classification Output         crossentropyex with 'tench', 'goldfish', and 998 other classes

 

The Image Input layer specifies the input size. You can resize the image before passing it through the network, but the network also can process larger images. If you feed the network larger images, the activations also become larger. However, since the network is trained on images of size 227-by-227, it is not trained to recognize objects or features larger than that size.

## 4.1.3 Show Activations of First Convolutional Layer

Investigate features by observing which areas in the convolutional layers activate on an image and comparing with the corresponding areas in the original images. Each layer of a convolutional neural network consists of many 2-D arrays called *channels*. Pass the image through the network and examine the output activations of the conv1 layer.

act1 = activations(net,im,'conv1','OutputAs','channels');

The activations are returned as a 3-D array, with the third dimension indexing the channel on the conv1 layer. To show these activations using the montage function, reshape the array to 4-D. The third dimension in the input to montagerepresents the image color. Set the third dimension to have size 1 because the activations do not have color. The fourth dimension indexes the channel.

sz = size(act1);

act1 = reshape(act1,\[sz(1) sz(2) 1 sz(3)\]);

Now you can show the activations. Each activation can take any value, so normalize the output using mat2gray. All activations are scaled so that the minimum activation is 0 and the maximum is 1. Display a montage of the 96 images on an 8-by-12 grid, one for each channel in the layer.

montage(mat2gray(act1),'Size',\[8 12\])

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/VisualizeActivationsOfAConvolutionalNeuralNetworkExample\_02.png](images/00020.jpeg)

## 4.1.4 Investigate the Activations in Specific Channels

Each square in the montage of activations is the output of a channel in the conv1 layer. White pixels represent strong positive activations and black pixels represent strong negative activations. A channel that is mostly gray does not activate as strongly on the input image. The position of a pixel in the activation of a channel corresponds to the same position in the original image. A white pixel at some location in a channel indicates that the channel is strongly activated at that position.

Resize the activations in channel 32 to have the same size as the original image and display the activations.

act1ch32 = act1(:,:,:,32);

act1ch32 = mat2gray(act1ch32);

act1ch32 = imresize(act1ch32,imgSize);

imshowpair(im,act1ch32,'montage')

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/VisualizeActivationsOfAConvolutionalNeuralNetworkExample\_03.png](images/00021.jpeg)

You can see that this channel activates on red pixels, because the whiter pixels in the channel correspond to red areas in the original image.

## 4.1.5 Find the Strongest Activation Channel

You also can try to find interesting channels by programmatically investigating channels with large activations. Find the channel with the largest activation using the max function, resize, and show the activations.

\[maxValue,maxValueIndex\] = max(max(max(act1)));

act1chMax = act1(:,:,:,maxValueIndex);

act1chMax = mat2gray(act1chMax);

act1chMax = imresize(act1chMax,imgSize);

imshowpair(im,act1chMax,'montage')

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/VisualizeActivationsOfAConvolutionalNeuralNetworkExample\_04.png](images/00022.jpeg)

Compare to the original image and notice that this channel activates on edges. It activates positively on light left/dark right edges, and negatively on dark left/light right edges.

## 4.1.6 Investigate a Deeper Layer

Most convolutional neural networks learn to detect features like color and edges in their first convolutional layer. In deeper convolutional layers, the network learns to detect more complicated features. Later layers build up their features by combining features of earlier layers. Investigate the conv5 layer in the same way as the conv1 layer. Calculate, reshape, and show the activations in a montage.

act5 = activations(net,im,'conv5','OutputAs','channels');

sz = size(act5);

act5 = reshape(act5,\[sz(1) sz(2) 1 sz(3)\]);

montage(imresize(mat2gray(act5),\[48 48\]))

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/VisualizeActivationsOfAConvolutionalNeuralNetworkExample\_05.png](images/00023.jpeg)

There are too many images to investigate in detail, so focus on some of the more interesting ones. Display the strongest activation in the conv5 layer.

\[maxValue5,maxValueIndex5\] = max(max(max(act5)));

act5chMax = act5(:,:,:,maxValueIndex5);

imshow(imresize(mat2gray(act5chMax),imgSize))

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/VisualizeActivationsOfAConvolutionalNeuralNetworkExample\_06.png](images/00024.jpeg)

In this case, the maximum activation channel is not as interesting for detailed features as some others, and shows strong negative (dark) as well as positive (light) activation. This channel is possibly focusing on faces.

In the montage of all channels, there are channels that might be activating on eyes. Investigate channels 3 and 5 further.

montage(imresize(mat2gray(act5(:,:,:,\[3 5\])),imgSize))

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/VisualizeActivationsOfAConvolutionalNeuralNetworkExample\_07.png](images/00025.jpeg)

Many of the channels contain areas of activation that are both light and dark. These are positive and negative activations, respectively. However, only the positive activations are used because of the rectified linear unit (ReLU) that follows the conv5 layer. To investigate only positive activations, repeat the analysis to visualize the activations of the relu5 layer.

act5relu = activations(net,im,'relu5','OutputAs','channels');

sz = size(act5relu);

act5relu = reshape(act5relu,\[sz(1) sz(2) 1 sz(3)\]);

montage(imresize(mat2gray(act5relu(:,:,:,\[3 5\])),imgSize))

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/VisualizeActivationsOfAConvolutionalNeuralNetworkExample\_08.png](images/00026.jpeg)

Compared to the activations of the conv5 layer, the activations of the relu5 layer clearly pinpoint areas of the image that have strong facial features.

## 4.1.7 Test Whether a Channel Recognizes Eyes

Check whether channels 3 and 5 of the relu5 layer activate on eyes. Input a new image with one closed eye to the network and compare the resulting activations with the activations of the original image.

Read and show the image with one closed eye and compute the activations of the relu5 layer.

imClosed = imread(fullfile(matlabroot,'examples','nnet','face-eye-closed.jpg'));

imshow(imClosed)

 

act5Closed = activations(net,imClosed,'relu5','OutputAs','channels');

sz = size(act5Closed);

act5Closed = reshape(act5Closed,\[sz(1),sz(2),1,sz(3)\]);

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/VisualizeActivationsOfAConvolutionalNeuralNetworkExample\_09.png](images/00027.jpeg)

Plot the images and activations in one figure.

channelsClosed = repmat(imresize(mat2gray(act5Closed(:,:,:,\[3 5\])),imgSize),\[1 1 3\]);

channelsOpen = repmat(imresize(mat2gray(act5relu(:,:,:,\[3 5\])),imgSize),\[1 1 3\]);

montage(cat(4,im,channelsOpen\*255,imClosed,channelsClosed\*255));

title('Input Image, Channel 3, Channel 5');

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/VisualizeActivationsOfAConvolutionalNeuralNetworkExample\_10.png](images/00028.jpeg)

You can see from the activations that both channels 3 and 5 activate on individual eyes, and to some degree also on the area around the mouth.

The network has never been told to learn about eyes, but it has learned that eyes are a useful feature to distinguish between classes of images. Previous machine learning approaches often manually designed features specific to the problem, but these deep convolutional networks can learn useful features for themselves. For example, learning to identify eyes could help the network distinguish between a leopard and a leopard print rug.

# 4.2 Visualize Features of a Convolutional Neural Network

 

This example shows how to visualize the features learned by convolutional neural networks.

Convolutional neural networks use *features* to classify images. The network learns these features itself during the training process. What the network learns during training is sometimes unclear. However, you can use the deepDreamImage function to visualize the features learned.

The *convolutional* layers of a network output multiple 2-D arrays. Each array (or channel) corresponds to a filter applied to the layer input. The channels output by *fully connected* layers correspond to high-level combinations of the features learned by earlier layers.

You can visualize what the learned features look like by using deepDreamImage to generate images that strongly activate a particular channel of the network layers.

The example requires Neural Network Toolbox™, Image Processing Toolbox™, and Neural Network Toolbox Model *for AlexNet Network* support package.

## 4.2.1 Load Pretrained Network

Load a pretrained AlexNet network.

net = alexnet;

## 4.2.2 Visualize Convolutional Layers

There are five 2-D convolutional layers in the AlexNet network. The convolutional layers towards the beginning of the network have a small receptive field size and learn small, low-level features. The layers towards the end of the network have larger receptive field sizes and learn larger features.

Using the Layers property, view the network architecture and locate the convolutional layers. Notice that the 2-D convolutional layers are layers 2, 6, 10, 12, and 14.

net.Layers

ans = 

 

  25x1 Layer array with layers:

 

     1   'data'     Image Input                   227x227x3 images with 'zerocenter' normalization

     2   'conv1'    Convolution                   96 11x11x3 convolutions with stride \[4  4\] and padding \[0  0\]

     3   'relu1'    ReLU                          ReLU

     4   'norm1'    Cross Channel Normalization   cross channel normalization with 5 channels per element

     5   'pool1'    Max Pooling                   3x3 max pooling with stride \[2  2\] and padding \[0  0\]

     6   'conv2'    Convolution                   256 5x5x48 convolutions with stride \[1  1\] and padding \[2  2\]

     7   'relu2'    ReLU                          ReLU

     8   'norm2'    Cross Channel Normalization   cross channel normalization with 5 channels per element

     9   'pool2'    Max Pooling                   3x3 max pooling with stride \[2  2\] and padding \[0  0\]

    10   'conv3'    Convolution                   384 3x3x256 convolutions with stride \[1  1\] and padding \[1  1\]

    11   'relu3'    ReLU                          ReLU

    12   'conv4'    Convolution                   384 3x3x192 convolutions with stride \[1  1\] and padding \[1  1\]

    13   'relu4'    ReLU                          ReLU

    14   'conv5'    Convolution                   256 3x3x192 convolutions with stride \[1  1\] and padding \[1  1\]

    15   'relu5'    ReLU                          ReLU

    16   'pool5'    Max Pooling                   3x3 max pooling with stride \[2  2\] and padding \[0  0\]

    17   'fc6'      Fully Connected               4096 fully connected layer

    18   'relu6'    ReLU                          ReLU

    19   'drop6'    Dropout                       50% dropout

    20   'fc7'      Fully Connected               4096 fully connected layer

    21   'relu7'    ReLU                          ReLU

    22   'drop7'    Dropout                       50% dropout

    23   'fc8'      Fully Connected               1000 fully connected layer

    24   'prob'     Softmax                       softmax

    25   'output'   Classification Output         crossentropyex with 'tench', 'goldfish', and 998 other classes

**Features on Convolutional Layer 1**

Set layer to be the first convolutional layer. This layer is the second layer in the network and is named 'conv1'.

layer = 2;

name = net.Layers(layer).Name

name =

 

    'conv1'

 

Visualize the first 56 features learned by this layer using deepDreamImage by setting channels to be the vector of indices 1:56. Set 'PyramidLevels' to 1 so that the images are not scaled. To display the images together, you can use montage(Image Processing Toolbox).

deepDreamImage uses a compatible GPU, by default, if available. Otherwise it uses the CPU. A CUDA®-enabled NVIDIA® GPU with compute capability 3.0 or higher is required for training on a GPU.

channels = 1:56;

 

I = deepDreamImage(net,layer,channels, ...

    'PyramidLevels',1);

 

figure

montage(I)

title(\['Layer ',name,' Features'\])

|============================================|

|    Pyramid   |  Iteration   |  Activation  |

|     Level    |              |   Strength   |

|============================================|

|            1 |            1 |         2.46 |

|            1 |            2 |        38.02 |

|            1 |            3 |        73.59 |

|            1 |            4 |       109.16 |

|            1 |            5 |       144.72 |

|            1 |            6 |       180.29 |

|            1 |            7 |       215.86 |

|            1 |            8 |       251.42 |

|            1 |            9 |       286.99 |

|            1 |           10 |       322.56 |

|============================================|

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/VisualizeConvolutionalNeuralNetworkLayersExample\_01.png](images/00029.jpeg)

These images mostly contain edges and colors, which indicates that the filters at layer 'conv1' are edge detectors and color filters. The edge detectors are at different angles, which allows the network to construct more complex features in the later layers.

 

**Features on Convolutional Layer 2**

These features are created using the features from layer 'conv1'. The second convolutional layer is named 'conv2', which corresponds to layer 6. Visualize the first 30 features learned by this layer by setting channels to be the vector of indices 1:30.

layer = 6;

channels = 1:30;

 

I = deepDreamImage(net,layer,channels,...

    'PyramidLevels',1);

 

figure

montage(I)

name = net.Layers(layer).Name;

title(\['Layer ',name,' Features'\])

|============================================|

|    Pyramid   |  Iteration   |  Activation  |

|     Level    |              |   Strength   |

|============================================|

|            1 |            1 |         3.86 |

|            1 |            2 |         4.87 |

|            1 |            3 |        14.14 |

|            1 |            4 |        21.64 |

|            1 |            5 |        27.33 |

|            1 |            6 |        31.88 |

|            1 |            7 |        35.66 |

|            1 |            8 |        39.32 |

|            1 |            9 |        41.96 |

|            1 |           10 |        44.27 |

|============================================|

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/VisualizeConvolutionalNeuralNetworkLayersExample\_02.png](images/00030.jpeg)

**Features on Convolutional Layers 3–5**

For each of the remaining convolutional layers, visualize the first 30 features learned. To suppress detailed output on the optimization process, set 'Verbose' to 'false' in the call to deepDreamImage. Notice that the layers which are deeper into the network yield more detailed filters.

 

layers = \[10 12 14\];

channels = 1:30;

 

for layer = layers

    I = deepDreamImage(net,layer,channels,...

        'Verbose',false, ...

        'PyramidLevels',1);

 

    figure

    montage(I)

    name = net.Layers(layer).Name;

    title(\['Layer ',name,' Features'\])

end

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/VisualizeConvolutionalNeuralNetworkLayersExample\_03.png](images/00031.jpeg)

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/VisualizeConvolutionalNeuralNetworkLayersExample\_04.png](images/00032.jpeg)

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/VisualizeConvolutionalNeuralNetworkLayersExample\_05.png](images/00033.jpeg)

## 4.2.3 Visualize Fully Connected Layers

There are three fully connected layers in the AlexNet model. The fully connected layers are towards the end of the network and learn high-level combinations of the features learned by the earlier layers.

Select the first two fully connected layers (layers 17 and 20).

layers = \[17 20\];

For each of these layers, use deepDreamImage to visualize the first six features. Set 'NumIterations' to 50 in the call to deepDreamImage to produce more detailed images. The images generated from the final fully connected layer correspond to the image classes.

channels = 1:6;

 

for layer = layers

    I = deepDreamImage(net,layer,channels, ...

        'Verbose',false, ...

        'NumIterations',50);

 

    figure

    montage(I)

    name = net.Layers(layer).Name;

    title(\['Layer ',name,' Features'\])

end

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/VisualizeConvolutionalNeuralNetworkLayersExample\_06.png](images/00034.jpeg)

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/VisualizeConvolutionalNeuralNetworkLayersExample\_07.png](images/00035.jpeg)

To produce images that resemble each class the most closely, select the final fully connected layer, and set channels to be the indices of the classes.

layer = 23;

channels = \[9 188 231 563 855 975\];

The class names are stored in the ClassNames property of the output layer (the last layer). You can view the names of the selected classes by selecting the entries in channels.

net.Layers(end).ClassNames(channels)

ans =

 

  1×6 cell array

 

  Columns 1 through 4

 

    'hen'    'Yorkshire terrier'    'Shetland sheepdog'    'fountain'

 

  Columns 5 through 6

 

    'theater curtain'    'geyser'

 

Generate detailed images that strongly activate these classes.

I = deepDreamImage(net,layer,channels, ...

    'Verbose',false, ...

    'NumIterations',50);

 

figure

montage(I)

name = net.Layers(layer).Name;

title(\['Layer ',name,' Features'\])

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/VisualizeConvolutionalNeuralNetworkLayersExample\_08.png](images/00036.jpeg)

# 4.3 Train a Convolutional Neural Network Using Data in ImageDatastore

 

Load the data as an ImageDatastore object.

digitDatasetPath = fullfile(matlabroot,'toolbox','nnet','nndemos',...

    'nndatasets','DigitDataset');

digitData = imageDatastore(digitDatasetPath,...

        'IncludeSubfolders',true,'LabelSource','foldernames');

The data store contains 10000 synthetic images of digits 0-9. The images are generated by applying random transformations to digit images created using different fonts. Each digit image is 28-by-28 pixels.

Display some of the images in the datastore.

figure;

perm = randperm(10000,20);

for i = 1:20

    subplot(4,5,i);

    imshow(digitData.Files{perm(i)});

end

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/ConstructAndTrainAConvolutionalNeuralNetworkExample\_01.png](images/00015.jpeg)

Check the number of images in each digit category.

digitData.countEachLabel

ans =

 

  10×2 table

 

    Label    Count

    \_\_\_\_\_    \_\_\_\_\_

 

    0        1000 

    1        1000 

    2        1000 

    3        1000 

    4        1000 

    5        1000 

    6        1000 

    7        1000 

    8        1000 

    9        1000 

 

The data contains an equal number of images per category.

Divide the data set so that each category in the training set has 750 images and the testing set has the remaining images from each label.

trainingNumFiles = 750;

rng(1) % For reproducibility

\[trainDigitData,testDigitData\] = splitEachLabel(digitData,...

                                  trainingNumFiles,'randomize');

splitEachLabel splits the image files in digitData into two new datastores, trainDigitData and testDigitData.

Define the convolutional neural network architecture.

layers = \[imageInputLayer(\[28 28 1\]);

          convolution2dLayer(5,20);

          reluLayer();

          maxPooling2dLayer(2,'Stride',2);

          fullyConnectedLayer(10);

          softmaxLayer();

          classificationLayer()\];

Set the options to default settings for the stochastic gradient descent with momentum. Set the maximum number of epochs at 20, and start the training with an initial learning rate of 0.001.

options = trainingOptions('sgdm','MaxEpochs',20,...

        'InitialLearnRate',0.0001);

Train the network.

convnet = trainNetwork(trainDigitData,layers,options);

Training on single GPU.

Initializing image normalization.

|=========================================================================================|

|     Epoch    |   Iteration  | Time Elapsed |  Mini-batch  |  Mini-batch  | Base Learning|

|              |              |  (seconds)   |     Loss     |   Accuracy   |     Rate     |

|=========================================================================================|

|            1 |            1 |         0.06 |       3.0845 |       13.28% |       0.0001 |

|            1 |           50 |         0.72 |       1.0945 |       65.63% |       0.0001 |

|            2 |          100 |         1.43 |       0.7276 |       74.22% |       0.0001 |

|            3 |          150 |         2.14 |       0.4743 |       83.59% |       0.0001 |

|            4 |          200 |         2.85 |       0.3086 |       91.41% |       0.0001 |

|            5 |          250 |         3.56 |       0.2324 |       92.97% |       0.0001 |

|            6 |          300 |         4.25 |       0.1542 |       97.66% |       0.0001 |

|            7 |          350 |         4.95 |       0.1315 |       97.66% |       0.0001 |

|            7 |          400 |         5.63 |       0.0944 |       96.09% |       0.0001 |

|            8 |          450 |         6.33 |       0.0668 |       98.44% |       0.0001 |

|            9 |          500 |         7.02 |       0.0458 |       99.22% |       0.0001 |

|           10 |          550 |         7.73 |       0.0544 |      100.00% |       0.0001 |

|           11 |          600 |         8.43 |       0.0660 |       99.22% |       0.0001 |

|           12 |          650 |         9.12 |       0.0338 |      100.00% |       0.0001 |

|           13 |          700 |         9.82 |       0.0340 |      100.00% |       0.0001 |

|           13 |          750 |        10.51 |       0.0370 |       99.22% |       0.0001 |

|           14 |          800 |        11.21 |       0.0264 |      100.00% |       0.0001 |

|           15 |          850 |        11.91 |       0.0182 |      100.00% |       0.0001 |

|           16 |          900 |        12.61 |       0.0234 |      100.00% |       0.0001 |

|           17 |          950 |        13.32 |       0.0224 |      100.00% |       0.0001 |

|           18 |         1000 |        14.01 |       0.0160 |      100.00% |       0.0001 |

|           19 |         1050 |        14.70 |       0.0233 |      100.00% |       0.0001 |

|           19 |         1100 |        15.39 |       0.0245 |      100.00% |       0.0001 |

|           20 |         1150 |        16.09 |       0.0154 |      100.00% |       0.0001 |

|           20 |         1160 |        16.23 |       0.0146 |      100.00% |       0.0001 |

|=========================================================================================|

Run the trained network on the test set that was not used to train the network and predict the image labels (digits).

YTest = classify(convnet,testDigitData);

TTest = testDigitData.Labels;

Calculate the accuracy.

accuracy = sum(YTest == TTest)/numel(TTest)

accuracy =

 

    0.9852

 

Accuracy is the ratio of the number of true labels in the test data matching the classifications from classify, to the number of images in the test data. In this case about 98.5% of the digit estimations match the true digit values in the test set.

## 4.3.1 Construct and Train a Convolutional Neural Network

Load the training data.

load lettersTrainSet

XTrain contains 1500 28-by-28 grayscale images of the letters A, B, and C in a 4-D array. There are equal numbers of each letter in the data set. TTrain contains the categorical array of the letter labels.

Display some of the letter images.

figure;

perm = randperm(1500,20);

for i = 1:20

    subplot(4,5,i);

    imshow(XTrain(:,:,:,perm(i)));

end

![Descripción: http://es.mathworks.com/help/examples/nnet/win64/UseDataInImageDatastoreForTrainingCNNExample\_01.png](images/00037.jpeg)

Define the convolutional neural network architecture.

layers = \[imageInputLayer(\[28 28 1\]);

          convolution2dLayer(5,16);

          reluLayer();

          maxPooling2dLayer(2,'Stride',2);

          fullyConnectedLayer(3);

          softmaxLayer();

          classificationLayer()\];

Set the options to default settings for the stochastic gradient descent with momentum.

options = trainingOptions('sgdm');

Train the network.

rng('default') % For reproducibility

net = trainNetwork(XTrain,TTrain,layers,options);

Training on single GPU.

Initializing image normalization.

|=========================================================================================|

|     Epoch    |   Iteration  | Time Elapsed |  Mini-batch  |  Mini-batch  | Base Learning|

|              |              |  (seconds)   |     Loss     |   Accuracy   |     Rate     |

|=========================================================================================|

|            1 |            1 |         3.55 |       1.0994 |       27.34% |       0.0100 |

|            5 |           50 |         4.66 |       0.2175 |       98.44% |       0.0100 |

|           10 |          100 |         5.42 |       0.0238 |      100.00% |       0.0100 |

|           14 |          150 |         6.18 |       0.0108 |      100.00% |       0.0100 |

|           19 |          200 |         6.93 |       0.0088 |      100.00% |       0.0100 |

|           23 |          250 |         7.68 |       0.0048 |      100.00% |       0.0100 |

|           28 |          300 |         8.44 |       0.0035 |      100.00% |       0.0100 |

|           30 |          330 |         8.88 |       0.0052 |      100.00% |       0.0100 |

|=========================================================================================|

Run the trained network on a test set that was not used to train the network and predict the image labels (letters).

load lettersTestSet;

XTest contains 1500 28-by-28 grayscale images of the letters A, B, and C in a 4-D array. There is again equal numbers of each letter in the data set. TTest contains the categorical array of the letter labels.

YTest = classify(net,XTest);

Calculate the accuracy.

accuracy = sum(YTest == TTest)/numel(TTest)

accuracy =

 

    0.9273

 

**Input Arguments**

**imds — Images with labels for classification problems  
ImageDatastore object**

Images, specified as an ImageDatastore object with categorical labels. You can store data in ImageDatastorefor only classification problems.

ImageDatastore allows batch-reading of JPG or PNG image files using pre-fetching. If you use a custom function for reading the images, pre-fetching does not happen. For more information about this data type, see [ImageDatastore](http://es.mathworks.com/help/matlab/ref/imagedatastore-object.html).

**X — Images  
4-D numeric array**

 

Images, specified as a 4-D numeric array. The first three dimensions must be the height, width, and channels, and the last dimension must index the individual images.

If there are NaNs in the array, they are propagated through the training, however, in most cases the training fails to converge.

**Data Types: **single | double

**Y — Responses for a classification or a regression problem  
array of categorical responses | numeric matrix | 4-D numeric array**

 

Responses for a classification or a regression problem, specified as one of the following:

*   For a classification problem, Y is a categorical vector containing the image labels. 
*   For a regression problem, Y can be an 

*   *n*\-by-*r* numeric matrix, where *n* is the number of observations and *r* is the number of responses
*   *h*\-by-*w*\-by-*c*\-by-*n* numeric array, where *n* is the number of observations and *h*\-by-*w*\-by-*c* is the size of a single response.

Responses must not contain NaNs.

**Data Types: **categorical | double

**tbl — Input data  
table**

Input data, specified as a table. tbl must contain the predictors in the first column as either absolute or relative image paths or images. The type and location of the responses depend on the problem:

·        For a classification problem, the response must be a categorical variable containing labels for the images. If the name of the response variable is not specified in the call to trainNetwork, the responses must be in the second column. If the responses are in a different column of tbl, then you must specify the response variable name using the [responseName](http://es.mathworks.com/help/nnet/ref/trainnetwork.html#inputarg_responseName) positional argument.

·        For a regression problem, the responses must be numerical values in the column or columns after the first one. The responses can be either in multiple columns as scalars or in a single column as numeric vectors or cell arrays containing numeric 3-D arrays. When you do not specify the name of the response variable or variables, trainNetwork accepts the remaining columns of tbl as the response variables. You can specify the response variable names using the responseName positional argument.

Responses must not contain NaNs. If there are NaNs in the predictor data, they are propagated through the training, however, in most cases the training fails to converge.

 

**Data Types: **table

**responseName — Name of response variable for a regression and classification problem  
character vector**

 

Name of the response variable for a regression and classification problem, specified as a character vector that shows the name of the variable containing the responses in [tbl](http://es.mathworks.com/help/nnet/ref/trainnetwork.html#inputarg_tbl).

 

**Data Types: **char

**responseNames — Names of response variables for a regression problem  
cell array**

 

Names of the response variables for a regression problem, specified as a cell array of character vectors that show the names of the variables containing the responses in [tbl](http://es.mathworks.com/help/nnet/ref/trainnetwork.html#inputarg_tbl).

 

**Data Types: **cell

**layers — An array of network layers  
Layer object**

 

An array of network layers, specified as a [Layer](http://es.mathworks.com/help/nnet/ref/layer-class.html) object. layers can be the layers of a checkpoint network trainNetwork previously saved. In that case, enter the network layers using the dot notation. For example, if the name of the checkpoint network is net, then enter net.Layers for the layers argument.

**options — Training options  
TrainingOptionsSGDM object**

 

Training options, specified as a TrainingOptionsSGDM object returned by the [trainingOptions](http://es.mathworks.com/help/nnet/ref/trainingoptions.html) function. SGDM stands for the stochastic gradient descent with momentum solver.

**Output Arguments**

**trainedNet — Trained network  
SeriesNetwork object**

 

Trained network, returned as a SeriesNetwork object.

**traininfo — Information on the training  
structure**

Information on the training, returned as a structure with the following fields.

·        TrainingLoss — Loss function value at each iteration

·        TrainingAccuracy — Training accuracy at each iteration if network is a classification network

·        TrainingRMSE — Training RMSE at each iteration if network is a regression network

·        BaseLearnRate — The learning rate at each iteration

# 4.4 Label Images for Classification Model Training

 

## 4.4.1 Description

The Training Image Labeler provides an easy way to label objects in images. Using this app, you can:

·        Interactively specify rectangular regions of interest (ROIs) for multiple categories of objects.

·        Export ROIs for training or evaluating an object detector.

·        Train an object detector using the trainCascadeObjectDetector function.

## 4.4.2 Open the Training Image Labeler

·        MATLAB^® Toolstrip: Open the Apps tab, under **Image Processing and Computer Vision**, click the app icon.

·        MATLAB command prompt: Enter trainingImageLabeler

## 4.4.3 App Controls

You can add an unlimited number of images to the **Data Browser**. You can then select, remove, and create ROIs, and save your session. When you are done, you can export the ROI information to an XML file.

**![Descripción: http://es.mathworks.com/help/vision/ug/trainingimagelabeler\_addimages.png](images/00038.gif) Add Images**

Use the **Add Images** icon to select and add images to the **Data Browser**. You can add more images at any time during your editing session. The source images remain in the folder where they were originally located. The app does not make copies of the original images or move them. If you rotate the images in the **Data Browser**, the app overwrites the images in their original location with the modified orientation.

The app provides a list of image thumbnails that you loaded for the session. Next to each thumbnail, you see the file name and number of ROIs created in that image.

![Descripción: http://es.mathworks.com/help/vision/ug/trainingimagelabeler\_filenamesandrois.png](images/00039.gif)

**![Descripción: http://es.mathworks.com/help/vision/ug/trainingimagelabeler\_roi.png](images/00040.gif) Specify Regions of Interest**

After you load images, you can delineate ROIs. You can switch between images and continue creating ROIs. The app allows you to create ROI Labels for multiple object categories. Each ROI label has a name and a color. First create the labels and then draw the ROIs in images.

**Create labels**:

1.                Click the **Add ROI** label ![Descripción: http://es.mathworks.com/help/vision/ug/trainingimagelabeler\_addroilabel.png](images/00041.gif) for each object category.

2.                Name each ROI label and select its color.

3.                Select the category from the **ROI labels** list you created.

4.                Draw an ROI by dragging the cursor over the object in the image.

*   To modify the size of an ROI, click either the corner or side grips. To keep the aspect ratio of the ROI while changing its size, hold **Shift**.
*   To copy and paste an ROI, click within its border to select it. You can select one or more ROIs to move or to copy and paste.
*   To delete an ROI, click the red x in its upper-right corner.
*   If the object of interest fills the entire image, right-click the image and select **Add full image ROI** from the menu.

To show or hide the label names in the currently displayed image, select **Show ROI Labels**.

![Descripción: http://es.mathworks.com/help/vision/ug/trainingimagelabeler\_roistopsign.png](images/00042.gif)

You can also use the following common shortcuts:

·                  **Ctrl+C** to copy

·                  **Ctrl+V** to paste

·                  **Ctrl+X** to cut

**![Descripción: http://es.mathworks.com/help/vision/ug/trainingimagelabeler\_removerotatesort.png](images/00043.gif) Remove, Rotate, and Sort Images**

You can remove, rotate, or sort the images. Right-click any image to access these options. To select multiple images, press **Ctrl**+click. To select consecutive images, press **Shift**+click. To sort images by the number of ROIs, from least amount of ROIs contained in each image, right-click any image and select **Sort list by number of ROIs**.

**![Descripción: http://es.mathworks.com/help/vision/ug/trainingimagelabeler\_newsession.png](images/00044.gif) New Session**

When you start a new session, you can save the current session before clearing it.

**![Descripción: http://es.mathworks.com/help/vision/ug/trainingimagelabeler\_opensession.png](images/00045.gif) Open Session**

You can open a new session to replace or add to the current session. The app loads the selected MAT session file. To replace your current session, from the **Open Session** options, select **Open an existing session**. To combine multiple sessions, select **Add session to the current session**.

**![Descripción: http://es.mathworks.com/help/vision/ug/trainingimagelabeler\_savesession.png](images/00046.gif) Save Session**

You can name and save your session to a .MAT file. The default name is LabelingSession. The saved session file contains all the required information to reload the session in the state that you saved it. It contains the paths to the original images, the coordinates for the ROI bounding boxes for each image, file names, and logical information to record the state of the files.

**![Descripción: http://es.mathworks.com/help/vision/ug/trainingimagelabeler\_export.png](images/00047.gif) Export ROIs**

When you click **Export ROIs**, the app exports the ROI information to the MATLAB workspace as an *M*\-by-*N* table containing the image file names and the ROIs. The image file names are stored in the first column of the table. The subsequent columns contain the ROIs for each category.

![Descripción: http://es.mathworks.com/help/vision/ug/trainingimagelabeler\_exported.png](images/00048.gif)

If you only have one ROI label, the app gives you the additional option to export the ROIs as a struct array. The structure contains two fields. One field stores the image file location and the other field stores the corresponding ROI information for each image.

**![Descripción: http://es.mathworks.com/help/vision/ug/trainingimagelabeler\_importrois.png](images/00049.gif)Import ROIs**

You can import ROIs created using another labeling method. The ROIs must be stored in a table using the same format as the ROIs exported by the app. The table can be a variable in the MATLAB workspace, or it can be saved as a MAT file.

# 4.5 Training Image Labeler

 

Label images for training a classifier

 

## 4.5.1 Description

 

![](images/00050.jpeg)

The **Training Image Labeler** app allows you to interactively specify rectangular Regions of Interest (ROIs).

 

## 4.5.2 Open the Training Image Labeler App

·        MATLAB^® Toolstrip: On the **Apps** tab, under **Image Processing and Computer Vision**, click the app icon.

·        MATLAB command prompt: Enter `trainingImageLabeler`.

`trainingImageLabeler` invokes an app for labeling ground truth data in images. This app allows you to interactively specify rectangular Regions of Interest (ROIs). The ROIs define locations of objects, which are used to train a classifier. It outputs training data in a format supported by the [`trainCascadeObjectDetector`](http://es.mathworks.com/help/vision/ref/traincascadeobjectdetector.html) function. The function trains a model to use with the [`vision.CascadeObjectDetector`](http://es.mathworks.com/help/vision/ref/vision.cascadeobjectdetector-class.html) detector.

` `

`trainingImageLabeler(imageFolder)` invokes the app and immediately loads the images from `imageFolder`.

` `

`trainingImageLabeler(sessionFile)` invokes the app and immediately loads a saved image labeler session. `sessionFile` contains the path to the MAT file of the saved session.

` `

`trainingImageLabeler(imgDataStore)` invokes the app and immediately loads the image from an [`imageDatastore`](http://es.mathworks.com/help/matlab/ref/imagedatastore.html) object.

` `

`trainingImageLabeler CLOSE` closes all open apps.

 

 

  

5Chapter 5

DEEP LEARNING. OBJECT DETECTION AND RECOGNITION 

# 5.1 INTRODUCTION

#  

Computer Vision System Toolbox supports several approaches for image classification, object detection, and recognition, including:

·        Deep learning and Convolutional neural networks (CNNs)

·        Bag of features

·        Template matching

·        Blob analysis

·        Viola-Jones algorithm

A CNN is a popular deep learning architecture that automatically learns useful feature representations directly from image data. Bag of features encodes image features into a compact representation suitable for image classification and image retrieval. Template matching uses a small image, or template, to find matching regions in a larger image. Blob analysis uses segmentation and blob properties to identify objects of interest. The Viola-Jones algorithm uses Haar-like features and a cascade of classifiers to identify objects, including faces, noses, and eyes. You can train this classifier to recognize other objects.

 

 

## 5.1.1 Deep Learning for Computer Vision

Deep Learnig for Computer Vision perform classification, object detection, and transfer learning using convolutional neural networks (CNNs, or ConvNets)

Convolutional neural networks (CNNs, or ConvNets) are essential tools for deep learning, and are especially useful for image classification, object detection, and recognition tasks. CNNs are implemented as a series of interconnected layers. The layers are made up of repeated blocks of convolutional, ReLU (rectified linear units), and pooling layers. The convolutional layers convolve their input with a set of filters. The filters were automatically learned during network training. The ReLU layer adds nonlinearity to the network, which enables the network to approximate the nonlinear mapping between image pixels and the semantic content of an image. The pooling layers downsample their inputs and help consolidate local image features.

 
| **Note:**   Convolutional neural networks require Neural Network Toolbox™. Training and prediction are supported on a CUDA^®\-capable GPU with a compute capability of 3.0 or higher. Use of a GPU is recommended and requires Parallel Computing Toolbox™. |
| --- |

 

You can construct a CNN architecture, train a network, and use the trained network to predict class labels or detect objects. You can also extract features from a pretrained network, and use these features to train a classifier. Additionally, you can perform transfer learning which retrains the CNN on new data.

[![](images/00051.gif)](http://www.mathworks.com/help/vision/examples/image-category-classification-using-deep-learning.html)

 

 

## 5.1.2 Deep Learning And Convulitional Neural Network

Deep Learning construct and train convolutional neural networks (CNNs, ConvNets) for classification and regression and autoencoder neural networks for learning features

Deep learning uses neural networks to learn useful representations of features directly from data. If you have labeled data, perform supervised learning with convolutional neural networks (CNNs, ConvNets) for classification, regression, and transfer learning using pretrained networks. If you have unlabeled data, perform unsupervised learning with autoencoder neural networks for feature extraction..

Convolutional neural networks (ConvNets) are widely used tools for deep learning. They are specifically suitable for images as inputs, although they are also used for other applications such as text, signals, and other continuous responses. They differ from other types of neural networks in a few ways:

Convolutional neural networks are inspired from the biological structure of a visual cortex, which contains arrangements of simple and complex cells [\[1\]](http://www.mathworks.com/help/nnet/ug/introduction-to-convolutional-neural-networks.html#bvnobzh). These cells are found to activate based on the subregions of a visual field. These subregions are called receptive fields. Inspired from the findings of this study, the neurons in a convolutional layer connect to the subregions of the layers before that layer instead of being fully-connected as in other types of neural networks. The neurons are unresponsive to the areas outside of these subregions in the image.

These subregions might overlap, hence the neurons of a ConvNet produce spatially-correlated outcomes, whereas in other types of neural networks, the neurons do not share any connections and produce independent outcomes.

In addition, in a neural network with fully-connected neurons, the number of parameters (weights) can increase quickly as the size of the input increases. A convolutional neural network reduces the number of parameters with the reduced number of connections, shared weights, and downsampling.

A ConvNet consists of multiple layers, such as convolutional layers, max-pooling or average-pooling layers, and fully-connected layers.

The neurons in each layer of a ConvNet are arranged in a 3-D manner, transforming a 3-D input to a 3-D output. For example, for an image input, the first layer (input layer) holds the images as 3-D inputs, with the dimensions being height, width, and the color channels of the image. The neurons in the first convolutional layer connect to the regions of these images and transform them into a 3-D output. The hidden units (neurons) in each layer learn nonlinear combinations of the original inputs, which is called feature extraction [\[2\]](http://www.mathworks.com/help/nnet/ug/introduction-to-convolutional-neural-networks.html#bvotzdh). These learned features, also known as activations, from one layer become the inputs for the next layer. Finally, the learned features become the inputs to the classifier or the regression function at the end of the network.

The architecture of a ConvNet can vary depending on the types and numbers of layers included. The types and number of layers included depends on the particular application or data. For example, if you have categorical responses, you must have a classification function and a classification layer, whereas if your response is continuous, you must have a regression layer at the end of the network. A smaller network with only one or two convolutional layers might be sufficient to learn a small number of gray scale image data. On the other hand, for more complex data with millions of colored images, you might need a more complicated network with multiple convolutional and fully connected layers.

You can concatenate the layers of a convolutional neural network in MATLAB^® in the following way:

layers = \[imageInputLayer(\[28 28 1\])

          convolution2dLayer(5,20)

          reluLayer

          maxPooling2dLayer(2,'Stride',2)

          fullyConnectedLayer(10)

          softmaxLayer

          classificationLayer\];

After defining the layers of your network, you must specify the training options using the [trainingOptions](http://www.mathworks.com/help/nnet/ref/trainingoptions.html) function. For example,

options = trainingOptions('sgdm');

Then, you can train the network with your training data using the [trainNetwork](http://www.mathworks.com/help/nnet/ref/trainnetwork.html) function. The data, layers, and training options become the inputs to the training function. For example,

convnet = trainNetwork(data,layers,options);

# 5.2 Create New Deep Network

 

## 5.2.1 Specify Layers of Convolutional Neural Network

The first step of creating and training a new convolutional neural network (ConvNet) is to define the network layers. This topic explains the details of ConvNet layers, and the order they appear in a ConvNet.

The architecture of a ConvNet can vary depending on the types and numbers of layers included. The types and number of layers included depends on the particular application or data. For example, if you have categorical responses, you must have a softmax layer and a classification layer, whereas if your response is continuous, you must have a regression layer at the end of the network. A smaller network with only one or two convolutional layers might be sufficient to learn on a small number of gray scale image data. On the other hand, for more complex data with millions of colored images, you might need a more complicated network with multiple convolutional and fully connected layers.

You can define the layers of a convolutional neural network in MATLAB^® in an array format, for example,

layers = \[imageInputLayer(\[28 28 1\])

          convolution2dLayer(5,20)

          reluLayer

          maxPooling2dLayer(2,'Stride',2)

          fullyConnectedLayer(10)

          softmaxLayer

          classificationLayer\];

layers is an array of Layer objects. layers becomes an input for the training function trainNetwork.

## 5.2.2 Image Input Layer

Image input layer defines the size of the input images of a convolutional neural network and contains the raw pixel values of the images. You can add an input layer using the imageInputLayer function. Specify your image size in the inputSize argument. Size of an image corresponds to the height, weight, and the number of color channels of that image. For example, for a gray scale image, the number of channels would be 1, and for a color image it is 3.

In this layer, you can also specify the network to perform data augmentation, such as random flipping or cropping of the data, or data transformation by subtracting the mean of the image from the pixel values in the training set. The purpose of augmentation and normalization transforms is to reduce overfitting, which might occur with especially larger networks.

## 5.2.3 Convolutional Layer

**Filters and Stride:** A convolutional layer consists of neurons that connect to subregions of the input images or the outputs of the layer before it. A convolutional layer learns the features localized by these regions while scanning through an image. You can specify the size of these regions using the filterSize input argument in the call to convolution2dLayer function.

For each region, the trainNetwork function computes a dot product of the weights and the input, and then adds a bias term. A set of weights that are applied to a region in the image is called a *filter*. The filter moves along the input image vertically and horizontally, repeating the same computation for each region, i.e., convolving the input. The step size with which it moves is called a *stride*. You can specify this step size with the Stride name-value pair argument. These local regions that the neurons connect to might overlap depending on the filterSize and 'Stride'.

The number of weights used for a filter is *h*\**w*\**c*, where *h* is the height, and *w* is the width of the filter size, and *c* is the number of channels in the input (for example, if the input is a color image, the number of color channels is 3). The number of filters determines the number of channels in the output of a convolutional layer. Specify the number of filters using the numFilters argument in the call to convolution2dLayer.

**Feature Maps:** As a filter moves along the input, it uses the same set of weights and bias for the convolution, forming a *feature map*. Hence, the number of feature maps a convolutional layer has is equal to the number of filters (number of channels). Each feature map has a different set of weights and a bias. So, the total number of parameters in a convolutional layer is ((*h*\**w*\**c* + 1)\**Number of Filters*), where 1 is for the bias.

**Zero Padding:** You can also apply zero padding to input image borders vertically and horizontally using the 'Padding' name-value pair argument. Padding is basically adding rows or columns of zeros to the borders of an image input. It helps you control the output size of the layer it is added to.

**Output Size:** The output height and width of a convolutional layer is (*Input Size* – *Filter Size* + 2\**Padding*)/*Stride* + 1. This value must be an integer for the whole image to be fully covered. If the combination of these parameters does not lead the image to be fully covered, the software by default ignores the remaining part of the image along the right and bottom edge in the convolution.

**Number of Neurons:** The product of the output height and width gives the total number of neurons in a feature map, say *Map Size*. The total number of neurons (output size) in a convolutional layer, then, is *Map Size*\**Number of Filters*.

For example, suppose that the input image is a 28-by-28-by-3 color image. For a convolutional layer with 16 filters, and a filter size of 8-by-8, the number of weights per filter is 8\*8\*3 = 192, and the total number of parameters in the layer is (192+1) \* 16 = 3088. Assuming stride is 4 in each direction and there is no zero padding, the total number of neurons in each feature map is 6-by-6 ((28 – 8+0)/4 + 1 = 6). Then, the total number of neurons in the layer is 6\*6\*16 = 256.

**Learning Parameters:** You can also adjust the learning rates and regularization parameters for this layer using the related name-value pair arguments while defining the convolutional layer. If you choose not to adjust them, trainNetwork uses the global training parameters defined by trainingOptions function.

A convolutional neural network can consists of one or multiple convolutional layers. The number of convolutional layers depends on the amount and complexity of the data.

The results from the neurons of a convolutional layer usually pass through some form of nonlinearity. Neural Network Toolbox™ uses rectified linear units (ReLU) function for this purpose. Each convolutional layer can be followed by ReLU layer or a pooling layer.

## 5.2.4 ReLU Layer

A convolutional layer is usually followed by a nonlinear activation function. In MATLAB, it is a rectified linear unit (ReLU) function, specified by a ReLU layer. You can specify the ReLU layer using the [reluLayer](http://www.mathworks.com/help/nnet/ref/relulayer.html) function. It performs a threshold operation to each element, where any input value less than zero is set to zero. The ReLU layer does not change the size of its input.

## 5.2.5 Cross Channel Normalization (Local Response Normalization) Layer

This layer performs a channel-wise local response normalization. It usually follows the ReLU activation layer. You can specify this layer using the [crossChannelNormalizationLayer](http://www.mathworks.com/help/nnet/ref/crosschannelnormalizationlayer.html) function. This layer replaces each element with a normalized value it obtains using the elements from a certain number of neighboring channels (elements in the normalization window). 

You must specify the size of normalization window using the windowChannelSize argument in the call to crossChannelNormalizationLayer argument. You can also specify the hyperparameters using the Alpha, Beta, and K name-value pair arguments.

Note that, the previous normalization formula is slightly different than what is presented previously. You can obtain the equivalent formula by multiplying the alpha value by the windowChannelSize.

## 5.2.6 Max- and Average-Pooling Layers

Max- and average-pooling layers follow the convolutional layers for down-sampling, hence, reducing the number of connections to the following layers (usually a fully-connected layer). They do not perform any learning themselves, but reduce the number of parameters to be learned in the following layers. They also help reduce overfitting. You can specify these layers using the [maxPooling2dLayer](http://www.mathworks.com/help/nnet/ref/maxpooling2dlayer.html) and [averagePooling2dLayer](http://www.mathworks.com/help/nnet/ref/averagepooling2dlayer.html).

Max-pooling layer returns the maximum values of rectangular regions of its input. The size of the rectangular regions are determined by the poolSize to maxPoolingLayer. For example, if poolSize is \[2,3\], the software returns the maximum value of regions of height 2 and width 3.

Similarly, the average-pooling layer outputs the average values of rectangular regions of its input. The size of the rectangular regions is determined by the poolSize in the call to averagePoolingLayer. For example, if poolSize is \[2,3\], the software returns the average value of regions of height 2 and width 3. The maxPoolingLayer and averagepoolingLayer functions scan through the input horizontally and vertically in step sizes you can specify using the Stride argument in the call to either function. If the poolSize is smaller than or equal to Stride, then the pooling regions do not overlap.

For nonoverlapping regions (poolSize and Stride are equal), if the input to the pooling layer is *n*\-by-*n*, and the pooling region size is *h*\-by-*h*, then the pooling layer down-samples the regions by *h* [\[6\]](http://www.mathworks.com/help/nnet/ug/layers-of-a-convolutional-neural-network.html#bu741xw). That is, the output of a max- or average-pooling layer for one channel of a convolutional layer is *n*/*h*\-by-*n*/*h*. For overlapping regions, the output of a pooling layer is (*Input Size* – *Pool Size* + 2\**Padding*)/*Stride* + 1.

## 5.2.7 Dropout Layer

A dropout layer randomly sets the layer's input elements to zero with a given probability. You can specify the dropout layer using the [dropoutLayer](http://www.mathworks.com/help/nnet/ref/dropoutlayer.html) function.

Although the output of a dropout layer is equal to its input, this operation corresponds to temporarily dropping a randomly chosen unit and all of its connections from the network during training. So, for each new input element, trainNetwork randomly selects a subset of neurons, forming a different layer architecture. These architectures use common weights, but because the learning does not depend on specific neurons and connections, the dropout layer might help prevent overfitting [\[7\]](http://www.mathworks.com/help/nnet/ug/layers-of-a-convolutional-neural-network.html#bvk8642), [\[2\]](http://www.mathworks.com/help/nnet/ug/layers-of-a-convolutional-neural-network.html#bvnojz7-1). Similar to max- or average-pooling layers, no learning takes place in this layer.

## 5.2.8 Fully Connected Layer

The convolutional (and down-sampling) layers are followed by one or more fully connected layers. You can specify a fully connected layer using the [fullyConnectedLayer](http://www.mathworks.com/help/nnet/ref/fullyconnectedlayer.html)function.

As the name suggests, all neurons in a fully connected layer connect to the neurons in the layer previous to it. This layer combines all of the features (local information) learned by the previous layers across the image to identify the larger patterns. For classification problems, the last fully connected layer combines them to classify the images. That is why, the OutputSize parameter in the last fully connected layer is equal to the number of classes in the target data. For regression problems, the output size must be equal to the number of response variables.

You can also adjust the learning rate and the regularization parameters for this layer using the related name-value pair arguments while defining the fully connected layer. If you choose not to adjust them, trainNetwork uses the global training parameters defined by trainingOptions function.

## 5.2.9 Softmax and Classification Layers

For classification problems, a softmax layer and then a classification layer must follow the final fully connected layer. You can specify these layers using the [softmaxLayer](http://www.mathworks.com/help/nnet/ref/softmaxlayer.html) and [classificationLayer](http://www.mathworks.com/help/nnet/ref/classificationlayer.html) functions, respectively.

The softmax function is also known as the *normalized exponential* and can be considered the multi-class generalization of the logistic sigmoid function.

A classification output layer must follow the softmax layer. In the classification output layer, trainNetwork takes the values from the softmax function and assigns each input to one of the *k* mutually exclusive classes using the cross entropy function for a 1-of-*k* coding scheme 

## 5.2.10 Regression Layer

You can also use ConvNets for regression problems, where the target (output) variable is continuous. In such cases, a regression output layer must follow the final fully connected layer. You can specify the regression layer using the [regressionLayer](http://www.mathworks.com/help/nnet/ref/regressionlayer.html) function. The default activation function for the regression layer is the mean squared error

## 5.2.11 Set Up Parameters and Train Convolutional Neural Network

After you define the layers of your network, next step is to set up the training options for the network. You can use the trainingOptions function to set up the global training parameters. trainNetwork then uses these options to perform the training. trainingOptions saves these options as an instance of a TrainingOptionsSGDM object and you must provide it as an input argument to trainNetwork. For example,

opts = trainingOptions('sgdm');

convnet = trainNetwork(data,layers,opt);

The learning layers convolution2dLayer and fullyConnectedLayer also have a few options to adjust the learning parameters for those layers. See below for more details.

## 5.2.12 Set Up Training Parameters Using trainingOptions

**Specify Solver and Maximum Number of Epochs**

trainNetwork uses the Stochastic Gradient Descent with Momentum (SGDM) as the optimization algorithm. You must specify 'sgdm' as the SolverName in the call to trainingOptions. SGDM updates the weights and biases (parameters) by taking small steps in the direction of the negative gradient of the loss function, in such a way to minimize the loss. It updates the parameters using a subset of the data every time. This subset is called a *mini-batch*. You can specify the size of this subset using the 'MiniBatchSize' name-value pair argument in trainingOptions.

Each evaluation of the gradient using a mini-batch is called an *iteration*. And a full pass through the whole data set is called an *epoch*. The maximum number of epochs to run the training for is also a parameter you can specify. Use the 'MaxEpochs' name-value pair argument in the call to trainingOptions. The default value is 30, but you might choose a smaller number of epochs for small networks, or for fine-tuning and transfer learning, where most of the learning is done previously.

The momentum parameter is a way to prevent the oscillation of the stochastic gradient descent algorithm along the path of steepest descent. As a rule of thumb, the default value for this parameter is 0.9. However, you can change this value using the 'Momentum' name-value pair argument.

**Specify and Modify Learning Rate**

You can specify the global learning rate using the 'InitialLearnRate' name-value pair argument in trainingOptions. The default rate is 0.01, but you might want to choose a smaller value if you are performing transfer learning. By default, trainNetwork uses this value throughout the whole training process unless you choose to change this value every certain number of epochs by multiplying with a factor. Instead of using a small fixed learning rate through the entire training, choosing a larger learning rate at the beginning of training and gradually reducing this value during optimization might help shorten the training time, while enabling smaller steps towards to optimum value as the training progresses, hence a finer search towards the end of the training.

If you would like to gradually reduce the learning rate, use the 'LearnRateSchedule','piecewise' name-value pair argument. Once you choose this option, trainNetwork by default multiplies the initial learning rate by a factor of 0.1 every 10 epochs. However, you have the option of specifying the factor by which to reduce the initial learning rate and the number of epochs using the 'LearnRateDropFactor' and 'LearnRateDropPeriod' name-value pair arguments, respectively.

**Select Hardware Resource**

If there is an available GPU, trainNetwork by default uses a GPU for training. If there is no available GPU, it uses a CPU. Alternatively, you can specify the execution environment you want using the 'ExecutionEnvironment' name-value pair argument. You can choose to use a single CPU ('cpu'), multiple CPU cores ('parallel'), a single GPU ('gpu'), or multiple-GPUs ('multiple-gpu'). All options other than 'cpu' require Parallel Computing Toolbox™. Training on a GPU requires a CUDA-enabled GPU with compute capability 3.0 or higher.

 

**Save Checkpoint Networks and Resume Training**

Neural Network Toolbox™ lets you periodically save networks as .mat files after each epoch during training. This is especially important when you have a large network or a large data set and training takes a long time. If the training gets interrupted for some reason, you can resume training from the last saved checkpoint network. If you want trainNetwork to save checkpoint networks, then you must specify the name of the path using the CheckpointPath name-value pair argument in the call to trainingOptions. If the path you specify is wrong, then trainingOptions returns an error.

trainNetwork automatically assigns unique names to these checkpoint network files. For example, convnet\_checkpoint\_\_351\_\_2016\_11\_09\_\_12\_04\_23.mat, where 351 is the iteration number, 2016\_11\_09 is the date and 12\_04\_21 is the time trainNetwork saves the network. You can load any of these by double clicking on them or typing, for example,

load convnet\_checkpoint\_\_351\_\_2016\_11\_09\_\_12\_04\_23.mat

in the command line. You can then resume training by using the layers of this network in the call to trainNetwork, for example,

trainNetwork(Xtrain,Ytrain,net.Layers,options)

You must manually specify the training options and the input data as the checkpoint network does not contain this information.

 

For a full list of optional name-value pair arguments, see the [trainingOptions](http://www.mathworks.com/help/nnet/ref/trainingoptions.html) function reference page.

## 5.2.13 Set Up Parameters in Convolutional and Fully Connected Layers

You have the option to set the learning parameters different than the global values specified by trainingOptions in a certain convolutional and/or fully connected layer. You can specify a value for the BiasLearnRateFactor or the WeightLearnRateFactor name-value pair in the call to convolution2dLayer or fullyConnectedLayer functions to adjust the learning rate for the biases and weights. The trainNetwork function multiplies the learning rate you specify in the trainingOptions function with these factors. Similarly, you can also specify the L[2] regularizer parameter for the weights and biases in these layers using the BiasL2Regularizer and WeightL2Regularizer name-value pair arguments. trainNetwork function then multiplies the L[2] regularizer values you specify in the trainingOptions function with these factors.

## 5.2.14 Initialize Weights in Convolutional and Fully Connected Layers

The default for the initial weights for the convolutional and fully connected layers follow a Gaussian distribution with mean 0 and standard deviation 0.01. The default for the initial bias is 0. You can manually change the initialization for the weights and bias after you specify these layers.

## 5.2.15 Train Your Network

After you specify the layers of your ConvNet and specify the training parameters, you can train your network using the training data. The data, layers, and the training options are all positional input arguments for the trainNetwork function. For example,

layers = \[imageInputLayer(\[28 28 1\])

          convolution2dLayer(5,20)

          reluLayer()

          maxPooling2dLayer(2,'Stride',2)

          fullyConnectedLayer(10)

          softmaxLayer()

          classificationLayer()\];

options = trainingOptions('sgdm');

convnet = trainNetwork(data,layers,options);

Training data can be in a matrix, table, or data store format. For more information, see the [trainNetwork](http://www.mathworks.com/help/nnet/ref/trainnetwork.html) function reference page.

# 5.3 Resume Training from a Checkpoint Network

 

This example shows how to save checkpoint networks while training a convolutional neural network and resume training from a previously saved network.

## 5.3.1 Load Sample Data

Load the sample data as a 4-D array.

\[XTrain,TTrain\] = digitTrain4DArrayData;

Display the size of XTrain.

size(XTrain)

ans =

 

          28          28           1        5000

 

digitTrain4DArrayData loads the digit training set as 4-D array data. XTrain is a 28-by-28-by-1-by-5000 array, where 28 is the height and 28 is the width of the images. 1 is the number of channels and 5000 is the number of synthetic images of handwritten digits. TTrain is a categorical vector containing the labels for each observation.

Display some of the images in XTrain .

figure;

perm = randperm(5000,20);

for i = 1:20

   subplot(4,5,i);

   imshow(XTrain(:,:,:,perm(i)));

end

![Descripción: http://www.mathworks.com/help/examples/nnet/win64/ResumeTrainingConvNetFromACheckpointNetworkExample\_01.png](images/00052.jpeg)

## 5.3.2 Define Layers of Network

Define the layers of the convolutional neural network.

layers = \[imageInputLayer(\[28 28 1\])

          convolution2dLayer(5,20)

          reluLayer()

          maxPooling2dLayer(2,'Stride',2)

          fullyConnectedLayer(10)

          softmaxLayer()

          classificationLayer()\];

## 5.3.3 Specify Training Options with Checkpoint Path and Train Network

Set the options to default settings for the stochastic gradient descent with momentum and specify the path for saving the checkpoint networks.

options = trainingOptions('sgdm','CheckpointPath','C:\\Temp\\cnncheckpoint');

Train the network.

convnet = trainNetwork(XTrain,TTrain,layers,options);

Training on single GPU.

Initializing image normalization.

|=========================================================================================|

|     Epoch    |   Iteration  | Time Elapsed |  Mini-batch  |  Mini-batch  | Base Learning|

|              |              |  (seconds)   |     Loss     |   Accuracy   |     Rate     |

|=========================================================================================|

|            1 |            1 |         0.02 |       2.3022 |        7.81% |       0.0100 |

|            2 |           50 |         0.63 |       2.2684 |       31.25% |       0.0100 |

|            3 |          100 |         1.22 |       1.5395 |       53.13% |       0.0100 |

|            4 |          150 |         1.81 |       1.4287 |       50.00% |       0.0100 |

|            6 |          200 |         2.43 |       1.1682 |       60.94% |       0.0100 |

|            7 |          250 |         3.04 |       0.7370 |       77.34% |       0.0100 |

|            8 |          300 |         3.65 |       0.8038 |       71.09% |       0.0100 |

|            9 |          350 |         4.26 |       0.6766 |       78.91% |       0.0100 |

|           11 |          400 |         4.88 |       0.4824 |       89.06% |       0.0100 |

|           12 |          450 |         5.50 |       0.3670 |       90.63% |       0.0100 |

|           13 |          500 |         6.11 |       0.3582 |       92.19% |       0.0100 |

|           15 |          550 |         6.75 |       0.2501 |       93.75% |       0.0100 |

|           16 |          600 |         7.37 |       0.2662 |       93.75% |       0.0100 |

|           17 |          650 |         7.97 |       0.1974 |       96.09% |       0.0100 |

|           18 |          700 |         8.59 |       0.2140 |       97.66% |       0.0100 |

|           20 |          750 |         9.21 |       0.1402 |       99.22% |       0.0100 |

|           21 |          800 |         9.82 |       0.1324 |       97.66% |       0.0100 |

|           22 |          850 |        10.43 |       0.1373 |       96.88% |       0.0100 |

|           24 |          900 |        11.07 |       0.0913 |      100.00% |       0.0100 |

|           25 |          950 |        11.70 |       0.0935 |       98.44% |       0.0100 |

|           26 |         1000 |        12.31 |       0.0647 |      100.00% |       0.0100 |

|           27 |         1050 |        12.92 |       0.0678 |       99.22% |       0.0100 |

|           29 |         1100 |        13.55 |       0.1053 |       98.44% |       0.0100 |

|           30 |         1150 |        14.17 |       0.0714 |       99.22% |       0.0100 |

|           30 |         1170 |        14.41 |       0.0497 |      100.00% |       0.0100 |

|=========================================================================================|

trainNetwork uses a GPU if there is one available. If there is no available GPU, then it uses CPU. Note: For the available hardware options, see the trainingOptions function page.

Suppose the training was interrupted after the 8th epoch and did not complete. Rather than restarting the training from the beginning, you can load the last checkpoint network and resume training from that point.

## 5.3.4 Load Checkpoint Network and Resume Training

Load the checkpoint network.

load convnet\_checkpoint\_\_351\_\_2016\_11\_09\_\_12\_04\_23.mat

trainNetwork automatically assigns unique names to the checkpoint network files. For example, in this case, where 351 is the iteration number, 2016\_11\_09 is the date and 12\_04\_21 is the time trainNetwork saves the network.

If you don't have the data and the training options in your working directory, you must manually load and/or specify them before you can resume training.

Specify the training options to reduce the maximum number of epochs.

options = trainingOptions('sgdm','MaxEpochs',20, ...

        'CheckpointPath','C:\\Temp\\cnncheckpoint');

You can also adjust other training options, such as initial learning rate.

Resume the training using the layers of the checkpoint network you loaded with the new training options. The name of the network, by default, is net .

convnet2 = trainNetwork(XTrain,TTrain,net.Layers,options)

Training on single GPU.

Initializing image normalization.

|=========================================================================================|

|     Epoch    |   Iteration  | Time Elapsed |  Mini-batch  |  Mini-batch  | Base Learning|

|              |              |  (seconds)   |     Loss     |   Accuracy   |     Rate     |

|=========================================================================================|

|            1 |            1 |         0.02 |       0.5210 |       84.38% |       0.0100 |

|            2 |           50 |         0.62 |       0.4168 |       87.50% |       0.0100 |

|            3 |          100 |         1.23 |       0.4532 |       87.50% |       0.0100 |

|            4 |          150 |         1.83 |       0.3424 |       92.97% |       0.0100 |

|            6 |          200 |         2.45 |       0.3177 |       95.31% |       0.0100 |

|            7 |          250 |         3.06 |       0.2091 |       94.53% |       0.0100 |

|            8 |          300 |         3.67 |       0.1829 |       96.88% |       0.0100 |

|            9 |          350 |         4.27 |       0.1531 |       97.66% |       0.0100 |

|           11 |          400 |         4.91 |       0.1482 |       96.88% |       0.0100 |

|           12 |          450 |         5.58 |       0.1293 |       97.66% |       0.0100 |

|           13 |          500 |         6.31 |       0.1134 |       98.44% |       0.0100 |

|           15 |          550 |         6.94 |       0.1006 |      100.00% |       0.0100 |

|           16 |          600 |         7.55 |       0.0909 |       98.44% |       0.0100 |

|           17 |          650 |         8.16 |       0.0567 |      100.00% |       0.0100 |

|           18 |          700 |         8.76 |       0.0654 |      100.00% |       0.0100 |

|           20 |          750 |         9.41 |       0.0654 |      100.00% |       0.0100 |

|           20 |          780 |         9.77 |       0.0606 |       99.22% |       0.0100 |

|=========================================================================================|

 

convnet2 = 

 

  SeriesNetwork with properties:

 

    Layers: \[7×1 nnet.cnn.layer.Layer\]

# 5.4 Object Detection Using Deep Learning

 

This example shows how to train an object detector using deep learning and R-CNN (Regions with Convolutional Neural Networks).

## 5.4.1 Overview

This example shows how to train an R-CNN object detector for detecting stop signs. R-CNN is an object detection framework, which uses a convolutional neural network (CNN) to classify image regions within an image \[1\]. Instead of classifying every region using a sliding window, the R-CNN detector only processes those regions that are likely to contain an object. This greatly reduces the computational cost incurred when running a CNN.

To illustrate how to train an R-CNN stop sign detector, this example follows the transfer learning workflow that is commonly used in deep learning applications. In transfer learning, a network trained on a large collection of images, such as ImageNet \[2\], is used as the starting point to solve a new classification or detection task. The advantage of using this approach is that the pre-trained network has already learned a rich set of image features that are applicable to a wide range of images. This learning is transferable to the new task by fine-tuning the network. A network is fine-tuned by making small adjustments to the weights such that the feature representations learned for the original task are slightly adjusted to support the new task.

The advantage of transfer learning is that the number of images required for training and the training time are reduced. To illustrate these advantages, this example trains a stop sign detector using the transfer learning workflow. First a CNN is pre-trained using the CIFAR-10 data set, which has 50,000 training images. Then this pre-trained CNN is fine-tuned for stop sign detection using just 41 training images. Without, pre-training the CNN, training the stop sign detector would require many more images.

Note: This example requires Computer Vision System Toolbox™, Image Processing Toolbox™, Neural Network Toolbox™, and Statistics and Machine Learning Toolbox™.

Using a CUDA-capable NVIDIA™ GPU with compute capability 3.0 or higher is highly recommended for running this example. Use of a GPU requires the Parallel Computing Toolbox™.

## 5.4.2 Download CIFAR-10 Image Data

Download the CIFAR-10 data set \[3\]. This dataset contains 50,000 training images that will be used to train a CNN.

% Download CIFAR-10 data to a temporary directory

cifar10Data = tempdir;

 

url = 'https://www.cs.toronto.edu/~kriz/cifar-10-matlab.tar.gz';

 

helperCIFAR10Data.download(url, cifar10Data);

 

% Load the CIFAR-10 training and test data.

\[trainingImages, trainingLabels, testImages, testLabels\] = helperCIFAR10Data.load(cifar10Data);

Each image is a 32x32 RGB image and there are 50,000 training samples.

size(trainingImages)

ans =

 

          32          32           3       50000

 

CIFAR-10 has 10 image categories. List the image categories:

numImageCategories = 10;

categories(trainingLabels)

ans =

 

  10×1 cell array

 

    'airplane'

    'automobile'

    'bird'

    'cat'

    'deer'

    'dog'

    'frog'

    'horse'

    'ship'

    'truck'

 

% Display a few of the training images, resizing them for display.

figure

thumbnails = trainingImages(:,:,:,1:100);

thumbnails = imresize(thumbnails, \[64 64\]);

montage(thumbnails)

![Descripción: http://www.mathworks.com/help/examples/vision\_product/win64/DeepLearningRCNNObjectDetectionExample\_01.png](images/00053.jpeg)

## 5.4.3 Create A Convolutional Neural Network (CNN)

A CNN is composed of a series of layers, where each layer defines a specific computation. The Neural Network Toolbox™ provides functionality to easily design a CNN layer-by-layer. In this example, the following layers are used to create a CNN:

imageInputLayer - Image input layer

convolutional2dLayer - 2D convolution layer for Convolutional Neural Networks

reluLayer - Rectified linear unit (ReLU) layer

maxPooling2dLayer - Max pooling layer

fullyConnectedLayer - Fully connected layer

softmaxLayer - Softmax layer

classificationLayer - Classification output layer for a neural network

The network defined here is similar to the one described in \[4\] and starts with an imageInputLayer. The input layer defines the type and size of data the CNN can process. In this example, the CNN is used to process CIFAR-10 images, which are 32x32 RGB images:

% Create the image input layer for 32x32x3 CIFAR-10 images

\[height, width, numChannels, ~\] = size(trainingImages);

 

imageSize = \[height width numChannels\];

inputLayer = imageInputLayer(imageSize)

inputLayer = 

 

  ImageInputLayer with properties:

 

                Name: ''

           InputSize: \[32 32 3\]

 

   Hyperparameters

    DataAugmentation: 'none'

       Normalization: 'zerocenter'

 

Next, define the middle layers of the network. The middle layers are made up of repeated blocks of convolutional, ReLU (rectified linear units), and pooling layers. These 3 layers form the core building blocks of convolutional neural networks. The convolutional layers define sets of filter weights, which are updated during network training. The ReLU layer adds non-linearity to the network, which allow the network to approximate non-linear functions that map image pixels to the semantic content of the image. The pooling layers downsample data as it flows through the network. In a network with lots of layers, pooling layers should be used sparingly to avoid downsampling the data too early in the network.

% Convolutional layer parameters

filterSize = \[5 5\];

numFilters = 32;

 

middleLayers = \[

 

% The first convolutional layer has a bank of 32 5x5x3 filters. A

% symmetric padding of 2 pixels is added to ensure that image borders

% are included in the processing. This is important to avoid

% information at the borders being washed away too early in the

% network.

convolution2dLayer(filterSize, numFilters, 'Padding', 2)

 

% Note that the third dimension of the filter can be omitted because it

% is automatically deduced based on the connectivity of the network. In

% this case because this layer follows the image layer, the third

% dimension must be 3 to match the number of channels in the input

% image.

 

% Next add the ReLU layer:

reluLayer()

 

% Follow it with a max pooling layer that has a 3x3 spatial pooling area

% and a stride of 2 pixels. This down-samples the data dimensions from

% 32x32 to 15x15.

maxPooling2dLayer(3, 'Stride', 2)

 

% Repeat the 3 core layers to complete the middle of the network.

convolution2dLayer(filterSize, numFilters, 'Padding', 2)

reluLayer()

maxPooling2dLayer(3, 'Stride',2)

 

convolution2dLayer(filterSize, 2 \* numFilters, 'Padding', 2)

reluLayer()

maxPooling2dLayer(3, 'Stride',2)

 

\]

middleLayers = 

 

  9x1 Layer array with layers:

 

     1   ''   Convolution   32 5x5 convolutions with stride \[1  1\] and padding \[2  2\]

     2   ''   ReLU          ReLU

     3   ''   Max Pooling   3x3 max pooling with stride \[2  2\] and padding \[0  0\]

     4   ''   Convolution   32 5x5 convolutions with stride \[1  1\] and padding \[2  2\]

     5   ''   ReLU          ReLU

     6   ''   Max Pooling   3x3 max pooling with stride \[2  2\] and padding \[0  0\]

     7   ''   Convolution   64 5x5 convolutions with stride \[1  1\] and padding \[2  2\]

     8   ''   ReLU          ReLU

     9   ''   Max Pooling   3x3 max pooling with stride \[2  2\] and padding \[0  0\]

A deeper network may be created by repeating these 3 basic layers. However, the number of pooling layers should be reduced to avoid downsampling the data prematurely. Downsampling early in the network discards image information that is useful for learning.

The final layers of a CNN are typically composed of fully connected layers and a softmax loss layer.

finalLayers = \[

 

% Add a fully connected layer with 64 output neurons. The output size of

% this layer will be an array with a length of 64.

fullyConnectedLayer(64)

 

% Add an ReLU non-linearity.

reluLayer

 

% Add the last fully connected layer. At this point, the network must

% produce 10 signals that can be used to measure whether the input image

% belongs to one category or another. This measurement is made using the

% subsequent loss layers.

fullyConnectedLayer(numImageCategories)

 

% Add the softmax loss layer and classification layer. The final layers use

% the output of the fully connected layer to compute the categorical

% probability distribution over the image classes. During the training

% process, all the network weights are tuned to minimize the loss over this

% categorical distribution.

softmaxLayer

classificationLayer

\]

finalLayers = 

 

  5x1 Layer array with layers:

 

     1   ''   Fully Connected         64 fully connected layer

     2   ''   ReLU                    ReLU

     3   ''   Fully Connected         10 fully connected layer

     4   ''   Softmax                 softmax

     5   ''   Classification Output   crossentropyex

Combine the input, middle, and final layers.

layers = \[

    inputLayer

    middleLayers

    finalLayers

    \]

layers = 

 

  15x1 Layer array with layers:

 

     1   ''   Image Input             32x32x3 images with 'zerocenter' normalization

     2   ''   Convolution             32 5x5 convolutions with stride \[1  1\] and padding \[2  2\]

     3   ''   ReLU                    ReLU

     4   ''   Max Pooling             3x3 max pooling with stride \[2  2\] and padding \[0  0\]

     5   ''   Convolution             32 5x5 convolutions with stride \[1  1\] and padding \[2  2\]

     6   ''   ReLU                    ReLU

     7   ''   Max Pooling             3x3 max pooling with stride \[2  2\] and padding \[0  0\]

     8   ''   Convolution             64 5x5 convolutions with stride \[1  1\] and padding \[2  2\]

     9   ''   ReLU                    ReLU

    10   ''   Max Pooling             3x3 max pooling with stride \[2  2\] and padding \[0  0\]

    11   ''   Fully Connected         64 fully connected layer

    12   ''   ReLU                    ReLU

    13   ''   Fully Connected         10 fully connected layer

    14   ''   Softmax                 softmax

    15   ''   Classification Output   crossentropyex

Initialize the first convolutional layer weights using normally distributed random numbers with standard deviation of 0.0001. This helps improve the convergence of training.

layers(2).Weights = 0.0001 \* randn(\[filterSize numChannels numFilters\]);

## 5.4.4 Train CNN Using CIFAR-10 Data

Now that the network architecture is defined, it can be trained using the CIFAR-10 training data. First, set up the network training algorithm using the trainingOptions function. The network training algorithm uses Stochastic Gradient Descent with Momentum (SGDM) with an initial learning rate of 0.001. During training, the initial learning rate is reduced every 8 epochs (1 epoch is defined as one complete pass through the entire training data set). The training algorithm is run for 40 epochs.

Note that the training algorithm uses a mini-batch size of 128 images. If using a GPU for training, this size may need to be lowered due to memory constraints on the GPU.

% Set the network training options

opts = trainingOptions('sgdm', ...

    'Momentum', 0.9, ...

    'InitialLearnRate', 0.001, ...

    'LearnRateSchedule', 'piecewise', ...

    'LearnRateDropFactor', 0.1, ...

    'LearnRateDropPeriod', 8, ...

    'L2Regularization', 0.004, ...

    'MaxEpochs', 40, ...

    'MiniBatchSize', 128, ...

    'Verbose', true);

Train the network using the trainNetwork function. This is a computationally intensive process that takes 20-30 minutes to complete. To save time while running this example, a pre-trained network is loaded from disk. If you wish to train the network yourself, set the doTraining variable shown below to true.

Note that a CUDA-capable NVIDIA™ GPU with compute capability 3.0 or higher is highly recommeded for training.

% A trained network is loaded from disk to save time when running the

% example. Set this flag to true to train the network.

doTraining = false;

 

if doTraining

    % Train a network.

    cifar10Net = trainNetwork(trainingImages, trainingLabels, layers, opts);

else

    % Load pre-trained detector for the example.

    load('rcnnStopSigns.mat','cifar10Net')

end

## 5.4.5 Validate CIFAR-10 Network Training

After the network is trained, it should be validated to ensure that training was successful. First, a quick visualization of the first convolutional layer's filter weights can help identify any immediate issues with training.

% Extract the first convolutional layer weights

w = cifar10Net.Layers(2).Weights;

 

% rescale and resize the weights for better visualization

w = mat2gray(w);

w = imresize(w, \[100 100\]);

 

figure

montage(w)

![Descripción: http://www.mathworks.com/help/examples/vision\_product/win64/DeepLearningRCNNObjectDetectionExample\_02.png](images/00054.jpeg)

The first layer weights should have some well defined structure. If the weights still look random, then that is an indication that the network may require additional training. In this case, as shown above, the first layer filters have learned edge-like features from the CIFAR-10 training data.

To completely validate the training results, use the CIFAR-10 test data to measure the classification accuracy of the network. A low accuracy score indicates additional training or additional training data is required. The goal of this example is not necessarily to achieve 100% accuracy on the test set, but to sufficiently train a network for use in training an object detector.

% Run the network on the test set.

YTest = classify(cifar10Net, testImages);

 

% Calculate the accuracy.

accuracy = sum(YTest == testLabels)/numel(testLabels)

accuracy =

 

    0.7456

 

Further training will improve the accuracy, but that is not necessary for the purpose of training the R-CNN object detector.

## 5.4.6 Load Training Data

Now that the network is working well for the CIFAR-10 classification task, the transfer learning approach can be used to fine-tune the network for stop sign detection.

Start by loading the ground truth data for stop signs.

% Load the ground truth data

data = load('stopSignsAndCars.mat', 'stopSignsAndCars');

stopSignsAndCars = data.stopSignsAndCars;

 

% Update the path to the image files to match the local file system

visiondata = fullfile(toolboxdir('vision'),'visiondata');

stopSignsAndCars.imageFilename = fullfile(visiondata, stopSignsAndCars.imageFilename);

 

% Display a summary of the ground truth data

summary(stopSignsAndCars)

Variables:

 

    imageFilename: 41×1 cell array of character vectors

 

    stopSign: 41×1 cell

 

    carRear: 41×1 cell

 

    carFront: 41×1 cell

 

The training data is contained within a table that contains the image filename and ROI labels for stop signs, car fronts, and rears. Each ROI label is a bounding box around objects of interest within an image. For training the stop sign detector, only the stop sign ROI labels are needed. The ROI labels for car front and rear must be removed:

% Only keep the image file names and the stop sign ROI labels

stopSigns = stopSignsAndCars(:, {'imageFilename','stopSign'});

 

% Display one training image and the ground truth bounding boxes

I = imread(stopSigns.imageFilename{1});

I = insertObjectAnnotation(I, 'Rectangle', stopSigns.stopSign{1}, 'stop sign', 'LineWidth', 8);

 

figure

imshow(I)

![Descripción: http://www.mathworks.com/help/examples/vision\_product/win64/DeepLearningRCNNObjectDetectionExample\_03.png](images/00055.jpeg)

Note that there are only 41 training images within this data set. Training an R-CNN object detector from scratch using only 41 images is not practical and would not produce a reliable stop sign detector. Because the stop sign detector is trained by fine-tuning a network that has been pre-trained on a larger dataset (CIFAR-10 has 50,000 training images), using a much smaller dataset is feasible.

## 5.4.7 Train R-CNN Stop Sign Detector

Finally, train the R-CNN object detector using trainRCNNObjectDetector. The input to this function is the ground truth table which contains labeled stop sign images, the pre-trained CIFAR-10 network, and the training options. The training function automatically modifies the original CIFAR-10 network, which classified images into 10 categories, into a network that can classify images into 2 classes: stop signs and a generic background class.

During training, the input network weights are fine-tuned using image patches extracted from the ground truth data. The 'PositiveOverlapRange' and 'NegativeOverlapRange' parameters control which image patches are used for training. Positive training samples are those that overlap with the ground truth boxes by 0.5 to 1.0, as measured by the bounding box intersection over union metric. Negative training samples are those that overlap by 0 to 0.3. The best values for these parameters should be chosen by testing the trained detector on a validation set.

For R-CNN training, **the use of a parallel pool of MATLAB workers is highly recommended to reduce training time**. trainRCNNObjectDetector automatically creates and uses a parallel pool based on your [parallel preference settings](http://www.mathworks.com/help/vision/gs/computer-vision-system-toolbox-preferences.html). Ensure that the use of the parallel pool is enabled prior to training.

To save time while running this example, a pre-trained network is loaded from disk. If you wish to train the network yourself, set the doTraining variable shown below to true.

Note that a CUDA-capable NVIDIA™ GPU with compute capability 3.0 or higher is highly recommeded for training.

% A trained detector is loaded from disk to save time when running the

% example. Set this flag to true to train the detector.

doTraining = false;

 

if doTraining

 

    % Set training options

    options = trainingOptions('sgdm', ...

        'MiniBatchSize', 128, ...

        'InitialLearnRate', 1e-3, ...

        'LearnRateSchedule', 'piecewise', ...

        'LearnRateDropFactor', 0.1, ...

        'LearnRateDropPeriod', 100, ...

        'MaxEpochs', 100, ...

        'Verbose', true);

 

    % Train an R-CNN object detector. This will take several minutes.

    rcnn = trainRCNNObjectDetector(stopSigns, cifar10Net, options, ...

    'NegativeOverlapRange', \[0 0.3\], 'PositiveOverlapRange',\[0.5 1\])

else

    % Load pre-trained network for the example.

    load('rcnnStopSigns.mat','rcnn')

end

## 5.4.8 Test R-CNN Stop Sign Detector

The R-CNN object detector can now be used to detect stop signs in images. Try it out on a test image:

% Read test image

testImage = imread('stopSignTest.jpg');

 

% Detect stop signs

\[bboxes, score, label\] = detect(rcnn, testImage, 'MiniBatchSize', 128)

bboxes =

 

   419   147    31    20

 

 

score =

 

  single

 

    0.9955

 

 

label = 

 

  categorical

 

     stopSign 

 

The R-CNN object detect method returns the object bounding boxes, a detection score, and a class label for each detection. The labels are useful when detecting multiple objects, e.g. stop, yield, or speed limit signs. The scores, which range between 0 and 1, indicate the confidence in the detection and can be used to ignore low scoring detections.

% Display the detection results

\[score, idx\] = max(score);

 

bbox = bboxes(idx, :);

annotation = sprintf('%s: (Confidence = %f)', label(idx), score);

 

outputImage = insertObjectAnnotation(testImage, 'rectangle', bbox, annotation);

 

figure

imshow(outputImage)

![Descripción: http://www.mathworks.com/help/examples/vision\_product/win64/DeepLearningRCNNObjectDetectionExample\_04.png](images/00056.jpeg)

## 5.4.9 Debugging Tips

The network used within the R-CNN detector can also be used to process the entire test image. By directly processing the entire image, which is larger than the network's input size, a 2-D heat-map of classification scores can be generated. This is a useful debugging tool because it helps identify items in the image that are confusing the network, and may help provide insight into improving training.

% The trained network is stored within the R-CNN detector

rcnn.Network

ans = 

 

  SeriesNetwork with properties:

 

    Layers: \[15×1 nnet.cnn.layer.Layer\]

 

Extract the activations from the softmax layer. These are the classification scores produced by the network as it scans the image.

featureMap = activations(rcnn.Network, testImage, 'softmax', 'OutputAs', 'channels');

 

% The softmax activations are stored in a 3-D array.

size(featureMap)

ans =

 

    43    78     2

 

The 3rd dimension in featureMap corresponds to the object classes

rcnn.ClassNames

ans =

 

  2×1 cell array

 

    'stopSign'

    'Background'

 

The stop sign feature map is stored in the first channel

stopSignMap = featureMap(:, :, 1);

The size of the activations output is smaller than the input image due to the downsampling operations in the network. To generate a nicer visualization, resize stopSignMap to the size of the input image. This is a very crude approximation that maps activations to image pixels and should only be used for illustrative purposes.

% Resize stopSignMap for visualization

\[height, width, ~\] = size(testImage);

stopSignMap = imresize(stopSignMap, \[height, width\]);

 

% Visualize the feature map superimposed on the test image.

featureMapOnImage = imfuse(testImage, stopSignMap);

 

figure

imshow(featureMapOnImage)

![Descripción: http://www.mathworks.com/help/examples/vision\_product/win64/DeepLearningRCNNObjectDetectionExample\_05.png](images/00057.jpeg)

The stop sign in the test image corresponds nicely with the largest peak in the network activations. This helps verify that the CNN used within the R-CNN detector has effectively learned to identify stop signs. Had there been other peaks, this may indicate that the training requires additional negative data to help prevent false positives. If that's the case, then you can increase 'MaxEpochs' in the trainingOptions and re-train.

 

# 5.5 Object Detection Using Faster R-CNN Deep Learning

 

This example shows how to train an object detector using a deep learning technique named Faster R-CNN (Regions with Convolutional Neural Networks).

## 5.5.1 Overview

This example shows how to train a Faster R-CNN object detector for detecting vehicles. Faster R-CNN \[1\] is an extension of the R-CNN \[2\] and Fast R-CNN \[3\] object detection techniques. All three of these techniques use convolutional neural networks (CNN). The difference between them is how they select regions to process and how those regions are classified. R-CNN and Fast R-CNN use a region proposal algorithm as a pre-processing step before running the CNN. The proposal algorithms are typically techniques such as EdgeBoxes \[4\] or Selective Search \[5\], which are independent of the CNN. In the case of Fast R-CNN, the use of these techniques becomes the processing bottleneck compared to running the CNN. Faster R-CNN addresses this issue by implementing the region proposal mechanism using the CNN and thereby making region proposal a part of the CNN training and prediction steps.

In this example, a vehicle detector is trained using the trainFasterRCNNObjectDetector function from Computer Vision System Toolbox™. The example has the following sections:

·        Load the data set.

·        Design the convolutional Neural Network (CNN).

·        Configure training options.

·        Train Faster R-CNN object detector.

·        Evaluate the trained detector.

Note: This example requires Computer Vision System Toolbox™, Image Processing Toolbox™, and Neural Network Toolbox™.

Using a CUDA-capable NVIDIA™ GPU with compute capability 3.0 or higher is highly recommended for running this example. Use of a GPU requires Parallel Computing Toolbox™.

## 5.5.2 Load Dataset

This example uses a small vehicle data set that contains 295 images. Each image contains 1 to 2 labeled instances of a vehicle. A small data set is useful for exploring the Faster R-CNN training procedure, but in practice, more labeled images are needed to train a robust detector.

% Load vehicle data set

data = load('fasterRCNNVehicleTrainingData.mat');

vehicleDataset = data.vehicleTrainingData;

The training data is stored in a table. The first column contains the path to the image files. The remaining columns contain the ROI labels for vehicles.

% Display first few rows of the data set.

vehicleDataset(1:4,:)

ans =

 

  4×2 table

 

          imageFilename             vehicle   

    \_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_\_    \_\_\_\_\_\_\_\_\_\_\_\_

 

    'vehicles/image\_00001.jpg'    \[1×4 double\]

    'vehicles/image\_00002.jpg'    \[1×4 double\]

    'vehicles/image\_00003.jpg'    \[1×4 double\]

    'vehicles/image\_00004.jpg'    \[1×4 double\]

 

Display one of the images from the data set to understand the type of images it contains.

% Add fullpath to the local vehicle data folder.

dataDir = fullfile(toolboxdir('vision'),'visiondata');

vehicleDataset.imageFilename = fullfile(dataDir, vehicleDataset.imageFilename);

 

% Read one of the images.

I = imread(vehicleDataset.imageFilename{10});

 

% Insert the ROI labels.

I = insertShape(I, 'Rectangle', vehicleDataset.vehicle{10});

 

% Resize and display image.

I = imresize(I, 3);

figure

imshow(I)

![Descripción: http://www.mathworks.com/help/examples/vision\_product/win64/DeepLearningFasterRCNNObjectDetectionExample\_01.png](images/00058.jpeg)

Split the data set into a training set for training the detector, and a test set for evaluating the detector. Select 60% of the data for training. Use the rest for evaluation.

% Split data into a training and test set.

idx = floor(0.6 \* height(vehicleDataset));

trainingData = vehicleDataset(1:idx,:);

testData = vehicleDataset(idx:end,:);

## 5.5.3 Create a Convolutional Neural Network (CNN)

A CNN is the basis of the Faster R-CNN object detector. Create the CNN layer by layer using Neural Network Toolbox™ functionality.

Start with the imageInputLayer function, which defines the type and size of the input layer. For classification tasks, the input size is typically the size of the training images. For detection tasks, the CNN needs to analyze smaller sections of the image, so the input size must be similar in size to the smallest object in the data set. In this data set all the objects are larger than \[16 16\], so select an input size of \[32 32\]. This input size is a balance between processing time and the amount of spatial detail the CNN needs to resolve.

% Create image input layer.

inputLayer = imageInputLayer(\[32 32 3\]);

Next, define the middle layers of the network. The middle layers are made up of repeated blocks of convolutional, ReLU (rectified linear units), and pooling layers. These layers form the core building blocks of convolutional neural networks.

% Define the convolutional layer parameters.

filterSize = \[3 3\];

numFilters = 32;

 

% Create the middle layers.

middleLayers = \[

 

    convolution2dLayer(filterSize, numFilters, 'Padding', 1)

    reluLayer()

    convolution2dLayer(filterSize, numFilters, 'Padding', 1)

    reluLayer()

    maxPooling2dLayer(3, 'Stride',2)

 

    \];

You can create a deeper network by repeating these basic layers. However, to avoid downsampling the data prematurely, keep the number of pooling layers low. Downsampling early in the network discards image information that is useful for learning.

The final layers of a CNN are typically composed of fully connected layers and a softmax loss layer.

finalLayers = \[

 

    % Add a fully connected layer with 64 output neurons. The output size

    % of this layer will be an array with a length of 64.

    fullyConnectedLayer(64)

 

    % Add a ReLU non-linearity.

    reluLayer()

 

    % Add the last fully connected layer. At this point, the network must

    % produce outputs that can be used to measure whether the input image

    % belongs to one of the object classes or background. This measurement

    % is made using the subsequent loss layers.

    fullyConnectedLayer(width(vehicleDataset))

 

    % Add the softmax loss layer and classification layer.

    softmaxLayer()

    classificationLayer()

\];

Combine the input, middle, and final layers.

layers = \[

    inputLayer

    middleLayers

    finalLayers

    \]

layers = 

 

  11x1 Layer array with layers:

 

     1   ''   Image Input             32x32x3 images with 'zerocenter' normalization

     2   ''   Convolution             32 3x3 convolutions with stride \[1  1\] and padding \[1  1\]

     3   ''   ReLU                    ReLU

     4   ''   Convolution             32 3x3 convolutions with stride \[1  1\] and padding \[1  1\]

     5   ''   ReLU                    ReLU

     6   ''   Max Pooling             3x3 max pooling with stride \[2  2\] and padding \[0  0\]

     7   ''   Fully Connected         64 fully connected layer

     8   ''   ReLU                    ReLU

     9   ''   Fully Connected         2 fully connected layer

    10   ''   Softmax                 softmax

    11   ''   Classification Output   crossentropyex

## 5.5.4 Configure Training Options

trainFasterRCNNObjectDetector trains the detector in four steps. The first two steps train the region proposal and detection networks used in Faster R-CNN. The final two steps combine the networks from the first two steps such that a single network is created for detection \[1\]. Each training step can have different convergence rates, so it is beneficial to specify independent training options for each step. To specify the network training options use trainingOptions from Neural Network Toolbox™.

% Options for step 1.

optionsStage1 = trainingOptions('sgdm', ...

    'MaxEpochs', 10, ...

    'InitialLearnRate', 1e-5, ...

    'CheckpointPath', tempdir);

 

% Options for step 2.

optionsStage2 = trainingOptions('sgdm', ...

    'MaxEpochs', 10, ...

    'InitialLearnRate', 1e-5, ...

    'CheckpointPath', tempdir);

 

% Options for step 3.

optionsStage3 = trainingOptions('sgdm', ...

    'MaxEpochs', 10, ...

    'InitialLearnRate', 1e-6, ...

    'CheckpointPath', tempdir);

 

% Options for step 4.

optionsStage4 = trainingOptions('sgdm', ...

    'MaxEpochs', 10, ...

    'InitialLearnRate', 1e-6, ...

    'CheckpointPath', tempdir);

 

options = \[

    optionsStage1

    optionsStage2

    optionsStage3

    optionsStage4

    \];

Here, the learning rate for the first two steps is set higher than the last two steps. Because the last two steps are fine-tuning steps, the network weights can be modified more slowly than in the first two steps.

In addition, 'CheckpointPath' is set to a temporary location for all the training options. This name-value pair enables the saving of partially trained detectors during the training process. If training is interrupted, such as from a power outage or system failure, you can resume training from the saved checkpoint.

## 5.5.5 Train Faster R-CNN

Now that the CNN and training options are defined, you can train the detector using trainFasterRCNNObjectDetector.

During training, image patches are extracted from the training data. The 'PositiveOverlapRange' and 'NegativeOverlapRange' name-value pairs control which image patches are used for training. Positive training samples are those that overlap with the ground truth boxes by 0.6 to 1.0, as measured by the bounding box intersection over union metric. Negative training samples are those that overlap by 0 to 0.3. The best values for these parameters should be chosen by testing the trained detector on a validation set. To choose the best values for these name-value pairs, test the trained detector on a validation set.

For Faster R-CNN training, **the use of a parallel pool of MATLAB workers is highly recommended to reduce training time**. trainFasterRCNNObjectDetector automatically creates and uses a parallel pool based on your parallel preference settings. Ensure that the use of the parallel pool is enabled prior to training.

A CUDA-capable NVIDIA™ GPU with compute capability 3.0 or higher is highly recommended for training.

To save time while running this example, a pretrained network is loaded from disk. To train the network yourself, set the doTrainingAndEval variable shown here to true.

% A trained network is loaded from disk to save time when running the

% example. Set this flag to true to train the network.

doTrainingAndEval = false;

 

if doTrainingAndEval

    % Set random seed to ensure example training reproducibility.

    rng(0);

 

    % Train Faster R-CNN detector. Select a BoxPyramidScale of 1.2 to allow

    % for finer resolution for multiscale object detection.

    detector = trainFasterRCNNObjectDetector(trainingData, layers, options, ...

        'NegativeOverlapRange', \[0 0.3\], ...

        'PositiveOverlapRange', \[0.6 1\], ...

        'BoxPyramidScale', 1.2);

else

    % Load pretrained detector for the example.

    detector = data.detector;

end

To quickly verify the training, run the detector on a test image.

% Read a test image.

I = imread('highway.png');

 

% Run the detector.

\[bboxes, scores\] = detect(detector, I);

 

% Annotate detections in the image.

I = insertObjectAnnotation(I, 'rectangle', bboxes, scores);

figure

imshow(I)

![Descripción: http://www.mathworks.com/help/examples/vision\_product/win64/DeepLearningFasterRCNNObjectDetectionExample\_02.png](images/00059.jpeg)

## 5.5.6 Evaluate Detector Using Test Set

Testing a single image showed promising results. To fully evaluate the detector, testing it on a larger set of images is recommended. Computer Vision System Toolbox™ provides object detector evaluation functions to measure common metrics such as average precision (evaluateDetectionPrecision) and log-average miss rates (evaluateDetectionMissRate). Here, the average precision metric is used. The average precision provides a single number that incorporates the ability of the detector to make correct classifications (precision) and the ability of the detector to find all relevant objects (recall).

The first step for detector evaluation is to collect the detection results by running the detector on the test set. To avoid long evaluation time, the results are loaded from disk. Set the doTrainingAndEval flag from the previous section to true to execute the evaluation locally.

if doTrainingAndEval

    % Run detector on each image in the test set and collect results.

    resultsStruct = struct(\[\]);

    for i = 1:height(testData)

 

        % Read the image.

        I = imread(testData.imageFilename{i});

 

        % Run the detector.

        \[bboxes, scores, labels\] = detect(detector, I);

 

        % Collect the results.

        resultsStruct(i).Boxes = bboxes;

        resultsStruct(i).Scores = scores;

        resultsStruct(i).Labels = labels;

    end

 

    % Convert the results into a table.

    results = struct2table(resultsStruct);

else

    % Load results from disk.

    results = data.results;

end

 

% Extract expected bounding box locations from test data.

expectedResults = testData(:, 2:end);

 

% Evaluate the object detector using Average Precision metric.

\[ap, recall, precision\] = evaluateDetectionPrecision(results, expectedResults);

The precision/recall (PR) curve highlights how precise a detector is at varying levels of recall. Ideally, the precision would be 1 at all recall levels. In this example, the average precision is 0.6. The use of additional layers in the network can help improve the average precision, but might require additional training data and longer training time.

% Plot precision/recall curve

figure

plot(recall, precision)

xlabel('Recall')

ylabel('Precision')

grid on

title(sprintf('Average Precision = %.1f', ap))

![Descripción: http://www.mathworks.com/help/examples/vision\_product/win64/DeepLearningFasterRCNNObjectDetectionExample\_03.png](images/00060.jpeg)

 

# 5.6 Object Detectors

 

Computer Vision System Toolbox provides pretrained object detections and the functionality to train a custom detector. The cascade object detector uses the Viola-Jones algorithm to detect people's faces, noses, eyes, mouth, or upper body. The people detector detects people in an input image using the histogram of oriented gradients (HOG) features and a trained support vector machine (SVM) classifier.

You can customize the cascade object detector using the [`trainCascadeObjectDetector`](http://es.mathworks.com/help/vision/ref/traincascadeobjectdetector.html) function . You can also use the [Training Image Labeler](http://es.mathworks.com/help/vision/ref/trainingimagelabeler-app.html), feature extractors, and the Statistics and Machine Learning Toolbox classifiers to create a custom detector.

# 5.7 Train a Cascade Object Detector

## 5.7.1 Why Train a Detector?

The [vision.CascadeObjectDetector](http://es.mathworks.com/help/vision/ref/vision.cascadeobjectdetector-class.html) System object comes with several pretrained classifiers for detecting frontal faces, profile faces, noses, eyes, and the upper body. However, these classifiers are not always sufficient for a particular application. Computer Vision System Toolbox™ provides the [trainCascadeObjectDetector](http://es.mathworks.com/help/vision/ref/traincascadeobjectdetector.html) function to train a custom classifier.

![Descripción: http://es.mathworks.com/help/vision/ug/traincascadeobjectdetector\_overview.png](images/00061.jpeg)

## 5.7.2 What Kinds of Objects Can You Detect?

The Computer Vision System Toolbox cascade object detector can detect object categories whose aspect ratio does not vary significantly. Objects whose aspect ratio remains fixed include faces, stop signs, and cars viewed from one side.

The [vision.CascadeObjectDetector](http://es.mathworks.com/help/vision/ref/vision.cascadeobjectdetector-class.html) System object detects objects in images by sliding a window over the image. The detector then uses a cascade classifier to decide whether the window contains the object of interest. The size of the window varies to detect objects at different scales, but its aspect ratio remains fixed. The detector is very sensitive to out-of-plane rotation, because the aspect ratio changes for most 3-D objects. Thus, you need to train a detector for each orientation of the object. Training a single detector to handle all orientations will not work.

## 5.7.3 How Does the Cascade Classifier Work?

The cascade classifier consists of stages, where each stage is an ensemble of weak learners. The weak learners are simple classifiers called *decision stumps*. Each stage is trained using a technique called boosting. *Boosting* provides the ability to train a highly accurate classifier by taking a weighted average of the decisions made by the weak learners.

Each stage of the classifier labels the region defined by the current location of the sliding window as either positive or negative. *Positive* indicates that an object was found and *negative* indicates no objects were found. If the label is negative, the classification of this region is complete, and the detector slides the window to the next location. If the label is positive, the classifier passes the region to the next stage. The detector reports an object found at the current window location when the final stage classifies the region as positive.

The stages are designed to reject negative samples as fast as possible. The assumption is that the vast majority of windows do not contain the object of interest. Conversely, true positives are rare and worth taking the time to verify.

·        A *true positive* occurs when a positive sample is correctly classified.

·        A *false positive* occurs when a negative sample is mistakenly classified as positive.

·        A *false negative* occurs when a positive sample is mistakenly classified as negative.

To work well, each stage in the cascade must have a low false negative rate. If a stage incorrectly labels an object as negative, the classification stops, and you cannot correct the mistake. However, each stage can have a high false positive rate. Even if the detector incorrectly labels a nonobject as positive, you can correct the mistake in subsequent stages.

The overall false positive rate of the cascade classifier is *f^s*, where *f* is the false positive rate per stage in the range (0 1), and *s* is the number of stages. Similarly, the overall true positive rate is *t^s*, where *t* is the true positive rate per stage in the range (0 1\]. Thus, adding more stages reduces the overall false positive rate, but it also reduces the overall true positive rate.

## 5.7.4 Create a Cascade Classifier Using the  trainCascadeObjectDetector

Cascade classifier training requires a set of positive samples and a set of negative images. You must provide a set of positive images with regions of interest specified to be used as positive samples. You can use the [Training Image Labeler](http://es.mathworks.com/help/vision/ref/trainingimagelabeler-app.html)to label objects of interest with bounding boxes. The Training Image Labeler outputs a table to use for positive samples. You also must provide a set of negative images from which the function generates negative samples automatically. To achieve acceptable detector accuracy, set the number of stages, feature type, and other function parameters.

![Descripción: http://es.mathworks.com/help/vision/ug/traincascadeobjectdetector\_training.png](images/00062.gif)

**Considerations when Setting Parameters**

Select the function parameters to optimize the number of stages, the false positive rate, the true positive rate, and the type of features to use for training. When you set the parameters, consider these tradeoffs.

 
| **Condition** || **Consideration** |
| --- | --- |
| A large training set (in the thousands). || Increase the number of stages and set a higher false positive rate for each stage. |
| A small training set. || Decrease the number of stages and set a lower false positive rate for each stage. |
| To reduce the probability of missing an object. || Increase the true positive rate. However, a high true positive rate can prevent you from achieving the desired false positive rate per stage, making the detector more likely to produce false detections. |
| To reduce the number of false detections. || Increase the number of stages or decrease the false alarm rate per stage. |

**Feature Types Available for Training**

Choose the feature that suits the type of object detection you need. The [trainCascadeObjectDetector](http://es.mathworks.com/help/vision/ref/traincascadeobjectdetector.html) supports three types of features: Haar, local binary patterns (LBP), and histograms of oriented gradients (HOG). Haar and LBP features are often used to detect faces because they work well for representing fine-scale textures. The HOG features are often used to detect objects such as people and cars. They are useful for capturing the overall shape of an object. For example, in the following visualization of the HOG features, you can see the outline of the bicycle.

![Descripción: http://es.mathworks.com/help/vision/ug/traincascadeobjectdetector\_bicyclehog.png](images/00063.jpeg)

You might need to run the trainCascadeObjectDetector function multiple times to tune the parameters. To save time, you can use LBP or HOG features on a small subset of your data. Training a detector using Haar features takes much longer. After that, you can run the Haar features to see if the accuracy improves.

**Supply Positive Samples**

To create positive samples easily, you can use the [Training Image Labeler](http://es.mathworks.com/help/vision/ref/trainingimagelabeler-app.html) app. The Training Image Labeler provides an easy way to label positive samples by interactively specifying rectangular regions of interest (ROIs).

![Descripción: http://es.mathworks.com/help/vision/ug/traincascade\_labeler.png](images/00064.gif)

You can also specify positive samples manually in one of two ways. One way is to specify rectangular regions in a larger image. The regions contain the objects of interest. The other approach is to crop out the object of interest from the image and save it as a separate image. Then, you can specify the region to be the entire image. You can also generate more positive samples from existing ones by adding rotation or noise, or by varying brightness or contrast.

**Supply Negative Images**

Negative samples are not specified explicitly. Instead, the [trainCascadeObjectDetector](http://es.mathworks.com/help/vision/ref/traincascadeobjectdetector.html) function automatically generates negative samples from user-supplied negative images that do not contain objects of interest. Before training each new stage, the function runs the detector consisting of the stages already trained on the negative images. Any objects detected from these image are false positives, which are used as negative samples. In this way, each new stage of the cascade is trained to correct mistakes made by previous stages.

![Descripción: http://es.mathworks.com/help/vision/ug/traincascadeobjectdetector\_negativeimages.png](images/00065.jpeg)

As more stages are added, the detector's overall false positive rate decreases, causing generation of negative samples to be more difficult. For this reason, it is helpful to supply as many negative images as possible. To improve training accuracy, supply negative images that contain backgrounds typically associated with the objects of interest. Also, include negative images that contain nonobjects similar in appearance to the objects of interest. For example, if you are training a stop-sign detector, include negative images that contain road signs and shapes similar to a stop sign.

**Choose the Number of Stages**

There is a trade-off between fewer stages with a lower false positive rate per stage or more stages with a higher false positive rate per stage. Stages with a lower false positive rate are more complex because they contain a greater number of weak learners. Stages with a higher false positive rate contain fewer weak learners. Generally, it is better to have a greater number of simple stages because at each stage the overall false positive rate decreases exponentially. For example, if the false positive rate at each stage is 50%, then the overall false positive rate of a cascade classifier with two stages is 25%. With three stages, it becomes 12.5%, and so on. However, the greater the number of stages, the greater the amount of training data the classifier requires. Also, increasing the number of stages increases the false negative rate. This increase results in a greater chance of rejecting a positive sample by mistake. Set the false positive rate (FalseAlarmRate) and the number of stages, (NumCascadeStages) to yield an acceptable overall false positive rate. Then you can tune these two parameters experimentally.

Training can sometimes terminate early. For example, suppose that training stops after seven stages, even though you set the number of stages parameter to 20. It is possible that the function cannot generate enough negative samples. If you run the function again and set the number of stages to seven, you do not get the same result. The results between stages differ because the number of positive and negative samples to use for each stage is recalculated for the new number of stages.

**Training Time of Detector**

Training a good detector requires thousands of training samples. Large amounts of training data can take hours or even days to process. During training, the function displays the time it took to train each stage in the MATLAB^® Command Window. Training time depends on the type of feature you specify. Using Haar features takes much longer than using LBP or HOG features.

## 5.7.5 Troubleshooting

**What if you run out of positive samples?**

The [trainCascadeObjectDetector](http://es.mathworks.com/help/vision/ref/traincascadeobjectdetector.html) function automatically determines the number of positive samples to use to train each stage. The number is based on the total number of positive samples supplied by the user and the values of the TruePositiveRate and NumCascadeStages parameters.

The number of available positive samples used to train each stage depends on the true positive rate. The rate specifies what percentage of positive samples the function can classify as negative. If a sample is classified as a negative by any stage, it never reaches subsequent stages. For example, suppose you set the TruePositiveRate to 0.9, and all of the available samples are used to train the first stage. In this case, 10% of the positive samples are rejected as negatives, and only 90% of the total positive samples are available for training the second stage. If training continues, then each stage is trained with fewer and fewer samples. Each subsequent stage must solve an increasingly more difficult classification problem with fewer positive samples. With each stage getting fewer samples, the later stages are likely to overfit the data.

Ideally, use the same number of samples to train each stage. To do so, the number of positive samples used to train each stage must be less than the total number of available positive samples. The only exception is that when the value of TruePositiveRate times the total number of positive samples is less than 1, no positive samples are rejected as negatives.

The function calculates the number of positive samples to use at each stage using the following formula:

number of positive samples = [floor](http://es.mathworks.com/help/matlab/ref/floor.html)(totalPositiveSamples / (1 + (NumCascadeStages - 1) \* (1 - TruePositiveRate)))

This calculation does not guarantee that the same number of positive samples are available for each stage. The reason is that it is impossible to predict with certainty how many positive samples will be rejected as negatives. The training continues as long as the number of positive samples available to train a stage is greater than 10% of the number of samples the function determined automatically using the preceding formula. If there are not enough positive samples the training stops and the function issues a warning. The function also outputs a classifier consisting of the stages that it had trained up to that point. If the training stops, you can add more positive samples. Alternatively, you can increase TruePositiveRate. Reducing the number of stages can also work, but such reduction can also result in a higher overall false alarm rate.

 

**What to do if you run out of negative samples?**

The function calculates the number of negative samples used at each stage. This calculation is done by multiplying the number of positive samples used at each stage by the value of NegativeSamplesFactor.

Just as with positive samples, there is no guarantee that the calculated number of negative samples are always available for a particular stage. The trainCascadeObjectDetector function generates negative samples from the negative images. However, with each new stage, the overall false alarm rate of the cascade classifier decreases, making it less likely to find the negative samples.

The training continues as long as the number of negative samples available to train a stage is greater than 10% of the calculated number of negative samples. If there are not enough negative samples, the training stops and the function issues a warning. It outputs a classifier consisting of the stages that it had trained up to that point. When the training stops, the best approach is to add more negative images. Alternatively, you can reduce the number of stages or increase the false positive rate.

## 5.7.6 Examples

**Train a Five-Stage Stop-Sign Detector**

This example shows you how to set up and train a five-stage, stop-sign detector, using 86 positive samples. The default value for TruePositiveRate is 0.995.

Step 1: Load the positive samples data from a MAT-file. In this example, file names and bounding boxes are contained in the array of structures labeled 'data'.

load('stopSigns.mat');

Step 2: Add the image directory to the MATLAB path.

imDir = fullfile(matlabroot,'toolbox','vision','visiondata','stopSignImages');

addpath(imDir);

Step 3: Specify the folder with negative images.

negativeFolder = fullfile(matlabroot,'toolbox','vision','visiondata','nonStopSigns');

Step 4: Train the detector.

trainCascadeObjectDetector('stopSignDetector.xml',data,negativeFolder,'FalseAlarmRate',0.2,'NumCascadeStages',5);

Computer Vision System Toolbox software returns the following message:

![Descripción: http://es.mathworks.com/help/vision/ug/train\_cascade\_output.jpg](images/00066.jpeg)

All 86 positive samples were used to train each stage. This high rate occurs because the true positive rate is very high relative to the number of positive samples.

**[Train a Five-Stage Stop-Sign Detector with a Decreased True Positive Rate](http://es.mathworks.com/help/vision/ug/train-a-cascade-object-detector.html)**

This example shows you how to train a stop-sign detector on the same data set as the first example, (steps 1–3), but with the TruePositiveRate decreased to 0.98.

Step 4: Train the detector.

trainCascadeObjectDetector('stopSignDetector\_tpr0\_98.xml',data,negativeFolder,...

'FalseAlarmRate',0.2,'NumCascadeStages', 5,...

'TruePositiveRate', 0.98);

![Descripción: http://es.mathworks.com/help/vision/ug/traincascadeobjectdetector\_example2.png](images/00067.jpeg)

Only 79 of the total 86 positive samples were used to train each stage. This lowered rate occurs because the true positive rate was low enough for the function to start rejecting some of the positive samples as false negatives.

**[Train a Ten-Stage Stop-Sign Detector](http://es.mathworks.com/help/vision/ug/train-a-cascade-object-detector.html)**

This example shows you how to train a stop-sign detector on the same data set as the first example, (steps 1–3), but with the number of stages increased to 10.

Step 4: Train the detector.

trainCascadeObjectDetector('stopSignDetector\_10stages.xml',data,negativeFolder,...

'FalseAlarmRate',0.2,'NumCascadeStages',10);

![Descripción: http://es.mathworks.com/help/vision/ug/traincascadeobjectdetector\_example3.png](images/00068.jpeg)

In this case, NegativeSamplesFactor was set to 2, therefore the number of negative samples used to train each stage was 172. Notice that the function generated only 33 negative samples for stage 6 and was not able to train stage 7 at all. This condition occurs because the number of negatives in stage 7 was less than 17, (roughly half of the previous number of negative samples). The function produced a stop-sign detector with 6 stages, instead of the 10 previously specified. The resulting overall false alarm rate is 0.2⁷\=1.28e-05, while the expected false alarm rate is 1.024e-07.

At this point, you can add more negative images, reduce the number of stages, or increase the false positive rate. For example, you can increase the false positive rate, FalseAlarmRate, to 0.5. The expected overall false-positive rate in this case is 0.0039.

Step 4: Train the detector.

trainCascadeObjectDetector('stopSignDetector\_10stages\_far0\_5.xml',data,negativeFolder,...

'FalseAlarmRate',0.5,'NumCascadeStages',10);

![Descripción: http://es.mathworks.com/help/vision/ug/traincascadeobjectdetector\_example4.png](images/00069.jpeg)

This time the function trains eight stages before the threshold reaches the overall false alarm rate of 0.000587108 and training stops.

 

## 5.7.7 Train Stop Sign Detector

Load the positive samples data from a MAT file. The file contains a table specifying bounding boxes for several object categories. The table was exported from the Training Image Labeler app.

Load positive samples.

load('stopSignsAndCars.mat');

Select the bounding boxes for stop signs from the table.

positiveInstances = stopSignsAndCars(:,1:2);

Add the image directory to the MATLAB path.

imDir = fullfile(matlabroot,'toolbox','vision','visiondata',...

    'stopSignImages');

addpath(imDir);

Specify the foler for negative images.

negativeFolder = fullfile(matlabroot,'toolbox','vision','visiondata',...

    'nonStopSigns');

Create an imageDatastore object containing negative images.

negativeImages = imageDatastore(negativeFolder);

Train a cascade object detector called 'stopSignDetector.xml' using HOG features. NOTE: The command can take several minutes to run.

trainCascadeObjectDetector('stopSignDetector.xml',positiveInstances, ...

    negativeFolder,'FalseAlarmRate',0.1,'NumCascadeStages',5);

Automatically setting ObjectTrainingSize to \[ 35, 32 \]

Using at most 42 of 42 positive samples per stage

Using at most 84 negative samples per stage

 

\--cascadeParams--

Training stage 1 of 5

\[........................................................................\]

Used 42 positive and 84 negative samples

Time to train stage 1: 0 seconds

 

Training stage 2 of 5

\[........................................................................\]

Used 42 positive and 84 negative samples

Time to train stage 2: 0 seconds

 

Training stage 3 of 5

\[........................................................................\]

Used 42 positive and 84 negative samples

Time to train stage 3: 2 seconds

 

Training stage 4 of 5

\[........................................................................\]

Used 42 positive and 84 negative samples

Time to train stage 4: 5 seconds

 

Training stage 5 of 5

\[........................................................................\]

Used 42 positive and 17 negative samples

Time to train stage 5: 9 seconds

 

Training complete

Use the newly trained classifier to detect a stop sign in an image.

detector = vision.CascadeObjectDetector('stopSignDetector.xml');

Read the test image.

img = imread('stopSignTest.jpg');

Detect a stop sign.

bbox = step(detector,img);

Insert bounding box rectangles and return the marked image.

 detectedImg = insertObjectAnnotation(img,'rectangle',bbox,'stop sign');

Display the detected stop sign.

figure; imshow(detectedImg);

![Descripción: http://es.mathworks.com/help/examples/vision/win64/TrainAStopSignDetectorExample\_01.png](images/00070.jpeg)

Remove the image directory from the path.

rmpath(imDir);

# 5.8 Image Retrieval with Bag of Visual Words

 

You can use the Computer Vision System Toolbox™ functions to search by image, also known as a content-based image retrieval (CBIR) system. CBIR systems are used to retrieve images from a collection of images that are similar to a query image. The application of these types of systems can be found in many areas such as a web-based product search, surveillance, and visual place identification. First the system searches a collection of images to find the ones that are visually similar to a query image.

The retrieval system uses a bag of visual words, a collection of image descriptors, to represent your data set of images. Images are indexed to create a mapping of visual words. The index maps each visual word to their occurrences in the image set. A comparison between the query image and the index provides the images most similar to the query image. By using the CBIR system workflow, you can evaluate the accuracy for a known set of image search results.

![Descripción: http://es.mathworks.com/help/vision/ug/image\_retrieval.png](images/00071.jpeg)

## 5.8.1 Retrieval System Workflow

1.      **Create image set that represents image features for retrieval**. Use [imageDatastore](http://es.mathworks.com/help/matlab/ref/imagedatastore.html) to store the image data. Use a large number of images that represent various viewpoints of the object. A large and diverse number of images helps train the bag of visual words and increases the accuracy of the image search.

2.      **Type of feature**. The [indexImages](http://es.mathworks.com/help/vision/ref/indeximages.html) function creates the bag of visual words using the speeded up robust features (SURF). For other types of features, you can use a custom extractor, and then use [bagOfFeatures](http://es.mathworks.com/help/vision/ref/bagoffeatures-class.html) to create the bag of visual words.

You can use the original imgSet or a different collection of images for the training set. To use a different collection, create the bag of visual words before creating the image index, using the [bagOfFeatures](http://es.mathworks.com/help/vision/ref/bagoffeatures-class.html) function. The advantage of using the same set of images is that the visual vocabulary is tailored to the search set. The disadvantage of this approach is that the retrieval system must relearn the visual vocabulary to use on a drastically different set of images. With an independent set, the visual vocabulary is better able to handle the additions of new images into the search index.

3.      **Index the images**. The [indexImages](http://es.mathworks.com/help/vision/ref/indeximages.html) function creates a search index that maps visual words to their occurrences in the image collection. When you create the bag of visual words using an independent or subset collection, include the bag as an input argument to indexImages. If you do not create an independent bag of visual words, then the function creates the bag based on the entire imgSet input collection. You can add and remove images directly to and from the image index using the [addImages](http://es.mathworks.com/help/vision/ref/invertedimageindex.addimages.html) and [removeImages](http://es.mathworks.com/help/vision/ref/invertedimageindex.removeimages.html) methods.

4.      **Search data set for similar images**. Use the [retrieveImages](http://es.mathworks.com/help/vision/ref/retrieveimages.html) function to search the image set for images which are similar to the query image. Use the NumResults property to control the number of results. For example, to return the top 10 similar images, set the ROI property to use a smaller region of a query image. A smaller region is useful for isolating a particular object in an image that you want to search for.

## 5.8.2 Evaluate Image Retrieval

Use the [evaluateImageRetrieval](http://es.mathworks.com/help/vision/ref/evaluateimageretrieval.html) function to evaluate image retrieval by using a query image with a known set of results. If the results are not what you expect, you can modify or augment image features by the bag of visual words. Examine the type of the features retrieved. The type of feature used for retrieval depends on the type of images within the collection. For example, if you are searching an image collection made up of scenes, such as beaches, cities, or highways, use a global image feature. A global image feature, such as a color histogram, captures the key elements of the entire scene. To find specific objects within the image collections, use local image features extracted around object keypoints instead.

# 5.9 Image Classification with Bag of Visual  Words

Use the Computer Vision System Toolbox™ functions for image category classification by creating a bag of visual words. The process generates a histogram of visual word occurrences that represent an image. These histograms are used to train an image category classifier. The steps below describe how to setup your images, create the bag of visual words, and then train and apply an image category classifier.

## 5.9.1 Step 1: Set Up Image Category Sets

Organize and partition the images into training and test subsets. Use the [imageDatastore](http://es.mathworks.com/help/matlab/ref/imagedatastore.html) function to store images to use for training an image classifier. Organizing images into categories makes handling large sets of images much easier. You can use the [splitEachLabel](http://es.mathworks.com/help/matlab/ref/datastore.spliteachlabel.html) function to split the images into training and test data.

Read the category images and create image sets.

setDir  = fullfile(toolboxdir('vision'),'visiondata','imageSets');

imds = imageDatastore(setDir,'IncludeSubfolders',true,'LabelSource',...

    'foldernames');

Separate the sets into training and test image subsets. In this example, 30% of the images are partitioned for training and the remainder for testing.

\[trainingSet,testSet\] = splitEachLabel(imds,0.3,'randomize');

![Descripción: http://es.mathworks.com/help/vision/ug/bagoffeatures\_imageset.png](images/00072.jpeg)

## 5.9.2 Step 2: Create Bag of Features

Create a visual vocabulary, or bag of features, by extracting feature descriptors from representative images of each category.

The [bagOfFeatures](http://es.mathworks.com/help/vision/ref/bagoffeatures-class.html) object defines the features, or visual words, by using the [k-means clustering](http://es.mathworks.com/help/stats/k-means-clustering.html#bq_679x-19) (Statistics and Machine Learning Toolbox) algorithm on the feature descriptors extracted from trainingSets. The algorithm iteratively groups the descriptors into *k* mutually exclusive clusters. The resulting clusters are compact and separated by similar characteristics. Each cluster center represents a feature, or visual word.

You can extract features based on a feature detector, or you can define a grid to extract feature descriptors. The grid method may lose fine-grained scale information. Therefore, use the grid for images that do not contain distinct features, such as an image containing scenery, like the beach. Using speeded up robust features (or SURF) detector provides greater scale invariance. By default, the algorithm runs the 'grid' method.

![Descripción: http://es.mathworks.com/help/vision/ug/bagoffeatures\_visualwordsoverview.png](images/00073.jpeg)

This algorithm workflow analyzes images in their entirety. Images must have appropriate labels describing the class that they represent. For example, a set of car images could be labeled cars. The workflow does not rely on spatial information nor on marking the particular objects in an image. The bag-of-visual-words technique relies on detection without localization.

## 5.9.3 Step 3: Train an Image Classifier With Bag of Visual Words

The [trainImageCategoryClassifier](http://es.mathworks.com/help/vision/ref/trainimagecategoryclassifier.html) function returns an image classifier. The function trains a multiclass classifier using the error-correcting output codes (ECOC) framework with binary support vector machine (SVM) classifiers. The trainImageCategoryClassfier function uses the bag of visual words returned by the [bagOfFeatures](http://es.mathworks.com/help/vision/ref/bagoffeatures-class.html) object to encode images in the image set into the histogram of visual words. The histogram of visual words are then used as the positive and negative samples to train the classifier.

1.      Use the [bagOfFeatures](http://es.mathworks.com/help/vision/ref/bagoffeatures-class.html) encode method to encode each image from the training set. This function detects and extracts features from the image and then uses the approximate nearest neighbor algorithm to construct a feature histogram for each image. The function then increments histogram bins based on the proximity of the descriptor to a particular cluster center. The histogram length corresponds to the number of visual words that the [bagOfFeatures](http://es.mathworks.com/help/vision/ref/bagoffeatures-class.html)object constructed. The histogram becomes a feature vector for the image.

![Descripción: http://es.mathworks.com/help/vision/ug/bagoffeatures\_encodeoverview.png](images/00074.jpeg)

2.                Repeat step 1 for each image in the training set to create the training data.

![Descripción: http://es.mathworks.com/help/vision/ug/bagoffeatures\_bofclassify.png](images/00075.jpeg)

3.                Evaluate the quality of the classifier. Use the [imageCategoryClassifier](http://es.mathworks.com/help/vision/ref/imagecategoryclassifier-class.html) evaluate method to test the classifier against the validation image set. The output confusion matrix represents the analysis of the prediction. A perfect classification results in a normalized matrix containing 1s on the diagonal. An incorrect classification results fractional values.

![Descripción: http://es.mathworks.com/help/vision/ug/bagoffeatures\_bofevaluate.png](images/00076.jpeg)

## 5.9.4 Step 4: Classify an Image or Image Set

Use the [imageCategoryClassifier](http://es.mathworks.com/help/vision/ref/imagecategoryclassifier-class.html) predict method on a new image to determine its category.

# 5.10 Digit Classification Using HOG Features

 

This example shows how to classify digits using HOG features and a multiclass SVM classifier.

Object classification is an important task in many computer vision applications, including surveillance, automotive safety, and image retrieval. For example, in an automotive safety application, you may need to classify nearby objects as pedestrians or vehicles. Regardless of the type of object being classified, the basic procedure for creating an object classifier is:

·        Acquire a labeled data set with images of the desired object.

·        Partition the data set into a training set and a test set.

·        Train the classifier using features extracted from the training set.

·        Test the classifier using features extracted from the test set.

To illustrate, this example shows how to classify numerical digits using HOG (Histogram of Oriented Gradient) features \[1\] and a multiclass SVM (Support Vector Machine) classifier. This type of classification is often used in many Optical Character Recognition (OCR) applications.

The example uses the fitcecoc function from the Statistics and Machine Learning Toolbox™ and the extractHOGFeatures function from the Computer Vision System Toolbox™.

## 5.10.1 Digit Data Set

Synthetic digit images are used for training. The training images each contain a digit surrounded by other digits, which mimics how digits are normally seen together. Using synthetic images is convenient and it enables the creation of a variety of training samples without having to manually collect them. For testing, scans of handwritten digits are used to validate how well the classifier performs on data that is different than the training data. Although this is not the most representative data set, there is enough data to train and test a classifier, and show the feasibility of the approach.

% Load training and test data using |imageDatastore|.

syntheticDir   = fullfile(toolboxdir('vision'), 'visiondata','digits','synthetic');

handwrittenDir = fullfile(toolboxdir('vision'), 'visiondata','digits','handwritten');

 

% |imageDatastore| recursively scans the directory tree containing the

% images. Folder names are automatically used as labels for each image.

trainingSet = imageDatastore(syntheticDir,   'IncludeSubfolders', true, 'LabelSource', 'foldernames');

testSet     = imageDatastore(handwrittenDir, 'IncludeSubfolders', true, 'LabelSource', 'foldernames');

Use countEachLabel to tabulate the number of images associated with each label. In this example, the training set consists of 101 images for each of the 10 digits. The test set consists of 12 images per digit.

countEachLabel(trainingSet)

ans =

 

  10×2 table

 

    Label    Count

    \_\_\_\_\_    \_\_\_\_\_

 

    0        101  

    1        101  

    2        101  

    3        101  

    4        101  

    5        101  

    6        101  

    7        101  

    8        101  

    9        101  

 

countEachLabel(testSet)

ans =

 

  10×2 table

 

    Label    Count

    \_\_\_\_\_    \_\_\_\_\_

 

    0        12   

    1        12   

    2        12   

    3        12   

    4        12   

    5        12   

    6        12   

    7        12   

    8        12   

    9        12   

 

Show a few of the training and test images

figure;

 

subplot(2,3,1);

imshow(trainingSet.Files{102});

 

subplot(2,3,2);

imshow(trainingSet.Files{304});

 

subplot(2,3,3);

imshow(trainingSet.Files{809});

 

subplot(2,3,4);

imshow(testSet.Files{13});

 

subplot(2,3,5);

imshow(testSet.Files{37});

 

subplot(2,3,6);

imshow(testSet.Files{97});

![Descripción: http://es.mathworks.com/help/examples/vision\_product/win64/HOGDigitClassificationExample\_01.png](images/00077.jpeg)

Prior to training and testing a classifier, a pre-processing step is applied to remove noise artifacts introduced while collecting the image samples. This provides better feature vectors for training the classifier.

% Show pre-processing results

exTestImage = readimage(testSet,37);

processedImage = imbinarize(rgb2gray(exTestImage));

 

figure;

 

subplot(1,2,1)

imshow(exTestImage)

 

subplot(1,2,2)

imshow(processedImage)

![](images/00078.jpeg)

## 5.10.2 Using HOG Features

The data used to train the classifier are HOG feature vectors extracted from the training images. Therefore, it is important to make sure the HOG feature vector encodes the right amount of information about the object. The extractHOGFeaturesfunction returns a visualization output that can help form some intuition about just what the "right amount of information" means. By varying the HOG cell size parameter and visualizing the result, you can see the effect the cell size parameter has on the amount of shape information encoded in the feature vector:

img = readimage(trainingSet, 206);

 

% Extract HOG features and HOG visualization

\[hog\_2x2, vis2x2\] = extractHOGFeatures(img,'CellSize',\[2 2\]);

\[hog\_4x4, vis4x4\] = extractHOGFeatures(img,'CellSize',\[4 4\]);

\[hog\_8x8, vis8x8\] = extractHOGFeatures(img,'CellSize',\[8 8\]);

 

% Show the original image

figure;

subplot(2,3,1:3); imshow(img);

 

% Visualize the HOG features

subplot(2,3,4);

plot(vis2x2);

title({'CellSize = \[2 2\]'; \['Length = ' num2str(length(hog\_2x2))\]});

 

subplot(2,3,5);

plot(vis4x4);

title({'CellSize = \[4 4\]'; \['Length = ' num2str(length(hog\_4x4))\]});

 

subplot(2,3,6);

plot(vis8x8);

title({'CellSize = \[8 8\]'; \['Length = ' num2str(length(hog\_8x8))\]});

![Descripción: http://es.mathworks.com/help/examples/vision\_product/win64/HOGDigitClassificationExample\_03.png](images/00079.jpeg)

The visualization shows that a cell size of \[8 8\] does not encode much shape information, while a cell size of \[2 2\] encodes a lot of shape information but increases the dimensionality of the HOG feature vector significantly. A good compromise is a 4-by-4 cell size. This size setting encodes enough spatial information to visually identify a digit shape while limiting the number of dimensions in the HOG feature vector, which helps speed up training. In practice, the HOG parameters should be varied with repeated classifier training and testing to identify the optimal parameter settings.

cellSize = \[4 4\];

hogFeatureSize = length(hog\_4x4);

## 5.10.3 Train a Digit Classifier

Digit classification is a multiclass classification problem, where you have to classify an image into one out of the ten possible digit classes. In this example, the fitcecoc function from the Statistics and Machine Learning Toolbox™ is used to create a multiclass classifier using binary SVMs.

Start by extracting HOG features from the training set. These features will be used to train the classifier.

% Loop over the trainingSet and extract HOG features from each image. A

% similar procedure will be used to extract features from the testSet.

 

numImages = numel(trainingSet.Files);

trainingFeatures = zeros(numImages, hogFeatureSize, 'single');

 

for i = 1:numImages

    img = readimage(trainingSet, i);

 

    img = rgb2gray(img);

 

    % Apply pre-processing steps

    img = imbinarize(img);

 

    trainingFeatures(i, :) = extractHOGFeatures(img, 'CellSize', cellSize);

end

 

% Get labels for each image.

trainingLabels = trainingSet.Labels;

Next, train a classifier using the extracted features.

% fitcecoc uses SVM learners and a 'One-vs-One' encoding scheme.

classifier = fitcecoc(trainingFeatures, trainingLabels);

## 5.10.4 Evaluate the Digit Classifier

Evaluate the digit classifier using images from the test set, and generate a confusion matrix to quantify the classifier accuracy.

As in the training step, first extract HOG features from the test images. These features will be used to make predictions using the trained classifier.

% Extract HOG features from the test set. The procedure is similar to what

% was shown earlier and is encapsulated as a helper function for brevity.

\[testFeatures, testLabels\] = helperExtractHOGFeaturesFromImageSet(testSet, hogFeatureSize, cellSize);

 

% Make class predictions using the test features.

predictedLabels = predict(classifier, testFeatures);

 

% Tabulate the results using a confusion matrix.

confMat = confusionmat(testLabels, predictedLabels);

 

helperDisplayConfusionMatrix(confMat)

digit  | 0        1        2        3        4        5        6        7        8        9        

\---------------------------------------------------------------------------------------------------

0      | 0.25     0.00     0.08     0.00     0.00     0.00     0.58     0.00     0.08     0.00     

1      | 0.00     0.75     0.00     0.00     0.08     0.00     0.00     0.08     0.08     0.00     

2      | 0.00     0.00     0.67     0.17     0.00     0.00     0.08     0.00     0.00     0.08     

3      | 0.00     0.00     0.00     0.58     0.00     0.00     0.33     0.00     0.00     0.08     

4      | 0.00     0.08     0.00     0.17     0.75     0.00     0.00     0.00     0.00     0.00     

5      | 0.00     0.00     0.00     0.00     0.00     0.33     0.58     0.00     0.08     0.00     

6      | 0.00     0.00     0.00     0.00     0.25     0.00     0.67     0.00     0.08     0.00     

7      | 0.00     0.08     0.08     0.33     0.00     0.00     0.17     0.25     0.00     0.08     

8      | 0.00     0.00     0.00     0.08     0.00     0.00     0.00     0.08     0.67     0.17     

9      | 0.00     0.08     0.00     0.25     0.17     0.00     0.08     0.00     0.00     0.42     

The table shows the confusion matrix in percentage form. The columns of the matrix represent the predicted labels, while the rows represent the known labels. For this test set, digit 0 is often misclassified as 6, most likely due to their similar shapes. Similar errors are seen for 9 and 3. Training with a more representative data set like MNIST \[2\] or SVHN \[3\], which contain thousands of handwritten characters, is likely to produce a better classifier compared with the one created using this synthetic data set.

## 5.10.5 Summary

This example illustrated the basic procedure for creating a multiclass object classifier using the extractHOGfeaturesfunction from the Computer Vision System Toolbox and the fitcecoc function from the Statistics and Machine Learning Toolbox™. Although HOG features and an ECOC classifier were used here, other features and machine learning algorithms can be used in the same way. For instance, you can explore using different feature types for training the classifier; or you can see the effect of using other machine learning algorithms available in the Statistics and Machine Learning Toolbox™ such as k-nearest neighbors.

# 5.11 Image Category Classification Using Bag of Features

 

This example shows how to use a bag of features approach for image category classification. This technique is also often referred to as bag of words. Visual image categorization is a process of assigning a category label to an image under test. Categories may contain images representing just about anything, for example, dogs, cats, trains, boats.

## 5.11.1 Download Caltech101 Image Set

To learn about bag of features image category classification, you will first download a suitable image data set. One of the most widely cited and used data sets is [Caltech 101](http://www.vision.caltech.edu/Image_Datasets/Caltech101), collected by Fei-Fei Li, Marco Andreetto, and Marc 'Aurelio Ranzato.

% Location of the compressed data set

url = 'http://www.vision.caltech.edu/Image\_Datasets/Caltech101/101\_ObjectCategories.tar.gz';

% Store the output in a temporary folder

outputFolder = fullfile(tempdir, 'caltech101'); % define output folder

Note that downloading the set from the web can take a very long time depending on your Internet connection. It can be 30 minutes or more since the set contains 126MB of data. The commands below will block MATLAB for that period of time. Alternatively, you can use your web browser to first download the set to your local disk. If you choose that route, re-point the 'url' variable above to the file that you downloaded.

if ~exist(outputFolder, 'dir') % download only once

    disp('Downloading 126MB Caltech101 data set...');

    untar(url, outputFolder);

end

## 5.11.2 Load Image Sets

Instead of operating on the entire Caltech 101 set, which can be time consuming, use three categories: airplanes, ferry, and laptop. Note that for the bag of features approach to be effective, majority of each image's area must be occupied by the subject of the category, for example, an object or a type of scene.

rootFolder = fullfile(outputFolder, '101\_ObjectCategories');

Construct an ImageDatastore based on the following categories from Caltech 101: 'airplanes', 'ferry', 'laptop'. Use imageDatastore to help you manage the data. Since imageDatastore operates on image file locations, and therefore does not load all the images into memory, it is safe to use on large image collections.

categories = {'airplanes', 'ferry', 'laptop'};

imds = imageDatastore(fullfile(rootFolder, categories), 'LabelSource', 'foldernames');

You can easily inspect the number of images per category as well as category labels as shown below:

tbl = countEachLabel(imds)

tbl =

 

  3×2 table

 

      Label      Count

    \_\_\_\_\_\_\_\_\_    \_\_\_\_\_

 

    airplanes    800  

    ferry         67  

    laptop        81  

 

Note that the labels were derived from directory names used to construct the ImageDatastore, but can be customized by manually setting the Labels property of the ImageDatastore object.

## 5.11.3 Prepare Training and Validation Image Sets

Since imds above contains an unequal number of images per category, let's first adjust it, so that the number of images in the training set is balanced.

minSetCount = min(tbl{:,2}); % determine the smallest amount of images in a category

 

% Use splitEachLabel method to trim the set.

imds = splitEachLabel(imds, minSetCount, 'randomize');

 

% Notice that each set now has exactly the same number of images.

countEachLabel(imds)

ans =

 

  3×2 table

 

      Label      Count

    \_\_\_\_\_\_\_\_\_    \_\_\_\_\_

 

    airplanes    67   

    ferry        67   

    laptop       67   

 

Separate the sets into training and validation data. Pick 30% of images from each set for the training data and the remainder, 70%, for the validation data. Randomize the split to avoid biasing the results.

\[trainingSet, validationSet\] = splitEachLabel(imds, 0.3, 'randomize');

The above call returns two imageDatastore objects ready for training and validation tasks. Below, you can see example images from the three categories included in the training data.

% Find the first instance of an image for each category

airplanes = find(trainingSet.Labels == 'airplanes', 1);

ferry = find(trainingSet.Labels == 'ferry', 1);

laptop = find(trainingSet.Labels == 'laptop', 1);

 

% figure

 

subplot(1,3,1);

imshow(readimage(trainingSet,airplanes))

subplot(1,3,2);

imshow(readimage(trainingSet,ferry))

subplot(1,3,3);

imshow(readimage(trainingSet,laptop))

![](images/00080.jpeg)

## 5.11.4 Create a Visual Vocabulary and Train an Image Category Classifier

Bag of words is a technique adapted to computer vision from the world of natural language processing. Since images do not actually contain discrete words, we first construct a "vocabulary" of [SURF](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX) features representative of each image category.

This is accomplished with a single call to bagOfFeatures function, which:

1.                extracts SURF features from all images in all image categories

2.                constructs the visual vocabulary by reducing the number of features through quantization of feature space using K-means clustering

bag = bagOfFeatures(trainingSet);

Creating Bag-Of-Features.

\-------------------------

\* Image category 1: airplanes

\* Image category 2: ferry

\* Image category 3: laptop

\* Selecting feature point locations using the Grid method.

\* Extracting SURF features from the selected feature point locations.

\*\* The GridStep is \[8 8\] and the BlockWidth is \[32 64 96 128\].

 

\* Extracting features from 60 images...done. Extracted 247480 features.

\* Keeping 80 percent of the strongest features from each category.

\* Balancing the number of features across all image categories to improve clustering.

\*\* Image category 2 has the least number of strongest features: 58003.

\*\* Using the strongest 58003 features from each of the other image categories.

 

\* Using K-Means clustering to create a 500 word visual vocabulary.

\* Number of features          : 174009

\* Number of clusters (K)      : 500

\* Initializing cluster centers...100.00%.

\* Clustering...completed 39/100 iterations (~0.41 seconds/iteration)...converged in 39 iterations.

\* Finished creating Bag-Of-Features

 

Additionally, the bagOfFeatures object provides an encode method for counting the visual word occurrences in an image. It produced a histogram that becomes a new and reduced representation of an image.

img = readimage(imds, 1);

featureVector = encode(bag, img);

 

% Plot the histogram of visual word occurrences

figure

bar(featureVector)

title('Visual word occurrences')

xlabel('Visual word index')

ylabel('Frequency of occurrence')

![Descripción: http://es.mathworks.com/help/examples/vision\_product/win64/ImageCategoryClassificationExample\_02.png](images/00081.jpeg)

This histogram forms a basis for training a classifier and for the actual image classification. In essence, it encodes an image into a feature vector.

Encoded training images from each category are fed into a classifier training process invoked by the trainImageCategoryClassifier function. Note that this function relies on the multiclass linear SVM classifier from the Statistics and Machine Learning Toolbox™.

categoryClassifier = trainImageCategoryClassifier(trainingSet, bag);

Training an image category classifier for 3 categories.

\--------------------------------------------------------

\* Category 1: airplanes

\* Category 2: ferry

\* Category 3: laptop

 

\* Encoding features for 60 images...done.

 

\* Finished training the category classifier. Use evaluate to test the classifier on a test set.

 

The above function utilizes the encode method of the input bag object to formulate feature vectors representing each image category from the trainingSet.

## 5.11.5 Evaluate Classifier Performance

Now that we have a trained classifier, categoryClassifier, let's evaluate it. As a sanity check, let's first test it with the training set, which should produce near perfect confusion matrix, i.e. ones on the diagonal.

confMatrix = evaluate(categoryClassifier, trainingSet);

Evaluating image category classifier for 3 categories.

\-------------------------------------------------------

\* Category 1: airplanes

\* Category 2: ferry

\* Category 3: laptop

 

\* Evaluating 60 images...done.

 

\* Finished evaluating all the test sets.

 

\* The confusion matrix for this test set is:

 

                        PREDICTED

KNOWN        | airplanes   ferry   laptop   

\--------------------------------------------

airplanes    | 0.95        0.05    0.00     

ferry        | 0.00        1.00    0.00     

laptop       | 0.05        0.00    0.95     

 

\* Average Accuracy is 0.97.

 

Next, let's evaluate the classifier on the validationSet, which was not used during the training. By default, the evaluatefunction returns the confusion matrix, which is a good initial indicator of how well the classifier is performing.

confMatrix = evaluate(categoryClassifier, validationSet);

 

% Compute average accuracy

mean(diag(confMatrix));

Evaluating image category classifier for 3 categories.

\-------------------------------------------------------

 

\* Category 1: airplanes

\* Category 2: ferry

\* Category 3: laptop

 

\* Evaluating 141 images...done.

 

\* Finished evaluating all the test sets.

 

\* The confusion matrix for this test set is:

 

 

                        PREDICTED

KNOWN        | airplanes   ferry   laptop   

\--------------------------------------------

airplanes    | 0.83        0.13    0.04     

ferry        | 0.02        0.98    0.00     

laptop       | 0.04        0.00    0.96     

 

\* Average Accuracy is 0.92.

 

Additional statistics can be derived using the rest of arguments returned by the evaluate function. See help for imageCategoryClassifier/evaluate. You can tweak the various parameters and continue evaluating the trained classifier until you are satisfied with the results.

## 5.11.6 Try the Newly Trained Classifier on Test Images

You can now apply the newly trained classifier to categorize new images.

img = imread(fullfile(rootFolder, 'airplanes', 'image\_0690.jpg'));

\[labelIdx, scores\] = predict(categoryClassifier, img);

 

% Display the string label

categoryClassifier.Labels(labelIdx)

ans =

 

  cell

 

    'airplanes'

# 5.12 Image Retrieval Using Customized Bag of Features

 

This example shows how to create a Content Based Image Retrieval (CBIR) system using a customized bag-of-features workflow.

## 5.12.1 Introduction

Content Based Image Retrieval (CBIR) systems are used to find images that are visually similar to a query image. The application of CBIR systems can be found in many areas such as a web-based product search, surveillance, and visual place identification. A common technique used to implement a CBIR system is bag of visual words, also known as bag of features\[1,2\]. Bag of features is a technique adapted to image retrieval from the world of document retrieval. Instead of using actual words as in document retrieval, bag of features uses image features as the visual words that describe an image.

Image features are an important part of CBIR systems. These image features are used to gauge similarity between images and can include global image features such as color, texture, and shape. Image features can also be local image features such as speeded up robust features (SURF), histogram of gradients (HOG), or local binary patterns (LBP). The benefit of the bag-of-features approach is that the type of features used to create the visual word vocabulary can be customized to fit the application.

The speed and efficiency of image search is also important in CBIR systems. For example, it may be acceptable to perform a brute force search in a small collection of images of less than a 100 images, where features from the query image are compared to features from each image in the collection. For larger collections, a brute force search is not feasible and more efficient search techniques must be used. The bag of features provides a concise encoding scheme to represent a large collection of images using a sparse set of visual word histograms. This enables compact storage and efficient search through an inverted index data structure.

The Computer Vision System Toolbox™ provides a customizable bag-of-features framework to implement an image retrieval system. The following steps outline the procedure:

1.                Select the Image Features for Retrieval

2.                Create a Bag Of Features

3.                Index the Images

4.                Search for Similar Images

In this example, you will go through these steps to create an image retrieval system for searching the 17 Category Flower Dataset\[3\]. This dataset contains about 1300 images of 17 different types of flowers.

Download this dataset for use in the rest of this example.

% Location of the compressed data set

url = 'http://www.robots.ox.ac.uk/~vgg/data/flowers/17/17flowers.tgz';

 

% Store the output in a temporary folder

outputFolder = fullfile(tempdir, '17Flowers'); % define output folder

Note that downloading the dataset from the web can take a very long time depending on your Internet connection. The commands below will block MATLAB for that period of time. Alternatively, you can use your web browser to first download the set to your local disk. If you choose that route, re-point the 'url' variable above to the file that you downloaded.

if ~exist(outputFolder, 'dir') % download only once

    disp('Downloading 17-Category Flower Dataset (58 MB)...');

    untar(url, outputFolder);

end

 

flowerImageSet = imageDatastore(fullfile(outputFolder,'jpg'),'LabelSource','foldernames');

 

% Total number of images in the data set

numel(flowerImageSet.Files)

ans =

 

        1360

 

## 5.12.2 Step 1 - Select the Image Features for Retrieval

The type of feature used for retrieval depends on the type of images within the collection. For example, if searching an image collection made up of scenes (beaches, cities, highways), it is preferable to use a global image feature, such as a color histogram that captures the color content of the entire scene. However, if the goal is to find specific objects within the image collections, then local image features extracted around object keypoints are a better choice.

Let's start by viewing a few of the images to get an idea of how to approach the problem.

% Display a few of the flower images

helperDisplayImageMontage(flowerImageSet.Files(1:50:1000));

![Descripción: http://es.mathworks.com/help/examples/vision\_product/win64/ImageRetrievalExample\_01.png](images/00082.jpeg)

In this example, the goal is to search for similar flowers in the dataset using the color information in the query image. The images in the dataset contain one kind of flower in every image. Therefore, a simple image feature based on the spatial layout of color is a good place to start.

The following function describes the algorithm used to extract color features from a given image. This function will be used as a [custom feature extractor](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX) within bagOfFeatures to extract color features.

type exampleBagOfFeaturesColorExtractor.m

function \[features, metrics\] = exampleBagOfFeaturesColorExtractor(I) 

% Example color layout feature extractor. Designed for use with bagOfFeatures.

%

% Local color layout features are extracted from truecolor image, I and

% returned in features. The strength of the features are returned in

% metrics.

 

\[~,~,P\] = size(I);

 

isColorImage = P == 3; 

 

if isColorImage

    

    % Convert RGB images to the L\*a\*b\* colorspace. The L\*a\*b\* colorspace

    % enables you to easily quantify the visual differences between colors.

    % Visually similar colors in the L\*a\*b\* colorspace will have small

    % differences in their L\*a\*b\* values.

    Ilab = rgb2lab(I);                                                                             

      

    % Compute the "average" L\*a\*b\* color within 16-by-16 pixel blocks. The

    % average value is used as the color portion of the image feature. An

    % efficient method to approximate this averaging procedure over

    % 16-by-16 pixel blocks is to reduce the size of the image by a factor

    % of 16 using IMRESIZE. 

    Ilab = imresize(Ilab, 1/16);

    

    % Note, the average pixel value in a block can also be computed using

    % standard block processing or integral images.

    

    % Reshape L\*a\*b\* image into "number of features"-by-3 matrix.

    \[Mr,Nr,~\] = size(Ilab);    

    colorFeatures = reshape(Ilab, Mr\*Nr, \[\]); 

           

    % L2 normalize color features

    rowNorm = sqrt(sum(colorFeatures.^2,2));

    colorFeatures = bsxfun(@rdivide, colorFeatures, rowNorm + eps);

        

    % Augment the color feature by appending the \[x y\] location within the

    % image from which the color feature was extracted. This technique is

    % known as spatial augmentation. Spatial augmentation incorporates the

    % spatial layout of the features within an image as part of the

    % extracted feature vectors. Therefore, for two images to have similar

    % color features, the color and spatial distribution of color must be

    % similar.

    

    % Normalize pixel coordinates to handle different image sizes.

    xnorm = linspace(-0.5, 0.5, Nr);      

    ynorm = linspace(-0.5, 0.5, Mr);    

    \[x, y\] = meshgrid(xnorm, ynorm);

    

    % Concatenate the spatial locations and color features.

    features = \[colorFeatures y(:) x(:)\];

    

    % Use color variance as feature metric.

    metrics  = var(colorFeatures(:,1:3),0,2);

else

    

    % Return empty features for non-color images. These features are

    % ignored by bagOfFeatures.

    features = zeros(0,5);

    metrics  = zeros(0,1);     

end

 

## 5.12.3 Step 2 - Create a Bag Of Features

With the feature type defined, the next step is to learn the visual vocabulary within the bagOfFeatures using a set of training images. The code shown below picks a random subset of images from the dataset for training and then trains bagOfFeatures using the 'CustomExtractor' option.

% Pick a random subset of the flower images

% trainingSet = splitEachLabel(flowerImageSet, 0.4, 'randomized');

%

% Create a custom bag of features using the 'CustomExtractor' option

% colorBag = bagOfFeatures(trainingSet, ...

%   'CustomExtractor', @exampleBagOfFeaturesColorExtractor, ...

%   'VocabularySize', 10000);

The previous code is commented out because the training process takes several minutes. The rest of the example uses a pre-trained bagOfFeatures to save time. If you wish to recreate colorBag locally, consider [enabling parallel computing](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX) to reduce processing time.

% Load pre-trained bagOfFeatures

load('savedColorBagOfFeatures.mat','colorBag');

## 5.12.4 Step 3 - Index the Images

Now that the bagOfFeatures is created, the entire flower image set can be indexed for search. The indexing procedure extracts features from each image using the custom extractor function from step 1. The extracted features are encoded into a visual word histogram and added into the image index.

% Create a search index

% flowerImageIndex = indexImages(flowerImageSet, colorBag, 'SaveFeatureLocations', false);

Because the indexing step processes thousands of images, the rest of this example uses a saved index to save time. You may recreate the index locally by running the code shown above. Consider [enabling parallel computing](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX) to reduce processing time.

% Load the pre-saved index

load('savedColorBagOfFeatures.mat', 'flowerImageIndex');

## 5.12.5 Step 4 - Search for Similar Images

The final step is to use the retrieveImages function to search for similar images.

% Define a query image

queryImage = readimage(flowerImageSet, 502);

 

figure

imshow(queryImage)

 

% Search for the top 20 images with similar color content

\[imageIDs, scores\] = retrieveImages(queryImage, flowerImageIndex);

![Descripción: http://es.mathworks.com/help/examples/vision\_product/win64/ImageRetrievalExample\_02.png](images/00083.jpeg)

retrieveImages returns the image IDs and the scores of each result. The scores are sorted from best to worst.

scores

scores =

 

    0.9463

    0.2838

    0.2814

    0.2694

    0.2647

    0.2635

    0.2443

    0.2432

    0.2370

    0.2212

    0.2198

    0.2176

    0.2175

    0.2164

    0.2131

    0.2048

    0.2038

    0.2032

    0.2031

    0.2022

 

The imageIDs correspond to the images within the image set that are similar to the query image.

% Display results using montage. Resize images to thumbnails first.

helperDisplayImageMontage(flowerImageSet.Files(imageIDs))

![Descripción: http://es.mathworks.com/help/examples/vision\_product/win64/ImageRetrievalExample\_03.png](images/00084.jpeg)

flowerImageIndex contains several index statistics that are relevant to search. One of these is the 'WordFrequency' property. It contains the percentage of images in which each visual word occurs. This shows you which words are more common as well as which ones are rare across the entire dataset. It is often helpful to suppress the most common words as these do not help us reduce the search set when looking for the most relevant images. Conversely, it is also helpful to suppress very rare words as they may be coming from outliers in the image set. You can control how much the upper and lower ends of the visual word distribution effects the search results by tuning the 'WordFrequencyRange' property. A good way to set this value is to plot the sorted WordFrequency values.

figure

plot(sort(flowerImageIndex.WordFrequency))

![Descripción: http://es.mathworks.com/help/examples/vision\_product/win64/ImageRetrievalExample\_04.png](images/00085.jpeg)

The plot shows that the distribution of visual words reaches its peak at around 45%. This means that only a few visual words are in 45% of the images. If the upper part of the distribution is at 80% or 90%, then it's best to exclude those via the 'WordFrequencyRange' property, and run the search again. For example, let's lower the upper range to 20% and check the effects on the search results.

% Lower WordFrequencyRange

flowerImageIndex.WordFrequencyRange = \[0.01 0.2\];

 

% Re-run retrieval

\[imageIDs, scores\] = retrieveImages(queryImage, flowerImageIndex);

 

% Show results

helperDisplayImageMontage(flowerImageSet.Files(imageIDs))

![Descripción: http://es.mathworks.com/help/examples/vision\_product/win64/ImageRetrievalExample\_05.png](images/00086.jpeg)

In this case, because the upper range is near 45%, a setting of 20% is going to prevent a lot of relevant matches from appearing in the search results. This is confirmed by the poor search results.

## 5.12.6 Conclusion

This example showed you how to customize the bagOfFeatures and how to use indexImages and retrieveImages to create an image retrieval system based on color features. The techniques shown here may be extended to other feature types by further customizing the features used within bagOfFeatures.

 

  

6Chapter 6

LOCAL FEATURES, PATTERN MATCHING AND OPTICAL CHARACTER RECOGNITION

# 6.1 Local Feature Detection and Extraction

 

Local features and their descriptors, which are a compact vector representations of a local neighborhood, are the building blocks of many computer vision algorithms. Their applications include image registration, object detection and classification, tracking, and motion estimation. Using local features enables these algorithms to better handle scale changes, rotation, and occlusion. The Computer Vision System Toolbox™ provides the FAST, Harris, and Shi & Tomasi methods for detecting corner features, and the SURF and MSER methods for detecting blob features. The toolbox includes the SURF, FREAK, BRISK, and HOG descriptors. You can mix and match the detectors and the descriptors depending on the requirements of your application.

## 6.1.1 What Are Local Features?

Local features refer to a pattern or distinct structure found in an image, such as a point, edge, or small image patch. They are usually associated with an image patch that differs from its immediate surroundings by texture, color, or intensity. What the feature actually represents does not matter, just that it is distinct from its surroundings. Examples of local features are blobs, corners, and edge pixels.

**Example of Corner Detection**

`I = imread('circuit.tif');``corners = detectFASTFeatures(I,'MinContrast',0.1);``J = insertMarker(I,corners,'circle');``imshow(J);` 

![](images/00087.gif)

## 6.1.2 Benefits and Applications of Local Features

Local features let you find image correspondences regardless of occlusion, changes in viewing conditions, or the presence of clutter. In addition, the properties of local features make them suitable for image classification, such as in Image Classification with Bag of Visual Words.

Local features are used in two fundamental ways:

·        To localize anchor points for use in image stitching or 3-D reconstruction.

·        To represent image contents compactly for detection or classification, without requiring image segmentation.

 

## 6.1.3 What Makes a Good Local Feature?

Detectors that rely on gradient-based and intensity variation approaches detect good local features. These features include edges, blobs, and regions. Good local features exhibit the following properties:

·        **Repeatable detections**:  
When given two images of the same scene, most features that the detector finds in both images are the same. The features are robust to changes in viewing conditions and noise.

·        **Distinctive**:   
The neighborhood around the feature center varies enough to allow for a reliable comparison between the features.

·        **Localizable**:   
The feature has a unique location assigned to it. Changes in viewing conditions do not affect its location.

## 6.1.4 Feature Detection and Feature Extraction

*Feature detection* selects regions of an image that have unique content, such as corners or blobs. Use feature detection to find points of interest that you can use for further processing. These points do not necessarily correspond to physical structures, such as the corners of a table. The key to feature detection is to find features that remain locally invariant so that you can detect them even in the presence of rotation or scale change.

*Feature extraction* involves computing a descriptor, which is typically done on regions centered around detected features. Descriptors rely on image processing to transform a local pixel neighborhood into a compact vector representation. This new representation permits comparison between neighborhoods regardless of changes in scale or orientation. Descriptors, such as SIFT or SURF, rely on local gradient computations. Binary descriptors, such as BRISK or FREAK, rely on pairs of local intensity differences, which are then encoded into a binary vector.

## 6.1.5 Choose a Feature Detector and Descriptor

Select the best feature detector and descriptor by considering the criteria of your application and the nature of your data. The first table helps you understand the general criteria to drive your selection. The next two tables provide details on the detectors and descriptors available in Computer Vision System Toolbox™.

**Considerations for Selecting a Detector and Descriptor**

 
| **Criteria** || **Suggestion** |
| --- | --- |
| Type of features in your image || Use a detector appropriate for your data. For example, if your image contains an image of bacteria cells, use the blob detector rather than the corner detector. If your image is an aerial view of a city, you can use the corner detector to find man-made structures. |
| Context in which you are using the features:Matching key pointsClassification || The HOG and SURF descriptors are suitable for classification tasks. In contrast, binary descriptors, such as BRISK and FREAK, are typically used for finding point correspondences between images, which are used for registration. |
| Type of distortion present in your image || Choose a detector and descriptor that addresses the distortion in your data. For example, if there is no scale change present, consider a corner detector that does not handle scale. If your data contains a higher level of distortion, such as scale and rotation, then use the more computationally intensive SURF feature detector and descriptor. |
| Performance requirements:.Real-time performance required.Accuracy versus speed || Binary descriptors are generally faster but less accurate than gradient-based descriptors. For greater accuracy, use several detectors and descriptors at the same time. |

**Choose a Detection Function Based on Feature Type**

 
| **Detector** || **Feature Type** || **Function** || **Scale Independent** |
| --- | --- | --- | --- |
| FAST  || Corner || [`detectFASTFeatures`](http://es.mathworks.com/help/vision/ref/detectfastfeatures.html) || No |
| Minimum eigenvalue algorithm || Corner || [`detectMinEigenFeatures`](http://es.mathworks.com/help/vision/ref/detectmineigenfeatures.html) || No |
| Corner detector  || Corner || [`detectHarrisFeatures`](http://es.mathworks.com/help/vision/ref/detectharrisfeatures.html) || No |
| SURF  || Blob || [`detectSURFFeatures`](http://es.mathworks.com/help/vision/ref/detectsurffeatures.html) || Yes |
| BRISK  || Corner || [`detectBRISKFeatures`](http://es.mathworks.com/help/vision/ref/detectbriskfeatures.html) || Yes |
| MSER  || Region with uniform intensity || [`detectMSERFeatures`](http://es.mathworks.com/help/vision/ref/detectmserfeatures.html) || Yes |

 

**Choose a Descriptor Method**

| **Descriptor** || **Binary** || **Function and Method** || **Invariance** || **Typical Use** |
| --- | --- | --- | --- | --- |
| **Scale** || **Rotation** || **Finding Point Correspondences** || **Classification** |
| HOG || No || [`extractHOGFeatures`](http://es.mathworks.com/help/vision/ref/extracthogfeatures.html)(`I`, ...) || No || No || No || Yes |
| LBP || No || [`extractLBPFeatures`](http://es.mathworks.com/help/vision/ref/extractlbpfeatures.html)(`I`, ...) || No || Yes || No || Yes |
| SURF || No || [`extractFeatures`](http://es.mathworks.com/help/vision/ref/extractfeatures.html)(`I`, '`Method`','`SURF`') || Yes || Yes || Yes || Yes |
| FREAK || Yes || [`extractFeatures`](http://es.mathworks.com/help/vision/ref/extractfeatures.html)(`I`, '`Method`','`FREAK`') || Yes || Yes || Yes || No |
| BRISK || Yes || [`extractFeatures`](http://es.mathworks.com/help/vision/ref/extractfeatures.html)(`I`, '`Method`','`BRISK`') || Yes || Yes || Yes || No |
| BlockSimple pixel neighborhood around a keypoint || No || [`extractFeatures`](http://es.mathworks.com/help/vision/ref/extractfeatures.html)(`I`, '`Method`','`Block`') || No || No || Yes || Yes |

 

## 6.1.6 Use Local Features

Registering two images is a simple way to understand local features. This example finds a geometric transformation between two images. It uses local features to find well-localized anchor points.

**Display two images.**

The first image is the original image.

`original = imread('cameraman.tif');``figure;``imshow(original);` 

![](images/00088.jpeg)

The second image, is the original image rotated and scaled.

`scale = 1.3;``J = imresize(original,scale);``theta = 31;``distorted = imrotate(J,theta);``figure``imshow(distorted)` 

![](images/00089.jpeg)

**Detect matching features between the original and distorted image.**

Detecting the matching SURF features is the first step in determining the transform needed to correct the distorted image.

`ptsOriginal  = detectSURFFeatures(original);``ptsDistorted = detectSURFFeatures(distorted);` 

**Extract features and compare the detected blobs between the two images.**

The detection step found several roughly corresponding blob structures in both images. Compare the detected blob features. This process is facilitated by feature extraction, which determines a local patch descriptor.

`[featuresOriginal,validPtsOriginal] = ...``            extractFeatures(original,ptsOriginal);``[featuresDistorted,validPtsDistorted] = ...``            extractFeatures(distorted,ptsDistorted);` 

It is possible that not all of the original points were used to extract descriptors. Points might have been rejected if they were too close to the image border. Therefore, the valid points are returned in addition to the feature descriptors.

The patch size used to compute the descriptors is determined during the feature extraction step. The patch size corresponds to the scale at which the feature is detected. Regardless of the patch size, the two feature vectors, `featuresOriginal` and `featuresDistorted`, are computed in such a way that they are of equal length. The descriptors enable you to compare detected features, regardless of their size and rotation.

**Find candidate matches.**

Obtain candidate matches between the features by inputting the descriptors to the `matchFeatures` function. Candidate matches imply that the results can contain some invalid matches. Two patches that match can indicate like features but might not be a correct match. A table corner can look like a chair corner, but the two features are obviously not a match.

`indexPairs = matchFeatures(featuresOriginal,featuresDistorted);` 

**Find point locations from both images.**

Each row of the returned `indexPairs` contains two indices of candidate feature matches between the images. Use the indices to collect the actual point locations from both images.

`matchedOriginal  = validPtsOriginal(indexPairs(:,1));``matchedDistorted = validPtsDistorted(indexPairs(:,2));` 

**Display the candidate matches.**

`figure``showMatchedFeatures(original,distorted,matchedOriginal,matchedDistorted)``title('Candidate matched points (including outliers)')`` ` 

![](images/00090.jpeg)

**Analyze the feature locations.**

If there are a sufficient number of valid matches, remove the false matches. An effective technique for this scenario is the RANSAC algorithm. The `estimateGeometricTransform` function implements M-estimator sample consensus (MSAC), which is a variant of the RANSAC algorithm. MSAC finds a geometric transform and separates the inliers (correct matches) from the outliers (spurious matches).

`[tform, inlierDistorted,inlierOriginal] = ...``            estimateGeometricTransform(matchedDistorted,...``                matchedOriginal,'similarity');`` ` 

**Display the matching points.**

`figure``showMatchedFeatures(original,distorted,inlierOriginal,inlierDistorted)``title('Matching points (inliers only)')``legend('ptsOriginal','ptsDistorted')` 

![](images/00091.jpeg)

**Verify the computed geometric transform.**

Apply the computed geometric transform to the distorted image.

`outputView = imref2d(size(original));``recovered  = imwarp(distorted,tform,'OutputView',outputView);` 

Display the recovered image and the original image.

`figure``imshowpair(original,recovered,'montage')` 

![](images/00092.jpeg)

## 6.1.7 Image Registration Using Multiple Features

This example builds on the results of the "Use Local Features" example. Using more than one detector and descriptor pair enables you to combine and reinforce your results. Multiple pairs are also useful for when you cannot obtain enough good matches (inliers) using a single feature detector.

Load the original image.

`original = imread('cameraman.tif');``figure;``imshow(original);``text(size(original,2),size(original,1)+15, ...``    'Image courtesy of Massachusetts Institute of Technology', ...``    'FontSize',7,'HorizontalAlignment','right');` 

![](images/00093.jpeg)

Scale and rotate the original image to create the distorted image.

`scale = 1.3;``J = imresize(original, scale);`` ``theta = 31;``distorted = imrotate(J,theta);``figure``imshow(distorted)` 

![](images/00094.jpeg)

Detect the features in both images. Use the BRISK detectors first, followed by the SURF detectors.

`ptsOriginalBRISK  = detectBRISKFeatures(original,'MinContrast',0.01);``ptsDistortedBRISK = detectBRISKFeatures(distorted,'MinContrast',0.01);`` ``ptsOriginalSURF  = detectSURFFeatures(original);``ptsDistortedSURF = detectSURFFeatures(distorted);` 

Extract descriptors from the original and distorted images. The BRISK features use the FREAK descriptor by default.

`[featuresOriginalFREAK,validPtsOriginalBRISK]  = ...``        extractFeatures(original,ptsOriginalBRISK);``[featuresDistortedFREAK,validPtsDistortedBRISK] = ...``        extractFeatures(distorted,ptsDistortedBRISK);`` ``[featuresOriginalSURF,validPtsOriginalSURF]  = ...``        extractFeatures(original,ptsOriginalSURF);``[featuresDistortedSURF,validPtsDistortedSURF] = ...``        extractFeatures(distorted,ptsDistortedSURF);` 

Determine candidate matches by matching FREAK descriptors first, and then SURF descriptors. To obtain as many feature matches as possible, start with detector and matching thresholds that are lower than the default values. Once you get a working solution, you can gradually increase the thresholds to reduce the computational load required to extract and match features.

`indexPairsBRISK = matchFeatures(featuresOriginalFREAK,...``            featuresDistortedFREAK,'MatchThreshold',40,'MaxRatio',0.8);`` ``indexPairsSURF = matchFeatures(featuresOriginalSURF,featuresDistortedSURF);` 

Obtain candidate matched points for BRISK and SURF.

`matchedOriginalBRISK  = validPtsOriginalBRISK(indexPairsBRISK(:,1));``matchedDistortedBRISK = validPtsDistortedBRISK(indexPairsBRISK(:,2));`` ``matchedOriginalSURF  = validPtsOriginalSURF(indexPairsSURF(:,1));``matchedDistortedSURF = validPtsDistortedSURF(indexPairsSURF(:,2));` 

Visualize the BRISK putative matches.

`figure``showMatchedFeatures(original,distorted,matchedOriginalBRISK,...``            matchedDistortedBRISK)``title('Putative matches using BRISK & FREAK')``legend('ptsOriginalBRISK','ptsDistortedBRISK')`` ` 

![](images/00095.jpeg)

Combine the candidate matched BRISK and SURF local features. Use the `Location` property to combine the point locations from BRISK and SURF features.

`matchedOriginalXY  = ...``    [matchedOriginalSURF.Location; matchedOriginalBRISK.Location];``matchedDistortedXY = ...``    [matchedDistortedSURF.Location; matchedDistortedBRISK.Location];` 

Determine the inlier points and the geometric transform of the BRISK and SURF features.

`[tformTotal,inlierDistortedXY,inlierOriginalXY] = ...``    estimateGeometricTransform(matchedDistortedXY,...``        matchedOriginalXY,'similarity');`` ` 

Display the results. The result provides several more matches than the example that used a single feature detector.

`figure``showMatchedFeatures(original,distorted,inlierOriginalXY,inlierDistortedXY)``title('Matching points using SURF and BRISK (inliers only)')``legend('ptsOriginal','ptsDistorted')`` ` 

![](images/00096.jpeg)

Compare the original and recovered image.

`outputView = imref2d(size(original));``recovered  = imwarp(distorted,tformTotal,'OutputView',outputView);`` ``figure;``imshowpair(original,recovered,'montage')` 

![](images/00097.jpeg)

# 6.2 Pattern Matching

 

This example shows how to use the 2-D normalized cross-correlation for pattern matching and target tracking. The example uses predefined or user specified target and number of similar targets to be tracked. The normalized cross correlation plot shows that when the value exceeds the set threshold, the target is identified.

## 6.2.1 Introduction

In this example you use normalized cross correlation to track a target pattern in a video. The pattern matching algorithm involves the following steps:

*   The input video frame and the template are reduced in size to minimize the amount of computation required by the matching algorithm.
*   Normalized cross correlation, in the frequency domain, is used to find a template in the video frame.
*   The location of the pattern is determined by finding the maximum cross correlation value.

## 6.2.2 Initialization

Initialize required variables such as the threshold value for the cross correlation and the decomposition level for Gaussian Pyramid decomposition.

`threshold = single(0.99);``level = 2;``Create System object™ to read a video file.``hVideoSrc = vision.VideoFileReader('vipboard.mp4', ...``                                'VideoOutputDataType', 'single',...``                                'ImageColorSpace', 'Intensity');`` ` 

Create three gaussian pyramid System objects for decomposing the target template and decomposing the Image under Test(IUT). The decomposition is done so that the cross correlation can be computed over a small region instead of the entire original size of the image.

`hGaussPymd1 = vision.Pyramid('PyramidLevel',level);``hGaussPymd2 = vision.Pyramid('PyramidLevel',level);``hGaussPymd3 = vision.Pyramid('PyramidLevel',level);`` ` 

Create two 2-D FFT System objects one for the image under test and the other for the target.

`hFFT2D1 = vision.FFT;``hFFT2D2 = vision.FFT;`` ` 

Create a System object to perform 2-D inverse FFT after performing correlation (equivalent to multiplication) in the frequency domain.

`hIFFFT2D = vision.IFFT;`` ` 

Create 2-D convolution System object to average the image energy in tiles of the same dimension of the target.

`hConv2D = vision.Convolver('OutputSize','Valid');`` ` 

Here you implement the following sequence of operations.

`% Specify the target image and number of similar targets to be tracked. By``% default, the example uses a predefined target and finds up to 2 similar``% patterns. Set the variable useDefaultTarget to false to specify a new``% target and the number of similar targets to match.``useDefaultTarget = true;``[Img, numberOfTargets, target_image] = ...``  videopattern_gettemplate(useDefaultTarget);`` ``% Downsample the target image by a predefined factor using the``% gaussian pyramid System object. You do this to reduce the amount of``% computation for cross correlation.``target_image = single(target_image);``target_dim_nopyramid = size(target_image);``target_image_gp = step(hGaussPymd1, target_image);``target_energy = sqrt(sum(target_image_gp(:).^2));`` ``% Rotate the target image by 180 degrees, and perform zero padding so that``% the dimensions of both the target and the input image are the same.``target_image_rot = imrotate(target_image_gp, 180);``[rt, ct] = size(target_image_rot);``Img = single(Img);``Img = step(hGaussPymd2, Img);``[ri, ci]= size(Img);``r_mod = 2^nextpow2(rt + ri);``c_mod = 2^nextpow2(ct + ci);``target_image_p = [target_image_rot zeros(rt, c_mod-ct)];``target_image_p = [target_image_p; zeros(r_mod-rt, c_mod)];``% Compute the 2-D FFT of the target image``target_fft = step(hFFT2D1, target_image_p);``% Initialize constant variables used in the processing loop.``target_size = repmat(target_dim_nopyramid, [numberOfTargets, 1]);``gain = 2^(level);``Im_p = zeros(r_mod, c_mod, 'single'); % Used for zero padding``C_ones = ones(rt, ct, 'single');      % Used to calculate mean using conv` 

Create a System object to calculate the local maximum value for the normalized cross correlation.

`hFindMax = vision.LocalMaximaFinder( ...``            'Threshold', single(-1), ...``            'MaximumNumLocalMaxima', numberOfTargets, ...``            'NeighborhoodSize', floor(size(target_image_gp)/2)*2 - 1);` 

Create a System object to display the tracking of the pattern.

`sz = get(0,'ScreenSize');``pos = [20 sz(4)-400 400 300];``hROIPattern = vision.VideoPlayer('Name', 'Overlay the ROI on the target', ...``    'Position', pos);`` ` 

Initialize figure window for plotting the normalized cross correlation value

`hPlot = videopatternplots('setup',numberOfTargets, threshold);`` ` 

## 6.2.3 Video Processing Loop

Create a processing loop to perform pattern matching on the input video. This loop uses the System objects you instantiated above. The loop is stopped when you reach the end of the input file, which is detected by the VideoFileReader System object.

`while ~isDone(hVideoSrc)``    Im = step(hVideoSrc);``    Im_gp = step(hGaussPymd3, Im);`` ``    % Frequency domain convolution.``    Im_p(1:ri, 1:ci) = Im_gp;    % Zero-pad``    img_fft = step(hFFT2D2, Im_p);``    corr_freq = img_fft .* target_fft;``    corrOutput_f = step(hIFFFT2D, corr_freq);``    corrOutput_f = corrOutput_f(rt:ri, ct:ci);`` ``    % Calculate image energies and block run tiles that are size of``    % target template.``    IUT_energy = (Im_gp).^2;``    IUT = step(hConv2D, IUT_energy, C_ones);``    IUT = sqrt(IUT);`` ``    % Calculate normalized cross correlation.``    norm_Corr_f = (corrOutput_f) ./ (IUT * target_energy);``    xyLocation = step(hFindMax, norm_Corr_f);`` ``    % Calculate linear indices.``    linear_index = sub2ind([ri-rt, ci-ct]+1, xyLocation(:,2),...``        xyLocation(:,1));`` ``    norm_Corr_f_linear = norm_Corr_f(:);``    norm_Corr_value = norm_Corr_f_linear(linear_index);``    detect = (norm_Corr_value > threshold);``    target_roi = zeros(length(detect), 4);``    ul_corner = (gain.*(xyLocation(detect, :)-1))+1;``    target_roi(detect, :) = [ul_corner, fliplr(target_size(detect, :))];`` ``    % Draw bounding box.``    Imf = insertShape(Im, 'Rectangle', target_roi, 'Color', 'green');``    % Plot normalized cross correlation.``    videopatternplots('update',hPlot,norm_Corr_value);``    step(hROIPattern, Imf);``end``release(hVideoSrc);`` ` 

![](images/00098.jpeg)

![](images/00099.jpeg)

## 6.2.4 Summary

This example shows use of Computer Vision System Toolbox™ to find a user defined pattern in a video and track it. The algorithm is based on normalized frequency domain cross correlation between the target and the image under test. The video player window displays the input video with the identified target locations. Also a figure displays the normalized correlation between the target and the image which is used as a metric to match the target. As can be seen whenever the correlation value exceeds the threshold (indicated by the blue line), the target is identified in the input video and the location is marked by the green bounding box.

# 6.3 Optical Character Recognition (OCR)

 

OCR Recognize text using optical character recognition

Recognizing text in images is a common task performed in computer vision applications. For example, you can capture video from a moving vehicle to alert a driver about a road sign. Segmenting out the text from a cluttered scene helps with related tasks such as optical character recognition (OCR).

## 6.3.1 Train Optical Character Recognition for Custom Fonts

The optical character recognition (OCR) app trains the [ocr](http://es.mathworks.com/help/vision/ref/ocr.html) function to recognize a custom language or font. You can use this app to label character data interactively for OCR training and to generate an OCR language data file for use with the ocr function.

![Descripción: http://es.mathworks.com/help/vision/ug/ocr\_app\_flow.png](images/00100.gif)

## 6.3.2 Open the OCR Trainer App

 

·        MATLAB^® Toolstrip: On the **Apps** tab, under **Image Processing and Computer Vision**, click ![Descripción: http://es.mathworks.com/help/vision/ug/ocr\_app\_icon.png](images/00101.gif), the OCR app icon.

·        MATLAB command prompt: Enter ocrTrainer.

 

## 6.3.3 Train OCR

 

1.      In the OCR Trainer, click **New Session** to open the OCR Training Session Settings dialog box.

2.      Under **Output Settings**, enter a name for the OCR language data file and choose the output folder location for the file. The location you specify must be writable.

3.      Under **Labeling Method**, either label the data manually or pre-label it using optical character recognition. If you use OCR, you can select either the pre-installed English or Japanese language, or you can download additional language support files.

4.      To limit the OCR to a specific character set, select the **Character set** check box and add the characters.

5.      Add images at any time during the training session. The trainer automatically segments the images for OCR training. Inspect the results to verify expected text segmentation. To improve the segmentation, pre-process your images using the [Image Segmenter](http://es.mathworks.com/help/images/ref/imagesegmenter-app.html) app. Once the images are added, you can inspect segmentation results from the training image view.

 

![Descripción: http://es.mathworks.com/help/vision/ug/ocr\_app\_segmented.png](images/00102.gif)

 

6.      Remove any noisy images. To improve segmentation results, you can draw a region of interest to select a portion of an image. The display shows the original image on the left and the edited one on the right. When you are done, click **Accept All**.

7.      Modify the extracted samples from the character view window.

*   To correct samples, select a group of samples from the **Data Browser** pane and change the labels using the **Character Label** field.
*   To exclude a sample from training, right-click the sample and select the option to move that sample to the **Unknown** category. Unknown samples are listed at the top of the **Data Browser** pane and are not used for training.
*   If the bounding box clipped a character, double-click the character and modify it in the image it was extracted from.

 

![Descripción: http://es.mathworks.com/help/vision/ug/ocr\_app\_interface.png](images/00103.gif)

 

8.      After correcting the samples, click **Train**. When the trainer completes training, the app creates an OCR language data file and saves it to the folder you specified.

 

## 6.3.4 App Controls

**Sessions**

Starts a new session, opens a saved session, or adds a session to the current one. You can also save and name the session. The sessions are saved as MAT files.

**Add Images**

Adds images. You can add images when you start a new session or after you accept the current collection of images.

**Settings**

Set or change the font display.

**Edit Box**

Selects the image that contains the selected character, along with the bounding boxes. You can create additional regions, merge, modify, or delete existing images. To delete an ROI, use the **delete** key.

**Train**

Creates an OCR data file from the session. To use the .traineddata file with the [ocr](http://es.mathworks.com/help/vision/ref/ocr.html) function, set the 'Language'property for the ocr function, and follow the directions for a custom language.

**Generate Function**

Creates an autogenerated evaluation function for verification of training results.

## 6.3.5 Install OCR Language Data Files

OCR Language Data files contain pretrained language data from the OCR Engine, [tesseract-ocr](https://github.com/tesseract-ocr/tessdata), to use with the [ocr](http://es.mathworks.com/help/vision/ref/ocr.html)function.

**Installation**

After you install third-party support files, you can use the data with the Computer Vision System Toolbox™ product. Use one of two ways to install the Add-on support files.

·        Select **Get Add-ons** from the **Add-ons** drop-down menu from the MATLAB^® desktop. The Add-on files are in the "MathWorks Features" section.

·        Type visionSupportPackages in a MATLAB Command Window and follow the prompts.

When a new version of MATLAB software is released, repeat this process to check for updates. You can also check for updates between releases.

**Pretrained Language Data and the ocr function**

After you install the pretrained language data files, you can specify one or more additional languages using the Languageproperty of the [ocr](http://es.mathworks.com/help/vision/ref/ocr.html) function. Use the appropriate language character vector with the property.

txt = ocr(img,'Language','Finnish');

 

# 6.4 Automatically Detect and Recognize Text in Natural Images

 

This example shows how to detect regions in an image that contain text. This is a common task performed on unstructured scenes. Unstructured scenes are images that contain undetermined or random scenarios. For example, you can detect and recognize text automatically from captured video to alert a driver about a road sign. This is different than structured scenes, which contain known scenarios where the position of text is known beforehand.

Segmenting text from an unstructured scene greatly helps with additional tasks such as optical character recognition (OCR). The automated text detection algorithm in this example detects a large number of text region candidates and progressively removes those less likely to contain text.

## 6.4.1 Step 1: Detect Candidate Text Regions Using MSER

The MSER feature detector works well for finding text regions \[1\]. It works well for text because the consistent color and high contrast of text leads to stable intensity profiles.

Use the detectMSERFeatures function to find all the regions within the image and plot these results. Notice that there are many non-text regions detected alongside the text.

colorImage = imread('handicapSign.jpg');

I = rgb2gray(colorImage);

 

% Detect MSER regions.

\[mserRegions, mserConnComp\] = detectMSERFeatures(I, ...

    'RegionAreaRange',\[200 8000\],'ThresholdDelta',4);

 

figure

imshow(I)

hold on

plot(mserRegions, 'showPixelList', true,'showEllipses',false)

title('MSER regions')

hold off

![Descripción: http://es.mathworks.com/help/examples/vision\_product/win64/TextDetectionExample\_01.png](images/00104.jpeg)

## 6.4.2 Step 2: Remove Non-Text Regions Based On Basic Geometric Properties

Although the MSER algorithm picks out most of the text, it also detects many other stable regions in the image that are not text. You can use a rule-based approach to remove non-text regions. For example, geometric properties of text can be used to filter out non-text regions using simple thresholds. Alternatively, you can use a machine learning approach to train a text vs. non-text classifier. Typically, a combination of the two approaches produces better results \[4\]. This example uses a simple rule-based approach to filter non-text regions based on geometric properties.

There are several geometric properties that are good for discriminating between text and non-text regions \[2,3\], including:

·        Aspect ratio

·        Eccentricity

·        Euler number

·        Extent

·        Solidity

Use regionprops to measure a few of these properties and then remove regions based on their property values.

% Use regionprops to measure MSER properties

mserStats = regionprops(mserConnComp, 'BoundingBox', 'Eccentricity', ...

    'Solidity', 'Extent', 'Euler', 'Image');

 

% Compute the aspect ratio using bounding box data.

bbox = vertcat(mserStats.BoundingBox);

w = bbox(:,3);

h = bbox(:,4);

aspectRatio = w./h;

 

% Threshold the data to determine which regions to remove. These thresholds

% may need to be tuned for other images.

filterIdx = aspectRatio' > 3;

filterIdx = filterIdx | \[mserStats.Eccentricity\] > .995 ;

filterIdx = filterIdx | \[mserStats.Solidity\] < .3;

filterIdx = filterIdx | \[mserStats.Extent\] < 0.2 | \[mserStats.Extent\] > 0.9;

filterIdx = filterIdx | \[mserStats.EulerNumber\] < -4;

 

% Remove regions

mserStats(filterIdx) = \[\];

mserRegions(filterIdx) = \[\];

 

% Show remaining regions

figure

imshow(I)

hold on

plot(mserRegions, 'showPixelList', true,'showEllipses',false)

title('After Removing Non-Text Regions Based On Geometric Properties')

hold off

![Descripción: http://es.mathworks.com/help/examples/vision\_product/win64/TextDetectionExample\_02.png](images/00105.jpeg)

## 6.4.3 Step 3: Remove Non-Text Regions Based On Stroke Width Variation

Another common metric used to discriminate between text and non-text is stroke width. *Stroke width* is a measure of the width of the curves and lines that make up a character. Text regions tend to have little stroke width variation, whereas non-text regions tend to have larger variations.

To help understand how the stroke width can be used to remove non-text regions, estimate the stroke width of one of the detected MSER regions. You can do this by using a distance transform and binary thinning operation \[3\].

% Get a binary image of the a region, and pad it to avoid boundary effects

% during the stroke width computation.

regionImage = mserStats(6).Image;

regionImage = padarray(regionImage, \[1 1\]);

 

% Compute the stroke width image.

distanceImage = bwdist(~regionImage);

skeletonImage = bwmorph(regionImage, 'thin', inf);

 

strokeWidthImage = distanceImage;

strokeWidthImage(~skeletonImage) = 0;

 

% Show the region image alongside the stroke width image.

figure

subplot(1,2,1)

imagesc(regionImage)

title('Region Image')

 

subplot(1,2,2)

imagesc(strokeWidthImage)

title('Stroke Width Image')

![Descripción: http://es.mathworks.com/help/examples/vision\_product/win64/TextDetectionExample\_03.png](images/00106.jpeg)

In the images shown above, notice how the stroke width image has very little variation over most of the region. This indicates that the region is more likely to be a text region because the lines and curves that make up the region all have similar widths, which is a common characteristic of human readable text.

In order to use stroke width variation to remove non-text regions using a threshold value, the variation over the entire region must be quantified into a single metric as follows:

% Compute the stroke width variation metric

strokeWidthValues = distanceImage(skeletonImage);

strokeWidthMetric = std(strokeWidthValues)/mean(strokeWidthValues);

Then, a threshold can be applied to remove the non-text regions. Note that this threshold value may require tuning for images with different font styles.

% Threshold the stroke width variation metric

strokeWidthThreshold = 0.4;

strokeWidthFilterIdx = strokeWidthMetric > strokeWidthThreshold;

The procedure shown above must be applied separately to each detected MSER region. The following for-loop processes all the regions, and then shows the results of removing the non-text regions using stroke width variation.

% Process the remaining regions

for j = 1:numel(mserStats)

 

    regionImage = mserStats(j).Image;

    regionImage = padarray(regionImage, \[1 1\], 0);

 

    distanceImage = bwdist(~regionImage);

    skeletonImage = bwmorph(regionImage, 'thin', inf);

 

    strokeWidthValues = distanceImage(skeletonImage);

 

    strokeWidthMetric = std(strokeWidthValues)/mean(strokeWidthValues);

 

    strokeWidthFilterIdx(j) = strokeWidthMetric > strokeWidthThreshold;

 

end

 

% Remove regions based on the stroke width variation

mserRegions(strokeWidthFilterIdx) = \[\];

mserStats(strokeWidthFilterIdx) = \[\];

 

% Show remaining regions

figure

imshow(I)

hold on

plot(mserRegions, 'showPixelList', true,'showEllipses',false)

title('After Removing Non-Text Regions Based On Stroke Width Variation')

hold off

![Descripción: http://es.mathworks.com/help/examples/vision\_product/win64/TextDetectionExample\_04.png](images/00107.jpeg)

## 6.4.4 Step 4: Merge Text Regions For Final Detection Result

At this point, all the detection results are composed of individual text characters. To use these results for recognition tasks, such as OCR, the individual text characters must be merged into words or text lines. This enables recognition of the actual words in an image, which carry more meaningful information than just the individual characters. For example, recognizing the string 'EXIT' vs. the set of individual characters {'X','E','T','I'}, where the meaning of the word is lost without the correct ordering.

One approach for merging individual text regions into words or text lines is to first find neighboring text regions and then form a bounding box around these regions. To find neighboring regions, expand the bounding boxes computed earlier with regionprops. This makes the bounding boxes of neighboring text regions overlap such that text regions that are part of the same word or text line form a chain of overlapping bounding boxes.

% Get bounding boxes for all the regions

bboxes = vertcat(mserStats.BoundingBox);

 

% Convert from the \[x y width height\] bounding box format to the \[xmin ymin

% xmax ymax\] format for convenience.

xmin = bboxes(:,1);

ymin = bboxes(:,2);

xmax = xmin + bboxes(:,3) - 1;

ymax = ymin + bboxes(:,4) - 1;

 

% Expand the bounding boxes by a small amount.

expansionAmount = 0.02;

xmin = (1-expansionAmount) \* xmin;

ymin = (1-expansionAmount) \* ymin;

xmax = (1+expansionAmount) \* xmax;

ymax = (1+expansionAmount) \* ymax;

 

% Clip the bounding boxes to be within the image bounds

xmin = max(xmin, 1);

ymin = max(ymin, 1);

xmax = min(xmax, size(I,2));

ymax = min(ymax, size(I,1));

 

% Show the expanded bounding boxes

expandedBBoxes = \[xmin ymin xmax-xmin+1 ymax-ymin+1\];

IExpandedBBoxes = insertShape(colorImage,'Rectangle',expandedBBoxes,'LineWidth',3);

 

figure

imshow(IExpandedBBoxes)

title('Expanded Bounding Boxes Text')

![Descripción: http://es.mathworks.com/help/examples/vision\_product/win64/TextDetectionExample\_05.png](images/00108.jpeg)

Now, the overlapping bounding boxes can be merged together to form a single bounding box around individual words or text lines. To do this, compute the overlap ratio between all bounding box pairs. This quantifies the distance between all pairs of text regions so that it is possible to find groups of neighboring text regions by looking for non-zero overlap ratios. Once the pair-wise overlap ratios are computed, use a graph to find all the text regions "connected" by a non-zero overlap ratio.

Use the bboxOverlapRatio function to compute the pair-wise overlap ratios for all the expanded bounding boxes, then use graph to find all the connected regions.

% Compute the overlap ratio

overlapRatio = bboxOverlapRatio(expandedBBoxes, expandedBBoxes);

 

% Set the overlap ratio between a bounding box and itself to zero to

% simplify the graph representation.

n = size(overlapRatio,1);

overlapRatio(1:n+1:n^2) = 0;

 

% Create the graph

g = graph(overlapRatio);

 

% Find the connected text regions within the graph

componentIndices = conncomp(g);

The output of conncomp are indices to the connected text regions to which each bounding box belongs. Use these indices to merge multiple neighboring bounding boxes into a single bounding box by computing the minimum and maximum of the individual bounding boxes that make up each connected component.

% Merge the boxes based on the minimum and maximum dimensions.

xmin = accumarray(componentIndices', xmin, \[\], @min);

ymin = accumarray(componentIndices', ymin, \[\], @min);

xmax = accumarray(componentIndices', xmax, \[\], @max);

ymax = accumarray(componentIndices', ymax, \[\], @max);

 

% Compose the merged bounding boxes using the \[x y width height\] format.

textBBoxes = \[xmin ymin xmax-xmin+1 ymax-ymin+1\];

Finally, before showing the final detection results, suppress false text detections by removing bounding boxes made up of just one text region. This removes isolated regions that are unlikely to be actual text given that text is usually found in groups (words and sentences).

% Remove bounding boxes that only contain one text region

numRegionsInGroup = histcounts(componentIndices);

textBBoxes(numRegionsInGroup == 1, :) = \[\];

 

% Show the final text detection result.

ITextRegion = insertShape(colorImage, 'Rectangle', textBBoxes,'LineWidth',3);

 

figure

imshow(ITextRegion)

title('Detected Text')

![Descripción: http://es.mathworks.com/help/examples/vision\_product/win64/TextDetectionExample\_06.png](images/00109.jpeg)

## 6.4.5 Step 5: Recognize Detected Text Using OCR

After detecting the text regions, use the ocr function to recognize the text within each bounding box. Note that without first finding the text regions, the output of the ocr function would be considerably more noisy.

ocrtxt = ocr(I, textBBoxes);

\[ocrtxt.Text\]

ans =

 

    'HANDICIXPPED

     PARKING

     SPECIAL PLATE

     REQUIRED

     UNAUTHORIZED

     VEHICLES

     MAY BE TOWED

     AT OWNERS

     EXPENSE

     

     '

 

This example showed you how to detect text in an image using the MSER feature detector to first find candidate text regions, and then it described how to use geometric measurements to remove all the non-text regions. This example code is a good starting point for developing more robust text detection algorithms. Note that without further enhancements this example can produce reasonable results for a variety of other images, for example, posters.jpg or licensePlates.jp

# 6.5 Recognize Text Using Optical Character Recognition (OCR)

 

This example shows how to use the ocr function from the Computer Vision System Toolbox™ to perform Optical Character Recognition.

## 6.5.1 Text Recognition Using the ocr Function

Recognizing text in images is useful in many computer vision applications such as image search, document analysis, and robot navigation. The ocr function provides an easy way to add text recognition functionality to a wide range of applications.

% Load an image

I = imread('businessCard.png');

 

% Perform OCR

results = ocr(I);

 

% Display one of the recognized words

word = results.Words{2}

 

% Location of the word in I

wordBBox = results.WordBoundingBoxes(2,:)

word =

 

    'MathWorks®'

 

 

wordBBox =

 

   173    75   376    61

 

% Show the location of the word in the original image

figure;

Iname = insertObjectAnnotation(I, 'rectangle', wordBBox, word);

imshow(Iname);

![Descripción: http://es.mathworks.com/help/examples/vision\_product/win64/OCRExample\_01.png](images/00110.jpeg)

## 6.5.2 Information Returned By the ocr Function

The ocr functions returns the recognized text, the recognition confidence, and the location of the text in the original image. You can use this information to identify the location of misclassified text within the image.

% Find characters with low confidence

lowConfidenceIdx = results.CharacterConfidences < 0.5;

 

% Get the bounding box locations of the low confidence characters

lowConfBBoxes = results.CharacterBoundingBoxes(lowConfidenceIdx, :);

 

% Get confidence values

lowConfVal = results.CharacterConfidences(lowConfidenceIdx);

 

% Annotate image with character confidences

str      = sprintf('confidence = %f', lowConfVal);

Ilowconf = insertObjectAnnotation(I, 'rectangle', lowConfBBoxes, str);

 

figure;

imshow(Ilowconf);

![Descripción: http://es.mathworks.com/help/examples/vision\_product/win64/OCRExample\_02.png](images/00111.jpeg)

Here, the logo in the business card is incorrectly classified as a text character. These kind of OCR errors can be identified using the confidence values before any further processing takes place.

## 6.5.3 Challenges Obtaining Accurate Results

ocr performs best when the text is located on a uniform background and is formatted like a document. When the text appears on a non-uniform background, additional pre-processing steps are required to get the best OCR results. In this part of the example, you will try to locate the digits on a keypad. Although, the keypad image may appear to be easy for OCR, it is actually quite challenging because the text is on a non-uniform background.

I = imread('keypad.jpg');

I = rgb2gray(I);

 

figure;

imshow(I)

![Descripción: http://es.mathworks.com/help/examples/vision\_product/win64/OCRExample\_03.png](images/00112.jpeg)

% Run OCR on the image

results = ocr(I);

 

results.Text

ans =

 

    ' 

     

     '

 

The empty results.Text indicates that no text is recognized. In the keypad image, the text is sparse and located on an irregular background. In this case, the heuristics used for document layout analysis within ocr might be failing to find blocks of text within the image, and, as a result, text recognition fails. In this situation, disabling the automatic layout analysis, using the 'TextLayout' parameter, may help improve the results.

% Set 'TextLayout' to 'Block' to instruct ocr to assume the image

% contains just one block of text.

results = ocr(I, 'TextLayout', 'Block');

 

results.Text

ans =

 

  0×0 empty char array

 

**What Went Wrong?**

Adjusting the 'TextLayout' parameter did not help. To understand why OCR continues to fail, you have to investigate the initial binarization step performed within ocr. You can use imbinarize to check this initial binarization step because both ocr and the default 'global' method in imbinarize use Otsu's method for image binarization.

BW = imbinarize(I);

 

figure;

imshowpair(I, BW, 'montage');

![Descripción: http://es.mathworks.com/help/examples/vision\_product/win64/OCRExample\_04.png](images/00113.jpeg)

After thresholding, the binary image contains no text. This is why ocr failed to recognize any text in the original image. You can help improve the results by pre-processing the image to improve text segmentation. The next part of the example explores two useful pre-processing techniques.

## 6.5.4 Image Pre-processing Techniques To Improve Results

The poor text segmentation seen above is caused by the non-uniform background in the image, i.e. the light-gray keys surrounded by dark gray. You can use the following pre-processing technique to remove the background variations and improve the text segmentation. Additional details about this technique are given in the example entitled [Correcting Nonuniform Illumination](XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX).

% Remove keypad background

Icorrected = imtophat(I, strel('disk', 15));

 

BW1 = imbinarize(Icorrected);

 

figure;

imshowpair(Icorrected, BW1, 'montage');

![Descripción: http://es.mathworks.com/help/examples/vision\_product/win64/OCRExample\_05.png](images/00114.jpeg)

After removing the background variation, the digits are now visible in the binary image. However, there are a few artifacts at the edge of the keys and the small text next to the digits that may continue to hinder accurate OCR of the whole image. Additional pre-processing using [morphological reconstruction](http://blogs.mathworks.com/steve/2008/07/14/opening-by-reconstruction/) helps to remove these artifacts and produce a cleaner image for OCR.

% Perform morphological reconstruction and show binarized image.

marker = imerode(Icorrected, strel('line',10,0));

Iclean = imreconstruct(marker, Icorrected);

 

BW2 = imbinarize(Iclean);

 

figure;

imshowpair(Iclean, BW2, 'montage');

![Descripción: http://es.mathworks.com/help/examples/vision\_product/win64/OCRExample\_06.png](images/00115.jpeg)

After these pre-processing steps, the digits are now well segmented from the background and ocr produces better results.

results = ocr(BW2, 'TextLayout', 'Block');

 

results.Text

ans =

 

    '«-1 ..c2 .3

     ....4 .5 .....6

     W7 M8 M9

     -\*1..o fl

     

     '

 

There is some "noise" in the results due to the smaller text next to the digits. Also, the digit 0, is falsely recognized as the letter 'o'. This type of error may happen when two characters have similar shapes and there is not enough surrounding text for the ocr function to determine the best classification for a specific character. Despite the "noisy" results, you can still find the digit locations in the original image using the locateText method with the OCR results.

The locateText method supports regular expressions so you can ignore irrelevant text.

% The regular expression, '\\d', matches the location of any digit in the

% recognized text and ignores all non-digit characters.

regularExpr = '\\d';

 

% Get bounding boxes around text that matches the regular expression

bboxes = locateText(results, regularExpr, 'UseRegexp', true);

 

digits = regexp(results.Text, regularExpr, 'match');

 

% draw boxes around the digits

Idigits = insertObjectAnnotation(I, 'rectangle', bboxes, digits);

 

figure;

imshow(Idigits);

![Descripción: http://es.mathworks.com/help/examples/vision\_product/win64/OCRExample\_07.png](images/00116.jpeg)

Another approach to improve the results is to leverage a priori knowledge about the text within the image. In this example, the text you are interested in contains only numeric digits. You can improve the results by constraining ocr to only select the best matches from the set '0123456789'.

% Use the 'CharacterSet' parameter to constrain OCR

results = ocr(BW2, 'CharacterSet', '0123456789', 'TextLayout','Block');

 

results.Text

ans =

 

    ' 1 1   2   3

     5 4  5   06

      7  3  9

      4 1 0  51

     

     '

 

The results now only have characters from the digit character set. However, you can see that several non-digit characters in the image are falsely recognized as digits. This can happen when a non-digit character closely resembles one of the digits.

You can use the fact that there are only 10 digits on the keypad along with the character confidences to find the 10 best digits.

% Sort the character confidences

\[sortedConf, sortedIndex\] = sort(results.CharacterConfidences, 'descend');

 

% Keep indices associated with non-NaN confidences values

indexesNaNsRemoved = sortedIndex( ~isnan(sortedConf) );

 

% Get the top ten indexes

topTenIndexes = indexesNaNsRemoved(1:10);

 

% Select the top ten results

digits = num2cell(results.Text(topTenIndexes));

bboxes = results.CharacterBoundingBoxes(topTenIndexes, :);

 

Idigits = insertObjectAnnotation(I, 'rectangle', bboxes, digits);

 

figure;

imshow(Idigits);

![Descripción: http://es.mathworks.com/help/examples/vision\_product/win64/OCRExample\_08.png](images/00117.jpeg)

## 6.5.5 ROI-based Processing To Improve Results

In some situations, just pre-processing the image may not be sufficient to achieve good OCR results. One approach to use in this situation, is to identify specific regions in the image that ocr should process. In the keypad example image, these regions would be those that just contain the digits. You may select the regions manually using imrect, or you can automate the process. In this example, you will use vision.BlobAnalysis to find the digits on the keypad.

% Initialize the blob analysis System object(TM)

blobAnalyzer = vision.BlobAnalysis('MaximumCount', 500);

 

% Run the blob analyzer to find connected components and their statistics.

\[area, centroids, roi\] = step(blobAnalyzer, BW1);

 

% Show all the connected regions

img = insertShape(I, 'rectangle', roi);

figure;

imshow(img);

![Descripción: http://es.mathworks.com/help/examples/vision\_product/win64/OCRExample\_09.png](images/00118.jpeg)

There are many connected regions within the keypad image. Small regions are not likely to contain any text and can be removed using the area statistic returned by vision.BlobAnalysis. Here, regions having an area smaller than 300 are removed.

areaConstraint = area > 300;

 

% Keep regions that meet the area constraint

roi = double(roi(areaConstraint, :));

 

% Show remaining blobs after applying the area constraint.

img = insertShape(I, 'rectangle', roi);

figure;

imshow(img);

![Descripción: http://es.mathworks.com/help/examples/vision\_product/win64/OCRExample\_10.png](images/00119.jpeg)

Further processing based on a region's aspect ratio is applied to identify regions that are likely to contain a single character. This helps to remove the smaller text characters that are jumbled together next to the digits. In general, the larger the text the easier it is for ocr to recognize.

% Compute the aspect ratio.

width  = roi(:,3);

height = roi(:,4);

aspectRatio = width ./ height;

 

% An aspect ratio between 0.25 and 1 is typical for individual characters

% as they are usually not very short and wide or very tall and skinny.

roi = roi( aspectRatio > 0.25 & aspectRatio < 1 ,:);

 

% Show regions after applying the area and aspect ratio constraints.

img = insertShape(I, 'rectangle', roi);

figure;

imshow(img);

![Descripción: http://es.mathworks.com/help/examples/vision\_product/win64/OCRExample\_11.png](images/00120.jpeg)

The remaining regions can be passed into the ocr function, which accepts rectangular regions of interest as input. The size of the regions are increased slightly to include additional background pixels around the text characters. This helps to improve the internal heuristics used to determine the polarity of the text on the background (e.g. light text on a dark background vs. dark text on a light background).

roi(:,1:2) = roi(:,1:2) - 4;

roi(:,3:4) = roi(:,3:4) + 8;

results = ocr(BW1, roi, 'TextLayout', 'Block');

The recognized text can be displayed on the original image using insertObjectAnnotation. The deblank function is used to remove any trailing characters, such as white space or new lines. There are a few missing classifications in these results (e.g. the digit 8) that are correctable using additional pre-processing techniques.

text = deblank( {results.Text} );

img  = insertObjectAnnotation(I, 'rectangle', roi, text);

 

figure;

imshow(img)

![Descripción: http://es.mathworks.com/help/examples/vision\_product/win64/OCRExample\_12.png](images/00121.jpeg)

Although vision.BlobAnalysis enabled you to find the digits in the keypad image, it may not work as well for images of natural scenes where there are many objects in addition to the text.

## 6.5.6 Summary

This example showed how the ocr function can be used to recognize text in images, and how a seemingly easy image for OCR required extra pre-processing steps to produce good results.

#  

# 6.6 Start Deep Learning Faster Using Transfer Learning

 

Transfer learning is commonly used in deep learning applications. You can take a pretrained network and use it as a starting point to learn a new task. Fine-tuning a network with transfer learning is much faster and easier than training from scratch. You can quickly make the network learn a new task using a smaller number of training images. The advantage of transfer learning is that the pretrained network has already learned a rich set of features that can be applied to a wide range of other similar tasks.

For example, if you take a network trained on thousands or millions of images, you can retrain it for new object detection using only hundreds of images. You can effectively fine-tune a pretrained network with much smaller data sets than the original training data. Transfer learning might not be faster than training a new network if you have a very large dataset.

Transfer learning enables you to:

·        Transfer the learned features of a pretrained network to a new problem

·        Transfer learning is faster and easier than training a new network

·        Reduce training time and dataset size

·        Perform deep learning without needing to learn how to create a whole new network

#  

# 6.7 Train Classifiers Using Features Extracted from Pretrained Networks

#  

Feature extraction allows you to use the power of pretrained networks without investing time and effort into training. Feature extraction can be the fastest way to use deep learning. You extract learned features from a pretrained network, and use those features to train a classifier, for example, a support vector machine (SVM — requires Statistics and Machine Learning Toolbox™). For example, if an SVM trained using `alexnet` can achieve >90% accuracy on your training and validation set, then fine-tuning with transfer learning might not be worth the effort to gain some extra accuracy. You also risk overfitting the training data if you perform fine-tuning on a small dataset. If the SVM cannot achieve good enough accuracy for your application, then fine-tuning is worth the effort to seek higher accuracy.

# 6.8 Deep Learning with Big Data on GPUs and in Parallel

 

Neural networks are inherently parallel algorithms. You can take advantage of this parallelism by using Parallel Computing Toolbox™ to distribute training across multicore CPUs, graphical processing units (GPUs), and clusters of computers with multiple CPUs and GPUs.

Training deep networks is extremely computationally intensive and you can usually accelerate training by using a high performance GPU. If you do not have a suitable GPU, you can train on one or more CPU cores instead. You can train a convolutional neural network on a single GPU or CPU, or on multiple GPUs or CPU cores, or in parallel on a cluster. Using GPU or parallel options requires Parallel Computing Toolbox.

You do not need multiple computers to solve problems using data sets too big to fit in memory. You can use the `imageDatastore` function to work with batches of data without needing a cluster of machines. However, if you have a cluster available, it can be helpful to take your code to the data repository rather than moving large amounts of data around.

 

 

 

 
| **Deep Learning Hardware and Memory Considerations** || **Recommendations** || **Required Products** |
| --- | --- | --- |
| Data too large to fit in memory || To import data from image collections that are too large to fit in memory, use the `imageDatastore` function. This function is designed to read batches of images for faster processing in machine learning and computer vision applications. || MATLABNeural Network Toolbox |
| CPU || If you do not have a suitable GPU, you can train on a CPU instead. By default, the [`trainNetwork`](http://www.mathworks.com/help/nnet/ref/trainnetwork.html) function uses the CPU if no GPU is available. || MATLABNeural Network Toolbox |
| GPU || By default, the [`trainNetwork`](http://www.mathworks.com/help/nnet/ref/trainnetwork.html) function uses a GPU if available. Requires a CUDA^®\-enabled NVIDIA^® GPU with compute capability 3.0 or higher. Check your GPU using `gpuDevice`. Specify the execution environment using the [`trainingOptions`](http://www.mathworks.com/help/nnet/ref/trainingoptions.html)function. || MATLABNeural Network ToolboxParallel Computing Toolbox |
| Parallel on your local machine using multiple GPUs or CPU cores || Take advantage of multiple workers by specifying the execution environment with the [`trainingOptions`](http://www.mathworks.com/help/nnet/ref/trainingoptions.html)  function. If you have more than one GPU on your machine, specify `'multi-gpu'`. Otherwise, specify `'parallel'`. || MATLABNeural Network ToolboxParallel Computing Toolbox |
| Parallel on a cluster or in the cloud || Scale up to use workers on clusters or in the cloud to accelerate your deep learning computations. Use [`trainingOptions`](http://www.mathworks.com/help/nnet/ref/trainingoptions.html) and specify `'parallel'` to use a compute cluster. See [Deep Learning in the Cloud](http://www.mathworks.com/help/nnet/ug/deep-learning-in-matlab.html#bvnwvxn). || MATLABNeural Network Toolbox, Parallel Computing Toolbox, MATLAB Distributed Computing Server™ |

 

  

7Chapter 7

DEEP LEARNING IN THE CLOUD. PARALLEL COMPUTING 

# 7.1 DEEP LEARNING AND MULTIPLE GPUs

 

You can use MATLAB to perform deep learning with multiple GPUs. Using multiple GPUs to train a single model provides greater memory and parallelism. These additional resources afford you larger networks and datasets; and for models which take hours or days to train, could save you time.

 

Deep learning is faster when you can use high-performance GPUs for training. If you don't have a suitable GPU available, you can use the new Amazon EC2 P2 instances to experiment. P2 instances are high-specification multi-GPU machines. You can use deep learning on  machines with a single GPU, and later scale up to 8 GPUs per machine to accelerate training, utilizing parallel computing to train a large, neural network with all of the processing power available.

 

Deep learning uses neural networks to learn useful representations of features directly from data. Neural networks combine multiple nonlinear processing layers, using simple elements operating in parallel, inspired by biological nervous systems. Deep learning models can achieve state-of-the-art accuracy in object classification, sometimes exceeding human-level performance. You can train models using a large set of labeled data and neural network architectures that contain many layers, usually including some convolutional layers. Training these models is computationally intensive; you can usually accelerate training by using high-specification GPUs.

 

For this chapter, we use a well-known existing network called AlexNet. AlexNet is a deep convolutional neural network (CNN), designed for image classification with 1000 possible categories. MATLAB has a built-in helper function to load a pre-trained AlexNet network:

 

**% Load the AlexNet network network = alexnet;**

 

If the required package does not exist, you will be prompted to install it using the MATLAB Add-on Explorer. Inspect the layers of this network using the Layers property:

 

**network.Layers**

 

The goal is to classify images into the correct class. For this chapter, we created our own image dataset using images available under a Creative Commons license. The dataset contains 96,000 color images in 55 classes. Here we show five random images from the first five classes.

 

![](images/00122.gif)

 

We resize and crop each image to 227x227 to match the size of the input layer of AlexNet

 

 

 

 

 

 

 

 

 

# 7.2 Transfer Learning

 

Training a large network, such as AlexNet, requires millions of images and several days of compute time. The original AlexNet was trained over several days on a subset of the ImageNet dataset, which consisted of over a million labelled images in 1000 categories. AlexNet has learned rich feature representations for a wide range of images. To quickly train the AlexNet network to classify our new dataset, we use a technique called transfer learning. Transfer learning utilizes the idea that the features a network learns when trained on one dataset are also useful for other similar datasets. You can fix the initial layers of a pre-trained network, and only fine-tune the last few layers to learn the specific features of the new dataset. Transfer learning usually results in faster training times than training a new CNN and enables use of  a smaller dataset without overfitting.

 

The following code shows how to apply transfer learning to AlexNet to classify your own dataset. 

 

1.   Load the AlexNet network and replace the final few classification layers. To minimize changes to the feature layers in the rest of the network, increase the learning rate of the new fully-connected layer.

 

**% Load the AlexNet network networkOriginal = alexnet; layersOriginal = networkOriginal.Layers;**

**% Copy all but the last 3 layers layersTransfer = layersOriginal(1:end-3);**

**% Replace the fully connected layer with a higher learning rate layersTransfer(end+1) = fullyConnectedLayer(55,...**

**    'WeightLearnRateFactor',10,...**

**    'BiasLearnRateFactor',20);**

**% Replace the softmax and classification layers layersTransfer(end+1) = softmaxLayer(); layersTransfer(end+1) = classificationLayer();**

 

2\. Create the options for transfer learning. Compared to training a network from scratch, you can set a lower initial learning rate and train for fewer epochs.

 

**% Define the transfer learning training options optionsTransfer = trainingOptions('sgdm',...**

**    'MiniBatchSize',250,...**

**    'MaxEpochs',30,...**

**    'InitialLearnRate',0.00125,...**

**    'LearnRateDropFactor',0.1,...**

**    'LearnRateDropPeriod',20);**

 

3\. Supply the set of labelled training images to imageDatastore, specifying where you have saved the data. You can use an imageDatastore to efficiently access all of the image files.  imageDatastore is designed to read batches of images for faster processing in machine learning and computer vision applications. imageDatastore can import data from image collections that are too large to fit in memory.

 

**% Define the training data imdsTrain = imageDatastore('imageDataset/train',...**

**    'IncludeSubFolders',true,...**

**    'LabelSource','foldernames');**

 

The dataset images are split into two sets: one for training, and a second for testing. The training set in this example is in a local folder called 'imageDataset/train'.

 

4\. To train the network use the **[trainNetwork]** function: 

 

**net = trainNetwork(imdsTrain,layersTransfer,optionsTransfer);**

 

The result is a fully-trained network which can be used to classify your new dataset.

 

# 7.3 Test the Network

 

After you create a fully-trained network, you can use it to classify a new set of images and measure how accurate it is. The following code tests the accuracy of classification using the test set of images located in a local folder called 'imageDataset/test'. The accuracy score is the percentage of correctly classified images using the test set.

 

**% Define the testing data imdsTest = imageDatastore('imageDataset/test',...**

**    'IncludeSubfolders',true,...**

**    'LabelSource','foldernames');**

**% Measure the accuracy yTest = classify(net,imdsTest); accuracy = sum(yTest == imdsTest.Labels) / numel(imdsTest.Labels);**

 

# 7.4 Training with Multiple GPUs

 

Cutting-edge neural networks rely on increasingly large training datasets and networks structures. In turn, this requires increased training times and memory resources. To support training such networks, MATLAB provides support for training a single network using multiple GPUs in parallel. Depending on your network and dataset, this can provide the following benefits.

 

## 7.4.1 Increased GPU Memory

Convolutional neural networks are typically trained iteratively using batches of images. This is done because the whole dataset is far too big to fit into GPU memory. The optimal batch size depends on the exact network and dataset in question, so you need to experiment. Too large a batch size can lead to slow convergence, while too small a batch size can lead to no convergence at all. Often the batch size is dictated by the GPU memory available. For larger networks, the memory requirements per image increases and the maximum batch size is reduced.

 

When training with multiple GPUs, each image batch is distributed between the GPUs. This effectively increases the total GPU memory available, allowing larger batch sizes. Depending on your application, a larger batch size could provide better convergence or classification accuracy.

 

## 7.4.2 Reduced Training Time

Using multiple GPUs can provide a significant improvement in performance. When deciding if you expect multi-GPU training to deliver a performance gain, consider the following factors:

 

·        How long is the iteration on each GPU? If each GPU iteration is short, the added overhead of communication between GPUs can dominate. Try increasing the computation per iteration by using a larger batch size.

·        Are you using more than 8 GPUs? Communication between more than 8 GPUs on a single machine introduces a significant communication delay.

·        Are all the GPUs on a single machine? Communication between GPUs on different machines introduces a significant communication delay. 

 

By default, the **[trainNetwork]** function uses a GPU (if available), otherwise the CPU is used. If you have more than one GPU on your local machine, enable multiple GPU training by setting the 'ExecutionEnvironment' option to 'multi-gpu' in your training options. As discussed above, you may also wish to increase the batch size and learning rate for better convergence and/or performance.

 

**% Define the multi-gpu training options optionsTransfer = trainingOptions('sgdm',...**

**    'MiniBatchSize',2000,...**

**    'MaxEpochs',30,...**

**    'InitialLearnRate',0.01,...**

**    'LearnRateDropFactor',0.1,...**

**    'LearnRateDropPeriod',20,...**

**    'ExecutionEnvironment','multi-gpu');**

If you do not have multiple GPUs on your local machine, you can use Amazon EC2 to lease a multiGPU cloud cluster.

 

# 7.5 Scale Up to Deep Learning in the Cloud

 

Having performed transfer learning on one desktop computer, you now want to make use of a high- specification multi-GPU machine. Amazon can provide suitable machines on demand, using their new P2 instances. The new ***Amazon EC2 P2*** [](https://aws.amazon.com/ec2/instance-types/p2/) instances are machines specifically designed for compute-intensive applications, providing up to 16 NVIDIA Tesla K80 GPUs per machine. In the following sections, you can learn how to reserve a P2 instance, connect to the data, and train a model in parallel using multiple GPUs in the cloud.

 

To use deep learning in the cloud, you need:

 

•                  MATLAB, Neural Network Toolbox, Parallel Computing Toolbox™

•                  A MathWorks account

•                  Access to ***MATLAB Distributed Computing Server™ for Amazon EC2***

•                  An Amazon Web Services account

## 7.5.1 Connecting to Amazon EC2 Using MathWorks Cloud Center

Amazon Elastic Compute Cloud (Amazon EC2) is a web service which you can use to set up compute capacity in the cloud. Amazon EC2 is ideally suited for intensive computational demands and large datasets found in deep learning. By using Amazon EC2, you can economically scale up your computing resources and gain access to domain-specific hardware. You can use a single GPU to take advantage of the parallel nature of neural networks, dramatically reducing the time required to train a single model. You can use multiple GPUs to train larger models in less time. You can scale up beyond the desktop, and scale in a flexible way without requiring any long-term commitment. 

 

MathWorks Cloud Center is a web application for creating and accessing compute clusters in the Amazon Web Services cloud for parallel computing with MATLAB. You can access a cloud cluster from your client MATLAB session, like any other cluster in your own onsite network. To learn more, refer to ***MATLAB Distributed Computing Server for Amazon EC2***. To set up your credentials and create a new cluster, refer to ***Create and Manage Clusters*** [i](http://www.mathworks.com/help/cloudcenter/ug/cloud-computing-console.html)n the Cloud Center documentation. 

 

In the following example, we create a cluster of a single machine with 8 GPUs and 8 workers. Setting the number of workers equal to the number of GPUs ensures there is no competition between workers for GPU resources. The main steps are:

 

*   Log in to ***Cloud Center*** using your MathWorks email address and password. 
*   Click **User Preferences** and follow the on-screen instructions to set up your Amazon Web Services (AWS) credentials. For help, refer to the Cloud Center documentation: ***Set Up Your Amazon Web Services (AWS) Credentials.*** 
*   To create a cluster of Amazon EC2 instances, click **Create a Cluster**.
*   Complete the following steps, and then ensure your settings look similar to the screenshot below. 

 

*   Name the cluster
*   Choose an appropriate **Region**
*   Select **Machine Type: Double Precision GPU (p2.8xlarge, 16 core, 8 GPU)**
*   For **Number of Workers**, select **8**
*   Leave the other settings as defaults and click **Create Cluster**

 

![](images/00123.jpeg)

*Cloud Center: Create a cluster with multiple GPUs.*

 

*   To access your cluster from MATLAB, on the home tab select Parallel > Discover Clusters to search for your Amazon EC2 clusters. When you select the cluster, the wizard automatically sets it as your default cluster.

 

Confirm your cluster is online: either from Cloud Center, or from within MATLAB by creating a cluster instance and displaying the details:

 

**cluster = parcluster(); disp(cluster);**

 

By default, if the cluster is left idle for too long, it automatically shuts down to avoid incurring unwanted expense. If your cluster has shut down, bring it back online either by clicking **Start Up** in Cloud Center, or typing **start(cluster);** in MATLAB: **start(cluster);**

 

After your cluster is online, query the GPU device of each worker:

**wait(cluster) spmd     disp(gpuDevice()); end**

 

This returns details of the GPU device visible to each worker process in your cluster. The spmd block automatically starts the workers in a parallel pool, if you have default preferences. The first time you create a parallel pool on a cloud cluster can take several minutes. 

 

You can start or shut down the parallel pool using the Parallel Pool menu in the bottom left of the MATLAB desktop.

 

# 7.6 Training with a GPU Cluster

 

To enable training on a compute cluster, set the 'ExecutionEnvironment' option to 'parallel' in your training options.

 

**% Define the parallel training options optionsTransfer = trainingOptions('sgdm',...**

**    'MiniBatchSize',2000,...**

**    'MaxEpochs',30,...**

**    'InitialLearnRate',0.01,...**

**    'LearnRateDropFactor',0.1,...**

**    'LearnRateDropPeriod',20,...**

**    'ExecutionEnvironment','parallel');**

 

If no pool is open, **[trainNetwork]** will automatically open one using the default cluster profile. If the pool has access to GPUs, then they will be used.

 

When training on a cluster, the location passed to **[imageDatastore]** must exist on both the client MATLAB and on the worker MATLAB. For this reason, we store our data in an Amazon S3 bucket. An S3 location is referenced by a URL, hence the path is visible on all machines. For more information on using data in S3, refer to Use Data in Amazon S3 Storage.

 

# 7.7 Use Data in Amazon S3 Storage

 

Amazon Simple Storage Service (S3) provides secure and scalable storage in the cloud. Once data is uploaded to Amazon S3, it can be accessed from anywhere, making it ideally suited for distributing machine learning datasets to cloud clusters. We uploaded our training and test images stored locally in the 'imageDataset' folder to an S3 bucket of the same name. More information about uploading and accessing data using S3 can be found in the ***Amazon S3 documentation.***

 

By default, objects stored in Amazon S3 are private and can only be accessed by their owner. To access or modify these resources, the client must first have the correct authentication tokens. To generate these tokens, the resource owner can use the AWS Management Console to create an  **Access Key ID** and corresponding **Secret Access Key**. Clients who they share tokens with will then have programmatic access to their data stored in Amazon S3. Further details about generating access keys can be found in the ***Amazon Access Keys documentation.***

 

The following example demonstrates how you would configure your AWS authentication tokens as environment variables. Enter in your local MATLAB:

 

**% Set AWS credentials as environment variables on local client MATLAB setenv('AWS\_ACCESS\_KEY\_ID', 'AKIAIOSFODNN7EXAMPLE'); setenv('AWS\_SECRET\_ACCESS\_KEY', ... 'wJalrXUtnFEMI/K7MDENG/nPxRiCYEXAMPLEKEY');**

 

To access training data, you now simply create an image datastore pointing to the URL of the S3 bucket.

 

**% Define the Amazon S3 training data imdsTrain = imageDatastore('s3://imageDataset/train',...**

**    'IncludeSubfolders', true, ...**

**    'LabelSource', 'foldernames');**

 

To access S3 resources from a cluster, you must set the same environment variables on your workers. The following code manually opens a parallel pool on your cloud cluster and copies the necessary environment variables to the workers.

 

**% Set AWS credentials on all workers aws\_access\_key\_id = getenv('AWS\_ACCESS\_KEY\_ID'); aws\_secret\_access\_key\_id = getenv('AWS\_SECRET\_ACCESS\_KEY'); spmd     setenv('AWS\_ACCESS\_KEY\_ID',aws\_access\_key\_id);     setenv('AWS\_SECRET\_ACCESS\_KEY',aws\_secret\_access\_key\_id); end**

 

The workers now have access to the Amazon S3 resources for the lifetime of the parallel pool.

 

# 7.8 Results

 

Having used Mathworks Cloud Center and Amazon EC2 to lease a multi-GPU compute cluster, we would now like to investigate the performance benefits which this affords. The following plot shows the classification accuracy of our network as a function of training time. The classification accuracy is defined as the accuracy achieved by the network on the mini batch of images for the current training iteration. The training was repeated four times, each using a different number of GPUs to train the network in parallel. As discussed in ***Increased GPU Memory***, training across more GPUs permits a larger image batch size. We therefore scale the image batch size with the number of GPUs to fully utilize the available memory. To normalize the learning rate per epoch, we also scale the learning rate with the image batch size, because a larger batch size provides fewer iterations per epoch.

![](images/00124.jpeg)

*Training convergence with varying numbers of GPUs.*

 

These results show that the additional memory and parallelism of more GPUs can provide significantly faster training. Smoothing out the data, we find that the time taken to reach a classification accuracy of 95% decreases by approximately 30-40% with each doubling of the number of GPUs used to train. This reduces the training time to around 10 minutes when using 8 GPUs, compared to more than 40 minutes with a single GPU. 

 

To further quantify these results, we plot the average image throughput, to normalize for the different batch sizes. This shows an increase in the number of images processed per unit time of approximately 70% with each doubling of the number of GPUs.

 

![](images/00125.jpeg)

*Image throughput with varying numbers of GPUs.*

 

Using a separate dataset of test images, we measure the classification accuracy of our networks on unseen images. The four networks trained with different numbers of GPUs all achieve an accuracy of 87%, to within half a percent.

To see the script for training AlexNet with your own data using a multi-GPU cluster, see  ***Appendix – MATLAB code***. 

 

**Note:** Creating a cluster and parallel pool in the cloud can take up to 10 minutes. For the small problem analyzed in this paper, this was a significant proportion of the total time. For other problems where the total training time can take hours or days, this cluster startup time becomes negligible.

 

# 7.9 Conclusions

 

In this chapter, we show how you can use MATLAB to train a large, deep neural network. The code provides a worked example; demonstrating how to train a network to classify images, use it to classify a new set of images, and measure the accuracy of the classification. Using Mathworks Cloud Center with Amazon EC2 to lease a multi-GPU compute cluster, we demonstrate a significant reduction in training time by distributing the work across multiple GPUs in parallel. For large datasets, such a performance increase can save hours or days.

 

**Useful links:**

 

For more information, see the following resources:

 

·        ***https://www.mathworks.com/discovery/deep-learning.html***

 

Central resource for Deep Learning with MATLAB

 

·        ***https://www.mathworks.com/help/nnet/convolutional-neural-networks.html***

 

Neural Network Toolbox documentation on essential tools for deep learning

 

·        ***https://www.mathworks.com/products/parallel-computing/parallel-computing-on-the-cloud/***

·        ***https://aws.amazon.com/console/***

#  

# 7.10 Appendix – MATLAB Code

 

The following MATLAB code uses transfer learning to train AlexNet on a new image dataset stored in Amazon S3 using a cluster. To run this script, use your own Amazon S3 bucket and set the appropriate environment variables for your Amazon Access key.

 

**% Number of workers to train with. Set this number equal to the number of % GPUs on you cluster. If you specify more workers than GPUs, the remaining**

**% workers will be idle. numberOfWorkers = 8;**

**% Scale batch size with expected number of GPUs miniBatchSize = 250 \* numberOfWorkers;**

**% Scale learning rate with batch size learningRate = 0.00125 \* numberOfWorkers;**

**%% Load the AlexNet network networkOriginal = alexnet; layersOriginal = networkOriginal.Layers;**

**% Copy all but the last 3 layers layersTransfer = layersOriginal(1:end-3);**

**% Replace the fully connected layer with a higher learning rate**

**% The output size should be equal to the number of labels in your dataset. layersTransfer(end+1) = fullyConnectedLayer(55,...**

**    'WeightLearnRateFactor',10,...**

**    'BiasLearnRateFactor',20);**

**% Replace the softmax and classification layers layersTransfer(end+1) = softmaxLayer(); layersTransfer(end+1) = classificationLayer();**

**%% Start a parallel pool if one is not already open pool = gcp('nocreate'); if isempty(pool)     parpool(numberOfWorkers); elseif (pool.NumWorkers ~= numberOfWorkers)     delete(pool);     parpool(numberOfWorkers); end**

**%% Copy local AWS credentials to all workers aws\_access\_key\_id = getenv('AWS\_ACCESS\_KEY\_ID'); aws\_secret\_access\_key\_id = getenv('AWS\_SECRET\_ACCESS\_KEY'); spmd     setenv('AWS\_ACCESS\_KEY\_ID',aws\_access\_key\_id);     setenv('AWS\_SECRET\_ACCESS\_KEY',aws\_secret\_access\_key\_id); end**

**%% Load the training and test data imds = imageDatastore('s3://imageDataset',...**

**    'IncludeSubfolders',true, ...**

**    'LabelSource','foldernames');**

**%% Shuffle and split data into training and testing**

**\[imdsTrain,imdsTest\] = splitEachLabel(shuffle(imds),0.9);**

**%% Define the transfer learning training options optionsTransfer = trainingOptions('sgdm',...**

**    'MiniBatchSize',miniBatchSize,...**

**    'MaxEpochs',30,...**

**    'InitialLearnRate',learningRate,...**

**    'LearnRateDropFactor',0.1,...**

**    'LearnRateDropPeriod',20,...**

**    'Verbose',true,... **

**    'ExecutionEnvironment','parallel');**

**%% Train the network on the cluster net = trainNetwork(imdsTrain,layersTransfer,optionsTransfer);**

**%% Record the accuracy for this network**

**% Uses the trained network to classify the test images on the local machine**

**% and compares this to their ground truth labels. YTest = classify(net,imdsTest); accuracy = sum(YTest == imdsTest.Labels)/numel(imdsTest.Labels);**

 

 

 

  

**8Chapter 8**

CONVOLUTIONAL Neural NetworkS WITH MATLAB. FUNCTIONS 

**8.1 Perform classification, feature extraction, and transfer learning using convolutional neural networks (CNNs, ConvNets)**

 

Convolution neural networks (CNNs or ConvNets) are essential tools for deep learning, and are especially suited for image recognition. You can construct a CNN architecture, train a network, and use the trained network to predict class labels. You can also extract features from a pre-trained network, and use these features to train a linear classifier. Neural Network Toolbox also enables you to perform transfer learning; that is, retrain the last fully connected layer of an existing CNN on new data.

 

**8.2 Construct Network Architecture. FUNCTIONS**

 

MATLAB has the following functions:

 

 
| [imageInputLayer](http://www.mathworks.com/help/nnet/ref/imageinputlayer.html) || Image input layer |
| --- | --- |
| [convolution2dLayer](http://www.mathworks.com/help/nnet/ref/convolution2dlayer.html) || Convolutional layer |
| [reluLayer](http://www.mathworks.com/help/nnet/ref/relulayer.html) || Rectified Linear Unit (ReLU) layer |
| [crossChannelNormalizationLayer](http://www.mathworks.com/help/nnet/ref/crosschannelnormalizationlayer.html) || Channel-wise local response normalization layer |
| [averagePooling2dLayer](http://www.mathworks.com/help/nnet/ref/averagepooling2dlayer.html) || Average pooling layer object |
| [maxPooling2dLayer](http://www.mathworks.com/help/nnet/ref/maxpooling2dlayer.html) || Max pooling layer |
| [fullyConnectedLayer](http://www.mathworks.com/help/nnet/ref/fullyconnectedlayer.html) || Fully connected layer |
| [dropoutLayer](http://www.mathworks.com/help/nnet/ref/dropoutlayer.html) || Dropout layer |
| [softmaxLayer](http://www.mathworks.com/help/nnet/ref/softmaxlayer.html) || Softmax layer |
| [classificationLayer](http://www.mathworks.com/help/nnet/ref/classificationlayer.html) || Create a classification output layer |

 

## 8.2.1 Create an image input layer: imageInputLayer

**Syntax**

·        inputlayer = imageInputLayer(inputSize)

·        inputlayer = imageInputLayer(inputSize,Name,Value)

**Description**

[inputlayer](http://www.mathworks.com/help/nnet/ref/imageinputlayer.html#outputarg_inputlayer) = imageInputLayer([inputSize](http://www.mathworks.com/help/nnet/ref/imageinputlayer.html#inputarg_inputSize)) returns an image input layer.

[inputlayer](http://www.mathworks.com/help/nnet/ref/imageinputlayer.html#outputarg_inputlayer) = imageInputLayer([inputSize](http://www.mathworks.com/help/nnet/ref/imageinputlayer.html#inputarg_inputSize),[Name,Value](http://www.mathworks.com/help/nnet/ref/imageinputlayer.html#namevaluepairarguments)) returns an image input layer, with additional options specified by one or more Name,Value pair arguments. For example, you can specify a name for the layer.

**Examples: Create Image Input Layer**

Create an image input layer for 28-by-28 color images. Specify that the software flips the images from left to right at training time with a probability of 0.5.

inputlayer = imageInputLayer(\[28 28 3\],'DataAugmentation','randfliplr')

inputlayer = 

 

  ImageInputLayer with properties:

 

                Name: ''

           InputSize: \[28 28 3\]

    DataAugmentation: 'randfliplr'

       Normalization: 'zerocenter'

**Input Arguments**

**inputSize — Size of input data**

**  
row vector of two or three integer numbers**

Size of the input data, specified as a row vector of two integer numbers corresponding to \[height,width\] or three integer numbers corresponding to \[height,width,channels\].

If the inputSize is a vector of two numbers, then the software sets the channel size to 1.

**Example: **\[200,200,3\]

**Data Types: **single | double

**Name-Value Pair Arguments**

Specify optional comma-separated pairs of Name,Value arguments. Name is the argument name and Value is the corresponding value. Name must appear inside single quotes (' '). You can specify several name and value pair arguments in any order as Name1,Value1,...,NameN,ValueN.

**Example: **'DataAugmentation','randcrop','Normalization','none','Name','input' specifies that the software takes a random crop of the image at training time, does not normalize the data, and assigns the name of the layer as input.

**'DataAugmentation' — Data augmentation transforms  
'none' (default) | 'randcrop' | 'randfliplr' | cell array of 'randcrop' and 'randfliplr'**

 

Data augmentation transforms to use during training, specified as the comma-separated pair consisting of 'DataAugmentation' and one of the following.

 

·        'none' — No data augmentation

·        'randcrop' — Take a random crop from the training image. The random crop has the same size as the inputSize.

·        'randfliplr' — Randomly flip the input images from left to right with a 50% chance in the vertical axis.

·        Cell array of 'randcrop' and 'randfliplr'. The software applies the augmentation in the order specified in the cell array.

 

Augmentation of image data is another way of reducing overfitting 

**Example: **'DataAugmentation',{'randfliplr','randcrop'}

 

**Data Types: **char | cell

**'Normalization' — Data transformation  
'zerocenter' (default) | 'none'**

 

Data transformation to apply every time data is forward-propagated through the input layer, specified as the comma-separated pair consisting of 'Normalization' and one of the following.

·        'zerocenter' — The software subtracts its mean from the training set.

·        'none' — No transformation.

**Example: **'Normalization','none'

**Data Types: **char

**'Name' — Name for the layer  
'' (default) | character vector**

 

Name for the layer, specified as the comma-separated pair consisting of Name and a character vector.

 

**Example: **'Name','inputlayer'

**Data Types: **char

**Output Arguments**

**inputlayer — Input layer for the image data  
  
**

**ImageInputLayer object**

 

Input layer for the image data, returned as an [ImageInputLayer](http://www.mathworks.com/help/nnet/ref/imageinputlayer-class.html) object.

For information on concatenating layers to construct convolutional neural network architecture, see [Layer](http://www.mathworks.com/help/nnet/ref/layer-class.html).

## 8.2.2 Create 2-D convolutional layer: convolution2dLayer

**Syntax**

·        `convlayer = convolution2dLayer(filterSize,numFilters)`

·        `convlayer = convolution2dLayer(filterSize,numFilters,Name,Value)`

**Description**

`convlayer` `= convolution2dLayer(``filterSize``,``numFilters``)` returns a [layer for 2-D convolution](http://www.mathworks.com/help/nnet/ref/convolution2dlayer.html#bu7kxr9-4).

`convlayer` `= convolution2dLayer(``filterSize``,``numFilters``,``Name,Value``)` returns the convolutional layer, with additional options specified by one or more `Name,Value` pair arguments.

**Examples:**

**Create convolutional layer**

Create a convolutional layer with 96 filters, each with a height and width of 11. Use a stride (step size) of 4 in the horizontal and vertical directions.

`convlayer = convolution2dLayer(11,96,'Stride',4);` 

**Specify Initial Weight and Biases in Convolutional Layer**

Create a convolutional layer with 32 filters, each with a height and width of 5. Pad the input image with 2 pixels along its border. Set the learning rate factor for the bias to 2. Manually initialize the weights from a Gaussian distribution with a standard deviation of 0.0001.

`layer = convolution2dLayer(5,32,'Padding',2,'BiasLearnRateFactor',2);` 

Suppose the input has color images. Manually initialize the weights from a Gaussian distribution with standard deviation of 0.0001.

`layer.Weights = randn([5 5 3 32])*0.0001;` 

The size of the local regions in the layer is 5-by-5. The number of color channels for each region is 3. The number of feature maps is 32 (the number of filters). Therefore, there are 5\*5\*3\*32 weights in the layer.

`randn([5 5 3 32])` returns a 5-by-5-by-3-by-32 array of values from a Gaussian distribution with a mean of 0 and a standard deviation of 1. Multiplying the values by 0.0001 sets the standard deviation of the Gaussian distribution equal to 0.0001.

Similarly, initialize the biases from a Gaussian distribution with a mean of 1 and a standard deviation of 0.00001.

`layer.Bias = randn([1 1 32])*0.00001+1;` 

There are 32 feature maps, and therefore 32 biases. `randn([1 1 32])` returns a 1-by-1-by-32 array of values from a Gaussian distribution with a mean of 0 and a standard deviation of 1. Multiplying the values by 0.00001 sets the standard deviation of values equal to 0.00001, and adding 1 sets the mean of the Gaussian distribution equal to 1.

**Convolution That Fully Covers the Input Image**

Suppose the size of the input image is 28-by-28-1. Create a convolutional layer with 16 filters that have a height of 6 and a width of 4, that traverses the image with a stride of 4 both horizontally and vertically. Make sure the convolution covers the images completely.

For the convolution to fully cover the input image, both the horizontal and vertical output dimensions must be integer numbers. For the horizontal output dimension to be an integer, one row zero padding is required on the top and bottom of the image: (28 – 6+ 2\*1)/4 + 1 = 7. For the vertical output dimension to be an integer, no zero padding is required: (28 – 4+ 2\*0)/4 + 1 = 7. Construct the convolutional layer as follows:

`convlayer = convolution2dLayer([6 4],16,'Stride',4,'Padding',[1 0]);` 

**Input Arguments**

### `filterSize` — height and width of filters integer value | vector of two integer      values

 

Height and width of the filters, specified as an integer value or a vector of two integer values. `filterSize` defines the size of the local regions to which the neurons connect in the input.

 

·        If `filterSize` is a scalar value, then the filters have the same height and width.

·        If `filterSize` is a vector, then it must be of the form \[*h* *w*\], where *h* is the height and *w* is the width.

**Example:**`[5,5]`

**Data Types:**`single` | `doublé`

 

### `numFilters` — Number of filters integer value

 

Number of filters, specified as an integer value. `numFilters` represents the number of neurons in the convolutional layer that connect to the same region in the input. This parameter determines the number of channels (feature maps) in the output of the convolutional layer.

 

**Data Types:**`single` | `doublé`

**Output Arguments**

### `convlayer` — 2-D convolutional layer Convolution2DLayer object

 

2-D convolutional layer for convolutional neural networks, returned as a [`Convolution2DLayer`](http://www.mathworks.com/help/nnet/ref/convolution2dlayer-class.html) object.

**Convolutional Layer**

A convolutional layer consists of neurons that connect to small regions of the input or the layer before it. These regions are called *filters*. You can specify the size of these regions using the [`filterSize`](http://www.mathworks.com/help/nnet/ref/convolution2dlayer.html#inputarg_filterSize) input argument.

For each region, the software computes a dot product of the weights and the input, and then adds a bias term. The filter then moves along the input vertically and horizontally, repeating the same computation for each region, i.e., convolving the input. The step size with which it moves is called a *stride*. You can specify this step size with the `Stride` name-value pair argument. These local regions that the neurons connect to might overlap depending on the `filterSize` and `Stride`.

The number of weights used for a filter is *h*\**w*\**c*, where *h* is the height, and *w* is the width of the filter size, and *c* is the number of channels in the input (for example, if the input is a color image, the number of channels is three). As a filter moves along the input, it uses the same set of weights and bias for the convolution, forming a feature map. The convolution layer usually has multiple feature maps, each with a different set of weights and a bias. The number of feature maps is determined by the number of filters.

The total number of parameters in a convolutional layer is ((*h*\**w*\**c* \+ 1)\**Number of Filters*), where 1 is for the bias.

The output height and width of the convolutional layer is (*Input Size* – *Filter Size* \+ 2\**Padding*)/*Stride* \+ 1. This value must be an integer for the whole image to be fully covered. If the combination of these parameters does not lead the image to be fully covered, the software by default ignores the remaining part of the image along the right and bottom edge in the convolution.

The total number of neurons in a feature map, say *Map Size*, is the product of the output height and width. The total number of neurons (output size) in a convolutional layer, then, is *Map Size*\**Number of Filters*.

For example, suppose that the input image is a 28-by-28-by-3 color image. For a convolutional layer with 16 filters, and a filter size of 8-by-8, the number of weights per filter is 8\*8\*3 = 192, and the total number of parameters in the layer is (192+1) \* 16 = 3088. Assuming stride is 4 in each direction, the total number of neurons in each feature map is 6-by-6 ((28 – 8+0)/4 + 1 = 6). Then, the total number of neurons in the layer is 6\*6\*16 = 256. Usually, the results from these neurons pass through some form of nonlinearity, such as rectified linear units (ReLU).

## 8.2.3 Create a Rectified Linear Unit (ReLU) layer: reluLayer

**Syntax**

·        `layer = reluLayer()`

·        `layer = reluLayer(Name,Value)`

**Description**

`layer` `= reluLayer()` returns a rectified linear unit (ReLU) layer. It performs a threshold operation to each element, where any input value less than zero is set to zero, i.e.,

*![](images/00126.jpeg)*

The ReLU layer does not change the size of its input.

` `

`layer` `= reluLayer(``Name,Value``)` returns a ReLU layer, with the additional option specified by the `Name,Value` pair argument.

**Examples**

Create a rectified linear unit layer with the name `relu1`.

 

`layer = reluLayer('Name','relu1');` 

 

## 8.2.4 Create a local response normalization layer: crossChannelNormalizationLayer

**Syntax**

·        `localnormlayer = crossChannelNormalizationLayer(windowChannelSize)`

·        `localnormlayer = crossChannelNormalizationLayer(windowChannelSize,Name,Value)`

**Description**

`localnormlayer` `= crossChannelNormalizationLayer(``windowChannelSize``)` returns a [local response normalization](http://www.mathworks.com/help/nnet/ref/crosschannelnormalizationlayer.html#bu868uk) layer, which carries out channel-wise normalization [\[1\]](http://www.mathworks.com/help/nnet/ref/crosschannelnormalizationlayer.html#bu6xy50).

`localnormlayer` `= crossChannelNormalizationLayer(``windowChannelSize``,``Name,Value``)` returns a local response normalization layer, with additional options specified by one or more `Name,Value` pair arguments.

**Examples**

Create a local response normalization layer for channel-wise normalization, where a window of five channels will be used to normalize each element, and the additive constant for the normalizer (*K*) is 1.

 

`localnormlayer = crossChannelNormalizationLayer(5,'K',1);` 

 

## 8.2.5 Create an average pooling layer: averagePooling2dLayer

**Syntax**

·        `avgpoollayer = averagePooling2dLayer(poolSize)`

·        `avgpoollayer = averagePooling2dLayer(poolSize,Name,Value)`

**Description**

`avgpoollayer` `= averagePooling2dLayer(``poolSize``)` returns a layer that performs [average pooling](http://www.mathworks.com/help/nnet/ref/averagepooling2dlayer.html#bu7kwr9-2), dividing the input into rectangular regions and computing the average of each region. `poolSize` specifies the dimensions of the rectangular region.

`avgpoollayer` `= averagePooling2dLayer(``poolSize``,``Name,Value``)` returns the average pooling layer, with additional options specified by one or more `Name,Value` pair arguments.

**Examples:**

**Average Pooling Layer with Non-Overlapping Pooling Regions**

Create an average pooling layer with non-overlapping pooling regions, which down-samples by a factor of 2.

`avgpoollayer = averagePooling2dLayer(2,'Stride',2);`` ` 

The height and width of the rectangular region (pool size) are both 2. This layer creates pooling regions of size \[2,2\] and takes the average of the four elements in each region. Because the stride (step size for moving along the images vertically and horizontally) is also \[2,2\] the pooling regions do not overlap.

**Average Pooling Layer with Overlapping Pooling Regions**

Create an average pooling layer with overlapping pooling regions. Also add padding for the top and bottom of the input.

`avgpoollayer = averagePooling2dLayer([3,2],'Stride',2,'Padding',[1 0]);` 

The height and width of the rectangular region (pool size) are 3 and 2. This layer creates pooling regions of size \[3,2\] and takes the average of the six elements in each region. Because the stride is \[2,2\], the pooling regions overlap.

A value of `1` for the `Padding` name-value pair indicates that software also adds a row of zeros to the top and bottom of the input data. `0` indicates that no padding is added to the right and left of the input data.

 

## 8.2.6 Create max pooling layer: maxPooling2dLayer

**Syntax**

·        maxpoollayer = maxPooling2dLayer(poolSize)

·        maxpoollayer = maxPooling2dLayer(poolSize,Name,Value)

**Description**

[maxpoollayer](http://www.mathworks.com/help/nnet/ref/maxpooling2dlayer.html#outputarg_maxpoollayer) = maxPooling2dLayer([poolSize](http://www.mathworks.com/help/nnet/ref/maxpooling2dlayer.html#inputarg_poolSize)) returns a layer that performs [max pooling](http://www.mathworks.com/help/nnet/ref/maxpooling2dlayer.html#bu7kv4s-2), dividing the input into rectangular regions and returning the maximum value of each region. poolSize specifies the dimensions of a pooling region.

[maxpoollayer](http://www.mathworks.com/help/nnet/ref/maxpooling2dlayer.html#outputarg_maxpoollayer) = maxPooling2dLayer([poolSize](http://www.mathworks.com/help/nnet/ref/maxpooling2dlayer.html#inputarg_poolSize),[Name,Value](http://www.mathworks.com/help/nnet/ref/maxpooling2dlayer.html#namevaluepairarguments)) returns the max pooling layer, with additional options specified by one or more Name,Value pair arguments.

**Examples:**

**Max Pooling Layer with Non-Overlapping Pooling Regions**

 

Create a max pooling layer with non-overlapping pooling regions, which down-samples by a factor of 2.

maxpoollayer = maxPooling2dLayer(2,'Stride',2);

The height and width of the rectangular region (pool size) are both 2. This layer creates pooling regions of size \[2,2\] and returns the maximum of the four elements in each region. Because the stride (step size for moving along the images vertically and horizontally) is also \[2,2\], the pooling regions do not overlap.

**Max Pooling Layer with Overlapping Pooling Regions**

 

Create a max pooling layer with overlapping pooling regions. Also add padding for the top and bottom of the input.

maxpoollayer = maxPooling2dLayer(\[3,2\],'Stride',2,'Padding',\[1 0\]);

The height and width of the rectangular region (pool size) are 3 and 2. This layer creates pooling regions of size \[3,2\] and returns the maximum of the six elements in each region. Because the stride (step size for moving along the images vertically and horizontally) is \[2,2\], the pooling regions overlap.

The value 1 for the Padding name-value pair indicates that the software adds a row of zeros to the top and bottom of the input data. 0 indicates that no padding is added to the right and left of the input data.

## 8.2.7 Create fully connected layer: fullyConnectedLayer

**Syntax**

·        fullconnectlayer = fullyConnectedLayer(outputSize)

·        fullconnectlayer = fullyConnectedLayer(outputSize,Name,Value)

**Description**

[fullconnectlayer](http://www.mathworks.com/help/nnet/ref/fullyconnectedlayer.html#outputarg_fullconnectlayer) = fullyConnectedLayer([outputSize](http://www.mathworks.com/help/nnet/ref/fullyconnectedlayer.html#inputarg_outputSize)) returns a fully connected layer, in which the software multiplies the input by a weight matrix and then adds a bias vector.

[fullconnectlayer](http://www.mathworks.com/help/nnet/ref/fullyconnectedlayer.html#outputarg_fullconnectlayer) = fullyConnectedLayer([outputSize](http://www.mathworks.com/help/nnet/ref/fullyconnectedlayer.html#inputarg_outputSize),[Name,Value](http://www.mathworks.com/help/nnet/ref/fullyconnectedlayer.html#namevaluepairarguments)) returns a fully connected layer with additional options specified by one or more Name,Value pair arguments.

**Examples:**

**Create Fully Connected Layer**

Create a fully connected layer with an output size of 10.

fullconnectlayer = fullyConnectedLayer(10);

The software determines the input size at training time.

**Specify Initial Weight and Biases in Fully Connected Layer**

Create a fully connected layer with an output size of 10. Set the learning rate factor for the bias to 2. Manually initialize the weights from a Gaussian distribution with a standard deviation of 0.0001.

layers = \[imageInputLayer(\[28 28 1\],'Normalization','none');

          convolution2dLayer(5,20,'NumChannels',1);

          reluLayer();

          maxPooling2dLayer(2,'Stride',2);

          fullyConnectedLayer(10);

          softmaxLayer();

          classificationLayer()\];

To initialize the weights of the fully connected layer, you must know the layer's input size. The input size is equal to the output size of the preceding max pooling layer, which, in turn, depends on the output size of the convolutional layer.

For one direction in a channel (feature map) of the convolutional layer, the output is ((28 – 5 + 2\*0)/1) +1 = 24. The max pooling layer has nonoverlapping regions, so it down-samples by 2 in each direction, i.e., 24/2 = 12. For one channel of the convolutional layer, the output of the max pooling layer is 12 \* 12 = 144. There are 20 channels in the convolutional layer, so the output of the max pooling layer is 144 \* 20 = 2880. This is the size of the input to the fully connected layer.

The formula for overlapping regions gives the same result: For one direction of a channel, the output is (((24 – 2 +0)/2) + 1 = 12. For one channel, the output is 144, and for all 20 channels in the convolutional layer, the output of the max pooling layer is 2880.

Initialize the weights of the fully connected layer from a Gaussian distribution with a mean of 0 and a standard deviation of 0.0001.

layers(5).Weights = randn(\[10 2880\])\*0.0001;

randn(\[10 2880\]) returns a 10-by-2880 matrix of values from a Gaussian distribution with mean 0 and standard deviation 1. Multiplying the values by 0.0001 sets the standard deviation of the Gaussian distribution equal to 0.0001.

Similarly, initialize the biases from a Gaussian distribution with a mean of 1 and a standard deviation of 0.0001.

layers(5).Bias = randn(\[10 1\])\*0.0001+1;

The size of the bias vector is equal to the output size of the fully connected layer, which is 10. randn(\[10 1\]) returns a 10-by-1 vector of values from a Gaussian distribution with a mean of 0 and a standard deviation of 1. Multiplying the values by 0.00001 sets the standard deviation of values equal to 0.00001, and adding 1 sets the mean of the Gaussian distribution equal to 1.

## 8.2.8 Create a dropout layer: dropoutLayer

**Syntax**

·        droplayer = dropoutLayer()

·        droplayer = dropoutLayer(probability)

·        droplayer = dropoutLayer(\_\_\_,Name,Value)

**Description**

[droplayer](http://www.mathworks.com/help/nnet/ref/dropoutlayer.html#outputarg_droplayer) = dropoutLayer() returns a [dropout layer](http://www.mathworks.com/help/nnet/ref/dropoutlayer.html#bu71zk2-2), which randomly sets input elements to zero with a probability of 0.5. Dropout layer only works at training time.

[droplayer](http://www.mathworks.com/help/nnet/ref/dropoutlayer.html#outputarg_droplayer) = dropoutLayer([probability](http://www.mathworks.com/help/nnet/ref/dropoutlayer.html#inputarg_probability)) returns a dropout layer, which randomly sets input elements to zero with a probability specified by probability.

[droplayer](http://www.mathworks.com/help/nnet/ref/dropoutlayer.html#outputarg_droplayer) = dropoutLayer(**\_\_\_**,[Name,Value](http://www.mathworks.com/help/nnet/ref/dropoutlayer.html#namevaluepairarguments)) returns the dropout layer, with the additional option specified by the Name,Value pair argument.

**Examples**

Create a dropout layer, which randomly sets about 40% of the input to zero. Assign the name of the layer as dropout1.

 

droplayer = dropoutLayer(0.4,'Name','dropout1');

## 8.2.9 Create a softmax layer softmaxLayer

**Syntax**

·        smlayer = softmaxLayer()

·        smlayer = softmaxLayer(Name,Value)

**Description**

[smlayer](http://www.mathworks.com/help/nnet/ref/softmaxlayer.html#outputarg_smlayer) = softmaxLayer() returns a softmax layer for classification problems. The softmax layer uses the softmax activation function.

[smlayer](http://www.mathworks.com/help/nnet/ref/softmaxlayer.html#outputarg_smlayer) = softmaxLayer([Name,Value](http://www.mathworks.com/help/nnet/ref/softmaxlayer.html#namevaluepairarguments)) returns a softmax layer, with the additional option specified by the Name,Value pair argument.

**Examples**

**Create Softmax Layer with Specified Name**

 

Create a softmax layer with the name sml1.

smlayer = softmaxLayer('Name','sml1');

## 8.2.10 Create a classification output layer: classificationLayer

**Syntax**

·        `coutputlayer = classificationLayer()`

·        `coutputlayer = classificationLayer(Name,Value)`

**Description**

`coutputlayer` `= classificationLayer()` returns a classification output layer for a neural network. The classification output layer holds the name of the [loss function](http://www.mathworks.com/help/nnet/ref/classificationlayer.html#bu80p30-3) that the software uses for training the network for multi-class classification, the size of the output, and the class labels.

`coutputlayer` `= classificationLayer(``Name,Value``)` returns the classification output layer, with the additional option specified by the `Name,Value` pair argument.

**Examples**

Create a classification output layer with the name `'coutput'`.

 

`coutputlayer = classificationLayer('Name','coutput')``coutputlayer = `` ``  ClassificationOutputLayer with properties:`` ``      OutputSize: 'auto'``    LossFunction: 'crossentropyex'``      ClassNames: {}``            Name: 'coutput'` 

 

The software determines the output layer automatically during training. The default loss function for classification is cross entropy for *k* mutually exclusive classes.

 

**8.3 TRAIN NETWORKS. FUNCTIONS**

 

MATLAB has the following functions:

 

 
| [`trainingOptions`](http://www.mathworks.com/help/nnet/ref/trainingoptions.html) || Options for training neural network |
| --- | --- |
| [`trainNetwork`](http://www.mathworks.com/help/nnet/ref/trainnetwork.html) || Train a network |

 

## 8.3.1 Train network: trainNetwork

**Syntax**

·        `trainedNet = trainNetwork(imds,layers,options)`

·        `trainedNet = trainNetwork(X,Y,layers,options)`

·        `[trainedNet,traininfo] = trainNetwork(`**\_\_\_**`)`

**Description**

**NOTE: **`trainNetwork`**requires the Parallel Computing Toolbox and a CUDA^®\-enabled NVIDIA^®GPU with compute capability 3.0 or higher.**

`trainedNet` `= trainNetwork(``imds``,``layers``,``options``)` returns a trained network defined by the convolutional neural network (ConvNet) architecture, `layers`, for the input image data, `imds`, using the training options, `options`.

`trainedNet` `= trainNetwork(``X``,``Y``,``layers``,``options``)` returns a trained network for the predictors in `X` and responses in `Y`.

`[``trainedNet``,``traininfo``] = trainNetwork(`**\_\_\_**`)` also returns information on the training for any of the above input arguments.

**Examples:**

**Train a Convolutional Neural Network Using Data in ImageDatastore**

Load the sample data as an `ImageDatastore` object.

 

`digitDatasetPath = fullfile(matlabroot,'toolbox','nnet','nndemos',...``    'nndatasets','DigitDataset');``digitData = imageDatastore(digitDatasetPath,...``        'IncludeSubfolders',true,'LabelSource','foldernames');`` ` 

The data store contains 10000 synthetic images of digits 0-9. The images are generated by applying random transformations to digit images created using different fonts. Each digit image is 28-by-28 pixels.

Display some of the images in the datastore.

`for i = 1:20``    subplot(4,5,i);``    imshow(digitData.Files{i});``end` 

![](images/00127.jpeg)

 

Check the number of images in each digit category.

`digitData.countEachLabel``ans = `` ``    Label    Count``    _____    _____`` ``    0         988 ``    1        1026 ``    2        1003 ``    3         993 ``    4         991 ``    5        1017 ``    6         992 ``    7         999 ``    8        1003 ``    9         988 `` ` 

The data contains an unequal number of images per category.

To balance the number of images for each digit in the training set, first find the minimum number of images in a category.

`minSetCount = min(digitData.countEachLabel{:,2})``minSetCount =`` ``   988`` ` 

Divide the dataset so that each category in the training set has 494 images and the testing set has the remaining images from each label.

`trainingNumFiles = round(minSetCount/2);``rng(1) % For reproducibility``[trainDigitData,testDigitData] = splitEachLabel(digitData,...``                                  trainingNumFiles,'randomize');` 

`splitEachLabel` splits the image files in `digitData` into two new datastores, `trainDigitData` and `testDigitData`.

 

Define the convolutional neural network architecture.

`layers = [imageInputLayer([28 28 1]);``          convolution2dLayer(5,20);``          reluLayer();``          maxPooling2dLayer(2,'Stride',2);``          fullyConnectedLayer(10);``          softmaxLayer();``          classificationLayer()];`` ` 

Set the options to default settings for the stochastic gradient descent with momentum. Set the maximum number of epochs at 20, and start the training with an initial learning rate of 0.001.

`options = trainingOptions('sgdm','MaxEpochs',20,...``        'InitialLearnRate',0.001);` 

Train the network.

`convnet = trainNetwork(trainDigitData,layers,options);`` ``|=========================================================================================|``|     Epoch    |   Iteration  | Time Elapsed |  Mini-batch  |  Mini-batch  | Base Learning|``|              |              |  (seconds)   |     Loss     |   Accuracy   |     Rate     |``|=========================================================================================|``|            2 |           50 |         0.72 |       0.2232 |       92.97% |     0.001000 |``|            3 |          100 |         1.37 |       0.0182 |       99.22% |     0.001000 |``|            4 |          150 |         1.99 |       0.0141 |      100.00% |     0.001000 |``|            6 |          200 |         2.64 |       0.0023 |      100.00% |     0.001000 |``|            7 |          250 |         3.27 |       0.0004 |      100.00% |     0.001000 |``|            8 |          300 |         3.91 |       0.0001 |      100.00% |     0.001000 |``|           10 |          350 |         4.56 |       0.0002 |      100.00% |     0.001000 |``|           11 |          400 |         5.19 |       0.0003 |      100.00% |     0.001000 |``|           12 |          450 |         5.82 |       0.0001 |      100.00% |     0.001000 |``|           14 |          500 |         6.46 |       0.0001 |      100.00% |     0.001000 |``|           15 |          550 |         7.09 |       0.0001 |      100.00% |     0.001000 |``|           16 |          600 |         7.72 |       0.0001 |      100.00% |     0.001000 |``|           18 |          650 |         8.37 |       0.0001 |      100.00% |     0.001000 |``|           19 |          700 |         9.00 |       0.0001 |      100.00% |     0.001000 |``|           20 |          750 |         9.62 |       0.0001 |      100.00% |     0.001000 |``|=========================================================================================|` 

Run the trained network on the test set that was not used to train the network and predict the image labels (digits).

`YTest = classify(convnet,testDigitData);``TTest = testDigitData.Labels;` 

Calculate the accuracy.

`accuracy = sum(YTest == TTest)/numel(TTest)``accuracy =`` ``    0.9984`` ` 

Accuracy is the ratio of the number of true labels in the test data matching the classifications from classify, to the number of images in the test data. In this case about 99.8% of the digit estimations match the true digit values in the test set.

**Construct and Train a Convolutional Neural Network**

Load the sample data.

`load lettersTrainSet`` ` 

XTrain contains 1500 28-by-28 grayscale images of the letters A, B, and C in a 4-D array. There is equal numbers of each letter in the data set. TTrain contains the categorical array of the letter labels.

Display some of the letter images.

`figure;``for j = 1:20``    subplot(4,5,j);``    selectImage = datasample(XTrain,1,4);``    imshow(selectImage,[]);``end` 

![](images/00128.jpeg)

Define the convolutional neural network architecture.

`layers = [imageInputLayer([28 28 1]);``          convolution2dLayer(5,16);``          reluLayer();``          maxPooling2dLayer(2,'Stride',2);``          fullyConnectedLayer(3);``          softmaxLayer();``          classificationLayer()];` 

 

Set the options to default settings for the stochastic gradient descent with momentum.

`options = trainingOptions('sgdm');` 

Train the network.

`rng('default') % For reproducibility``net = trainNetwork(XTrain,TTrain,layers,options);`` ``|=========================================================================================|``|     Epoch    |   Iteration  | Time Elapsed |  Mini-batch  |  Mini-batch  | Base Learning|``|              |              |  (seconds)   |     Loss     |   Accuracy   |     Rate     |``|=========================================================================================|``|            5 |           50 |         0.50 |       0.2175 |       98.44% |     0.010000 |``|           10 |          100 |         1.01 |       0.0238 |      100.00% |     0.010000 |``|           14 |          150 |         1.52 |       0.0108 |      100.00% |     0.010000 |``|           19 |          200 |         2.03 |       0.0088 |      100.00% |     0.010000 |``|           23 |          250 |         2.53 |       0.0048 |      100.00% |     0.010000 |``|           28 |          300 |         3.04 |       0.0035 |      100.00% |     0.010000 |``|=========================================================================================|` 

Run the trained network on a test set that was not used to train the network and predict the image labels (letters).

`load lettersTestSet;` 

XTest contains 1500 28-by-28 grayscale images of the letters A, B, and C in a 4-D array. There is again equal numbers of each letter in the data set. TTest contains the categorical array of the letter labels.

`YTest = classify(net,XTest);` 

Compute the confusion matrix.

`targets(:,1)=(TTest=='A');``targets(:,2)=(TTest=='B');``targets(:,3)=(TTest=='C');``outputs(:,1)=(YTest=='A');``outputs(:,2)=(YTest=='B');``outputs(:,3)=(YTest=='C');`` ``plotconfusion(double(targets'),double(outputs'))`` ` 

## 8.3.2 Options for training neural network. trainingOptions

**Syntax**

·        `options = trainingOptions(solverName)`

·        `options = trainingOptions(solverName,Name,Value)`

**Description**

`options` `= trainingOptions(``solverName``)` returns a set of training options for the solver specified by `solverName`.

`options` `= trainingOptions(``solverName``,``Name,Value``)` returns a set of training options, with additional options specified by one or more `Name,Value` pair arguments.

**Examples**

Create a set of options for training a network using stochastic gradient descent with momentum. Reduce the learning rate by a factor of 0.2 every 5 epochs. Set the maximum number of epochs for training at 20, and use a mini-batch with 300 observations at each iteration. Specify a path for saving checkpoint networks after every epoch.

`options = trainingOptions('sgdm',...``      'LearnRateSchedule','piecewise',...``      'LearnRateDropFactor',0.2,... ``      'LearnRateDropPeriod',5,... ``      'MaxEpochs',20,... ``      'MiniBatchSize',300,...``      'CheckpointPath','C:\TEMP\checkpoint');`` ` 

# 8.4 Extract Features and Predict Outcomes. FUNCTIONS

MATLAB has the following functions:

 

 
| [`activations`](http://www.mathworks.com/help/nnet/ref/seriesnetwork.activations.html) || Compute network layer activations |
| --- | --- |
| [`predict`](http://www.mathworks.com/help/nnet/ref/seriesnetwork.predict.html) || Predict responses using a trained network |
| [`classify`](http://www.mathworks.com/help/nnet/ref/seriesnetwork.classify.html) || Classify data using a trained network |

` ` 

## 8.4.1 Compute network layer activations: activations

**Syntax**

·        `features = activations(net,X,layer)`

·        `features = activations(net,X,layer,Name,Value)`

**Description**

`features` `= activations(``net``,``X``,``layer``)` returns network activations for a specific layer using the trained network `net` and the data in `X`.

`features` `= activations(``net``,``X``,``layer``,``Name,Value``)` returns network activations for a specific layer with additional options specified by one or more `Name,Value` pair arguments.

For example, you can specify the format of the output `trainedFeatures`.

**Example: Extract Features from Trained Convolutional Neural Network**

**NOTE:** Training a convolutional neural network requires Parallel Computing Toolbox™ and a CUDA®-enabled NVIDIA® GPU with compute capability 3.0 or higher.

 

Load the sample data.

\[XTrain,TTrain\] = digitTrain4DArrayData;

 

digitTrain4DArrayData loads the digit training set as 4-D array data. XTrain is a 28-by-28-by-1-by-4940 array, where 28 is the height and 28 is the width of the images. 1 is the number of channels and 4940 is the number of synthetic images of handwritten digits. TTrain is a categorical vector containing the labels for each observation.

 

Construct the convolutional neural network architecture.

layers = \[imageInputLayer(\[28 28 1\]);

          convolution2dLayer(5,20);

          reluLayer();

          maxPooling2dLayer(2,'Stride',2);

          fullyConnectedLayer(10);

          softmaxLayer();

          classificationLayer()\];

Set the options to default settings for the stochastic gradient descent with momentum.

options = trainingOptions('sgdm');

Train the network.

rng('default')

net = trainNetwork(XTrain,TTrain,layers,options);

|=========================================================================================|

|     Epoch    |   Iteration  | Time Elapsed |  Mini-batch  |  Mini-batch  | Base Learning|

|              |              |  (seconds)   |     Loss     |   Accuracy   |     Rate     |

|=========================================================================================|

|            2 |           50 |         0.45 |       2.2301 |       47.66% |     0.010000 |

|            3 |          100 |         0.88 |       0.9880 |       75.00% |     0.010000 |

|            4 |          150 |         1.31 |       0.5558 |       82.03% |     0.010000 |

|            6 |          200 |         1.75 |       0.4022 |       89.06% |     0.010000 |

|            7 |          250 |         2.17 |       0.3750 |       88.28% |     0.010000 |

|            8 |          300 |         2.61 |       0.3368 |       91.41% |     0.010000 |

|           10 |          350 |         3.04 |       0.2589 |       96.09% |     0.010000 |

|           11 |          400 |         3.47 |       0.1396 |       98.44% |     0.010000 |

|           12 |          450 |         3.90 |       0.1802 |       96.09% |     0.010000 |

|           14 |          500 |         4.33 |       0.0892 |       99.22% |     0.010000 |

|           15 |          550 |         4.76 |       0.1221 |       96.88% |     0.010000 |

|           16 |          600 |         5.19 |       0.0961 |       98.44% |     0.010000 |

|           18 |          650 |         5.62 |       0.0856 |       99.22% |     0.010000 |

|           19 |          700 |         6.05 |       0.0651 |      100.00% |     0.010000 |

|           20 |          750 |         6.49 |       0.0582 |       98.44% |     0.010000 |

|           22 |          800 |         6.92 |       0.0808 |       98.44% |     0.010000 |

|           23 |          850 |         7.35 |       0.0521 |       99.22% |     0.010000 |

|           24 |          900 |         7.77 |       0.0248 |      100.00% |     0.010000 |

|           25 |          950 |         8.20 |       0.0241 |      100.00% |     0.010000 |

|           27 |         1000 |         8.63 |       0.0253 |      100.00% |     0.010000 |

|           28 |         1050 |         9.07 |       0.0260 |      100.00% |     0.010000 |

|           29 |         1100 |         9.49 |       0.0246 |      100.00% |     0.010000 |

|=========================================================================================|

 

Make predictions, but rather than taking the output from the last layer, specify the second ReLU layer (the sixth layer) as the output layer.

trainFeatures = activations(net,XTrain,6);

These predictions from an inner layer are known as *activations* or *features* . activations method, by default, uses a CUDA-enabled GPU with compute ccapability 3.0, when available. You can also choose to run activations on a CPU using the 'ExecutionEnvironment','cpu' name-value pair argument.

You can use the returned features to train a support vector machine using the Statistics and Machine Learning Toolbox™ function [fitcecoc](http://www.mathworks.com/help/stats/fitcecoc.html).

svm = fitcecoc(trainFeatures,TTrain);

Load the test data.

\[XTest,TTest\]= digitTest4DArrayData;

Extract the features from the same ReLU layer (the sixth layer) for test data and use the returned features to train a support vector machine.

testFeatures = activations(net,XTest,6);

testPredictions = predict(svm,testFeatures);

Plot the confusion matrix. Convert the data into the format plotconfusion accepts

ttest = dummyvar(double(TTest))'; % dummyvar requires Statistics and Machine Learning Toolbox

tpredictions = dummyvar(double(testPredictions))';

plotconfusion(ttest,tpredictions);

![Descripción: http://www.mathworks.com/help/examples/nnet/ExtractFeaturesFromTrainedConvolutionalNeuralNetworkExample\_01.png](images/00129.jpeg)

The overall accuracy for the test data using the trained network net is 99.4%.

Manually compute the overall accuracy.

accuracy = sum(TTest == testPredictions)/numel(TTest)

accuracy =

 

    0.9937

 

## 8.4.2 Predict responses using a trained network: predict

**Syntax**

`YPred = predict(net,X)`  
`YPred = predict(net,X,Name,Value)`

**Description**

`YPred` `= predict(``net``,``X``)` predicts responses for data in `X` using the trained network `net`.

`YPred` `= predict(``net``,``X``,``Name,Value``)` predicts responses with the additional option specified by the `Name,Value` pair argument.

**Examples: Predict Output Scores Using a Trained ConvNet**

**NOTE:** Training a convolutional neural network requires Parallel Computing Toolbox and a CUDA®-enabled NVIDIA® GPU with compute capability 3.0 or higher.

 

Load the sample data.

\[XTrain,TTrain\] = digitTrain4DArrayData;

digitTrain4DArrayData loads the digit training set as 4-D array data. XTrain is a 28-by-28-by-1-by-4940 array, where 28 is the height and 28 is the width of the images. 1 is the number of channels and 4940 is the number of synthetic images of handwritten digits. TTrain is a categorical vector containing the labels for each observation.

Construct the convolutional neural network architecture.

layers = \[imageInputLayer(\[28 28 1\]);

          convolution2dLayer(5,20);

          reluLayer();

          maxPooling2dLayer(2,'Stride',2);

          fullyConnectedLayer(10);

          softmaxLayer();

          classificationLayer()\];

Set the options to default settings for the stochastic gradient descent with momentum.

options = trainingOptions('sgdm');

Train the network.

rng(1)

net = trainNetwork(XTrain,TTrain,layers,options);

|=========================================================================================|

|     Epoch    |   Iteration  | Time Elapsed |  Mini-batch  |  Mini-batch  | Base Learning|

|              |              |  (seconds)   |     Loss     |   Accuracy   |     Rate     |

|=========================================================================================|

|            2 |           50 |         0.42 |       2.2315 |       51.56% |     0.010000 |

|            3 |          100 |         0.83 |       1.0606 |       68.75% |     0.010000 |

|            4 |          150 |         1.25 |       0.6321 |       82.03% |     0.010000 |

|            6 |          200 |         1.67 |       0.3873 |       85.16% |     0.010000 |

|            7 |          250 |         2.09 |       0.4310 |       89.84% |     0.010000 |

|            8 |          300 |         2.52 |       0.3524 |       90.63% |     0.010000 |

|           10 |          350 |         2.94 |       0.2313 |       96.88% |     0.010000 |

|           11 |          400 |         3.36 |       0.2115 |       94.53% |     0.010000 |

|           12 |          450 |         3.78 |       0.1681 |       96.88% |     0.010000 |

|           14 |          500 |         4.21 |       0.1171 |      100.00% |     0.010000 |

|           15 |          550 |         4.64 |       0.0920 |       99.22% |     0.010000 |

|           16 |          600 |         5.06 |       0.1015 |       99.22% |     0.010000 |

|           18 |          650 |         5.49 |       0.0682 |       98.44% |     0.010000 |

|           19 |          700 |         5.92 |       0.0927 |       99.22% |     0.010000 |

|           20 |          750 |         6.35 |       0.0685 |       98.44% |     0.010000 |

|           22 |          800 |         6.77 |       0.0496 |       99.22% |     0.010000 |

|           23 |          850 |         7.20 |       0.0483 |       99.22% |     0.010000 |

|           24 |          900 |         7.64 |       0.0492 |       99.22% |     0.010000 |

|           25 |          950 |         8.06 |       0.0390 |      100.00% |     0.010000 |

|           27 |         1000 |         8.49 |       0.0315 |      100.00% |     0.010000 |

|           28 |         1050 |         8.92 |       0.0187 |      100.00% |     0.010000 |

|           29 |         1100 |         9.35 |       0.0338 |      100.00% |     0.010000 |

|=========================================================================================|

 

Run the trained network on a test set and predict the scores.

\[XTest,TTest\]= digitTest4DArrayData;

YTestPred = predict(net,XTest);

predict, by default, uses a CUDA-enabled GPU with compute ccapability 3.0, when available. You can also choose to run predict on a CPU using the 'ExecutionEnvironment','cpu' name-value pair argument.

Display the first 10 images in the test data and compare to the predictions from predict.

 

TTest(1:10,:)

ans = 

 

     0 

     0 

     0 

     0 

     0 

     0 

     0 

     0 

     0 

     0 

 

YTestPred(1:10,:)

ans =

 

  10×10 single matrix

 

  Columns 1 through 7

 

    1.0000    0.0000    0.0000    0.0000    0.0000    0.0000    0.0000

    1.0000    0.0000    0.0000    0.0000    0.0000    0.0000    0.0000

    0.9998    0.0000    0.0000    0.0000    0.0001    0.0000    0.0000

    0.9981    0.0000    0.0005    0.0000    0.0000    0.0000    0.0000

    0.9898    0.0032    0.0037    0.0000    0.0000    0.0000    0.0002

    0.9987    0.0000    0.0013    0.0000    0.0000    0.0000    0.0000

    1.0000    0.0000    0.0000    0.0000    0.0000    0.0000    0.0000

    0.9922    0.0000    0.0000    0.0000    0.0000    0.0000    0.0000

    0.9930    0.0000    0.0000    0.0000    0.0000    0.0000    0.0000

    0.9846    0.0000    0.0000    0.0000    0.0000    0.0000    0.0080

 

  Columns 8 through 10

 

    0.0000    0.0000    0.0000

    0.0000    0.0000    0.0000

    0.0000    0.0000    0.0001

    0.0000    0.0011    0.0004

    0.0015    0.0014    0.0001

    0.0000    0.0000    0.0000

    0.0000    0.0000    0.0000

    0.0000    0.0000    0.0078

    0.0000    0.0000    0.0070

    0.0000    0.0000    0.0073

 

TTest contains the digits corresponding to the images in XTest. The columns of YTestPred contain predict's estimation of a probability that an image contains a particular digit. That is, the first column contains the probability estimate that the given image is digit 0, the second column contains the probability estimate that the image is digit 1, the third column contains the probability estimate that the image is digit 2, and so on. You can see that predict's estimation of probabilities for the correct digits are almost 1 and the probability for any other digit is almost 0. predict correctly estimates the first 10 observations as digit 0.

## 8.4.3 Classify data using a trained network: classify

**Syntax**

`[Ypred,scores] = classify(net,X)`  
`[Ypred,scores] = classify(net,X,Name,Value)`

**Description**

`[``Ypred``,``scores``] = classify(``net``,``X``)` estimates the classes for the data in `X` using the trained network, `net`.

`[``Ypred``,``scores``] = classify(``net``,``X``,``Name,Value``)` estimates the classes with the additional option specified by the `Name,Value` pair argument.

**Examples: Classify Images Using Trained ConvNet**

**NOTE:** Training a convolutional neural network requires Parallel Computing Toolbox™ and a CUDA®-enabled NVIDIA® GPU with compute capability 3.0 or higher.

 

Load the sample data.

`[XTrain,TTrain] = digitTrain4DArrayData;`` ` 

`digitTrain4DArrayData` loads the digit training set as 4-D array data. `XTrain` is a 28-by-28-by-1-by-4940 array, where 28 is the height and 28 is the width of the images. 1 is the number of channels and 4940 is the number of synthetic images of handwritten digits. `TTrain` is a categorical vector containing the labels for each observation.

 

Construct the convolutional neural network architecture.

`layers = [imageInputLayer([28 28 1]);``          convolution2dLayer(5,20);``          reluLayer();``          maxPooling2dLayer(2,'Stride',2);``          fullyConnectedLayer(10);``          softmaxLayer();``          classificationLayer()];`` ` 

Set the options to default settings for the stochastic gradient descent with momentum.

`options = trainingOptions('sgdm');` 

 

Train the network.

`rng('default')``net = trainNetwork(XTrain,TTrain,layers,options);``|=========================================================================================|``|     Epoch    |   Iteration  | Time Elapsed |  Mini-batch  |  Mini-batch  | Base Learning|``|              |              |  (seconds)   |     Loss     |   Accuracy   |     Rate     |``|=========================================================================================|``|            2 |           50 |         0.42 |       2.2301 |       47.66% |     0.010000 |``|            3 |          100 |         0.83 |       0.9880 |       75.00% |     0.010000 |``|            4 |          150 |         1.24 |       0.5558 |       82.03% |     0.010000 |``|            6 |          200 |         1.66 |       0.4023 |       89.06% |     0.010000 |``|            7 |          250 |         2.08 |       0.3750 |       88.28% |     0.010000 |``|            8 |          300 |         2.50 |       0.3368 |       91.41% |     0.010000 |``|           10 |          350 |         2.93 |       0.2589 |       96.09% |     0.010000 |``|           11 |          400 |         3.35 |       0.1396 |       98.44% |     0.010000 |``|           12 |          450 |         3.77 |       0.1802 |       96.09% |     0.010000 |``|           14 |          500 |         4.19 |       0.0892 |       99.22% |     0.010000 |``|           15 |          550 |         4.62 |       0.1221 |       96.88% |     0.010000 |``|           16 |          600 |         5.05 |       0.0961 |       98.44% |     0.010000 |``|           18 |          650 |         5.48 |       0.0857 |       99.22% |     0.010000 |``|           19 |          700 |         5.90 |       0.0651 |      100.00% |     0.010000 |``|           20 |          750 |         6.33 |       0.0582 |       98.44% |     0.010000 |``|           22 |          800 |         6.76 |       0.0808 |       98.44% |     0.010000 |``|           23 |          850 |         7.19 |       0.0521 |       99.22% |     0.010000 |``|           24 |          900 |         7.61 |       0.0248 |      100.00% |     0.010000 |``|           25 |          950 |         8.03 |       0.0241 |      100.00% |     0.010000 |``|           27 |         1000 |         8.46 |       0.0253 |      100.00% |     0.010000 |``|           28 |         1050 |         8.88 |       0.0260 |      100.00% |     0.010000 |``|           29 |         1100 |         9.31 |       0.0246 |      100.00% |     0.010000 |``|=========================================================================================|` 

 

Run the trained network on a test set.

`[XTest,TTest]= digitTest4DArrayData;``YTestPred = classify(net,XTest);` 

Display the first 10 images in the test data and compare to the classification from `classify`.

`[TTest(1:10,:) YTestPred(1:10,:)]``ans = `` ``     0      0 ``     0      0 ``     0      0 ``     0      0 ``     0      0 ``     0      0 ``     0      0 ``     0      0 ``     0      0 ``     0      0 `` ` 

The results from `classify` match the true digits for the first ten images.

Calculate the accuracy over all test data.

`accuracy = sum(YTestPred == TTest)/numel(TTest)``accuracy =`` ``    0.9929` 

 

 

 

  

**9Chapter 9**

CONVOLUTIONAL Neural NetworkS WITH MATLAB. CLASSES 

**9.1 INTRODUCTION**

 

Convolution neural networks (CNNs or ConvNets) are essential tools for deep learning, and are especially suited for image recognition. You can construct a CNN architecture, train a network, and use the trained network to predict class labels. You can also extract features from a pre-trained network, and use these features to train a linear classifier. Neural Network Toolbox also enables you to perform transfer learning; that is, retrain the last fully connected layer of an existing CNN on new data.

 

**9.2 Construct Network Architecture. CLASSES**

 

MATLAB has the following classes:

 

 
| [Layer](http://www.mathworks.com/help/nnet/ref/layer-class.html) || Network layer |
| --- | --- |

 

## 9.2.1 Network layer: layer

**Description**

Network layer class containing the layer information. Each layer in the architecture of a convolutional neural network is of Layer class.

**Construction**

To define the architecture of a convolutional neural network, create a vector of layers directly.

**Copy Semantics**

Value. To learn how value classes affect copy operations, see the following paragraphs: 

**Two Copy Behaviors**

There are two fundamental kinds of MATLAB^® objects — handles and values.

*Value* objects behave like MATLAB fundamental types with respect to copy operations. Copies are independent values. Operations that you perform on one object do not affect copies of that object.

*Handle* objects are referenced by their handle variable. Copies of the handle variable refer to the same object. Operations that you perform on a handle object are visible from all handle variables that reference that object.

**Value Object Copy Behavior**

MATLAB numeric variables are value objects. For example, when you copy `a` to the variable `b`, both variables are independent of each other. Changing the value of `a` does not change the value of `b`:

`a = 8;``b = a;` 

 

Now reassign `a`. `b` is unchanged:

`a = 6;``b``b =``     8` 

Clearing `a` does not affect `b`:

`clear a``b``b =``     8`` ``Value Object Properties` 

 

The copy behavior of values stored as properties in value objects is the same as numeric variables. For example, suppose `vobj1` is a value object with property `a`:

`vobj1.a = 8; ` 

If you copy `vobj1` to `vobj2`, and then change the value of `vobj1` property `a`, the value of the copied object's property, `vobj2.a`, is unaffected:

`vobj2 =vobj1;``vobj1.a = 5;``vobj2.a``ans =``     8` 

**Handle Object Copy Behavior**

Here is a handle class called `HdClass` that defines a property called `Data`.

`classdef HdClass < handle``   properties``      Data``   end``   methods``      function obj = HdClass(val)``         if nargin > 0``            obj.Data = val;``         end``      end``   end``end` 

Create an object of this class:

`hobj1 = HdClass(8)` 

Because this statement is not terminated with a semicolon, MATLAB displays information about the object:

`hobj1 = `` ``  HdClass with properties:`` ``    Data: 8` 

The variable `hobj1` is a handle that references the object created. Copying `hobj1` to `hobj2` results in another handle referring to the same object:

`hobj2 = hobj1``hobj2 = `` ``  HdClass with properties:`` ``    Data: 8` 

Because handles reference the object, copying a handle copies the handle to a new variable name, but the handle still refers to the same object. For example, given that `hobj1` is a handle object with property `Data`:

`hobj1.Data``ans =`` ``     8` 

Change the value of `hobj1`'s `Data` property and the value of the copied object's `Data` property also changes:

`hobj1.Data = 5;``hobj2.Data``ans =`` ``     5` 

Because `hobj2` and `hobj1` are handles to the same object, changing the copy, `hobj2`, also changes the data you access through handle `hobj1`:

`hobj2.Data = 17;``hobj1.Data``ans =`` ``    17` 

**Reassigning Handle Variables**

Reassigning a handle variable produces the same result as reassigning any MATLAB variable. When you create an object and assign it to `hobj1`:

`hobj1 = HdClass(3.14);` 

`hobj1` references the new object, not the same object referenced previously (and still referenced by `hobj2`).

**Clearing Handle Variables**

When you clear a handle from the workspace, MATLAB removes the variable, but does not remove the object referenced by the other handle. However, if there are no references to an object, MATLAB destroys the object.

Given `hobj1` and `hobj2`, which both reference the same object, you can clear either handle without affecting the object:

`hobj1.Data = 2^8;``clear hobj1``hobj2``hobj2 = `` ``  HdClass with properties:`` ``    Data: 256`` ` 

If you clear both `hobj1` and `hobj2`, then there are no references to the object. MATLAB destroys the object and frees the memory used by that object.

**Deleting Handle Objects**

To remove an object referenced by any number of handles, use [`delete`](http://www.mathworks.com/help/matlab/ref/delete.html). Given `hobj1` and `hobj2`, which both refer to the same object, delete either handle. MATLAB deletes the object:

`hobj1 = HdClass(8);``hobj2 = hobj1;``delete(hobj1)``hobj2``hobj2 = `` ``  handle to deleted HdClass` 

Use `clear` to remove the variable from the workspace.

**Modifying Objects**

When you pass an object to a function, MATLAB passes a copy of the object into the function workspace. If the function modifies the object, MATLAB modifies only the copy of the object that is in the function workspace. The differences in copy behavior between handle and value classes are important in such cases:

·        Value object — The function must return the modified copy of the object. To modify the object in the caller's workspace, assign the function output to a variable of the same name

·        Handle object — The copy in the function workspace refers to the same object. Therefore, the function does not have to return the modified copy.

**Testing for Handle or Value Class**

To determine if an object is a handle object, use the [`isa`](http://www.mathworks.com/help/matlab/ref/isa.html) function. If `obj` is an object of some class, this statement determines if `obj` is a handle:

`isa(obj,'handle')` 

For example, the `containers.Map` class creates a handle object:

`hobj = containers.Map({'Red Sox','Yankees'},{'Boston','New York'});``isa(hobj,'handle')``ans =`` ``     1` 

`hobj` is also a `containers.Map` object:

`isa(hobj,'containers.Map')``ans =`` ``     1` 

Querying the class of `hobj` shows that it is a `containers.Map` object:

`class(hobj)``ans =`` ``containers.Map` 

The [`class`](http://www.mathworks.com/help/matlab/ref/class.html) function returns the specific class of an object.

**Indexing**

You can access the properties of a layer in the network architecture by indexing into the vector of layers and using dot notation. For example, an image input layer is the first layer in a convolutional neural network. To access the InputSize property of the image input layer, use layers(1).InputSize. 

**Examples:**

**Construct Network Architecture**

 

Define a convolutional neural network architecture for classification, with only one convolutional layer, a ReLU layer, and a fully connected layer.

cnnarch = \[

        imageInputLayer(\[28 28 3\])

        convolution2dLayer(\[5 5\],10)

        reluLayer()

        fullyConnectedLayer(10)

        softmaxLayer()

        classificationLayer()

                 \];

Alternatively you can create the layers individually and then concatenate them.

input = imageInputLayer(\[28 28 3\]);

conv = convolution2dLayer(\[5 5\],10);

relu = reluLayer();

fcl = fullyConnectedLayer(10);

sml = softmaxLayer();

col = classificationLayer();

cnnarch = \[input;conv;relu;fcl;sml;col\];

cnnarch is a 6-by-1 vector of layers.

Display the class for this vector of layers.

class (cnnarch)

nnet.cnn.layer.Layer

cnnarch is a Layer object.

**Access Layers and Properties in a Layer Array**

 

Define a convolutional neural network architecture for classification, with only one convolutional layer, a ReLU layer, and a fully connected layer.

layers = \[imageInputLayer(\[28 28 3\])

        convolution2dLayer(\[5 5\],10)

        reluLayer()

        fullyConnectedLayer(10)

        softmaxLayer()

        classificationLayer()\];

Display the image input layer.

layers(1)

ans = 

 

  ImageInputLayer with properties:

 

                Name: ''

           InputSize: \[28 28 3\]

    DataAugmentation: 'none'

       Normalization: 'zerocenter'

Extract the input size.

layers(1).InputSize

ans =

 

    28    28     3

Display the stride for the convolutional layer.

layers(2).Stride

ans =

 

     1     1

Access the bias learn rate factor for the fully connected layer.

layers(4).BiasLearnRateFactor

ans =

 

     1

**Create a Typical Convolutional Neural Network Architecture**

 

Create a convolutional neural network for classification with two convolutional layers and two fully connected layers. Down-sample the convolutional layers using max pooling with 2-by-2 non-overlapping pooling regions. Use a rectified linear unit as nonlinear activation function for the convolutional layers and fully connected layer. Use local response normalization for the first two convolutional layers. The first convolutional layer has 12 4-by-3 filters and the second convolutional layer has 16 5-by-5 filters. The first fully connected layer has 100 neurons. Suppose the input data are gray images of size 28-by-28, and there are 10 classes. Assign a name to each layer.

layers = \[imageInputLayer(\[28 28 1\],'Normalization','none','Name','inputl')

          convolution2dLayer(\[4 3\],12,'NumChannels',1,'Name','conv1')

          reluLayer('Name','relu1')

          crossChannelNormalizationLayer(4,'Name','cross1')

          maxPooling2dLayer(2,'Stride',2,'Name','max1')

          convolution2dLayer(5,16,'NumChannels',12,'Name','conv2')

          reluLayer('Name','relu2');

          crossChannelNormalizationLayer(4,'Name','cross2')

          maxPooling2dLayer(2,'Stride',2,'Name','max2')

          fullyConnectedLayer(256,'Name','full1')

          reluLayer('Name','relu4')

          fullyConnectedLayer(10,'Name','full2')

          softmaxLayer('Name','softm')

          classificationLayer('Name','out')\];

**9.3 TRAIN NETWORKS. CLASSES**

 

MATLAB has the following classes:

 

 
| [SeriesNetwork](http://www.mathworks.com/help/nnet/ref/seriesnetwork-class.html) || Series network class |
| --- | --- |
| [TrainingOptionsSGDM](http://www.mathworks.com/help/nnet/ref/trainingoptionssgdm-class.html) || Training options for stochastic gradient descent with momentum |

## 9.3.1 Series network class: SeriesNetwork

**Description**

A series network class that contains the layers in the trained network. A series network is a network with layers arranged one after another. There is a single input and a single output.

**Construction**

trainedNet = trainNetwork(X,Y,layers,options) returns a trained network. trainedNet is a SeriesNetwork object.

For more information on training a convolutional neural network, see [trainNetwork](http://www.mathworks.com/help/nnet/ref/trainnetwork.html).

**Input Arguments**

**X — Images: 4-D numeric array**

**Y — Class labels: array of categorical responses**

**layers — An array of network layers: Layer object**

**options — Training options object**

**Methods**

 
| [activations](http://www.mathworks.com/help/nnet/ref/seriesnetwork.activations.html) || Compute network layer activations |
| --- | --- |
| [classify](http://www.mathworks.com/help/nnet/ref/seriesnetwork.classify.html) || Classify data using a trained network |
| [predict](http://www.mathworks.com/help/nnet/ref/seriesnetwork.predict.html) || Predict responses using a trained network |

**Copy Semantics**

Value. To learn how value classes affect copy operations, see the previous class.

**Examples: Construct and Train a Convolutional Neural Network**

Load the sample data.

\[XTrain,TTrain\] = digitTrain4DArrayData;

digitTrain4DArrayData loads the digit training set as 4-D array data. XTrain is a 28-by-28-by-1-by-4940 array, where 28 is the height and 28 is the width of the images. 1 is the number of channels and 4940 is the number of synthetic images of handwritten digits. TTrain is a categorical vector containing the labels for each observation.

 

Construct the convolutional neural network architecture.

layers = \[imageInputLayer(\[28 28 1\]);

          convolution2dLayer(5,20);

          reluLayer();

          maxPooling2dLayer(2,'Stride',2);

          fullyConnectedLayer(10);

          softmaxLayer();

          classificationLayer()\];

Set the options to default settings for the stochastic gradient descent with momentum.

options = trainingOptions('sgdm');

Train the network.

net = trainNetwork(XTrain,TTrain,layers,options);

|=========================================================================================|

|     Epoch    |   Iteration  | Time Elapsed |  Mini-batch  |  Mini-batch  | Base Learning|

|              |              |  (seconds)   |     Loss     |   Accuracy   |     Rate     |

|=========================================================================================|

|            2 |           50 |         0.42 |       2.2301 |       47.66% |     0.010000 |

|            3 |          100 |         0.83 |       0.9880 |       75.00% |     0.010000 |

|            4 |          150 |         1.26 |       0.5558 |       82.03% |     0.010000 |

|            6 |          200 |         1.68 |       0.4023 |       89.06% |     0.010000 |

|            7 |          250 |         2.10 |       0.3750 |       88.28% |     0.010000 |

|            8 |          300 |         2.53 |       0.3368 |       91.41% |     0.010000 |

|           10 |          350 |         2.95 |       0.2589 |       96.09% |     0.010000 |

|           11 |          400 |         3.38 |       0.1396 |       98.44% |     0.010000 |

|           12 |          450 |         3.80 |       0.1802 |       96.09% |     0.010000 |

|           14 |          500 |         4.22 |       0.0892 |       99.22% |     0.010000 |

|           15 |          550 |         4.66 |       0.1221 |       96.88% |     0.010000 |

|           16 |          600 |         5.08 |       0.0961 |       98.44% |     0.010000 |

|           18 |          650 |         5.51 |       0.0857 |       99.22% |     0.010000 |

|           19 |          700 |         5.93 |       0.0651 |      100.00% |     0.010000 |

|           20 |          750 |         6.35 |       0.0582 |       98.44% |     0.010000 |

|           22 |          800 |         6.77 |       0.0808 |       98.44% |     0.010000 |

|           23 |          850 |         7.19 |       0.0521 |       99.22% |     0.010000 |

|           24 |          900 |         7.61 |       0.0248 |      100.00% |     0.010000 |

|           25 |          950 |         8.04 |       0.0241 |      100.00% |     0.010000 |

|           27 |         1000 |         8.46 |       0.0253 |      100.00% |     0.010000 |

|           28 |         1050 |         8.89 |       0.0260 |      100.00% |     0.010000 |

|           29 |         1100 |         9.31 |       0.0246 |      100.00% |     0.010000 |

|=========================================================================================|

Run the trained network on a test set and predict the image labels (digits).

\[XTest,TTest\]= digitTest4DArrayData;

YTest = classify(net,XTest);

Calculate the accuracy.

accuracy = sum(YTest == TTest)/numel(TTest)

0.9929

**Tips**

·        A convolutional neural network model saved with R2016a can only be loaded with a GPU, because in R2016a, the learnable parameters are stored as gpuArrays. Once you load the model, you can resave it in R2016b. This saves the learnable parameters as MATLAB arrays. You can then change the execution environment to CPU while running the network.

## 9.3.2 Training options for stochastic gradient descent with momentum. TrainingOptionsSGDM 

**Description**

Class that is comprising training options such as learning rate information, L2 regularization factor, and mini-batch size for stochastic gradient descent with momentum.

**Construction**

options = trainingOptions([solverName](http://www.mathworks.com/help/nnet/ref/trainingoptionssgdm-class.html#inputarg_solverName)) returns a set of training options for the solver specified by solverName.

options = trainingOptions([solverName](http://www.mathworks.com/help/nnet/ref/trainingoptionssgdm-class.html#inputarg_solverName),Name,Value) returns a set of training options, with additional options specified by one or more Name,Value pair arguments.

**Input Arguments**

**solverName — Solver to use for training the network (default) | 'sgdm'**

**Properties**

**Momentum — Contribution of the previous gradient step a scalar value from 0 to 1**

**InitialLearnRate — Initial learning rate a scalar value**

**LearnRateScheduleSettings — Settings for learning rate schedule, specified by the user structure**

**L2Regularization — Factor for L2 regularizer scalar value**

**MaxEpochs — Maximum number of epochs an integer value**

**MiniBatchSize — Size of the mini-batch an integer value**

**Verbose — Indicator to display the information on the training progress 1 (default) | 0**

**Copy Semantics**

Value. To learn how value classes affect copy operations, see the previous class documentation.

**Examples. Specify Training Options**

Create a set of options for training with stochastic gradient descent with momentum. The learning rate will be reduced by a factor of 0.2 every 5 epochs. The training will last for 20 epochs, and each iteration will use a mini-batch with 300 observations.

options = trainingOptions('sgdm',...

      'LearnRateSchedule','piecewise',...

      'LearnRateDropFactor',0.2,... 

      'LearnRateDropPeriod',5,... 

      'MaxEpochs',20,... 

      'MiniBatchSize',300);

**9.4 Construct Network Architecture. Layers**

 

MATLAB has de following clases:

 
| [ImageInputLayer](http://www.mathworks.com/help/nnet/ref/imageinputlayer-class.html) || Image input layer |
| --- | --- |
| [Convolution2DLayer](http://www.mathworks.com/help/nnet/ref/convolution2dlayer-class.html) || Convolutional layer |
| [ReLULayer](http://www.mathworks.com/help/nnet/ref/relulayer-class.html) || Rectified Linear Unit (ReLU) layer |
| CrossChannelNormalizationLayer || Channel-wise local response normalization layer |
| [AveragePooling2DLayer](http://www.mathworks.com/help/nnet/ref/averagepooling2dlayer-class.html) || Average pooling layer object |
| [MaxPooling2DLayer](http://www.mathworks.com/help/nnet/ref/maxpooling2dlayer-class.html) || Max pooling layer |
| [FullyConnectedLayer](http://www.mathworks.com/help/nnet/ref/fullyconnectedlayer-class.html) || Fully connected layer |
| [DropoutLayer](http://www.mathworks.com/help/nnet/ref/dropoutlayer-class.html) || Dropout layer |
| [SoftmaxLayer](http://www.mathworks.com/help/nnet/ref/softmaxlayer-class.html) || Softmax layer |
| [ClassificationOutputLayer](http://www.mathworks.com/help/nnet/ref/classificationoutputlayer-class.html) || Classification output layer |

## 9.4.1 ImageInputLayer class

**Description**

Image input layer class containing the input size, data transformation, and the layer name.

**Construction**

inputlayer = imageInputLayer([inputSize](http://www.mathworks.com/help/nnet/ref/imageinputlayer-class.html#inputarg_inputSize)) returns an image input layer.

inputlayer = imageInputLayer([inputSize](http://www.mathworks.com/help/nnet/ref/imageinputlayer-class.html#inputarg_inputSize), Name,Value) returns an image input layer, with additional options specified by one or more Name,Value pair arguments.

For more information on the name-value pair arguments, see imageInputLayer.

**Input Arguments**

**inputSize — Size of input data row vector of two or three integer numbers**

**Properties**

**inputSize — Size of input data row vector of three integer numbers**

**DataAugmentation — Data augmentation transforms 'none' (default) | 'randcrop' | 'randfliplr' | cell array of 'randcrop' and 'randfliplr'**

**Normalization — Data transformation 'zerocenter' (default) | 'none'**

**Name — Layer name '' (default) | character vector**

**Examples: Create and Display Image Input Layer**

Create an image input layer for 28-by-28 color images. Specify that the software flips the images from left to right at training time with a probability of 0.5.

inputlayer = imageInputLayer(\[28 28 3\],'DataAugmentation','randfliplr');

inputlayer = 

 

  ImageInputLayer with properties:

 

                Name: ''

           InputSize: \[28 28 3\]

    DataAugmentation: 'randfliplr'

       Normalization: 'zerocenter'

Display the input size.

inputlayer.InputSize

ans =

 

    28    28     3

## 9.4.2 Convolution2DLayer class

**Description**

A convolutional layer class containing filter size, number of channels, layer name, weights and bias data.

**Construction**

convlayer = convolutional2dLayer([filterSize](http://www.mathworks.com/help/nnet/ref/convolution2dlayer-class.html#inputarg_filterSize),[numFilters](http://www.mathworks.com/help/nnet/ref/convolution2dlayer-class.html#inputarg_numFilters)) returns a layer for 2-D convolution.

convlayer = convolutional2dLayer([filterSize](http://www.mathworks.com/help/nnet/ref/convolution2dlayer-class.html#inputarg_filterSize),[numFilters](http://www.mathworks.com/help/nnet/ref/convolution2dlayer-class.html#inputarg_numFilters),Name,Value) returns the convolutional layer, with additional options specified by one or more Name,Valuepair arguments.

For more details, see [convolution2dLayer](http://www.mathworks.com/help/nnet/ref/convolution2dlayer.html) function reference page.

**Input Arguments**

**filterSize — Height and width of filters integer value | vector of two integer values**

**numFilters — Number of filters integer value**

**Properties**

**Stride — Step size for traversing input \[1 1\] (default) | vector of two scalar values**

**Padding — Size of zero padding applied to borders of input \[0 0\] (default) | vector of two scalar values**

**NumChannels — Number of channels for each filter 'auto' (default) | integer value**

**Weights — The layer weights 4-D array**

**Bias — The layer biases 3-D array**

**WeightLearnRateFactor — Learning rate factor for weights scalar value**

**WeightL2Factor — L2 regularization factor for weights scalar value**

**BiasLearnRateFactor — Learning rate factor for biases scalar value**

**BiasL2Factor — L2 regularization factor for biases scalar value**

**Name — Layer name '' (default) | character vector**

**Examples Create Convolutional Layer**

Create a convolutional layer with 96 filters that have a height and width of 11, and use a stride (step size) of 4 in the horizontal and vertical directions.

convlayer = convolution2dLayer(11,96,'Stride',4)

convlayer = 

 

  Convolution2DLayer with properties:

 

                     Name: ''

               FilterSize: \[11 11\]

              NumChannels: 'auto'

               NumFilters: 96

                   Stride: \[4 4\]

                  Padding: \[0 0\]

                  Weights: \[\]

                     Bias: \[\]

    WeightLearnRateFactor: 1

           WeightL2Factor: 1

      BiasLearnRateFactor: 1

             BiasL2Factor: 0

You can display any of the properties separately by indexing into the object. For example, display the filter size.

convlayer.FilterSize

ans =

 

    11    11

## 9.4.3 ReLULayer class

**Description**

A rectified linear unit (ReLU) layer class that contains the name of the layer. A ReLU layer performs a threshold operation, where any input value less than zero is set to zero, i.e.

**![](images/00126.jpeg)**

**Construction**

layer = relu() returns a ReLU layer.

layer = reluLayer(Name,Value) returns a ReLU layer, with the additional option specified by the Name,Value pair argument.

**Properties**

**Name — Layer name '' (default) | character vector**

 

Layer name, stored as a character vector. If Name is set to '', then the software automatically assigns a name at training time.

**Data Types: **char

**Examples: Create ReLU Layer with Specified Name**

Create a rectified linear unit layer with the name relu1.

 

layer = reluLayer('Name','relu1');

## 9.4.4 CrossChannelNormalizationLayer class

**Description**

Channel-wise local response normalization layer class that contains the size of the channel window, the hyperparameters for normalization, and the name of the layer.

**Construction**

localnormlayer = crossChannelNormalizationLayer([windowChannelSize](http://www.mathworks.com/help/nnet/ref/crosschannelnormalizationlayer-class.html#inputarg_windowChannelSize)) returns a [local response normalization](http://www.mathworks.com/help/nnet/ref/crosschannelnormalizationlayer-class.html#bu62ue3) layer, which carries out channel-wise normalization [\[1\]](http://www.mathworks.com/help/nnet/ref/crosschannelnormalizationlayer.html#bu6xy50).

localnormlayer = crossChannelNormalizationLayer([windowChannelSize](http://www.mathworks.com/help/nnet/ref/crosschannelnormalizationlayer-class.html#inputarg_windowChannelSize),Name,Value) returns a local response normalization layer, with additional options specified by one or more Name,Value pair arguments.

For more details on the name-value pair arguments, see [crossChannelNormalizationLayer](http://www.mathworks.com/help/nnet/ref/crosschannelnormalizationlayer.html).

**Input Arguments**

**windowChannelSize — The size of the channel window  
positive integer**

**Properties**

**windowChannelSize — The size of the channel window positive integer**

**Alpha — *α* hyperparameter in the normalization scalar value**

**Beta — *β* hyperparameter in the normalization 0.75 (default) | scalar value**

**K — *K* hyperparameter in the normalization 2 (default) | scalar value**

**Name — Layer name '' (default) | character vector**

**Examples: Create Local Response Normalization Layer**

Create a local response normalization layer for channel-wise normalization, where a window of 5 channels will be used to normalize each element, and the additive constant for the normalizer is 1.

localnormlayer = crossChannelNormalizationLayer(5,'K',1);

localnormlayer = 

 

  CrossChannelNormalizationLayer with properties:

 

    WindowChannelSize: 5

                Alpha: 1.0000e-04

                 Beta: 0.7500

                    K: 1

                 Name: ''

## 9.4.5 AveragePooling2DLayer class

**Description**

Average pooling layer class containing the pool size, the stride size, padding, and the name of the layer. An average pooling layer performs down-sampling by dividing the input into rectangular pooling regions and computing the average of each region. It returns the averages for the pooling regions. The size of the pooling regions is determined by the poolSize argument to the [averagePooling2dLayer](http://www.mathworks.com/help/nnet/ref/averagepooling2dlayer.html) function.

**Construction**

avgpoollayer \= averagePooling2dLayer([poolSize](http://www.mathworks.com/help/nnet/ref/averagepooling2dlayer-class.html#inputarg_poolSize)) creates a layer that performs average pooling. poolSize specifies the dimensions of the rectangular region.

avgpoollayer \= averagePooling2dLayer([poolSize](http://www.mathworks.com/help/nnet/ref/averagepooling2dlayer-class.html#inputarg_poolSize), Name,Value) creates the average pooling layer, with additional options specified by one or more Name,Value pair arguments.

For more details, see [averagePooling2dLayer](http://www.mathworks.com/help/nnet/ref/averagepooling2dlayer.html).

**Input Arguments**

**poolSize — Height and width of pooling región scalar value | vector of two scalar values**

**Properties**

**PoolSize — Height and width of pooling región scalar | vector of two scalar values**

**Stride — Step size for traversing input \[1 1\] (default) | vector of two scalar values**

**Padding — Size of zero padding applied to borders of input \[0 0\] (default) | vector of two scalar values**

**Name — Layer name '' (default) | character vector**

**Examples: **

**Average Pooling Layer with Non-Overlapping Pooling Regions**

Create an average pooling layer with non-overlapping pooling regions. Set the layer to down-sample by a factor of 2.

avgpoollayer = averagePooling2dLayer(2,'Stride',2)

avgpoollayer = 

 

  AveragePooling2DLayer with properties:

 

    PoolSize: \[2 2\]

      Stride: \[2 2\]

     Padding: \[0 0\]

        Name: ''

The height and width of the rectangular region (pool size) are both 2. This layer creates pooling regions of size \[2 2\] and takes the average of the four elements in each region. Because the step size for traversing the images vertically and horizontally (stride) is also \[2 2\] the pooling regions do not overlap.

**Average Pooling Layer with Overlapping Pooling Regions**

Create an average pooling layer with overlapping pooling regions. Add padding for the top and bottom of the input.

avgpoollayer = averagePooling2dLayer(\[3 2\],'Stride',2,...

    'Padding',\[1 0\],'Name','avg1')

avgpoollayer = 

 

  AveragePooling2DLayer with properties:

 

    PoolSize: \[3 2\]

      Stride: \[2 2\]

     Padding: \[1 0\]

        Name: 'avg1'

The height and width of the rectangular region (pool size) are 3 and 2. This layer creates pooling regions of size \[3 2\] and takes the average of the six elements in each region. Because the step size for stride) is \[2 2\] the pooling regions overlap.

A value of 1 for the Padding name-value pair indicates that averagepooling2dlayer also adds a row of zeros to the top and bottom of the input data. 0 indicates that no padding is added to the right and left of the input data.

You can display any of the properties by using dot notation. Display the name of the layer.

avgpoollayer.Name 

ans =

 

avg1

## 9.4.6 MaxPooling2DLayer class

**Description**

Max pooling layer class containing the pool size, the stride size, padding, and the name of the layer. A max pooling layer performs down-sampling by dividing the input into rectangular pooling regions, and computing the maximum of each region. The size of the pooling regions is determined by the poolSize argument to the maxPooling2dLayerfunction.

**Construction**

maxpoollayer \= maxPooling2dLayer([poolSize](http://www.mathworks.com/help/nnet/ref/maxpooling2dlayer-class.html#inputarg_poolSize)) returns a layer that performs max pooling, which is dividing the input into rectangular regions and returning the maximum of each region. poolSize specifies the dimensions of a pooling region.

maxpoollayer \= maxPooling2dLayer([poolSize](http://www.mathworks.com/help/nnet/ref/maxpooling2dlayer-class.html#inputarg_poolSize),Name,Value) returns the max pooling layer, with additional options specified by one or more Name,Value pair arguments.

For more details on the name-value pair arguments, see [maxPooling2dLayer](http://www.mathworks.com/help/nnet/ref/maxpooling2dlayer.html).

**Input Arguments**

**poolSize — Height and width of pooling región scalar value | vector of two scalar values**

**Properties**

**PoolSize — Height and width of pooling región scalar | vector of two scalar values**

**Stride — Step size for traversing input \[1 1\] (default) | vector of two scalar values**

**Padding — Size of the padding applied to the borders of the input \[0,0\] (default) | vector of two scalar values**

**Name — Layer name '' (default) | character vector**

**Examples:**

**Max Pooling Layer with Non-Overlapping Pooling Regions**

 

Create a maxpooling layer with non-overlapping pooling regions, which down-samples by a factor of 2.

maxpoollayer = maxPooling2dLayer(2,'Stride',2);

maxpoollayer = 

 

  MaxPooling2DLayer with properties:

 

    PoolSize: \[2 2\]

      Stride: \[2 2\]

     Padding: \[0 0\]

        Name: ''

The height and width of the rectangular region (pool size) are both 2. This layer creates pooling regions of size \[2 2\] and returns the maximum of the four elements in each region. Because the step size for traversing the images vertically and horizontally (stride) is also \[2 2\] the pooling regions do not overlap.

**Max Pooling Layer with Overlapping Pooling Regions**

 

Create a max pooling layer with overlapping pooling regions. Also add padding for the top and bottom of the input.

maxpoollayer = maxPooling2dLayer(\[3 2\],'Stride',2,...

   'Padding',\[1 0\],'Name','max1');

maxpoollayer = 

 

  MaxPooling2DLayer with properties:

 

    PoolSize: \[3 2\]

      Stride: \[2 2\]

     Padding: \[1 0\]

        Name: 'max1'

The height and width of the rectangular region (pool size) are 3 and 2. This layer creates pooling regions of size \[3 2\] and returns the maximum of the six elements in each region. Because the step size for traversing the images vertically and horizontally (stride) is \[2 2\] the pooling regions overlap.

1 in the value for the Padding name-value pair indicates that software also adds padding to the top and bottom of the input data. 0 indicates that no padding is added to the right and left of the input data.

You can display any of the properties by indexing into the object. Display the name of the layer.

maxpoollayer.Name 

ans =

 

max1

## 9.4.7 FullyConnectedLayer class

**Description**

A fully connected layer class containing input and output size, layer name, and weights and bias data.

**Construction**

fullconnectlayer = fullyConnectedLayer([outputSize](http://www.mathworks.com/help/nnet/ref/fullyconnectedlayer-class.html#inputarg_outputSize)) returns a fully connected layer, in which the software multiplies the input by a matrix and then adds a bias vector.

fullconnectlayer = fullyConnectedLayer([outputSize](http://www.mathworks.com/help/nnet/ref/fullyconnectedlayer-class.html#inputarg_outputSize),Name,Value) returns the fully connected layer, with additional options specified by one or more Name,Value pair arguments.

For more details on the name-value pair arguments, see [fullyConnectedLayer](http://www.mathworks.com/help/nnet/ref/fullyconnectedlayer.html).

**Input Arguments**

**outputSize — Size of output for fully connected layer integer value**

**Properties**

**InputSize — Layer input size a positive integer | 'auto'**

**OutputSize — Layer output size a positive integer**

**Weights — Layer weights OutputSize\-by-InputSize matrix**

**Bias — Layer biases OutputSize\-by-1 matrix**

**WeightLearnRateFactor — Learning rate factor for weights scalar value**

**WeightL2Factor — L2 regularization factor for weights scalar value**

**BiasLearnRateFactor — Learning rate factor for biases scalar value**

**BiasL2Factor — L2 regularization factor for biases scalar value**

**Name — Layer name '' (default) | character vector**

**Examples: Create Fully Connected Layer**

Create a fully connected layer with an output size of 10.

fullclayer = fullyConnectedLayer(10)

fullclayer = 

 

  FullyConnectedLayer with properties:

 

                  Weights: \[\]

                     Bias: \[\]

    WeightLearnRateFactor: 1

           WeightL2Factor: 1

      BiasLearnRateFactor: 1

             BiasL2Factor: 0

                InputSize: 'auto'

               OutputSize: 10

                     Name: ''

The software determines the input size and initializes the weights and bias at training time.

## 9.4.8 DropoutLayer class

**Description**

A dropout layer class that contains the probability for dropping input elements and the name of the layer. Dropout layer is used only during training.

**Construction**

droplayer = dropoutLayer() returns a dropout layer, that randomly sets input elements to zero with a probability of 0.5. Dropout might help prevent overfitting.

droplayer = dropoutLayer([probability](http://www.mathworks.com/help/nnet/ref/dropoutlayer-class.html#inputarg_probability)) returns a dropout layer, that randomly sets input elements to zero with a probability specified by the probability argument.

droplayer = dropoutLayer(**\_\_\_**, Name,Value) returns the dropout layer, with the additional option specified by the Name,Value pair argument.

**Input Arguments**

**probability — Probability for dropping out input elements 0.5 (default) | a scalar value in the range 0 to 1**

**Properties**

**Probability — Probability for dropping input elements with a scalar value**

**Name — Layer name '' (default) | character vector**

**Definitions: Dropout Layer**

A dropout layer randomly sets a layer's input elements to zero with a given probability.

This corresponds to temporarily dropping a randomly chosen unit and all of its connections from the network during training. So, for each new input element, the software randomly selects a subset of neurons, hence forms a different layer architecture. These architectures use common weights, but because the learning does not depend on specific neurons and connections, the dropout layer might help prevent overfitting .

**Examples: Create a Dropout Layer**

Create a dropout layer, which randomly sets about 40% of the input to zero. Name the layer as dropout1.

droplayer = dropoutLayer(0.4,'Name','dropout1')

droplayer = 

 

  DropoutLayer with properties:

 

    Probability: 0.4000

           Name: 'dropout1'

 

## 9.4.9 SoftmaxLayer class

**Description**

A softmax layer, which uses the softmax activation function. For a classification problem with more than 2 classes, the softmax function is:

![](images/00130.jpeg)

![](images/00131.jpeg)

![](images/00132.jpeg)

**Construction**

smlayer = softmaxLayer() returns a softmax layer for classification problems.

smlayer \= softmaxLayer('Name',layername) returns a softmax layer, with the additional option specified by the 'Name',layername name-value pair argument.

**Properties**

**Name — Layer name '' (default) | character vector**

**Example: Create a Softmax Layer with Specified Name**

Create a softmax layer with the name sml1.

smlayer = softmaxLayer('Name','sml1');

## 9.4.10 ClassificationOutputLayer class

**Description**

The classification output layer, containing the name of the loss function that is used for training the network, the size of the output, and the class labels.

 

**Construction**

classoutputlayer = classificationLayer() returns a classification output layer for a neural network.

classoutputlayer = classificationLayer(Name,Value) returns the classification output layer, with additional option specified by the Name,Value pair argument.

**Properties**

**OutputSize — Size of output scalar value**

**LossFunction — Loss function for training 'crossentropyex'**

**ClassNames — Names of clases empty cell array (before training) | cell array of class names (after training)**

**Name — Layer name '' (default) | character vector**

**Examples: Create Classification Output Layer**

Create a classification output layer with the name 'coutput'.

coutputlayer = classificationLayer('Name','coutput')

coutputlayer = 

 

  ClassificationOutputLayer with properties:

 

      OutputSize: 'auto'

    LossFunction: 'crossentropyex'

      ClassNames: {}

            Name: 'coutput'

**Definitions: Cross Entropy Function for k Mutually Exclusive Classes**

For multi-class classification problems the software assigns each input to one of the *k* mutually exclusive classes. The loss (error) function for this case is the cross entropy function for a 1-of-*k* coding scheme :

**![](images/00133.jpeg)**

**![](images/00134.jpeg)**

**![](images/00135.jpeg)**

**![](images/00136.jpeg)**

The output unit activation function is the softmax function:

 

**![](images/00137.jpeg)**

 

  

**10Chapter 10**

Image Category Classification Using Deep Learning

# 10.1 Overview

 

A Convolutional Neural Network (CNN) is a powerful machine learning technique from the field of deep learning. CNNs are trained using large collections of diverse images. From these large collections, CNNs can learn rich feature representations for a wide range of images. These feature representations often outperform hand-crafted features such as HOG, LBP, or SURF. An easy way to leverage the power of CNNs, without investing time and effort into training, is to use a pre-trained CNN as a feature extractor.

In this example, images from Caltech 101 are classified into categories using a multiclass linear SVM trained with CNN features extracted from the images. This approach to image category classification follows the standard practice of training an off-the-shelf classifier using features extracted from images. For example, the Image Category Classification Using Bag Of Features example uses SURF features within a bag of features framework to train a multiclass SVM. The difference here is that instead of using image features such as HOG or SURF, features are extracted using a CNN. And, as this example will show, the classifier trained using CNN features provides close to 100% accuracy, which is higher than the accuracy achieved using bag of features and SURF.

Note: This example requires Computer Vision System Toolbox™, Image Processing Toolbox™, Neural Network Toolbox™, Parallel Computing Toolbox™, Statistics and Machine Learning Toolbox™, and a CUDA-capable NVIDIA™ GPU with compute capability 3.0 or higher.

function DeepLearningImageClassificationExample

# 10.2 Check System Requirements

 

A CUDA-capable NVIDIA™ GPU with compute capability 3.0 or higher is highly recommended to run this example. Query the GPU device to check if it can run this example:

% Get GPU device information

deviceInfo = gpuDevice;

 

% Check the GPU compute capability

computeCapability = str2double(deviceInfo.ComputeCapability);

assert(computeCapability > 3.0, ...

    'This example requires a GPU device with compute capability 3.0 or higher.')

# 10.3 Download Image Data

 

The category classifier will be trained on images from [Caltech 101](http://www.vision.caltech.edu/Image_Datasets/Caltech101). Caltech 101 is one of the most widely cited and used image data sets, collected by Fei-Fei Li, Marco Andreetto, and Marc 'Aurelio Ranzato.

% Download the compressed data set from the following location

url = 'http://www.vision.caltech.edu/Image\_Datasets/Caltech101/101\_ObjectCategories.tar.gz';

% Store the output in a temporary folder

outputFolder = fullfile(tempdir, 'caltech101'); % define output folder

Note: Download time of the data depends on your internet connection. The next set of commands use MATLAB to download the data and will block MATLAB. Alternatively, you can use your web browser to first download the dataset to your local disk. To use the file you downloaded from the web, change the 'outputFolder' variable above to the location of the downloaded file.

if ~exist(outputFolder, 'dir') % download only once

    disp('Downloading 126MB Caltech101 data set...');

    untar(url, outputFolder);

end

# 10.4 Load Images

 

Instead of operating on all of Caltech 101, which is time consuming, use three of the categories: airplanes, ferry, and laptop. The image category classifier will be trained to distinguish amongst these six categories.

rootFolder = fullfile(outputFolder, '101\_ObjectCategories');

categories = {'airplanes', 'ferry', 'laptop'};

Create an ImageDatastore to help you manage the data. Because ImageDatastore operates on image file locations, images are not loaded into memory until read, making it efficient for use with large image collections.

imds = imageDatastore(fullfile(rootFolder, categories), 'LabelSource', 'foldernames');

The imds variable now contains the images and the category labels associated with each image. The labels are automatically assigned from the folder names of the image files. Use countEachLabel to summarize the number of images per category.

tbl = countEachLabel(imds)

tbl = 

 

      Label      Count

    \_\_\_\_\_\_\_\_\_    \_\_\_\_\_

 

    airplanes    800  

    ferry         67  

    laptop        81  

 

Because imds above contains an unequal number of images per category, let's first adjust it, so that the number of images in the training set is balanced.

minSetCount = min(tbl{:,2}); % determine the smallest amount of images in a category

 

% Use splitEachLabel method to trim the set.

imds = splitEachLabel(imds, minSetCount, 'randomize');

 

% Notice that each set now has exactly the same number of images.

countEachLabel(imds)

ans = 

 

      Label      Count

    \_\_\_\_\_\_\_\_\_    \_\_\_\_\_

 

    airplanes    67   

    ferry        67   

    laptop       67   

 

Below, you can see example images from three of the categories included in the dataset.

% Find the first instance of an image for each category

airplanes = find(imds.Labels == 'airplanes', 1);

ferry = find(imds.Labels == 'ferry', 1);

laptop = find(imds.Labels == 'laptop', 1);

 

figure

subplot(1,3,1);

imshow(readimage(imds,airplanes))

subplot(1,3,2);

imshow(readimage(imds,ferry))

subplot(1,3,3);

imshow(readimage(imds,laptop))

![](images/00138.jpeg)

# 10.5 Download Pre-trained Convolutional Neural Network (CNN)

 

Now that the images are prepared, you will need to download a pre-trained CNN model for this example. There are several pre-trained networks that have gained popularity. Most of these have been trained on the ImageNet dataset, which has 1000 object categories and 1.2 million training images. "AlexNet" is one such model and can be downloaded from MatConvNet\[2,3\]:

% Location of pre-trained "AlexNet"

cnnURL = 'http://www.vlfeat.org/matconvnet/models/beta16/imagenet-caffe-alex.mat';

% Store CNN model in a temporary folder

cnnMatFile = fullfile(tempdir, 'imagenet-caffe-alex.mat');

Note: Download time of the data depends on your internet connection. The next set of commands use MATLAB to download the data and will block MATLAB. Alternatively, you can use your web browser to first download the dataset to your local disk. To use the file you downloaded from the web, change the 'cnnMatFile' variable above to the location of the downloaded file.

if ~exist(cnnMatFile, 'file') % download only once

    disp('Downloading pre-trained CNN model...');

    websave(cnnMatFile, cnnURL);

end

## 10.5.1 Load Pre-trained AlexNet Network

There are several pre-trained networks that have gained popularity. Most of these have been trained on the ImageNet dataset, which has 1000 object categories and 1.2 million training images. "AlexNet" is one such model and can be loaded using the alexnet function from Neural Network Toolbox. Using alexnet requires that you first install Neural Network Toolbox Model for AlexNet Network.

% Load pre-trained AlexNet

net = alexnet()

net = 

 

  SeriesNetwork with properties:

 

    Layers: \[25×1 nnet.cnn.layer.Layer\]

 

Other popular networks trained on ImageNet include VGG-16 and VGG-19 \[3\], which can be loaded using vgg16 and vgg19 from the Neural Network Toolbox™.

net.Layers defines the architecture of the CNN.

% View the CNN architecture

net.Layers

ans = 

 

  25x1 Layer array with layers:

 

     1   'data'     Image Input                   227x227x3 images with 'zerocenter' normalization

     2   'conv1'    Convolution                   96 11x11x3 convolutions with stride \[4  4\] and padding \[0  0\]

     3   'relu1'    ReLU                          ReLU

     4   'norm1'    Cross Channel Normalization   cross channel normalization with 5 channels per element

     5   'pool1'    Max Pooling                   3x3 max pooling with stride \[2  2\] and padding \[0  0\]

     6   'conv2'    Convolution                   256 5x5x48 convolutions with stride \[1  1\] and padding \[2  2\]

     7   'relu2'    ReLU                          ReLU

     8   'norm2'    Cross Channel Normalization   cross channel normalization with 5 channels per element

     9   'pool2'    Max Pooling                   3x3 max pooling with stride \[2  2\] and padding \[0  0\]

     10   'conv3'    Convolution                   384 3x3x256 convolutions with stride \[1  1\] and padding \[1  1\]

     11   'relu3'    ReLU                          ReLU

     12   'conv4'    Convolution                   384 3x3x192 convolutions with stride \[1  1\] and padding \[1  1\]

     13   'relu4'    ReLU                          ReLU

     14   'conv5'    Convolution                   256 3x3x192 convolutions with stride \[1  1\] and padding \[1  1\]

    15   'relu5'    ReLU                          ReLU

    16   'pool5'    Max Pooling                   3x3 max pooling with stride \[2  2\] and padding \[0  0\]

    17   'fc6'      Fully Connected               4096 fully connected layer

    18   'relu6'    ReLU                          ReLU

    19   'drop6'    Dropout                       50% dropout

    20   'fc7'      Fully Connected               4096 fully connected layer

    21   'relu7'    ReLU                          ReLU

    22   'drop7'    Dropout                       50% dropout

    23   'fc8'      Fully Connected               1000 fully connected layer

    24   'prob'     Softmax                       softmax

    25   'output'   Classification Output         crossentropyex with 'tench', 'goldfish', and 998 other classes

The first layer defines the input dimensions. Each CNN has a different input size requirements. The one used in this example requires image input that is 227-by-227-by-3.

% Inspect the first layer

net.Layers(1)

ans = 

 

  ImageInputLayer with properties:

 

                Name: 'data'

           InputSize: \[227 227 3\]

 

   Hyperparameters

    DataAugmentation: 'none'

       Normalization: 'zerocenter'

 

The intermediate layers make up the bulk of the CNN. These are a series of convolutional layers, interspersed with rectified linear units (ReLU) and max-pooling layers \[2\]. Following the these layers are 3 fully-connected layers.

The final layer is the classification layer and its properties depend on the classification task. In this example, the CNN model that was loaded was trained to solve a 1000-way classification problem. Thus the classification layer has 1000 classes from the ImageNet dataset.

% Inspect the last layer

net.Layers(end)

 

% Number of class names for ImageNet classification task

numel(net.Layers(end).ClassNames)

ans = 

 

  ClassificationOutputLayer with properties:

 

            Name: 'output'

      ClassNames: {1×1000 cell}

      OutputSize: 1000

 

   Hyperparameters

    LossFunction: 'crossentropyex'

 

 

ans =

 

        1000

 

Note that the CNN model is not going to be used for the original classification task. It is going to be re-purposed to solve a different classification task on the Caltech 101 dataset.

# 10.6 Load Pre-trained CNN

 

The CNN model is saved in MatConvNet's format. Load the MatConvNet network data into convnet, a SeriesNetworkobject from Neural Network Toolbox™, using the helper function helperImportMatConvNet. A SeriesNetwork object can be used to inspect the network architecture, classify new data, and extract network activations from specific layers.

% Load MatConvNet network into a SeriesNetwork

convnet = helperImportMatConvNet(cnnMatFile)

convnet = 

 

  SeriesNetwork with properties:

 

    Layers: \[23×1 nnet.cnn.layer.Layer\]

 

convnet.Layers defines the architecture of the CNN.

% View the CNN architecture

convnet.Layers

ans = 

 

  23x1 Layer array with layers:

 

     1   'input'                 Image Input                   227x227x3 images with 'zerocenter' normalization

     2   'conv1'                 Convolution                   96 11x11x3 convolutions with stride \[4  4\] and padding \[0  0\]

     3   'relu1'                 ReLU                          ReLU

     4   'norm1'                 Cross Channel Normalization   cross channel normalization with 5 channels per element

     5   'pool1'                 Max Pooling                   3x3 max pooling with stride \[2  2\] and padding \[0  0\]

     6   'conv2'                 Convolution                   256 5x5x48 convolutions with stride \[1  1\] and padding \[2  2\]

     7   'relu2'                 ReLU                          ReLU

     8   'norm2'                 Cross Channel Normalization   cross channel normalization with 5 channels per element

     9   'pool2'                 Max Pooling                   3x3 max pooling with stride \[2  2\] and padding \[0  0\]

    10   'conv3'                 Convolution                   384 3x3x256 convolutions with stride \[1  1\] and padding \[1  1\]

    11   'relu3'                 ReLU                          ReLU

    12   'conv4'                 Convolution                   384 3x3x192 convolutions with stride \[1  1\] and padding \[1  1\]

    13   'relu4'                 ReLU                          ReLU

    14   'conv5'                 Convolution                   256 3x3x192 convolutions with stride \[1  1\] and padding \[1  1\]

    15   'relu5'                 ReLU                          ReLU

    16   'pool5'                 Max Pooling                   3x3 max pooling with stride \[2  2\] and padding \[0  0\]

    17   'fc6'                   Fully Connected               4096 fully connected layer

    18   'relu6'                 ReLU                          ReLU

    19   'fc7'                   Fully Connected               4096 fully connected layer

    20   'relu7'                 ReLU                          ReLU

    21   'fc8'                   Fully Connected               1000 fully connected layer

    22   'prob'                  Softmax                       softmax

    23   'classificationLayer'   Classification Output         cross-entropy with 'n01440764', 'n01443537', and 998 other classes

The first layer defines the input dimensions. Each CNN has a different input size requirements. The one used in this example requires image input that is 227-by-227-by-3.

% Inspect the first layer

convnet.Layers(1)

ans = 

 

  ImageInputLayer with properties:

 

                Name: 'input'

           InputSize: \[227 227 3\]

 

   Hyperparameters

    DataAugmentation: 'none'

       Normalization: 'zerocenter'

 

The intermediate layers make up the bulk of the CNN. These are a series of convolutional layers, interspersed with rectified linear units (ReLU) and max-pooling layers \[2\]. Following the these layers are 3 fully-connected layers.

The final layer is the classification layer and its properties depend on the classification task. In this example, the CNN model that was loaded was trained to solve a 1000-way classification problem. Thus the classification layer has 1000 classes from the ImageNet dataset.

% Inspect the last layer

convnet.Layers(end)

 

% Number of class names for ImageNet classification task

numel(convnet.Layers(end).ClassNames)

ans = 

 

  ClassificationOutputLayer with properties:

 

            Name: 'classificationLayer'

      ClassNames: {1000×1 cell}

      OutputSize: 1000

 

   Hyperparameters

    LossFunction: 'crossentropyex'

 

 

ans =

 

        1000

 

Note that the CNN model is not going to be used for the original classification task. It is going to be re-purposed to solve a different classification task on the Caltech 101 dataset.

 

# 10.7 Pre-process Images For CNN

 

As mentioned above, convnet can only process RGB images that are 227-by-227. To avoid re-saving all the images in Caltech 101 to this format, setup the imds read function, imds.ReadFcn, to pre-process images on-the-fly. The imds.ReadFcn is called every time an image is read from the ImageDatastore.

% Set the ImageDatastore ReadFcn

imds.ReadFcn = @(filename)readAndPreprocessImage(filename);

Note that other CNN models will have different input size constraints, and may require other pre-processing steps.

    function Iout = readAndPreprocessImage(filename)

 

        I = imread(filename);

 

        % Some images may be grayscale. Replicate the image 3 times to

        % create an RGB image.

        if ismatrix(I)

            I = cat(3,I,I,I);

        end

 

        % Resize the image as required for the CNN.

        Iout = imresize(I, \[227 227\]);

 

        % Note that the aspect ratio is not preserved. In Caltech 101, the

        % object of interest is centered in the image and occupies a

        % majority of the image scene. Therefore, preserving the aspect

        % ratio is not critical. However, for other data sets, it may prove

        % beneficial to preserve the aspect ratio of the original image

        % when resizing.

    end

# 10.8 Prepare Training and Test Image Sets

 

Split the sets into training and validation data. Pick 30% of images from each set for the training data and the remainder, 70%, for the validation data. Randomize the split to avoid biasing the results. The training and test sets will be processed by the CNN model.

\[trainingSet, testSet\] = splitEachLabel(imds, 0.3, 'randomize');

# 10.9 Extract Training Features Using CNN

 

Each layer of a CNN produces a response, or activation, to an input image. However, there are only a few layers within a CNN that are suitable for image feature extraction. The layers at the beginning of the network capture basic image features, such as edges and blobs. To see this, visualize the network filter weights from the first convolutional layer. This can help build up an intuition as to why the features extracted from CNNs work so well for image recognition tasks. Note that visualizing deeper layer weights is beyond the scope of this example. You can read more about that in the work of Zeiler and Fergus \[4\].

% Get the network weights for the second convolutional layer

w1 = convnet.Layers(2).Weights;

 

% Scale and resize the weights for visualization

w1 = mat2gray(w1);

w1 = imresize(w1,5);

 

% Display a montage of network weights. There are 96 individual sets of

% weights in the first layer.

figure

montage(w1)

title('First convolutional layer weights')

![Descripción: http://es.mathworks.com/help/examples/vision\_product/DeepLearningImageClassificationExample\_02.png](images/00139.jpeg)

Notice how the first layer of the network has learned filters for capturing blob and edge features. These "primitive" features are then processed by deeper network layers, which combine the early features to form higher level image features. These higher level features are better suited for recognition tasks because they combine all the primitive features into a richer image representation \[5\].

You can easily extract features from one of the deeper layers using the activations method. Selecting which of the deep layers to choose is a design choice, but typically starting with the layer right before the classification layer is a good place to start. In convnet, the this layer is named 'fc7'. Let's extract training features using that layer.

featureLayer = 'fc7';

trainingFeatures = activations(convnet, trainingSet, featureLayer, ...

    'MiniBatchSize', 32, 'OutputAs', 'columns');

Note that the activations function automatically uses a GPU for processing if one is available, otherwise, a CPU is used. Because of the number of layers in AlexNet, using a GPU is highly recommended. Using a the CPU to run the network will greatly increase the time it takes to extract features.

In the code above, the 'MiniBatchSize' is set 32 to ensure that the CNN and image data fit into GPU memory. You may need to lower the 'MiniBatchSize' if your GPU runs out of memory. Also, the activations output is arranged as columns. This helps speed-up the multiclass linear SVM training that follows.

# 10.10 Train A Multiclass SVM Classifier Using CNN Features

 

Next, use the CNN image features to train a multiclass SVM classifier. A fast Stochastic Gradient Descent solver is used for training by setting the fitcecoc function's 'Learners' parameter to 'Linear'. This helps speed-up the training when working with high-dimensional CNN feature vectors, which each have a length of 4096.

% Get training labels from the trainingSet

trainingLabels = trainingSet.Labels;

 

% Train multiclass SVM classifier using a fast linear solver, and set

% 'ObservationsIn' to 'columns' to match the arrangement used for training

% features.

classifier = fitcecoc(trainingFeatures, trainingLabels, ...

    'Learners', 'Linear', 'Coding', 'onevsall', 'ObservationsIn', 'columns');

# 10.11 Evaluate Classifier

 

Repeat the procedure used earlier to extract image features from testSet. The test features can then be passed to the classifier to measure the accuracy of the trained classifier.

% Extract test features using the CNN

testFeatures = activations(convnet, testSet, featureLayer, 'MiniBatchSize',32);

 

% Pass CNN image features to trained classifier

predictedLabels = predict(classifier, testFeatures);

 

% Get the known labels

testLabels = testSet.Labels;

 

% Tabulate the results using a confusion matrix.

confMat = confusionmat(testLabels, predictedLabels);

 

% Convert confusion matrix into percentage form

confMat = bsxfun(@rdivide,confMat,sum(confMat,2))

confMat =

 

     1     0     0

     0     1     0

     0     0     1

 

% Display the mean accuracy

mean(diag(confMat))

ans =

 

     1

 

# 10.12 Try the Newly Trained Classifier on Test Images

 

You can now apply the newly trained classifier to categorize new images.

newImage = fullfile(rootFolder, 'airplanes', 'image\_0690.jpg');

 

% Pre-process the images as required for the CNN

img = readAndPreprocessImage(newImage);

 

% Extract image features using the CNN

imageFeatures = activations(convnet, img, featureLayer);

% Make a prediction using the classifier

label = predict(classifier, imageFeatures)

label = 

 

     airplanes 

 

# 10.13 References

 

\[1\] Deng, Jia, et al. "Imagenet: A large-scale hierarchical image database." Computer Vision and Pattern Recognition, 2009. CVPR 2009. IEEE Conference on. IEEE, 2009.

\[2\] Krizhevsky, Alex, Ilya Sutskever, and Geoffrey E. Hinton. "Imagenet classification with deep convolutional neural networks." Advances in neural information processing systems. 2012.

\[3\] Vedaldi, Andrea, and Karel Lenc. "MatConvNet-convolutional neural networks for MATLAB." arXiv preprint arXiv:1412.4564 (2014).

\[4\] Zeiler, Matthew D., and Rob Fergus. "Visualizing and understanding convolutional networks." Computer Vision-ECCV 2014. Springer International Publishing, 2014. 818-833.

\[5\] Donahue, Jeff, et al. "Decaf: A deep convolutional activation feature for generic visual recognition." arXiv preprint arXiv:1310.1531 (2013).

 

  

**11Chapter 11**

Transfer Learning Using Convolutional Neural Networks AND PRETRAINED Convolutional Neural Networks

# 11.1 Transfer Learning Using Convolutional Neural Networks

 

Fine-tune a convolutional neural network pretrained on digit images to learn the features of letter images. Transfer learning is considered as the transfer of knowledge from one learned task to a new task in machine learning \[1\]. In the context of neural networks, it is transferring learned features of a pretrained network to a new problem. Training a convolutional neural network from the beginning in each case usually is not effective when there is not sufficient amount of training data. The common practice in deep learning for such cases is to use a network that is trained on a large data set for a new problem. While the initial layers of the pretrained network can be fixed, the last few layers must be fine-tuned to learn the specific features of the new data set. Transfer learning usually results in faster training times than training a new convolutional neural network because you do not need to estimate all the parameters in the new network.

**NOTE:** Training a convolutional neural network requires Parallel Computing Toolbox™ and a CUDA®-enabled NVIDIA® GPU with compute capability 3.0 or higher.

Load the sample data as an ImageDatastore.

digitDatasetPath = fullfile(matlabroot,'toolbox','nnet','nndemos',...

    'nndatasets','DigitDataset');

digitData = imageDatastore(digitDatasetPath,...

        'IncludeSubfolders',true,'LabelSource','foldernames');

The data store contains 10000 synthetic images of digits 0–9. The images are generated by applying random transformations to digit images created using different fonts. Each digit image is 28-by-28 pixels.

Display some of the images in the datastore.

for i = 1:20

    subplot(4,5,i);

    imshow(digitData.Files{i});

end

![Descripción: http://es.mathworks.com/help/examples/nnet/TransferLearningUsingConvolutionalNeuralNetworksExample\_01.png](images/00140.jpeg)

Check the number of images in each digit category.

digitData.countEachLabel

ans = 

 

    Label    Count

    \_\_\_\_\_    \_\_\_\_\_

 

    0         988 

    1        1026 

    2        1003 

    3         993 

    4         991 

    5        1017 

    6         992 

    7         999 

    8        1003 

    9         988 

 

The data contains an unequal number of images per category.

To balance the number of images for each digit in the training set, first find the minimum number of images in a category.

minSetCount = min(digitData.countEachLabel{:,2})

minSetCount =

 

   988

 

Divide the dataset so that each category in the training set has 494 images and the testing set has the remaining images from each label.

trainingNumFiles = round(minSetCount/2);

rng(1) % For reproducibility

\[trainDigitData,testDigitData\] = splitEachLabel(digitData,...

                                  trainingNumFiles,'randomize');

splitEachLabel splits the image files in digitData into two new datastores, trainDigitData and testDigitData.

Create the layers for the convolutional neural network.

layers = \[imageInputLayer(\[28 28 1\])

         convolution2dLayer(5,20)

         reluLayer()

         maxPooling2dLayer(2,'Stride',2)

         fullyConnectedLayer(10)

         softmaxLayer()

         classificationLayer()\];

Create the training options. Set the maximum number of epochs at 20, and start the training with an initial learning rate of 0.001.

options = trainingOptions('sgdm','MaxEpochs',20,...

        'InitialLearnRate',0.001);

Train the network using the training set and the options you defined in the previous step.

convnet = trainNetwork(trainDigitData,layers,options);

|=========================================================================================|

|     Epoch    |   Iteration  | Time Elapsed |  Mini-batch  |  Mini-batch  | Base Learning|

|              |              |  (seconds)   |     Loss     |   Accuracy   |     Rate     |

|=========================================================================================|

|            2 |           50 |         0.71 |       0.2233 |       92.97% |     0.001000 |

|            3 |          100 |         1.37 |       0.0182 |       99.22% |     0.001000 |

|            4 |          150 |         2.02 |       0.0395 |       99.22% |     0.001000 |

|            6 |          200 |         2.70 |       0.0105 |       99.22% |     0.001000 |

|            7 |          250 |         3.35 |       0.0026 |      100.00% |     0.001000 |

|            8 |          300 |         4.00 |       0.0004 |      100.00% |     0.001000 |

|           10 |          350 |         4.67 |       0.0002 |      100.00% |     0.001000 |

|           11 |          400 |         5.32 |       0.0001 |      100.00% |     0.001000 |

|           12 |          450 |         5.95 |       0.0001 |      100.00% |     0.001000 |

|           14 |          500 |         6.60 |       0.0002 |      100.00% |     0.001000 |

|           15 |          550 |         7.23 |       0.0001 |      100.00% |     0.001000 |

|           16 |          600 |         7.87 |       0.0001 |      100.00% |     0.001000 |

|           18 |          650 |         8.52 |       0.0001 |      100.00% |     0.001000 |

|           19 |          700 |         9.15 |       0.0001 |      100.00% |     0.001000 |

|           20 |          750 |         9.79 |       0.0000 |      100.00% |     0.001000 |

|=========================================================================================|

Test the network using the testing set and compute the accuracy.

YTest = classify(convnet,testDigitData);

TTest = testDigitData.Labels;

accuracy = sum(YTest == TTest)/numel(YTest)

accuracy =

 

    0.9976

 

Accuracy is the ratio of the number of true labels in the test data matching the classifications from classify, to the number of images in the test data. In this case 99.78% of the digit estimations match the true digit values in the test set.

Now, suppose you would like to use the trained network net to predict classes on a new set of data. Load the letters training data.

load lettersTrainSet.mat

XTrain contains 1500 28-by-28 grayscale images of the letters A, B, and C in a 4-D array. TTrain contains the categorical array of the letter labels.

Display some of the letter images.

figure;

for j = 1:20

    subplot(4,5,j);

    selectImage = datasample(XTrain,1,4);

    imshow(selectImage,\[\]);

end

![Descripción: http://es.mathworks.com/help/examples/nnet/TransferLearningUsingConvolutionalNeuralNetworksExample\_02.png](images/00141.jpeg)

The pixel values in XTrain are in the range \[0 1\]. The digit data used in training the network net were in \[0 255\]; scale the letters data between \[0 255\].

XTrain = XTrain\*255;

The last three layers of the trained network net are tuned for the digit dataset, which has 10 classes. The properties of these layers depend on the classification task. Display the fully connected layer (fullyConnectedLayer).

convnet.Layers(end-2)

ans = 

 

  FullyConnectedLayer with properties:

 

          Name: 'fc'

 

   Hyperparameters

     InputSize: 2880

    OutputSize: 10

 

   Learnable Parameters

       Weights: \[10×2880 single\]

          Bias: \[10×1 single\]

 

Use properties method to see a list of all properties.

Display the last layer (classificationLayer).

convnet.Layers(end)

ans = 

 

  ClassificationOutputLayer with properties:

 

            Name: 'classoutput'

      ClassNames: {10×1 cell}

      OutputSize: 10

 

   Hyperparameters

    LossFunction: 'crossentropyex'

 

These three layers must be fine-tuned for the new classification problem. Extract all the layers but the last three from the trained network, net.

layersTransfer = convnet.Layers(1:end-3);

The letters data set has three classes. Add a new fully connected layer for three classes, and increase the learning rate for this layer.

layersTransfer(end+1) = fullyConnectedLayer(3,...

              'WeightLearnRateFactor',10,...

                  'BiasLearnRateFactor',20);

WeightLearnRateFactor and BiasLearnRateFactor are multipliers of the global learning rate for the fully connected layer.

Add a softmax layer and a classification output layer.

layersTransfer(end+1) = softmaxLayer();

layersTransfer(end+1) = classificationLayer();

Create the options for transfer learning. You do not have to train for many epochs (MaxEpochs can be lower than before). Set the InitialLearnRate at a lower rate than used for training net to improve convergence by taking smaller steps.

optionsTransfer = trainingOptions('sgdm',...

         'MaxEpochs',5,...

         'InitialLearnRate',0.000005,...

         'Verbose',true);

Perform transfer learning.

convnetTransfer = trainNetwork(XTrain,TTrain,...

                    layersTransfer,optionsTransfer);

 

 

|=========================================================================================|

|     Epoch    |   Iteration  | Time Elapsed |  Mini-batch  |  Mini-batch  | Base Learning|

|              |              |  (seconds)   |     Loss     |   Accuracy   |     Rate     |

|=========================================================================================|

|            5 |           50 |         0.43 |       0.0011 |      100.00% |     0.000005 |

|=========================================================================================|

Load the letters test data. Similar to the letters training data, scale the testing data between \[0 255\], because the training data were between that range.

load lettersTestSet.mat

XTest = XTest\*255;

Test the accuracy.

YTest = classify(convnetTransfer,XTest);

accuracy = sum(YTest == TTest)/numel(TTest)

accuracy =

 

    0.9587

 

# 11.2 Pretrained Convolutional Neural Network

 

Training Convolutional Neural Networks (ConvNets) can be difficult and time consuming. In some cases, it makes sense to start with a ConvNet already trained on a large data set and then adapt it to the current problem. You can use a previously trained network for two purposes:

·        Feature extraction — Use the ConvNet to extract features from data (images) and then use those features to train a different classifier, e.g., a support vector machine (SVM).

·        Transfer learning — Take a network trained on a large dataset and retrain the last few layers on a smaller data set.

The Caffe version of AlexNet (*https://github.com/BVLC/caffe/tree/master/ models/ bvlc\_alexnet*), is available to download and use for your problems. The network is trained on a subset of the images from ImageNet database, which are used in ImageNet Large-Scale Visual Recognition Challenge (ILSVRC). There are 1000 categories and about 1000 training images in each category.

You can install the trained network from the Add-Ons gallery. Select **Get Add-Ons** from the **Add-Ons** drop-down menu of the MATLAB^® desktop. The add-on files are in the "MathWorks Features" section. Choose Neural Network Toolbox Model for AlexNet Network..

After you download the support package, you can access it by typing alexnet in the command line.

net = alexnet

net = 

 

  SeriesNetwork with properties:

 

    Layers: \[25×1 nnet.cnn.layer.Layer\]

The trained network is a SeriesNetwork object. You can see the details of the architecture by using dot notation.

net.Layers

ans = 

 

  25x1 Layer array with layers:

 

     1   'data'     Image Input                   227x227x3 images with 'zerocenter' normalization

     2   'conv1'    Convolution                   96 11x11x3 convolutions with stride \[4  4\] and padding \[0  0\]

     3   'relu1'    ReLU                          ReLU

     4   'norm1'    Cross Channel Normalization   cross channel normalization with 5 channels per element

     5   'pool1'    Max Pooling                   3x3 max pooling with stride \[2  2\] and padding \[0  0\]

     6   'conv2'    Convolution                   256 5x5x48 convolutions with stride \[1  1\] and padding \[2  2\]

     7   'relu2'    ReLU                          ReLU

     8   'norm2'    Cross Channel Normalization   cross channel normalization with 5 channels per element

     9   'pool2'    Max Pooling                   3x3 max pooling with stride \[2  2\] and padding \[0  0\]

    10   'conv3'    Convolution                   384 3x3x256 convolutions with stride \[1  1\] and padding \[1  1\]

    11   'relu3'    ReLU                          ReLU

    12   'conv4'    Convolution                   384 3x3x192 convolutions with stride \[1  1\] and padding \[1  1\]

    13   'relu4'    ReLU                          ReLU

    14   'conv5'    Convolution                   256 3x3x192 convolutions with stride \[1  1\] and padding \[1  1\]

    15   'relu5'    ReLU                          ReLU

    16   'pool5'    Max Pooling                   3x3 max pooling with stride \[2  2\] and padding \[0  0\]

    17   'fc6'      Fully Connected               4096 fully connected layer

    18   'relu6'    ReLU                          ReLU

    19   'drop6'    Dropout                       50% dropout

    20   'fc7'      Fully Connected               4096 fully connected layer

    21   'relu7'    ReLU                          ReLU

    22   'drop7'    Dropout                       50% dropout

    23   'fc8'      Fully Connected               1000 fully connected layer

    24   'prob'     Softmax                       softmax

    25   'output'   Classification Output         cross-entropy with 'tench', 'goldfish', and 998 other classes

Suppose you want to classify an image using this trained network. First, read the image to classify.

I = imread('peppers.png');

This image is of size 384-by-512-by-3. You must adjust it to the size of the images the network was trained on. Extract the input size of the network.

sz = net.Layers(1).InputSize

sz =

 

   227   227     3

Crop image to the input size of the network.

I = I(1:sz(1),1:sz(2),1:sz(3));

Classify (predict the label of ) the image using AlexNet.

label = classify(net, I)

label = 

 

     bell pepper

classify is a method of SeriesNetwork. Show the image and the classification results.

figure

imshow(I)

text(10,20,char(label),'Color','white')

![](images/00142.jpeg)

**References**

\[1\] https://github.com/BVLC/caffe/tree/master/models/bvlc\_alexnet

\[2\] Krizhevsky, A., I. Sutskever, and G. E. Hinton. "ImageNet Classification with Deep Convolutional Neural Networks. " *Advances in Neural Information Processing Systems*. Vol 25, 2012.

\[3\] http://www.image-net.org/

 

 

  

**12Chapter 12**

AUTOENCODERS

# 12.1 Autoencoder class

 

**Description**

 

An Autoencoder object contains an autoencoder network, which consists of an encoder and a decoder. The encoder maps the input to a hidden representation. The decoder attempts to map this representation back to the original input.

**Construction**

 

autoenc = trainAutoencoder([X](http://es.mathworks.com/help/nnet/ref/autoencoder-class.html#inputarg_X)) returns an autoencoder trained using the training data in X.

autoenc = trainAutoencoder([X](http://es.mathworks.com/help/nnet/ref/autoencoder-class.html#inputarg_X),[hiddenSize](http://es.mathworks.com/help/nnet/ref/autoencoder-class.html#inputarg_hiddenSize)) returns an autoencoder with the hidden representation size of hiddenSize.

autoenc = trainAutoencoder(**\_\_\_**,Name,Value) for any of the above input arguments with additional options specified by one or more Name,Value pair arguments.

**Input Arguments**

 

X — training data  
matrix | cell array of image data

 

Hiddensize — size of hidden representation of the autoencoder   
10 (default) | positive integer value

 

**Methods**

 
| [decode](http://es.mathworks.com/help/nnet/ref/autoencoder.decode.html) || Decode encoded data |
| --- | --- |
| [encode](http://es.mathworks.com/help/nnet/ref/autoencoder.encode.html) || Encode input data |
| [generateFunction](http://es.mathworks.com/help/nnet/ref/autoencoder.generatefunction.html) || Generate a MATLAB function to run the autoencoder |
| [generateSimulink](http://es.mathworks.com/help/nnet/ref/autoencoder.generatesimulink.html) || Generate a Simulink model for the autoencoder |
| [network](http://es.mathworks.com/help/nnet/ref/autoencoder.network.html) || Convert Autoencoder object into network object |
| [plotWeights](http://es.mathworks.com/help/nnet/ref/autoencoder.plotweights.html) || Plot a visualization of the weights for the encoder of an autoencoder |
| [predict](http://es.mathworks.com/help/nnet/ref/autoencoder.predict.html) || Reconstruct the inputs using trained autoencoder |
| [stack](http://es.mathworks.com/help/nnet/ref/autoencoder.stack.html) || Stack encoders from several autoencoders together |
| [view](http://es.mathworks.com/help/nnet/ref/autoencoder.view.html) || View autoencoder |

 

# 12.2 Autoencoder FUNCTIONS

 

## 12.2.1 Functions

 

 
| [`trainAutoencoder`](http://es.mathworks.com/help/nnet/ref/trainautoencoder.html) || Train an autoencoder |
| --- | --- |
| [`trainSoftmaxLayer`](http://es.mathworks.com/help/nnet/ref/trainsoftmaxlayer.html) || Train a softmax layer for classification |
| [`decode`](http://es.mathworks.com/help/nnet/ref/autoencoder.decode.html) || Decode encoded data |
| [`encode`](http://es.mathworks.com/help/nnet/ref/autoencoder.encode.html) || Encode input data |
| [`generateFunction`](http://es.mathworks.com/help/nnet/ref/autoencoder.generatefunction.html) || Generate a MATLAB function to run the autoencoder |
| [`generateSimulink`](http://es.mathworks.com/help/nnet/ref/autoencoder.generatesimulink.html) || Generate a Simulink model for the autoencoder |
| [`network`](http://es.mathworks.com/help/nnet/ref/autoencoder.network.html) || Convert Autoencoder object into network object |
| [`plotWeights`](http://es.mathworks.com/help/nnet/ref/autoencoder.plotweights.html) || Plot a visualization of the weights for the encoder of an autoencoder |
| [`predict`](http://es.mathworks.com/help/nnet/ref/autoencoder.predict.html) || Reconstruct the inputs using trained autoencoder |
| [`stack`](http://es.mathworks.com/help/nnet/ref/autoencoder.stack.html) || Stack encoders from several autoencoders together |
| [`view`](http://es.mathworks.com/help/nnet/ref/autoencoder.view.html) || View autoencoder |

 

## 12.2.2 trainAutoencoder

 

Train an autoencoder

**Syntax**

·        autoenc = trainAutoencoder(X)

·        autoenc = trainAutoencoder(X,hiddenSize)

·        autoenc = trainAutoencoder(**\_\_\_**,Name,Value)

**Description**

[autoenc](http://es.mathworks.com/help/nnet/ref/trainautoencoder.html#outputarg_autoenc) = trainAutoencoder([X](http://es.mathworks.com/help/nnet/ref/trainautoencoder.html#inputarg_X)) returns an autoencoder, autoenc, trained using the training data in X.

[autoenc](http://es.mathworks.com/help/nnet/ref/trainautoencoder.html#outputarg_autoenc) = trainAutoencoder([X](http://es.mathworks.com/help/nnet/ref/trainautoencoder.html#inputarg_X),[hiddenSize](http://es.mathworks.com/help/nnet/ref/trainautoencoder.html#inputarg_hiddenSize)) returns an autoencoder autoenc, with the hidden representation size of hiddenSize.

[autoenc](http://es.mathworks.com/help/nnet/ref/trainautoencoder.html#outputarg_autoenc) = trainAutoencoder(**\_\_\_**,[Name,Value](http://es.mathworks.com/help/nnet/ref/trainautoencoder.html#namevaluepairarguments)) returns an autoencoder autoenc, for any of the above input arguments with additional options specified by one or more Name,Value pair arguments.

For example, you can specify the sparsity proportion or the maximum number of training iterations.

**Examples. Train Sparse Autoencoder**

 

Load the sample data.

X = abalone\_dataset;

 

X is an 8-by-4177 matrix defining eight attributes for 4177 different abalone shells: sex (M, F, and I (for infant)), length, diameter, height, whole weight, shucked weight, viscera weight, shell weight. For more information on the dataset, type help abalone\_dataset in the command line.

 

Train a sparse autoencoder with default settings.

autoenc = trainAutoencoder(X);

Reconstruct the abalone shell ring data using the trained autoencoder.

XReconstructed = predict(autoenc,X);

Compute the mean squared reconstruction error.

mseError = mse(X-XReconstructed)

mseError =

 

    0.0167

 

**Train Autoencoder with Specified Options**

 

Load the sample data.

X = abalone\_dataset;

X is an 8-by-4177 matrix defining eight attributes for 4177 different abalone shells: sex (M, F, and I (for infant)), length, diameter, height, whole weight, shucked weight, viscera weight, shell weight. For more information on the dataset, type help abalone\_dataset in the command line.

 

Train a sparse autoencoder with hidden size 4, 400 maximum epochs, and linear transfer function for the decoder.

autoenc = trainAutoencoder(X,4,'MaxEpochs',400,...

'DecoderTransferFunction','purelin');

 

Reconstruct the abalone shell ring data using the trained autoencoder.

XReconstructed = predict(autoenc,X);

Compute the mean squared reconstruction error.

mseError = mse(X-XReconstructed)

mseError =

 

    0.0056

 

**Reconstruct Observations Using Sparse Autoencoder**

 

Generate the training data.

rng(0,'twister'); % For reproducibility

n = 1000;

r = linspace(-10,10,n)';

x = 1 + r\*5e-2 + sin(r)./r + 0.2\*randn(n,1);

 

Train autoencoder using the training data.

hiddenSize = 25;

autoenc = trainAutoencoder(x',hiddenSize,...

        'EncoderTransferFunction','satlin',...

        'DecoderTransferFunction','purelin',...

        'L2WeightRegularization',0.01,...

        'SparsityRegularization',4,...

        'SparsityProportion',0.10);

 

Generate the test data.

n = 1000;

r = sort(-10 + 20\*rand(n,1));

xtest = 1 + r\*5e-2 + sin(r)./r + 0.4\*randn(n,1);

 

Predict the test data using the trained autoencoder, autoenc .

 

xReconstructed = predict(autoenc,xtest');

Plot the actual test data and the predictions.

figure;

plot(xtest,'r.');

hold on

plot(xReconstructed,'go');

![](images/00143.jpeg)

**Reconstruct Handwritten Digit Images Using Sparse Autoencoder**

 

Load the training data.

X = digittrain\_dataset;

 

The training data is a 1-by-5000 cell array, where each cell containing a 28-by-28 matrix representing a synthetic image of a handwritten digit.

Train an autoencoder with a hidden layer containing 25 neurons.

hiddenSize = 25;

autoenc = trainAutoencoder(X,hiddenSize,...

        'L2WeightRegularization',0.004,...

        'SparsityRegularization',4,...

        'SparsityProportion',0.15);

 

Load the test data.

x = digittest\_dataset;

 

The test data is a 1-by-5000 cell array, with each cell containing a 28-by-28 matrix representing a synthetic image of a handwritten digit.

Reconstruct the test image data using the trained autoencoder, autoenc.

 

xReconstructed = predict(autoenc,x);

View the actual test data.

figure;

for i = 1:20

    subplot(4,5,i);

    imshow(X{i});

end

 

View the reconstructed test data.

figure;

for i = 1:20

    subplot(4,5,i);

    imshow(xReconstructed{i});

end

## 12.2.3 decode

 

Decode encoded data

**Syntax**

·        Y = decode(autoenc,Z)

**Description**

[Y](http://es.mathworks.com/help/nnet/ref/autoencoder.decode.html#outputarg_Y) = decode([autoenc](http://es.mathworks.com/help/nnet/ref/autoencoder.decode.html#inputarg_autoenc),[Z](http://es.mathworks.com/help/nnet/ref/autoencoder.decode.html#inputarg_Z))returns the [decoded data](http://es.mathworks.com/help/nnet/ref/autoencoder.decode.html#buy6x9s) Y, using the autoencoder object autoenc.

Trained autoencoder, returned by the trainAutoencoder function as an object of the Autoencoder class.

 

Data encoded by autoenc, specified as a matrix. Each column of Z represents an encoded sample (observation).

 

Decoded data, returned as a matrix or a cell array of image data.

If the autoencoder [autoenc](http://es.mathworks.com/help/nnet/ref/autoencoder.decode.html#inputarg_autoenc) was trained on a cell array of image data, then Y is also a cell array of images.

 

If the autoencoder autoenc was trained on a matrix, then Y is also a matrix, where each column of Y corresponds to one sample or observation.

**Example: Decode Encoded Data For New Images**

 

Load the training data.

X = digitTrainCellArrayData;

 

X is a 1-by-5003 cell array, where each cell contains a 28-by-28 matrix representing a synthetic image of a handwritten digit.

Train an autoencoder using the training data with a hidden size of 15.

hiddenSize = 15;

autoenc = trainAutoencoder(X,hiddenSize);

 

Extract the encoded data for new images using the autoencoder.

Xnew = digitTestCellArrayData;

features = encode(autoenc,Xnew);

 

Decode the encoded data from the autoencoder.

Y = decode(autoenc,features);

Y is a 1-by-4997 cell array, where each cell contains a 28-by-28 matrix representing a synthetic image of a handwritten digit.

 

## 12.2.4 encode

 

Encode input data

**Syntax**

 

Z = encode(autoenc,Xnew)

 

**Description**

 

[Z](http://es.mathworks.com/help/nnet/ref/autoencoder.encode.html#outputarg_Z) = encode([autoenc](http://es.mathworks.com/help/nnet/ref/autoencoder.encode.html#inputarg_autoenc),[Xnew](http://es.mathworks.com/help/nnet/ref/autoencoder.encode.html#inputarg_Xnew)) returns the [encoded data](http://es.mathworks.com/help/nnet/ref/autoencoder.encode.html#buxdn14-9), Z, for the input data Xnew, using the autoencoder, autoenc.

 

**Example. Encode Decoded Data for New Images**

 

Load the sample data.

X = digitTrainCellArrayData;

 

X is a 1-by-5003 cell array, where each cell contains a 28-by-28 matrix representing a synthetic image of a handwritten digit.

Train an autoencoder with a hidden size of 50 using the training data.

autoenc = trainAutoencoder(X,50);

Encode decoded data for new image data.

Xnew = digitTestCellArrayData;

Z = encode(autoenc,Xnew);

 

Xnew is a 1-by-4997 cell array. Z is a 50-by-4997 matrix, where each column represents the image data of one handwritten digit in the new data Xnew.

 

## 12.2.5 predict

 

Reconstruct the inputs using trained autoencoder

**Syntax**

 

·        Y = predict(autoenc,X)

 

**Description**

 

Y = predict(autoenc,X) returns the predictions [Y](http://es.mathworks.com/help/nnet/ref/autoencoder.predict.html#outputarg_Y) for the input data X, using the autoencoder [autoenc](http://es.mathworks.com/help/nnet/ref/autoencoder.predict.html#inputarg_autoenc). The result Y is a reconstruction of X.

 

**Examples: Predict Continuous Measurements Using Trained Autoencoder**

 

Load the training data.

X = iris\_dataset;

 

The training data contains measurements on four attributes of iris flowers: Sepal length, sepal width, petal length, petal width.

Train an autoencoder on the training data using the positive saturating linear transfer function in the encoder and linear transfer function in the decoder.

autoenc = trainAutoencoder(X,'EncoderTransferFunction',...

'satlin','DecoderTransferFunction','purelin');

 

Reconstruct the measurements using the trained network, autoenc.

 

xReconstructed = predict(autoenc,X);

 

Plot the predicted measurement values along with the actual values in the training dataset.

for i = 1:4

h(i) = subplot(1,4,i);

plot(X(i,:),'r.');

hold on

plot(xReconstructed(i,:),'go');

hold off;

end

title(h(1),{'Sepal';'Length'});

title(h(2),{'Sepal';'Width'});

title(h(3),{'Petal';'Length'});

title(h(4),{'Petal';'Width'});

 

![](images/00144.jpeg)

The red dots represent the training data and the green circles represent the reconstructed data.

 

## 12.2.6 stack

 

Stack encoders from several autoencoders together

**Syntax**

·        stackednet = stack(autoenc1,autoenc2,...)

·        stackednet = stack(autoenc1,autoenc2,...,net1)

**Description**

stackednet = stack(autoenc1,autoenc2,...) returns a network object created by stacking the encoders of the autoencoders, [autoenc1](http://es.mathworks.com/help/nnet/ref/autoencoder.stack.html#inputarg_autoenc1), autoenc2, and so on.

stackednet = stack(autoenc1,autoenc2,...,net1) returns a network object created by stacking the encoders of the autoencoders and the network object [net1](http://es.mathworks.com/help/nnet/ref/autoencoder.stack.html#inputarg_net1).

The autoencoders and the network object can be stacked only if their dimensions match.

 

**Tips**

·        The size of the hidden representation of one autoencoder must match the input size of the next autoencoder or network in the stack.

·        The first input argument of the stacked network is the input argument of the first autoencoder. The output argument from the encoder of the first autoencoder is the input of the second autoencoder in the stacked network. The output argument from the encoder of the second autoencoder is the input argument to the third autoencoder in the stacked network, and so on.

·        The stacked network object stacknet inherits its training parameters from the final input argument [net1](http://es.mathworks.com/help/nnet/ref/autoencoder.stack.html#inputarg_net1).

 

**Examples. Create a Stacked Network**

 

Load the training data.

\[X,T\] = iris\_dataset;

 

Train an autoencoder with a hidden layer of size 5 and a linear transfer function for the decoder. Set the L2 weight regularizer to 0.001, sparsity regularizer to 4 and sparsity proportion to 0.05.

hiddenSize = 5;

autoenc = trainAutoencoder(X, hiddenSize, ...

    'L2WeightRegularization', 0.001, ...

    'SparsityRegularization', 4, ...

    'SparsityProportion', 0.05, ...

    'DecoderTransferFunction','purelin');

 

Extract the features in the hidden layer.

features = encode(autoenc,X);

Train a softmax layer for classification using the features .

 

softnet = trainSoftmaxLayer(features,T);

 

Stack the encoder and the softmax layer to form a deep network.

stackednet = stack(autoenc,softnet);

View the stacked network.

view(stackednet);

 

![](images/00145.jpeg)

 

## 12.2.7 generateFunction

 

Generate a MATLAB function to run the autoencoder

**Syntax**

·        generateFunction(autoenc)

·        generateFunction(autoenc,pathname)

·        generateFunction(autoenc,pathname,Name,Value)

**Description**

generateFunction([autoenc](http://es.mathworks.com/help/nnet/ref/autoencoder.generatefunction.html#inputarg_autoenc)) generates a complete stand-alone function in the current directory, to run the autoencoder autoenc on input data.

generateFunction([autoenc](http://es.mathworks.com/help/nnet/ref/autoencoder.generatefunction.html#inputarg_autoenc),[pathname](http://es.mathworks.com/help/nnet/ref/autoencoder.generatefunction.html#inputarg_pathname)) generates a complete stand-alone function to run the autoencoder autoenc on input data in the location specified by pathname.

generateFunction([autoenc](http://es.mathworks.com/help/nnet/ref/autoencoder.generatefunction.html#inputarg_autoenc),[pathname](http://es.mathworks.com/help/nnet/ref/autoencoder.generatefunction.html#inputarg_pathname),[Name,Value](http://es.mathworks.com/help/nnet/ref/autoencoder.generatefunction.html#namevaluepairarguments)) generates a complete stand-alone function with additional options specified by the Name,Value pair argument.

**Tips**

·        If you do not specify the path and the file name, generateFunction, by default, creates the code in an m-file with the name neural\_function.m. You can change the file name after generateFunction generates it. Or you can specify the path and file name using the [pathname](http://es.mathworks.com/help/nnet/ref/autoencoder.generatefunction.html#inputarg_pathname) input argument in the call to generateFunction.

**Input Arguments**

**autoenc — Trained autoencoder Autoencoder object**

**pathname — Location for generated function string**

**Examples: Generate MATLAB Function for Running Autoencoder**

Load the sample data.

X = iris\_dataset;

Train an autoencoder with 4 neurons in the hidden layer.

autoenc = trainAutoencoder(X,4);

Generate the code for running the autoencoder. Show the links to the MATLAB^® function.

generateFunction(autoenc)

MATLAB function generated: neural\_function.m

To view generated function code: edit neural\_function

For examples of using function: help neural\_function

Generate the code for the autoencoder in a specific path.

generateFunction(autoenc,'H:\\Documents\\Autoencoder')

MATLAB function generated: H:\\Documents\\Autoencoder.m

To view generated function code: edit Autoencoder

For examples of using function: help Autoencoder

## 12.2.8 generateSimulink

 

Generate a Simulink model for the autoencoder

**Syntax**

·        `generateSimulink(autoenc)`

**Description**

`generateSimulink(``autoenc``)` creates a Simulink^® model for the autoencoder, `autoenc`.

**Input Arguments**

**autoenc — Trained autoencoder Autoencoder object**

**Examples: Generate Simulink Model for Autoencoder**

 

Load the training data.

`X = digitsmall_dataset;` 

The training data is a 1-by-500 cell array, where each cell containing a 28-by-28 matrix representing a synthetic image of a handwritten digit.

Train an autoencoder with a hidden layer containing 25 neurons.

`hiddenSize = 25;``autoenc = trainAutoencoder(X,hiddenSize,...``        'L2WeightRegularization',0.004,...``        'SparsityRegularization',4,...``        'SparsityProportion',0.15);` 

 

Create a Simulink model for the autoencoder, `autoenc`.

 

`generateSimulink(autoenc)`` ` 

![](images/00146.gif)

 

 

## 12.2.9 plotWeights

 

Plot a visualization of the weights for the encoder of an autoencoder

 

**Syntax**

·        plotWeights(autoenc)

·        h = plotWeights(autoenc)

**Description**

plotWeights([autoenc](http://es.mathworks.com/help/nnet/ref/autoencoder.plotweights.html#inputarg_autoenc)) visualizes the weights for the autoencoder, autoenc.

[h](http://es.mathworks.com/help/nnet/ref/autoencoder.plotweights.html#outputarg_h) = plotWeights([autoenc](http://es.mathworks.com/help/nnet/ref/autoencoder.plotweights.html#inputarg_autoenc)) returns a function handle h, for the visualization of the encoder weights for the autoencoder, autoenc.

**Tips**

·        plotWeights allows the visualization of the features that the autoencoder learns. Use it when the autoencoder is trained on image data. The visualization of the weights has the same dimensions as the images used for training.

**Input Arguments**

**autoenc — Trained autoencoder Autoencoder object**

**Output Arguments**

**h — Image object handle**

**Examples: Visualize Learned Features**

Load the training data.

X = digitTrainCellArrayData;

The training data is a 1-by-5003 cell array, where each cell contains a 28-by-28 matrix representing a synthetic image of a handwritten digit.

Train an autoencoder with a hidden layer of 25 neurons.

hiddenSize = 25;

autoenc = trainAutoencoder(X,hiddenSize, ...

  'L2WeightRegularization',0.004, ...

  'SparsityRegularization',4, ...

  'SparsityProportion',0.2);

Visualize the learned features.

plotWeights(autoenc);

![](images/00147.jpeg)

## 12.2.10 view

View autoencoder

**Syntax**

·        view(autoenc)

**Description**

view([autoenc](http://es.mathworks.com/help/nnet/ref/autoencoder.view.html#inputarg_autoenc)) returns a diagram of the autoencoder, autoenc.

**Input Arguments**

**autoenc — Trained autoencoder  
Autoencoder object**

**Examples: View Autoencoder**

Load the training data.

X = iris\_dataset;

Train an autoencoder with a hidden layer of size 5 and a linear transfer function for the decoder. Set the L2 weight regularizer to 0.001, sparsity regularizer to 4 and sparsity proportion to 0.05.

hiddenSize = 5;

autoenc = trainAutoencoder(X, hiddenSize, ...

    'L2WeightRegularization',0.001, ...

    'SparsityRegularization',4, ...

    'SparsityProportion',0.05, ...

    'DecoderTransferFunction','purelin');

View the autoencoder.

view(autoenc)

![Descripción: http://es.mathworks.com/help/examples/nnet/ViewAutoencoderExample\_01.png](images/00148.jpeg)

# 12.3 Construct Deep Network Using Autoencoders

 

Load the sample data.

\[X,T\] = wine\_dataset;

 

Train an autoencoder with a hidden layer of size 10 and a linear transfer function for the decoder. Set the L2 weight regularizer to 0.001, sparsity regularizer to 4 and sparsity proportion to 0.05.

hiddenSize = 10;

autoenc1 = trainAutoencoder(X,hiddenSize,...

    'L2WeightRegularization',0.001,...

    'SparsityRegularization',4,...

    'SparsityProportion',0.05,...

    'DecoderTransferFunction','purelin');

 

Extract the features in the hidden layer.

features1 = encode(autoenc1,X);

Train a second autoencoder using the features from the first autoencoder. Do not scale the data.

hiddenSize = 10;

autoenc2 = trainAutoencoder(features1,hiddenSize,...

    'L2WeightRegularization',0.001,...

    'SparsityRegularization',4,...

    'SparsityProportion',0.05,...

    'DecoderTransferFunction','purelin',...

    'ScaleData',false);

Extract the features in the hidden layer.

features2 = encode(autoenc2,features1);

Train a softmax layer for classification using the features, features2, from the second autoencoder, autoenc2.

softnet = trainSoftmaxLayer(features2,T,'LossFunction','crossentropy');

Stack the encoders and the softmax layer to form a deep network.

deepnet = stack(autoenc1,autoenc2,softnet);

Train the deep network on the wine data.

deepnet = train(deepnet,X,T);

Estimate the wine types using the deep network, deepnet.

wine\_type = deepnet(X);

Plot the confusion matrix.

plotconfusion(T,wine\_type);

![](images/00149.jpeg)

 

 

  

13Chapter 13

AUTOENCODERS. EXAMPLES

# 13.1 Train Stacked Autoencoders for Image Classification

 

This example shows how to use Neural Network Toolbox autoencoders functionality for training a deep neural network to classify images of digits.

Neural networks with multiple hidden layers can be useful for solving classification problems with complex data, such as images. Each layer can learn features at a different level of abstraction. However, training neural networks with multiple hidden layers can be difficult in practice.

One way to effectively train a neural network with multiple layers is by training one layer at a time. You can achieve this by training a special type of network known as an autoencoder for each desired hidden layer.

This example shows you how to train a neural network with two hidden layers to classify digits in images. First you train the hidden layers individually in an unsupervised fashion using autoencoders. Then you train a final softmax layer, and join the layers together to form a deep network, which you train one final time in a supervised fashion.

## 13.1.1 Data set

 

This example uses synthetic data throughout, for training and testing. The synthetic images have been generated by applying random affine transformations to digit images created using different fonts.

Each digit image is 28-by-28 pixels, and there are 5,000 training examples. You can load the training data, and view some of the images.

% Load the training data into memory

\[xTrainImages,tTrain\] = digitTrainCellArrayData;

 

% Display some of the training images

clf

for i = 1:20

    subplot(4,5,i);

    imshow(xTrainImages{i});

end

![Descripción: http://www.mathworks.com/help/examples/nnet/AutoencoderDigitsExample\_01.png](images/00150.jpeg)

The labels for the images are stored in a 10-by-5000 matrix, where in every column a single element will be 1 to indicate the class that the digit belongs to, and all other elements in the column will be 0. It should be noted that if the tenth element is 1, then the digit image is a zero.

## 13.1.2 Training the first autoencoder

 

Begin by training a sparse autoencoder on the training data without using the labels.

An autoencoder is a neural network which attempts to replicate its input at its output. Thus, the size of its input will be the same as the size of its output. When the number of neurons in the hidden layer is less than the size of the input, the autoencoder learns a compressed representation of the input.

Neural networks have weights randomly initialized before training. Therefore the results from training are different each time. To avoid this behavior, explicitly set the random number generator seed.

rng('default')

Set the size of the hidden layer for the autoencoder. For the autoencoder that you are going to train, it is a good idea to make this smaller than the input size.

hiddenSize1 = 100;

The type of autoencoder that you will train is a sparse autoencoder. This autoencoder uses regularizers to learn a sparse representation in the first layer. You can control the influence of these regularizers by setting various parameters:

 

·        L2WeightRegularization controls the impact of an L2 regularizer for the weights of the network (and not the biases). This should typically be quite small.

·        SparsityRegularization controls the impact of a sparsity regularizer, which attempts to enforce a constraint on the sparsity of the output from the hidden layer. Note that this is different from applying a sparsity regularizer to the weights.

·        SparsityProportion is a parameter of the sparsity regularizer. It controls the sparsity of the output from the hidden layer. A low value for SparsityProportion usually leads to each neuron in the hidden layer "specializing" by only giving a high output for a small number of training examples. For example, if SparsityProportion is set to 0.1, this is equivalent to saying that each neuron in the hidden layer should have an average output of 0.1 over the training examples. This value must be between 0 and 1. The ideal value varies depending on the nature of the problem.

 

Now train the autoencoder, specifying the values for the regularizers that are described above.

autoenc1 = trainAutoencoder(xTrainImages,hiddenSize1, ...

    'MaxEpochs',400, ...

    'L2WeightRegularization',0.004, ...

    'SparsityRegularization',4, ...

    'SparsityProportion',0.15, ...

    'ScaleData', false);

You can view a diagram of the autoencoder. The autoencoder is comprised of an encoder followed by a decoder. The encoder maps an input to a hidden representation, and the decoder attempts to reverse this mapping to reconstruct the original input.

view(autoenc1)

![Descripción: http://www.mathworks.com/help/examples/nnet/AutoencoderDigitsExample\_02.png](images/00151.jpeg)

## 13.1.3 Visualizing the weights of the first autoencoder

 

The mapping learned by the encoder part of an autoencoder can be useful for extracting features from data. Each neuron in the encoder has a vector of weights associated with it which will be tuned to respond to a particular visual feature. You can view a representation of these features.

figure()

plotWeights(autoenc1);

![Descripción: http://www.mathworks.com/help/examples/nnet/AutoencoderDigitsExample\_03.png](images/00152.jpeg)

You can see that the features learned by the autoencoder represent curls and stroke patterns from the digit images.

The 100-dimensional output from the hidden layer of the autoencoder is a compressed version of the input, which summarizes its response to the features visualized above. Train the next autoencoder on a set of these vectors extracted from the training data. First, you must use the encoder from the trained autoencoder to generate the features.

feat1 = encode(autoenc1,xTrainImages);

## 13.1.4 Training the second autoencoder

 

After training the first autoencoder, you train the second autoencoder in a similar way. The main difference is that you use the features that were generated from the first autoencoder as the training data in the second autoencoder. Also, you decrease the size of the hidden representation to 50, so that the encoder in the second autoencoder learns an even smaller representation of the input data.

hiddenSize2 = 50;

autoenc2 = trainAutoencoder(feat1,hiddenSize2, ...

    'MaxEpochs',100, ...

    'L2WeightRegularization',0.002, ...

    'SparsityRegularization',4, ...

    'SparsityProportion',0.1, ...

    'ScaleData', false);

Once again, you can view a diagram of the autoencoder with the view function.

view(autoenc2)

![Descripción: http://www.mathworks.com/help/examples/nnet/AutoencoderDigitsExample\_04.png](images/00153.jpeg)

You can extract a second set of features by passing the previous set through the encoder from the second autoencoder.

feat2 = encode(autoenc2,feat1);

The original vectors in the training data had 784 dimensions. After passing them through the first encoder, this was reduced to 100 dimensions. After using the second encoder, this was reduced again to 50 dimensions. You can now train a final layer to classify these 50-dimensional vectors into different digit classes.

## 13.1.5 Training the final softmax layer

 

Train a softmax layer to classify the 50-dimensional feature vectors. Unlike the autoencoders, you train the softmax layer in a supervised fashion using labels for the training data.

softnet = trainSoftmaxLayer(feat2,tTrain,'MaxEpochs',400);

You can view a diagram of the softmax layer with the view function.

view(softnet)

![Descripción: http://www.mathworks.com/help/examples/nnet/AutoencoderDigitsExample\_05.png](images/00154.jpeg)

 

## 13.1.6 Forming a stacked neural network

 

You have trained three separate components of a deep neural network in isolation. At this point, it might be useful to view the three neural networks that you have trained. They are autoenc1, autoenc2, and softnet.

view(autoenc1)

view(autoenc2)

view(softnet)

![Descripción: http://www.mathworks.com/help/examples/nnet/AutoencoderDigitsExample\_06.png](images/00151.jpeg)

![Descripción: http://www.mathworks.com/help/examples/nnet/AutoencoderDigitsExample\_07.png](images/00155.jpeg)

![Descripción: http://www.mathworks.com/help/examples/nnet/AutoencoderDigitsExample\_08.png](images/00154.jpeg)

As was explained, the encoders from the autoencoders have been used to extract features. You can stack the encoders from the autoencoders together with the softmax layer to form a deep network.

deepnet = stack(autoenc1,autoenc2,softnet);

You can view a diagram of the stacked network with the view function. The network is formed by the encoders from the autoencoders and the softmax layer.

view(deepnet)

![Descripción: http://www.mathworks.com/help/examples/nnet/AutoencoderDigitsExample\_09.png](images/00156.jpeg)

With the full deep network formed, you can compute the results on the test set. To use images with the stacked network, you have to reshape the test images into a matrix. You can do this by stacking the columns of an image to form a vector, and then forming a matrix from these vectors.

% Get the number of pixels in each image

imageWidth = 28;

imageHeight = 28;

inputSize = imageWidth\*imageHeight;

 

% Load the test images

\[xTestImages,tTest\] = digitTestCellArrayData;

 

% Turn the test images into vectors and put them in a matrix

xTest = zeros(inputSize,numel(xTestImages));

for i = 1:numel(xTestImages)

    xTest(:,i) = xTestImages{i}(:);

end

You can visualize the results with a confusion matrix. The numbers in the bottom right-hand square of the matrix give the overall accuracy.

y = deepnet(xTest);

plotconfusion(tTest,y);

![Descripción: http://www.mathworks.com/help/examples/nnet/AutoencoderDigitsExample\_10.png](images/00157.jpeg)

## 13.1.7 Fine tuning the deep neural network

 

The results for the deep neural network can be improved by performing backpropagation on the whole multilayer network. This process is often referred to as fine tuning.

You fine tune the network by retraining it on the training data in a supervised fashion. Before you can do this, you have to reshape the training images into a matrix, as was done for the test images.

% Turn the training images into vectors and put them in a matrix

xTrain = zeros(inputSize,numel(xTrainImages));

for i = 1:numel(xTrainImages)

    xTrain(:,i) = xTrainImages{i}(:);

end

 

% Perform fine tuning

deepnet = train(deepnet,xTrain,tTrain);

You then view the results again using a confusion matrix.

y = deepnet(xTest);

plotconfusion(tTest,y);

![Descripción: http://www.mathworks.com/help/examples/nnet/AutoencoderDigitsExample\_11.png](images/00158.jpeg)

## 13.1.8 Summary

 

This example showed how to train a deep neural network to classify digits in images using Neural Network Toolbox™. The steps that have been outlined can be applied to other similar problems, such as classifying images of letters, or even small images of objects of a specific category.

 

# 13.2 Transfer Learning Using Convolutional Neural Networks

 

Fine-tune a convolutional neural network pretrained on digit images to learn the features of letter images. Transfer learning is considered as the transfer of knowledge from one learned task to a new task in machine learning \[1\]. In the context of neural networks, it is transferring learned features of a pretrained network to a new problem. Training a convolutional neural network from the beginning in each case usually is not effective when there is not sufficient amount of training data. The common practice in deep learning for such cases is to use a network that is trained on a large data set for a new problem. While the initial layers of the pretrained network can be fixed, the last few layers must be fine-tuned to learn the specific features of the new data set. Transfer learning usually results in faster training times than training a new convolutional neural network because you do not need to estimate all the parameters in the new network.

**NOTE:** Training a convolutional neural network requires Parallel Computing Toolbox™ and a CUDA®-enabled NVIDIA® GPU with compute capability 3.0 or higher.

Load the sample data as an ImageDatastore.

digitDatasetPath = fullfile(matlabroot,'toolbox','nnet','nndemos',...

    'nndatasets','DigitDataset');

digitData = imageDatastore(digitDatasetPath,...

        'IncludeSubfolders',true,'LabelSource','foldernames');

The data store contains 10000 synthetic images of digits 0–9. The images are generated by applying random transformations to digit images created using different fonts. Each digit image is 28-by-28 pixels.

Display some of the images in the datastore.

for i = 1:20

    subplot(4,5,i);

    imshow(digitData.Files{i});

end

![Descripción: http://www.mathworks.com/help/examples/nnet/TransferLearningUsingConvolutionalNeuralNetworksExample\_01.png](images/00159.jpeg)

Check the number of images in each digit category.

digitData.countEachLabel

ans = 

 

    Label    Count

    \_\_\_\_\_    \_\_\_\_\_

 

    0         988 

    1        1026 

    2        1003 

    3         993 

    4         991 

    5        1017 

    6         992 

    7         999 

    8        1003 

    9         988 

 

The data contains an unequal number of images per category.

To balance the number of images for each digit in the training set, first find the minimum number of images in a category.

minSetCount = min(digitData.countEachLabel{:,2})

minSetCount =

 

   988

 

Divide the dataset so that each category in the training set has 494 images and the testing set has the remaining images from each label.

trainingNumFiles = round(minSetCount/2);

rng(1) % For reproducibility

\[trainDigitData,testDigitData\] = splitEachLabel(digitData,...

                                  trainingNumFiles,'randomize');

splitEachLabel splits the image files in digitData into two new datastores, trainDigitData and testDigitData.

Create the layers for the convolutional neural network.

layers = \[imageInputLayer(\[28 28 1\])

         convolution2dLayer(5,20)

         reluLayer()

         maxPooling2dLayer(2,'Stride',2)

         fullyConnectedLayer(10)

         softmaxLayer()

         classificationLayer()\];

Create the training options. Set the maximum number of epochs at 20, and start the training with an initial learning rate of 0.001.

options = trainingOptions('sgdm','MaxEpochs',20,...

        'InitialLearnRate',0.001);

Train the network using the training set and the options you defined in the previous step.

convnet = trainNetwork(trainDigitData,layers,options);

|=========================================================================================|

|     Epoch    |   Iteration  | Time Elapsed |  Mini-batch  |  Mini-batch  | Base Learning|

|              |              |  (seconds)   |     Loss     |   Accuracy   |     Rate     |

|=========================================================================================|

|            2 |           50 |         0.71 |       0.2233 |       92.97% |     0.001000 |

|            3 |          100 |         1.37 |       0.0182 |       99.22% |     0.001000 |

|            4 |          150 |         2.02 |       0.0395 |       99.22% |     0.001000 |

|            6 |          200 |         2.70 |       0.0105 |       99.22% |     0.001000 |

|            7 |          250 |         3.35 |       0.0026 |      100.00% |     0.001000 |

|            8 |          300 |         4.00 |       0.0004 |      100.00% |     0.001000 |

|           10 |          350 |         4.67 |       0.0002 |      100.00% |     0.001000 |

|           11 |          400 |         5.32 |       0.0001 |      100.00% |     0.001000 |

|           12 |          450 |         5.95 |       0.0001 |      100.00% |     0.001000 |

|           14 |          500 |         6.60 |       0.0002 |      100.00% |     0.001000 |

|           15 |          550 |         7.23 |       0.0001 |      100.00% |     0.001000 |

|           16 |          600 |         7.87 |       0.0001 |      100.00% |     0.001000 |

|           18 |          650 |         8.52 |       0.0001 |      100.00% |     0.001000 |

|           19 |          700 |         9.15 |       0.0001 |      100.00% |     0.001000 |

|           20 |          750 |         9.79 |       0.0000 |      100.00% |     0.001000 |

|=========================================================================================|

Test the network using the testing set and compute the accuracy.

YTest = classify(convnet,testDigitData);

TTest = testDigitData.Labels;

accuracy = sum(YTest == TTest)/numel(YTest)

accuracy =

 

    0.9976

 

Accuracy is the ratio of the number of true labels in the test data matching the classifications from classify, to the number of images in the test data. In this case 99.78% of the digit estimations match the true digit values in the test set.

Now, suppose you would like to use the trained network net to predict classes on a new set of data. Load the letters training data.

load lettersTrainSet.mat

XTrain contains 1500 28-by-28 grayscale images of the letters A, B, and C in a 4-D array. TTrain contains the categorical array of the letter labels.

Display some of the letter images.

figure;

for j = 1:20

    subplot(4,5,j);

    selectImage = datasample(XTrain,1,4);

    imshow(selectImage,\[\]);

end

![Descripción: http://www.mathworks.com/help/examples/nnet/TransferLearningUsingConvolutionalNeuralNetworksExample\_02.png](images/00160.jpeg)

The pixel values in XTrain are in the range \[0 1\]. The digit data used in training the network net were in \[0 255\]; scale the letters data between \[0 255\].

XTrain = XTrain\*255;

The last three layers of the trained network net are tuned for the digit dataset, which has 10 classes. The properties of these layers depend on the classification task. Display the fully connected layer (fullyConnectedLayer).

convnet.Layers(end-2)

ans = 

 

  FullyConnectedLayer with properties:

 

          Name: 'fc'

 

   Hyperparameters

     InputSize: 2880

    OutputSize: 10

 

   Learnable Parameters

       Weights: \[10×2880 single\]

          Bias: \[10×1 single\]

 

Use properties method to see a list of all properties.

Display the last layer (classificationLayer).

convnet.Layers(end)

ans = 

 

  ClassificationOutputLayer with properties:

 

            Name: 'classoutput'

      ClassNames: {10×1 cell}

      OutputSize: 10

 

   Hyperparameters

    LossFunction: 'crossentropyex'

 

These three layers must be fine-tuned for the new classification problem. Extract all the layers but the last three from the trained network, net.

layersTransfer = convnet.Layers(1:end-3);

The letters data set has three classes. Add a new fully connected layer for three classes, and increase the learning rate for this layer.

layersTransfer(end+1) = fullyConnectedLayer(3,...

              'WeightLearnRateFactor',10,...

                  'BiasLearnRateFactor',20);

WeightLearnRateFactor and BiasLearnRateFactor are multipliers of the global learning rate for the fully connected layer.

Add a softmax layer and a classification output layer.

layersTransfer(end+1) = softmaxLayer();

layersTransfer(end+1) = classificationLayer();

Create the options for transfer learning. You do not have to train for many epochs (MaxEpochs can be lower than before). Set the InitialLearnRate at a lower rate than used for training net to improve convergence by taking smaller steps.

optionsTransfer = trainingOptions('sgdm',...

         'MaxEpochs',5,...

         'InitialLearnRate',0.000005,...

         'Verbose',true);

Perform transfer learning.

convnetTransfer = trainNetwork(XTrain,TTrain,...

                    layersTransfer,optionsTransfer);

|=========================================================================================|

|     Epoch    |   Iteration  | Time Elapsed |  Mini-batch  |  Mini-batch  | Base Learning|

|              |              |  (seconds)   |     Loss     |   Accuracy   |     Rate     |

|=========================================================================================|

|            5 |           50 |         0.43 |       0.0011 |      100.00% |     0.000005 |

|=========================================================================================|

Load the letters test data. Similar to the letters training data, scale the testing data between \[0 255\], because the training data were between that range.

load lettersTestSet.mat

XTest = XTest\*255;

Test the accuracy.

YTest = classify(convnetTransfer,XTest);

accuracy = sum(YTest == TTest)/numel(TTest)

accuracy =

 

    0.9587