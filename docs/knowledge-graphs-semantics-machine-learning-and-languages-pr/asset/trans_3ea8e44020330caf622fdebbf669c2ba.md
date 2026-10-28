
可通过可折叠的附加信息打开，例如其*特征*（例如，地点、时间段等）、图像和摘要（见图 3）。在此窗口中，通过允许用户输入笔记为注释预留了空间。原始的*发现*通过 Hub 和整个 Fragmentarium 中的可视化和功能得到解决。用户可以在 Hub 中对数据集应用过滤器或显示统计信息。同时，这也满足了*采样*的需求，因为 Hub 中的过滤器可用于根据用户的兴趣选择数据。在 Fragmentarium 中，使用附加到用户控制器的射线指针选择新的感兴趣节点会使其成为新的*主片段*并更新可视化。因此，用户能够在检查其属性和关系的同时从一个节点移动到另一个节点。历史记录显示迄今为止访问的主片段的顺序（见图 3）。遵循 Wagner 等人 [26] 的建议，我们为用户提供 egocentric 和 exocentric 两种视角，用户可以抓取并转换相关片段的整个星座（包括平移、均匀缩放和旋转）。由此，用户可以从初始的 egocentric 视角切换到 exocentric 视角。最后，应用程序提供了一个帮助菜单，解释所有功能。

### 3.3.1. *后端*

为了实现数据后端，我们依赖 Neo4j⁶ 作为一种图数据库，旨在管理和查询大型知识图谱。我们依赖 DBpedia 作为主要数据源，原因有几点。首先，DBpedia 建立在 Wikipedia 之上，是使用最广泛的在线百科全书 [32]，也是真正协作创建内容的杰出范例之一。Wikimedia Commons⁷ 是 Wikipedia 百科全书家族的一部分，包含超过两千五百万个音频、视频和图像文件 [33]，包括扫描书籍、具有历史意义的照片、插图和地图。通过多种媒体访问历史数据在其探索和解释中发挥着重要作用。第三，DBpedia 与其他相关信息互联，并与其他数据集相连 [34]，使我们能够通过语义相关性探索历史数据。除了 DBpedia，我们还使用 Wikidata，因为它通过一组明确定义的属性表示资源的时空信息，这对于历史数据探索至关重要。

首先，我们从 DBpedia 中提取资源，包括 Wikipedia 文本、图像、视频和音频文件。对于每个资源，我们提取其正向和反向方向的连接。之后，我们通过 DBpedia 资源中的属性 `owl:sameAs` 找到 Wikidata 中的等效条目，并检索时空信息。

为了在历史研究背景下将 DBpedia 和 Wikidata 的数据整合到知识图数据库中，我们在 eTaRDiS 项目中与历史学家合作开发了适当的数据库模式。我们将 DBpedia 的类重构为七个类别：`Agent`、`Place`、`Event`、`Topical Concept`、`Material Object`、`Cultural Artifact` 和 `Miscellaneous`。原因是 DBpedia 的类并非为历史数据背景而设计。例如，Motherland Calls（即 DBpedia 中的资源 `res:The_Motherland_Calls`）是一座代表“斯大林格勒战役英雄”的雕像，但在 DBpedia 中该资源的类别是 `dbo:ArtWork`，在我们的数据库中重构为 `Cultural Artifact`。

![](img/5368dd329bd72fa0bf97ac91d6cef632_168_0.png)

**图 2.** 可视化的外部视图显示主片段（此处为 Albert Einstein）表示为用户站立其上的彩色平台。相关片段表示为彩色、带标签的球体。它们的排列提供了有关片段间相互关系的线索。

![](img/5368dd329bd72fa0bf97ac91d6cef632_168_1.png)

**图 3.** 用户从 egocentric 视角探索场景。对于每个球体，其对应的详细窗口通过显示其时间段、地点、图片（如有）和描述文本来揭示对应片段的更深信息。位于视野下方的历史记录显示迄今为止访问的主片段的顺序（此处为 United States）。在视野的上部，指南针用作引导线；如果节点被标记，其标记会以各自类别的颜色出现在指南针上。被称为“关系详情”的功能有助于弄清两个片段之间的关系。它显示了它们在时间上的差距、其位置之间的最短距离以及其类别差异。

类为 `dbo:Person`、`dbo:Organization`、`dbo:Species`、`dbo:Language` 和 `dbo:EthnicGroup` 的资源被归类为 Agent 类别。此外，类为 `dbo:MeanOfTransportation`、`dbo:Currency`、`dbo:Device`、`dbo:Food` 和 `dbo:ChemicalSubstance` 的资源被归类为 Material Object。所有无法归类到上述类别之一的资源都被归类为 Miscellaneous。

在另一个映射过程中，我们将 DBpedia 和 Wikidata 的属性映射到我们七个类别的每个类别的最小描述属性集。描述属性为 i) category，ii) locations，iii) name，iv) sub-categories，v) time period 和 vi) properties。列出所有包含位置地理信息的属性。相应地，所有包含时间信息的属性都收集在描述属性 `time period` 中。表 1 显示了类别 Agent（即 `res:Albert_Einstein`）的六个描述属性的示例。描述属性 `properties` 由 26 个属性组成，其中一些在表中显示。这些每个资源的最小描述属性集在 Fragmentarium 中片段的详细窗口中用作标准化简要描述（见图 3）。

|  | 描述性属性 | 值 |
|---|---|---|
| 1 | `category` | Agent |
| 2 | `name` | Albert Einstein |
| 3 | `locations` | Germany, United States, Switzerland, Austria |
| 4 | `subcategories` | dbo:Agent, dbo:Person, dbo:Scientist |
| 5 | `time period` | 01.01.1879 - 31.12.1955 |
| 6 | `properties/gender` | male |
|  | `properties/positions` | professor |
|  | `properties/religion` | pantheism |
|  | `properties/abstract` | "Albert Einstein was a German-born theoretical physicist, widely acknowledged to be one of the greatest physicists..." |

表 1. 资源 `res:Albert_Einstein` 的六个描述属性示例。描述属性 `properties` 对此资源包含 26 个属性。

为了访问知识图数据库并应用适当的过滤函数，开发了一个 API。该 API 允许我们查询数据库中可作为 Fragmentarium 中历史片段可视化的特定资源。此外，可以应用过滤器来查询特定地理位置或时间范围内的资源。此外，API 还用于根据 DBpedia 中的摘要计算片段之间的中心和相对语义距离。

## 4. 用户研究

在本节中，我们介绍了一项用户研究，该研究帮助我们深入了解用户如何与 eTaRDiS 交互。用户研究设计了两个目标：1) 评估用户（历史学家或对历史感兴趣的普通人）能否检索与特定历史问题相关的信息，2) 评估应用程序的可用性。

参与者从 Hub 开始，被要求打开一个预设，以 Hundred Years’ War（即资源 `res:Hundred_Years'_War`）作为 Fragmentarium 中的起始主片段，并获得主要功能简要教程。介绍后，他们被指示选择一个以片段 Albert Einstein（即资源 `res:Albert_Einstein`）作为四个连续任务的起始点的预设，并在 Fragmentarium 中被要求“出声思考”（方法基于 [35]）。在本节中，我们描述了用户研究的任务、参与者和结果。

### 4.1. 任务

任务的 underlying 问题为：‘片段 World War II（WWII）、J. Robert Oppenheimer（Oppenheimer）和 Manhattan Project 之间的关系是什么？’。为了回答这个问题，参与者首先被要求在 Fragmentarium 中找到这三个片段。作为第二个任务，他们必须检索
