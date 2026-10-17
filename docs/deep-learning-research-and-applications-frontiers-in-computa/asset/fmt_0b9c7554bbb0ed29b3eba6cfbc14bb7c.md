
## 2. Detection

In most scenarios such as in obstacle detection for self-driving cars, the number of objects that are to be detected are not known beforehand. Detection involves both localization of objects in the images and labelling them. There has been a lot of progress in this field. In \[[11](#bodymatter-002.xhtml#b_9783110670905-002_ref_011)\], the authors have proposed a method called region-based convolutional neural networks (R-CNNs). In this method, a network is used to propose regions of interest in the image. These regions of interest are then passed to a CNN classifier which predicts the class of the object in the region. A faster version of R-CNNs was proposed in \[[12](#bodymatter-002.xhtml#b_9783110670905-002_ref_012)\] where the region proposal is done after a feature map of the whole image has been generated using a CNN. Other approaches such as you only look once \[[13](#bodymatter-002.xhtml#b_9783110670905-002_ref_013)\] and single shot detection \[[14](#bodymatter-002.xhtml#b_9783110670905-002_ref_014)\] have been developed. These approaches are significantly faster as they involve passing the image through a CNN only once.

## 3. Semantic segmentation

Semantic segmentation involves assigning a class to every pixel in the image. Long et al., presented a model in \[[10](#bodymatter-002.xhtml#b_9783110670905-002_ref_010)\] called the fully convolutional networks which achieved breakthrough results in semantic segmentation. The model first uses the convolution operation to map the image to a feature map and then the transposed convolution operation is used to map this feature map back to a map with height and width the same as the input image. The depth of the final output is equal to the number of classes. Thus, the value of the point at row *i*, column *j*, and depth *d* in the output feature map helps us compute the probability of the pixel *I[ij]* in the input image *I* belonging to class *d*. [Figures 2.15](#bodymatter-002.xhtml#b_9783110670905-002_fig_015)–[2.26](#bodymatter-002.xhtml#b_9783110670905-002_fig_026) illustrate localization, detection, and segmentation.

## 4. Speech recognition

The application of CNNs is not limited to just visual data. CNNs are also being applied in speech and text processing. Speech recognition is the task of identifying words and phrases in speech and storing them in machine-readable format. Most approaches such as in \[[15](#bodymatter-002.xhtml#b_9783110670905-002_ref_015)\] pass frames from the audio signal to a CNN. The CNN uses a pooling operation over time. CNNs have been shown to be comparable to recurrent neural networks (RNNs) for speech recognition.

## 5. Visual Question Answering (VQA)

In VQA, our agent has to answer questions related to an image. These tasks require a deeper understanding of the image; simple captions are not that useful. The agent also needs to perform complex reasoning. Many modern approaches such as \[[16](#bodymatter-002.xhtml#b_9783110670905-002_ref_016)\] use a CNN to map the image to a feature vector using a CNN and using a RNN for generating an answer for the given textual question. The advantage of such a system is that it can be trained end to end.

## 2.10 Conclusion and future work

In this chapter we have introduced the powerful CNNs (CNN). CNNs allow us to overcome the many problems faced when making DNNs. They have found application in many domains such as image classification, object detection, segmentation, text classification, and speech recognition. The recently developed generative adversarial networks (GANs) \[[17](#bodymatter-002.xhtml#b_9783110670905-002_ref_017)\] have opened up new possibilities for applications of CNNs. Radford et al. \[[18](#bodymatter-002.xhtml#b_9783110670905-002_ref_018)\] presented an architecture that combines both GANs and CNNs. This has resulted in many impressive breakthroughs in generative tasks involving images. In \[[9](#bodymatter-002.xhtml#b_9783110670905-002_ref_009)\], the authors have used this combination of CNNs and GANs for upscaling images to higher resolutions. A lot of progress has also taken place in mapping images from one domain to another even without paired datasets \[[19](#bodymatter-002.xhtml#b_9783110670905-002_ref_019)\]. Capsule networks \[[20](#bodymatter-002.xhtml#b_9783110670905-002_ref_020)\] have built upon CNNs and are an attempt at extracting equivariant features. CNNs are an active area of research and new applications with breakthrough results are consistently being found.

## References

\[1\]Mitchell T. M. Machine learning. WCB, 1997. [→](#bodymatter-002.xhtml#xref_d63256e2953)

\[2\]Goodfellow I., Bengio Y., & Courville A. Deep Learning. MIT Press, 2016. [a](#bodymatter-002.xhtml#xref_d63256e4196), [b](#bodymatter-002.xhtml#xref_d63256e4659), [c](#bodymatter-002.xhtml#xref_d63256e4874)

\[3\]Kauderer-Abrams E. Quantifying Translation-Invariance in Convolutional Neural Networks. 2017. [a](#bodymatter-002.xhtml#xref_d63256e5112), [b](#bodymatter-002.xhtml#xref_d63256e5121)

\[4\]Gens R., Pedro M. D. Deep symmetry networks. Advances in Neural Information Processing Systems, 2014. [→](#bodymatter-002.xhtml#xref_d63256e5115)

\[5\]Jaderberg M., Simonyan K., & Zisserman A. Spatial transformer networks. Advances in Neural Information Processing Systems, 2015. [→](#bodymatter-002.xhtml#xref_d63256e5118)

\[6\]Simonyan K., Vedaldi A., Zisserman A. Deep inside convolutional networks: Visualising image classification models and saliency maps. arXiv preprint arXiv:1312.6034, 2013. [→](#bodymatter-002.xhtml#xref_d63256e6171)

\[7\]Dumoulin V., Visin F. A guide to convolution arithmetic for deep learning. arXiv preprint arXiv:1603.07285, 2016. [→](#bodymatter-002.xhtml#xref_d63256e6264)

\[8\]Zeiler M. D., & Fergus R. Visualizing and understanding convolutional networks. European conference on computer vision, Springer, Cham, September 2014, 818–833. [→](#bodymatter-002.xhtml#xref_d63256e6268)

\[9\]Ledig C., Theis L., Huszr F., Caballero J., Cunningham A., Acosta A., & Shi W. Photo-Realistic Single Image Super-Resolution Using a Generative Adversarial Network. CVPR, July 2017, 2(3), 4. [a](#bodymatter-002.xhtml#xref_d63256e6271), [b](#bodymatter-002.xhtml#xref_d63256e6429)

\[10\]Long J., Shelhamer E., & Darrell T. Fully convolutional networks for semantic segmentation. Proceedings of the IEEE conference on computer vision and pattern recognition, 2015, 3431–3440. [a](#bodymatter-002.xhtml#xref_d63256e6274), [b](#bodymatter-002.xhtml#xref_d63256e6361)

\[11\]Girshick R., Donahue J., Darrell T., & Malik J. Rich feature hierarchies for accurate object detection and semantic segmentation. Proceedings of the IEEE conference on computer vision and pattern recognition, 2014, 580–587. [a](#bodymatter-002.xhtml#xref_d63256e6333), [b](#bodymatter-002.xhtml#xref_d63256e6344)

\[12\]Girshick R. Fast R-CNN. Proceedings of the IEEE international conference on computer vision, 2015, 1440–1448. [→](#bodymatter-002.xhtml#xref_d63256e6347)

\[13\]Redmon J., Divvala S., Girshick R., & Farhadi A. You only look once: Unified, real-time object detection. Proceedings of the IEEE conference on computer vision and pattern recognition, 2016, 779–788. [→](#bodymatter-002.xhtml#xref_d63256e6350)

\[14\]Liu W., Anguelov D., Erhan D., Szegedy C., Reed S., Fu C. Y., & Berg A. C. Ssd: Single shot multibox detector. European conference on computer vision, Springer, Cham, October 2016, 21–37. [→](#bodymatter-002.xhtml#xref_d63256e6353)

\[15\]Palaz D., Collobert R. Analysis of cnn-based speech recognition system using raw speech as input. Proceedings of INTERSPEECH, 2015, EPFL-CONF-210029. [→](#bodymatter-002.xhtml#xref_d63256e6396)

\[16\]Malinowski M., Rohrbach M., & Fritz M. Ask your neurons: A neural-based approach to answering questions about images. Proceedings of the IEEE international conference on computer vision, 2015, 1–9. [→](#bodymatter-002.xhtml#xref_d63256e6404)
