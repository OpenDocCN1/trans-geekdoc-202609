
“We need in the `User` class to add `alerts` property.”

“We need in the `User` class to add `jobs` property.”

“We need in the `User` class to add `queues` property.”

“We need in the `User` class to add `caches` property.”

“We need in the `User` class to add `databases` property.”

“We need in the `User` class to add `servers` property.”

“We need in the `User` class to add `containers` property.”

“We need in the `User` class to add `clusters` property.”

“We need in the `User` class to add `networks` property.”

“We need in the `User` class to add `security` property.”

“We need in the `User` class to add `identity` property.”

“We need in the `User` class to add `auth` property.”

“We need in the `User` class to add `storage` property.”

“We need in the `User` class to add `compute` property.”

“We need in the `User` class to add `search` property.”

“We need in the `User` class to add `analytics` property.”

“We need in the `User` class to add `ai` property.”

“We need in the `User` class to add `ml` property.”

“We need in the `User` class to add `data` property.”

“We need in the `User` class to add `blockchain` property.”

“We need in the `User` class to add `iot` property.”

“We need in the `User` class to add `edge` property.”

“We need in the `User` class to add `mobile` property.”

“We need in the `User` class to add `web` property.”

“We need in the `User` class to add `cloud` property.”

“We need in the `User` class to add `enterprise` property.”

“We need in the `User` class to add `consumer` property.”

“We need in the `User` class to add `finance` property.”

“We need in the `User` class to add `health` property.”

“We need in the `User` class to add `education` property.”

“We need in the `User` class to add `social` property.”

“We need in the `User` class to add `entertainment` property.”

“We need in the `User` class to add `gaming` property.”

“We need in the `User` class to add `ecommerce` property.”

“We need in the `User` class to add `marketing` property.”

“We need in the `User` class to add `sales` property.”

“We need in the `User` class to add `support` property.”

“We need in the `User` class to add `operations` property.”

“We need in the `User` class to add `hr` property.”

“We need in the `User` class to add `legal` property.”

“We need in the `User` class to add `finance` property.”

“We need in the `User` class to add `strategy` property.”

“We need in the `User` class to add `innovation` property.”

“We need in the `User` class to add `product` property.”

“We need in the `User` class to add `service` property.”

“We need in the `User` class to add `design` property.”

“We need in the `User` class to add `engineering` property.”

“We need in the `User` class to add `technology` property.”

“We need in the `User` class to add `data` property.”

“We need in the `User` class to add `science` property.”

“We need in the `User` class to add `ai` property.”

“We need in the `User` class to add `ml` property.”

“We need in the `User` class to add `security` property.”

“We need in the `User` class to add `privacy` property.”

“We need in the `User` class to add `ethics` property.”

“We need in the `User` class to add `sustainability` property.”

## 封装我们的思想

这当然没问题。至少在我们达到那种同事开始从变量中持有的类名来实例化对象的程度之前。你知道我指的是什么：动态类解析。

```
// 危险的代码
$className = $propertyName . 'Validator';
$validator = new $className($propertyValue);
return $validator;
```

这类操作只应该发生在工厂（无论是抽象工厂还是其他的）中，并且返回的对象必须符合一个清晰且易于理解的接口。如果它发生在“荒野”——即构成应用程序正常业务流程的代码中，那么坦率地说，你的代码已经出大问题了。游戏结束了，是时候开始着手重写了。

与其试图逃避它，不如说，我们不打算这样做。松解耦合和依赖注入的概念将在本书的后部分详细讨论。对使用 `new` 关键字产生过敏的想法也将在此讨论。不过，目前，我只想让你们默认这样一点：在我们的 `User` 类内部实例化验证器实例是一个严格禁止的场景。我让你们默认，是因为如果你已经是在读这本书的第二遍或更多遍，你已经知道为什么应该这样了。

看到了吧？我告诉过你的。北极熊！

那么，我们如何将验证器引入 `User` 类呢？有一种答案，当然是通过构造函数将其传递进来。我们的下一次重构正是如此做的。

```php
public function __construct(
    array $userData,
    UserDataValidator $udv
) {
    if (!$this->isValid($userData)) {
        throw new Exception(
            $udv->getErrorMessage(),
            $udv->getErrorCode()
        );
    }
    $this->userData = $userData;
}
```

## 封装我们的思想

看看我们做了什么！这里的建议是，针对 `$UserData` 数组的所有验证逻辑都很好地被封装在了 `UserValidator` 对象中。只要我们对这个验证器及其操作充满信任，就能以非常简洁的方式使用经过验证的数据初始化我们的 `User` 对象。此外，$UserData$ 结构的未来任何更改（你知道的，业务团队想要记录“喜爱的颜色”，下周就会变成“鞋码”）都不会导致我们现有的 `User` 类发生任何变化，这只能是好事，对吧？

尽管如此，我们还可以更进一步。我们可以将 `$UserData` 数组和 `UserValidator` 合并为一个对象。我们管它称为 `UserDataTransport` 对象，并修改代码如下：

```php
class User
{
  /**
   * @var UserDataTransport
   */
  private $userData;

  public function __construct(UserDataTransport $udt)
  {
    $this->userData = $udt;
  }
}
```

最后，我们得到了一个非常短小优雅的 `User` 类，它正确地在私有属性中持有验证过的用户属性，但这种方式不会让验证程序弄乱 `User` 类本身，而这些程序我们可能在其他地方也会。从 `User` 类的角度来看，它现在被有效数据正确初始化，因为我们也信任 `$udt` 实例在被传递之前已经正确地完成了它的工作。

你们中你们可能在想，我们在这里成就的仅仅是把本应该在 `User` 类中的方法移动到了其他地方，然后在上面套上了一个名为 `User` 的相当没用的壳。如果这就是我们旅程的终点，那么就是完全正确的。

但并不是旅程的终点。虽然我们确实正在接近最后的直道，但我们已经到了应该停顿一下、泡杯好茶并思考一下的地步。

## 封装我们的思想

如果你观察我们在这里所做的，可以将 `$udt` 实例看作一个种子、一个内核、一个单元，它仅仅代表了我们想要持久化到应用程序中需要实现的任何存储系统中的数据。我们到达了一个非常有趣的点。我们的可持久化数据现在被**封装**在一个离散的单元中，该单元与我们的模型类分离并被其消费。

这是我们在构建大规模应用程序时想要实现的关键设计目标。我们希望我们的模型类专注于表现得它们应该具有的模型类的行为。通过向模型类注入诸如数据传输对象等的方法，我们能够将模型层与处理数据持久化的实现细节解耦。

如果你对市面上的一个或多个 PHP 框架稍微熟悉，你可能会意识到它们在实现模型层持久化时所采取的许多多样化方法。在某些情况下，你被要求扩展框架提供的基础模型来实现应用模型。在另一些情况下，你被要求混合你的模型类设计，以便向装饰器和适配器暴露它们管理的属性。无论哪种情况，你都被要求将你的模型设计适应到它们的持久化机制中，在此过程中，你被预期放弃至少一个或另一个健康的设计原则。在我看来，这不仅很糟糕，而且简直不可理喻。

通过向你的模型类注入必需的数据内核，你让自己从这种破坏原则的约束中解放出来。你的模型可以正确地封装它们本应承担的业务逻辑，而存储解决方案的反复变化会立即且正确地被归到模型层之外，并到它们真正所属的持久化层。

我们的 `User` 类还剩下什么？我们仍然处于需要提供访问数据手段这一点。我们的起点是提供 getter 和 setter，它们构成了实体。到目前为止，我们唯一的用例是将数据取出来，我将访问修饰符设置为私有。

## 封装我们的思想

```php
class User {
    /**
     * **var UserDataTransport
     */
    private $userData;

    public function __construct(UserDataTransport $udt) {
        $this->userData = $udt;
    }

    private function getDataTransport() {
        return $this->userData;
    }

    public function getUsername() {
        return $this->userData->getUsername();
    }

    public function getEmail() {
        return $this->userData->getEmail();
    }

    public function setEmail($email) {
        try {
            $this->userData->setEmail($email);
            return $this;
        } catch (DataTransportException $e) {
            $msg = $e->getMessage();
            $code = $e->getCode();
            throw new ModelException($msg, $code);
        }
    }
}
```

这里有几点需要注意。首先，由于我们目前没有获取数据的用例，我将 `getDataTransport()` 方法的访问修饰符设置为私有，以供构成公共接口的 getter 使用。此外，我们这里只有一个 setter 方法，即针对 email 属性的。除非你的应用程序支持用户更改用户名，否则用户名属性的 setter 可能是多余的。

## 封装我们的思想

现在，让我们把注意力转向执行者，即应用程序的处理器。我们已经讨论过如何通过实现一个 `PasswordManager` 类，将密码处理过程从我们的 `User` 类中分离出来。为了开启这一路线，让我们来看看这在代码中是如何实现的。

```php
class PasswordManager {
    const PASSWORD_MANAGER_COST = 10;

    public function getPasswordHash($rawPassword)
    {
        $options = array(
            'cost' => self::PASSWORD_MANAGER_COST
        );
        return password_hash($rawPassword, PASSWORD_BCRYPT, $options);
    }

    public function verifyPassword($rawPassword, $hashedPassword)
    {
        return password_verify($rawPassword, $hashedPassword);
    }
}
```

正如你所看到的，我们的 `PasswordManager` 类的意图表达非常明确。即使没有代码中本应包含的文档块（docblocks），你也能非常清晰地遵循它的执行路径。我们成功地将确保使用最佳密码处理方法的两个核心方法封装在一个目的单一的单元单元中。从这里开始，实现 PHP 提供的其他 `password_hash()` 相关函数以完成该类定义的实用性只需简单一步。

> 顺便提一下，如果你从这一章没有学到任何东西，把这个 `PasswordManager` 类复制并粘贴到你自己的应用程序中也比什么都好。如果你还没有使用语言提供的 `password_hash()` 函数，你应该开始使用。我稍后会解释原因，因为这个主题在书中“实践”部分会有专门的章节介绍。

封装我们的思想。

遵循同样的原则，我们没有理由不回到早早消除的 `$balance` 属性，并编写一个 `BalanceManager` 类，这个类封装了我们处理用户余额所需的所有知识。

为了指定多个账单地址和送货地址。这难道不是非常适合提供一个 `AddressManager` 类吗？

# 总结

我们走了一段长而曲折的道路才到达这里。在开始，我指出纯粹意义上的“封装”不等同于“信息隐藏”。然后我要求你将这两者视为同一种事物。我非常希望，你并不是把我当成某个疯子，而是能理解我的意图——每个完成这一章的人，无论其起始知识如何，在结束时都有共同的理解：当我们在日常工作中谈论封装时，我们实际上指的是这两个捆绑为一的概念。

共同的术语、共同的语言，是协作软件开发中的一个重要因素。我希望实现的只是这一理想中的一小部分。

在翻阅这些章节的过程中，我探索了一个相当典型（尽管极其瘦小）的模型类的演变，在此过程中，我似乎过度关注了将单个职责拆分为更小的、离散的代码包。之所以这样做也有一些辅助性的动机，我在此承认这一点。
