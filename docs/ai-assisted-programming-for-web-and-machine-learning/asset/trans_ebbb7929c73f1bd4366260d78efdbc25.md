

# 在 Jupyter Notebook 中你好 Hello World

```
print("Hello, World!")
```

## 使用 AI 工具增强数据探索

准备好 Jupyter Notebook 后，你可以集成强大的工具来更有效地分析和可视化你的数据。通过强大的数据剖析工具，让探索和理解数据变得轻而易举：

- **Pandas profiling**: 自动生成数据集的详细摘要。

- **安装：**
```bash
pip install pandas-profiling
```

> 兼容性说明：Pandas-profiling 软件包不兼容 Python 3.13，因为它依赖于在 Python 3.13 中已移除的弃用 cgi 模块。为了避免安装问题，在使用此库时建议使用 Python 3.10 或 3.11。

- **可选的替代方案（如果你已经安装了 Python 3.13）：** 创建一个带有 Python 3.10 或 3.11 的虚拟环境：
```bash
# 假设你已经安装了 Python 3.10
python3.10 -m venv venv-py310
source venv-py310/bin/activate # 或 Windows 上使用 venv-py310\Scripts\activate
# 然后安装 pandas-profiling
pip install pandas-profiling
```

- **示例用法：**
```python
from pandas_profiling import ProfileReport
import pandas as pd
df = pd.read_csv("data.csv")
profile = ProfileReport(df, title="Data Profile")
profile.to_notebook_iframe()
```

- **Great expectations**: 通过验证确保数据质量和一致性。

- **安装：**
```bash
pip install great-expectations
```

- **示例用法：**
```python
from great_expectations.dataset import PandasDataset
dataset = PandasDataset(df)
dataset.expect_column_values_to_be_in_set("category", ["A", "B", "C"])
```

- **OpenAI 集成**: 使用 OpenAI 的 GPT 用自然语言生成数据解解或摘要：

- **安装：**
```bash
pip install openai
```

- **示例用法：**
```python
import openai
openai.api_key = "your-api-key-here"
response = openai.ChatCompletion.create(
  model="gpt-3.5-turbo",
  messages=[
    {"role": "system", "content": "You are a helpful data analyst."},
    {"role": "user", "content": "Summarize the dataset in plain English."}
  ],
  max_tokens=50
)
print(response.choices[0].message["content"].strip())
```

> 注意：使用 `openai.Completion.create()` 的旧代码（例如使用 text-davinci-003）将不再适用于 OpenAI Python 包 1.0.0 或更高版本。对于 gpt-3.5-turbo 或 gpt-4 等模型，请始终使用新的 Chat Completion API。

有关用法用法，请访问 https://github.com/openai/openai-python。

# 高级可视化

使用这些强大的高级数据可视化工具，创建令人印象且引人入胜的视觉效果：

- **Dash 用于交互式仪表板**: 构建实时洞察的动态仪表板。
  - 安装：
    ```bash
    pip install dash
    ```
  - 示例用法：
    ```python
    from dash import Dash, dcc
    app = Dash()
    app.layout = html.Div([
        dcc.Graph(figure={'data': {'x': [1, 2, 3], 'y': [4, 1, 2]}})
    ])
    app.run_server(debug=True)
    ```

- **Bokeh 用于交互式图表**: 创建视觉上震撼且交互式的图表。
  - 安装：
    ```bash
    pip install bokeh
    ```
  - 示例用法：
    ```python
    from bokeh.plotting import figure, show
    p = figure(title="Dynamic Plot")
    p.line(x=[1, 2, 3], y=[4, 5, 6])
    show(p)
    ```

# 在 Notebook 上进行高效协作

协作在数据驱动项目中至关重要。虽然 Notebook 擅长个人工作流，但它们的 JSON 格式会让版本控制变得复杂。以下是无缝协作的方法：

- **使用 Jupytext 将 Notebook 转换为脚本。**
  - 安装：
    ```bash
    pip install jupytext
    ```
  - 示例：
    ```bash
    jupyter --sync notebook.ipynb
    ```

- **使用 DVC 管理数据集：**
  - 安装：
    ```bash
    pip install dvc
    dvc init
    dvc add dataset.csv
    ```

- **使用 nbdime 解决合并冲突：**
  - 安装：
    ```bash
    pip install nbdime
    nbdime diff notebook1.ipynb notebook2.ipynb
    ```

# 现实应用案例

通过这些真实案例，发现数据分析和建模如何帮助解决日常生活的问题：

- **零售探索性数据分析 (EDA)**: 分析销售数据以识别表现最佳的产品：

```python
import pandas as pd
import seaborn as sns
import matplotlib.pyplot as plt
# 加载数据集（确保包含 'product' 和 'sales' 列）
df = pd.read_csv("sales_data.csv")
# 按产品分组并计算总销售额
top_products = df.groupby("product")["sales"].sum().nlargest(10)
# 绘制总销售额前 10 个产品的图表
sns.barplot(x=top_products.values, y=top_products.index)
plt.title("Top 10 Products by Sales")
plt.xlabel("Total Sales")
plt.ylabel("Product")
plt.tight_layout()
plt.show()
```

注意：将 sales_data.csv 替换为实际文件路径。确保数据集至少包含两列：

- **product**: 产品名称或标识符
- **sales**: 数值销售额

**能源消耗预测：** 使用时间序列分析预测能源需求：
```python
from statsmodels.tsa.holt import ExponentialSmoothing
model = ExponentialSmoothing(data["consumption"],
    seasonal="add", seasonal_periods=24).fit()
forecast = model.forecast(steps=48)
print(forecast)
```

**情感分析：** 构建情感分析模型来分析客户评论：
```python
from sklearn.feature_extraction.text import CountVectorizer
from sklearn.naive_bayes import MultinomialNB
X = vectorizer.fit_transform(reviews)
model = MultinomialNB().fit(X, labels)
```

