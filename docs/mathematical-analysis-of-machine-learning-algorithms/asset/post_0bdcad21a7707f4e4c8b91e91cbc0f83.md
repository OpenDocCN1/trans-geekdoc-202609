
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

## 7.1. ALGORITHMIC STABILITY

Stability can be used to derive an expected generalization bound for a learning algorithm. We have the following result, which shows that the expected generalization loss of a stable learning algorithm is bounded by the expected training loss.

**Theorem 7.2** If an algorithm $\mathcal{A}$ is $\epsilon$-uniformly stable, then for $S_n \sim \mathcal{D}^n$,

$$
\mathbb{E}_{S_n}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),\mathcal{D}) \le \mathbb{E}_{S_n}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),S_n) + \epsilon.
$$

*Proof* Consider two independent samples of size $n$: $S_n = \{Z_1, \dots, Z_n\}$ and $S'_n = \{Z'_1, \dots, Z'_n\}$. Let $S_n^{(i)} = \{Z_1, \dots, Z_{i-1}, Z'_i, Z_{i+1}, \dots, Z_n\}$. Let $p_t^{(i)}$ be the distribution obtained by $\mathcal{A}$ with $S_n^{(i)}$. We have

$$
\mathbb{E}_{S_n}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),\mathcal{D}) - \mathbb{E}_{S_n}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),S_n)
= \frac{1}{n}\sum_{i=1}^{n}\mathbb{E}_{S_n}\mathbb{E}_{S'_n}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n^{(i)}),Z_i)
 - \frac{1}{n}\sum_{i=1}^{n}\mathbb{E}_{S_n}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),Z_i)
$$

$$
= \frac{1}{n}\sum_{i=1}^{n}\mathbb{E}_{S_n}\mathbb{E}_{S'_n}\left[\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n^{(i)}),Z_i) - \mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),Z_i)\right] \le \epsilon.
$$

The first equation used the fact that $Z_i$ is independent of $S_n^{(i)}$, and thus the distribution of $\phi(\mathcal{A}(S_n^{(i)}),Z_i)$ is the same as that of $\phi(\mathcal{A}(S_n),Z)$ with $Z \sim \mathcal{D}$. The inequality used the definition of uniform stability. $\square$

It is also possible to obtain a large probability statement for any uniformly stable algorithm. The proof relies on a concentration inequality for a leave-one-out estimate, which we leave to Section 7.6 (see Theorem 7.24). Using this result, we can obtain the following high-probability result that bounds the generalization loss in terms of training loss for uniformly stable algorithms.

**Theorem 7.3** Assume that $\mathcal{A}$ is $\epsilon$ uniformly stable. Let $S_n = \{Z_1, \dots, Z_n\} \sim \mathcal{D}^n$ and $S'_n = \{Z'_1, \dots, Z'_n\} \sim \mathcal{D}^n$ be independent training and validation sets of iid data from $\mathcal{D}$. Assume that there exists $\alpha \in (0, 1)$ such that for some $\delta \in (0, 1)$, we have the following inequality between the expected validation loss and the expected test loss. With probability at least $1 - \delta$,

$$
\alpha \mathbb{E}_{S_n}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),\mathcal{D}) \le \frac{1}{n}\sum_{i=1}^{n}\mathbb{E}_{S_n}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),Z'_i) + \epsilon_n(\delta). \tag{7.1}
$$

Then with probability at least $1 - \delta$,

$$
\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),\mathcal{D}) \le \mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),S_n) + (1 - \alpha)\mathbb{E}_{S_n}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),S_n) + \epsilon_n(\delta/2) + (2 + 5\lceil\log_2 n\rceil)\epsilon\ln(2/\delta) + (3 - \alpha)\epsilon.
$$

*Proof* We define

$$
g(S_n;z) = \mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),\mathcal{D}) - \mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),z).
$$

Then $\mathbb{E}_Z g(S_n;Z) = 0$ and $g(S_n;z)$ is $2\epsilon$ uniformly stable. Theorem 7.24 implies that with probability at least $1 - \delta/2$,

$$
\bar{g}(S_{n+1}) \le 2\lceil\log_2 n\rceil\,\epsilon(1 + 2.5\ln(2/\delta)), \tag{7.2}
$$

where

$$
\bar{g}(S_{n+1}) = \frac{1}{n}\sum_{i=1}^{n}\left[\left(\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_{n+1}^{(i)}),\mathcal{D}) - \mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_{n+1}^{(i)}),Z_i)\right) - \underbrace{\left(\mathbb{E}_{S_{n+1}^{(i)}}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_{n+1}^{(i)}),\mathcal{D}) - \mathbb{E}_{S_{n+1}^{(i)}}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_{n+1}^{(i)}),Z_i)\right)}_{\Delta_n}\right].
$$

Here $S_{n+1} = S_n \cup \{Z_{n+1}\}$ with $Z_{n+1} \sim \mathcal{D}$ independent of $S_n$. Moreover, as in Theorem 7.24, we use the notation $S_{n+1}^{(i)} = \{Z_1, \dots, Z_{i-1}, Z_{n+1}, Z_{i+1}, \dots, Z_n\}$.

In (7.1), we observe that $\mathbb{E}_{S_n}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),\mathcal{D})$ is a number that depends on $\mathcal{D}$, and $\mathbb{E}_{S_n}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),Z_i)$ depends only on $Z_i$. Therefore by changing $S_n$ to $S_{n+1}^{(i)}$ and $Z'_i$ to $Z_i$, we obtain the following equivalent form of (7.1). With probability at least $1 - \delta/2$,

$$
\begin{aligned}
\Delta_n &= \frac{1}{n}\sum_{i=1}^{n}\left[\mathbb{E}_{S_{n+1}^{(i)}}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_{n+1}^{(i)}),\mathcal{D}) - \mathbb{E}_{S_{n+1}^{(i)}}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_{n+1}^{(i)}),Z_i)\right] \\
&\le (1-\alpha)\mathbb{E}_{S_n}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),\mathcal{D}) + \epsilon_n(\delta/2) \\
&\le (1-\alpha)\mathbb{E}_{S_n}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),S_n) + \epsilon_n(\delta/2) + (1-\alpha)\epsilon. \tag{7.3}
\end{aligned}
$$

The first inequality is equivalent to (7.1). The second inequality used Theorem 7.2. It follows from the union bound that with probability $1 - \delta$, both (7.2) and (7.3) hold. This implies that

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

In the proof, the first inequality used uniform stability of $\mathcal{A}$. The second inequality used (7.2) and (7.3). The third inequality used the uniform stability of $\mathcal{A}$. $\square$

### Example 7.4

For bounded loss $\phi(\cdot,\cdot) \in [0,1]$, we can apply the additive Chernoff bound and let $\alpha = 1$ and

$$
\epsilon_n(\delta) = \sqrt{\frac{\ln(1/\delta)}{2n}}
$$

in (7.1). This leads to the following inequality. With probability at least $1 - \delta$,

$$
\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),\mathcal{D}) \le \mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),S_n) + (2 + 5\lceil\log_2 n\rceil)\epsilon\ln(2/\delta) + 2\epsilon + \sqrt{\frac{\ln(2/\delta)}{2n}}.
$$

We note that in Example 7.4, if we employ a uniformly stable algorithm $\mathcal{A}(S_n)$ that achieves approximate empirical risk minimization, then the same argument in the standard analyses of the ERM method (such as those in Chapter 3) can be used to derive an oracle inequality for $\mathcal{A}$ that holds in high probability. An important advantage of deriving such results using stability analysis instead of empirical process in Chapter 3 is that stability analysis does not have to rely on covering numbers (or related concept such as Rademacher complexity). As we will see later, stability analysis can be used with computational procedures such as SGD, for which the concept of covering numbers can be difficult to apply.

### Example 7.5

For bounded loss $\phi(\cdot,\cdot) \in [0,1]$, we can apply the multiplicative Chernoff bound (2.11) with $\alpha = 1 - \gamma$ for $\gamma \in (0,1)$, and

$$
\epsilon_n(\delta) = \frac{\ln(1/\delta)}{2\gamma n}
$$

in (7.1). This leads to the following inequality. With probability at least $1 - \delta$,

$$
\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),\mathcal{D}) \le \mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),S_n) + \gamma\mathbb{E}_{S_n}\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),S_n) + (2 + 5\lceil\log_2 n\rceil)\epsilon\ln(2/\delta) + 3\epsilon + \frac{\ln(2/\delta)}{2\gamma n}.
$$

The result implies that if one can design a stable learning algorithm that achieves near zero training loss, then the test loss is also near zero with large probability. One may also use Bernstein's inequality together with the variance condition to obtain a similar result. We leave it as an exercise.

In addition to uniform stability, we will also consider the following closely related concept of leave-one-out stability. It is easier to define training data dependent stability using leave-one-out stability, and to allow different training loss and test loss, as in (6.1).

### Definition 7.6

Given datasets $S_n = \{Z_1, \dots, Z_n\} \subset S_{n+1} = \{Z_1, \dots, Z_n, Z_{n+1}\}$, let $\epsilon(\cdot,\cdot)$ be a function $\mathcal{Z} \times \mathcal{Z}^{n+1} \to \mathbb{R}$. The algorithm $\mathcal{A}(S_n)$ is $\epsilon(\cdot,\cdot)$ leave-one-out stable if there exists $\tilde{\mathcal{A}}(S_{n+1})$ such that for all $(Z_{n+1}, S_{n+1})$,

$$
\mathbb{E}_{\mathcal{A}}\phi(\mathcal{A}(S_n),Z_{n+1}) - \mathbb{E}_{\mathcal{A}}\phi(\tilde{\mathcal{A}}(S_{n+1}),Z_{n+1}) \le \epsilon(Z_{n+1}, S_{n+1}),
$$

where $\mathbb{E}_{\mathcal{A}}$ denotes the expectation over the internal randomization of the algorithm.

