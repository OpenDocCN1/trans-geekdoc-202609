

- 定义一个关联数组（`$displayHash`），用于存储由模板文件（视图）渲染的内容。
- 检查该页面是否是在约束检查失败导致的转介后到达的（而不仅仅是用户第一次请求）：
  - 如果是，设置 `$displayHash` 的一部分以指示此情况，并从当前的 `request` 对象（该对象已通过临时 cookie 提供）中检索原始失败的请求对象。
  - 从检索到的 `request` 对象中获取一个 `constraintfailure` 对象数组。
  - 遍历这些 `constraintfailure` 对象，在 `$displayHash` 中填充一个新组建的数组，其中包含每个失败的类型。
- 立即渲染模板文件（require 模板文件）。

search.php 的代码（不是 search.phtml —— 后面会讲到）如下所示：

```
<?php
require_once("constants.php");
require_once("request.php");
require_once("constraint.php");
require_once("constraintfailure.php");

$strTemplateFile = "search.phtml";

$displayHash = Array();

$objRequest = new request();
$blHadProblems = ($objRequest->IsRedirectFollowingConstraintFailure());

$displayHash["HADPROBLEMS"] = $blHadProblems;

if ($blHadProblems) {
$objFailingRequest =
$objRequest->GetOriginalRequestObjectFollowingConstraintFailure();
$arConstraintFailures = $objRequest->GetConstraintFailures();
$displayHash["PROBLEMS"] = Array();
for ($i=0; $i<sizeof($arConstraintFailures)-1; $i++) {
$objThisConstraintFailure = &$arConstraintFailures[$i];
$objThisFailingConstraintObject =
$objThisConstraintFailure->GetFailedConstraintObject();
$intTypeOfFailure = $objThisFailingConstraintObject->GetConstraintType();
switch ($intTypeOfFailure) {
case CT_MINLENGTH:
$displayHash["PROBLEMS"][] = "Your search term was too short.";
break;
case CT_MAXLENGTH:
$displayHash["PROBLEMS"][] = "Your search term was too long.";
break;
case CT_PERMITTEDCHARACTERS:
$displayHash["PROBLEMS"][] = "Your search term contained characters
I didn't understand.";
break;
};
};
};
require_once($strTemplateFile);
exit(0);
?>
```

请注意末尾的 exit 语句。虽然这并非绝对必要，但它可以防止你在模板获取控制权后意外编写代码。

现在让我们来看看模板本身。

## search.phtml

模板的唯一职责是智能地渲染 `$displayHash` 的内容，并添加合适的周围 HTML。请注意，你不需要将 `$displayHash` 声明为全局变量。require 模板的操作会将其粘附到原始脚本的末尾。PHP 解释器在执行时将其视为一个单一脚本。

在此特定模板中，除了渲染创建搜索表单所需的简单 HTML 外，你还必须渲染因刚刚发生的搜索失败而生成的任何错误消息。

值得注意的是，以下 HTML 非常非常简单——绝非使用了所有最新 CSS 的精美语义 XHTML。希望你已经意识到，这仅仅是为了示例的清晰度。在你自己的应用程序中，模板无疑会大得多且更加复杂。

将以下内容另存为 `search.phtml`（而不是已经创建的 `search.php`）：

```
<html>
<head>
<title>Ed's Search Page</title>
</head>
<body>
<H1>Ed's Search Page</H1>
<hr>
You can search for types of steak here.
<BR><BR>
<? if ($displayHash["HADPROBLEMS"]) { ?><BR>
<B>Sorry, there <?=(sizeof($displayHash["PROBLEMS"]) > 1) ? "were problems" : "was a problem"?> with your search!</B>
<? for ($i=0; $i<sizeof($displayHash["PROBLEMS"])-1; $i++) { ?>
<?=$displayHash["PROBLEMS"][$i]?>
<? } ?>
<? } ?>
<FORM METHOD="POST" ACTION="searchresults.php">
<TABLE BORDER="0">
</TR>
            <TD>Type of Steak</TD>
            <TD><INPUT TYPE="TEXT" NAME="typeOfSteak"></TD>
        </TR>
        </TABLE><BR>
        <INPUT TYPE="SUBMIT">
        </FORM>

        </body>
        </html>
```

请注意 PHP 有多简单，其中包含非常基本的语句，例如 `if` 和 `for`。原则上，如果你在模板文件中编写的代码复杂度更高，那么它很可能位置不对，应该放在控制器页面（`.php`）或某个类（`.php`）中。

本章后面你将了解在模板中使用这些简单语句的一种替代方法，一种根本不使用 PHP 的方法：`true templating`。

如果在浏览器中运行 `search.php`，你应该会看到它成功渲染了标准搜索表单，如图 13-2 所示。

![](img/a1b732997d9cb194dceec0570dc79710_335_0.png)

图 13-2 search.php 的标准搜索表单

显然，搜索页面需要一个目标。这是通过两个不同的文件提供的：控制器和模板。

## searchresults.php

搜索结果页面将是搜索页面的直接目标，其任务是判断其输入是否可接受。

它的任务*不是*告知用户输入不可接受。相反，用户将通过 302 HTTP 重定向被*返回*到原始搜索页面，然后由该页面说明不足之处。

> 请勿直接在 Web 浏览器中运行此代码。它期望从搜索页面调用。

以下示例中适用的条件与传递给脚本的唯一搜索参数有关——即用户提供的搜索字符串。它必须包含 4 到 11 个字符，且必须是字母，而不是数字：

```
<?
require_once("constants.php");
require_once("request.php");
require_once("constraint.php");
require_once("constraintfailure.php");

$strTemplateFile = "searchresults.phtml";

$displayHash = Array();
session_start();

if ($_POST) {
    $objRequest = new request();
    $objRequest->SetRedirectOnConstraintFailure(true);

    $objConstraint = new constraint(CT_MINLENGTH, "3");
    $objRequest->AddConstraint("typeofSteak", VERB_METHOD_POST, $objConstraint);
    $objConstraint = new constraint(CT_MAXLENGTH, "12");
    $objRequest->AddConstraint("typeofSteak", VERB_METHOD_POST, $objConstraint);
    $objConstraint = new constraint(CT_PERMITTEDCHARACTERS,
    "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz");
    $objRequest->AddConstraint("typeofSteak", VERB_METHOD_POST, $objConstraint);

    $objRequest->SetConstraintFailureDefaultRedirectURL("/search.php");
    $objRequest->TestConstraints();

    # If we've got this far, tests have been passed - perform the search.
    $displayHash["RESULTS"] = Array();
    $arSteaks = array("fillet", "rump", "sirloin", "burnt");

    for ($i=0; $i<sizeof($arSteaks)-1; $i++) {
        if (! (strpos (trim(strtolower ($arSteaks[$i])),
        strtolower (trim($objRequest->GetParameterValue("typeofSteak")))))
        == false) {
            array_push($displayHash["RESULTS"], $arSteaks[$i]);
        }
    };

    $_SESSION['dh'] = $displayHash;
    header("Location: searchresults.php");
    exit(0);
}
} else {
    $displayHash = $_SESSION['dh'];
    require_once($strTemplateFile);
    exit(0);
};
?>
```

请注意，$displayHash 模板内容变量在 request 对象重新实例化时再次被定义。

首先，控制器测试它是否是因 HTTP POST 调用的。如果是，则对输入的每个约束都定义为 constraint 对象的一个新实例。然后使用 AddConstraint 添加它，指定传递方法（在此示例中为 POST）和参数名作为额外操作数。

为了消除引荐页面必须可用的需求，你需要指定一个默认 URL（即原始搜索页面）。如果你正在尝试此示例，则需要相应调整本章脚本的路径。

随后调用一个方法：TestConstraints()。这将执行验证你所表达的所有约束是否已满足所需的测试。如果有任一约束未满足，则它会被添加到该 request 对象中包含的约束失败数组中。

在这些测试结束时，如果任何测试导致失败，则该 request 对象获授权强制用户返回搜索页面，这是由使用 SetRedirectOnConstraintFailure() 导致的。首先，它将此页面上 request 对象的当前状态序列化为一个快照，然后将其作为 cookie 推送到浏览器。当用户返回搜索页面时，该 cookie 将由 request 对象解析以确定出了什么问题。

如果发生重定向，则根本不会显示模板。结果，用户根本不会意识到他们已经访问了第二个页面。这改善了用户体验。用户不会感觉自己已经“离开”了原始搜索页面。因此，他们会立即意识到有什么不对劲。

假设测试通过，搜索可以继续。在示例中，请注意搜索机制非常简单。在现实场景中，无疑会使用外部类来执行搜索。

在搜索结果变量填充后，它会暂时存储在会话中。然后发出重定向以使用 HTTP GET 重新加载页面。重新加载时，可以通过从会话中恢复 display hash 的值来显示模板。请注意，重新加载时不会执行验证和搜索，因为 `if ($_POST)` 条件求值为 false。

