

### 表 7.4 不同血压病例配对获得的 *P* 值

| | BMI | HR | 年龄 |
|---|---|---|---|
| 高血压–临界高血压 | 0.013 | 0.36 | 0.007 |
| 临界高血压–正常 | 0.000 | 0.005 | 0.000 |
| 正常–高血压 | 0.000 | 0.005 | 0.000 |

最后，基于所提出的线性回归模型，实现了一个基于智能手机的 Android 应用程序，用于预测 SBP 和 DBP 值。图 7.4 展示了基于用户输入的年龄、HR 和 BMI 来预测血压的 Android 应用程序。图 7.4a 和 7.4b 分别显示了 Android 应用程序的主屏幕和应用程序预测 SBP 与 DBP 值的界面。

![图 7.4 Android 应用程序。(a) Android 应用程序主屏幕和 (b) Android 应用程序预测血压。](images/Fig07_04.jpg)

**图 7.4** Android 应用程序。(a) Android 应用程序主屏幕和 (b) Android 应用程序预测血压。

### 7.4.1 局限性与未来展望

所提出的研究存在一些局限性。获取的数据集不符合 AAMI 或 BHS 标准的标准，无法据此观察模型的性能。此外，在 Bland-Altman 图中可见一种趋势，即误差值在高和低血压值处增加。未来，可以根据国际标准协议收集更多数据集，以改进血压估计值。此外，基于深度学习框架的物联网系统可将该工作扩展至改善医疗保健系统以及连续血压监测 [25, 26]。

## 7.5 结论

在本研究中，基于生物特征参数的独立效应，提出了一种无创且非阻塞性的血压估计回归模型。对于即时检测（POC）应用，还实现了一个基于 Android 的平台，以在远程环境中连续监测血压。此外，BMI 显示出是血压测量的强预测因子，高 BMI 是高血压的风险增加因素。但现有模型的局限性在于，预测血压的性别相关差异未包含在本研究中。对于未来的研究，建议纳入性别差异对血压和 BMI 双方的影响，以便在更大样本量中验证该模型。

## 致谢

我们感谢印度加尔各答 EKO 心脏基金会的 Sankar Mitra 博士，以及印度加尔各答 NCS Diagnostics 的 Kamal Oswal 博士，感谢他们在整个工作过程中的帮助和指导。

## 参考文献

1.  **WHO**, “Global health observatory data,” <http://web.archive.org/web/www.who.int/gho/ncd/riskfactors/bloodpressureprevalencetext/en/>, 2016 [Accessed: 2016-12-8].

2.  **M. C. Staff**, “High blood pressure (hypertension),” <http://web.archive.org/web/http://www.mayoclinic.org/diseases-conditions/high-blood-pressure/in-depth/high-blood-pressure/art-20045868>, 2016 [Accessed: 2016-12-22].

3.  **W. B. Droyvold, K. Midthjell, T. I. L. Nilsen, and J. Holmen**, “Change in body mass index and its impact on blood pressure: a prospective population study,” *International Journal of Obesity*, vol. 29, no. 6, pp. 650–655, 2005.

4.  **J. S. Kaufman, M. C. Asuzu, J. Mufunda, T. Forrester, R. Wilks, A. Luke, A. E. Long, and R. S. Cooper**, “Relationship between blood pressure and body mass index in lean populations,” *Hypertension*, vol. 30, no. 6, 1997.

5.  **J. Y. Kim, B. H. Cho, S. M. Im, M. J. Jeon, I. Y. Kim, and S. Kim**, “Comparative study on artificial neural network with multiple regressions for continuous estimation of blood pressure,” in *IEEE International Conference Engineering in Medicine and Biology Society (EMBC)*, 27th Annual Conference, Shanghai, China, 2005, pp. 6942–6945.

6.  **S. S. Franklin, W. Gustin, N. D. Wong, M. G. Larson, M. A. Weber, W. B. Kannel, and D. Levy**, “Hemodynamic patterns of age-related changes in blood pressure,” *Circulation*, vol. 96, no. 1, pp. 308–315, July 1997.

7.  **S. Landahl, C. Bengtsson, J. A. Sigurdsson, A. Svanborg, and K. Svärdsudd**, “Age-related changes in blood pressure,” *Hypertension*, vol. 8, no. 11, pp. 1044–1049, 1986.

8.  **M. Jain, N. Kumar, and S. Deb**, “An affordable cuff-less blood pressure estimation solution,” in *International Conference of the IEEE Engineering in Medicine and Biology Society (EMBC)*, Lake Buena Vista, FL, Aug 2016.

9.  **M. Kachuee, M. M. Kiani, H. Mohammadzade, and M. Shabany**, “Cuff-less blood pressure estimation algorithms for continuous health-care monitoring.” *IEEE Transactions on Bio-Medical Engineering*, vol. 9294, no. c, pp. 1–11, 2016.

10.  **R. Murthy and D. Kotz**, “Assessing blood-pressure measurement in tablet-based mHealth apps,” in *Sixth International Conference on Communication Systems and Networks (COMSNETS)*, Bangalore, India, 2014.

11.  **B. Jana, K. Oswal, S. Mitra, G. Saha, and S. Banerjee**, “Windkessel model-based cuffless blood pressure estimation using continuous wave doppler ultrasound system,” *IEEE Sensors Journal*, vol. 20, no. 17, pp. 9989–9999, 2020.

12.  **S. Lee and J.-H. Chang**, “Oscillometric blood pressure estimation based on deep learning,” *IEEE Transactions on Industrial Informatics*, vol. 13, no. 2, pp. 461–472, 2017.

13.  **Harvard Heart Letter**, “Don’t trust this smartphone app to measure your blood pressure,” <http://www.health.harvard.edu/heart-health/dont-trust-this-smartphone-app-to-measure-your-blood-pressure>, 2016 [Accessed: 2016-12-15].

14.  **M. Hall, E. Frank, G. Holmes, B. Pfahringer, P. Reutemann, and I. H. Witten**, “The WEKA data mining software,” *ACM SIGKDD Explorations Newsletter*, vol. 11, no. 1, 2009.

15.  **E. T. Lee and J. W. Wang**, *Statistical Methods for Survival Data Analysis*, 4th ed. Wiley Publishing, New York, 2013.

16.  **R. O. Duda, P. E. Hart, and D. G. Stork**, *Pattern Classification* (2nd Edition). Wiley-Interscience, New York, 2000.

17.  **G. Developers**, “Android developers,” <https://developer.android.com/index.html>, 2016 [Accessed: 2016–10–09].

18.  **“Non-Invasive Sphygmomanometers—Part 2: Clinical Validation of Automated Measurement Type, ANSI/AAMI/ISO Standard 81060-2,”** 2009.

19.  **E. O’brien, J. Petrie, W. Littler, M. De Swiet, P. L. Padfield, D. G. Altmanu, M. Blandg, A. Coats, and N. Atkins**, “The British Hypertension Society protocol for the evaluation of blood pressure measuring devices,” *Journal of Hypertension*, vol. 11, no. 2, pp. 43–62, 1993.

20.  **S. Puke, T. Suzuki, K. Nakayama, H. Tanaka, and S. Minami**, “Blood pressure estimation from pulse wave velocity measured on the chest,” in *35th Annual International Conference Engineering in Medicine and Biology Society (EMBC)*, Osaka, Japan, 2013.

21.  **D. Giavarina**, “Understanding Bland Altman analysis,” *Biochemia medica*, vol. 25, no. 2, pp. 141–151, 2015.

22.  **N. K. Mungreiphy, S. Kapoor, and R. Sinha**, “Association between BMI, blood pressure, and age: study among Tangkhul Naga tribal males of Northeast India,” *Journal of Anthropology*, vol. 2011, pp. 1–6, 2011.

23.  **M. Szumilas**, “Explaining odds ratios,” *Journal of the Canadian Academy of Child and Adolescent Psychiatry*, vol. 19, no. 3, pp. 227–229, Aug 2010.

