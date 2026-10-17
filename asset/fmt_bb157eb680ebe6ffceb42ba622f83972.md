
* Copyright (c) 1999-2001,2005-2012 Apple Inc. All Rights Reserved.

* @APPLE_LICENSE_HEADER_START@

* This file contains Original Code and/or Modifications of Original Code as defined in and that are subject to the Apple Public Source License Version 2.0 (the 'License'). You may not use this file except in compliance with the License. Please obtain a copy of the License at http://www.opensource.apple.com/apsl/ and read it before using this file.

* The Original Code and all software distributed under the License are distributed on an 'AS IS' basis, WITHOUT WARRANTY OF ANY KIND, EITHER EXPRESS OR IMPLIED, AND APPLE HEREBY DISCLAIMS ALL SUCH WARRANTIES, INCLUDING WITHOUT LIMITATION, ANY WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE, QUIET ENJOYMENT OR NON-INFRINGEMENT. Please see the License for the specific language governing rights and limitations under the License.

* @APPLE_LICENSE_HEADER_END@

```
int VerifyServerKeyExchange(ExchangeParams params,
                            uint8_t *expected_hash, size_t expected_hash_len) {
  int err;
  HashCtx ctx = 0;
  uint8_t *hash = 0;
  size_t hash_len;

  if ((err = ReadyHash(&ctx)) != 0)
    goto fail;

1 if ((err = SSLHashSHA1.update(ctx, params.clientRandom, PARAM_LEN)) != 0)
    goto fail;

2 if ((err = SSLHashSHA1.update(ctx, params.serverRandom, PARAM_LEN)) != 0)
    goto fail;

    goto fail;

3 if ((err = SSLHashSHA1.update(ctx, params.signedParams, PARAM_LEN)) != 0)
    goto fail;

  if ((err = SSLHashSHA1.final(ctx, &hash, &hash_len)) != 0)
    goto fail;

  if (hash_len != expected_hash_len) {
    err = -106;
    goto fail;
  }

4 if ((err = memcmp(hash, expected_hash, hash_len)) != 0) {
    err = -100;  // Error code for mismatch
  }

  SSLFreeBuffer(hash);

fail:
  if (ctx)
    SSLFreeBuffer(ctx);
  }

  return err;
}
```

`VerifyServerKeyExchange` 函数接受一个 `params` 参数（包含三个字段），计算其内容的消息摘要哈希值，并将结果与对数据进行身份验证的 `expected_hash` 值进行比较。返回值为零表示哈希值匹配，这是有效请求所必需的。非零返回值表示出现了问题：哈希值不匹配（`-100`）、哈希长度不匹配（`-106`），或哈希计算库因未指明的错误返回了某个非零错误码。安全性取决于此：对哈希值或数据的任何篡改都会导致哈希不匹配，从而发出异常信号。

### 正确代码逻辑

让我们先梳理正确版本的代码逻辑（即未引入重复 `goto` 语句之前）。在设置好 `HashCtx ctx` 上下文变量后，它依次对 `params` 的三个数据字段进行哈希计算（位置 1、2 和 3）。如果发生任何错误，它会跳转到 `fail` 标签，返回变量 `err` 中的错误码。否则，它继续执行，将哈希结果复制到缓冲区，并将其（位置 4）与预期哈希值进行比较。比较函数 `memcmp` 相等时返回 `0`；如果哈希不同，代码将错误码 `-100` 赋给 `err` 并继续向下执行以返回该结果。

### 功能测试

在考虑安全测试之前，让我们先为 `VerifyServerKeyExchange` 函数编写一个功能测试。功能测试检查代码是否按预期执行，此处的简单示例绝非详尽无遗。本示例使用 C 语言的 MinUnit 测试框架。你只需知道：`mu_assert(condition, message)` 会检查表达式 `condition` 是否为真；如果不为真，断言失败并打印所提供的 `message`：

```c
mu_assert(0 == VerifyServerKeyExchange(test0, expected_hash, SIG_LEN),
    "Expected correct hash check to succeed.");
```

此调用使用已知良好的参数调用该函数，因此我们期望返回值为 `0` 以通过测试。在函数内部，三个字段将被哈希（位置 1、2 和 3）。哈希值在位置 4 处比较相等。未展示的是三个数据字段的测试值（在名为 `test0` 的 `ExchangeParams` 结构体中）以及服务器会签名的预计算正确哈希值（`expected_hash`）。

### 带漏洞的功能测试

现在引入 GotoFail 漏洞（那行高亮代码），看看会产生什么影响。当我们用额外的 `goto` 重新运行功能测试时，测试仍然通过。代码在重复的 `goto` 之前运行正常，但随后跳过了第三个数据字段的哈希计算（位置 3）和哈希比较（位置 4）。函数将继续验证正确的输入，但现在也会验证一些本应拒绝的错误输入。然而，我们尚不知情。这正是安全测试如此重要——且如此容易被忽视——的原因。

更彻底的功能测试可能会包含额外的测试用例，例如检查验证失败（非零返回值）的情况。然而，功能测试往往止步于全面覆盖所有需要验证函数出于安全考虑而拒绝输入的情况。这就是安全测试发挥作用的地方，我们将在接下来看到。

## 安全测试用例

现在让我们编写一些安全测试用例。由于有三块数据需要哈希，这意味着要编写三个相应的测试；每个测试都会以某种方式改变数据值，导致哈希值与预期值不匹配。目标 `verify` 函数应该拒绝这些输入，因为被更改的值可能代表数据篡改，而哈希比较正是为了防止这种情况。实际的值（`test1`、`test2`、`test3`）是正确的 `test0` 的副本，只是在三个数据字段中的一个上有细微变化；这些值本身并不重要，因此未展示。以下是这三个测试用例：

```c
mu_assert(-100 == VerifyServerKeyExchange(test1, expected_hash, SIG_LEN),
    "Expected to fail hash check: wrong client random.");

mu_assert(-100 == VerifyServerKeyExchange(test2, expected_hash, SIG_LEN),
    "Expected to fail hash check: wrong server random.");

mu_assert(-100 == VerifyServerKeyExchange(test3, expected_hash, SIG_LEN),
    "Expected to fail hash check: wrong signed parameters.");
```

由于该漏洞，这三个测试都将失败。`verify` 函数在遇到麻烦的 `goto` 之前工作正常，但随后无条件跳转到标签 `fail`，导致其哈希工作未完成，且从未比较哈希值。因为我们编写这些测试时预期验证失败为正确行为，所以返回值 `0` 会导致测试失败。现在我们有了一个测试安全网，本可以在发布前捕获此漏洞，从而避免由此引发的惨剧。

为了追求完整性，还可以想到另一个安全测试用例。如果所有三个值都正确（如 `test0` 情况），但使用了不同的签名哈希（`wrong_hash`）会怎样？这是该测试用例：

```c
mu_assert(-100 == VerifyServerKeyExchange(test0, wrong_hash, SIG_LEN),
    "Expected check against the wrong hash value to fail.");
```

正如预期的那样，由于错误的 `goto`，此测试也会失败。虽然对于这个特定漏洞，只需其中一个测试就能捕获，但安全测试的目的是覆盖尽可能广泛的潜在漏洞范围。

### 安全测试的局限性

安全测试旨在检测代码中潜在的主要故障点，但永远无法覆盖代码出错的无数种方式。有可能引入我们刚编写的测试无法检测到的漏洞，但这种情况不太会无意中发生。除非测试覆盖率极其彻底，否则始终存在制造出能溜过测试的 Bug 的可能性；然而，主要威胁在于无意的 Bug，因此一组适度的安全测试用例可能非常有效。

确定安全测试用例需要多彻底需要判断力，但经验法则很明确：

*   对于对安全至关重要的代码，安全测试更为重要。
*   最重要的安全测试通常检查拒绝访问、拒绝输入或失败（而非成功）等行为。
*   安全测试用例应确保每个关键步骤（在我们的示例中，即三个哈希和哈希比较）都能正确工作。

在仔细研究了一个由简单（尽管意外）原因导致的真实安全漏洞，以及如何针对此类情况进行安全测试之后，让我们考虑一般情况，看看我们如何能预见此类问题并主动避免它。

## 编写安全测试用例

> 一个好的测试用例是指那些极有可能发现尚未被发现的错误的测试用例。
>
> —Glenford Myers

安全测试用例确认特定的安全故障不会发生。这些测试的动机源于四个问题中的第二个：什么可能出错？这与*渗透测试*不同，后者是诚实的人以合乎道德的方式猛烈敲打软件以发现漏洞，以便在坏人发现之前修复它们，因为安全测试并不试图探明所有可能的利用方式。安全测试还通过提供针对未来漏洞引入的保护，与渗透测试有所不同。

安全测试用例检查保护机制是否正常工作，这通常涉及拒绝或中和无效输入和不允许的操作。虽然没人能专门预见 GotoFail Bug，但很容易看出 `VerifyServerKeyExchange` 函数中的所有 `if` 语句都对安全至关重要。在一般情况下，此类代码要求对每个强制执行安全检查的条件进行测试覆盖。有了这种级别的测试，当多余的 `goto` 造成漏洞时，其中一个测试用例就会失败并引起你的注意。

你应该在编写其他单元测试时创建安全测试用例，而不是作为发现漏洞后的反应。安全系统通过阻止不当操作、拒绝恶意输入、拒绝访问等方式来保护宝贵资源。在这些安全机制存在的任何地方，都应创建安全测试用例，以确保未经授权的操作确实会失败。

常见的安全测试用例的通用示例包括：测试使用错误密码的登录尝试会失败、从用户空间未经授权访问内核资源的尝试会失败、以及以各种方式无效或格式错误的数字证书总是会被拒绝。阅读代码是获取优秀安全测试用例想法的好方法。

### 测试输入验证

让我们考虑输入验证的安全测试用例。作为一个简单的例子，我们将测试要求字符串长度至少 10 个字符、最多 20 个字符，且仅由字母数字 ASCII 字符组成的输入验证代码。

你可以创建辅助函数来执行这种标准化的输入验证，确保其统一且无故障地发生，然后将输入验证与匹配的测试用例结合起来，确认验证检查有效，且代码在允许的限制内正常运行，一直到极限值。事实上，由于 off-by-one 错误（边界错误）在编程中非常普遍，最好同时检查恰好在限制处和刚好超出限制处的情况。以下单元测试涵盖了此示例的输入验证测试用例：

*   检查长度为 10 的有效输入能通过，但长度为 9 或更短的输入会失败。
*   检查长度为 20 的有效输入能通过，但长度为 21 或更长的输入会失败。
*   检查包含一个或多个无效字符的输入总是会失败。

当然，功能测试应该已经检查过满足所有约束条件的示例输入能否正常工作。

再举一个类似的例子，假设被测代码将字节数组参数存储在长度为 *N* 字节的固定长度缓冲区中。安全测试用例应确保代码对大小不超过 *N* 的输入按预期工作，但大小为 *N*+1 的输入会被安全地拒绝。

### 测试 XSS 漏洞

现在让我们看一个更具挑战性的安全测试用例，以及一些可用的不同测试策略。回顾第 11 章的 XSS 漏洞，不可信的输入将自身注入到 Web 服务器生成的 HTML 中并突破到页面中，例如通过引入脚本来运行并发起攻击。该漏洞的根本原因是转义不当，因此我们的安全测试将集中于此。

假设被测代码是以下 Python 函数，它根据描述内容的字符串组合 HTML 片段：

#### 易受攻击的代码

```python
def html_tag(name, attrs):
    """Build and return an HTML fragment with attribute values.
    >>> html_tag('meta', {'name': 'test', 'content': 'example'})
    '<meta name="test" content="example">'
    """
    result = '<%s' % name
    for attr in attrs:
        result += ' %s="%s"' % (attr, html.escape(attrs[attr]))
    return result + ">"
```

注释（由 `"""` 分隔）中的 `doctest` 示例（以 `>>>` 前缀标记）演示了如何使用此函数为 `<meta>` 标签生成 HTML 文本。第一行构建结果文本字符串的第一部分：即打开每个 HTML 标签的尖括号（`<`），后跟标签名称。然后循环遍历属性（`attrs`），为每个属性追加一个空格及其声明（形式为 `X="Y"`）。

代码正确地将 `html.escape` 函数应用于每个属性字符串值，但我们仍应对其进行测试。（就我们的目的而言，我们假设属性值是唯一需要转义的潜在不受信输入来源。虽然在实践中这通常已足够，但任何情况皆有可能，因此某些应用中可能需要更多的转义或输入验证。）

让我们使用 Python 的 `unittest` 库编写测试用例：

```python
class ExampleTestCases(unittest.TestCase):
    def test_basic(self):
        self.assertEqual(html_tag('meta', {'name': 'test', 'content': '123'}),
                         '<meta name="test" content="123">')

    def test_special_char(self):
        self.assertEqual(html_tag('meta', {'name': 'test', 'content': 'x"'}),
                         '<meta name="test" content="x&quot;">')

if __name__ == '__main__':
    unittest.main()
```

第一个测试用例是一个基本的功能测试，展示了这些单元测试如何工作。当从命令行运行时，模块会调用最后一行中的单元测试框架 `main`。这会自动调用所有 `unittest.TestCase` 子类的各个方法，这些方法包含单元测试。`assertEqual` 方法比较其参数，二者应相等，否则测试失败。

现在让我们看看名为 `test_special_char` 的安全测试用例。既然我们知道 XSS 可以通过跳出不受信输入所在的双引号来利用代码，我们就用一个包含双引号的字符串来测试转义。正确的 HTML 转义应将其转换为 HTML 实体 `&quot;`，正如 `assertEqual` 语句中的预期字符串所示。如果我们在目标方法中移除 `html.escape` 函数，此测试确实会失败，这正是我们所期望的。

到目前为止一切顺利。但请注意，为了编写测试，我们必须预先知道哪些类型的输入可能有问题（双引号字符）。由于 HTML 规范相当复杂，我们如何知道不需要更多重要的测试用例？我们可以尝试许多其他特殊字符，`escape` 函数会将其中许多转换为各种 HTML 实体值（例如，将大于号转换为 `&gt;`）。然而，像这样调整测试用例以覆盖所有可能性将涉及大量工作。

既然我们在处理 HTML，我们可以使用详细了解规范的库来为我们分担繁重的工作。以下测试用例检查形成 HTML 标签的结果，正如我们之前对相同的两个测试值所做的那样：正常情况和包含双引号字符的字符串，依次赋值给变量 `content`：

```python
    def test_parsed_html(self):
```
