
为提高可读性，我们打开了文件对象（代码片段 [1] 和 [2]），并在代码片段 [3] 的第一行指定了它们的变量名。这个 `with` 语句管理两个资源对象，这些对象在 `with` 之后以逗号分隔的列表中指定。`for` 语句将每条记录解包为 `account`、`name` 和 `balance`。如果 `account` 不是 '300'，我们将 `record`（包含换行符）写入 `temp_file`。否则，我们组装包含 'Williams' 以替代 'White' 的新记录，并将其写入文件。代码片段 [3] 之后，`temp_file.txt` 包含：

```
100 Jones 24.98
200 Doe 345.67
300 Williams 0.00
400 Stone -42.16
500 Rich 224.62
```

## os 模块文件处理函数

此时，我们有旧的 `accounts.txt` 文件和新的 `temp_file.txt`。要完成更新，让我们删除旧的 `accounts.txt` 文件，然后将 `temp_file.txt` 重命名为 `accounts.txt`。`os` 模块 4 提供与操作系统交互的函数，包括几个用于操作系统文件和目录的函数。既然我们已创建临时文件，让我们使用 `remove` 函数 5 删除原始文件：

4 https://docs.python.org/3/library/os.html.

5 使用 `remove` 时需谨慎；它不会警告你正在 *永久* 删除文件。

![](img/34b7fc2f1ee27beb73bca14927d42340_354_0.png)

```
In [4]: import os

In [5]: os.remove('accounts.txt')
```

接下来，让我们使用 `rename` 函数将临时文件重命名为 'accounts.txt'：

![](img/34b7fc2f1ee27beb73bca14927d42340_354_1.png)

```
In [6]: os.rename('temp_file.txt', 'accounts.txt')
```

## 9.5 使用 JSON 进行序列化

我们将用来与基于云的服务（如 Twitter、IBM Watson 等）交互的许多库，通过 JSON 对象与你的应用程序通信。JSON（JavaScript 对象表示法）是一种基于文本的、人类和计算机都可读的数据交换格式，用于将对象表示为名称-值对的集合。JSON 甚至可以表示自定义类的对象，就像你将在下一章中构建的那些对象一样。

JSON 已成为跨平台传输对象的首选数据格式。这一点在调用基于云的 Web 服务时尤其适用，这些服务是你通过 Internet 调用的函数和方法。你将熟练处理 JSON 数据。在“数据挖掘 Twitter”章节中，你将访问包含推文及其元数据的 JSON 对象。在“IBM Watson 和认知计算”章节中，你将访问 Watson 服务返回的 JSON 响应中的数据。在“大数据：Hadoop、Spark、NoSQL 和 IoT”章节中，我们将从 Twitter 获取的 JSON 推文对象存储在 MongoDB（一种流行的 NoSQL 数据库）中。在该章节中，我们还将处理其他以 JSON 对象形式发送和接收数据的 Web 服务。

### JSON 数据格式

JSON 对象类似于 Python 字典。每个 JSON 对象包含花括号中的逗号分隔的属性名和值列表。例如，以下键-值对可能表示客户记录：

```
{"account": 100, "name": "Jones", "balance": 24.98}
```

JSON 还支持数组，数组类似于 Python 列表，是方括号中的逗号分隔值。例如，以下是可接受的数字 JSON 数组：

```
[100, 200, 300]
```

JSON 对象和数组中的值可以是：

- 双引号括起来的字符串（如 "Jones"），
- 数字（如 100 或 24.98），
- JSON 布尔值（在 JSON 中表示为 `true` 或 `false`），
- `null`（表示无值，类似于 Python 中的 `None`），
- 数组（如 `[100, 200, 300]`），以及
- 其他 JSON 对象。

### Python 标准库模块 json

**json** 模块使你能够将对象转换为 JSON（JavaScript 对象表示法）文本格式。这被称为对数据进行 **序列化**。请考虑以下字典，它包含一个键-值对，该键为 'accounts'，关联的值是一个表示两个账户的字典列表。每个账户字典包含三个键-值对，分别对应账户号码、姓名和余额：

单击此处查看代码图片

```
In [1]: accounts_dict = {'accounts': [
    ...:     {'account': 100, 'name': 'Jones', 'balance': 24.98},
    ...:     {'account': 200, 'name': 'Doe', 'balance': 345.67}]}
```

### 将对象序列化为 JSON

让我们将该对象以 JSON 格式写入文件：

单击此处查看代码图片

```
In [2]: import json

In [3]: with open('accounts.json', 'w') as accounts:
    ...:     json.dump(accounts_dict, accounts)
```

代码片段 [3] 打开文件 `accounts.json` 并使用 **json** 模块的 **dump** 函数将字典 `accounts_dict` 序列化到文件中。生成的文件包含以下文本，我们略微重新格式化以提高可读性：

单击此处查看代码图片

```
{"accounts": [
{"account": 100, "name": "Jones", "balance": 24.98},
{"account": 200, "name": "Doe", "balance": 345.67}]}
```

请注意，JSON 使用双引号字符来界定字符串。

### 反序列化 JSON 文本

json 模块的 load 函数读取其文件对象参数的完整 JSON 内容，并将 JSON 转换为 Python 对象。这被称为对数据进行反序列化。让我们从这段 JSON 文本重建原始 Python 对象：

单击此处查看代码图片

```
In [4]: with open('accounts.json', 'r') as accounts:
    ...:     accounts_json = json.load(accounts)
    ...:
    ...:
```

现在我们可以与加载的对象进行交互。例如，我们可以显示字典：

单击此处查看代码图片

```
In [5]: accounts_json
Out[5]:
{'accounts': [{'account': 100, 'name': 'Jones', 'balance': 24.98],
{'account': 200, 'name': 'Doe', 'balance': 345.67}]}
```

如你所料，你可以访问字典的内容。让我们获取与 'accounts' 键关联的字典列表：

单击此处查看代码图片

```
In [6]: accounts_json['accounts']
Out[6]:
[{'account': 100, 'name': 'Jones', 'balance': 24.98],
{'account': 200, 'name': 'Doe', 'balance': 345.67}]}
```

现在，让我们获取各个账户字典：

单击此处查看代码图片

```
In [7]: accounts_json['accounts'][0]
Out[7]: {'account': 100, 'name': 'Jones', 'balance': 24.98}
In [8]: accounts_json['accounts'][1]
Out[8]: {'account': 200, 'name': 'Doe', 'balance': 345.67}
```

虽然我们在此未这样做，但你也可以修改字典。例如，你可以向列表中添加账户或从列表中删除账户，然后将字典写回 JSON 文件。

### 显示 JSON 文本

json 模块的 dumps 函数（dumps 是“dump string”的缩写）返回对象在 JSON 格式中的 Python 字符串表示。使用 dumps 配合 load，你可以从文件读取 JSON 并以良好缩进的格式显示它——有时称为“美化打印” JSON。当 dumps 函数调用包含 indent 关键字参数时，字符串包含用于美化打印的换行符和缩进——你也可以在使用 dump 函数向文件写入时使用 indent：

单击此处查看代码图片

```
In [9]: with open('accounts.json', 'r') as accounts:
    ...:     print(json.dumps(json.load(accounts), indent=4))
    ...:
{
    "accounts": [
        {
            "account": 100,
            "name": "Jones",
            "balance": 24.98
        },
        {
            "account": 200,
            "name": "Doe",
            "balance": 345.67
        }
    ]
}
```

## 9.6 安全聚焦：Pickle 序列化和反序列化

Python 标准库的 pickle 模块可以将对象序列化为 Python 特定的数据格式。注意：Python 文档对 pickle 提供了以下警告：

- “Pickle 文件可能被攻击。如果你通过网络接收到原始 pickle 文件，请不要信任！它可能包含恶意代码，当你尝试反序列化它时，这些代码会运行任意 Python。但是，如果你自己进行 pickle 写入和读取，你是安全的（当然，前提是没有其他人可以访问 pickle 文件。） 6

6 https://wiki.python.org/moin/UsingPickle.

- “Pickle 是一种协议，允许序列化任意复杂的 Python 对象。因此，它特定于 Python，不能用于与用其他语言编写的应用程序通信。它默认也不安全：反序列化来自不可信源的 pickle 数据可能会执行任意代码，如果数据是由熟练攻击者精心构造的。” 7

7 https://docs.python.org/3/tutorial/inputoutput.html#reading-and-writing-files.

我们不推荐使用 pickle，但它已被使用多年，因此你可能会在旧代码中遇到它——旧代码通常不再受支持。

## 9.7 关于文件的其他说明

下表总结了文本文件的各种文件打开模式，包括我们已介绍的读取和写入模式。写入和追加模式在文件不存在时会创建文件。读取模式在文件不存在时会引发 FileNotFoundError。每种文本文件模式都有一个对应的二进制文件模式，指定 b，如 'rb' 或 'wb+'。例如，如果你要读取或写入二进制文件（如图像、音频、视频、压缩的 ZIP 文件以及许多其他流行的自定义文件格式），则会使用这些模式。

| Mode | Description |
|---|---|
| 'r' | 打开文本文件以供读取。如果在调用 open 时未指定文件打开模式，则这是默认模式。 |
| 'w' | 打开文本文件以供写入。现有文件内容将被删除。 |
