
## 使用深度学习进行视频标签化和分段

由于深度学习能够从复杂数据中发现复杂的模式，它最适合对视频进行智能分析并提取关键信息。然而，训练深度学习模型的一个常见挑战是训练数据集的可用性，这在许多情况下很难获得。另一个挑战是训练深度学习模型所需的较长训练时间。这些挑战可以通过利用迁移学习（Yosinski, 2014）来解决，该方法提供了使用相对较小的数据集和训练时间来重新训练预训练模型的可能性。迁移学习所用的思想是利用在一个训练任务中获得的知識用于另一个任务。

(Xu, 2015) 中提出的技术结合了卷积神经网络和循环神经网络用于视频字幕生成。循环神经网络的低级输出通过标签嵌入进行增强。后一步骤根据生成句子的相关性进行评分。然而，这一任务等同于视频翻译，并不专门执行标签预测。另一种视频标签化技术 (Xu, 2015) 提出了一种使用深度学习的事件本体，包括事件及其概念。所提出的技术通过开放的网络界面实现本体浏览、语义事件搜索和视频标签化。尽管这种方法看起来很有前途，但深度学习模型、训练和标签算法的细节大部分缺失。

### 表 2. 现有视频分段方法概述

| 技术 | 描述 | 局限性 |
| --- | --- | --- |
| 镜头聚类 | 基于镜头视觉相似性的镜头边界检测和聚类 | 无法分类的镜头。手工制作的特征。 |
| 动作识别 | 使用 SVM 训练的识别模型 | 工程化的图像特征 |
| 视听特征 | 寻找关键帧并使用其视听特征构建多个场景转换图 (STG) | STG 对低级视觉特征的利用。需要启发式设置某些 STG 参数。 |

Zhou 等人 (2017) 首先使用深度学习估算帧级标签来预测视频标签。CNN 输出通过可学习的池化函数融合，以预测视频级别的标签。这是第一个将帧级预测融合为视频级标签预测的深度学习视频标签化方法。尽管在这个过程中忽略了运动信息，但该技术在视频标签化方面很有效。然而，该算法仍未完全解决本章所讨论的问题。Ilyas 等人 (2019) 提出的另一种技术首先发现视频中的关键帧，并使用这些关键帧训练深度神经网络以生成最相关的标签。

本章作者提出的一项最新技术 (Khan, 2020) 同时解决了视频标签化和分段问题。开发了一种用于帧级分析的技术，最终通过融合和过滤信息生成视频级标签。使用迁移学习在代表 50 个标签词汇表的静态视频帧上重新训练深度学习模型。代替对所有帧运行推理，仅由关键帧检测算法选择具有代表性的帧。标签预测算法减少了标签之间的冗余性，并为所有标签分配分数。最后，选择具有最高分数的标签作为视频的代表性标签。标签预测算法生成的语料库包含视频镜头的开始和结束位置、每个镜头的单个标签以及关键帧。此信息用于根据预测的标签对视频进行分段。尽管该技术基本上是为视频标签预测和分段提出的，但它可以很容易地应用于其他类型的视频。标签词汇表是可扩展的，且可以通过极少努力重新训练深度学习模型以纳入更多标签。

## 局限性与约束

相关文献并未结合讨论本章中提出的问题，除了 Khan 等人 (2020) 提出的技术。然而，该技术也没有为标签预测整合运动信息。对于视频中快速变化且高度动态的场景，运动信息在准确预测场景方面起着关键作用。

使用机器学习进行标签预测的现有技术的另一个局限是它们对人工注释数据的依赖。这些数据并不总是严谨的专家分析的结果。例如，流行视频流媒体服务（如 YouTube）视频的元数据通常是草率分配的。这限制了算法的准确性，导致搜索结果和视频推荐不准确。由于众多上述任务依赖于准确的标签，视频标签预测需要高水平的准确性。

现有的视频分段技术主要通过首先找到镜头边界，然后基于其低级手工图像特征的视听相似性将镜头聚类到同一集群中来对视频进行分段。由于工程化图像特征存在已知问题，这些技术不能高效地分段视频。

## 潜在研究领域

使用深度学习的现有视频标签预测和分段方法可以在以下方面改进：

- 通过将长短期记忆 (LSTM) 模型与卷积神经网络集成，可以将运动信息纳入特征学习。LSTM 模型对学习时空信息很有用，预计能增强高度动态场景的预测准确性。
- 某些场景的准确预测还需要整合音频信息。例如，视频中的喜剧场景只有整合音频信息才能准确预测。LSTM 模型可用于学习音频特征以及视觉特征，以预测此类视频片段的标签。
- 公共视频数据库中可用的视频/视频脚本、评论或剧情可以进一步增加标签预测准确性。这些信息是仔细编写的，通常经过数据库管理员审查。因此，它可用于进一步提高标签预测准确性。
- YouTube-8M 数据集包含 800 万个视频的视觉特征。该数据集可自由用于训练视频分类算法。该数据集可用于开发比 Khan 等人 (2020) 构建的更大且类似的标签词汇表。使用类似于 Khan 等人 (2020) 开发的技术，可以开发一种视频标签化和分段算法，能够更准确地预测视频标签并涵盖更广泛的视频主题。

## 结论

本章回顾现有的视频标签预测和分段技术。回顾显示，现有的视频标签化技术在很大程度上依赖于人工注释数据和/或没有完全解决本章中表述的问题。同时，视频分段技术主要依赖于存在已知问题的手工图像特征。结论是，此任务只能通过机器学习技术有效执行。更准确地说，基于深度学习的技术在此背景下最能实现更高的效能。此外，本章还表明将视频标签预测与分段结合具有诸多优势，应结合研究。视频标签化和分段相关的问题被强调，并描述了改进的潜在研究领域。

## 参考文献

Acharya, S. (2012). U.S. Patent No. 8,098,976. Washington, DC: U.S. Patent and Trademark Office.

Antol, S., Agrawal, A., Lu, J., Mitchell, M., Batra, D., Lawrence Zitnick, C., & Parikh, D. (2015). Vqa: Visual question answering. In Proceedings of the IEEE international conference on computer vision (pp. 2425-2433). IEEE.

Aradhye, H., Toderici, G., & Yagnik, J. (2009, December). Video2text: Learning to annotate video content. In IEEE International Conference on Data Mining Workshops (pp. 144-151). IEEE.

Baber, J., Afzulpurkar, N., & Bakhtyar, M. (2011). Video segmentation into scenes using entropy and SURF. In 7th International Conference on Emerging Technologies (pp. 1-6). 10.1109/ICET.2011.6048496

Baber, J., Satho, S. I., Afzulpurkar, N., & Keatmanee, C. (2013, August). Bag of visual words model for videos segmentation into scenes. In Proceedings of the Fifth International Conference on Internet Multimedia Computing and Service (pp. 191-194). 10.1145/2499788.2499814

Boccignone, G., Chianese, A., Moscato, V., & Picariello, A. (2005). Foveated shot detection for video segmentation. IEEE Transactions on Circuits and Systems for Video Technology, 15(3), 365–377. doi:10.1109/TCSVT.2004.842603

Bredin, H. (2012, March). Segmentation of TV shows into scenes using speaker diarization and speech recognition. In IEEE International Conference on Acoustics, Speech and Signal Processing (ICASSP) (pp. 2377-2380). 10.1109/ICASSP.2012.6288393

Charniak, E. (2019). Introduction to deep learning. The MIT Press.

