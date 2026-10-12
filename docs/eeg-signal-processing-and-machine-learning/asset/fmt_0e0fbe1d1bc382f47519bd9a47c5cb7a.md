
# Tensor Decomposition and Applications

A tensor is a multidimensional array. More formally, an N‐way or Nth‐order tensor is an element of the tensor product of N vector spaces, each of which has its own coordinate system. A first‐order tensor is a vector, a second‐order tensor is a matrix, and a third‐order tensor has three indices. Tensors of order three or higher are called higher‐order tensors. The order of a tensor is the number of dimensions also known as way or mode. A tensor decomposition has been widely used in signal processing such as in [41]–[50] and neuroscience such as in [51]–[60], [96]. [Figure 5.7](#c05.xhtml#c5-fig-0007) illustrates the concept.

Decomposition of higher‐order tensors has applications in chemometrics, signal processing, communications, linear algebra, computer vision, data mining, neuroscience, and graph analysis. For detection, separation, localization, noise removal, and tracking. Traditionally, two particular tensor decompositions can be considered to be higher‐order extensions of the matrix SVD, namely Canonical decomposition (CANDECOMP)/PARAFAC (CP) tensor decomposition.

From a mathematical viewpoint, there are two general tensor factorization approaches. The first one is the Tucker model which tries to factorize a three‐way tensor to a smaller tensor (core tensor) and three other factors/matrices. This model is not unique since there are various ways the core tensor can be organized. The second one is the PARAFAC tensor model with a superdiagonal core tensor. Since there is no other variation of such a core tensor the PARAFAC factorization is unique which means for orthogonal or independent sources, the mixtures can be decomposed into their constituent sources without any ambiguity. [Figure 5.8](#c05.xhtml#c5-fig-0008) represents the above models. Also, PARAFAC decomposes a tensor into the sum of rank one tensors and the Tucker decomposition is a higher‐order form of principal component analysis (PCA).

There are many other tensor decompositions, including INDSCAL, PARAFAC2, CANDELINC, DEDICOM, and PARATUCK2 as well as nonnegative variants of all of them [[61]](#c05.xhtml#c5-bib-0061). The N‐way Toolbox, Tensor Toolbox, and Multilinear Engine are examples of software packages for working with tensors.

![Figure 5.7 Tensor and its various modes.](images/c05f007.gif)

**Figure 5.7** Tensor and its various modes.

![Figure 5.8 Tensor factorization using: (a) Tucker and (b) PARAFAC models.](images/c05f008.gif)

**Figure 5.8** Tensor factorization using: (a) Tucker and (b) PARAFAC models.

Recently, tensor factorization has been widely used for BSS of both instantaneous and convolutive mixtures. To be able to benefit from tensor modelling, we need to build up a tensor from our two‐dimensional multichannel measurements. As an example, a time–space–frequency tensor can be built by initially transforming the data into the TF domain and then incorporating the space (geometrical locations of the sensors) dimension. For analysis of EEG or magnetoencephalography (MEG) this can be illustrated as in [Figure 5.9](#c05.xhtml#c5-fig-0009).

In general, any other dimension in which the data variation is significant and desired can be selected. For example, to exploit the nonstationarity, one of the dimensions can be represented by the signal segment number. This allows the changes in statistics of the data to be tracked effectively within the tensor model.

![Figure 5.9 A tensor representation of a set of multichannel EEG signals. (a) Time‐domain representation. (b) Time–frequency representation of each electrode signal. (c) The constructed tensor.](images/c05f009a.gif)

**Figure 5.9** A tensor representation of a set of multichannel EEG signals. (a) Time‐domain representation. (b) Time–frequency representation of each electrode signal. (c) The constructed tensor.

In [[60]](#c05.xhtml#c5-bib-0060) an approach for the removal of eye‐blink artefacts from EEG signals based on a novel STF model of EEGs and the robust minimum variance beamformer (RMVB) has been proposed. In this method, in order to remove the artefact, the RMVB has been provided with a priori information, namely, an estimation of the steering vector corresponding to the point source of the eye blink. The artefact‐removed EEGs are subsequently reconstructed by deflation. The a priori knowledge, the vector corresponding to the spatial distribution of the eye‐blink factor, is identified using the STF model of EEGs, provided by the PARAFAC method. In order to reduce the computational complexity present in the estimation of the STF model using the three‐way PARAFAC, the time domain is sub‐divided into a number of segments and a four‐way array is then set to estimate the space–time–frequency–time/segment (STF‐TS) model of the data using the four‐way PARAFAC. The correct number of the factors of the STF model has been effectively estimated by using a novel core consistency diagnostic (CORCONDIA)‐based measure.

Subsequently, the STF‐TS model is shown to approximate closely the classic STF model, with significantly lower computational cost. The results demonstrate that such an algorithm effectively identifies and removes the eye‐blink (EB) artefact from raw EEG measurements. Using this approach, [Figure 5.10](#c05.xhtml#c5-fig-0010) shows the space, time, and frequency signatures of an eye blink as the result of applying PARAFAC. [Figure 5.11](#c05.xhtml#c5-fig-0011) shows the restored EEGs after applying the STF‐TS method. In this method the nonstationarity of the data is also exploited through segmentation as discussed in [Section 5.8.2](#c05.xhtml#c5-sec-0021).

The above approach shows that PARAFAC can be combined with another modality mainly to intelligently select and extract the atom (source) of interest.

More applications of PARAFAC such as in [[59]](#c05.xhtml#c5-bib-0059) related to BCI are explained in other chapters of this book.

![Figure 5.10 The extracted factors using STF–TS modelling. (a) and (b) illustrate respectively the spectral and temporal signatures of the extracted factors. (c) and (d) represents the spatial distributions of those extracted factors [60].](images/c05f010.gif)

**Figure 5.10** The extracted factors using STF–TS modelling. (a) and (b) illustrate respectively the spectral and temporal signatures of the extracted factors. (c) and (d) represents the spatial distributions of those extracted factors [[60]](#c05.xhtml#c5-bib-0060).

## 5.8.2 Solving BSS of Nonstationary Sources Using Tensor Factorization

Using a simple PARAFAC model may provide some insightful information about various components in the signal mixtures. As an example, [Figure 5.12](#c05.xhtml#c5-fig-0012) demonstrates the results of PARAFAC operation for detecting two components (atoms) of an EEG segment recording during left finger movement. The main component in [Figure 5.12](#c05.xhtml#c5-fig-0012)b is in the right‐hand side (contralateral) and the second component in [Figure 5.12](#c05.xhtml#c5-fig-0012)a is in the same side (ipsilateral) of the brain motor cortex.

In this approach, in order to localize seizure signals (within the scalp through an analysis of EEG), a tensor with three modes, i.e. time samples, scales, and electrodes, has been constructed through wavelet analysis of multichannel EEG. Next, they demonstrate that PARAFAC provides promising results in modelling the complex structure of epileptic seizure, localizing a seizure origin and extracting the artefacts.

![Figure 5.11 Restoration of the EEG signals in (a) from multiple eye blinks after applying the STF–TS method [60]; the results are shown in (b).](images/c05f011a.gif)
