
![](img/a2fc2296b12812e9151e817bff1de16d_381_0.png)

FIGURE 18.6 Image data exchange between QuPath and ImageJ shows interoperability feature (here, positive cell count from QuPath is sent to ImageJ)

script to the selected image. Complex workflows in QuPath can be completed with little scripting. QuPath has its own script editor that can be selected in the Automate tab (Burri, 2022).

Histological study of a tissue or cell section has been challenging for pathologists, due to the time required, along with the risk of partial explanation (Aeffner et al., 2019). But this software enables whole slide image analysis, helping save time. The nucleus/cell area ratio is a particularly helpful parameter for tumour cell identification. Because tumour nuclei are typically larger and more tightly packed than non-tumour nuclei, this value is typically higher for tumour cells. Both of these properties are included in the nucleus/cell area ratio measurement. The measurement is somewhat “noisy”, which contributes to the nucleus/cell area ratio’s limited use (Bankhead et al., 2017). Here, as seen in Figure 18.7, the nucleus/cell ratio is 0.082. As observed, there is significant variation on a cell-by-cell basis, but, overall, tumour cells exhibit higher values (i.e., more yellow/white colour in tumour areas).

## 18.5.4 CellProfiler

CellProfiler (https://cellprofiler.org/releases) is a free and open-source software designed to help biologists with no prior experience in computer vision or programming to automatically calculate characteristics from hundreds of images. Advanced image analysis techniques and algorithms are available as separate modules that can be connected sequentially to create a pipeline. The “pipeline” is utilized to recognize and quantify biological objects and characteristics in images. The CellProfiler biological image analysis tool is widely used to gather a comprehensive set of morphologic, structural, and textural information about cells and organisms on the screen.

![](img/a2fc2296b12812e9151e817bff1de16d_382_0.png)

![](img/a2fc2296b12812e9151e817bff1de16d_382_1.png)

![](img/a2fc2296b12812e9151e817bff1de16d_382_2.png)

FIGURE 18.7 QuPath (A) cell detection in QuPath showing cell nuclei and cell wall, (B) showing all the detections measurement, (C) density map showing region where a higher number of cells is present

Additionally, it has the linked or flexible cell-tracing abilities of time-lapse tests, like the linear assignment problem (LAP) approach, that offer reliable tracking by bridging sequential openings and catching object unions and splits (Bray and Carpenter, 2015). Originally created in MATLAB, CellProfiler was rewritten in Python 2 in 2010, reaching its official end-of-life in 2020. Several changes have been made to the CellProfiler user interface in response to comments from biologists, with the aim of making the application more approachable and user-friendly.

A more feature-rich 3D viewer that allows users to analyze any plane in a volume has now taken the place of the simple 3D viewer first offered in CellProfiler 3.0, and several previous modules have also been improved. The threshold model was completely redesigned to enable adaptive use of all previously developed threshold algorithms, offering users more options in images with significantly changeable backgrounds. “MeasureObjectSizeShape” may record up to 60 new shape measures for each item, including bounding box positions, image moments, and inertia tensors, which are now available in scikit-image. Tissue segment analysis stands out as a possible area for development. As system memory is frequently insufficient to load the complete image at once, the huge file sizes associated with tissue specimens present a difficulty for image analysis. CellProfiler evaluates a wide range of properties, including area, intensity, shape, and texture, identifying cellular and sub-cellular parts in the image. It features pipelines where various image analysis modules can be applied.

It can answer a variety of biological questions, such as cell size, shape, or sub-cellular patterns of DNA. Furthermore, it has advanced algorithms for the analysis of images, which correctly differentiate swarmed cells and non-mammalian cells.

It is optimized for the analysis of two-dimensional (2D) images, as the software operates on a modular pipeline concept. Each module within the software is specifically designed for image processing, contributing to the creation of a structured pipeline. This pipeline facilitates the application of various image analysis modules for tasks such as evaluating cellular properties, including size, shape, and sub-cellular patterns. Each module is designed to be placed in a specific order for images, contributing to the formation of a pipeline that leads to image processing see Figure 18.8. Currently, there are over 50 modules available for use. Measurements are available using its built-in viewing with tools for data plotting. It can be accessible in Microsoft Excel (as CSV) or OpenOffice Calc (Carpenter et al., 2006).

In CellProfiler, the “IdentifyPrimaryObjects” module aids in the identification of objects like nuclei. Comparable to Fiji, this process involves several steps, including Gaussian Blur, Thresholding, Fill Holes, and the declumping of objects using Watershed, followed by Analyze Particles. This sequence highlights the software’s interoperability. In Fiji, the process involves several steps, whereas in CellProfiler, these same steps are encapsulated in a module, providing easy accessibility for analysis. It has a feature for building a pipeline: first, the image can be loaded by opening or dragging and dropping, then select the image type (RGB, Gray), then on the left-hand side double-click the window to add modules, like ColourToGray > IdentifyPrimaryObjects > IdentifySecondaryObjects (see Figure 18.8). The results can be exported as a CSV file (Ward et al., 2022).

As an open-source platform, CellProfiler is for image analysis. It is used to create reproducible analysis pipelines, modular for larger-scale studies. The modules present in the software can be arranged to form the pipeline in different orders according to specific needs for the analysis of images (Flach et al., 2022). It is the better option of the software available for large-scale pipelines for image analysis (see Figure 18.9).

## 18.5.5 Icy

Icy is free, open-source, and available at http://icy.bioimageanalysis.org/. Icy is a platform for collaborative bioimage informatics that combines software with a high-end visual programming framework for the smooth creation of sophisticated imaging workflows, as well as a community website for sharing tools and resources. By promoting and supporting the reusability, modularity, standardization, and management of algorithms and protocols, Icy expands the principles of reproducible research. The BioImage Analysis Lab at the Institute Pasteur developed Icy in 2011. It was created with the intention of addressing the broadest range of biological applications, facilitating simple access to cutting-edge image analysis methods, and promoting reproducibility research (de Chaumont et al., 2012). Icy provides a platform for sharing and publishing collaborative algorithm developments, encourages code sharing and reusability to speed up the creation of new algorithms, and streamlines user feedback and support via a community website (de Chaumont et al., 2013).

Icy is a Java-based desktop application that is supplemented with a website, which acts as a central location for the contribution and exchange of protocols, scripts, and

![](img/a2fc2296b12812e9151e817bff1de16d_384_0.png)

![](img/a2fc2296b12812e9151e817bff1de16d_384_1.png)

![](img/a2fc2296b12812e9151e817bff1de16d_384_2.png)

FIGURE 18.8 CellProfiler software (A) adding module to pipeline, (B) thresholding image (ConvertImageToObject), (C) object measurements

![](img/a2fc2296b12812e9151e817bff1de16d_384_3.png)

FIGURE 18.9 Shows the modular pipeline i.e., adding modules to the image from the left tab and showing the changes in images

plugins. The interface features a ribbon-style toolbar that is very reminiscent of one such tool found in Microsoft’s Office Suite, which makes it extremely simple to use. Icy also incorporates bio-formats to read images for loading WSIs, but it is not able to support the organization of multi-resolution pyramids, which creates a memory management issue when reading very high-resolution images. Icy can be combined with Cytomine as a plugin called Icytomine. To use Icy analysis tools in WSIs, this plugin creates a bridge between the two applications (Gonzalez Obando et al., 2019).

Icy has certain features like spot detection, feature extraction, and best threshold, which chooses the best auto-thresholding technique. It also has an Active Cells plugin, which implements fast active contours for image segmentation (see Figure 18.10). Icy has “protocols” which refers to bioimage analysis workflows and
