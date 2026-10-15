
[Figure 2.7](#chapter02.xhtml#f2_7) 图 2.7 展示了这四个概念——侧向化、外向化、无声化和贴合声音——之间的关系。侧向化声音（在用户头脑内部播放）根据上下文可能是无声化或贴合的。例如，旁白通常被视为无声化，即没有实体来源，但我们听到它似乎来自头脑内部。然而，我们习惯于使用侧向化声音和头部声音的耳机聆听，因此倾向于认为声音存在于别处，无论是‘虚空’中，还是通过耳机或移动设备屏幕的‘魔力’或‘磁化’效果（参见 [第 4 章](#chapter04.xhtml)）。

![Figure 2.7Acousmatic and attached sounds as lateralised and externalised](images/fig2_7.jpg)

[Figure 2.7](#chapter02.xhtml#f2-7)Acousmatic and attached sounds as lateralised and externalised

## 2.12 六度自由

AAR 不仅涉及将虚拟声音嵌入现实世界，还涉及在环境中移动。移动能够增强存在感（Järvinen, [2017](#chapter02.xhtml#r28)），并且在双耳听声系统中，跟踪运动有助于虚拟声音的外向化，使其看起来像是与现实共存（Roginska, [2018](#chapter02.xhtml#r52); Brandenburg, et al., [2023](#chapter02.xhtml#r13)）。在 AAR 中，听觉显示是主要的 *输出* 界面，而移动通常是主要的 *输入* 界面；事件和交互是基于用户位置和运动触发的。

在 XR 世界中，“度自由”概念至关重要。它是指在给定空间中一个对象可能实现的不同运动（Paterson and Llewellyn, [2022](#chapter02.xhtml#r47)）。在 AAR 中，用户——即此例中的“对象”——很少受到物理限制而只能在环境中移动，度自由通常指系统跟踪用户头部并据此调整双耳听声虚拟声场的能力。

如果双耳听声应用是为始终保持头部正前方的静止用户设计的，虚拟声场可以在空间上固定，使用 0 度自由。如果用户保持静止，虚拟声音与现实共存的幻觉可能非常逼真，*Séance*（参见第 5.4 节）是一个很好的例子。在类似的应用中，若虚拟声音附着于左侧 2 米外的物体，那么声音会听起来像是来自该物体左侧 2 米处。然而，一旦用户转头，声场会随之转动，虚拟声音不再与该物体对齐。

为了让声场在转头时仍保持固定，系统应能够跟踪 *三度自由*（3DoF）。这里的三度指的是欧拉角中的方向，即旋转运动：俯仰、偏航和滚动。要实现 3DoF，用户的头部必须被传感器跟踪，这样当头部转动时，虚拟声场会相应旋转；虚拟声音便会看起来仍然贴合物体。

如果体验能够同时跟踪用户在空间中的移动和头部运动，则拥有 *六度自由*，即 *6DoF*（参见 [图 2.8](#chapter02.xhtml#f2_8)）。这三个额外度是欧几里得空间沿 x 轴（左右）、y 轴（前后）和 z 轴（上下）的平移运动（Mazuryk and Gervautz, [1999](#chapter02.xhtml#r37)）。此时，虚拟声场可以实时更新以匹配用户的移动，并看起来像是固定于环境中。

![Figure 2.8Six degrees of freedom (6DoF)](images/fig2_8.jpg)

[Figure 2.8](#chapter02.xhtml#f2-8)Six degrees of freedom (6DoF)

值得注意的是，术语 3DoF 有时也指平移运动——即沿 x、y、z 轴的移动——但这种用法在虚拟音频语境中较少见。

## 2.13 结论

AAR 可以被视为一套共享目标的多种技术与应用框架：增强对现实的感知与理解。这通过将虚拟听觉内容与环境融合、消除和替换声音、以及改善听觉来实现。本章介绍了一些与 AAR 相关的核心概念和术语，后续章节将继续引用。下一章探讨现实、沉浸感和互动性，为增强现实应用和体验奠定基础。

## 参考文献

1.  [Aalborg University](#chapter02.xhtml#re_ref7) (2024) ‘Audio Only VR for Blind Gamers’, Aalborg University’s Research Portal. Available at: [https://vbn.aau.dk/en/projects/audio-only-vr-for-blind-gamers](https://vbn.aau.dk/en/projects/audio-only-vr-for-blind-gamers) (Accessed: 3 December 2024).

2.  [Akın, A.T. and Cömert, Ç](#chapter02.xhtml#re_ref8). (2023) ‘The Development of an Augmented Reality Audio Application for Visually Impaired Persons’, Multimedia Tools and Applications, 82 (11), pp. 17493–17512. Available at: [https://doi.org/10.1007/s11042-022-14134-x](https://doi.org/10.1007/s11042-022-14134-x).

3.  [Albrecht, R., Väänänen, R. and Lokki, T.](#chapter02.xhtml#re_ref9) (2016) ‘Guided by Music: Pedestrian and Cyclist Navigation with Route and Beacon Guidance’, Personal and Ubiquitous Computing, 20 (1), pp. 121–145. Available at: [https://doi.org/10.1007/s00779-016-0906-z](https://doi.org/10.1007/s00779-016-0906-z).

4.  [Azuma, R.](#chapter02.xhtml#re_ref10) (1997) ‘A Survey of Augmented Reality’, Presence: Teleoperators and Virtual Environments, 6 (4), pp. 355–385. Available at: [https://doi.org/10.1162/pres.1997.6.4.355](https://doi.org/10.1162/pres.1997.6.4.355).

5.  [Azuma, R.](#chapter02.xhtml#re_ref11) et al. (2001) ‘Recent Advances in Augmented Reality’, IEEE Computer Graphics and Applications, 21 (6), pp. 34–47. Available at: [https://doi.org/10.1109/38.963459](https://doi.org/10.1109/38.963459).

6.  [Bach-y-Rita, P. and Kercel, S.W.](#chapter02.xhtml#re_ref12) (2003) ‘Sensory Substitution and the Human–Machine Interface’, Trends in Cognitive Science, 7 (12), pp. 541–546. Available at: [https://doi.org/10.1016/j.tics.2003.10.013](https://doi.org/10.1016/j.tics.2003.10.013).

7.  [Brandenburg, K.](#chapter02.xhtml#re_ref13) et al. (2023) ‘Implementation of and Application Scenarios for Plausible Immersive Audio Via Headphones’, in Audio Engineering Society Convention 155, Audio Engineering Society. Available at: [https://www.aes.org/e-lib/browse.cfm?elib=22308](https://www.aes.org/e-lib/browse.cfm?elib=22308) (Accessed: 25 November 2023).

8.  [Brandenburg, K. and Sloma, U.](#chapter02.xhtml#re_ref14) (2024) ‘Conversation with Matias Harju, May 23’.

9.  [Chion, M.](#chapter02.xhtml#re_ref15) (1994) Audio-Vision: Sound on Screen. Columbia University Press.

10.  [Choueiri, E.](#chapter02.xhtml#re_ref16) (2018) ‘Binaural Audio Through Loudspeakers’, in A. Roginska and P. Geluso (eds) Immersive Sound: The Art and Science of Binaural and Multi-Channel Audio. Routledge, pp. 124–179.

11.  [Cliffe, L.](#chapter02.xhtml#re_ref17) (2022) Audio Augmented Objects and the Audio Augmented Reality Experience. PhD thesis. University of Nottingham. Available at: [https://eprints.nottingham.ac.uk/69795/](https://eprints.nottingham.ac.uk/69795/).

