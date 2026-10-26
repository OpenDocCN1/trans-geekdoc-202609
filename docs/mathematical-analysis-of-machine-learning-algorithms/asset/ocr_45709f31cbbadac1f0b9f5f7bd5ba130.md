# Spring Boot 3 实战案例

本项目是一个基于 Spring Boot 3 的实战项目，包含用户管理、商品管理、订单管理等核心模块。通过本案例，您将学会如何使用 Spring Boot 3 + MyBatis-Plus + Redis 构建一个完整的企业级应用。

# 一、技术栈

+   - 后端框架：Spring Boot 3.x
+   - 持久层框架：MyBatis-Plus 3.5.x
+   - 缓存中间件：Redis 7.x
+   - 数据库：MySQL 8.x
+   - 接口文档：Knife4j / OpenAPI 3.0
+   - 项目构建：Maven 3.8+

# 二、项目结构

```
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
```

# 三、核心功能演示

以下为项目的核心接口示例：

```
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
```

# 四、数据库设计

| 字段名 | 类型 | 约束 | 说明 |
|--------|------|------|------|
| id | BIGINT | PK, AUTO_INCREMENT | 用户ID |
| username | VARCHAR(50) | NOT NULL, UNIQUE | 用户名 |
| password | VARCHAR(100) | NOT NULL | 密码（BCrypt加密） |
| email | VARCHAR(100) | 可空 | 邮箱 |
| status | TINYINT | DEFAULT 1 | 状态：1-正常，0-禁用 |
| create_time | DATETIME | DEFAULT CURRENT_TIMESTAMP | 创建时间 |

# 五、部署与运行

+   1. 克隆项目到本地：`git clone https://github.com/demo/spring-boot3-demo.git`
+   2. 修改 `application.yml` 中的数据库和 Redis 配置
+   3. 执行 `mvn spring-boot:run` 启动项目
+   4. 访问接口文档：`http://localhost:8080/doc.html`