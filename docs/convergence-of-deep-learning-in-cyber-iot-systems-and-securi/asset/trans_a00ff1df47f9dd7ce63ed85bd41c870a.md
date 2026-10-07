

# DL 在网络-IoT 系统与安全中的收敛

## 11.4.3 基于读器的流程

1. $N_s = K_s \oplus N_t$ (11.1)
2. $AID_t = h(ID_{tj}||K_t||N_t||Tr_{seq})$ (11.2)
$AID_t$ 是拼接的哈希函数，$ID_{tj}||K_t||N_t||Tr_{seq}$
3. $EL = LAI_t \oplus (||K_t||N_t||)$ (11.3)
用于提供安全传输的哈希函数
4. $V_1 = h(AID_t||N_s||K_s||R_s||S_{od}||EL)$ (11.4)
$V_1$ 是 $AID_t||N_s||K_s||R_s||S_{od}$ 的哈希函数或
$pid_i \in_{enj} K \in_{rmi}$
$AID_i = pid_i, K_i = \in_{enj}$

在接收到 $M_t$（未知哈希值）后，将生成并计算一个数值，该信息位于后端以供安全传输。

## 11.4.4 后端服务器流程

生成 $Nr$
推导出 $Ny = Krs \oplus Nr$
$Ny$ 是 $Krs \oplus Nr$ 的异或运算结果
计算 $V_2 = hashing (MA1||Nr||Krs||LAir)$
$V_2$ 是 $MA1||Nr||Krs||LAir$ 的哈希函数
$AID_t, Kt, Nx, Ri, Sid$ 并检查其是否等于 $V_1$。

它在接收到来自后端服务器的消息后进行计算。后端服务器根据生成的随机数信息和哈希函数进行检查和计算，一旦安全可靠地完成了验证，将继续进行身份验证的进一步处理，并使用跟踪序列号进行更新 [25]。在接收信息后，所有信息被放入消息中，计算出的必要消息将被传输；另一端从服务器消息后，结合其标签信息进行计算，并发送回服务器进行身份验证过程。

## 11.4.5 读器侧最终计算与检查操作

$V^* = hash (R||N||K) = V$ (11.5)

$V_3^*$ 是 $\left(R|N|K\right)Tr_{rs}$ 的哈希函数

$N_i=K_{ts} \oplus N_x=K_{rs} \oplus V_y?? AID_t \text{ 和 } LAI_t$

$TR = hashing \left(K_{ts}||ID_{tj}||N_t\right) \oplus_{seqnew}$

$V_4=Tr(Tr||K_{ts}||ID_{tj}||N_t)$ (11.6)

$V_4$ 是 $Tr||K_t||ID_{tj}||N_t$ 的哈希函数

$V_3=h(Ri||N_t||K_{rs})$
$V_3$ 是 $Ri||N_t||K_{rs}$ 的哈希函数

$V^* = hashing(Tr||K||ID||N)=V$ (11.7)

计算并更新：

$Tr_{seqnew}=h(K_t||ID_{tj}||N_t) \oplus Tr$
$Tr_{seqnew}$ 是异或和哈希
$K_{tsnew}=hash(K_{ts}||ID_{tj}||Tr_{seqnew})$
$K_{tsnew}=h(ID_{tj}||kem_j) \oplus X, K_{ts}=K_{tsnew}$

该过程为保护隐私的相互认证策略提供了一种安全流程，其中信息经过加固以提高安全性，为智能应用中的本地化家庭安全提供了伪代码密钥生成以及前向安全性使用上的支持。这种方法还助于防止智能家居用例在正常网络中遭受克隆攻击、拒绝服务攻击，以及分布式拒绝服务（DDoS）攻击。

## 11.5 基于各种特征的所提方法与现有方法的观察结果

在此，我们根据表 11.2 所示的所提安全访问模型框架控制方案，对现有方法结合不同的特征或参数进行了对观测。

如表 11.2 所示，我们将不同模型在不同属性和特征下的性能与所提模型进行了对比。当我们在尝试与不同参数进行比较时，特别是在引入从读器到用户服务器的相互认证时，每个模型都有其局限；表 11.3 表明了所有通信方之间的执行总时间。

上述对比了现有模型与所提模型的执行总时间，显示了每个模型在与安全性特征对比时以毫秒为单位的反映。所提方法表现更好，时间为 0.94 毫秒，优于所有现有模型。所提模型的复杂度显示出更高水平的安全性。权衡值也被置于最高优先级。该研究用于带有生物识别模型的人脸识别，我们收集了面部表情并用于实验研究。

我们收集了包含不同脸部图像的数据集，并用于生物识别模型，如图 11.3 所示。不同面部的标签已保存在通信方服务器中，以对这些图像进行验证。从读器侧到后端服务器，身份验证过程从所有侧进行检查，并提供了不同部分的平均执行时间及其总平均时间。发现图像匹配方案更安全，且在不同的现有模型中应用更广泛，尽管与不同模型相比，其执行时间更长。

各种现有模型和所提模型的性能评估在结果 1 或图 11.4 中给出。所提方法在与现有模型对比时显示出更好的安全性，结果 11.5 所示，所提方法在执行时间上表现优异，证明了智能家居用例的。

表 11.2 基于各种特征的所提方法与现有方法的对比

| 方法 | 从所有侧进行身份验证 | 设备提供匿名性 | 设备提供安全性 | 设备提供本地化 | 扩展性 |
|---|---|---|---|---|---|
| 使用 SURF 的模型 | 不提供 | 不提供 | 不提供 | 不提供 | 不提供 |
| 使用 SIFT 的模型 | 不提供 | 不提供 | 不提供 | 不提供 | 不提供 |
| 使用 IMA 的模型 | 提供 | 不提供 | 不提供 | 不提供 | 不提供 |
| 所提模型 | 提供 | 提供 | 提供 | 提供 | 提供 |
（注：此处示例）

表 11.3 现有模型与所提模型的执行总时间

| 模型 | 执行总时间（ms） |
|---|---|
| 使用 SURF 的模型 | 0.59 |
| 使用 SIFT 的模型 | 0.41 |
| 使用 IMA 的模型 | 0.77 |
| 所提模型 | 0.94 |

图 11.3 用于生物识别模型的数据集

图 11.4 性能评估对比

图 11.5 执行时间对比

## 11.6 结论与未来工作

CONVERGENCE OF DL In Cyber-IoT Systems

246 CONVERGENCE OF DL In Cyber-IoT Systems

244 CONVERGENCE OF DL In Cyber-IoT Systems

242 CONVERGENCE OF DL In Cyber-IoT Systems

## 参考文献

1. Gope, P., Amin, R., Hafiz Islam, S., Kumar, N., Bhalla, V., Lightweight and privacy-preserving RFID authentication, secure city. Future Gen. Comput. Syst., 83, 629–637, 2018.
2. Akkaya, K., Guvenc, I., Aygun, R., Pala, N., Kadri, A., IoT-based occupancy for energy-efficient smart buildings. IEEE, 171, 1943–1952, 2020.
3. Hernández-Ramos, J., Victoria Moreno, M., Bernabé, J., Carrillo, D., Skarmenta, A., SAFIR: Secure access framework for IoT-enabled services on smart buildings. J. Comput. Syst., 8, 1452–1463, December 2015
4. Ziegelford, J., Garcia Monarch, O., Wehrle, K., Privacy in internet of things: Threats and challenges. ACM, 7, 12, 2728–2742, December 2014.
5. Martínez-Basél, A., Pérez-Martínez, P., Solanas, A., The pursuit of citizens: Privacy-aware smart city is possible. IEEE, 68, 2–6, 2020.
6. Zhang, K., Ni, J., Yang, K., Liang, X., Ren, J., Shen, X.S., Security and privacy in smart city applications: Challenges and solutions. Access Journal, 1–8, September 2018.
7. Celdrán, A.H., Clemente, E.J., Pérez, M.G., Pérez, G.M., SeCoMan: A semantic-aware framework for developing privacy-preserving and context-aware smart applications. IEEE Syst. J., 10, 3, 1–14, 2016.
8. Nguyen, T.A. and Aiello, M., Energy intelligent buildings based on user activity: A survey. Energy Build., 56, 244–257, 2013.
9. Arjunan, P., Saha, M., Choi, H., Gulati, M., Singh, A., Singh, P., Srivastava, M.B., SensorAct: A Decentralized and Scriptable Middleware for Smart Energy Buildings, IEEE, pp. 1–10, 2015.

