

其中 \(p_1 = 0.965\)、\(p_2 = 0.95\)、\(p_3 = 0.93\) 为系统的极点；且 \(c_0 = 0.932\) 为常数。

### 13.4.4 糖尿病患者术后血压控制

控制糖尿病患者术后血压是一项重大挑战，因为糖尿病和高血压相互关联，因此需要持续观察和控制。通过获取自动药物输注技术可以克服这一问题。一般来说，此类情况下可通过在建议水平下使用 SNP 来控制血压，如图 13.6 所示。BP 控制的 SNP 性能可表示为 [43]：

\(G_{BP}(s) = \frac{\Delta P d(s)}{I_i(s)} = \frac{k e^{-T_i s}(1 + \alpha e^{-T_c s})}{\tau s + 1}\) (13.6)

- 其中 \(\Delta P d(s) =\) 压力差（mmHg）；
- \(I_i (s) =\) SNP 输注速率（ml h\(^{-1}\)）；
- \(k =\) 患者灵敏度（\(k\) 值越高表示患者越敏感）；
- \(\alpha =\) 循环指数；
- \(\tau =\) 时间常数；
- \(T_i =\) 开口传输延迟；
- \(T_c =\) 循环时间。

一般来说，建模分为三种类型：标准型、敏感型和非敏感型。表 13.4 说明了所有三种建模类型的不同模型参数值，这些值会因人而异。

![](img/75406d5bb714dfd3e68fbbc717bd8f67_316_0.png)

图 13.6. 术后使用 PID 进行血压控制策略。

表 13.4. 模型参数。

| 参数 | 非敏感型 | 敏感型 | 标准型 |
|---|---|---|---|
| K | -0.179 | -9 | -0.714 |
| A | 0.4 | 0 | 0.4 |
| \(\tau\) | 60 | 20 | 30 |
| \(T_i\) | 75 | 30 | 45 |
| \(T_c\) | 60 | 30 | 40 |

### 13.4.5 使用 PM 进行心脏建模

为实现心率稳定，需要 PM、心脏和控制器的传递函数，如图 13.7 所示。PM 是一阶线性时变系统，可按 [74] 建模为：

\(G_p(s) = \frac{k}{1 + s\tau}\)

\(Ms^2 X(s) + Bs X(s) + K X(s) = F(s)\)
\(G_h^c = \frac{X(s)}{F(s)} = \frac{1}{Ms^2 + Bs + K}\)

- 其中：K = 稳态增益；
- M = 心肌体积；
- B = 心肌单元粘滞阻力的比例常数；
- K = 心肌单元扭转阻力的比例常数；
- F(s) = 心肌样本利用的力，该力通过电和电化学作用产生；
- X(s) = 心血管结构的运动；
- Gc h(s) = 心脏的闭环传递函数，考虑单位反馈。

### 13.4.6 肿瘤生长控制

在当今生活中，癌症是最严重的疾病，会增加死亡率。仅 2017 年就有约 1,373,500 人死于癌症，较 2012 年增加了 3% [75]。由于这一庞大数字，癌症患者的治疗高度依赖于化疗的有效性，如图 13.8 所示。通过使用带有 'Hahnfeldt 模型' [76] 的 PID 控制器可以克服这一问题。

\(\dot{x}_1 = -\lambda x_1 \ln \left( \frac{x_1}{x_2} \right)\)
\(\dot{x}_2 = b x_1 - d x_1^{2/3} x_2 - e x_2 g(t)\)
\(y = x_1\)

![](img/75406d5bb714dfd3e68fbbc717bd8f67_317_0.png)

图 13.7. 使用 PID 进行心脏病控制。

![](img/75406d5bb714dfd3e68fbbc717bd8f67_318_0.png)

图 13.8. 肿瘤生长控制使用 PID。

- 其中 x1 = 肿瘤大小（mm³）；
- x2 = 内皮细胞大小（mm³）；
- g = 受控抑制剂强度（mg kg⁻¹）；
- λ1 = 肿瘤发展速度（1/day）；
- b = 肿瘤对血管的刺激体积（1/day）；
- d = 先前形成的血管的内源性抑制（1/day.mm²）；
- e = 受控抑制剂对肿瘤血管的抗血管生成影响（kg/day.mg）。

### 13.5 结论

本文研究了 AI 与 PID 技术结合在医疗诊断领域的应用。为了在生物医学领域获得最卓越且最佳的响应，PID 控制器因其简单设计和智能调节策略而闻名。无噪声输入可为 PID 提供更高精度。PID 控制系统被研究用于控制不同的健康问题，例如糖尿病患者的胰岛素输注、术中及术后高血压（H-BP）的药物输注控制、肿瘤生长监测、用于早期控制关节炎的症状识别等。本文还研究了基于 AI 的 PID 与不同医疗技术的集成，以提高精度并增强诊断。讨论了基于 AI 的 PID 控制器、各种生物医学系统和药物输注控制系统的数学建模的有效性。本章中，基于 PID 控制器的生物医学系统帮助临床医生和控制工程师实时执行这种渐进且无害的输注方法，以实现系统输注自动化。所讨论的原型模型在医疗保健系统领域非常有效。

## 参考文献

- [1] Alley D E 2016 通过 Medicare 和 Medicaid 解决社会需求的负责任医疗社区 New Engl. J. Med. 374 8–11
- [2] ASTHO（州和地区卫生官员协会）。Medicaid 和公共卫生伙伴关系学习系列 http://astho.org/Health-Systems-Transformation/Medicaid-and-Public-Health-Partnerships/Learning-Series/Managed-Care
- [3] CMS（医疗保险和医疗补助服务中心）2019 年《医疗保险和医疗补助计划；患者保护与平价医疗法案；Medicare Advantage 组织和 Medicaid 管理护理计划、州 Medicaid 机构、CHIP 机构和 CHIP 管理护理实体、联邦促进交易所中的合格健康计划发行人以及医疗保健提供者拟议规则》。联邦纪事报 84 7610-80
- [4] Kissam S M, Beil H, Cousart C, Greenwald L M 和 Lloyd J T 2019 鼓励基于价值的支付的州：来自 CMS 州创新模式计划的经验 Milbank Quart. 97 506-42
- [5] Mendelson A, Kondo K, Damberg C, Low A, Motuapuaka M, Freeman M, O’Neil M, Relevo R 和 Kansagara D 2017 按效付费计划对健康、医疗保健使用和护理流程的影响：一项系统综述 Ann. Intern. Med. 166 341–55
- [6] Israeli S T 和 Verghese A 2019 人性化人工智能 JAMA 321 29–30
- [7] Patel V, Chatterji S, Chisholm D, Ebrahim S, Gopalakrishna G, Mathers C 和 Reddy K S 2011 印度的慢性疾病和伤害 Lancet 377 413–28
- [8] Murray C J L, Inoue M 和 Lopez A D 1997 按病因分类的死亡率和伤残替代预测 1990–2020：全球疾病负担研究 Lancet 349 1498–504
- [9] Govind K A 和 Sekhar R A 2014 心脏起搏器新型 PID 控制器设计 2014 Int. Conf. on Advances in Green Energy (ICAGE) (Piscataway, NJ: IEEE) pp 82–7
- [10] Sarangi L, Mohanty M N 和 Patnaik S 2017 使用模糊推理系统检测异常心脏状况 Int. J. Autom. Control 11 372–83
- [11] Sarangi L, Mohanty M N 和 Patnaik S 2016 使用频谱域变换的 E-医疗系统诊断代理中的危急心脏状况分析 Indian J. Sci. Technol. 9 1–7
- [12] Sarangi L, Mohanty M N 和 Patnaik S 2016 用于心血管疾病检测的基于 ANFIS 的 E-医疗保健系统设计 Recent Developments in Intelligent Systems and Interactive Applications (Berlin: Springer International Publishing) pp 445–53
- [13] Sarangi L, Mohanty M N 和 Patnaik S 2015 用于心脏病检测的智能决策支持系统 Int. J. Control. Theory Appl. 8 2137–43
- [14] Mohanty M D, Patnaik D, Parida M, Mohanty S 和 Mohanty M N 2019 医疗保健系统中 CCU/ICU 患者智能马桶的智能 PID 控制器设计 Int. Conf. on Intelligent Computing and Applications (Singapore: Springer) pp 97–107
- [15] Yen J 和 Langari R 1999 模糊逻辑。智能、控制和信息 (Englewood Cliffs, NJ: Prentice-Hall)
- [16] Zhou Y S 和 Lai L Y 2000 使用遗传算法对模糊控制器进行最优设计 IEEE Trans. Ind. App. 1 93–7
- [17] Vaishnav S R 和 Khan Z J 2007 用于高阶系统的具有较小规则集的 PID 和模糊逻辑控制器的设计与性能 Proc. of the World Congress on Engineering and Computer Science pp 24–6
- [18] Venugopal P, Ganguly A 和 Singh P 2013 使用模糊逻辑设计 PID 控制器调节方法 Int. J. Emerg. Trends Eng. Dev. 5 239–48
- [19] Mallesham G 和 Rajani A 2006 使用模糊逻辑对 PID 控制器进行自动调节 8th Int. Conf. on Development and Application Systems pp 120–7
- [20] Sharma S 和 Ma K K 2015 通过 PI、PD、PID 控制器对耦合罐系统液位控制的分析 Int. J. Sci. Res. 4 294–6

