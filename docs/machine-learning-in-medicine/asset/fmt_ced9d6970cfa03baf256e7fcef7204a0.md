
163. [163.](#C20_chapter13.xhtml#rref13_163) M. Ghazal, S. S. Ali, A. H. Mahmoud, A. M. Shalaby, and A. El-Baz, “Accurate detection of non-proliferative diabetic retinopathy in optical coherence tomography images using convolutional neural networks,” *IEEE Access*, vol. 8, pp. 34387–34397, 2020.

164. [164.](#C20_chapter13.xhtml#rref13_164) K. Hammouda, F. Khalifa, A. Soliman, H. Abdeltawab, M. Ghazal, M. Abou El-Ghar, A. Haddad, H. E. Darwish, R. Keynton, and A. El-Baz, “A 3D CNN with a learnable adaptive shape prior for accurate segmentation of bladder wall using mr images,” in *2020 IEEE 17th International Symposium on Biomedical Imaging (ISBI)*. IEEE, 2020, pp. 935–938.

165. [165.](#C20_chapter13.xhtml#rref13_165) A. Naglah, F. Khalifa, A. Mahmoud, M. Ghazal, P. Jones, T. Murray, A. S. Elmaghraby, and A. El-Baz, “Athlete-customized injury prediction using training load statistical records and machine learning,” in *2018 IEEE International Symposium on Signal Processing and Information Technology (ISSPIT)*. IEEE, 2018, pp. 459–464.

166. [166.](#C20_chapter13.xhtml#rref13_166) A. H. Mahmoud, “Utilizing radiation for smart robotic applications using visible, thermal, and polarization images.” Ph.D. dissertation, University of Louisville, 2014.

167. [167.](#C20_chapter13.xhtml#rref13_167) A. Mahmoud, A. El-Barkouky, J. Graham, and A. Farag, “Pedestrian detection using mixed partial derivative based his togram of oriented gradients,” in *2014 IEEE International Conference on Image Processing (ICIP)*. IEEE, 2014, pp. 2334–2337.

168. [168.](#C20_chapter13.xhtml#rref13_168) A. El-Barkouky, A. Mahmoud, J. Graham, and A. Farag, “An interactive educational drawing system using a humanoid robot and light polarization,” in *2013 IEEE International Conference on Image Processing*. IEEE, 2013, pp. 3407–3411.

169. [169.](#C20_chapter13.xhtml#rref13_169) A. H. Mahmoud, M. T. El-Melegy, and A. A. Farag, “Direct method for shape recovery from polarization and shading,” in *2012 19th IEEE International Conference on Image Processing*. IEEE, 2012, pp. 1769–1772.

170. [170.](#C20_chapter13.xhtml#rref13_170) M. A. Ghazal, A. Mahmoud, A. Aslantas, A. Soliman, A. Shalaby, J. A. Benediktsson, and A. El-Baz, “Vegetation cover estimation using convolutional neural networks,” *IEEE Access*, vol. 7, pp. 132563–132576, 2019.

171. [171.](#C20_chapter13.xhtml#rref13_171) M. Ghazal, A. Mahmoud, A. Shalaby, and A. El-Baz, “Automated framework for accurate segmentation of leaf images for plant health assessment,” *Environmental Monitoring and Assessment*, vol. 191, no. 8, p. 491, 2019.

# [CHAPTER 14](#C02a_toc.xhtml#rc14)

[Early Classification of Renal Rejection Types: A Deep Learning Approach](#C02a_toc.xhtml#rc14)

Mohamed Shehata, Fahmi Khalifa,  

Ahmed Soliman, Shams Shaker,  

Ahmed Shalaby, Maryam El-Baz,  

Ali Mahmoud and Amy C. Dwyer

University of Louisville

Louisville, Kentucky

Mohamed Abou El-Ghar

University of Mansoura

Mansoura, Egypt

Mohammed Ghazal

Abu Dhabi University

Abu Dhabi, United Arab Emirates

Jasjit S. Suri

AtheroPoint LLC

Roseville, California

Ayman El-Baz

University of Louisville

Louisville, Kentucky

University of Louisville at AlAlamein  

International University (UofL-AIU)

New Alamein City, Egypt

## Contents

[14.1 Introduction](#C21_chapter14.xhtml#secc014_1)

[14.2 Methods](#C21_chapter14.xhtml#secc014_2)

[14.2.1 Preprocessing/Segmenting Kidneys](#C21_chapter14.xhtml#secc014_2_1)

[14.2.2 Diffusion Features Extraction](#C21_chapter14.xhtml#secc014_2_2)

[14.2.3 Deep Learning Classification](#C21_chapter14.xhtml#secc014_2_3)

[14.3 Experimental Results](#C21_chapter14.xhtml#secc014_3)

[14.4 Conclusion](#C21_chapter14.xhtml#secc014_4)

[Acknowledgment](#C21_chapter14.xhtml#secc014_5)

[References](#C21_chapter14.xhtml#references-11)

## [14.1 Introduction](#C21_chapter14.xhtml#rsecc014_1)

In the United States alone, approximately 700,000 of the population suffer from chronic kidney disease (CKD) and if not treated promptly in a timely manner, it will lead to end-stage kidney disease (ESKD) and might lead to death. The optimal solution is to go through a renal transplantation surgery, but given the fact that kidney donors are very rare makes this task more complicated. In addition, these renal allografts might be diagnosed with renal transplantation failure in the first 5-year post-transplantation. One of the most detrimental factors of renal transplantation failure is acute renal rejection. In other words, the body rejects the new kidney due to immunological response \[[1](#C21_chapter14.xhtml#ref14_1)\]. To avoid such things, precautions should be taken during the early stages to prolong the survival rate of the transplanted organ \[[2](#C21_chapter14.xhtml#ref14_2),[3](#C21_chapter14.xhtml#ref14_3)\]. Namely, routine clinical follow-ups, estimation, and correct evaluation of the renal allograft after transplantation are essential to curtail the loss of allograft. This loss of allograft may be due to a few types of kidney rejection such as acute tubular necrosis (ATN), antibody-mediated rejection (AMR), or T-cell mediated rejection (TMR). Other types include immunosuppressive toxicity (IT) and viral infection (VI). Although each type of rejection contains a possible treatment, the possibility of two types of rejections occurring at the same time abates the treatment process \[[4](#C21_chapter14.xhtml#ref14_4)\].

Though biopsy is the gold standard method, it cannot be used for early detection because it is extremely invasive, time-consuming, expensive, and frequently causes injurious events such as bleeding, infections, and more \[[1](#C21_chapter14.xhtml#ref14_1)\]. Therefore, alternatives to biopsy that are safer and noninvasive are important. A precise renal computer-aided diagnostic system (CAD) that is non-invasive holds a reassuring analysis on renal allograft rejection. This system collects information, one kidney at a time, and then combines the information quickly at low cost to increase the patient’s survival rate.
