

## 用于 PC 的云端实时网络云分析的服务器与 Servlet 架构

575

# 下载速度

![](img/2b52fde0e707e8c2f05a10309c3f8982_586_0.png)

输入地址：192.168.16.108

Cloudant 数据库

下载速度
上传速度
接收的数据包
发送的数据包

图 5.69。更改实时监控的参数。

2. 例如，选择了“上传速度”参数，图表的的描述如图 5.70 所示发生动态变化。

用于 PC 的网络云分析

# 上传速度

![](img/2b52fde0e707e8c2f05a10309c3f8982_586_1.png)

输入地址：192.168.16.108

Cloudant 数据库

上传速度

图 5.70。参数改变后图表描述的动态变化。

### 5.3.9.2. 执行分析

- 1. 对于分类分析，点击“分类”按钮后，可以更改图 5.71 所示字段中的值。结果字段中会出现一个指示，用户需等待 Servlet 的响应。

576 T. P. Fowdur, L. Babooram, M. N-D-Ibn Nazir Rosun 和 M. Indoondomun

分类分析

| 下载速度: | 2000 | 上传速度: | 120 |
| :--- | :--- | :--- | :--- |
| 接收的数据包: | 1500 | 发送的数据包: | 800 |
| 活动 - KNN: | 请等待... | 活动 - MLP: | 请等待... | 分类 |

图 5.71。对 PC 执行分类分析。

- 2. 得到的结果如图 5.72 所示，显示了 KNN 和 MLP 分类的活动。

分类分析

| 下载速度: | 2000 | 上传速度: | 120 |
| :--- | :--- | :--- | :--- |
| 接收的数据包: | 1500 | 发送的数据包: | 800 |
| 活动 - KNN: | 流中 | 活动 - MLP: | 流中 | 分类 |

图 5.72。在指定特定参数时使用“预测”按钮获取分类分析。

- 3. 回归分析使用“预测”按钮进行，同时指定预测时间和窗口大小。该点接收的数据包数量将分别使用 MLR 和 MLP 进行预测。

回归分析

| 预测时间: | 10 | 窗口大小: | 20 |
| :--- | :--- | :--- | :--- |
| 接收包 - MLR: | 1231.15 | 接收包 - MLP: | 1231 | 预测 |

图 5.73。对 PC 执行回归分析。

### 6.3.9.3. 下载功能

- 1. 为了下载批量样本，在点击相应的“下载”按钮之前输入所需的数量。

下载到 CSV

| 下载最后 N 个: | 10 | 下载 |
| :--- | :--- | :--- |
| 按日期下载: | 2020年12月17日 | 下载 |

图 5.74。下载 PC 的最后 N 个样本。

- 2. 在此过程中，系统会向用户显示下载 .csv 文件的提示。用户可以直接打开文件，或使用“确定”按钮将其保存到设备上。

577 用于云端实时的服务器与 Servlet 架构

![](img/2b52fde0e707e8c2f05a10309c3f8982_588_0.png)

图 5.75。打开或保存 .csv 文件的提示。

- 3. 按日期下载的功能发生相同的过程，该字段以“MMM, DD YYYY”的格式输入，如图 5.76 所示月份为缩写。

| 下载到 CSV | | |
| :--- | :--- | :--- |
| 下载最后 N 个: 10 | 下载 | |
| 按日期下载: 2020年12月17日 | 下载 | |

图 5.76。按日期下载 PC。

## 参考文献

- [1] Cloudant, Java-Cloudant, GitHub, 2020. [在线]. 可: https://github.com/cloudant/java-cloudant. (访问 2020年12月8日).
- [2] Java2s, client-client-2.7.0.jar 文件. [在线]. 可: http://www.java2s.com/ref/java2s-downloadclient270jar-file.html. (访问 2020年12月8日).
- [3] Jfree, jfree/jfreechart, GitHub, 2020. [在线]. 可: https://github.com/jfree/jfreechart. (访问 2020年12月8日).
- [4] Mungi and Tanaka, JFreeChart, SourceForge, 2017年1月27日. [在线]. 可: https://sourceforge.net/projects/jfreechart/. (访问 2020年12月8日).
- [5] JAMA: A Java Matrix Package. [在线]. 可: https://math.nist.gov/javenumerics/jama/. (访问 2020年12月21日).
- [6] Maven Repository: org.json "json 20200518," MavenRepository. [在线]. 可: https://mvnrepository.com/artifact/org.json/json20200518. (访问 2020年12月21日).
- [7] 在你的 java 代码中使用 weka, Use weka in your java code - Weka Wiki. [在线]. 可: https://waikato.github.io/weka-use/weka_in_your_java_code/. (访问 2020年12月21日).
- [8] 下载并安装 Weka, Weka [在线]. 可: https://waikato.github.io/weka-wiki/downloading_weka/. (访问 2020年12月21日).
- [9] 文档
- [10] Java Neural Network Framework Neuroph. [在线]. 可: http://neuroph.org/
- [11] 文档
- [12] 文档
- [13] 文档
- [14] 文档
- [15] 文档
- [16] 文档
- [17] 文档
- [18] 文档
- [19] 文档
- [20] 文档
- [21] 文档

590 云端实时数据采集与客户端架构

