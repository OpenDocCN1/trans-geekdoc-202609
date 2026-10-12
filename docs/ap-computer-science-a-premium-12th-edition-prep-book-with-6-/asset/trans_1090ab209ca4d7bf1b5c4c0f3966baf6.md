

**注意事项：**

假设 Quick Reference 中的类已在适当的位置导入。

除非题目另有说明，假设方法调用中的参数不为 `null`，并且仅在满足方法前置条件时才调用方法。

在为每个问题编写解决方案时，您可以使用该问题中定义的类中列出的任何可访问方法。编写大量可以通过调用这些方法之一来替代的代码将无法获得满分。

### 1

`WordSet` 类的部分实现如下所示，它按无特定顺序存储一组 `String` 对象且不包含重复项。每个单词仅由大写字母组成。

`findkth` 方法返回集合中按字母顺序排列的第 *k* 个 `word`，即使 `WordSet` 的实现可能未排序。数字 *k* 的范围是从 1（对应字母顺序中的第一个）到 *N*，其中 *N* 是集合中单词的数量。例如，如果 `WordSet s` 存储单词 `{“GRAPE”, “PEAR”, “FIG”, “APPLE”}`，以下是调用 `s.findkth(k)` 时的值。

#### (a)

编写客户端方法 `countA`，返回 `WordSet s` 中以字母 “A” 开头的单词数量。在编写 `countA` 时，您可以调用 `WordSet` 类的任何方法。假设这些方法按规范工作。

完成方法 `countA`。

#### (b)

编写客户端方法 `removeA`，从非空 `WordSet` 中移除所有以 “A” 开头的单词。如果 `s` 中没有此类单词，则 `removeA` 不执行任何操作。在编写 `removeA` 时，您可以调用 (a) 部分指定的方法 `countA`。假设 `countA` 按规范工作，无论您在 (a) 部分编写了什么。

完成方法 `removeA`。

### 2

一家服装店出售鞋子、裤子和上衣。该店还允许顾客购买“套装”，套装包含三件商品：一双鞋子、一条裤子和一件上衣。

每件服装都有描述和价格。四种类型的服装由四个类 `Shoes`、`Pants`、`Top` 和 `Outfit` 表示。所有四个类都是 `ClothingItem` 类的子类，如下所示。

下图显示了 `ClothingItem` 类与 `Shoes`、`Pants`、`Top` 和 `Outfit` 类之间的关系。

商店允许顾客创建 `Outfit` 服装项，每个套装包含一双鞋子、一条裤子和一件上衣。套装的描述由鞋子、裤子和上衣的描述按顺序组成，用 `“/”` 分隔，后跟一个空格和 `“outfit”`。套装的价格计算如下。如果任意两件商品的价格之和等于或超过 100 美元，则对所有三件商品的价格之和打 25% 折扣（即打 75 折）。否则打 10% 折扣（即打 9 折）。

例如，一个由运动鞋（40 美元）、蓝色牛仔裤（50 美元）和 T 恤（10 美元）组成的套装，其名称为 `“sneakers/blue jeans/T-shirt outfit”`，价格为 0.90(40 + 50 + 10) = 90.00 美元。

一个由便鞋（50 美元）、短裤（20 美元）和衬衫（60 美元）组成的套装，其描述为 `“loafers/cutoffs/dress-shirt outfit”`，价格为 0.75(50+20+60) = 97.50 美元。

编写 `ClothingItem` 的子类 `Outfit`。您的实现必须只有一个构造器，按顺序接受代表一双鞋子、一条裤子和一件上衣的三个参数。

使用 `Outfit` 类的客户端类应该能够创建套装、获取其描述并获取其价格。您的实现应使客户端代码具有以下行为：

### 3

考虑一个笔记管理器对象，旨在存储和操作简短笔记列表。以下是一些典型笔记：

笔记由以下类表示。

笔记管理器由下面所示的 `NoteKeeper` 类表示。

#### (a)

编写 `NoteKeeper` 方法 `printNotes`。此方法打印 `noteList` 中的所有笔记，每行一个，并对笔记进行编号，从 1 开始。输出应如下所示。

```
1. pick up drycleaning
2. special dog chow
3. car registration
4. dentist Monday
5. dog license
```

完成方法 `printNotes`。

#### (b)

编写 `NoteKeeper` 方法 `removeNotes`。方法 `removeNotes` 从 `noteList` 中移除所有包含参数指定字符串的笔记。剩余笔记的顺序应保持不变。例如，假设 `NoteKeeper` 变量 `notes` 的 `noteList` 包含以下内容。

```
[pick up drycleaning, special dog chow, car registration, dentist Monday, dog license]
```

方法调用 `notes.removeNotes(“dog”)` 应将 `notes` 的 `noteList` 修改为

```
[pick up drycleaning, car registration, dentist Monday]
```

方法调用 `notes.removeNotes(“cow”)` 应保持上述列表不变。

这是另一个例子。如果 `noteList` 包含

```
[pick up car, buy carrots, dog license, carpet cleaning]
```

方法调用 `notes.removeNotes(“car”)` 应将 `notes` 的 `noteList` 修改为

```
[dog license]
```

完成方法 `removeNotes`。

### 4

考虑跟踪剧院可用座位的问题。剧院座位可以用一个二维整数数组表示，其中值 `0` 表示座位可用，值 `1` 表示座位已被占用。例如，下面的数组显示了小剧院某场演出的当前座位可用情况。

位置 `[1][3]` 的座位已被占用，但位置 `[0][4]` 的座位仍然可用。

一场演出可以用下面所示的 `Show` 类表示。

#### (a)

编写 `Show` 方法 `twoTogether`，该方法预订两个相邻座位，如果成功则返回 `true`。如果无法找到两个未被占用的相邻座位，该方法应保持演出状态不变并返回 `false`。例如，假设某演出的状态如下。

调用 `twoTogether` 应返回 `true`，且演出的最终状态可以是以下三种配置中的任意一种。

或

或

对于以下演出状态，调用 `twoTogether` 应返回 `false` 并保持二维数组如图所示。

完成方法 `twoTogether`。

#### (b)

编写 `Show` 方法 `findAdjacent`，该方法在指定行中查找指定数量的空闲相邻座位中的最低座位号。如果不存在这样的空闲座位块，`findAdjacent` 方法应返回 `-1`。无论返回值如何，均不应更改演出的状态。

例如，假设座位图如下所示。

下表显示了为 `show` 调用 `findAdjacent` 的一些示例。

完成方法 `findAdjacent`。

**停止**

**考试结束**

### 答案解析

### 第一部分

**1. (E)** 该行代码中的字符串参数使用了两个转义字符：

```
\"`，表示打印一个双引号。
`\n`，表示打印一个换行符（即换到下一行）。
```

