
是时候找出要执行的命令了，确保将 WFSOpen 调用与 WFSExecute 调用相关联，以区分所请求的操作。一旦识别出 WFSExecute 调用，您需要关注第二个参数，它是一个表示要执行的操作的数字。再次，以 Ripper 为例。在以下代码清单中，被压入的第二个参数是数字 302（参见行 .text:004090B8），但这个数字的用途是什么？

```
.text:004090B8 push 302
.text:004090BD push eax
.text:004090BE mov word ptr [ebp-28h], 2020h
.text:004090C4 mov byte ptr [ebp-26h], 20h
.text:004090C8 mov [ebp-25h], ecx
.text:004090CB mov [ebp-1Bh], ecx
.text:004090CE mov [ebp-1Fh], edi
.text:004090D1 call ds:WFSExecute
```

为了知道答案，您需要准备好 XFS SDK 的头文件（参见图 20-11）。

![](img/5f597c6a70133069118d9e804ace3775_575_0.png)

图 20-11 OpenXFS 头文件

每个头文件代表一种外设，并位于以下范围内：

- 100 - XFSPTR 银行打印机定义
- 200 - XFSIDC 识别卡单元定义
- 300 - XFSCDM 现金分配器定义
- 400 - XFSPIN 个人身份识别号码键盘定义
- 800 - XFSSIU 传感器和指示器单元定义
- 900 - XFSVDM 供应商相关模式定义

由于问题中的数字是 302，让我们来看看 SDK 中的 XFSCDM 文件定义。我们关注“CDM 执行命令”部分，因为调用了 WFSExecute（“CMD 信息命令”部分是在调用 WFSGetInfo 时使用）。计算目标数字的公式如下：
(CMD_SERVICE_OFFSET = WFS_SERVICE_CLASS_CDM(3) * 100) + 2 = 302
我们能够识别出问题中的 302 命令，即 WFS_CMD_CDM_DISPENSE，它指的是分配现金。

```
#define             WFS_SERVICE_CLASS_CDM                         (3) ⑤
#define             WFS_SERVICE_CLASS_VERSION_CDM                 0x0003
#define             WFS_SERVICE_CLASS_NAME_CDM                    "CDM"

#define             CDM_SERVICE_OFFSET                            (WFS_SERVICE_CLASS_CDM * 100) ⑤
```

# /* CDM 信息命令 */

```
#define             WFS_INF_CDM_STATUS                            (CDM_SERVICE_OFFSET + 1)
#define             WFS_INF_CDM_CAPABILITIES                      (CDM_SERVICE_OFFSET + 2)
#define             WFS_INF_CDM_CASH_UNIT_INFO                    (CDM_SERVICE_OFFSET + 3)
#define             WFS_INF_CDM_TELLER_INFO                       (CDM_SERVICE_OFFSET + 4)
#define             WFS_INF_CDM_CURRENCY_EXP                      (CDM_SERVICE_OFFSET + 6)
#define             WFS_INF_CDM_MIX_TYPES                         (CDM_SERVICE_OFFSET + 7)
#define             WFS_INF_CDM_MIX_TABLE                         (CDM_SERVICE_OFFSET + 8)
#define             WFS_INF_CDM_PRESENT_STATUS                    (CDM_SERVICE_OFFSET + 9)
```

# /* CDM 执行命令 */

```
#define             WFS_CMD_CDM_DENOMINATE                        (CDM_SERVICE_OFFSET + 1)
#define             WFS_CMD_CDM_DISPENSE                          (CDM_SERVICE_OFFSET + 2) ⑥

#define             WFS_CMD_CDM_PRESENT                           (CDM_SERVICE_OFFSET + 3)
#define             WFS_CMD_CDM_REJECT                            (CDM_SERVICE_OFFSET + 4)
#define             WFS_CMD_CDM_RETRACT                           (CDM_SERVICE_OFFSET + 5)
#define             WFS_CMD_CDM_OPEN_SHUTTER                      (CDM_SERVICE_OFFSET + 7)
#define             WFS_CMD_CDM_CLOSE_SHUTTER                     (CDM_SERVICE_OFFSET + 8)
#define             WFS_CMD_CDM_SET_TELLER_INFO                   (CDM_SERVICE_OFFSET + 9)
#define             WFS_CMD_CDM_SET_CASH_UNIT_INFO                (CDM_SERVICE_OFFSET + 10)
#define             WFS_CMD_CDM_START_EXCHANGE                    (CDM_SERVICE_OFFSET + 11)
#define             WFS_CMD_CDM_END_EXCHANGE                      (CDM_SERVICE_OFFSET + 12)
#define             WFS_CMD_CDM_OPEN_SAFE_DOOR                    (CDM_SERVICE_OFFSET + 13)
```

# /* CDM 消息 */

```
#define             WFS_SRVE_CDM_SAFEDOOROPEN                     (CDM_SERVICE_OFFSET + 1)
#define             WFS_SRVE_CDM_SAFEDOORCLOSED                   (CDM_SERVICE_OFFSET + 2)
#define             WFS_USRE_CDM_CASHUNITTHRESHOLD                (CDM_SERVICE_OFFSET + 3)
#define             WFS_SRVE_CDM_CASHUNITINFOCHANGED              (CDM_SERVICE_OFFSET + 4)
#define             WFS_SRVE_CDM_TELLERINFOCHANGED                (CDM_SERVICE_OFFSET + 5)
```

# /* WOSA/XPS CDM 错误 */

```
#define WFS_ERR_CDM_INVALIDCURRENCY                               ( - (CDM_SERVICE_OFFSET + 0) )
#define WFS_ERR_CDM_INVALIDTELLERID                               ( - (CDM_SERVICE_OFFSET + 1) )
#define WFS_ERR_CDM_CASHUNITERROR                                 ( - (CDM_SERVICE_OFFSET + 2) )
#define WFS_ERR_CDM_INVALIDDENOMINATION                           ( - (CDM_SERVICE_OFFSET + 3) )
#define WFS_ERR_CDM_INVALIDMIXNUMBER                              ( - (CDM_SERVICE_OFFSET + 4) )
#define WFS_ERR_CDM_NOCURRENCYMIX                                 ( - (CDM_SERVICE_OFFSET + 5) )
```

```
typedef struct _wfs_cdm_cashunit ⑦
{
USHORT   usNumber;
USHORT   usType;
LPSTR    lpszCashUnitName;
CHAR     cUnitID[5];
CHAR     cCurrencyID[3];
ULONG    ulValues;
ULONG    ulInitialCount;
ULONG    ulCount;
ULONG    ulRejectCount;
ULONG    ulMinimum;
ULONG    ulMaximum;
BOOL     bAppLock;
USHORT   usStatus;
USHORT   usNumPhysicalCUs;
LPWFSCDMPHCU  *lppPhysical;
} WFSCDMCASHUNIT, * LPWFSCDMCASHUNIT;
```

这些定义文件中还有更多有用的信息，可以帮助逆向工程师充分理解恶意软件逻辑，例如状态消息、错误消息，甚至结构定义 ⑦。

现在，您应该能够解剖从 Ripper 恶意软件中取出的下一个代码清单中执行的命令了：

```
.text:0040257B      push    ebx
.text:0040257C      push    ebx
.text:0040257D      push    201 ⑧
.text:00402582      push    eax
.text:00402583      mov     [ebp-4Ch], ebx
.text:00402586      call    ds:WFSGetInfo
```

我们可以看到，命令 201 ⑧ 属于 XFSIDC 定义文件（参见图 20-11），并且因为正在使用 WFSGetInfo 调用，这次我们关注“IDC 信息命令”部分。接下来，我们识别出正在调用 WFS_INF_IDC_STATUS ⑨ 命令，基本上是为了了解读卡器的状态！

```
#define  WFS_SERVICE_CLASS_IDC                         (2)
#define  WFS_SERVICE_CLASS_NAME_IDC                    "IDC"
#define  WFS_SERVICE_CLASS_VERSION_IDC                 0x0203

#define  IDC_SERVICE_OFFSET                            (WFS_SERVICE_CLASS_IDC * 100)

/* IDC Info Commands */
#define  WFS_INF_IDC_STATUS                            (IDC_SERVICE_OFFSET + 1)
#define  WFS_INF_IDC_CAPABILITIES                      (IDC_SERVICE_OFFSET + 2)
#define  WFS_INF_IDC_FORM_LIST                         (IDC_SERVICE_OFFSET + 3)
#define  WFS_INF_IDC_QUERY_FORM                        (IDC_SERVICE_OFFSET + 4)

/* IDC Execute Commands */
#define  WFS_CMD_IDC_READ_TRACK                        (IDC_SERVICE_OFFSET + 1)
#define  WFS_CMD_IDC_WRITE_TRACK                       (IDC_SERVICE_OFFSET + 2)
#define  WFS_CMD_IDC_EJECT_CARD                        (IDC_SERVICE_OFFSET + 3)
#define  WFS_CMD_IDC_RETAIN_CARD                       (IDC_SERVICE_OFFSET + 4)
```

对于专注于控制 XFS 中间件（Aglis、APTRA、Kalignite 等）的 Ploutus 等恶意软件，此方法不起作用。幸运的是，Ploutus 喜欢 .NET。因此，一旦恶意软件被去混淆，完整的源代码即可用于分析，无需逆向绝大多数组件（尽管某些组件是用 Delphi 实现的，需要进行逆向）。

## ATM 恶意软件对策

以下是处理 ATM 恶意软件时的最佳实践列表，这些实践绝对推荐，但不适用于所有攻击场景：

- 只有当防病毒软件或主机入侵防御系统（HIPS）“了解 ATM 环境”时才有用。例如，这些产品通常无法检测分配器中的恶意行为。
- 磁盘加密有助于防止通过从 ATM 断开存储设备来将恶意软件转移到柜员机的脱机攻击。
- 应用程序白名单有助于仅执行预期的进程。
- 渗透测试有助于在黑客之前主动识别问题。
- 应启用带密码保护的 BIOS。
- ATM 恶意软件培训有助于了解如何解剖和检测特定威胁。
- 应遵循“ATM 软件安全最佳实践指南”和“ATM 安全准则”。有关更多具体信息，请参阅“进一步阅读”部分。

## 摘要
