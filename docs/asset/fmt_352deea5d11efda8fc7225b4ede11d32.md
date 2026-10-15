
这为 `地理定位 AAR`（位置感知音频）的实现提供了可能，使用户能够创建、分享并享受嵌入环境的内容。在地理定位 AAR 中，专用软件平台用于将音频文件绑定在地图上的“地理围栏”区域。当携带移动设备并佩戴耳机的用户进入其中一个区域时，相应的声音会被播放。地理定位应用大致分为两类：1）多作者社交应用，用户可自行录制声音并放置在地图上，供其他用户后续发现；2）音频漫步或音频步道，通常针对特定场景，由单一创作者制作。

![Figure 5.5A geolocated audio walk made and shared on Echoes with geofenced trigger areas ¶ Source: A screenshot from the Echoes iOS app](img/fig5_5.jpg)

Figure 5.5A geolocated audio walk made and shared on `Echoes` with geofenced trigger areas ¶ Source: A screenshot from the Echoes iOS app

### 5.6.1 Multi-authored apps

最早的 GPS 依赖 AAR 实验之一是 `Hear&There`，在 MIT Media Lab 原型阶段由 `Rozier`、`Karahalios` 和 `Donath` 于 2000 年完成 (`2000)。与 Bederson 的概念类似，它强调社交属性，探索一种平台，使用户能够在校园范围内留下个人的听觉“印记”，并发现他人留下的印记。通过超越近距离传感器，利用 GPS 可将声音定位于用户希望的任意位置，为未来的位置感知音频应用打开了广阔的可能性。`Hear&There` 还能够追踪用户的头部朝向，实现 XY-Yaw（俯仰）度的声音空间化（见第 2.12 章），这一特性在当今地理定位体验中仍属稀有。

随后，公开的地理定位声音分享平台 `Roundware` 于 2008 年面向公众发布，至今仍在使用，是最早的平台之一 (`Burgund`, 2024)。此后出现了诸多其他平台，但大多寿命短暂。此类格式可能因缺乏连贯内容和与他人互动而导致进入门槛较高，难以激励用户前往现场聆听信息和声音。

### 5.6.2 Single-authored apps

单作者地理定位体验同样受欢迎，通常体现为音频漫步或音频步道，由多种移动应用和平台支持，使用户能够编辑并共享基于地图的音频内容，并在用户定位进入相应区域时自动触发播放。2010 年代期间陆续推出的平台包括 `NoTours`（2010）、`SonicMaps`（2012）、`Echoes`（2013）、`Soundtrackcity`（2013）以及 `U-Gruve`（2016）。在编辑阶段，这些应用提供用户预设工具，用于在地图布局上绘制“地理围栏”区域并为其分配音频片段。运行时，声音根据用户在区域内外的移动进行控制，有时甚至在区域内部。

地理定位音频常被独立艺术家和文化机构用于分享特定场所的记忆、戏剧、诗歌和音乐。部分平台提供商，如 `Echoes`，还会基于其技术框架制作定制经验和专属应用 (`Kopeček`, 2024)。除了音频步道，基于相同原则的互动旅游音频导览也应运而生。

此外，除了步行，任何移动方式 —  — 包括汽车、自行车、水上交通工具等 —  — 都可以创作地理定位内容。近期，`The Sonic Bike` 项目使用自行车装配扬声器，实现地理定位音乐与声艺 (`Bicrophonic Research Institute`, 2024)。`Audio Nomad`（`Woo` 等，2006）通过周围扬声器增强海景声景。`Autio`（由演员 Kevin Costner 联合创办）提供高制作水准的地理定位故事，主要面向汽车旅行者。尽管卫星导航限制了户外体验，但部分平台提供粗粒度的室内定位，如 `Echoes` 支持通过蓝牙低功耗（BLE）技术的 iBeacon 实现室内近距离交互。

### 5.6.3 Geolocated experiences

`Hyperkuulo`（意为“超听”）是一个基于 `NoTours` 平台的交互式漫步，值得一提。该漫步于 2013 年 4 月在芬兰坦佩雷（Tampere）推出，由 Ari Koivumäki 与坦佩雷应用技术大学的学生团队共同发起（2018)。漫步的叙事围绕一次带有听觉增强植入物的科学实验展开，耳机在故事中贯穿始终，将所有声音视为实验的一部分，并部分豁免了头戴式音频的局限。场景设在公园中，用户需要完成一系列任务，如逆时针绕泉花走动并哼唱“omm”，或在户外乐队台上制造回响。由于听觉敏感度提升，用户甚至能听到草木生长、远处桑拿房中的人在洗澡的声音，以及过去与未来的声音。随着用户到达指定地点，叙事会自动推进，但由于缺乏动作验证传感器，系统仅依赖用户自愿遵循指示，以保持一种虚假的主体性感（参见 `Fendt` 等，2012)。

Whereas `Hyperkuulo` was site-specific, `The Planets` (Sofilab, 2023) is an example of a transferable geolocated application. It is available in multiple urban parks around the world, authored remotely using `Google Maps` (Nitschke, 2022). The listener, equipped with a mobile phone and headphones, assumes the role of a spaceship pilot and navigates from planet to planet by walking within the park, guided by a binaurally rendered sound signal. Each planet, or designated area in the park, features the corresponding movement from Gustav Holst’s orchestral suite `The Planets`, played back as spatialised acousmatic instrument groups. While `The Planets` is set in a real-world environment and its primary interaction mode is physical movement within that space, the content itself lacks a direct contextual relationship with the surroundings. This forces listeners to actively interpret and construct their own connections between the space theme, the music, and the urban park.

## 5.7 AAR games

AAR games are a niche genre, but nevertheless, remain an interesting platform for studying interactivity and immersion in an audio augmented environment. They differ from audio games by bringing gameplay and stories physically to the real world, letting the player interact with the game kinaesthetically, and interact with the reality through the game.

### 5.7.1 Environmental relationship

Some of the earliest AAR games used the real environment merely as a platform for walking and thus interacting with the game, not unlike `The Planets`. For instance, `Guided by Voices` (Lyons, Gandy and Starner, 2000), a prototype developed at the Georgia Institute of Technology, USA, immersed the player into a fantasy world through virtual sounds without any narrative relationship with the real environment. Gameplay was based on making decisions in the acoustic fantasy world by physically moving between several locations within the real space, which could be an office, yard, or any other place. Despite the obvious incongruence between the real and virtual worlds, the movement reportedly aided in players’ immersion in the game. The game also fostered social interaction as multiple people could play it simultaneously in the same space.

A more recent AAR game prototype, `Sound PacMan` (Chatzidimitris, Gavalas and Michael, 2016), was, on the other hand, completely based on the user’s environment. The gameplay followed the idea of the original `Pac-Man`, but transformed the user’s local street network into the game’s maze; the player’s objective was to traverse along the real-world streets and eat ‘cookies’ while avoiding the pursuing ghosts that were also following along the same streets. Both cookies and ghosts were denoted by virtual sounds. The ubiquitous and adaptive nature of the game fundamentally leveraged the unique nature of AAR as a layer to reality, even if the contextual connection between the game characters and the local streets may have remained vague.

In contrast, the narrative connection with the environment was strong with `Audio Legends` (Rovithis et al., 2019; Moustakas et al., 2020), playable in 2018–2019. It was a site-specific outdoor game created by researchers at the Ionian University in Greece, and based on the folklore of the island of Corfu. The player’s task was to protect the island by escorting a sailor carrying wheat to the town’s entrance, locating and fighting ‘the monsters of plague’, and blocking incoming cannonballs (Rovithis, 2024). The real environment was utilised by embedding gameplay elements in the appropriate real-world surroundings, such as enemy gunships on the sea. The game also explored the use of gestures as an interaction mechanism within AAR: for instance, the user had to move the mobile device as if it were a shield to block the acousmatic cannonballs. The authentic environment and the contextual links between it and the story seem to have played a significant role in making the game feel immersive to the players (Rovithis et al., 2019).

`Zombies, Run!` takes an interesting approach to the user’s environment. Released in 2012, this AAR application immerses the user in a zombie narrative set in their own neighbourhood. As Runner Five, one of the few survivors, the user must run and evade zombies while completing game-like tasks to save the community. The user can listen to their own music playlist on a mobile device, which is, every now and then, interrupted by a ‘radio transmission’ where the protagonists talk to the user. The application also features Radio Mode that augments the listener’s music playlist with virtual radio broadcasts, creating an interesting layered reality discussed in Chapter 3.1.

The application does not attempt to embed virtual sounds in the environment other than with some general ambiences. In fact, location tracking is not utilised, meaning the system has no awareness of the user’s whereabouts or the nature of their surroundings. Instead, the gameplay relies on the user’s pace, with elements like randomly occurring chases where zombies’ breathing and drooling can be heard behind the user, prompting them to speed up for a minute to evade capture. Without head tracking, the app assumes users predominantly look forward while running. Despite not knowing the user’s surroundings, the dialogue references generic landmarks and directions (‘hospital’, ‘old mill’, ‘east of the trees’), creating an illusion that the story world aligns with the real one.

![Figure 5.6A player of Audio Legends blocking an incoming cannon ball with the mobile device ¶ Source: Photograph courtesy of Emmanouel Rovithis and Nikolaos Moustakas](img/fig5_6.jpg)

Figure 5.6A player of `Audio Legends` blocking an incoming cannon ball with the mobile device ¶ Source: Photograph courtesy of Emmanouel Rovithis and Nikolaos Moustakas
