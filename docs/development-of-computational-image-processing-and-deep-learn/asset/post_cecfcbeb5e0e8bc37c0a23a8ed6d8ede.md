
- 3.7.3 Decomposition method . . . . . . . . . . . . 154
- 3.7.4 Artificial neural network . . . . . . . . . . 157
- 3.7.5 Simplified decomposition method for tensors of fourth-order . . . . . . . . . . 160
- 3.8 Microstructure generation through generative adversarial network . . . . . . . . . . 161
- 3.8.1 Computational resources and software . . . . . . 162
- 3.8.2 Image pre-processing . . . . . . . . . . . . 163
- 3.8.3 Network architecture . . . . . . . . . . . . 168
- 3.8.4 Quantitative quality metrics . . . . . . . . . 170
- 3.8.5 Overview of all chosen parameters . . . . . . 173
- 4 Results . . . . . . . . . . . . . . . . . . . . 175
- 4.1 Characteristics of microstructure . . . . . . . 175
- 4.2 Plastificate investigations . . . . . . . . . . 177
- 4.2.1 Initial orientation . . . . . . . . . . . . 178
- 4.2.2 Porosity and volume . . . . . . . . . . . . 181
- 4.3 Fiber volume content . . . . . . . . . . . . . 184
- 4.3.1 Chemical dissolution . . . . . . . . . . . . 184
- 4.3.2 "Average or above" (AOA) thresholding . . . . 185
- 4.3.3 Convolutional neural network . . . . . . . . 189
- 4.4 Fiber length distributions . . . . . . . . . . 192
- 4.5 Fiber orientation . . . . . . . . . . . . . . 194
- 4.5.1 Validation of the application of the structure tensor method . . . . . . . . . . 195
- 4.5.2 Characteristics of the FOD across the z-axis . . . . 198
- 4.6 Interpolation of fiber orientation tensors . . . 199
- 4.6.1 Component averaging . . . . . . . . . . . . 200
- 4.6.2 Decomposition . . . . . . . . . . . . . . 204
- 4.6.3 Artificial neural network . . . . . . . . . . 208
- 4.6.4 Interpolation of tensors of fourth-order through adapted decomposition method . . . . 211
- 4.7 Microstructure image generation through generative adversarial network . . . . . . . . . 215
- 4.7.1 Generated images . . . . . . . . . . . . . . . . . . 215
- 4.7.2 Loss plot and FID . . . . . . . . . . . . . . . . . 217
- 4.7.3 Nearest neighbors . . . . . . . . . . . . . . . . . 219
- 5 Discussion . . . . . . . . . . . . . . . . . . . . . . . . . 227
- 5.1 Investigations of plastificate . . . . . . . . . . . . 227
- 5.2 Determination of fiber volume content . . . . . . . . 230
- 5.2.1 Chemical method . . . . . . . . . . . . . . . . . 231
- 5.2.2 "Average or above" (AOA) thresholding . . . . . 234
- 5.2.3 CNN . . . . . . . . . . . . . . . . . . . . . . 237
- 5.3 Fiber length distributions . . . . . . . . . . . . . 240
- 5.4 Fiber orientation distributions . . . . . . . . . . 241
- 5.4.1 A11 dominant and planar orientation . . . . . . . 241
- 5.4.2 Orientation behavior across thickness . . . . . . 243
- 5.4.3 Skewed flow front . . . . . . . . . . . . . . . . 244
- 5.4.4 Interpolation of fiber orientation tensors . . . . 246
- 5.5 Microstructure generation through generative adversarial network . . . . . . . . . . . . 257
- 5.5.1 Assessment of generated images . . . . . . . . . 257
- 5.5.2 Further development . . . . . . . . . . . . . . . 261
- 6 Final remarks . . . . . . . . . . . . . . . . . . . . . . . 263
- 6.1 Summary . . . . . . . . . . . . . . . . . . . . . . . 263
- 6.2 Conclusion . . . . . . . . . . . . . . . . . . . . . 265

## 7 Author's publications . . . . . . . . . . . . . . . . . 267
## 8 Supervised student theses . . . . . . . . . . . . . . . 271
## 9 Code and data availability . . . . . . . . . . . . . . . 273
## Bibliography . . . . . . . . . . . . . . . . . . . . . . . 275

## Appendices . . . . . . . . . . . . . . . . . . . 317
## A FVC evaluations . . . . . . . . . . . . . . . . . . 319
- A.1 Results of FVC determined by different conventional thresholding methods . . . . . . . . . . . . . . 319
- A.2 Results of FVC of Plaque 2 determined by AOA thresholding for different pre-filters . . . . . . . . . . . . . . 322
- A.3 Results of FVC of Plaque 3 determined by AOA thresholding for different pre-filters . . . . . . . . . . . . . . 325

## 1 Introduction

At the beginning of this thesis, the motivation for the topic under discussion will be addressed, followed by the objectives of this work and a brief outline of the thesis structure. Subsequently, the indication of the usage of texts/graphics from the author's own publications is clarified.

### 1.1 Motivation

The European Green Deal obliges all EU member states to become climate-neutral by 2050 [1]. To this end, Germany has set an interim target of a 55 % reduction in greenhouse gas emissions by 2030 compared to 1990 levels in a federal climate protection law [2]. The transport sector makes a significant contribution to emissions through automobile traffic and aviation, which makes reducing emissions in these areas correspondingly important. In recent years, research has therefore been carried out in a wide variety of scientific fields, with lightweight design in particular contributing to this end in the field of materials science. This is due to the fact that the vehicle mass enters linearly into four of the five types of driving resistance and therefore plays a decisive role in fuel consumption [3]. This makes material classes that are relatively light, but at the same time offer convincing structural rigidity and strength for the safety of vehicle occupants and functional maintenance, particularly relevant. Fiber reinforced polymers are arguably the best known, relatively new material system in this context of weight-specific excellent mechanical properties [4], which is why a lot of research funding has been invested in their characterization and modelling.

So-called continuous (Co) fiber reinforced components have higher stiffness and strength due to their microstructure (high anisotropy and high fiber volume content), whereas discontinuous (Dico) fiber reinforced components are faster and easier to manufacture and offer a high degree of design freedom. The combination of both Co and Dico to synergistically exploit the advantages of both material classes is the central topic of the International Research Training Group (IRTG) 2078, within the framework of which this doctoral thesis was written. It was funded by the German Research Foundation (DFG). Dico material shows a heterogeneous microstructure, the characterization of which is essential for understanding and simulating the material behavior. Therefore, the project C2 of the IRTG 2078, in the context of which this work was created, aimed to analyze the microstructure of the Dico material used in each generation in more detail; in this third generation of carbon fiber reinforced polyamide 6. In addition to conventional macroscopic and microscopic destructive testing methods, computed tomography (CT) has emerged as probably the most important non-destructive, imaging characterization option. The 3D images, which allow the spatial differentiation of the constituents of the composites through different gray values, can provide important microstructure characterization parameters through image processing algorithms, such as fiber volume contents, fiber length distributions or fiber orientation distributions.

While the development of evaluation methods for CT images of glass fiber reinforced polymers has progressed quite far, new challenges arise when using the stiffer, stronger but also more expensive carbon fibers as reinforcement material. Since polymers and carbon fibers are chemically quite similar and hence their attenuation coefficients differ little, the contrast in the images is comparatively low. In addition, carbon fibers usually have a diameter of 5 µm - 7 µm, which is below the image resolution when scanning reasonable sizes of specimens and also often below the possible image resolution of conventional CT devices in general. This makes it impossible to identify individual fibers and results in significantly higher noise in the images. Several problems arise from these conditions for this work leading to the research objectives described in the next section.
