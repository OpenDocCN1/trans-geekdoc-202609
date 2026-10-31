
Actuations. The available data for control-oriented modes will typically be sparse, that is, data has to be replaced by good simplifying guesses.

## 14.5 教程：xROM

本教程旨在让读者亲身体验学习到的 Galerkin 过程。这包括 Galerkin expansion, Galerkin projection, 和 model calibration.

教程将完全依赖于数值软件包 xROM (Semaan et al. 2020)，它是一个可自由获取的工具 for ROM. One purpose of xROM is to perform a modal decomposition from snapshot data and to carry out the Galerkin projection using the Navier–Stokes equations. Moreover, xROM

- (i) can analyze native CFD and PIV data;
- (ii) can handle a large spectrum of 2D and 3D grids (Cartesian, structured, unstructured, etc.);
- (iii) can create modal expansions and other modes (e.g., shift modes);
- (iv) is user-friendly through a single configuration file;
- (v) is parallelizable.

On the full capabilities of xROM, the reader is referred to the user manual, which is included in the package.

对于本教程，我们将采用直接数值模拟 (DNS) of a cylinder flow at Re = 100 following Chapter 1 and duplicating the results presented in Noack et al. (2003).

本教程组织如下。In Section 14.5.1, we shall get acquainted with the numerical setup and the considered flow. General characteristics of xROM and how to use it are introduced in Section 14.5.2. We shall deploy xROM to perform three tasks in Section 14.5.3.

### 14.5.1 数值设置

我们考虑 Re = 100 时的 2D cylinder wake. The DNS is performed with an FEM of third-order accuracy in space and time. The computational domain Ω_DNS is bounded by the rectangle −5 < x < 15 and −5 < y < 5, excluding the cylinder Ω_cyl = {(x,y) : x² + y² ≤ 1/2}. Details can be inferred from Noack et al. (2003). Figures 14.3 and 14.4 provide an impression of the domain, the grid, and the periodic flow. In the ROM analysis, the observation domain Ω = Ω_DNS is identical to the computational domain.

### 14.5.2 xROM 的一般特性

### xROM 功能

xROM is mainly designed to generate POD Galerkin models for a wide range of flow problems. To accomplish this, it has several additional preprocessing tools and options

![](img/ddadb1d3eaa6f9576eea68f95d453bca_319_0.png)

图 14.3 无结构网格 for the FEM direct numerical simulation of cylinder wake.

![](img/ddadb1d3eaa6f9576eea68f95d453bca_319_1.png)

图 14.4 快照的流线.

that extend its capabilities and configurability. The main features that make the full version of xROM attractive are presented in the following.

**预处理：** Two tools are available for the preprocessing phase. First, a PIV converter that directly converts PIV snapshots from their original .txt or .dat format to snapshots readable by xROM. Second, a tool to reduce the domain according to user-defined specifications, to compute the POD modes only in a specific region of interest.

**格式：** xROM currently reads/writes two formats: CFD General Notation System CGNS, an efficient binary open-source format, and the ASCII format from Tecplot, .dat, which is widely used in the research community.

**案例类型：** xROM supports a wide variety of mesh types: Cartesian equidistant, Cartesian, structured, and unstructured grids, in 2D and 3D.

**并行化：** The software is fully parallelized using Massively Parallel Implementation (MPI), which offers several benefits.

### 要求和下载

xROM is distributed as a single binary executable file, which makes its usage very easy. It should work on any Linux distribution with a C library version 2.19 or newer. To check the C library version, run in a terminal:

```
$ ldd --version
```

对于本教程，您可以下载一个较轻版本的程序，该版本不包含 CGNS 功能（链接）。² The archive contains three items: the xROM software, the documentation, and the current sample case. Once the archive is extracted, open a terminal and go to where the binary is stored. Make sure that the binary is executable. If not, run:

```
$ chmod +x xROM
```

运行 xROM 时，程序需要输入文件夹的路径作为参数。有两种方法可以定义它：直接作为命令行参数指定，或使用弹出窗口。The two ways to define the input folder are shown in the following:

![](img/ddadb1d3eaa6f9576eea68f95d453bca_320_0.png)

![](img/ddadb1d3eaa6f9576eea68f95d453bca_320_1.png)

(a)

(b)

图 14.5 (a) 圆柱尾迹文件夹选择错误。 (b) 圆柱尾迹文件夹选择正确。

### 从命令行输入文件夹：

在这种情况下，只需在运行程序时指定案例文件夹的正确路径，例如：

```
$ ./xROM /absolute/path/to/folder
```

请注意，它必须是绝对路径，可使用以下命令找到：

```
$ pwd
```

### 从弹出窗口输入文件夹：

如果命令行中未定义路径，则会打开一个弹出窗口，用户必须在其中选择正确的文件夹。在这种情况下，正确的命令是：

```
$ ./xROM
```

请注意正确选择文件夹：只有当窗口的“Selection”字段包含完整路径（包括输入文件夹）时才有效。In practice, the user has to click twice on the case folder (i.e., enter the folder) to get the path, unlike other common GUIs where the user only has to click once. This is exemplified in Figure 14.5, which shows how the cylinder_wake folder is (a) wrongly and (b) correctly selected.

² https://cloudstorage.tu-braunschweig.de/getlink/fi9HQ68borJL8dJ9t4Yxv2au/

### 配置文件和执行步骤

配置文件包含要执行的所有过程及其选项：要使用的工具（PIV conversion, domain reduction, ...），要执行的步骤以及每个步骤的参数。它是用户唯一需要的控制输入。All capabilities of xROM can be set up in this configuration file.

输入的一般形式为

```
<parameter> : <value>
```

详细规范如下：

- 每行只有一个参数及其值。
- 参数和值由冒号“：”分隔。
- 行中的空格无关紧要。
- 文件中行的位置无关紧要：例如，如果参数定义在第一行或最后一行，结果相同。
- 要停用一个选项，用户必须在行开头添加注释符号“#”。

xROM 的标准流程分为三个主要步骤：

- 1. Galerkin expansion,
- 2. Galerkin projection,
- 3. dynamical system.

Each of these steps contains its own options and tools in the configuration file. The user can selectively execute individual steps. It is possible, for instance, to compute only the Galerkin expansion or the Galerkin expansion and the projection without the dynamical system.

### 14.5.3 练习

如第 14.5.1 节所述，我们将使用圆柱流动的 DNS 快照，这些快照包含在软件包的 CylinderWake/InputData/Snapshots 下。由于三个练习都使用相同的数据集，我们将使用相同的案例文件夹，并为每个练习自动生成不同的运行目录。在每次运行之前，我们将对配置文件进行必要的修改。

### 练习 1：圆柱流动的 Galerkin 展开

在本练习中，我们对计算的快照执行 POD。The configuration file for this exercise is located under CylinderWake/ConfigFile, which you can open with any text editor. Most of the options are self-explanatory. For more details, you are referred to the user manual.

如 ConfigFile 所见，只有第一步 GalerkinExpansion 已启用。其余均已禁用，因为这些选项与本练习无关。Besides activating GalerkinExpansion, the only other option we need to concern ourselves with is the BaseFlow selection, which we choose as MeanFlow.

使用 ./xROM 执行程序后，将生成一个名为 OutputData 的新文件夹。在其中，POD 结果位于 GalerkinExpansion 下。Here you should find the output of the entire Galerkin expansion, which includes:

- 作为 Tecplot 兼容的 .dat 文件的基础流。
- 相关矩阵。
- 特征值。
- POD 模态系数作为数组，以及 PODAmplitudesPlot 下的 .png 图像。
- POD 模态作为 PODModes 下的 Tecplot 兼容的 .dat 文件。
- POD 谱作为 .png 图像。

如果您希望自行绘制特征值和模态系数，只需禁用 plotFigures 选项即可。All generated field data are saved in ASCII format and are Tecplot-compatible.

检查模态和模态系数可揭示该脱落流动的预期结果：

- 湍动能高度集中在前几个模态中，并随模态数增加而迅速下降。
- 前 8 个模态（至少）之间存在强烈的模态配对。
- 模态对之间表现出相位差。
- 模态和模态系数各自由单一频率主导，该频率随模态对的升高而增加。

### 练习 2：无校准的 POD Galerkin 模型

现在，我们已经计算了 Galerkin 展开，我们将执行 Galerkin 投影并生成第一个降阶模型。为此，我们将在 ConfigFile 中按如下方式激活第二步（GalerkinProjection）和第三步（DynamicalSystem）：

```
GalerkinProjection : yes      # (yes, no)
DynamicalSystem : yes         # (yes, no)
```

GalerkinProjection 和 DynamicalSystem 分别对 POD 模态执行 Galerkin 投影并求解动力系统。You should leave all other parameters unchanged. We note here the deactivated model calibration option.

执行程序后，将在 outputData/Run2 下生成 Galerkin 投影和动力系统的两个新目录。Under GalerkinProjection, you should now have three data files: ConvectionTensor, ViscosityMatrix, and MassMatrix, which are the linear, quadratic, and mass matrix terms from the projection. Since there is no forcing and the POD modes are orthonormal, the resultant mass matrix is (within machine accuracy) a unity matrix.

