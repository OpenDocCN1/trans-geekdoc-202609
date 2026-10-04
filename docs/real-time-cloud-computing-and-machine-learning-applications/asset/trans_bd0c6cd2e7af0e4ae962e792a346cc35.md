

# 108. T. P. Fowdur, L. Babaroom, M. N-D-Ibn Nazir Rosun 和 M. Indoondon

![](img/2b52fde0e707e8c2f05a10309c3f8982_119_0.png)

图 2.108. 为 Cloud Foundry 搜索 Eclipse 工具。

(iv) 接受许可协议条款，并点击图 2.109 中新窗口中的“Finish（完成）”按钮。随后下载插件并将其添加到 Eclipse。

![](img/2b52fde0e707e8c2f05a10309c3f8982_119_1.png)

图 2.109. 接受插件的许可协议。

## 云计算基础

2. 安装带有必要插件的 IDE 后，启动 IDE 并按图 2.110 所示创建一个新的动态 Web 项目（Dynamic Web Project）。

![](img/2b52fde0e707e8c2f05a10309c3f8982_120_0.png)

图 2.110. 创建项目名为 CalculateArea 并将运行时（Runtime）设置为 IBM Bluemix

2. 如图 2.111 所示，输入项目名为 CalculateArea 并将运行时设置为 IBM Bluemix Runtime。

![](img/2b52fde0e707e8c2f05a10309c3f8982_120_1.png)

图 2.111. 选择项目运行时（Project Runtime）。

3. 在项目资源管理器（Project Explorer）中，右键点击 CalculateArea 项目，并按图 2.112 所示创建一个新的 Servlet。

# 110. T. Powdler, L. Babooram, M. N-D-Ibn Nazir Rosun 和 M. Indoondon

![](img/2b52fde0e707e8c2f05a10309c3f8982_121_0.png)

图 2.112. 为 CalculateArea 项目创建一个新的 servlet。

- 4. 如图 2.113 所示并按如下设置包名和类名。

![](img/2b52fde0e707e8c2f05a10309c3f8982_121_1.png)

图 2.113. 设置包名和类名。

- 5. 如图 2.114 所示编辑 URL 映射（URL mappings），使映射从 /CalculateAreaServlet 变为 /，，然后点击 Finish（完成）。

## 云计算基础

![](img/2b52fde0e707e8c2f05a10309c3f8982_122_0.png)

图 2.114. 显示 CalculateArea 项目的 URL 映射。

图 2.115 显示了编辑器中自动生成的 CalculateAreaServlet java 类代码。观察发现，它包含了构造函数 `CalculateAreaServlet()`、`doGet()` 和 `doPost()` 方法，以及第 13 行的一处标记，用于指示之前输入的该 servlet 的 URL 映射。这意味着 URL 映射也可以更改。如果服务器配置为在 localhost 上运行，则可以通过 URL：http://localhost:8080/CalculateArea/ 访问，其中 `/` 之前的部分表示项目链接。由于 servlet 将在 IBM 云平台上运行，因此它将具有 URL：项目中的单例 servlet，在 `/` 之后没有添加其他标识符。或者，如果有两个 servlet，可以有两个链接来识别这些 servlet，例如：https://calcularea.eu-gb.myblueix.net/s1 和 https://calcularea.eu-gb.myblueix.net/s2。这些映射将在图 2.115 的每个 Servlet 的第 13 行处制 mapping 处完成，或者在图 2.114 中创建每个 servlet 时完成。`doGet()` 和 `doPost()` 方法的作用总结如下：

- `doGet()`：参数可以从明文 URL 中获取，它们通过特定的符号（通常是查询字符串，即 URL 中问号 `?` 之后）附加到 URL 后。随后它们会随服务器自身的头部信息一起发送。大多数 Web 服务器仅支持附加到头部的有限信息，此头部的大小不应超过 1024 字节。
- `doPost()`：参数单独发送。沿 `doPost()` 请求发送的参数数量是无限制的，相比之下 `doGet()` 方法有 1024 字节的限制。

# 112. T. P. Fowdur, L. Babooram, M. U-D-Ibn Nazir Rosun 和 M. Indoondonun

```
package calculateArea;

import java.io.IOException;

/**
 * Servlet implementation class CalculateAreaServlet
 */
@WebServlet("/calculateArea")
// URL mapping
public class CalculateAreaServlet extends HttpServlet {
    private static final long serialVersion = 1L;

    /**
     * @see HttpServlet()
     */
    public CalculateAreaServlet() {
        super();
        // 1000 Auto-generated constructor stub
    }

    /**
     * @see doGet(HttpServletRequest request, HttpServletResponse response)
     */
    protected void doGet(HttpServletRequest request, HttpServletResponse response) {
        // 1000 Auto-generated method stub
        response.getWriter().append("Served at:").append(request.getContextPath());
    }

    /**
     * @see doPost(HttpServletRequest request, HttpServletResponse response)
     */
    protected void doPost(HttpServletRequest request, HttpServletResponse response) {
        // 1000 Auto-generated method
        doGet(request, response);
    }
}
```

图 2.115. CalculateArea 的代码。- 6. 修改上述代码以接受来自 URL 的两个参数 length 和 width，并返回计算出的面积。2. CalculateArea 的 doGet 方法。

```java
protected void doGet(HttpServletRequest request, HttpServletResponse response) {
    // 声明变量
    int length;
    int width;

    /* 检查请求中的 "length" 参数是否为空 */
    if(request.getParameter("length")!=null){
        /* 从请求中提取 length 和 width 并将其转换为整数 */
        length=Integer.parseInt(request.getParameter("length"));
        width=Integer.parseInt(request.getParameter("width"));
    } else {
        /* 如果 length 为空，将两者都设为 1 */
        length = 1;
        width = 1;
    }

    /* 计算面积并返回 */
    int area = length*width;

    response.getWriter().println("area is:" + area);
}
```

7. 在项目中的右键点击 servlet 并按图 2.116 所示点击 Run。

![](img/2b52fde0e707e8c2f05a10309c3f8982_124.png)

图 2.116. CalculateArea。

# 114. T. P. Fowdur, L. Babooram, M. N-D-Ibn Nazir Rosun 和 M. Indoondon

8. 选择 IBM Bluix Server，按图 2.117 所示输入账户凭据。

![](img/2b52fde0e707e8c2f05a10309c3f8982_125_0.png)

图 2.117. 选择部署 CalculateArea 的 Server。

![](img/2b52fde0e707e8c2f05a10309c3f8982_125_1.png)

图 2.118. 验证 IBM Bluix。

## 云计算基础

9. 对于图 2.119 所示的后续屏幕，只需 Next（下一步）。

![](img/2b52fde0e707e8c2f05a10309c3f8982_126_0.png)

图 2.119. 选择默认空间。

10. 保留应用程序默认名称，将内存限制设置为256，并在图 2.120 中点击 Finish（完成）。IBM 云上的免费账户需要 256 MB 的内存限制。

![](img/2b52fde0e707e8c2f05a10309c3f8982_126_1.png)

图 2.120. 为 CalculateArea Servlet 设置内存限制。

11. 部署过程将在 Eclipse IDE 的控制台上启动，如图 2.121 所示。

# 116. T. P. Fowdur, L. Babooram, M. N-D-Ibn Nazir Rosun 和 M. Indoondon

![](img/2b52fde0e707e8c2f05a10309c3f8982_127_0.png)

图 2.121. 控制台上的 CalculateArea 部署。

- 12. 部署完成后，应用程序将在 Eclipse IDE 中的 URL http://calculatearea.eu-gb.mybleix.net/ 。由于此 URL 没有查询字符串，length 和 width 参数将为空，因此 servlet 将返回面积为 1。

![](img/2b52fde0e707e8c2f05a10309c3f8982_127_1.png)

图 2.122. 在 Eclipse IDE 中部署的 CalculateArea Servlet。

