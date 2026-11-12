
## INTRODUCTION

In modern years, Deep Learning (DL) (LeCun et al., 2015) has become a large influence on many fields in science and technology. It leads with advances and breakthroughs in audio recognition (Dahl et al., 2012) and image recognition (Krizhevsky et al., 2012), it can prepare artificial agents that defeat human players in Go (Silver et al., 2016) and ATARI games (Mnih et al., 2015), and it produces artistic new images (Mordvintsev et al., 2015; Tan et al., 2017) and music (Briot et al., 2017). The final goal is to produce systems that can help in the diagnosis of disease, to automate the difficult and time-consuming tasks of reading and examining medical images, and to promote treatment planning. We require to be capable to employ machine learning methods to automatically distribute medical images (for example, breast x-ray or biopsy images) as healthy (non-cancerous) or not healthy (cancerous). (M H Hesamian et al., 2019). The diagnosis and treatment decisions can be made based on what is learned about the unhealthy images. The goal is that automatic classification and segmentation can be accomplished using distinct and innovative deep learning techniques, and extraordinary levels of accuracy can be accomplished (Shen et al., 2017). The diagnosis of particular image depends on both image acquisition and image interpretation. Image acquisition devices have been developed up to a certain extent over the recent few years for getting the high resolution radiological images (X-Ray, CT and MRI scans, etc.). However, we started to attain the more benefits for automated image interpretation (L B Curiel et al., 2019). Computer vision activates the machine learning techniques to detect the image pattern as input and gives the effect in the form of size, colour, etc. Due to the extensive variety of different patient data, conventional learning methods are not guaranteed in the future. Now deep learning has much attention in all the fields especially in medicine. It is supposed to hold a $300 million medical imaging market in future. In 2021, deep learning will show rapid development in medicine than the other industry. It is the most powerful complex method of supervised learning. DL is particularly used for investigating the psychiatric and neurological disorders noncompulsory of manual feature selection.

DL technology implemented in medical imaging may enhance and increase innovative technology that has observed because of the digital imaging arrived. Over 15 years, most researchers understand that the applications of DL will bring over humans, and not only the diagnosis will be done by intelligent machines but will also help to prognosticate disease, command medicine and control of the disease treatment. The deep learning is transformed in several sectors such as ophthalmology, pathology, cancer detection, radiology etc. Ophthalmology is the first area to be transformed in health care, however, other sectors such as pathology and a cancer diagnosis has gained recognition and sufficient application with proper efficiency at present.

Medical image segmentation, recognizing and resolution of organs from different medical images produced by modern image techniques such as X-ray, ultrasound, CT or MRI. The images produced by imaging techniques has to give critical information about the shapes and volumes of the human organs. Several researchers have been reported (Suzuki et al., 2017; Lakhani et al., 2018; Kim et al., 2018) that the huge automated segmentation systems been developed by utilizing of existing DL methods. More advanced systems were built on common methods like mathematical methods and edge detection filters. Machine learning approaches towards image features have become more influential technique over others for a longer period of time. Due to hardware development, DL methods came into the picture and begun for giving the practical exhibition of image processing tasks in the field of academia and industry. The ability of deep learning procedures has started to good opportunity for image segmentation, and inappropriate for medical image segmentation. DL techniques have earned much attention in an image segmentation (Breininger et al., 2018) for the past few years. There are several modern review and research articles on medical image segmentation (Alexander Lundervold et al., 2019; Maier et al., 2019). Figure 1 representing the BD and DL in biomedical field. Deep learning is multi-disciplinary research field which includes physics, physiology, signals and systems (ss), mathematics, computer science, biology and medicine.

### Figure 1. Diagram of how biomedical information such as biomedical signals and images, genomic sequences and EHRs can be managed by BD and DL in particular domains of healthcare. Reprint produced from L B Curiel et al., Appl. Sci. 2019.

![](img/a636f78302652a9c2ec5900d81fba475_48_0.png)

## TYPES OF MEDICAL IMAGING

There are various methods of computer-aided detection system was produced and included in the clinical workflow in early 2010. The entirety of the principal responsibilities of medical imaging in radiology applications where the structural abnormalities are identified is classifying them into disease classifications. The different advanced imaging techniques are Microscopic, X-ray, Computer Tomography (CT), and Magnetic Resonance Imaging (MRI) (Ker et al., 2017; Lee et al., 2017; Litjens et al., 2017; Shen et al., 2017)

### Radiography Imaging Technique

It is an imaging technique to view the inner parts of the object using ionizing or non-ionizing radiation such as X-rays, gamma rays etc. It employs a wide beam of X-rays to observe non-uniformly composed material present in the organs. The images produced from this technique is used to find the assessment of the presence or absence of disease, damage or foreign object.

### MRI-Magnetic Resonance Imaging Technique

MRI is utilizing the high powerful magnets thereby emitting radio frequency pulse at the resonant frequency of hydrogen atoms to polarise and stimulate hydrogen nuclei of water molecules in human tissue. MRI doesn't suggest X-rays nor ionizing radiation. MRI is extensively used in hospitals and regarded as a more suitable choice than a CT scan because MRI attends medical diagnosis without revealing of the body to radiation. MRI scan takes a lot of time and are bigger than other scans.

### Ultrasound Imaging Technique

Ultrasound utilizes high range of sound waves for producing the sort of 3D images by tissue. It is more generally associated with fetus image in pregnant women. Ultrasound is also applied for viewing the various inner parts of the human body such as abdominal organs, breast, heart, tendons, arteries, muscles and veins. It presents less anatomical details relative to CT or MRI scans. A significant improvement is ultrasound imaging helps to analyse the use of moving structures in actual time without emitting of radiation. Extremely reliable to practice, can be quickly performed without any unfavourable effects and relatively reasonable.

### Endoscopy Imaging Technique

Endoscopy employs an endoscope that is infused directly into the organ to study the hollow organ of the body. The variety of endoscope changes depending upon the site to be observed in the body and can be administered by a doctor.

### Thermography Imaging Technique

Thermographic imaging technique produces the graphic visualization with respect to surface variation of temperature of the body by measuring the infrared emissions out from it. The amount of radiation increases with an improvement in temperature. It is intelligent for capturing moving objects in real-time.

Thermographic cameras are entirely valuable. Images of the objects having the information with respect to temperatures might not result in perfect thermal imaging of it.

## HARDWARE AND SOFTWARE FOR DEEP LEARNING

GPUs are parallel computing engines, which process the graphical data per second than central processing units (CPUs). Among modern hardware, GPU deep learning is usually 10–30 times faster than on CPUs. By considering hardware, the motivation behind the most deep learning methods are existence of open-source software packages (OSS). The institutions which provide effective GPU implementation in deep neural network operations. The present most popular packages were detailed below.

- 1. Theano (Bastien et al., 2012): provides Python interface
- 2. Tensorflow (Abadi et al., 2016): provides C++ and Python interfaces.
- 3. Torch (Collobert et al., 2011): provides a Lua interface and is used by Facebook AI research
- 4. Caffe (Jia et al., 2014): provides C++ and Python interfaces

## DEEP LEARNING METHODS

DL is one part of machine learning in AI use of multi-layered networks capable of translating the feature from datasets automatically in various tasks such as images, audio, video and text with high accuracy (Shen et al., 2017; Schmidhuber, 2015). DL automatically will learn the complex data representation in a self-taught manner and identify more complex relationships between the input and output (LeCun et al., 2015). Several researchers and data scientists have become interested in using different DL methods to achieve record-breaking performances in various applications (Krizhevsky et al., 2012; Wu et al., 2016). DL methods are divided into 5 principal groups (shown in Figure 2)

- 1. CNNs
- 2. Sequential models (Recurrent Neural Networks (RNNs))
- 3. Deep neural networks (Auto-Encoders)
- 4. Pre-trained models
- 5. Deep generative models (Restricted Boltzmann Machines (RBMs))

## CONVOLUTIONAL NEURAL NETWORK'S ARCHITECTURE (CNNS)

It is one type of important DL algorithm to do image classification, recognition faces, object detections and image recognition etc. CNN architecture consists of 3 different layers and its diagrammatic representation as shown in Figure 3.
