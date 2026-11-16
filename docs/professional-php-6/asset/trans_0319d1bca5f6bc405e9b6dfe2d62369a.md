

你现在可以看看如何使用 UML 开始构建这个解决方案。不过，在开始之前，有一点需要明确：本章演示了在设计应用程序时，随着你发现实现解决方案的新且更好的方法，你的思路可能会如何演变。因此，本章更应被视为示例应用程序的渐进式演进和开发，而非其代码的简单列举。像这样的具体示例可以帮助你更好地理解面向对象编程（OOP）的原理是如何工作的。

## 联系人管理器 UML 图

启动你选择的 UML 绘图应用程序，创建一个名为 ContactManager.[extension] 的新文件，其中 [extension] 是你应用程序的默认文件扩展名（例如，使用 Dia 创建的图表为 .dia，等等）。

首先，为你想要表示的不同类型的联系人信息创建类。对于这个示例应用程序，这些是地址、电子邮件地址和电话号码类——但你可以为所需的任何类型的联系人信息创建类。

## 表 3-1 联系人信息类

| 类 | 属性 |
| :--- | :--- |
| Address | street1<br>street2<br>city<br>state<br>zip（邮政编码）<br>type（家庭、工作，等等） |
| Email | email<br>type |
| PhoneNumber | number<br>extension<br>type |

这些类仅用于存储和显示数据，因此此时无需定义任何方法，类符号的第三部分为空。所有属性均为公共属性，因此都以加号作为前缀。图 3-1 展示了这些类当前的 UML 表示。

![](img/a1b732997d9cb194dceec0570dc79710_64_0.png)

图 3-1：基本联系人类型

接下来，你应该规划 Individual 和 Organization 类。一个个体拥有名、姓、雇主、职位、唯一标识符（数据库中的 id 字段）以及一个集合（电子邮件、地址和电话号码）。你还必须能够添加联系类型。图 3-2 展示了带有 Individual 类的 UML 图。

![](img/a1b732997d9cb194dceec0570dc79710_64_1.png)

图 3-2：Individual 类和联系类型

一个组织拥有名称、唯一标识符、联系类型的集合（与个体类似）、用于添加它们的方法以及员工集合。图 3-3 展示了带有 Organization 类的 UML 图。

![](img/a1b732997d9cb194dceec0570dc79710_65_0.png)

图 3-3：Individual 和 Organization 联系类型

该图显示 Individual 和 Organization 类共享许多相同的属性和方法。这通常表明，你可以通过使用继承来节省大量工作并提高应用程序的灵活性。你可以创建另一个类（本示例中的 Entity），在其中合并 Individual 和 Organization 类共有的功能，然后使它们共享相同的代码。在 UML 图中，你仅在实际实现属性和方法的类上标注它们。在这种情况下，你必须将 Individual 和 Organization 类的所有共同属性和方法移动到表示 Entity 类的符号中，如图 3-4 所示。仅当子类重写实现时，才将它们重复在子类中（子类从其父类继承成员）。

| Address |
|---------|
| +street1 |
| +street2 |
| +city |
| +state |
| +zip |
| +type |

| Email |
|-------|
| +email |
| +type |

| PhoneNumber |
|-------------|
| +number |
| +extension |
| +type |

| Entity |
|--------|
| +name |
| +id |
| +addresses: Address |
| +phoneNumbers: PhoneNumber |
| +emails: EmailAddress |
| +addEmail(objEmail:EmailAddress) |
| +addAddress(objAddress:Address) |
| +addPhone(objPhone:PhoneNumber) |

| Individual |
|------------|
| +firstname |
| +lastname |
| +name |
| +employer: Organization |
| +title |

| Organization |
|--------------|
| +employees: Individual |

**图 3-4：Entity 类，Individual 和 Organization 的通用超类**

在这种情况下，`Entity` 类的 `name` 属性在 `Individual` 类中被重写。当你检索 Individual 的 `name` 属性时，你将返回“lastname, firstname”。这样，你可以将 `Organization` 或 `Individual` 类交给一个函数，该函数只需打印一个名称，而无需使用单独的函数。

UML 还定义了用于指示关系的符号。在本示例中，你需要某种东西来显示 `Individual` 和 `Organization` 类继承自 `Entity` 类。如你所见，UML 规范将此关系称为 *泛化*，并使用从子类指向父类的开放箭头来指示它，如图 3-5 所示。

![](img/a1b732997d9cb194dceec0570dc79710_67_0.png)

图 3-5：泛化，由开放箭头指示

现在很明显，Individual 和 Organization 类继承自 Entity 类。使用连接器来指示继承，使你可以一眼看出图表中类之间的关系。

还需要展示另一种连接类型——Entity 类使用 Address、Email 和 PhoneNumber 类。UML 规范将此关系称为 composite，你通过在附加到类使用者一端的线上使用黑色菱形来指示它，如图 3-6 所示。被使用的类还具有一个称为多重性（即使用的数量）的属性。在本示例中，一个实体可能拥有零个、一个或多个任何联系类型，因此你在最靠近被使用项目的连接器线上写上 0..*，以指示一个类可能拥有 0 个或多个其所指向的类。

图 3-6 也展示了这种表示法。通过在图中揭示这种关系，你可以清楚地看到应用程序的哪些部分会受到另一部分更改的影响。在这里，对 Email、Address 或 PhoneNumber 类的更改将影响 Entity、Individual 和 Organization 类。

![](img/a1b732997d9cb194dceec0570dc79710_68_0.png)

图 3-6：Composite，通过在线段末端使用黑色菱形指示

一个 Entity 拥有一个 PhoneNumber、一个 Email 和一个 Address；在这三种情况下，它都可能拥有零个或多个该项目。因为 Individual 和 Organization 继承自 Entity，所以它们两者也都拥有零个或多个联系类型。

这就是目前为止所理解的应用程序基本结构。当然，你可以通过思考如何在现实中实际实现它来对其进行很多改进。关于这一点有几点重要事项需要注意。在下一节中，你将开发该应用程序。本章稍后将展示更多 UML，以便你清楚了解最终产品的样子。

回顾第 1 章中关于封装的讨论，将数据保护在私有成员变量中，并使用访问器方法来提供对这些属性的访问，这始终是个好主意。还要记住，使用 __get 和 __set 会使此过程更加容易。只需查看本章前面显示的类图，你就可以看到所有类都有相当简单的属性要求。因为你了解继承以及如何在 PHP 中利用它，所以你可以将功能从仅与 Entity 类绑定中解耦，并创建一个类，使你能够在其他类中重用其代码——实际上，为所有类共有的功能添加另一层抽象，以便更好地使用。这个父类将被称为 PropertyObject。

在现实世界中，出于良好实践的考虑，处理数据时你可能也希望添加一层抽象。为此，创建一个 DataManager 类可能是个好主意。还需要考虑的一点是，目前你没有统一的数据验证设施，因此需要一个可验证对象的接口。下面是接口的代码：

```
<?php
interface Validator {
    public function validate();
}
?>
```

