
## 7. Conclusions

The presented paper investigates the potential and benefits of processing raw GBSAR data in automated radar classification which can be particularly useful for industrial applications focused on monitoring and object detection in environments with limited visibility where this approach can save considerable resources and time. This differs from, and in this paper is contrasted with, the standard practice of applying classification algorithms on reconstructed images. The testing setup was developed around an FMCW based GBSAR system which was designed and constructed using low-cost components. The developed GBSAR was used in a series of measurements that were performed on several objects made of different materials with the final intention to realize a complete GBSAR radar system with embedded computer control capable of classifying these objects.

For classification purposes, a detailed analysis and comparison of two deep learning approaches to GBSAR object recognition was performed. The first approach was a more conventional SAR classification approach based on reconstructed GBSAR images, while in the second approach the classification was performed essentially on raw (unprocessed) data. Multiple different deep learning architectures for both approaches were trained, tested, and compared. These included two baselines based on fully-connected layers and LSTM networks, two standard convolutional neural network architectures-ResNet18 and MobileNetV3-popular in computer vision, and a modified variant of the ResNet18 network which makes it suitable for processing raw GBSAR data. The modification consists of preventing subsampling of the input in the horizontal dimension which is generally small due to the nature of GBSAR data. This modification is our main contribution regarding deep learning model design. The contribution was validated through experiments which showed that the best results on raw data are achieved by the modified version of ResNet18. Additionally, the practice of color jittering as a common data augmentation procedure in computer vision was extended to classification of raw GBSAR data and was shown to provide consistent, though small, improvements. Furthermore, it was shown that classification on raw data outperforms the classification based on reconstructed images. This was partially expected since the SAR image reconstruction algorithms necessarily introduce certain approximations, and with this negatively influence the integrity of the recorded data. In addition to better classification performance, raw data classification is inherently faster since it avoids the need for image reconstruction, and with this is more suitable for embedded computer implementation which opens possibilities for various application scenarios. On the other hand, it limits human visual confirmation and disables approaches in which radar images are combined with optical ones. However, keeping in mind that the primary focus is on applications in embedded systems, this is not a serious hindrance.

Even though this study has shown the applicability of this concept, it was tested using a relatively small dataset in order to focus on the comparison between approaches. Using larger datasets, more classes, and more general problem formulations could lead to more powerful and useful models. The other directions is to seek improvements in terms of more efficient networks and implementation in embedded computers with limited resources. With this in mind, for potential use in future research we generated and publicly released these datasets of raw GBSAR data and reconstructed radar images which we intend to update with time.

**Author Contributions:** Conceptualization, M.K., F.T., D.B. and M.B.; methodology, M.K., F.T., D.B. and M.B.; software, M.K. and F.T.; validation, M.K., F.T., D.B. and M.B.; formal analysis, M.K. and F.T.; investigation, M.K. and F.T.; resources, M.B.; data curation, M.K. and F.T.; writing—original draft preparation, M.K. and F.T.; writing—review and editing, D.B. and M.B.; visualization, M.K. and F.T.; supervision, D.B. and M.B.; project administration, M.B.; funding acquisition, M.B. All authors have read and agreed to the published version of the manuscript.

**Funding:** This work was supported in part by Croatian Science Foundation (HRZZ) under the project number IP-2019-04-1064.

**Data Availability Statement:** RealSAR datasets (RAW and IMG) used in this research are publicly available: https://data.mendeley.com/datasets/m458grc688/draft?a=ff342b09-dd03-4d09-a169-560af2f87773 (accessed on 1 November 2022).

**Conflicts of Interest:** The authors declare no conflict of interest.

## Abbreviations

The following abbreviations are used in this manuscript:

| Abbreviation | Meaning |
|---|---|
| SAR | Synthetic Aperture Radar |
| GBSAR | Ground Based SAR |
| CNN | Convolutional Neural Network |
| FMCW | Frequency Modulated Continuous Wave |
| FFT | Fast Fourier Transform |
| IFFT | Inverse FFT |
| RPi | Microcomputer Raspberry Pi 4B |
| VCO | Voltage-Controlled Oscillator |
| SNR | Signal to Noise Ratio |
| AP | Average Precision |
| mAP | Mean Average Precision |

## References

1. Copernicus Space Component Mission Management Team. Sentinel High Level Operations Plan (HLOP). Available online: https://sentinels.copernicus.eu/documents/247904/685154/Sentinel+HLOP+--+Issue+3.1.++16+Dec+2021.pdf (accessed on 23 July 2022).
2. Liu, B.; He, K.; Han, M.; Hu, X.; Ma, G.; Wu, M. Application of UAV and GB-SAR in Mechanism Research and Monitoring of Zhonghaicun Landslide in Southwest China. Remote Sens. 2021, 13, 1653. [CrossRef]
3. Izumi, Y.; Zou, L.; Kikuta, K.; Sato, M. Anomalous Atmospheric Phase Screen Compensation in Ground-Based SAR over Mountainous Area. In Proceedings of the IGARSS 2019—2019 IEEE International Geoscience and Remote Sensing Symposium, Yokohama, Japan, 28 July–2 August 2019; pp. 2030–2033. [CrossRef]
4. Chet, K.V.; Siong, L.C.; Hsin, W.H.H.; Wei, L.L.; Guey, C.W.; Yam, C.M.; Sze, L.T.; Kit, C.Y. Ku-band ground-based SAR experiments for surface deformation monitoring. In Proceedings of the 2015 IEEE 5th Asia-Pacific Conference on Synthetic Aperture Radar (APSAR), Singapore, 1–4 September 2015; pp. 641–644. [CrossRef]
5. Ma, Z.; Mei, G.; Prezioso, E.; Zhang, Z.; Xu, N. A deep learning approach using graph convolutional networks for slope deformation prediction based on time-series displacement data. Neural Comput. Appl. 2021, 33, 14441–14457. [CrossRef]
6. Tarchi, D.; Antonello, G.; Casagli, N.; Farina, P.; Fortuny-Guasch, J.; Guerri, L.; Leva, D. On the Use of Ground-Based SAR Interferometry for Slope Failure Early Warning: The Cortenova Rock Slide (Italy). In Landslides: Risk Analysis and Sustainable Disaster Management; Sassa, K., Fukuoka, H., Wang, F., Wang, G., Eds.; Springer: Berlin/Heidelberg, Germany, 2005; pp. 337–342. [CrossRef]
7. Martinez-Vazquez, A.; Fortuny-Guasch, J. A GB-SAR Processor for Snow Avalanche Identification. IEEE Trans. Geosci. Remote Sens. 2008, 46, 3948–3956. [CrossRef]
8. Miccinesi, L.; Consumi, T.; Beni, A.; Pieraccini, M. W-band MIMO GB-SAR for Bridge Testing/Monitoring. Electronics 2021, 10, 2261. [CrossRef]
9. Qiu, Z.; Jiao, M.; Jiang, T.; Zhou, L. Dam Structure Deformation Monitoring by GB-InSAR Approach. IEEE Access 2020, 8, 123287–123296. [CrossRef]
10. Du, S.; Feng, G.; Wang, J.; Feng, S.; Malekian, R.; Li, Z. A New Machine-Learning Prediction Model for Slope Deformation of an Open-Pit Mine: An Evaluation of Field Data. Energies 2019, 12, 1288. [CrossRef]
11. Kang, M.K.; Kim, K.E.; Cho, S.J.; Lee, H.; Lee, J.H. Wishart supervised classification results of C-band polarimetric GB-SAR image data. In Proceedings of the 2011 IEEE International Geoscience and Remote Sensing Symposium, Vancouver, BC, Canada, 24–29 July 2011; pp. 459–462. [CrossRef]
12. Feng, S.J; Ji, K.; Zhang, L.; Ma, X.; Kuang, G. SAR Target Classification Based on Integration of ASC Parts Model and Deep Learning Algorithm. IEEE J. Sel. Top. Appl. Earth Obs. Remote Sens. 2021, 14, 10213–10225. [CrossRef]
13. Liu, H.; Li, S. Decision fusion of sparse representation and support vector machine for SAR image target recognition. Neurocomputing 2013, 113, 97–104. [CrossRef]
14. Huang, Z.; Pan, Z.; Lei, B. Transfer Learning with Deep Convolutional Neural Network for SAR Target Classification with Limited Labeled Data. Remote Sens. 2017, 9, 907. [CrossRef]
15. Chen, S.; Wang, H.; Xu, F.; Jin, Y.Q. Target Classification Using the Deep Convolutional Networks for SAR Images. IEEE Trans. Geosci. Remote Sens. 2016, 54, 4806–4817. [CrossRef]
