
![](img/dd2f1e467aed0a84f984e6e656b2cc0f_249_0.png)

图8.10 朴素模型与MLP-ANN预报模型在不同预见期下的性能比较。

表8.6 MLP-ANN预报模型中的隐藏节点（神经元）数量。

| 输入变量 | 输出变量 | 隐藏节点 |
|---|---|---|
| RF_t-14, RF_t-13, RF_t-12, RF_t-11, RF_t-10, Q_t-2, Q_t-1, Q_t | Q_t+1 | 7 |
| RF_t-13, RF_t-12, RF_t-11, RF_t-10, RF_t-9, Q_t-2, Q_t-1, Q_t | Q_t+2 | 7 |
| RF_t-12, RF_t-11, RF_t-10, RF_t-9, RF_t-8, Q_t-2, Q_t-1, Q_t | Q_t+3 | 6 |
| RF_t-11, RF_t-10, RF_t-9, RF_t-8, RF_t-7, Q_t-2, Q_t-1, Q_t | Q_t+4 | 7 |
| RF_t-10, RF_t-9, RF_t-8, RF_t-7, RF_t-6, Q_t-2, Q_t-1, Q_t | Q_t+5 | 7 |
| RF_t-9, RF_t-8, RF_t-7, RF_t-6, RF_t-5, Q_t-2, Q_t-1, Q_t | Q_t+6 | 6 |
| RF_t-6, RF_t-5, RF_t-4, RF_t-3, RF_t-2, Q_t-2, Q_t-1, Q_t | Q_t+9 | 7 |
| RF_t-3, RF_t-2, RF_t-1, Q_t-2, Q_t-1, Q_t | Q_t+12 | 7 |

## 8.7. 业务化MLP-ANN预报模型

经过训练的MLP-ANN模型可结合实时观测数据，为Grande de San Miguel流域的洪水形势提供指导。许多预报系统可用作环境决策支持系统，以组织实时的复杂数据采集过程，并将模型与这些水文气象数据联系起来。

根据Werner等人（2013）的定义，预报系统可分为两类：模型中心法和模块化方法。前者基本上意味着模型或所用数据的任何变化都可能需要对系统进行重新设计和重新开发。后者是一种更灵活的方法，能够适应建模要求和数据转换方面的变化。在训练并验证MLP-ANN之后，决定采用模型中心法将所开发的MLP-ANN模型投入业务化运行，因为萨尔瓦多环境和自然资源部没有任何模块化预报平台（如Delft-FEWS）。预报系统的概念设计如图8.11所示，其中Grande de San Miguel流域的所有实时降雨量和水位均通过MATLAB例程从MARN数据库导入。随后，另一个MATLAB例程用于预处理实时观测数据，以删除错误数据、检测异常值、将水位转换为流量单位，并将水文气象数据从15分钟的时间步长聚合为1小时。随后，逐小时降雨量和流量数据用于

![](img/dd2f1e467aed0a84f984e6e656b2cc0f_250_0.png)

图8.11 Grande de San Miguel流域业务化MLP-ANN预报的概念设计。

## 致谢

我要感谢萨尔瓦多环境和自然资源部（MARN）提供本研究使用的数据。

## 参考文献

- Abrahart, R. J., & See, L. (2000). Comparing neural network and autoregressive moving average techniques for the provision of continuous river flow forecasts in two contrasting catchments. *Hydrological Processes*, 14(11–12), 2157–2172.
- Abrahart, R. J., & See, L. M. (2007). Neural network modeling of non-linear hydrological relationships. *Hydrology and Earth System Sciences*, 11(5), 1563–1579.
- Ahani, A., Shourian, M., & Rad, P. R. (2018). Performance assessment of the linear, nonlinear and non-parametric data driven models in river flow forecasting. *Water Resources Management*, 32(2), 383–399.
- Badrzadeh, H., Sarukkalige, R., & Jayawardena, A. W. (2015). Hourly runoff forecasting for flood risk management: Application of various computational intelligence models. *Journal of Hydrology*, 529, 1633–1643. https://doi.org/10.1016/j.jhydrol.2015.07.057
- Bowden, G. J., Dandy, G. C., & Maier, H. R. (2005). Input determination for neural network models in water resources applications. Part 1, Background and methodology. *Journal of Hydrology*, 301(1–4), 75–92. https://doi.org/10.1016/j.jhydrol.2004.06.021
- Chacon-Hurtado, J. (2012). *Streamflow forecast for hydropower generation-a data assimilation approach* (PhD Thesis). Unesco-IHE.
- Corzo, G. A., Solomatine, D. P., de Wit, M., Werner, M., Uhlenbrook, S., & Price, R. K. (2009). Combining semi-distributed process-based and data-driven models in flow simulation: A case study of the Meuse River basin. *Hydrology and Earth System Sciences*, 16.
- Corzo Perez, G. A. (2009). *Hybrid models for hydrological forecasting: Integration of data-driven and conceptual modeling techniques*. IHE Delft Institute for Water Education.
- Coulibaly, P., Anctil, F., & Bobée, B. (2000). Daily reservoir inflow forecasting using artificial neural networks with stopped training approach. *Journal of Hydrology*, 230 (3–4), 244–257.
- Dawson, C. W., & Wilby, R. L. (2001). Hydrological modeling using artificial neural networks. *Progress in Physical Geography: Earth and Environment*, 25(1), 80–108. https://doi.org/10.1177/030913330102500104
- Dayhoff, J. E. (1990). *Neural network architectures: An introduction*. Van Nostrand Reinhold Co.
- Fernando, D. A. K., & Jayawardena, A. W. (1998). Runoff forecasting using RBF networks with OLS algorithm. *Journal of Hydrologic Engineering*, 3(3), 203–209.
- Govindaraju, R. S., & Rao, A. R. (2013). *Artificial neural networks in hydrology* (Vol. 36). Springer Science & Business Media.
- Gupta, H. V., Kling, H., Yilmaz, K. K., & Martinez, G. F. (2009). Decomposition of the mean squared error and NSE performance criteria: Implications for improving hydrological modeling. Journal of Hydrology, 377(1–2), 80–91. https://doi.org/10.1016/j.jhydrol.2009.08.003
- Gupta, H. V., Sorooshian, S., & Yapo, P. O. (1998). Toward improved calibration of hydrologic models: Multiple and noncommensurable measures of information. Water Resources Research, 34(4), 751–763. https://doi.org/10.1029/97WR03495
- Häggström, M., & Lindström, G. (1990). Application of the HBV model for flood forecasting in six Central American rivers. SMHI. http://urn.kb.se/resolve?urn=urn:nbn:se:smhi:diva-2454
- Hsu, K., Gupta, H. V., & Sorooshian, S. (1995). Artificial neural network modeling of the rainfall-runoff process. Water Resources Research, 31(10), 2517–2530.
- Hu, T., Wu, F., & Zhang, X. (2007). Rainfall-runoff modeling using principal component analysis and neural network. Hydrology Research, 38(3), 235–248.
- Krause, P., Boyle, D. P., & Bäse, F. (2005). Comparison of different efficiency criteria for hydrological model assessment. Advances in Geosciences, 5, 89–97. https://doi.org/10.5194/adgeo-5-89-2005
- Lachtermacher, G., & Fuller, J. D. (1994). Backpropagation in hydrological time series forecasting. In Stochastic and statistical methods in hydrology and environmental engineering (pp. 229–242). Springer.
- Legates, D. R., & McCabe, G. J. (1999). Evaluating the use of “goodness-of-fit” measures in hydrologic and hydroclimatic model validation. Water Resources Research, 35(1), 233–241. https://doi.org/10.1029/1998WR900018
- Levenberg, K. (1944). A method for the solution of certain problems in least squares. Quarterly of Applied Mathematics, 2, 164–168. https://doi.org/10.1090/qam/10666
- Maier, H. R., & Dandy, G. C. (1996). The use of artificial neural networks for the prediction of water quality parameters. Water Resources Research, 32(4), 1013–1022.
- Marquardt, D. W. (1963). An algorithm for least-squares estimation of nonlinear parameters. Journal of the Society for Industrial and Applied Mathematics, 11(2), 431–441.
- Minns, A. W., & Hall, M. J. (1996). Artificial neural networks as rainfall-runoff models. Hydrological Sciences Journal, 41(3), 399–417.
- Nash, J. E., & Sutcliffe, J. V. (1970). River flow forecasting through conceptual models, part I: A discussion of principles. Journal of Hydrology, 10(3), 282–290.
- Rajurkar, M. P., Kothyari, U. C., & Chaube, U. C. (2002). Artificial neural networks for daily rainfall-runoff modeling. Hydrological Sciences Journal, 47(6), 865–877.
- Riverside Technology (2012). Development and implementation of a regional Flash Flood Guidance and Early Warning System: Lake Ilopango/Rio Jiboa, El Salvador. Technical Report, Riverside Technology, Colorado, USA.
- Servicio Hidrologico Nacional (2004). Sistema de alerta temprana por inundaciones. Experiencia en El Salvador. Technical Report, Servicio Nacional de Estudios Territoriales (SNET), San Salvador, El Salvador.

