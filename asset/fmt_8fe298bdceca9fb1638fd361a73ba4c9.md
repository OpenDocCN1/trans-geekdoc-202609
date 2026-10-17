
`grid()` 方法用于指定每个标签在 tkinter 窗口网格中的行和列位置。

每个标签被放置在特定的行和列，可选内边距（`padx` 和 `pady`）和对齐（`sticky`）设置。

以下是每个标签在网格中的位置细分：

*   `self.label1` 放置在第 1 行，第 0 列。
*   `self.label2` 放置在第 3 行，第 0 列。
*   `self.label3` 放置在第 5 行，第 0 列。
*   `self.label4` 放置在第 7 行，第 0 列。
*   `self.label5` 放置在第 10 行，第 0 列。
*   `self.label6` 放置在第 12 行，第 0 列。

这些标签作为 tkinter 窗口中的描述性文本元素，向用户提供关于 GUI 应用程序中不同选项或功能的说明或信息。颜色用于区分标签，使其视觉上更具吸引力，或根据其用途或功能进行分类。

### 添加图形和画布

代码在 `Design_Window` 类中定义了一个名为 `add_canvas()` 的方法。该方法负责向 tkinter GUI 窗口添加画布组件。

```python
def add_canvas(self, root):
    # Menambahkan canvas1 widget pada root untuk menampilkan hasil
    self.figure1 = Figure(figsize=(6.2, 7), dpi=100)
    self.figure1.patch.set_facecolor("lightgray")
    self.canvas1 = FigureCanvasTkAgg(self.figure1, master=root)
    self.canvas1.get_tk_widget().grid(row=0, column=1, columnspan=1,
                                      rowspan=25, padx=5, pady=5, sticky="n")

    # Menambahkan canvas2 widget pada root untuk menampilkan hasil
    self.figure2 = Figure(figsize=(6.2, 7), dpi=100)
    self.figure2.patch.set_facecolor("lightgray")
    self.canvas2 = FigureCanvasTkAgg(self.figure2, master=root)
    self.canvas2.get_tk_widget().grid(row=0, column=2, columnspan=1,
                                      rowspan=25, padx=5, pady=5, sticky="n")
```

#### 代码解析

##### 1. `add_canvas()` 方法

*   该方法旨在向 tkinter 窗口添加画布组件。
*   它接受两个参数：`self`（类实例的引用）和 `root`（将添加画布组件的 tkinter 主窗口）。

##### 2. 添加画布组件

在此方法中添加了两个画布组件，均用于显示图形结果。

##### 3. 创建 Figure 对象

*   为每个画布创建一个 `Figure` 对象。在 matplotlib 中，`Figure` 是所有绘图元素的顶级容器。
*   `Figure` 对象配置了特定的尺寸和背景颜色。`figsize` 参数设置图形的宽度和高度，`dpi`（每英寸点数）决定图形的分辨率。
*   `patch.set_facecolor` 方法用于将图形（画布）的背景颜色设置为 "lightgray"。

##### 4. 创建画布组件

*   为每个画布创建一个 `FigureCanvasTkAgg` 对象。该对象将 `Figure` 与 tkinter 画布组件关联。
*   `self.canvas1` 代表第一个画布，`self.canvas2` 代表第二个画布。
*   `FigureCanvasTkAgg` 构造函数接受两个参数：`Figure` 对象和主（`root`）tkinter 窗口。

##### 5. 网格布局

*   `grid` 方法用于指定每个画布组件在 tkinter 窗口网格中的行和列位置。
*   两个画布组件被放置在特定的行和列，带有可选的内边距（`padx` 和 `pady`）和对齐（`sticky`）设置。
*   它们并排放置在同一行的不同列中，暗示了水平布局。

总之，此方法向 tkinter 窗口添加了两个画布组件，每个都能显示图形结果。画布组件与 `Figure` 对象关联，允许在 GUI 中渲染各种类型的图表或图形内容。画布的背景颜色设置为 "lightgray" 以提高视觉清晰度。

### 添加列表框

代码在 `Design_Window` 类中定义了一个名为 `add_listboxes()` 的方法。该方法负责向 tkinter GUI 窗口添加列表框组件并填充项目列表。

```python
def add_listboxes(self, root):
    # Menambahkan list widget
    self.listbox = tk.Listbox(root, selectmode=tk.SINGLE, width=35)
    self.listbox.grid(row=2, column=0, sticky='n', padx=5, pady=1)

    # Menyisipkan item ke dalam list widget
    items = [
        "Marital Status", "Education", "Country",
        "Age Group", "Education with Response 0",
        "Education with Response 1",
        "Country with Response 0", "Country with Response 1",
        "Customer Age", "Income", "Amount of Wines",
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

#### 代码解析

##### 1. `add_listboxes()` 方法

*   该方法旨在向 tkinter 窗口添加列表框组件。
*   它接受两个参数：`self`（类实例的引用）和 `root`（将添加列表框的 tkinter 主窗口）。

##### 2. 添加列表框组件

使用 `tk.Listbox(root, selectmode=tk.SINGLE, width=35)` 创建列表框组件，其中：

*   `root` 是放置列表框的 tkinter 窗口。
*   `selectmode=tk.SINGLE` 指定一次只能选择一项。
*   `width=35` 将列表框组件的宽度设置为 35 个字符。

##### 3. 网格布局

*   `grid()` 方法用于指定列表框组件在 tkinter 窗口网格中的行和列位置。
*   列表框放置在第 2 行，第 0 列，带有可选的内边距（`padx` 和 `pady`）和对齐（`sticky`）设置。

##### 4. 填充列表框

*   在 `items` 列表变量中定义了一组项目（字符串）。这些项目代表将在列表框中显示的选项。
*   循环遍历 `items` 列表中的每个项目，并使用 `insert` 方法将其插入列表框，索引为 `tk.END`，这会将每个项目添加到列表框的末尾。

##### 5. 配置列表框高度

使用 `config()` 方法将列表框的高度配置为与 `items` 列表中的项目数量相匹配。这确保了列表框中的所有项目均可见，无需滚动。

总之，此方法向 tkinter 窗口添加了一个列表框组件，允许用户从预定义的选项列表中选择一项。列表框填充了项目，并调整了高度以容纳所有项目而无需滚动。这在 GUI 中常用于为用户提供选择。

### 添加组合框

代码在 `Design_Window` 类中定义了一个名为 `add_comboboxes()` 的方法。该方法负责向 tkinter GUI 窗口添加组合框组件并填充选项列表。

```python
def add_comboboxes(self, root):
    # Create ComboBoxes
    self.combo1 = ttk.Combobox(root, width=32)
    self.combo1["values"] = [
        "Categorized Income versus Response",
        "Categorized Total Purchase versus Categorized Income",
        "Categorized Recency versus Categorized Total Purchase",
        "Categorized Customer Month versus Categorized Customer Age",
        "Categorized Amount of Gold Products versus Categorized Income",
        "Categorized Amount of Fish Products versus Categorized Total AmountSpent",
        "Categorized Amount of Meat Products versus Categorized Recency",
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
```

#### 代码解析

##### 1. `add_comboboxes()` 方法

该方法旨在向 Tkinter 窗口添加组合框（`Combobox`）控件。

它接受两个参数：`self`（类实例的引用）和 `root`（将添加组合框的 Tkinter 主窗口）。

##### 2. 添加组合框

在该方法中创建了多个组合框，每个组合框对应一组特定的选项。

每个组合框均使用 `ttk.Combobox(root, width=32)` 创建，其中：

*   `root` 是放置组合框的 Tkinter 窗口。
*   `width=32` 将组合框控件的宽度设置为 32 个字符。

##### 3. 填充组合框

每个组合框通过 `values` 属性填充一个值列表（选项）。

选项以字符串列表形式提供，例如 `["Option 1", "Option 2", ...]`。

##### 4. 网格布局

使用 `grid` 方法指定每个组合框控件在 Tkinter 窗口网格中的行和列位置。

每个组合框放置在特定的行和列，并可设置可选的内边距（`padx` 和 `pady`）和对齐方式（`sticky`）。

各组合框在网格中的具体位置如下：

*   `self.combo1` 放置在第 4 行，第 0 列。
*   `self.combo2` 放置在第 6 行，第 0 列。
*   `self.combo3` 放置在第 8 行，第 0 列。
*   `self.combo4` 放置在第 11 行，第 0 列。

每个组合框均提供下拉选项供用户选择。这些组合框允许用户在 GUI 应用程序中选择各种分析或建模选项，使其具有交互性和通用性。

### 在根窗口添加控件

在 `Main_Class` 中添加导入语句 `from design_window import Design_Window`。该语句用于将 `design_window` 模块中的 `Design_Window` 类导入到当前 Python 脚本或程序中。具体解析如下：

*   `from design_window`：指定要导入的模块（Python 文件）名称，此处为 `design_window`。
*   `import Design_Window`：指定模块后，使用 `import` 关键字表示要从该模块导入的内容。此处导入 `Design_Window` 类。

执行此导入语句后，即可在 `Main_Class` 脚本中访问 `Design_Window` 类。你可以创建该类的实例，并根据需要使用其方法和属性。

随后，创建 `Design_Window` 类的实例并向其添加控件。将以下代码放入 `Main_Class` 的 `initialize()` 方法中：

```python
###### Creates necessary objects
self.obj_window = Design_Window()

###### Places widgets in root
self.obj_window.add_widgets(self.root)
```

#### 代码功能解析

##### 1. 创建 `Design_Window` 实例

`self.obj_window = Design_Window()`：创建 `Design_Window` 类的一个实例，并将其赋值给变量 `self.obj_window`。该实例代表一个可添加控件的 GUI 窗口。

##### 2. 向 `Design_Window` 添加控件

*   `self.obj_window.add_widgets(self.root)`：调用 `Design_Window` 实例（`self.obj_window`）的 `add_widgets()` 方法，并传入 `self.root` 作为参数。
*   `add_widgets` 方法预期会向 `Design_Window` 实例（`self.obj_window`）添加各种控件（按钮、标签、列表框、组合框等）。

通过创建 `Design_Window` 实例并向其添加控件，你可以在 `Design_Window` 对象内组织 GUI 组件。这有助于保持代码模块化，并使 GUI 应用程序的布局和功能更易于管理。

现在，`main_class.py` 完整代码如下：
