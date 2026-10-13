

# Python 代码示例

## GUI 列表框与下拉框初始化

```python
items = [
    "Marital Status", "Education", "Country",
    "Age Group", "Education with Response 0", "Education with Response 1",
    "Country with Response 0", "Country with Response 1",
    "Customer Age", "Income", "Mount of Wines",
    "Education versus Response", "Age Group versus Response",
    "Marital Status versus Response", "Country versus Response",
    "Number of Dependants versus Response",
    "Country versus Customer Age Per Education",
    "Num_TotalPurchases versus Education Per Marital Status"
]

for item in items:
    self.listbox.insert(tk.END, item)

self.listbox.config(height=len(items))
```

```python
def add_comboboxes(self, root):
    # 创建组合框
    self.combo1 = ttk.Combobox(root, width=32)
    self.combo1["values"] = [
        "Categorized Income versus Response",
        "Categorized Total Purchase versus Categorized Income",
        "Categorized Recency versus Categorized Total Purchase",
        "Categorized Customer Month versus Categorized Customer Age",
        "Categorized Mount of Gold Products versus Categorized Income",
        "Categorized Mount of Fish Products versus Categorized Total AmountSpent",
        "Categorized Mount of Meat Products versus Categorized Recency",
        "Distribution of Numerical Columns"
    ]
    self.combo1.grid(row=4, column=0, padx=5, pady=1, sticky="n")

    self.combo2 = ttk.Combobox(root, width=32)
    self.combo2["values"] = [
        "Correlation Matrix", "RF Features Importance",
        "ET Features Importance", "RFE Features Importance"
    ]
    self.combo2.grid(row=6, column=0, padx=5, pady=1, sticky="n")

    self.combo3 = ttk.Combobox(root, width=32)
    self.combo3["values"] = [
        "Linear Regression", "RF Regression",
        "Decision Trees Regression", "KNN Regression",
        "AdaBoost Regression", "Gradient Boosting Regression",
        "XGB Regression", "LGB Regression", "CatBoost Regression",
        "SVR Regression", "Lasso Regression", "Ridge Regression"
    ]
    self.combo3.grid(row=8, column=0, padx=5, pady=1, sticky="n")

    self.combo4 = ttk.Combobox(root, width=32)
    self.combo4["values"] = [
        "Logistic Regression", "Random Forest",
        "Decision Trees", "K-Nearest Neighbors",
        "AdaBoost", "Gradient Boosting",
        "Extreme Gradient Boosting", "Light Gradient Boosting",
        "Multi-Layer Perceptron", "Support Vector Classifier"
    ]
    self.combo4.grid(row=11, column=0, padx=5, pady=1, sticky="n")

    self.combo5 = ttk.Combobox(root, width=32)
    self.combo5["values"] = [
        "LSTM", "Convolutional NN", "Recurrent NN", "Feed-Forward NN", "Artifical NN"
    ]
    self.combo5.grid(row=13, column=0, padx=5, pady=1, sticky="n")
```

## `helper_plot.py` 模块

```python
# helper_plot.py
from tkinter import *
import seaborn as sns
import numpy as np
from pandastable import Table
from process_data import Process_Data
from machine_learning import Machine_Learning
from sklearn.metrics import confusion_matrix, roc_curve, accuracy_score
from sklearn.model_selection import learning_curve

class Helper_Plot:
    def __init__(self):
        self.obj_data = Process_Data()
        self.obj_ml = Machine_Learning()
        # self.obj_dl = Deep_Learning()

    def shows_table(self, root, df, width, height, title):
        frame = Toplevel(root)  # 新窗口
        self.table = Table(frame, dataframe=df, showtoolbar=True, showstatusbar=True)
        # 设置 Toplevel 尺寸
        frame.geometry(f"{width}x{height}")
        frame.title(title)
        self.table.show()

    # 定义函数以创建饼图和条形图作为子图
    def plot_piechart(self, df, var, figure, canvas, title=''):
        figure.clear()
        # 饼图（左侧子图）
        plot1 = figure.add_subplot(2, 1, 1)
        label_list = list(df[var].value_counts().index)
        colors = sns.color_palette("deep", len(label_list))
        _, _, autopcts = plot1.pie(
            df[var].value_counts(),
            autopct="%1.1f%%",
            colors=colors,
            startangle=30,
            labels=label_list,
            wedgeprops={"linewidth": 2, "edgecolor": "white"},  # 添加白色边框
            shadow=True,
            textprops={'fontsize': 7}
        )
        plot1.set_title("Distribution of " + var + " variable " + title, fontsize=10)

        # 条形图（右侧子图）
        plot2 = figure.add_subplot(2, 1, 2)
        ax = df[var].value_counts().plot(kind="barh", color=colors, alpha=0.8, ax=plot2)
        for i, j in enumerate(df[var].value_counts().values):
            ax.text(.7, i, j, weight="bold", fontsize=7)
        plot2.set_title("Count of " + var + " cases " + title, fontsize=10)

        figure.tight_layout()
        canvas.draw()

    def another_versus_response(self, df, feat, num_bins, figure, canvas):
        figure.clear()
        plot1 = figure.add_subplot(2, 1, 1)
        colors = sns.color_palette("Set2")
        df[df['Response'] == 0][feat].plot(ax=plot1, kind='hist', bins=num_bins, edgecolor='black', color=colors[0])
        plot1.set_title('Not Responsive', fontsize=15)
        plot1.set_xlabel(feat, fontsize=10)
        plot1.set_ylabel('Count', fontsize=10)

        data1 = []
        for p in plot1.patches:
            x = p.get_x() + p.get_width() / 2.
            y = p.get_height()
            plot1.annotate(format(y, '.0f'), (x, y), ha='center',
                           va='center', xytext=(0, 10),
                           weight="bold", fontsize=7, textcoords='offset points')
            data1.append([x, y])

        plot2 = figure.add_subplot(2, 1, 2)
        df[df['Response'] == 1][feat].plot(ax=plot2, kind='hist', bins=num_bins, edgecolor='black', color=colors[1])
        plot2.set_title('Responsive', fontsize=15)
        plot2.set_xlabel(feat, fontsize=10)
        plot2.set_ylabel('Count', fontsize=10)

        data2 = []
        for p in plot2.patches:
            x = p.get_x() + p.get_width() / 2.
            y = p.get_height()
            plot2.annotate(format(y, '.0f'), (x, y), ha='center',
                           va='center', xytext=(0, 10),
                           weight="bold", fontsize=7, textcoords='offset points')
            data2.append([x, y])

        figure.tight_layout()
        canvas.draw()

    # 在堆叠条形图内部放置标签
    def put_label_stacked_bar(self, ax, fontsize):
        # patches 是图表内的所有内容
        for rect in ax.patches:
            # 查找所有内容的位置
            height = rect.get_height()
            width = rect.get_width()
            x = rect.get_x()
            y = rect.get_y()
            # 条形的高度是数据值，可用作标签
            label_text = f'{height:.0f}'
            # ax.text(x, y, text)
            label_x = x + width / 2
            label_y = y + height / 2
            # 仅当高度大于指定值时绘制
            if height > 0:
                ax.text(label_x, label_y, label_text,
                        ha='center', va='center',
                        weight="bold", fontsize=fontsize)

    # 绘制一个变量对另一个变量的分布
    def dist_one_vs_another_plot(self, df, cat1, cat2, figure, canvas, title):
        figure.clear()
        plot1 = figure.add_subplot(1, 1, 1)
        group_by_stat = df.groupby([cat1, cat2]).size()
        colors = sns.color_palette("Set2", len(df[cat1].unique()))
        stacked_data = group_by_stat.unstack()
        group_by_stat.unstack().plot(kind='bar', stacked=True, ax=plot1, grid=True, color=colors)
        plot1.set_title(title, fontsize=12)
        plot1.set_ylabel('Number of Cases', fontsize=10)
        plot1.set_xlabel(cat1, fontsize=10)
        self.put_label_stacked_bar(plot1, 7)
        # 设置刻度标签字体
        plot1.tick_params(axis='both', which='major', labelsize=8)
        plot1.tick_params(axis='both', which='minor', labelsize=8)
        plot1.legend(fontsize=8)
        figure.tight_layout()
        canvas.draw()

    def box_plot(self, df, x, y, hue, figure, canvas, title):
        figure.clear()
        plot1 = figure.add_subplot(1, 1, 1)
        # 创建 Num_TotalPurchases 对比 Num_Dependants 的箱线图
        sns.boxplot(data=df, x=x, y=y, hue=hue, ax=plot1)
        plot1.set_title(title, fontsize=14)
        plot1.set_xlabel(x, fontsize=10)
        plot1.set_ylabel(y, fontsize=10)
        figure.tight_layout()
        canvas.draw()

    def choose_plot(self, df1, df2, chosen, figure1, canvas1, figure2, canvas2):
        print(chosen)
        if chosen == "Marital Status":
            self.plot_piechart(df2, "Marital_Status", figure1, canvas1)
        elif chosen == "Education":
            self.plot_piechart(df2, "Education", figure2, canvas2)
        elif chosen == "Country":
            # ... 后续逻辑省略
            pass
```

