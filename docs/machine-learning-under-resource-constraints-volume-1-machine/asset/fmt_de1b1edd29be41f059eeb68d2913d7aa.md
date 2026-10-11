
Currently, only the `root` user is allowed to use `kCQL`. To allow ordinary users to use `kCQL`, we could check if the user has the permission or capability to read from the parts of the kernel state that are required for the query. We could also enforce predicates that filter tuples. For example, a user might only be allowed to receive tuples from the `process` relation that contain the respective user ID attribute. However, it is not obvious what to do when tuples or attributes that the user cannot access are present in predicate evaluation (e.g., in joins deep in the query plan), but not in the actual output.

#### 2.1.6.3 Practical Applications

This section presents three case studies from our project that show how data collected in the context of the Linux kernel can be used to better understand and improve systems. In two of the case studies we have tapped the Linux kernel of Android-based smartphones. The third aims at improving the Linux kernel in general.

**Open Smartphone Data Collection** Data gathered on smartphones reveals a lot about users, but also about the behavior and efficiency of the underlying system software. During a 4-month study, we collected an anonymized open dataset on Android smartphones, which is now freely available for research.[⁶](#fn6)

**Reproducible Load Tests** Based on another data collection in Android’s Linux kernel and user-level services, we created representative resource usage profiles for arbitrary Android apps [[445]](#backmatter-001.xhtml#b_9783110785944-010_ref_445). This was done by recording traces of low-level events that are signaled to the app, such as the arrival of a GPS fix or network packet, actions executed by the app as a reaction, such as file I/O or display activity, and pauses. The traces can be mixed to create arbitrary app profiles. Hereby the challenge is to adapt pause durations and simulated event timestamps so that the mixed profile is realistic. System software developers can playback the mixed traces as reproducible load tests without the need for any real apps and, thus, can avoid any requirements on existing server connections, user activity, and so on.

**Learning OS Locking Rules** With the proliferation of multicore and manycore systems the Linux kernel has tremendously grown in complexity, because concurrent controls have to be coordinated in a fine-grained manner. Various kinds of locks are being used for this purpose. Even for experienced system software developers, it has become very difficult to determine the correct sequence of locks that have to be acquired before a particular member of an in-kernel data structure may be accessed safely. Few kernel components have a specification of their locking rules and most of them are outdated. Based on kernel-level data acquisition, namely lock creation and usage events, we developed `LockDoc` [[446]](#backmatter-001.xhtml#b_9783110785944-010_ref_446) as a possible solution to the kernel developers’ dilemma. `LockDoc` learns locking rules for data structures. It can thus (1) generate documentation, (2) identify outdated rules in existing documentation, and (3) find bugs in Linux by identifying rare event sequences that violate the learned rules. A number of documentation and code improvements have already been contributed and integrated into the Linux kernel.

### 2.1.7 Conclusion

Tapping the control and data flow of an operating system has its risks, as does any way of tampering with a complex system. It can however provide us with vital information that could hardly be obtained otherwise. The proper tools and abstractions help to mitigate the risk.

Over a period of several years we have therefore developed `kCQL`, which combines the best ideas of existing frameworks to a unique tool. It has a highly expressive query language, a resource-efficient implementation, and supports data aggregation very close to the data source.

Different application areas have been explored. It turned out that data gathered in the system software context can be used to learn much about user and application behavior, that we could precisely mimic application profiles, and that we could even improve the Linux kernel and its documentation.

## 2.2 PhyNetLab Test Bed

*Mojtaba Masoudinejad*

*Markus Buschhoff*

**Abstract:** Wireless sensor networks have matured to a point that they are ready for their integration into industrial applications. However, before performing any real-world roll-out, some aspects need detailed analysis. In addition to checks for the application performance and durability, system modularity and energy neutrality are two important concerns requiring accurate analysis. These requirements led to the development of `PhyNetLab`, a test bed for material flow and warehousing applications on wireless sensor networks.

Entities in industrial systems should be highly modular to enable flexible and reusable systems, and to ease the process of updating or upgrading system components after deployment. This provides easy-to-setup systems that are dynamically improvable while minimizing post-deployment modification effort and costs. Hence, required design principles for both hardware and software is explained by the case study of the `PhyNetLab` test bed.

Energy neutrality is a fundamental requirement for wireless sensor networks in logistics and production, because the infeasibility of battery management of several thousand network nodes will contracept any endeavor to become wireless here. This section shows several means to achieve energy neutrality by using energy harvesting, automatically generated energy models, and online energy accounting.

In addition to the hardware requirements, an industrial scale wireless sensor network also has several software requirements, and these are narrowed down even further when implementing a test bed for such a use case. Most importantly, `PhyNetLab` uses `Kratos`, a real-time operating system based on `C++` and `AspectC++` that allows modular, maintainable, and highly configurable code. Next to the language and framework properties, `Kratos` employs energy consumption accounting for peripheral devices while still running under heavy resource constraints.

The effectiveness and usability of the `PhyNetLab` test bed is further showcased by presenting a material handling process of a production system that was entirely built using `PhyNetLab`. Not only does it serve as a proof of concept for such a test bed, it also provides insights for possible future works discussed at the end of this section.

### 2.2.1 Introduction

Research in Wireless Sensor Networks (`WSN`) has been continuously advanced in the last years [[209]](#backmatter-001.xhtml#b_9783110785944-010_ref_209). These networks are from diverse fields of applications with different aims, specifications, and limitations. In addition to the singular `WSN`s developed separately, federations of `WSN` have been built as well, with `MoteLab` [[702]](#backmatter-001.xhtml#b_9783110785944-010_ref_702), `FIT/IoT-Lab` [[231]](#backmatter-001.xhtml#b_9783110785944-010_ref_231), `Indriya` [[180]](#backmatter-001.xhtml#b_9783110785944-010_ref_180), and `WISEBED` [[304]](#backmatter-001.xhtml#b_9783110785944-010_ref_304) as some famous implementations of them. While these platforms show proof of concept and enable testing and development of `WSN`s, some aspects are still open. Among them are the development of communication protocols for specific applications and energy-aware system design and operation in a large-scale deployment. Moreover, industrial roll-out requires more intensive system analysis to assure reliability in long run continuous operation under full load in industrial environments.
