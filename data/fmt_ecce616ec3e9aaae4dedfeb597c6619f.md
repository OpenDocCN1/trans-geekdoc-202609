
在系统创建的第一阶段，我们专注于开发处理医学领域短语交流以及问答格式交互的系统。在初始阶段，我们避免了完全的对话式语音，因为不流畅、填充词和其他因素使其变得困难。问答语料库主要由患者提出并由医疗从业者回答的查询，以及医生基于病史和症状提出的问题和患者作出的回答组成。Table 4.2 显示了为此目的创建的语料库统计数据。

Table 4.2: 语音翻译系统的语料库规格。

| Corpus specifications |

| --- |

| **Speakers statistics** |

| --- |

| Male: 58 speakers || Age >18 years and <65 years |

| Female: 42 speakers || Age >18 years and <60 years |

| **Sentence style** |

| Question answer format: 500 sentences || Hindi: मुझे कौन सी दवाईयाँ लेनी हैं डॉक्टर? |

| English: Which medicines do I need to take doctor? |

| Phrasal sentences || Hindi: मुझे सांस लेने में तकलीफ हो रही है |

| English: I have difficulty in breathing. |

| **Sentence average length** |

| Question–answer format: 8 words/sentence || Phrasal sentences: 5 words/phrase |

| **Recording specifications** |

| Tool: `PRAAT`, Ver:3.9 || Recording parameters: 16 bit, 16 KHz, Mono |

语料库的一个特殊特征与医学术语有关。语料库中医学术语的频率较低，因为我们使用了医生-患者互动模式，更可能的是医生-患者对话会使用一般语言术语，而不是过度使用医学术语。

### 4.5.2 实验设置

系统的流水线架构从接收用于训练系统的输入的 `ASR` 模块开始。该系统的 `ASR` 模块是使用 `Sphinx3`，一种基于 HMM 的语音识别器构建的。`SphinxTrain` 模块提供了电话列表、映射词典、填充词词典、波形文件的音标转录以及语音录音文件。训练器使用这些文件学习参数，以及 `Sphinx` 的解码器，该解码器为测试输入生成最合适的词序列。双语 `MT` 模块是使用 `NLTK` 工具包构建的。该模块使用基于规则的翻译实现英语到印地语，使用基于示例的翻译实现印地语到英语。具有挑战性的 `TTS` 模块是使用 `Festival` 和 `Festvox` 框架构建的。为了产生类人语音，基于 HMM 的 `TTS` 模块接收 `MT` 产生的输入文本，并将音标表示进一步标记为韵律单元。`WaveSurfer` 在此级别用于手动对齐标签和音素。Figure 4.8 表示使用 `WaveSurfer` 对英语句子进行的手动标注。韵律单元用于为输入文本产生自然语音。整体架构要求为系统中使用的两种语言提供电话集列表。

![Figure 4.8: Manual segmentation and labelling using WaveSurfer showing power plot, formants, and pitch.](img/b_9783110648195-004_fig_008.jpg)

Figure 4.8: 使用 `WaveSurfer` 进行手动分段和标注显示功率图、共振峰和音高。

### 4.5.3 性能评估

翻译系统的每个组件都单独进行评估。由于系统的整体性能取决于流水线组件中每个单元的性能，因此我们单独评估了组件性能。此评估还有助于识别需要更多关注以进一步改进的组件。`ASR` 组件性能以 `WER%` 评估，该指标考虑了插入、删除和替换词的计数。`MT` 组件可靠性的性能使用 `METEOR` 判断，这是一种与人工评估高度相关的方法。它考虑了精确率和召回率，并对召回率赋予更大权重。`TTS` 组件使用感知测试进行评估。确定了十名听众，并为他们播放输入样本的语音合成器。他们被要求在三点量表上对样本进行评判，该量表范围从不清楚的语音、难以理解到可理解的语音。

随机选择的 30 个基于问答的样本和 50 个短语句子用于测试两种语言的数据。评估在六次迭代中进行，每次迭代的样本大小相同，样本选择均随机进行。Figure 4.9 展示了六次迭代中 `ASR`、`MT` 和 `TTS` 每个组件的性能。`ASR` 模块的平均 `WER` 为 0.6743，即 `ASR` 系统的平均准确率为 67.43%，印地语语音识别为 67.43%，英语为 72%。这种低性能可能归因于环境噪声，也可能归因于设备麦克风质量，因为录音使用的是手机。

![Figure 4.9: Performance of ASR, MT, and TTS subsystems in different iterations.](img/b_9783110648195-004_fig_009.png)

Figure 4.9: 不同迭代中 `ASR`、`MT` 和 `TTS` 子系统的性能。

机器翻译系统的平均性能得分为 0.6621；印地语到英语的正确翻译率为 66.21%，英语到印地语翻译为 64.32%。Figure 4.9 中的表示对应于印地语到英语的转换。Table 4.3 显示了对印地语语音合成器若干样本的用户感知。

Table 4.3: 用户对合成语音的感知，按 1（不清楚）到 3（可理解）的量表衡量。

| →Users ↓Sample || User 1 || User 2 || User 3 || User 4 || User 5 || User 6 || User 7 || User 8 || User 9 || User 10 |

| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

| Sample 1 || 2 || 1 || 2 || 2 || 1 || 2 || 1 || 1 || 1 || 2 |

| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |

| Sample 2 || 3 || 2 || 2 || 3 || 3 || 2 || 2 || 2 || 3 || 2 |

| Sample 3 || 2 || 2 || 3 || 3 || 2 || 2 || 1 || 2 || 2 || 3 |

| Sample 4 || 3 || 2 || 2 || 2 || 3 || 3 || 2 || 2 || 2 || 2 |

| Sample 5 || 1 || 1 || 1 || 2 || 1 || 1 || 1 || 2 || 2 || 2 |

印地语语音合成器的平均性能评分为 3 分制中的 2.03，而英语的性能在同一量表上评为 2.12。

## 4.6 结论

在本章中，我们讨论了医疗服务中的语言障碍。语音技术在消除语言障碍方面的重要性与必要性在此已得到阐述。我们在针对自动通信技术构建的医疗领域相关挑战方面进行了识别。不同领域中现有的语音转语音系统的简要综述在此已涵盖。综述的分析有助于找到借助语音技术克服语言障碍的方法，并推动医疗保健领域语音转语音系统的开发。进一步地，我们在此讨论了医疗服务中印地语到英语及反向的语音转语音翻译系统。系统的每个组件都单独进行了讨论，并描述了 `ASR-MT-TTS` 的流水线架构以减少语言障碍。对子组件的性能进行了单独分析。它表明我们的系统表现相当不错，通过改进每个组件的不足之处可以获得进一步的提升。`ASR` 可以变得更具抗噪性，并且可以通过利用输入文本的多个假设来增强 `MT` 性能。显而易见的是，未来语音技术的使用将变得必不可少，尤其是在医疗保健领域，以打破语言障碍。

## 4.7 未来展望

未来首要目标是提高现有系统的准确性。语音启用服务以数据为中心；因此，我们需要增加语音语料库的规模以提高准确率。除此之外，在现有系统中集成降噪算法也有助于提高系统性能。印度是一个多语言国家。将语音启用服务扩展到其他语言的人群，将使其更容易获得全球医疗保健服务。我们打算在医疗保健领域开发多语言语音翻译系统，该系统将涵盖更多印度语言以及其他国家可获得更好医疗保健服务的国家语言。语料库需要涵盖由于说话者社会和经济背景而产生的口音变化，以提高系统鲁棒性。

如今，手机的使用正在迅速扩展，已覆盖印度大部分农村地区。将系统扩展到手机上部署，将为农村地区的医疗保健领域提供有价值的服务。

## References

Antony, P J. Machine translation approaches and survey for Indian languages. International Journal of Computational Linguistics & Chinese Language Processing, (2013), 18(1), Mar. a, b

Arora, K., Arora, S., and Roy, M K. Speech to speech translation: a communication boon. CSI Transactions on ICT, (2013), 1(3), 207–213.Sep. 1. →

Banerjee, S., Lavie, A. METEOR: An automatic metric for MT evaluation with improved correlation with human judgments. In proceedings of the ACL workshop on intrinsic and extrinsic evaluation measures for machine translation and/or summarization, (2005) Jun. 65–72. →

Beutnagel, M., Conkie, A., Schroeter, J., Stylianou, Y., and Syrdal, A The AT&T next-gen TTS system. Joint Meeting of ASA, EAA, and DAGA, (1999), 15, 18–24, Mar. →

Bischoff, A., Bovier, P A., Isah, R., Françoise, G., Ariel, E., and Louis, L. Language barriers between nurses and asylum seekers: Their impact on symptom reporting and referral. Social Science & Medicine, (2003), 57(3), 503–512.Aug. 1. →

Bouillon, P., Gerlach, J., Spechbach, H., Tsourakis, N., and Halimi Mallem, I S. BabelDr vs Google Translate: a user study at Geneva University Hospitals (HUG), (2017). a, b

Casserly, E D., Pisoni, D B. Speech perception and production. Wiley Interdisciplinary Reviews: Cognitive Science, (2010), 1(5), 629–647.Sep. a, b

Doddington, G. Automatic evaluation of machine translation quality using n-gram co-occurrence statistics. In Proceedings of the second international conference on Human Language Technology Research (2002), Mar 24 (pp. 138–145). Morgan Kaufmann Publishers Inc. →

Dorr, B J., Jordan, P W., and Benoit, J W. A Survey of Current Paradigms in Machine Translation. In Advances in Computers, Jan. 1, (1999), 49, 1–68, Elsevier. →

Dua, M., Aggarwal, R K., and Biswas, M. Performance evaluation of Hindi speech recognition system using optimized filterbanks. Engineering Science and Technology, an International Journal, (2018), 21(3), 389–398. Jun. 1. →

Ehsani, F., Kimzey, J., Master, D., Sudre, K., and Park, H. Speech to speech translation for medical triage in Korean. In proceedings of the workshop on Medical Speech Translation (2006) Jun. 9 (pp. 13–19). Association for Computational Linguistics. a, b

Ettelaie, E., Gandhe, S., Georgiou, P., Knight, K., Marcu, D., Narayanan, S., and Belvin, R. Transonics: a practical speech-to-speech translator for English-Farsi medical dialogues. In proceedings of the ACL 2005 on interactive poster and demonstration sessions, (2005) Jun. 25 (pp. 89–92). Association for Computational Linguistics. a, b

Fassil, Y. Jul Looking after the health of refugees. Bmj, (2000), 321(7252), 57–59. →

Flores, G., Abreu, M., and Tomany-Korman, S C. Limited English proficiency, primary language at home, and disparities in children’s health care: how language barriers are measured matters. Public Health Reports, (2005), 120(4), 418–430. Jul. →

Heinze, D T., Turchin A., and Jagannathan, V. Automated interpretation of clinical encounters with cultural cues and electronic health record generation. In Proceedings of the First International Workshop on Medical Speech Translation, (2006) Jun, 20–27.

Jacobs, E A., Lauderdale, D S., Meltzer, D., Shorey, J M., Levinson, W., and Thisted, R A. Jul Impact of interpreter services on delivery of health care to limited-English-proficient patients. Journal of General Internal Medicine, (2001), 16(7), 468–474. →

Jilka, M., Syrdal, A K., Conkie, A D., and Kapilow, D A Effects on TTS quality of methods of realizing natural prosodic variations. InProc. ICPhS, (2003). →

Jing, Z., and Min, Z. Speech recognition system based improved DTW algorithm. In 2010 International Conference on Computer, Mechatronics, Control and Electronic Engineering, (2010) Aug 24 (Vol. 5, pp. 320–323). IEEE. →

Kathol, A., Precoda, K., Vergyri, D., Wang, W., and Riehemann, S. Speech translation for low-resource languages: The case of pashto. In Ninth European Conference on Speech Communication and Technology, (2005). a, b

Klatt, D H. Review of text-to-speech conversion for English. Journal of the Acoustical Society of America, (1987), 82(3), 793–857. →
