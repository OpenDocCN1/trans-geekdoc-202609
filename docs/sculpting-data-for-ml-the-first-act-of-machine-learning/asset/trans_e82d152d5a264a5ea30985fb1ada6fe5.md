

### 可扩展标记语言 (XML)

以此标记语言导出的数据集作为 `.xml` 文件，其格式既易于人类阅读，也易于机器解析。XML 主要用于文本数据，因为它通过 Unicode 提供了对多语言的强力支持。尽管 XML 可能易于使用和推广，但它非常冗长，会导致数据量膨胀，因此不广泛用于导出数据集。

```
<?xml version="1.0" encoding="UTF-8"?>
<root>
  <row>
    <username>heylaura</username>
    <pin>1234</pin>
    <first_name>Laura</first_name>
    <last_name>Wu</last_name>
  </row>
  <row>
    <username>iampc</username>
    <pin>999</pin>
    <first_name>Paige</first_name>
    <last_name>Carter</last_name>
  </row>
  ...
</root>
```

还有其他极少用于导出数据集的格式，如 HTML (`.html`)、电子表格 (`.xls`、`.ods` 或 `.gsheet`)、统计产品与服务解决方案 SPSS (`.dat` 或 `.sps`) 等。然而，鉴于其诸多优点，CSV 和 JSON 是导出和导入数据集的两种最流行格式。

回顾一下，我们一直在处理从 ModCloth 提取的层级数据结构。为简单起见，我们可以将所有数据导出为 JSON 格式。

```
import json

output_file = open('./ModCloth_scraped_data.json', 'w', encoding='utf-8')

for r in scraped_data:
    output_file.write(json.dumps(r) + '\n')

output_file.close()
```

导出的数据集随后可以按如下方式导入学习框架：

```
def parseJson(fname):
    for line in open(fname, 'r'):
        yield eval(line)

scraped_data = list(parseJson('./ModCloth_scraped_data.json'))
```

