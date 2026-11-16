

| Method | Role |
| :--- | :--- |
| IsRedirectFollowingConstraintFailure | 如果当前显示的页面是因约束测试失败而发出的 302 重定向自动加载的，则此方法返回 true。 |
| GetOriginalRequestObjectFollowingConstraintFailure | 如果当前显示的页面是因约束测试失败而发出的 302 重定向自动加载的，则此方法返回调用该页面时存在的请求对象，即在约束测试失败之前的请求对象。 |
| SetRedirectOnConstraintFailure | 接受 `true` 或 `false` 作为参数，此方法使您能够告知 `request` 对象在任何约束测试失败时是否应执行 302 重定向。该重定向的目标通过 `SetConstraintFailureRedirectTargetURL` 和 `SetConstraintFailureDefaultRedirectTargetURL` 方法设置。 |
| SetConstraintFailureRedirectTargetURL | 设置约束失败后 302 重定向的目标。如果未设置，则使用引用页面（通常是所需目标），如果不可用，则使用默认 URL（通过 `SetConstraintFailureDefaultRedirectTargetURL` 方法设置）。 |
| SetConstraintFailureDefaultRedirectTargetURL | 如果未使用前述访问器方法设置目标 URL，则在因约束测试失败而需要引用时，使用引用页面。如果没有可用的引用页面（例如，用户通过书签访问），则改用此方法指定的默认 URL。 |
| GetParameterValue | 返回指定参数的值。该值直接从 `$_REQUEST` 获取，因此 GET 变量、POST 变量和 COOKIE 变量的搜索优先级取决于 PHP 的整体配置。 |
| GetParameters | 返回参数哈希——本质上是 `$_REQUEST` 的直接副本 |
| GetCookies | 返回 Cookie 哈希——本质上是 `$_COOKIE` 的直接副本 |
| GetPostVariables | 返回 `POST` 变量哈希——本质上是 `$_POST` 的直接副本 |
| GetGetVariables | 返回 `GET` 变量哈希——本质上是 `$_GET` 的直接副本 |
| `AddConstraint` | 向此请求添加一个约束。约束应用于单个参数，并指定必须满足的条件，才能视为该约束已满足。<br>此方法将参数名、传递方法（作为常量 `VERB_METHOD_GET`、`VERB_METHOD_POST` 或 `VERB_METHOD_COOKIE`）和约束对象（稍后讨论）作为其参数。添加约束后，无法移除。多个约束可应用于单个参数。 |
| `TestConstraints` | 依次测试每个约束，并通过填充成员变量 `$_arObjConstraintFailure` 记录任何失败的约束，可使用 `GetConstraintFailure` 访问。如果 `$_blRedirectOnConstraintFailure` 设置为 `true`，它会首先发出一个作为当前 `request` 对象序列化表示的临时 Cookie，然后自动重定向到相应的 URL。 |
| `GetConstraintFailures` | 当对 `TestConstraints()` 的调用指示一个或多个约束失败时，此方法将返回一个 `ConstraintFailure` 对象数组，表示所有此类失败。此方法需要从原始 `request` 对象访问，该对象可使用 `GetOriginalRequestObject() FollowingConstraintFailure` 访问（如前所述，在本表中）。 |

不用担心如果表 13-3 中的理论不太清楚。本章稍后，您将找到一个实际示例，展示如何在现实世界中使用此类及其余工具包。到那时一切都会变得清晰。

现在让我们来看看 `Constraint` 类及其近亲 `ConstraintFailure` 类。

## Constraint 类

`Constraint` 类仅作为面向对象的封装器存在。它不关心测试约束是否通过所需的代码。正如您刚才所见，这是由 `request` 对象处理的。

在名为 `constraint.php` 的文件中输入以下代码：

```php
<?php
require_once("constants.php");
class constraint {
   private $_intConstraintType;
   private $_strConstraintOperand;

   function __construct($intConstraintType, $strConstraintOperand) {
       $this->_intConstraintType = $intConstraintType;
       $this->_strConstraintOperand = $strConstraintOperand;
   }

   function GetConstraintType() {
       return($this->_intConstraintType);
   }

   function GetConstraintOperand() {
       return($this->_strConstraintOperand);
   }
}
?>
```

请注意，构造函数将约束类型（从枚举为常量的约束类型中选择一个）作为其第一个参数，将操作数作为其第二个参数。操作数的含义取决于约束类型。其解释由 `request` 对象在其实现每种约束类型时决定。例如，对于 CT_MAXLENGTH 约束，操作数应包含参数的最大长度。对于 CT_PERMITTEDCHARS 约束，操作数应包含一个字符串，其中包含参数中可能存在的所有允许字符。

为适应这种灵活性，操作数是一个字符串。但是，在进行测试时，它将被转换回其最合适的本地形式。

请注意，您不会在约束对象中存储正在测试的参数名。约束只是一个条件，可以使用 `request` 对象中的方法将其应用于任何（甚至多个）参数。出于此原因，为了整齐地封装任何给定的约束失败，还必须存储引发失败的参数和传递方法。这是通过 `ConstraintFailure` 类的实例完成的。

## ConstraintFailure 类

每当特定约束失败时，都会实例化一个 `ConstraintFailure` 对象。其构造函数期望参数名、传递方法（`VERB_METHOD_GET`、`VERB_METHOD_POST` 或 `VERB_METHOD_COOKIE`）以及导致失败的原始约束对象。

在正常使用中，将使用 `GetFailedConstraintObject` 方法通过先前描述的原生 `Constraint` 类方法来确定失败的约束的性质。

查看名为 `constraintfailure.php` 的文件中的以下代码：

```php
<?php
require_once("constants.php");
require_once("constraint.php");
class constraintfailure {
    private $_strParameterName;
    private $_intVerbMethod;
    private $_objFailedConstraintObject;

    function __construct($strParameterName, $intVerbMethod,
                $objFailedConstraintObject) {
        $this->__strParameterName = $strParameterName;
        $this->__intVerbMethod = $intVerbMethod;
        $this->__objFailedConstraintObject = $objFailedConstraintObject;
    }

    function GetParameterName() {
        return($this->__strParameterName);
    }

    function GetVerbMethod() {
        return($this->__intVerbMethod);
    }

    function GetFailedConstraintObject() {
        return($this->__objFailedConstraintObject);
    }
};
?>
```

此类整齐地封装了由于用户对页面的输入未满足您的验收标准而发生的失败。

如前面的代码所示，它包含失败的参数名、传递参数的方法（GET、POST 或 Cookie）以及失败的约束（表示为约束对象）测试。

此对象的实例可以通过 `GetConstraintFailures` 方法从 `Request` 类中检索，前提是 `Request` 类已在由约束失败引起的重定向后的 302 重定向上下文中实例化。

## 使用工具包

既然您已经了解了构成工具包的基本类，那么值得看看如何在现实世界应用程序中实现它。

在本示例中，您还将看到本章前面定义的 MVC 方法的一个实际案例——即使用原生 PHP 模板。（本章稍后的“真正的模板”部分将详细介绍其工作原理。）

假设您有一个由两个页面组成的搜索引擎：用于输入搜索词的搜索页面和用于显示结果的搜索词页面。

### search.php

初始搜索控制器有以下任务：

- 加载所有必要的组件。
- 定义模板文件 (search.phtml)。

