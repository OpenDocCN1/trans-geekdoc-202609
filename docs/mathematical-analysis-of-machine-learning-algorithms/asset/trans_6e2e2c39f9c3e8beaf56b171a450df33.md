
## Spring Boot 3 实战案例

本项目是一个基于 Spring Boot 3 的实战项目，包含用户管理、商品管理、订单管理等核心模块。通过本案例，您将学会如何使用 Spring Boot 3 + MyBatis-Plus + Redis 构建一个完整的企业级应用。

### 一、技术栈

- 后端框架：Spring Boot 3.x
- 持久层框架：MyBatis-Plus 3.5.x
- 缓存中间件：Redis 7.x
- 数据库：MySQL 8.x
- 接口文档：Knife4j / OpenAPI 3.0
- 项目构建：Maven 3.8+

### 二、项目结构

```bash
spring-boot3-demo/
├── src/main/java/com/example/demo/
│   ├── controller/        # 控制层
│   ├── service/           # 业务层
│   ├── mapper/            # 数据访问层
│   ├── entity/            # 实体类
│   ├── config/            # 配置类
│   └── DemoApplication.java
├── src/main/resources/
│   ├── application.yml    # 配置文件
│   ├── mapper/            # MyBatis XML 映射
│   └── static/            # 静态资源
├── pom.xml
└── README.md
```

### 三、核心功能演示

以下为项目的核心接口示例：

```java
@RestController
@RequestMapping("/api/user")
@RequiredArgsConstructor
public class UserController {

    private final UserService userService;

    /**
     * 分页查询用户列表
     */
    @GetMapping("/page")
    public Result<PageResult<UserVO>> page(@Valid UserQuery query) {
        return Result.success(userService.page(query));
    }

    /**
     * 新增用户
     */
    @PostMapping
    public Result<Long> add(@Valid @RequestBody UserDTO dto) {
        return Result.success(userService.add(dto));
    }
}
```

### 四、数据库设计

| 字段名 | 类型 | 约束 | 说明 |
|--------|------|------|------|
| id | BIGINT | PK, AUTO_INCREMENT | 用户ID |
| username | VARCHAR(50) | NOT NULL, UNIQUE | 用户名 |
| password | VARCHAR(100) | NOT NULL | 密码（BCrypt加密） |
| email | VARCHAR(100) | 可空 | 邮箱 |
| status | TINYINT | DEFAULT 1 | 状态：1-正常，0-禁用 |
| create_time | DATETIME | DEFAULT CURRENT_TIMESTAMP | 创建时间 |

### 五、部署与运行

1. 克隆项目到本地：`git clone https://github.com/demo/spring-boot3-demo.git`
2. 修改 `application.yml` 中的数据库和 Redis 配置
3. 执行 `mvn spring-boot:run` 启动项目
4. 访问接口文档：`http://localhost:8080/doc.html`

## 7.1. 算法稳定性

稳定性可用于推导学习算法的期望泛化界。我们有以下结果，它表明稳定学习算法的期望泛化损失被期望训练损失所限制。

**定理 7.2** 如果算法 $\mathcal{A}$ 是 $\epsilon$-一致稳定的，则对于 $S_n \sim \mathcal{D}^n$,

$$
\mathbb{E}_{S_n}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),\mathcal{D}) \le \mathbb{E}_{S_n}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),S_n) + \epsilon.
$$

*证明* 考虑两个大小为 $n$ 的独立样本：$S_n = \{Z_1, \dots, Z_n\}$ 和 $S'_n = \{Z'_1, \dots, Z'_n\}$。令 $S_n^{(i)} = \{Z_1, \dots, Z_{i-1}, Z'_i, Z_{i+1}, \dots, Z_n\}$。令 $p_t^{(i)}$ 为 $\mathcal{A}$ 在 $S_n^{(i)}$ 下得到的分布。我们有

$$
\mathbb{E}_{S_n}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),\mathcal{D}) - \mathbb{E}_{S_n}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),S_n)
= \frac{1}{n}\sum_{i=1}^{n}\mathbb{E}_{S_n}\mathbb{E}_{S'_n}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n^{(i)}),Z_i)
 - \frac{1}{n}\sum_{i=1}^{n}\mathbb{E}_{S_n}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),Z_i)
$$

$$
= \frac{1}{n}\sum_{i=1}^{n}\mathbb{E}_{S_n}\mathbb{E}_{S'_n}\left[\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n^{(i)}),Z_i) - \mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),Z_i)\right] \le \epsilon.
$$

第一个等式利用了 $Z_i$ 与 $S_n^{(i)}$ 独立的事实，因此 $\phi(\mathcal{A}(S_n^{(i)}),Z_i)$ 的分布与 $Z \sim \mathcal{D}$ 时的 $\phi(\mathcal{A}(S_n),Z)$ 的分布相同。不等式使用了均匀稳定性的定义。$\square$

对于任何一致稳定算法，也有可能得到一个大概率陈述。证明依赖于留一估计的集中不等式，我们将其留到第 7.6 节（见定理 7.24）。利用这一结果，我们可以得到以下高概率结果，该结果将一致稳定算法的泛化损失用训练损失来限制。

**定理 7.3** 假设 $\mathcal{A}$ 是 $\epsilon$ 一致稳定的。令 $S_n = \{Z_1, \dots, Z_n\} \sim \mathcal{D}^n$ 和 $S'_n = \{Z'_1, \dots, Z'_n\} \sim \mathcal{D}^n$ 为来自 $\mathcal{D}$ 的 iid 数据的独立训练集和验证集。假设存在 $\alpha \in (0, 1)$，使得对于某个 $\delta \in (0, 1)$，期望验证损失与期望测试损失之间有以下不等式。以至少 $1 - \delta$ 的概率，

$$
\alpha \mathbb{E}_{S_n}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),\mathcal{D}) \le \frac{1}{n}\sum_{i=1}^{n}\mathbb{E}_{S_n}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),Z'_i) + \epsilon_n(\delta). \tag{7.1}
$$

则以至少 $1 - \delta$ 的概率，

$$
\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),\mathcal{D}) \le \mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),S_n) + (1 - \alpha)\mathbb{E}_{S_n}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),S_n) + \epsilon_n(\delta/2) + (2 + 5\lceil\log_2 n\rceil)\epsilon\ln(2/\delta) + (3 - \alpha)\epsilon.
$$

*证明* 我们定义

$$
g(S_n;z) = \mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),\mathcal{D}) - \mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),z).
$$

则 $\mathbb{E}_Z g(S_n;Z) = 0$ 且 $g(S_n;z)$ 是 $2\epsilon$ 一致稳定的。定理 7.24 意味着以至少 $1 - \delta/2$ 的概率，

$$
\bar{g}(S_{n+1}) \le 2\lceil\log_2 n\rceil\,\epsilon(1 + 2.5\ln(2/\delta)), \tag{7.2}
$$

其中

$$
\bar{g}(S_{n+1}) = \frac{1}{n}\sum_{i=1}^{n}\left[\left(\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_{n+1}^{(i)}),\mathcal{D}) - \mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_{n+1}^{(i)}),Z_i)\right) - \underbrace{\left(\mathbb{E}_{S_{n+1}^{(i)}}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_{n+1}^{(i)}),\mathcal{D}) - \mathbb{E}_{S_{n+1}^{(i)}}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_{n+1}^{(i)}),Z_i)\right)}_{\Delta_n}\right].
$$

这里 $S_{n+1} = S_n \cup \{Z_{n+1}\}$，其中 $Z_{n+1} \sim \mathcal{D}$ 与 $S_n$ 独立。此外，与定理 7.24 中一样，我们使用记号 $S_{n+1}^{(i)} = \{Z_1, \dots, Z_{i-1}, Z_{n+1}, Z_{i+1}, \dots, Z_n\}$。

在 (7.1) 中，我们注意到 $\mathbb{E}_{S_n}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),\mathcal{D})$ 是一个依赖于 $\mathcal{D}$ 的数，而 $\mathbb{E}_{S_n}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),Z_i)$ 仅依赖于 $Z_i$。因此通过将 $S_n$ 更改为 $S_{n+1}^{(i)}$ 并将 $Z'_i$ 更改为 $Z_i$，我们得到 (7.1) 的以下等价形式。以至少 $1 - \delta/2$ 的概率，

$$
\begin{aligned}
\Delta_n &= \frac{1}{n}\sum_{i=1}^{n}\left[\mathbb{E}_{S_{n+1}^{(i)}}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_{n+1}^{(i)}),\mathcal{D}) - \mathbb{E}_{S_{n+1}^{(i)}}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_{n+1}^{(i)}),Z_i)\right] \\
&\le (1-\alpha)\mathbb{E}_{S_n}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),\mathcal{D}) + \epsilon_n(\delta/2) \\
&\le (1-\alpha)\mathbb{E}_{S_n}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),S_n) + \epsilon_n(\delta/2) + (1-\alpha)\epsilon. \tag{7.3}
\end{aligned}
$$

第一个不等式等价于 (7.1)。第二个不等式使用了定理 7.2。根据并集界，可以得出以概率 $1 - \delta$，(7.2) 和 (7.3) 同时成立。这意味着

$$
\begin{aligned}
\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),\mathcal{D})
&\le \frac{1}{n}\sum_{i=1}^{n}\left[\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_{n+1}^{(i)}),\mathcal{D})\right] + \epsilon \\
&= \frac{1}{n}\sum_{i=1}^{n}\left[\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_{n+1}^{(i)}),Z_i)\right] + \bar{g}(S_{n+1}) + \Delta_n + \epsilon \\
&\le \frac{1}{n}\sum_{i=1}^{n}\left[\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_{n+1}^{(i)}),Z_i)\right] + 2\lceil\log_2 n\rceil\epsilon(1 + 2.5\ln(2/\delta)) \\
&\quad + (1-\alpha)\mathbb{E}_{S_n}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),S_n) + \epsilon_n(\delta/2) + (2-\alpha)\epsilon \\
&\le \frac{1}{n}\sum_{i=1}^{n}\left[\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),Z_i)\right] + 2\lceil\log_2 n\rceil\epsilon(1 + 2.5\ln(2/\delta)) \\
&\quad + (1-\alpha)\mathbb{E}_{S_n}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),S_n) + \epsilon_n(\delta/2) + (3-\alpha)\epsilon.
\end{aligned}
$$

在证明中，第一个不等式使用了 $\mathcal{A}$ 的均匀稳定性。第二个不等式使用了 (7.2) 和 (7.3)。第三个不等式使用了 $\mathcal{A}$ 的均匀稳定性。$\square$

### 示例 7.4

对于有界损失 $\phi(\cdot,\cdot) \in [0,1]$，我们可以应用加性 Chernoff 界并令 $\alpha = 1$ 且

$$
\epsilon_n(\delta) = \sqrt{\frac{\ln(1/\delta)}{2n}}
$$

在 (7.1) 中。这导致以下不等式。以至少 $1 - \delta$ 的概率，

$$
\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),\mathcal{D}) \le \mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),S_n) + (2 + 5\lceil\log_2 n\rceil)\epsilon\ln(2/\delta) + 2\epsilon + \sqrt{\frac{\ln(2/\delta)}{2n}}.
$$

我们注意到在示例 7.4 中，如果我们采用实现近似经验风险最小化的均匀稳定算法 $\mathcal{A}(S_n)$，那么 ERM 方法的标准分析（如第 3 章中的分析）中的相同论证可用于推导出以高概率成立的 $\mathcal{A}$ 的 oracle 不等式。使用稳定性分析而不是第 3 章中的经验过程推导此类结果的一个重要优点是，稳定性分析不必依赖覆盖数（或相关概念如 Rademacher 复杂度）。正如我们稍后将看到的，稳定性分析可用于诸如 SGD 之类的计算过程，对于这些过程，覆盖数的概念可能难以应用。

### 示例 7.5

对于有界损失 $\phi(\cdot,\cdot) \in [0,1]$，我们可以应用乘性 Chernoff 界 (2.11)，其中 $\alpha = 1 - \gamma$，$\gamma \in (0,1)$，且

$$
\epsilon_n(\delta) = \frac{\ln(1/\delta)}{2\gamma n}
$$

在 (7.1) 中。这导致以下不等式。以至少 $1 - \delta$ 的概率，

$$
\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),\mathcal{D}) \le \mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),S_n) + \gamma\mathbb{E}_{S_n}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),S_n) + (2 + 5\lceil\log_2 n\rceil)\epsilon\ln(2/\delta) + 3\epsilon + \frac{\ln(2/\delta)}{2\gamma n}.
$$

该结果意味着如果可以设计一个实现接近零训练损失的稳定学习算法，那么测试损失也将以很大概率接近零。也可以使用 Bernstein 不等式结合方差条件来获得类似的结果。我们将其留作练习。

除了均匀稳定性之外，我们还将考虑以下密切相关的留一稳定性概念。使用留一稳定性更容易定义训练数据依赖的稳定性，并允许不同的训练损失和测试损失，如 (6.1) 中所示。

### 定义 7.6

给定数据集 $S_n = \{Z_1, \dots, Z_n\} \subset S_{n+1} = \{Z_1, \dots, Z_n, Z_{n+1}\}$，令 $\epsilon(\cdot,\cdot)$ 为函数 $\mathcal{Z} \times \mathcal{Z}^{n+1} \to \mathbb{R}$。算法 $\mathcal{A}(S_n)$ 是 $\epsilon(\cdot,\cdot)$ 留一稳定的，如果存在 $\tilde{\mathcal{A}}(S_{n+1})$ 使得对于所有 $(Z_{n+1}, S_{n+1})$，

$$
\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),Z_{n+1}) - \mathbb{E}_{\mathcal{A}}\phi(\tilde{\mathcal{A}}(S_{n+1}),Z_{n+1}) \le \epsilon(Z_{n+1}, S_{n+1}),
$$

其中 $\mathbb{E}_{\mathcal{A}}$ 表示算法内部随机性的期望。
