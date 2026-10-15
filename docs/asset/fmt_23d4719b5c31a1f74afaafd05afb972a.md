
60 或 50 毫秒（ms）以下的延迟通常在大多数虚拟音频场景中被认为是不可见的，而低于 30 ms 则几乎不可见（Brungart, Kordik and Simpson, [2006; Brandenburg et al., 2023]）。实际上，这些数值可以在跟踪系统非常快速（如 `OptiTrack` 或 `VIVE Tracker`）、音频渲染优化良好并在功率强大的计算机上运行且缓冲区很小、尽可能多的连接均为有线的情况下实现。然而，许多 AAR 应用无法在如此高的规格下运行。例如，即使使用 IMU 跟踪器进行头部朝向跟踪相对快速（延迟 10 ms，Supper, 2021），位置跟踪系统可能引入超过 100 ms 的延迟。好在头部朝向跟踪通常比位置跟踪更为关键，而快速位置跟踪仅在虚拟声音贴近时才变得重要。

音频渲染会增加额外延迟，如第 7.3 节所述。复杂的听觉场景对计算机和软件的要求更高，通常导致更大的音频缓冲区和更高的延迟。最后，如果需要向耳机进行无线音频传输，则可能引入显著延迟。专业无线系统可实现低于 1 毫秒的延迟。一些低延迟蓝牙编码（如 `aptX LL` 和 `LHDC LL`）的延迟为 30–40 ms，而标准蓝牙编码则可能超过 200 ms，这会显著影响用户体验（Katz, 2024）。综上，若系统能将运动到声音的延迟控制在约 100 ms，这在保持可信度方面已算相当不错（Lindau, 2009）。

听觉“远程效应”（ventriloquism effect），即虚拟声音“磁化”到可信的物理物体上，可以弥补部分动态错误（见 Ahrens, 2019）。但实际经验表明，这种容忍度有限，声音不能偏离太大。如果跟踪不稳定且虚拟声音在物理物体周围漂移，幻觉更容易破裂。

## 7.8 完整系统和标准

目前尚无法购买完整的 6DoF AAR 系统，至少在作者所知范围内，只有少数由制作 AAR 内容的公司研发的专有系统。然而，这些系统同样不完整：尽管它们在技术上设计得周到且可靠，但作者管道或跟踪系统仍可能依赖第三方工具和复杂的工作流。

部分解决方案已或将会可供购买，而第一个交互式沉浸式音频标准 `MPEG-I` 预计将在本书出版时于 2025 年发布。该标准由多家公司共同开发，旨在统一并稳定各设备上的音频渲染。它支持 6DoF 音频场景，兼容双耳耳机和扬声器设置。`MPEG-I` 具备可扩展性，能够为处理能力有限的移动设备优化渲染分辨率。它基于 `MPEG-H` 编码，支持通道式音频、对象式音频（OBA）以及更高阶麦克风阵列（HOA），并引入多点 HOA（Herre et al., 2024）。在 AAR 方面，一个重要特性是可以输入参数（如房间混响时间 RT60），以匹配虚拟声学与真实环境（Herre and Disch, 2023）。

另一项最近发布的标准和 codec `IVAS` 尤其值得关注。它由多家电信和技术公司联合开发，能够通过单个移动设备即兴捕获空间听觉场景（如会议桌周围的人），并且可以在终端设备上对每位参与者的远程音频流进行空间化（Bruhn, Multrus and Varga, 2022; IVAS Codec Public Collaboration Contributors, 2023）。

尚需观察这些标准将被硬件和软件公司多广泛采用，它们能否简化并统一生产流程，以及是否能实现无缝的跨平台内容分发。尽管如此，它们的存在已反映出虚拟和空间音频在行业中的重要性日益被认可。

## 7.9 结论

实现 AAR 的可能技术种类看似繁多，选择正确的方案始终是一项充满挑战的过程，且测试某一技术往往需要投入金钱和时间，最终可能发现它并非最佳选择。除地理定位 AAR 平台外，缺乏面向内容创作者的现成完整系统，可能会延缓创意落地。本章希望为从业者提供选型指导，帮助其在项目中精准选择组件，减少重复试错，同时展望 AAR 技术的潜力与机遇。

## 参考文献

1. Ahrens, A. 等 (2019) ‘Sound Source Localization with Varying Amount of Visual Information in Virtual Reality’，PLOS ONE, 14 (3), p. e0214603。Available at: [`doi.org/10.1371/journal.pone.0214603`](https://doi.org/10.1371/journal.pone.0214603)。

2. Albrecht, R., Lokki, T. and Savioja, L. (2011) ‘A Mobile Augmented Reality Audio System with Binaural Microphones’，in Proceedings of Interacting with Sound Workshop: Exploring Context-Aware, Local and Social Audio Applications. New York, NY, USA: Association for Computing Machinery (IwS ’11), pp. 7–11。Available at: [`doi.org/10.1145/2019335.2019337`](https://doi.org/10.1145/2019335.2019337)。

3. ALPS (2018) ‘ALPS – Acoustic Localisation Positioning System’。Available at: [`alps.fi/`](https://alps.fi/) (Accessed: 26 November 2024)。

4. Amfitech (2024) ‘AMFITRACKTM, AmfiTrack’。Available at: [`www.amfitrack.com`](https://www.amfitrack.com) (Accessed: 26 November 2024)。

5. Arena, F. 等 (2022) ‘An Overview of Augmented Reality’，Computers, 11 (2), p. 28。Available at: [`doi.org/10.3390/computers11020028`](https://doi.org/10.3390/computers11020028)。

6. Armbruster, S. (2024) ‘Conversation with Matias Harju, March 7’.

7. Bederson, B.B. (1995) ‘Audio Augmented Reality: A Prototype Automated Tour Guide’，in Conference Companion on Human Factors in Computing Systems – CHI ’95. Denver, Colorado, United States: ACM Press, pp. 210–211。Available at: [`doi.org/10.1145/223355.223526`](https://doi.org/10.1145/223355.223526)。

8. Bimber, O. and Raskar, R. (2005) Spatial Augmented Reality: Merging Real and Virtual Worlds. Wellesley, Massachussets: A K Peters.

9. Boquet, G., Vilajosana, X. and Martinez, B. (2024) ‘Feasibility of Providing High-Precision GNSS Correction Data Through Non-Terrestrial Networks’, IEEE Transactions on Instrumentation and Measurement, 73, pp. 1–15。Available at: [`doi.org/10.1109/TIM.2024.3453319`](https://doi.org/10.1109/TIM.2024.3453319)。

10. Brandenburg, K。et al. (2023) ‘Implementation of and Application Scenarios for Plausible Immersive Audio Via Headphones’，in Audio Engineering Society Convention 155, Audio Engineering Society。Available at: [`www.aes.org/e-lib/browse.cfm?elib=22308`](https://www.aes.org/e-lib/browse.cfm?elib=22308) (Accessed: 25 November 2023)。

11. Bruhn, S., Multrus, M. and Varga, I. (2022) ‘IVAS – 将 3GPP 语音和音频服务提升至新的沉浸式水平’, 3GPP Highlights, 十月, 第 8–9 页。

12. Brungart, D., Kordik, A.J. and Simpson, B. (2006) ‘头部跟踪延迟在虚拟音频显示中的影响’, Audio Engineering Society Journal, 54, 第 32–44 页。

13. Buttle, P. (2020) ‘视频游戏背后的力量：看看游戏引擎’, Medium。可在: [`medium.com/wetheplayers/the-power-behind-video-games-a-look-at-game-engines-2731315086e0`](https://medium.com/wetheplayers/the-power-behind-video-games-a-look-at-game-engines-2731315086e0) (访问日期: 2021 年 5 月 3 日)。

14. Dardari, D., Closas, P. and Djurić, P.M. (2015) ‘室内定位：理论、方法和技术’, IEEE Transactions on Vehicular Technology, 64 (4), 第 1263–1278 页。可在: [`doi.org/10.1109/TVT.2015.2403868`](https://doi.org/10.1109/TVT.2015.2403868)。

15. Doheny, E.P. et al. (2023) ‘利用智能手机麦克风录制的音频信号估计呼吸频率和呼气时长’, Biomedical Signal Processing and Control, 80, 第 104318 页。可在: [`doi.org/10.1016/j.bspc.2022.104318`](https://doi.org/10.1016/j.bspc.2022.104318)。

16. Engel, J.I. and Picinali, L. (2017) ‘长期适应音频增强现实系统’, in Institute of Acoustics Proceedings. ICSV24 2017, London。可在: [`www.ioa.org.uk/catalogue/paper/long-term-user-adaptation-audio-augmented-reality-system`](https://www.ioa.org.uk/catalogue/paper/long-term-user-adaptation-audio-augmented-reality-system)。

17. Fernandez-Hernandez, I. et al. (2018) ‘伽利略高精度：从方案和政策的角度看', in 69th International Astronautical Congress, Bremen, Germany.

18. Gampe, J. (2009) ‘交互式音频增强现实中的叙事’, in I.A. Iurgel, P. Petta, and N. Zagalo (eds) Interactive Storytelling. Berlin, Heidelberg: Springer Berlin Heidelberg (Lecture Notes in Computer Science), 第 298–303 页。可在: [`doi.org/10.1007/978-3-642-10643-9_34`](https://doi.org/10.1007/978-3-642-10643-9_34)。

19. Geng, J., Huang, D. and Torre, F.D. la (2022) ‘DensePose 从 Wi‑Fi 中获取', arXiv。可在: [`doi.org/10.48550/arXiv.2301.00250`](https://doi.org/10.48550/arXiv.2301.00250)。

20. Greenwald, W. (2024) ‘2024 年最佳智能眼镜', PCMag UK。可在: [`uk.pcmag.com/wearables/150162/the-best-smart-glasses-for-2024`](https://uk.pcmag.com/wearables/150162/the-best-smart-glasses-for-2024) (访问日期: 2024 年 10 月 25 日)。

21. Hatala, M. and Wakkary, R. (2005) ‘基于本体的用户建模在博物馆增强音频现实系统中', User Modeling and User-Adapted Interaction, 15 (3), 第 339–380 页。可在: [`doi.org/10.1007/s11257-005-2304-5`](https://doi.org/10.1007/s11257-005-2304-5)。

22. Herre, J. and Disch, S. (2023) ‘MPEG‑I 沉浸式音频 – 虚拟/增强现实音频标准的参考模型', Journal of the Audio Engineering Society, 71 (5), 第 229–240 页。可在: [`doi.org/10.17743/jaes.2022.0074`](https://doi.org/10.17743/jaes.2022.0074)。

23. Herre, J. et al. (2024) ‘MPEG‑I 沉浸式音频：一种高效的 VR/AR 音频表示方式，超越点源渲染', in. 2024 AES 6th International Conference on Audio for Games, Tokyo, Japan: Audio Engineering Society。可在: [`aes2.org/publications/elibrary-page/?id=22400`](https://aes2.org/publications/elibrary-page/?id=22400)。

24. HTC (2023) ‘VR 跟踪器和虚拟现实跟踪概述 – VR 101: 第三部分'. 可在: [`blog.vive.com/us/tracking-in-virtual-reality-and-beyond-vr-101-part-iii/`](https://blog.vive.com/us/tracking-in-virtual-reality-and-beyond-vr-101-part-iii/) (访问日期: 2024 年 11 月 27 日)。

25. Härmä, A. et al. (2004) ‘移动和可穿戴设备的增强现实音频', Journal of the Audio Engineering Society, 52 (6), 第 22 页。

26. Italiano, L. et al. (2024) ‘5G 定位教程', IEEE Communications Surveys & Tutorials, 第 1 页。可在: [`doi.org/10.1109/comst.2024.3449031`](https://doi.org/10.1109/comst.2024.3449031)。

27. IVAS Codec Public Collaboration Contributors (2023) ‘IVAS 编码器用于 NG 3GPP 语音和音频服务', 十月, 第 18–19 页。

28. Jacuzzi, G. (2018) ‘“增强音频”：创建 AR 音频体验所需的独特工具和功能概述', in International Conference on Audio for Virtual and Augmented Reality, Redmond, WA, USA: Audio Engineering Society, 第 8 页。

29. Katz, L. (2024) ‘了解蓝牙编码', SoundGuests。可在: [`www.soundguests.com/understanding-bluetooth-codecs-15352/`](https://www.soundguests.com/understanding-bluetooth-codecs-15352/) (访问日期: 2024 年 10 月 18 日)。
