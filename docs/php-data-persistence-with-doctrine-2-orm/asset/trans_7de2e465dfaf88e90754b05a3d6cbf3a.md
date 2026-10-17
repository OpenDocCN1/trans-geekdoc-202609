

另外，类型为 `VideoPost` 的实体并未按名为“频道”的分类进行组织。我们可以像下面这样覆盖关联：

```
<?php
namespace Entity;

/**
 * @Entity
 * @Table(name="posts_video")
 * @AssociationOverrides({
 *     @AssociationOverride(name="category",
 *         joinColumns=@JoinColumn(
 *              name="channel_id", referencedColumnName="id"
 *         )
 *     )
 * })
 */
class VideoPost extends Post
{
	// [..]
}
```

## 6 实体之间的引用

实体通常是更大、相互关联的对象图的一部分。它们持有对其他实体的引用。一个 `User` 持有其 `Post`s 的引用，而一个 `Post` 引用一个 `Category`，该 `Category` 又引用回设置该 `Category` 的 `User`，以此类推。正如我们将在下文中看到，建立实体之间连接的方式有很多种。连接由它们连接的项目数量以及关联的方向来表征。让我们来看看！

### 演示应用 Talking 的领域模型

下面的代码示例与本书前面介绍的演示应用的领域模型相关。领域模型的图示在本章中可能作为参考很有帮助。

### 6.1 单向一对一关系

与数据库中外键关系不同，数据库中两张表总是双向连接，但对象并非如此。因此，Doctrine 2 在对象之间区分单向关联和双向关联。单向意味着一个对象指向另一个对象，但后者没有指回的指针。

要在两个实体之间建立这种类型的关系，只需选择一个作为指针的成员变量即可：

```
<?php
namespace Entity;

/**
 * @Entity
 * @Table(name="users")
 */
class User
{
	// [..]

	/**
	* @OneToOne(targetEntity="Entity\ContactData")
	*/
	private $contactData;
	
	// [..]
}
```

`@OneToOne` 注解定义了关系的类型——一对一关系。`targetEntity` 属性定义了指针引用的实体类。使用 `targetEntity` 属性给出的类需要完全限定，包括命名空间（如果适用）。无论如何，都不能添加前导反斜杠。

现在，只要事先添加了 getter 方法，就可以通过加载的 `User` 访问引用的实体（`ContactData`）：

```
<?php
var_dump($user->getContactData());
```

然而，上面所示的简单持久化配置之所以有效，仅仅是因为 `ContactData` 有一个名为 `id` 的成员变量：

```
<?php
namespace Entity;

/**
 * @Entity
 * @Table(name="contact_data")
 */
class ContactData
{
	/**
	* @Id @Column(type="integer")
	* @GeneratedValue
	*/
	private $id;
	
	// [..]
}
```

如果成员变量的名称不同，例如 `contactDataId` 或类似名称，则需要告诉 Doctrine 2：

```
<?php
namespace Entity;

/**
 * @Entity
 * @Table(name="users")
 */
class User
{
	// [..]

	/**
	* @OneToOne(targetEntity="Entity\ContactData")
	* @JoinColumn(name="id", referencedColumnName="contactDataId")
	*/
	private $contactData;
	
	// [..]
}
```

本书后面我们将了解更多关于 `@JoinColumn` 注解的细节。

加载 `User` 及其 `ContactData`（如上所示）只有在数据库中的数据结构也事先设置好（除了 PHP 类和持久化配置之外）时才能工作。如果不这样做，这一切都不会工作，Doctrine 2 会报告错误。根据情况，以下之一将为真：

* 我们有一个在数据库中给定的现有数据结构，并将持久化配置调整为适应它。

* 我们没有给定的现有数据结构，且持久化配置没有外部限制。在这种情况下，Doctrine 2 的 `schema tool` 甚至可以仅根据持久化配置在数据库中创建数据结构。关于如何在数据库中自动创建数据结构的更多信息，可以在本书后面的章节“Doctrine 2 on the command line”中找到。

无论如何，重要的是数据结构和 Doctrine 2 持久化映射必须匹配。如果不匹配，肯定会遇到麻烦。schema tool 也可以用来验证数据结构和持久化映射是否匹配。

在下文中，让我们假设我们总是使用 schema tool 为演示应用程序创建数据结构。在这种情况下，调用适当的 schema tool 命令后，将创建表 `users`：

| Col | Type | Length | NULL? | KEY | Extras |
| --- | --- | --- | --- | --- | --- |
| id | INT | 11 | | PRI | auto_increment |
| first_name | VARCHAR | 255 | Y | | |
| last_name | VARCHAR | 255 | Y | | |
| gender | INT | 11 | Y | | |
| name_prefix | VARCHAR | 255 | Y | | |
| contactData_id | INT | 11 | Y | UNI | |

创建的表 `contact_data` 如下所示：

| Col | Type | Length | NULL? | KEY | Extras |
| --- | --- | --- | --- | --- | --- |
| id | INT | 11 | | PRI | |
| email | VARCHAR | 255 | Y | | |
| phone | VARCHAR | 255 | Y | | |

### 6.2 双向一对一关系

与单向一对一关系相反，双向一对一关系存在两个指针：一个从对象 A 指向对象 B，另一个从对象 B 指向对象 A。这里要谈论两个独立的指针很重要，我们马上就会看到。让我们再拿一个 `User` 实体，它引用一个 `UserInfo` 实体：

```
<?php
namespace Entity;

/**
 * @Entity
 * @Table(name="users")
 */
class User
{
	// [..]

	/**
	* @OneToOne(targetEntity="Entity\UserInfo")
	*/
	private $userInfo;

	// [..]
}
```

如果我们现在希望 `UserInfo` 实体指回 `User` 实体，则需要通过添加 `inversedBy="user"` 来扩展 `User` 实体的配置：

```
<?php
namespace Entity;

/**
 * @Entity
 * @Table(name="users")
 */
class User
{
	// [..]

	/**
	* @OneToOne(targetEntity="Entity\UserInfo", inversedBy="user")
	*/
	private $userInfo;

	// [..]
}
```

我们配置了 `UserInfo` 实体有一个名为 `$user` 的指针指向 `UserInfo` 实体。`UserInfo` 实体本身如下所示：

```
<?php
namespace Entity;

/**
 * @Entity
 * @Table(name="user_info")
 */
class UserInfo
{
	/**
	* @Id @Column(type="integer")
	* @GeneratedValue
	*/
	private $id;

	/** @Column(type="datetime", nullable=true) */
	private $signUpDate;

	/** @Column(type="datetime", nullable=true) */
	private $signOffDate = null;

	/**
	* @OneToOne(targetEntity="Entity\User", mappedBy="userInfo")
	*/
	private $user;

	public function setId($id)
	{
		$this->id = $id;
	}

	public function getId()
	{
		return $this->id;
	}

	public function setSignOffDate($signOffDate)
	{
		$this->signOffDate = $signOffDate;
	}

	public function getSignOffDate()
	{
		return $this->signOffDate;
	}

	public function setSignUpDate($signUpDate)
	{
		$this->signUpDate = $signUpDate;
	}

	public function getSignUpDate()
	{
		return $this->signUpDate;
	}

	public function setUser($user)
	{
		$this->user = $user;
	}

	public function getUser()
	{
		return $this->user;
	}
}

