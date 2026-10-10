

# 使用 Pandas 2.0 进行数据库交互

数据库交互是指使用编程语言或软件工具连接、查询和管理存储在数据库管理系统 (DBMS) 中数据的过程。Pandas 结合其他库，可以与各种数据库进行交互，例如 SQL 数据库（如 SQLite、MySQL、PostgreSQL）和 NoSQL 数据库（如 MongoDB），以读取和写入数据。在本示例中，我们将演示如何使用 Pandas 2.0 与 SQLite 数据库进行交互。SQLite 是一种轻量级、无服务器、自包含的 SQL 数据库引擎，易于设置，且无需单独的服务器进程。

## 安装 sqlite3 包

首先，您需要安装 `sqlite3` 包，它是 Python 标准库的一部分，通常已经预装。

```
!pip install pysqlite3
```

此代码将使用 `pip` 安装 `sqlite3` 包及其依赖项。

## 设置 SQLite 数据库

为了演示，我们将创建一个新的 SQLite 数据库和一张表，用于存储 `Customer_Churn_Modelling` 数据。

```
import sqlite3

# 连接到 SQLite 数据库（如果不存在，将创建一个名为 'churn.db' 的新文件）
conn = sqlite3.connect('churn.db')

# 创建一个游标对象以执行 SQL 命令
cursor = conn.cursor()

# 创建 'customer_churn' 表
create_table_query = '''
CREATE TABLE IF NOT EXISTS customer_churn (
    RowNumber INTEGER PRIMARY KEY,
    CustomerId INTEGER,
    Surname TEXT,
    CreditScore INTEGER,
    Geography TEXT,
    Gender TEXT,
    Age INTEGER,
    Tenure INTEGER,
    Balance REAL,
    NumOfProducts INTEGER,
    HasCrCard INTEGER,
    IsActiveMember INTEGER,
    EstimatedSalary REAL,
    Exited INTEGER
);
'''

cursor.execute(create_table_query)

# 提交更改并关闭游标
conn.commit()
cursor.close()
```

## 将数据加载到 SQLite 数据库

现在，我们将 `Customer_Churn_Modelling` 数据（假设存储在名为 `data` 的 DataFrame 中）插入到 `customer_churn` 表中。

```
# 将 DataFrame 中的数据插入到 SQLite 表中
data.to_sql('customer_churn', conn, if_exists='replace', index=False)
```

## 使用 Pandas 查询 SQLite 数据库

您可以使用 Pandas 在数据库上执行 SQL 查询，并将结果存储在 DataFrame 中。

```
# 定义 SQL 查询
sql_query = 'SELECT * FROM customer_churn WHERE Exited = 1'

# 执行查询并将结果存储在 DataFrame 中
churned_customers = pd.read_sql_query(sql_query, conn)
```

## 执行数据操作与分析

数据加载到 DataFrame 后，您可以使用前文讨论的相同 Pandas 函数和方法来操作和分析数据。

## 将数据写回 SQLite 数据库（可选）

如果您想将修改后的数据写回 SQLite 数据库，可以再次使用 `to_sql()` 方法。

```
# 假设 'modified_data' 是一个包含修改后数据的 DataFrame
modified_data.to_sql('customer_churn', conn, if_exists='replace', index=False)
```

## 关闭连接

最后，关闭与 SQLite 数据库的连接。

```
conn.close()
```

总之，Pandas 允许您通过连接数据库、查询数据以及管理数据库中的数据来与数据库进行交互。通过使用其他库（如本例中的 `sqlite3`），您可以执行数据库交互任务，并使用 Pandas 从数据库读取和写入数据。这种集成使 Pandas 成为涉及数据库的数据操作和分析的强大工具。

# 连接 Web API

通过 Pandas 利用 Web API 可以获取最新信息，并将其无缝集成到 DataFrame 中，以便进行后续评估和操作。这种与 API 的集成简化了实时访问和处理数据的流程，为分析提供了更高效的方法。在本示例中，我们将演示如何使用 `requests` 库连接到公共 API 并将数据加载到 Pandas DataFrame 中。

## 安装 HTTP 请求包

首先，您需要安装用于发送 HTTP 请求的 `requests` 包：

```
pip install requests
```

## 发起 API 请求并检索数据

在本示例中，我们将使用 JSONPlaceholder 提供的公共 API，它以 JSON 格式返回一组虚拟帖子列表。

```
import requests

# 定义 API 端点
api_url = 'https://jsonplaceholder.typicode.com/posts'

# 向 API 发送 HTTP GET 请求
response = requests.get(api_url)

# 检查请求是否成功
if response.status_code == 200:
    # 解析 JSON 数据
    json_data = response.json()
else:
    print(f'Error: Unable to fetch data from the API (status code: {response.status_code})')
```

## 将 JSON 数据加载到 Pandas DataFrame

获取 JSON 数据后，您可以使用 `pd.DataFrame()` 构造函数或 `pd.read_json()` 函数将其加载到 DataFrame 中。

```
import pandas as pd

# 将 JSON 数据加载到 DataFrame 中
data = pd.DataFrame(json_data)

# 或者，您可以使用 'pd.read_json()' 函数
# data = pd.read_json(api_url)
```

## 执行数据操作与分析

现在数据已加载到 DataFrame 中，您可以使用前文讨论的相同 Pandas 函数和方法来操作和分析数据。

请记住，连接不同 API 的过程可能因特定 API 和所需的身份验证方法而异。您可能需要提供 API 密钥、令牌或使用 OAuth 进行身份验证。请务必查阅 API 文档，了解如何连接和检索数据的详细说明。

总之，您可以使用 `requests` 等库连接到 Web API 并检索实时数据，将数据加载到 Pandas DataFrame 中以进行操作和分析。这一功能使 Pandas 成为处理动态数据源和实时应用的强大工具。

