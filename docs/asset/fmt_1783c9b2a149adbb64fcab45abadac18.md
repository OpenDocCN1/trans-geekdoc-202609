
When using an attractor sound, two trigger zones can be created around the source object, sometimes called `proximity zone` and `activation zone` (Vazquez-Alvarez et al., 2016). Proximity zone is larger, activation zone smaller. When the participant enters the proximity zone, or is already inside it, the attractor sound is played—for example, a telephone ringing behind a door. If the participant keeps stationed for a set period of time or moves out of the zone, the sound may stop to allow further exploration or alternative progression of the narrative. However, if the participant decides to move closer to the sound, the activation zone gets triggered, and the actual content starts to play. The transition must, of course, be smooth and natural—unless the attractor sound can continue playing in the background with the content mixed on top of it. Behind the door, we may hear footsteps approach, someone pick up the telephone, and a conversation start.

Instead of using map-based trigger zones, sounds can be controlled based on the user’s distance to the object. This approach is an obvious choice when only proximity tracking is available but can also work effectively with absolute tracking systems. For instance, distance-based triggering is a built-in feature in most audio middleware.

Attractor sounds are useful in exploration-based scenes where the participant can hear sounds from around the surroundings—invitations to narratives—and decide which one to choose. However, in practice, such a scene may be challenging to balance and programme for at least two reasons:

1. The attractor sounds should be audible far enough for the participant to hear at least two of them simultaneously. If only one is heard, the user will likely go directly to that source, skipping the exploration phase. However, if multiple sounds are audible, there is a risk of cacophony, so attenuation curves must be adjusted carefully and the sounds selected and mixed with care.

2. The logic of handling the different attractor sounds and the narrative content found from their sources may get complicated. For instance, what if the user selects one attractor and starts to listen to the content, but has second thoughts and walks away? Should the narrative continue and be audible to the user, fade out and pause—or fade out, stop and rewind? Meanwhile, what happened to the other attractor sounds; did they disappear, or are they still active? Furthermore, if the scene has a time limit after which the next one begins, users who explore multiple sounds may not have enough time to finish listening to their chosen story. These are, of course, common challenges in developing interactive experiences and these are not unique to AAR.

### 9.13 Spatial scale and offset

- [调整衰减曲线](https://example.org)是声音设计中常用的技术，通常用于定义声音可以被听见的距离。这在某种程度上将个体听觉空间的规模从“自然”状态转变为人工状态。此外，还有其他一些方法可以调整听觉视角和尺度，并可能带来叙事效益。

#### 9.13.1 受控衰减曲线

衰减曲线可以进行调整，例如防止同时发出的声音重叠，确保某些声音只能在更近的距离内被听见，或让某些声音无论用户与它们的距离如何变化都保持不变。尽管受控衰减曲线使得虚拟声音违背物理规律，但结果可能提供一个更连贯且受控的声景，在其语境下对听众来说可能显得自然且可信（Cliffe，2022）。

曲线也可用于更具创意的目的。例如，“缩放”到远处声音源的概念就是一个典型例子。在 `Hyperkuulo` 中，参与者在某个时刻可以听到遥远公共桑拿的声音，仿佛它们离得更近。虽然这种效果可以通过多种技术实现，但彻底调整衰减曲线提供了一种简单且有效的解决方案。

Martínez-Cabrejas 等人 (2024) 提出一种 `方向衰减模型`，即只有用户正面朝向的声音会被听见，周围的声音则被衰减。该概念并非新颖，虽然它可以帮助用户专注于感兴趣的对象，但在实现时应格外谨慎：Armbruster (2024) 指出，在展览中，人们会不断转动头部和身体——可能在寻找朋友并请求倾听——过滤掉这些用户运动需要复杂的算法。

#### 9.13.2 缩放空间响应

在常规的 3DoF、6DoF 以及俯仰-偏航系统中，将头向右转 90 度会导致虚拟声景向左转 90 度，从而保持声音与现实世界对齐。然而，对于某些声音，降低空间响应可能是合理的：在 90 度的头部转动时，声音仅向右平移约 45 度（参见 Figure 9.4）。`Vienna Augarten` 体验中，靠近瓷器展品时触发声音描述，利用了这种 `缩放空间响应` 技术：叙述者的声音既不完全空间化到展品上，也不完全固定于头部，而是适度倾向于目标物体。这既保持了认知焦点在描述上，又保留了叙事与展品之间的空间关联。该技术同样可用于其他非 diegetic 声音，例如音乐。

![Figure 9.4Scaled spatial response](img/fig9_4.jpg)

Figure 9.4 缩放空间响应

#### 9.13.3 3DoF 声音

环境中的声音通常是 `allocentric`，即相对于环境的；而头部锁定的声音则是 `egocentric`，随听者的移动和头部朝向变化（Tsingos，2018）。但有时，让声音随用户移动同时保持头部追踪是有益的，从而利用三度自由度（3DoF）。Ambisonic 环境音有时采用这种 3DoF 附着方式，也可以将其应用于基于对象的音频源，例如通过在用户周围创建一个虚拟扬声器穹顶。该方法适用于移动自由度较大的移动应用及其他应用，且在叙事和声音设计上也有需求，例如在记忆场景中，真实环境被语境性地“淡化”到背景中。

#### 9.13.4 空间偏移

虚拟声音的空间坐标也可以相对于除真实环境或用户之外的其他实体进行定义。在现实生活中，飞机在天空中的声音常常滞后于其视觉位置，这是由于声音速度慢于光速造成的，从而产生空间偏移的错觉。相反，靠近的火车声可能听起来像是从轨道前方发出，伴随类似激光枪的效果。此类在 AAR 中使用的效果可以在叙事上暗示我们从不同的听觉视角感知世界——要么是从自身视角但带有偏移，要么是完全相对于另一参考系的视角。例如，在英国国家剧院的戏剧 `Anna` 中，佩戴耳机的观众通过放置在主角耳中的双耳麦捕捉的双声道音频，体验到舞台事件。虽然观众视觉上仍坐在座位上观看，但他们听到的听觉世界仿佛附着在演员的头上。类似的空间偏移也可出现在双声道音频步道中，如果参与者偏离预定节奏或路径。

飞机和火车的例子也可能暗示时间偏移，即听者在其他感官模式中听到的世界事件发生在之前或之后。虽然这些偏移在 AAR 中提供了有趣的可能性，但如果缺乏叙事正当性，它们同样可能被视为错误。

## 9.14 近场

`近场` 声音指距离听者头部非常近（通常小于一米）但仍然外部化、不在头内播放的声音。对许多用户而言，这些声音会触发一种往往被认为令人愉悦或强烈的身体反应，正如 ASMR 视频的流行所示。人声在近场中可能让人感到极度亲密，或根据情境和声音性质显得具有威胁性。

在 AAR 中，近场声音可以通过至少双声道系统来实现。将声音放置在用户视野之外——侧面、后方、上方或下方——可以营造出声音真实存在的错觉，即使不需要头部追踪，尤其是当声音像蚊子般持续移动，或像精神低语般随头部移动时。

在 `Séance` 中，近场声音被有力地使用。它们能够将感知从环境转移到“内脏空间”，即我们自身的私密、即时空间（Mann et al., 2023）。这种效果在音频增强现实（AAR）体验中进一步放大：虚拟声音几乎与现实难以区分，我们无法确定耳边的声音是否真实。

## 9.15 移除与替换

虽然对于 AAR 创作者而言，选择性移除声音的工具尚未完全成熟，但这将 undoubtedly 带来有趣的叙事可能性。正如前文讨论，声学干扰或令人不安的声音是挑战，可以通过自适应且选择性的降噪技术消除。此类技术有时被称为 `diminished audio`（Dam et al., 2024），并可能在更具创意的应用中发挥作用。

有意省略某物体的声音可以通过突出其沉默来成为叙事或情感手段。例如，音乐盒在听者靠近时可能突然变 silenc，象征脆弱或孤独。

- 前文讨论的消除扩展技术也可以在只移除选定的声音时受益，此外，人声可以被擦除并用脚本化的虚拟语音取代。这既打开了创造性的可能性，也带来了令人不寒而栗的数字欺骗前景，这已经在深度伪造视频（Arena et al., [2022; Turner, 2022）中出现过。

1. 由于 AAR 融合了虚拟与真实，两者之间的同步至关重要。每一次交互在某种意义上都是同步的实例。然而，这里指的是虚拟与物理世界在特别有意义的时刻短暂交汇的情形。叙事上有许多有趣的同步方式，这里简要讨论两种。

第一种方法紧密关联于 Chion’s (1994) 的 `synchresis` 概念，即声音与画面同时出现时会产生一种心理图像，通常在极短的时刻内发生。在 AAR 中，可以通过让真实世界控制虚拟音频事件，精准地将一个虚拟声音与单个瞬时的真实事件同步，从而实现两者的语境融合。例如，当墙面时钟敲响 12 点时，通过窗户听到的喧闹街道声 suddenly 会转变为宁静的自然声，象征一种释放或自由的时刻。

当真实事件不可预测且由真实物体（如他人、动物、自然等）引起时，同步会更有效。但实现这种同步的设计难度较大，需要先进的感官系统。

另一种做法是引导用户与虚拟音频同步。Rotozaza 的 `Etiquette` 是一部在真实咖啡馆举办的参与式戏剧，两位参与者佩戴耳机并接收行动指令。在某个时刻，其中一位参与者被提示在提示语 “One, two, three, now” 时将手指放在桌面上，此时手指触碰桌面，钢琴和弦响起（Rotozaza, 2015）。虽然该效果的成功依赖于参与者的配合，但它体现了与听觉主体同步行动的概念，正如 Janet Cardiff 的音频漫步以及 `Alcatraz Cellhouse Tour` 所示，形成了虚拟与物理世界之间的直接、具体的联系。

## 9.16 Synchronisation

Since AAR merges virtual and real, synchronisation between these two realms is essential. Every interaction in AAR is, in a way, an instance of synchronisation. However, here the concept refers to short, sparse moments where the virtual and physical worlds intersect in a particularly meaningful way. Narratively, there are many interesting approaches to synchronisation, two of which will be briefly discussed here.

The first approach is closely related to Chion’s (1994) concept of `synchresis`, where a mental image is created as sound and visuals occur simultaneously, typically within a brief moment. In AAR, this could be achieved by letting the real world control virtual audio events, precisely synchronising a virtual sound to a single, momentary real-world event in order to create a contextual fusion between the two. For example, when the dials of a wall clock strike 12 o’clock, the bustling street sounds heard through a window could suddenly shift to serene nature sounds, perhaps symbolising a moment of release or freedom.

Synchronisation would potentially be most effective when the real-world event is unpredictable and caused by a real object, such as other people, animals, nature, etc. However, implementing such synchronisation may be difficult to design and would require an advanced sensory system.
