
-   [请特别注意带通配符匹配模式的扩展，如`file:///\*`, `http://\*/\*`, `\*://\*/\*`, 或`<all_urls>`。这些扩展可能会被用户访问的任何网站利用。]
-   ### 研究权限
    -   许多 Google Chrome 扩展程序请求并获得浏览器内的高权限。这使它们能够执行网站源不能做的操作。这种特权访问使它们对目标更有用，也使得被攻击的扩展对你更有价值。这一点尤其重要，因为扩展具备绕过 Same Origin Policy 限制的能力。
    -   鉴于运行此类特权代码的显著安全影响，开发者必须在安装时明确规定将使用 API 的部分。权限在 `manifest.json` 文件中声明。以下示例展示了一个典型的声明：
    ``` 
    "permissions": [ "http://*/*", "https://*/*", "tabs", "cookies" ], 
    ```
    -   安装扩展后，用户会看到一个确认对话框，列出扩展权限的可读描述。18 一旦用户点击“添加”，扩展即安装，拥有对话框中列出的全部权限，如图 7-11 所示。
    -   start figure
    -   [**Figure 7-11:**](#c07.html#figureanchor7-11) The Quick Note extension requesting permissions upon install
    -   ![c07f011.tif](image_fi/662090c07/c07f011.png)
    -   end figure
    -   许多在 Google Chrome Web Store 中的扩展请求访问所有网站的数据。同意安装此类扩展即意味着授予其读取用户访问的每一页的权限，包括使用 HTTPS URI 方案的站点。
    -   这些扩展可以读取密码、挂载键盘记录器等。有些甚至通过 HTTP 将数据发送给第三方。这些不安全的做法表明开发者未将安全放在首位，可能使这些扩展成为更具攻击性的目标。
-   ### 研究安全边界
    -   安全边界将内容脚本（及网页）与扩展的其余部分隔离。内容脚本在网页的 HTTP(S) 源上下文中运行，其他页面则在 `chrome-extension://` 源上运行。这两个源仅通过消息传递通信，默认情况下形成有效屏障，将不受信任的网页与高特权扩展后端隔开。
    -   Google 甚至提供了 19 个不安全编码实践的示例，帮助你理解和发现目标扩展中的安全漏洞。以下示例在扩展的后台页面运行并与内容脚本通信：
    ``` 
    chrome.tabs.sendMessage(tab.id, {greeting: "hello"}, function(response) {
      var resp = eval("(" + response.farewell + ")");
    });
    ```
    -   上述代码不安全地使用 `eval`，将内容脚本的消息作为参数的一部分。下一个示例利用 `innerHTML` 将不受信任的响应写入 DOM：
    ``` 
    chrome.tabs.sendMessage(tab.id, {greeting: "hello"}, function(response) {
      document.getElementById("resp").innerHTML = response.farewell;
    });
    ```
    -   查找 `eval` 和 `innerHTML` 的使用是进行代码审计的良好起点，尤其是在后台页面中。这些示例会导致跨内容脚本（Cross-content Scripting）漏洞，相关内容将在本章后部分详细说明。
    -   要利用这些漏洞，你需要先通过内容脚本 smuggle 攻击，从而间接获得消息传递 API 的访问权限。但还有一种场景：开发者可以在 `manifest.json` 中明确声明消息传递 API 可直接从网页访问：
    ``` 
    "externally_connectable": {
      "matches": ["http://browservictim.com/*"]
    }
    ```
    ``` 
    }
    ```
    -   在上述 JSON 代码中，你可以看到 `externally_connectable` 声明，指定哪些源可以直接访问消息传递 API。检查目标扩展的 `manifest.json` 是否存在此声明很有价值。
    -   由于 Google 未允许更宽泛的通配符（如 `*` 或 `*.com`）在 `externally_connectable` 的匹配模式中使用，攻击面因此受到限制。不过，如果 `http://browservictim.com` 存在 XSS 漏洞，仍可能成为攻击途径。
    -   Chrome 扩展仅允许预定义的消息传递方式，这大幅减少了攻击面。但仍可能存在足够的攻击空间，因此仍值得关注。
-   ### 研究内容安全策略（CSP）
    -   Google 将内容安全策略（CSP）纳入 Chrome 扩展的基础之中。20 如前所述，CSP 是对 web 资源施加的限制集合，可根据脚本的源决定是否允许或禁止执行脚本，从而有效降低开发者“自砍手”的风险。
    -   扩展使用的具体 CSP 限制在 `manifest.json` 中通过 `content_security_policy` 参数定义。若未明确声明，Chrome 会应用一套相对严格的默认限制。默认 CSP 指令示例如下：
    ```
    script-src 'self'; object-src 'self'
    ```
    -   该指令意味着对后端扩展组件的任何成功注入攻击的限制：
        -   不允许加载外部脚本，例如 `<script src=http://browserhacker.com>` 不会执行。
        -   不允许加载外部对象，如 Java、Flash 等。
        -   不允许内联脚本，如 `<script>code</script>`。
        -   不允许 `eval()` 及其衍生函数。
    -   这意味着攻击面被缩小。但问题是：有多少开发者会为了便利而放宽 CSP 指令？开发者（包括扩展开发者）常使用 JavaScript 模板引擎，而许多此类引擎依赖 `eval()` 函数。要使其正常工作，`manifest.json` 必须包含 `unsafe-eval` 指令。
    -   别小看安全，别认为它比那个炫酷的新 JavaScript 模板引擎更重要！如果你非常安静，几乎能听到项目经理的“风险接受”呼喊，以及那个弯腰的安全工程师低声咒骂。
    -   CSP 同时适用于扩展的 UI 页面和后台页面。仅限于安全边界内的扩展组件享受此保护，不适用于内容脚本。因此，当你在内容脚本中发现漏洞时，可以确信其可被利用。虽然运行在内容脚本中的代码权限受限，但影响仍然可观。本章后续将进一步介绍此类攻击。
    -   请务必检查目标扩展的 `manifest.json` 中的 `content_security_policy` 参数。安全可被锁定，但未必会被锁定。
-   ### 讨论 Internet Explorer 扩展
    -   Internet Explorer（IE）扩展的用户基数不如 Firefox 或 Chrome 普及。无论原因何在，这导致 IE 扩展的攻击范围相对较小。
    -   Microsoft 将 Internet Explorer 扩展归类为 Browser Helper Objects（BHOs）、工具栏和 ActiveX 控件。22 这些技术主要编译为 native code，因此可能易受传统缓冲区溢出、格式字符串漏洞和整数错误的影响。
