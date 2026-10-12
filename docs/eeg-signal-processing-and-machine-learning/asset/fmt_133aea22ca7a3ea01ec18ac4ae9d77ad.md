
# 学术与商业软件包对比表

| Name | Website (last visited in September 2020) | Inverse models |
| :--- | :--- | :--- |
| **Academic Software Packages** | | |
| Brainstorm | [https://neuroimage.usc.edu/brainstorm/](https://neuroimage.usc.edu/brainstorm/) | Dipole modelling, Beamformer, sLORETA, dSPM |
| Cartool | [https://sites.google.com/site/cartoolcommunity](https://sites.google.com/site/cartoolcommunity/) | Minimum Norm, LORETA, LAURA, Epifocus |
| EEGLab | [https://sccn.ucsd.edu/eeglab/index.php](https://sccn.ucsd.edu/eeglab/index.php) | Dipole modelling |
| FieldTrip | [http://www.fieldtriptoolbox.org](http://www.fieldtriptoolbox.org/) | Dipole modelling, Beamformer, Minimum Norm |
| LORETA | [http://www.uzh.ch/keyinst/loreta.htm](http://www.uzh.ch/keyinst/loreta.htm) | LORETA, sLORETA, eLORETA |
| MNE | [https://mne.tools/stable/index.html](https://mne.tools/stable/index.html) | MNE, dSPM, sLORETA, eLORETA |
| MUTMEG | [https://www.nitrc.org/projects/nutmeg](https://www.nitrc.org/projects/nutmeg) | Beamformer |
| SPM (mainly for fMRI) | [https://www.fil.ion.ucl.ac.uk/spm](https://www.fil.ion.ucl.ac.uk/spm/) | dSPM |
| **Commercial Software Packages** | | |
| BESA | [http://www.besa.de/products/besa‐research/besa‐research‐overview](http://www.besa.de/products/besa-research/besa-research-overview/) | Dipole modelling, RAP‐MUSIC, LORETA, sLORETA, LAURA, SSLOFO |
| Brainvision analyzer | [https://www.brainproducts.com](https://www.brainproducts.com/) | LORETA |
| BrainVoyager | [https://www.brainvoyager.com](https://www.brainvoyager.com/) | Beamformer, Minimum Norm, LORETA, LAURA |
| GeoSource | [https://www.egi.com/research-division/electrical-source-imaging/geosource](https://www.usa.philips.com/healthcare/solutions) | Minimum Norm, LORETA, sLORETA, LAURA |
| CURRY | [https://compumedicsneuroscan.com/curry‐source‐reconstruction](https://compumedicsneuroscan.com/curry-source-reconstruction/) | Dipole modelling, MUSIC, Beamformer, Minimum norm, sLORETA, eLORETA, SWARM |

在基于机器学习的方法中，特别是使用 `DNNs` 时，学习系统被训练以寻找皮层源位置的最佳排列，从而产生特定模式的多通道头皮 `EEG` 记录 [[92]](#c10.xhtml#c10-bib-0092)–[[98]](#c10.xhtml#c10-bib-0098)。

Abeyratne 等人 [[99]](#c10.xhtml#c10-bib-0099) 进行了早期关于使用人工神经网络（`ANNs`）进行脑源定位的研究。在他们的设计中，他们将头部模型、数据模型和传感器模型作为先验信息，同时考虑了球形头部模型和单源的简单场景。网络在已知偶极子位置的假设下对数据文件进行训练。在训练阶段，来自训练输出文件的偶极子参数向量（`X[p]`，`Y[p]`，`Z[p]`，`M[xp]`，`M[yp]`，`M[zp]`）及其对应的来自训练输入文件的头皮电压向量（`V1[p]`，`V2[p]`，…，`Vm[p]`）同时被应用到 `ANN`。头皮电压向量被设为输入，偶极子参数向量被设为目标输出。

在 [[100]](#c10.xhtml#c10-bib-0100) 中，用于求解逆单偶极子定位问题的前馈神经网络拥有一个包含 27 个神经元的输入层，对应电极处的 `M = 27` 个电位。输入层之后是一个或两个包含 `N` 个神经元的隐藏层。输出层最终包含产生所需偶极子参数的神经元。输入层神经元具有线性激活函数，而隐藏层和输出层神经元使用双曲正切激活函数。每个隐藏层和输出层神经元在其输入端都连接一个输出恒为 1 的偏置神经元，以允许激活函数具有非零阈值。呈现给网络的每个电位分布首先通过减去所有电位值的平均值进行平均参考化。随后，平均参考化后的电位通过除以最大电位的幅度进行归一化。在简单球形头部模型（半径 9.2 cm）中，偶极子位置参数相对于外头部边界半径归一化为 1。对于真实形状的头部模型，位置参数相对于头皮-空气界面的最佳拟合球半径进行归一化。给定位置的最优偶极子方向（在最小二乘意义上）可以直接计算。因此，此处神经网络仅用于估计偶极子位置参数。

为测试系统，作者使用大量随机分布在皮层上的偶极子输入对其进行训练。作者实现了约 3.5 mm 的平均定位误差，该网络包含两个隐藏层。

在 [[101]](#c10.xhtml#c10-bib-0101) 中，正向和逆向问题均尝试使用 `ANNs` 解决，这些网络通过反向传播技术离线训练，以学习头部体积传导的复杂源-电位关系。一经训练，这些网络能够以合理的计算成本将其知识推广到定位大脑内的功能活动。

## 10.10 总结

仅从 `EEG` 和 `MEG` 信号进行源定位是一个病态的优化问题。这主要是因为源的数量未知。该数量可能随时间变化，特别是在调查 `EP` 或运动相关源时。大多数提出的算法属于 `ECD` 和 `LD` 两大类方法。上述某些方法（如 `sLORETA`）已实现商业化，并据报在许多应用中具有合理的结果。不同方法的混合系统似乎能给出更好的结果。如果提出的代价函数能受到来自临床发现或特定几何边界的额外信息约束，定位也可能更准确。头部介质的非均匀性是 `EEG` 源定位的另一个主要问题。这对 `MEG` 影响较小；必须进行全面的医学和物理学实验研究，以找到准确的头部模型。使用或融合其他模态（如 `fMRI`）确实能提高定位结果的准确性。脑源定位有许多潜在应用，如 `ERP` 信号定位 [[33]](#c10.xhtml#c10-bib-0033) 和用于 `BCI` 的 `MRPs` [[102]](#c10.xhtml#c10-bib-0102)，以及癫痫源定位 [[103]](#c10.xhtml#c10-bib-0103)。`EEG` 和 `MEG` 源定位的最新进展，包括计算密集型机器学习系统（如 `DNNs`）的应用，允许更准确地定位多个源。头部模型参数、电极位置和源的数量仍然是基于机器学习的源定位技术的主要需求。

## 参考文献

1.  **1** Miltner, W., Braun, C., Johnson, R.E., and Rutchkin, A.D.S. (1994). A test of brain electrical source analysis (BESA): a simulation study. Electroencephalography and Clinical Neurophysiology 91: 295–310.

2.  **2** Scherg, M. and Ebersole, J.S. (1994). Brain source imaging of focal and multifocal epileptiform EEG activity. Clinical Neurophysiology 24: 51–60.

3.  **3** Scherg, M., Best, T., and Berg, P. (1999). Multiple source analysis of interictal spikes: goals, requirements, and clinical values. Journal of Clinical Neurophysiology 16: 214–224.

4.  **4** Aine, C., Huang, M., Stephen, J., and Christopher, R. (2000). Multistart algorithms for MEG empirical data analysis reliably characterize locations and time courses of multiple sources. NeuroImage 12: 159–179.
