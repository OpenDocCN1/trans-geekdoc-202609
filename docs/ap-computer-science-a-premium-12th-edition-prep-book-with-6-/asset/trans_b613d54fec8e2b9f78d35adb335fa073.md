

## 进一步思考：基础独立对象与类关系

基础独立对象包括 `Student`、`Menu`、`Score` 和 `FileHandler`。组合对象包括 `ClassList`（学生集合）、`ScoreList`（分数集合）和 `AllClasses`（`ClassList` 集合）。控制类是 `GradeBook`。`Display` 类对于许多成绩簿操作至关重要，例如显示班级列表或显示单个学生的信息。

### 类之间的关系

不存在继承关系。但是，对象之间存在许多组合关系。`GradeBook` *has-a* `Menu`，`ClassList` *has-a* `Student`（实际上是多个！），一个 `Student` *has-a* `name`、`average`、`grade`、`list_of_scores` 等。程序员必须决定是将这些属性编码为类还是数据字段。

### 识别行为

使用规格说明中的动词来识别程序中所需的操作。这些动词包括：maintain \<list\>、provide \<menu\>、allow \<user\>、create \<list\>、enter \<scores\>、correct \<data\>、display \<record\>、calculate \<average\>、calculate \<grade\>、print \<list\>、add \<student\>、delete \<student\>、transfer \<student\> 和 save \<data\>。

使用规格说明中的动词来识别可能的方法。

你必须做出一些设计决策，确定哪个类负责哪种行为。例如，是由 `ClassList` 显示单个 `Student` 的记录，还是由 `Student` 显示自己的记录？谁来录入分数——`GradeBook`、`ClassList` 还是 `Student`？让 `Student` 录入其他 `Student` 的分数合乎需要吗？很可能不合适！

### 设计决策

以下是一些初步决策。`GradeBook` 将 `provideMenu`。菜单选择将把执行发送到相关对象。

`ClassList` 将维护每个班级的更新列表。它将拥有以下公共方法：`addStudent`、`deleteStudent`、`transferStudent`、`createNewClass`、`printClassList`、`printScores` 和 `updateList`。该类中一个很好的辅助方法候选者是用于查找给定学生的 `search`。

每个 `Student` 将拥有完整的个人和成绩信息。公共方法将包括 `setName`、`getName`、`enterScore`、`correctData`、`findAverage`、`getAverage`、`getGrade` 和 `displayRecord`。

保存和检索信息对该程序至关重要。`FileHandler` 将负责 `openFileForReading`、`openFileForWriting`、`closeFiles`、`loadClass` 和 `saveClass` 等方法。`FileHandler` 类应在开始时就编写并测试，使用一个小的虚拟班级列表。

`Score`、`ScoreList` 和 `Student` 是易于实现的类。当这些工作正常后，程序员可以继续实现 `ClassList`。最后，可以开发拥有 `GradeBook` 的 `Display` GUI 类。这是自底向上开发的一个示例。

## 示例 3：战舰游戏模拟

一个程序模拟战舰游戏，这是一个双人游戏，每个玩家都有一个用于放置舰船的网格。每个玩家拥有五艘舰船：

![images](images/f201-01.jpg)

玩家舰队的网格可能如下所示。任意两个相邻的被占用方格必须属于同一艘舰船；即不同舰船不应“接触”。

![images](images/f201-02.jpg)

每个玩家的网格对另一个玩家隐藏。玩家轮流通过报出一个位置（行号和列号）来“射击”对方的舰船。玩家必须诚实回答，“命中”或“未命中”。如果是命中，该玩家获得另一次回合。如果整艘舰船被击中，拥有者必须说类似“你击沉了我的巡洋舰”这样的话。每个玩家必须记录命中和未命中的情况。击沉对手舰队的先行者为胜者。

### 识别类

规格说明中的名词包括：program、game、players、grid、ship、battleship、cruiser、submarine、destroyer、frigate、square、position、opponent、row、column、turn、hits、misses、fleet、winner。

排除以下各项：

![images](images/f202-01.jpg)

以下似乎是类的良好候选者：`Player`、`Grid`、`Position`、`Ship`、`Battleship`、`Cruiser`、`Submarine`、`Destroyer` 和 `Frigate`。此外，似乎还应该有一个 `GameManager` 和 `Display`。

### 类之间的关系

该程序提供了两个继承关系的示例。五艘舰船中的每一艘 *is-a* `Ship`，并共享通用特性，如 `isHit`、`isSunk` 和位置数组。然而，每艘舰船都有独特的名称、长度和网格中的位置。这意味着 `Ship` 是抽象类的良好候选者，带有抽象方法如 `getLength`、`getName` 和 `getPositions`，这些方法取决于舰船的种类。

第二个继承关系存在于网格之间。每个玩家有两种类型的网格：他自己的 `FleetGrid`（他自己舰船的当前状态）和他对手的 `HitGrid`，用于记录他的命中和未命中。这些网格中的每一个 *is-a* `Grid`。网格是接口的候选者，包含如 `getAdjacentNeighbors`、`getRightNeighbor` 等方法列表。`FleetGrid` 和 `HitGrid` 都将实现 `Grid`。

该程序中存在若干组合关系。一个 `Player` *has-a* `HitGrid` 和一个 `FleetGrid`，还拥有五艘舰船。`GameManager` 拥有两个 `Player` 对象，并且 *has-a* `Display`。`Display` 拥有每个网格。

### 识别行为

使用动词来识别程序中的关键方法：simulate \<game\>、place \<ships\>、shoot \<at position\>、call out \<position\>、respond \<hit or miss\>、sink \<ship\>、inform that \<ship was sunk\>、keep track of \<hits or misses\>、sink \<opponent's fleet\>、win \<game\>。

你需要决定谁做什么。没有确定的实现方式，但显然 `GameManager` 应该运行游戏并宣布胜利者。`GameManager` 也应该负责宣布舰船是否被击沉吗？这讲得通，因为游戏管理器可以看到双方玩家的网格。每个玩家应该记录自己的呼叫，以便做出明智的下一次呼叫，并回答“命中”或“未命中”。每个玩家会有一个显示器吗？还是 `Display` 拥有两个玩家？你必须设置好，使得玩家看不到对手的 `FleetGrid`，但可以看到自己的网格以及显示他所做呼叫状态的网格。每个玩家应该有一份自己的舰船列表，以便跟踪舰队状态吗？每艘舰船呢？舰船应该有一份位置列表，并记录自己是否被命中或击沉吗？

保存和检索更新信息对该程序至关重要。这似乎有点令人不知所措。从哪里开始？`Ship` 类是低层类，独立于玩家和网格。从这些开始，并测试你是否能获得关于每艘舰船的准确信息。在你的驱动程序中创建一个 `ArrayList<Ship>`。编写一个循环来打印每艘舰船的信息。多态性将负责获取每艘舰船的正确信息。

现在尝试 `Grid` 类。这是一个复杂的程序，每一小块都应该编码并用简单的输出进行测试。例如，`Grid` 可以用二维数组的 0 和 1 来显示，以显示舰船的位置。其他符号可用于显示已被命中和已被击沉的内容。

当网格的一切正常工作时，你可以添加一个拥有 `Grid` 变量和 `display` 方法的 `Display` 类。

尝试一个 `Player`。给他一份舰船列表、两个网格和一个 `Display`。

然后创建一个 `GameManager`。给她两个 `Player` 变量，并确保她有一个 `playGame` 方法。

上述程序开发是自底向上开发的一个示例。

### 词汇总结

AP 考试需知术语：

![images](images/f203-01.jpg)

### 程序分析

### 程序正确性

