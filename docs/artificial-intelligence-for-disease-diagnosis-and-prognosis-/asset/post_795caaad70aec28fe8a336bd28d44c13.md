
## Review of Artifact Detection Methods for Automated Analysis and Diagnosis in Digital Pathology

Hossain Shakawat
Department of Computer Science, American International University, Dhaka, Bangladesh

Sakir Hossain, Alamgir Kabir, S. M. Hasan Mahmud,
and M. M. Manjurul Islam
Memorial Sloan Kettering Cancer Center, New York, New York

Faisal Tariq
James Watt School of Engineering, University of Glasgow, Glasgow, UK

## CONTENTS

- 11.1 Introduction ......... 178
- 11.2 Automated Analysis and Diagnosis in Digital Pathology ......... 179
  - 11.2.1 Morphological Image Analysis ......... 182
  - 11.2.2 Molecular Image Analysis ......... 182
- 11.3 Major Artifacts ......... 184
  - 11.3.1 Scanning Artifacts ......... 184
  - 11.3.2 Tissue Artifacts ......... 186
- 11.4 Challenges for Automated Analysis due to Artifacts ......... 189
- 11.5 Review of Existing Artifact Detection Methods ......... 190
  - 11.5.1 Image Enhancement-Based and Other Methods ......... 191
  - 11.5.2 Machine Learning-Based Methods ......... 194
  - 11.5.3 Deep Learning-Based Methods ......... 195
- 11.6 Discussion ......... 197
- 11.7 Conclusion ......... 198

Traditionally, pathological analysis and diagnosis is performed by observing biopsy specimen fixed on a glass slide using a microscope. In digital pathology, a scanner converts the glass slide specimen into a high-resolution digital image, called whole slide image (WSI) which is observed on a computer screen. The WSI can be processed using image processing and artificial intelligence (AI) techniques for automatic analysis and diagnosis. The application of image processing and AI uncovers many useful information that remained unexplored in traditional pathology. This enabled more accurate analysis and precise selection treatment for better patient care. However, the accuracy of analysis could be affected if the quality of the WSI is compromised due to artifacts such as focus blur, tissue folds, or air bubbles. In traditional pathology, the specimen is checked for quality by manual review. A modern pathology requires an intelligent solution for reproducible automated analysis. This chapter introduces the whole slide imaging system and the major artifacts found in WSI, addresses the challenges of automated analysis caused by the artifacts, and reviews the existing artifact detection methods.

## 11.1 INTRODUCTION

Traditionally, the pathological analysis starts with a biopsy to remove tissue from the body, then the specimen is processed at different stages to place it on a transparent glass slide in a life-like state which is then examined under the microscope for analysis or to make a diagnostic decision. A pathologist compiles the entire specimen manually by adjusting the microscope to select suitable regions for examination during which artifact-affected areas are identified and ignored. Such manual selection and examination of regions are time-consuming, labor-intensive and the assessment may vary among pathologists. Figure 11.1 shows the approach of a traditional microscopy-based pathological system. A biopsy specimen goes through a series of steps to prepare the glass slide which includes tissue fixation, fitting tissue into a cassette, tissue processing, sectioning, and staining. When the glass slide specimen is ready, it is observed using a microscope. Pathological analysis using a glass slide specimen and microscope involves checking the quality of the glass slide specimen, selecting the appropriate region, and compiling the observed information. In a microscope-based traditional pathology, all these tasks are performed manually by a pathologist.

In digital pathology, an advanced imaging device called whole slide imaging (WSI) scanner is utilized in place of the microscope. The WSI scanner converts the entire pathological specimen into a digital image which is observed on a computer screen for analysis and diagnosis using special software. The WSI scanner is considered the key to digital pathology. WSI system enables inch-perfect conversion of pathology specimens into a digital image, rapid transmission of the digital specimen for consultations, lossless preservation of the specimen, and user-friendly examination of the specimen on a digital display. Moreover, the incorporation of the digital specimen to pathology allows the application of pattern recognition and image analysis techniques for automated analysis and diagnosis. However, the quality of analysis using automated methods highly depends on the quality of the digital specimen which can be affected by different artifacts. The digital specimen includes the artifact contained in the glass slide, plus the artifacts generated while converting the glass slide to the digital image. Artifacts such as tissue fold and focus blur trouble the automated tools and thus mislead the analysis. In traditional pathology, artifacts are detected and ignored

![](img/bffdb4a72252285ac92f0fad78a7f104_193_0.png)

Figure 11.1 Traditional pathology for microscope-based subjective analysis.

manually by the pathologist which is time prohibitive and vulnerable to fatigue. For a reproducible automated analysis and diagnosis system, a more practical approach is required. Therefore, the need for an automated quality evaluation system that can estimate the usability of a WSI and locate the artifacts to eliminate them during analysis is indisputable.

This chapter portrays the WSI system as the basis of automated analysis and diagnosis for smart healthcare. Then, the chapter presents the major artifacts which trouble the automatic analysis using WSI. Finally, existing artifact detection methods are reviewed and their application for the automatic analysis is assessed to design a practical system.

## 11.2 AUTOMATED ANALYSIS AND DIAGNOSIS IN DIGITAL PATHOLOGY

Digital pathology is an image-based environment where pathological operations such as sharing, managing, analysis, and diagnosis are performed using information technology and a digital version of pathological specimen called WSI. WSI scanner transforms the entire pathological specimen into a digital image. The concept of the digital pathological specimen was first introduced for remote pathological works, also called telepathology. The digital specimen was shared over the network for analysis or consultation by a pathologist of a remote location. The technology of producing digital specimens significantly improved over the years with the technology of telepathology which includes store-and-forward, robotic microscopy, and WSI. A robotic microscope produces a digital image for a selected area of the glass slide specimen adaptively where the WSI scanner converts the entire specimen into a digital image. The WSI system has two major components: A scanner that produces the digital image and a viewer that is used for observing the image on a computer screen. For many years, the WSI system was considered impractical and discouraged for clinical-pathological works. Major issues were the scanning time, image quality, image size, image format, color variation, interactive handling, and data sharing [2,3]. At present time, many advanced scanners are available that are capable of converting the entire specimen into a digital image in less than a minute. The quality of the image has improved significantly in recent time and the pixel size is reduced from 1 μm to 0.23 μm. The viewing software is improved which allows seamless zooming, panning, and handling of the WSI. In 2017, Food and Drug Administration in the United States approved Philips's scanner for primary diagnosis which promoted the adaptation of the WSI system in the hospitals. A laboratory in Sweden has implemented a WSI system for large-scale routine diagnosis [4]. However, there are some issues that remained unsolved and worthy to report, mainly related to image quality. The quality of the WSI depends on the quality of the glass slide specimen and the ability of the scanner to produce a high-quality image. Faulty specimen preparation introduces tissue artifacts such as tissue fold and air bubbles in the glass slide which eventually compromises the quality of WSI. The glass slide specimen preparation involves manual operation at different stages, though automatic sectioning machines and staining machines are available in some laboratories. The surface of the specimen on the glass slide is not entirely flat which troubles the focusing system of the scanner to find the optimal focus by adjusting the objective lens. As a result, the focusing system fails sometimes which introduces out-of-focus artifacts in the image. Noise is another crucial artifact caused by the scanning system. The image format is another important issue for the practical implementation of the WSI scanner. The WSI scanner converts the entire specimen into a digital image which is very large in dimensions and requires a large space to store. The size of an uncompressed WSI file ranges between 1GB and 30GB and there is no standard file format. Thus, it is not difficult to understand why a WSI is tricky to handle. The WSI system utilizes a pyramid model to allow the user to access the image at different magnifications as illustrated in Figure 11.2.

![](img/bffdb4a72252285ac92f0fad78a7f104_194_0.png)

Figure 11.2 Pyramid model for a multi-resolution whole slide image.

The top layer is the thumbnail image which provides the lowest resolution such as 1× magnification and the bottom layer contains the highest-resolution image such as
