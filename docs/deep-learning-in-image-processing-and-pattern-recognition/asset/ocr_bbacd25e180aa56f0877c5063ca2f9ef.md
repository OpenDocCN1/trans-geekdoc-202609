smoke regions in the first frames. However, the lower accuracy segmentation values in particular frames are justified by the similarity between intensity regions. Due to the appearance of smoke in various color combinations and different spatial domains, making it challenging to identify using traditional conventional methods. Another contributing factor to the lower accuracy values is the manual segmentation process. In certain cases, it can be difficult to determine whether a pixel belongs to the fire, smoke, or background class. For instance, when smoke is present against a cloudy sky or when flames are obscured by smoke and segmented as background, the model detected it because of its characteristics. While the resulting segmentation is not really false, it can influence the model’s performance evaluation.

# 5. Conclusions

Efforts to improve early detection and response to wildfires and smoke continue to evolve with advancements in technology and the use of data-driven approaches. By understanding the behavior and characteristics of smoke, it becomes possible to develop more effective strategies to prevent and mitigate their devastating effects. In this work, we introduced a new lightweight convolutional autoencoder architecture and incorporated an automatic scheme based on color and texture features characteristics of smoke and a nonlinear adaptive level set algorithm. Also, we provided a detailed explanation of the implementation and training process, as well as the experimental results and evaluation for both the reconstruction and segmentation stages in video sequences. Our proposed workflow yielded visually and quantitatively satisfactory results, effectively improving image quality, eliminating noise, and accurately detecting smoke boundaries in RGB video frames.

In future works, our objective is to conduct a thorough investigation into feature extraction and selection techniques, as well as generative models, in order to generate high-resolution and large-scale databases. Also, extend this methodology to track fires and smoke in more complex scenarios. Additionally, we plan to adapt this approach to detect fires and smoke with small appearances, as they serve as the first clue of a wildfire recipient, and implement the algorithm in an embedded system to use it for real-world applications. Ultimately, we intend to generalize our method and reproduce our findings with a diversified data pool.

**Author Contributions:** R.D. conceived the presented approach. R.D., M.B. and A.M. developed the theory and performed the computations. M.S., M.B. and A.M. verified the analytical methods and were involved in planning and supervising the work. M.S. and E.M. encouraged R.D. to design, and they supervised the findings of this work. All authors discussed the results and contributed to the final manuscript. All authors have read and agreed to the published version of the manuscript.

**Funding:** This research received no external funding.

**Data Availability Statement:** Experimental video data covered in this paper are available at the following http://signal.ee.bilkent.edu.tr/VisiFire/Demo/SampleClips.html accessed on 12 April 2023. For the image dataset provided by our laboratory research please contact the authors by email.

**Conflicts of Interest:** The authors declare no conflict of interest.

# References

+   1.  García-Jimenez, S.; Jurió, A.; Pagola, M.; De Miguel, L.; Barrenechea, E.; Bustince, H. Forest fire detection: A fuzzy system approach based on overlap indices. *Appl. Soft Comput.* **2017**, *3*, 834–842. [CrossRef]
2.  Tian, H.; Li, W.; Wang, L.; Oguntoba, P. Smoke detection in video: An image separation approach. *Int. J. Comput. Vis.* **2014**, *106*, 192–209. [CrossRef]
3.  Sun, Y.; Feng, J. Fire and smoke precise detection method based on the attention mechanism and anchor-free mechanism. *Complex Intell. Syst.* **2023**, *1–14*. [CrossRef]
4.  Wang, X.; Li, M.; Gao, M.; Liu, Q.; Li, Z.; Kou, L. Early smoke and flame detection based on transformer. *J. Saf. Sci. Resil.* **2023**, *4*, 294–304. [CrossRef]