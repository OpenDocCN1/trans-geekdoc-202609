

![](img/ddadb1d3eaa6f9576eea68f95d453bca_383_0.png)

图 17.3 GMFM 的无驱动动力学：驱动指令 b（左上）、增长率 σ（右上）、不稳定振子的相空间（左下）以及稳定振子的相空间（右下）。最后一个周期（T₁）用红色表示。圆圈（○）和点（●）分别代表振子的初始条件和最终状态。对于非控制系统，它们重合。该图使用 MATLAB 绘制，每周期 100 个点，共 100 个周期。

## Requirements

xMLC 软件使用 MATLAB 版本 9.2.0.556344（R2017a）编写。Natick, Massachusetts: The MathWorks Inc., 2017 以及 Octave 版本 4.2.2（2018）。John W. Eaton and others。因此，任何更高版本都应与该软件兼容。软件运行不需要特定的 MATLAB 包。对于 Octave，需要 communications 包。它可在官方网页 https://octave.sourceforge.io 上免费获取。也可通过图形用户界面使用 pkg 函数直接下载。

## Installation

xMLC 软件可从以下链接下载：

https://BerndNoack.com/programs/xMLC_v0.9.2.tar.gz

下载后，解压 xMLC_v0.9.2.tar.gz 文件并将 xMLC_v0.9.2 文件夹复制到所需位置。安装即完成。

为确保与 MATLAB 或 Octave 的兼容性，必须使用特定的文件。这些文件存储在 Compatibility/ 文件夹中。要在 MATLAB 和 Octave 之间切换，请在 Compatibility/ 文件夹中执行相应的 bash 文件 MatlabCompat.sh 或 OctaveCompat.sh。如果未使用 Linux 系统，请将 Compatibility/MATLAB/ 或 Compatibility/Octave/ 中的文件复制到对应文件夹。

有关 xMLC_v0.9.2 文件夹内容的更多信息，请参阅 README.md 文件。

## 17.5.3 Execution

要使用 xMLC 软件，请在 xMLC_v0.9.2 文件夹中启动 MATLAB 或 Octave 会话。然后运行 Initialization.m 脚本，并在兼容性方面替换文件，如第 17.5.2 节所述。该脚本加载所有必要的路径并创建一个带有 GMFM 基准问题的 xMLC 类对象。该对象默认存储在变量 mlc 下。要使用默认参数创建一个新的 xMLC 类对象，请使用以下命令：MyMLC = mlc;

以下部分描述了一些基本的 xMLC 参数和函数。所有命令均与 MATLAB 和 Octave 兼容，除了保存和加载函数是特定于每个软件的。

## xMLC parameters

启动 Initialization.m 脚本后，会打印出待解决问题的简要描述。它包含有关输入（控制器）数量、输出（传感器）数量、种群大小以及策略（遗传算子概率）的信息。每次创建新的 xMLC 类对象实例时都会显示此信息。要再次显示它，请使用 show_problem 方法，使用命令 mlc.show_problem;。mlc 对象有四个属性：

- population: 包含每个世代个体的所有信息和数据库引用；
- parameters: 定义所有参数的位置，无论是问题、控制律描述还是 xMLC 参数；
- table: 是数据库，包含探索过的所有个体，并非所有个体都因筛选选项而被评估；
- generation: 指当前世代的整数。默认情况下，当种群为空时设置为 0。

您可以使用以下命令访问和修改 xMLC 参数：

```matlab
% To display all the parameters
mlc.parameters % MATLAB only, for Octave see default_parameters.m
% To display parameters related to the problem definition
mlc.parameters.ProblemParameters % MATLAB only
% To display parameters related to the control law definition
mlc.parameters.ControlLaw % MATLAB only
% To display parameters related to the MLC algorithm
mlc.parameters.CrossoverProb
% To modify some MLC parameters
mlc.parameters.Elitism = 0;
mlc.parameters.CrossoverProb = 0.5;
```

```matlab
mlc.parameters.MutationProb = 0.5;
mlc.parameters.ReplicationProb = 0;
mlc.parameters.PopulationSize = 50;
```

在运行开始前不应修改问题参数和控制律参数；仅应考虑 xMLC 参数。要更改它们，请参阅第 17.5.4 节。

## My first run

设置好 xMLC 参数后，即可启动优化过程。个体种群的进化通过 go 方法完成。可以将世代数作为参数传入以执行多次进化迭代。无参数时执行一次进化步骤，从而评估生成的个体。过程结束后，xMLC 对象可以保存以供以后使用。所有运行都保存在 save_runs/ 文件夹中，并带有其名称和兼容性（MATLAB 或 Octave）。文件夹会自动创建。

```
% To compute the next generation and evaluate the new individuals.
mlc.go;
% To compute the next 5 generations :
mlc.go(5);
% To continue with the following 5 next generations :
mlc.go(10);
% Change the name of my run and save
mlc.parameters.Name = 'MyRun';
mlc.save_matlab; % for MATLAB
mlc.save_octave; % for Octave
% Load my run
mlc.load_matlab('MyRun'); % for MATLAB
mlc.load_octave('MyRun'); % for Octave
```

Octave 中的 for 循环不如 MATLAB 优化。因此，与 MATLAB 相比，使用 Octave 评估个体可能需要更长的时间。读者可通过调整 mlc.parameters.ProblemParameters 中的评估参数或 GMFM_problem.m 文件中的参数来根据自身需求优化个体的评估，见第 17.5.4 节。

## Post-Processing and Analysis

优化过程完成后，最佳个体可通过以下方法访问：mlc.best_individual;。该命令绘制有关最佳个体的信息。ID 号代表其在数据库中的索引。对于 GMFM 问题，会绘制最佳控制律的可视化，见图 17.4。第一个振子已成功稳定，而第二个振子已被去稳定化。此外，固定点仅在三个周期后才达到。增长率 σ 在 0 附近振荡，第二个振子位于半径为 √0.1 的极限环上。

有关最佳控制律的更多信息，请使用命令 `mlc.table.individuals(IDN)`; 其中 IDN 为最佳个体的 ID 号。其他特性如学习过程或 Pareto 前沿可通过命令 `mlc.convergence` 提取，见图 17.5。图 17.5(a) 显示，随着世代的推进，最佳控制的性能以及种群的整体性能都在提高。从第一代到最后一代，代价函数下降了一个数量级。在图 17.5(b) 中，推动 Pareto 前沿优化 $J_a$ 和 $J_b$ 的是最新世代，尽管惩罚参数仅为 $\gamma = 0.01$。

![](img/ddadb1d3eaa6f9576eea68f95d453bca_386_0.png)

**图 17.4** 与图 17.3 相同，为经过 100 个个体进化 10 代后计算得到的最佳控制律。

## 17.5.4 My MLC Problem

MLC 问题及其参数的定义由两个文件完成：`MyProblem_problem.m` 和 `MyProblem_parameters.m`。在 *Plant\MyProblem* 文件夹中提供了示例。问题参数和控制律参数应仅通过创建适当的 `MyProblem_parameters.m` 文件进行修改。这些参数包括惩罚参数 $\gamma$（gamma）、驱动限制、常数数量、算子（+, −, ×, ÷, ...）、寄存器初始化等。用户可自由对 *MyProblem* 文件进行任何修改。

