

存在多种语音合成方法，可分为发音合成、共振峰合成或拼接合成。首先，在这些方法中，发音语音合成基于生物力学模型，该模型负责在人类中启动语音信号。发音合成器模仿发音器官（舌头、嘴唇、声门和VT）的影响。这种再现是三维微分方程，其随时间变化并计算人工语音输出。这类模型的主要要求是拥有极高的计算资源。此外，这些模型产生的输出并不能产生流畅的语音且缺乏自然性（[Beutnagel et al., 1999](#bodymatter-004.xhtml#b_9783110648195-004_ref_004)）。共振峰语音合成包括源-滤波器模型，其基于源（声门）和滤波器可以独立处理的假设（[Jilka et al., 2003](#bodymatter-004.xhtml#b_9783110648195-004_ref_016)）。滤波器的作用基于带宽和共振峰频率。共振峰合成方法的优点是它只需要适中的计算资源即可生成极易理解的语音，尽管它并不能产生完全自然的语音。最后一种方法是拼接语音合成使用最小尺寸的语音单元，称为音素。音素在无噪声的环境中录制以开发语音数据库。这些录制的音素可以作为波形存储，或以合适的语音编码算法获得的编码信号形式存储。这种方法产生的语音使用实际声音的录制基本单元；因此，该方法具有生成自然语音的最高潜力（[Klatt, 1987](#bodymatter-004.xhtml#b_9783110648195-004_ref_019)）。

`HMM` 是模拟任何过程观察行为的最常见技术之一。`HMM` 的这种能力也用于在语音技术中建模人类语音行为。该模型在两个阶段工作。在第一个阶段，称为训练阶段，`HMM` 学习语音的声学-韵律方面。随后，在第二阶段，即语音生成阶段，`HMM` 提取待合成文本最可能的<|message|> 参数。`HMM` 可以通过两种不同的方式进行训练；第一种，使用单个说话人约 2–4 小时的长语音语料库；第二种，自适应训练方法，需要来自多个说话人的语音样本并将其适应特定说话人的语音特征。这种方法只需要少量语料库即可合成语音。不管采用哪种方法，在训练阶段 `HMM` 都使用语音语料库，其扩展以覆盖上下文依赖性的音标转写，以及标记的音素边界。诸如 `MFCC` 和音高及其导数等语音特征从波形中提取。在这些参数的帮助下，`HMM` 学习频谱和激励参数。[Figure 4.7](#bodymatter-004.xhtml#b_9783110648195-004_fig_007) 展示了基于 `HMM` 的语音合成器训练。

![Figure 4.7: HMM-based speech synthesizer training module.](graphic/converted/b_9783110648195-004_fig_007.png)

Figure 4.7: `HMM`-based speech synthesizer training module.

训练完成后，语音生成过程开始。该过程需要待朗读文本的音标转写和上下文相关标注。`HMM` 从状态持续时间密度函数中提取的音素持续时间创建频谱和激励参数。合成语音由此类参数获得。为了获得高质量的语音，应用混合激励模型。`Gnuspeech`、免费 `TTS` 和 `Festival Speech Synthesis system` 是可用于构建 `TTS` 系统的几个工具。

## 4.4 Performance evaluation

`TTS` 系统可以在多个方面进行评估。根据构建系统的目的，选择评估指标。`TTS` 系统的性能可以通过与语音质量相关的平均意见评分（`MOS`）来衡量，以评估自然度。评估的第二个参数是系统的可懂度，其以 `MOS` 或 `WER` 衡量。除此之外，准确性和可理解性也是评估 `TTS` 系统的其他指标。

## 4.5 Addressing language barriers in healthcare

语言障碍被认为是全球化中最主要的障碍之一。解决该障碍的必要性在医疗领域更为迫切。印度人口向世界其他地区迁移的现象十分普遍，且日渐增加。并非所有移出国境的人都受过教育，只能用其母语交流。另一方面，大多数国家都有自己的语言或使用英语作为交流媒介之一。印度也使用英语作为官方语言之一，但比例上受教育程度不高的人口无法用英语交流。为克服这一语言障碍，需要在印度语言和英语之间进行语音翻译。已有若干努力（[Vemula et al., 2010](#bodymatter-004.xhtml#b_9783110648195-004_ref_026)）朝此方向进行，但大多数集中在旅游领域。医疗设施作为最关键和最需要的设施之一，需要研究界的关注。全球范围内已开始研究以克服医疗服务中的语言障碍（[Ettelaie et al., 2005](#bodymatter-004.xhtml#b_9783110648195-004_ref_012)；[Ehsani et al., 2006](#bodymatter-004.xhtml#b_9783110648195-004_ref_011)）。医疗领域的 `S2S` 系统将有助于在中东国家以及其他发达国家寻求最佳医疗服务的印度移民。

基于语音技术的系统是高度数据驱动的系统，其成功主要取决于相关语言和领域数据库中可用的语料库（[Kathol et al., 2005](#bodymatter-004.xhtml#b_9783110648195-004_ref_018)）。本节介绍一个 `S2S` 翻译系统，可用于印地语到英语的翻译，反之亦然。印地语是一种资源匮乏的语言，创建此类系统并非易事，主要原因是缺乏数据，尤其是在医疗领域。对医疗领域工作的分析表明，使用语音技术的医疗/健康护理领域应用可分为不同类别：

* Dictation systems: Mainly used by doctors to provide notes to nurses/receptionists.
* Interactive systems: These voice-enabled systems are used to handle the interaction between patients and caretakers, patient and doctor, or patient and receptionists for making an appointment.
* Command and control systems: Generally used for controlling medical equipment.
* Language interpretation systems: These systems are mainly used to reduce the language barrier by providing translation services to the communication partners of different languages.

