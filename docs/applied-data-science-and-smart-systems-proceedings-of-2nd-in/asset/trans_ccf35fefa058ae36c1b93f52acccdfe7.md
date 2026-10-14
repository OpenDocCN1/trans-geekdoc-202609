
# 1. 初始化 `consonant` = 0, `kan` = “ “

## 2. 当生成的 IPA 词中还有未处理的字符时：如果 `consonant` == 0 且 IPA 词是元音：
将对应的元音从卡纳达映射表中添加到 ‘kan’ 中；否则如果 `consonant` != 1 且 IPA 词是元音：
## 3. 将辅音和元音组合，并将结果追加到 ‘kan’
## 4. 减少 ‘consonant’，否则如果 `consonant` != 1 且 IPA 词是下标：
将下标追加到辅音中；否则如果 IPA 词是辅音：
## 5. 增加 ‘consonant’ 并将其追加到 ‘kan’，否则：打印 “error”

| [Table 22.4](#ch22.xhtml#tab22_4) 显示了样本转写示例。 |
| [Table 22.4 卡纳达词的样本转写](#ch22.xhtml#R_tab22_4) |
| 英文单词 || IPA 翻译 || 转写 |
| --- | --- | --- |
| Annabella || ˌænəˈbɛlə || ಅನ್ನಾಬೆಲ್ಲಾ |
| --- | --- | --- |
| Time || taɪm’ || ಟೈಮ್ |
| School || skul || ಸ್ಕೂಲ್ |
| Transformer || trænsˈfɔrmər || ಟ್ರಾನ್ಸ್ಫಒರ್ಮೆರ್ |
| Amazing || əˈmeɪzɪŋ || ಅಮೇಜಿಂಗ್ |
| Public || ˈpəblɪk || ಪಬ್ಲಿಕ್ |
| Beautiful || ˈbjutəfəl || ಬ್ಯೂಟಿಫುಲ್ |

所提模型在验证集上表现良好，准确率为 86.9%，针对给定数据集。随着清洗后的数据集规模扩大，模型可能会表现更好。

## Discussion
所提工作结合了基于词典的拼写检查工具和转写。拼写检查工具基于词典，模型的性能主要取决于词典的容量。只要词典不断增长，性能就会随之提升。这并非高效的做法；相反，如果模型理解语法规则，它就不依赖词典中的单词。这也是未来计划的工作。

卡纳达转写工具是高效的，因为它基于卡纳达语法的规则，未来还可以添加更多功能并向公众发布。

## Conclusion
所提工作结合了基于词典的拼写检查工具和转写。拼写检查工具基于词典，模型的性能主要取决于词典的容量。只要词典不断增长，性能就会随之提升。这并非高效的做法；相反，如果模型理解语法规则，它就不依赖词典中的单词。这也是未来计划的工作。

卡纳达转写工具是高效的，因为它基于卡纳达语法的规则，未来还可以添加更多功能并向公众发布。

## References
*   [Randhawa, Er, Sumreet, K., and Saroa, Er C. S.](#ch22.xhtml#R_ref22_1) (2014). Study of spell checking techniques and available spell checkers in regional languages: a survey. Int. J. Technol. Res. Engg., 2(3), 148–151.

*   [Chaudhuri, B. B.](#ch22.xhtml#R_ref22_2) (2002). Towards Indian language spellchecker design. Lang. Engg. Conf., 2002 Proc., 139–146.

*   [Priya, M. C., Shunmuga, D., Karthika, R., Ashok Kumar, L., and Lovelyn Rose, S.](#ch22.xhtml#R_ref22_3) (2022). Multilingual low resource Indian language speech recognition and spell correction using Indic BERT. Sādhanā, 47(4), 227.

*   [Gamu, D. T. and Michael, M. W.](#ch22.xhtml#R_ref22_4) (2023). Morphology-based spell checker for Dawurootsuwa language. Scientif. Prog., 2023.

*   Sampath, A. and Varadhaganapathy, S. (2023). Hybrid Tamil spell checker with combined character splitting. Concur. Computat. Prac. Exp., 35(1), e7440.

*   [Patil, K. T., Bhavsar, R. P., and Pawar, B. V.](#ch22.xhtml#R_ref22_6) (2021). Spelling checking and error corrector system for Marathi language text using minimum edit distance algorithm. Adv. Comput. Data Sci. 5th Int. Conf. ICACDS 2021, Nashik, India, April 23–24, 2021, Revised Selected Papers, Part I 5, 102–111. Springer International Publishing, 2021.

*   Priyadarshani, H. S., Rajapaksha, M. D. W., Ranasinghe, M. M. S. P., Kengatharaiyer, S., and Dias, G. V. (2019). Statistical machine learning for transliteration: Transliterating names between Sinhala, Tamil and English. 2019 Int Conf. Asian Lang. Proc. (IALP), 244–249.

*   [Khattar, N., Singh, J., and Sidhu, J.](#ch22.xhtml#R_ref22_8) (2020). An energy efficient and adaptive threshold VM consolidation framework for cloud environment. Wire. Per. Comm., 113, 349–367.

*   [Goyal, K. D., Muhammad, R. A., Vishal, G., and Yasir, S.](#ch22.xhtml#R_ref22_9) (2022). Forward-backward transliteration of Punjabi Gurmukhi script using n-gram language model. ACM Trans. Asian Low-Res. Lang. Inform. Proc., 22(2), 1–24.

*   [Manjunath, K. E., Dinesh Babu, J., Sreenivasa Rao, K., and Ramasubramanian, V.](#ch22.xhtml#R_ref22_10) (2019). Development and analysis of multilingual phone recognition systems using Indian languages. Int. J. Speech Technol., 22, 157–168.

*   [Arya, R., Singh, J., and Kumar, A.](#ch22.xhtml#R_ref22_11) (2021). A survey of multidisciplinary domains contributing to affective computing. Comp. Sci. Rev., 40, 100399, [https://doi.org/10.1016/j.cosrev.2021.100399](http://dx.doi.org/10.1016/j.cosrev.2021.100399).

*   Prakash, A. and Hema, A. M. (2022). Exploring the role of language families for building Indic speech synthesisers. IEEE/ACM Trans. Audio Speech Lang. Proc., 31, 734–747.

*   Priya, M. C., Shunmuga, D., Karthika, R., Ashok Kumar, L., and Lovelyn Rose, S. (2022). Multilingual low resource Indian language speech recognition and spell correction using Indic BERT. Sādhanā, 47(4), 227.

*   [Praveen, N. and Shashidhar, K.](#ch22.xhtml#R_ref22_14) (2022). Phoneme based Kannada speech corpus for automatic speech recognition system. 2022 IEEE Int. Conf. Distribut. Comput. Elec. Cir. Elec. (ICDCECE), 1–5.

*   Rudregowda, S., Sudarshan Patil, K., Gururaj, H. L., Vi-nayakumar, R., and Moez, K. (2023). Visual speech recognition for Kannada language using VGG16 con-volutional neural network. Acoustics, 5(1), 343–353.

# 23 Real-time identification of traffic actors using YOLOv7

Pavan Kumar Polagani^([^(23)](#fn23))

Velagapudi Ramakrishna Siddhartha Engineering College, Vijayawada, India

DOI: [10.1201/9781003471059-23](https://dx.doi.org/10.1201/9781003471059-23)

## Abstract

**Real-time traffic object detection is a key topic in computer vision, especially for improving traffic safety and management. This research describes a novel strategy for detecting traffic actors in real-time using YOLOv7, a cutting-edge deep learning system. Traditional computer vision algorithms, such as Single Shot Detector, R-CNN, and older versions of You Only Look Once (YOLO), frequently exhibit slow response times and poor accuracy in high-traffic areas. YOLOv7, an advanced object detection method based on convolutional neural networks (CNNs), is used in the proposed approach to address these difficulties straight on. YOLOv7 not only achieves real-time object detection, but also greatly increases accuracy by removing superfluous candidate boxes and employing a non-maximum suppression module to choose the best bounding boxes from overlapping ones. Furthermore, the spatial pyramid pooling block improves accuracy by enhancing the network’s receptive field without introducing additional parameters. In this study, we demonstrate the performance of our model under various driving scenarios, including clear and cloudy skies, varying lighting, occlusions, and noisy input data. This model detects traffic participants such as automobiles, pedestrians, cyclists, and traffic signs, which contributes to improved traffic safety and management.**

**Keywords: YOLOv7, traffic detection, convolutional neural networks**

## Introduction
