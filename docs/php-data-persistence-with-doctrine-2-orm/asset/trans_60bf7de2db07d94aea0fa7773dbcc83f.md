

```php
<?php
namespace Entity;

/**
 * @Entity
 */
class ImagePost extends Post
{
	/** @Column(type="string") */
	protected $imageUrl;

	/**
	 * @param mixed $imageUrl
	 */
	public function setImageUrl($imageUrl)
	{
		$this->imageUrl = $imageUrl;
	}

	/**
	 * @return mixed
	 */
	public function getImageUrl()
	{
		return $this->imageUrl;
	}
}
```

同样的情况也适用于 `VideoPost`：

```php
<?php
namespace Entity;

/**
 * @Entity
 */
class VideoPost extends Post
{
	/** @Column(type="string") */
	protected $videoUrl;

	/**
	 * @param mixed $videoUrl
	 */
	public function setVideoUrl($videoUrl)
	{
		$this->videoUrl = $videoUrl;
	}

	/**
	 * @return mixed
	 */
	public function getVideoUrl()
	{
		return $this->videoUrl;
	}
}
```

Doctrine 2 使用的数据结构如下所示：

| Col | Type | Length | NULL? | KEY | Extras |
| --- | --- | --- | --- | --- | --- |
| id | INT | 11 | | PRI | auto\_increment |
| user\_id | INT | 11 | YES | MUL | |
| category\_id | INT | 11 | YES | MUL | |
| title | VARCHAR | 255 | | | |
| content | LONGTEXT | | | | |
| discr | VARCHAR | 255 | | | |
| videoUrl | VARCHAR | 255 | YES | | |
| imageUrl | VARCHAR | 255 | YES | | |

现在，所有三种类型的实体都可以轻松地被持久化。这种方法的缺点是，取决于层次结构的复杂程度以及涉及的类型之间的差异程度，表格会不断增长，其中包含许多特定类型永远不会使用的字段。在我们的例子中，`videoUrl` 永远不会被 `ImagePost` 类型的实体使用。`imageUrl` 不会被 `VideoPost` 实体使用，而对于 `Post` 实体来说，这两个字段都将保持空白。

这种方法的优点是，由于其本质，这种策略允许在层次结构中的所有类型之间进行非常高效的排队，而无需任何连接。

#### 5.4.2 类表继承

虽然单表继承为所有类型只使用一个表，但 *类表继承* 是一种不同的方法，其中层次结构中的每个类都映射到多个表。虽然这无疑提供了最佳的灵活性，但这也意味着重建实体将需要在数据库中进行连接。由于连接是昂贵的操作，通常，类表继承的性能不如单表继承。

配置的主要区别在于 `Post`：

```php
<?php
namespace Entity;

/**
 * @Entity(repositoryClass="Repository\Post")
 * @Table(name="posts")
 * @InheritanceType("JOINED")
 * @DiscriminatorColumn(name="discr", type="string")
 * @DiscriminatorMap({"text"="Post","video"="VideoPost","image"= "ImagePost"})
 */
class Post
{
	// member variables and associations shared between all types
}
```

现在不再使用继承类型“SINGLE\_TABLE”，而是使用“JOINED”。这告诉 Doctrine 2 应用类表继承策略。由于将为每个类型使用表，因此为子类配置表名可能很有用：

```php
<?php
namespace Entity;

/**
 * @Entity
 * @Table(name="posts_image")
 */
class ImagePost extends Post
{
	/** @Column(type="string") */
	protected $imageUrl;

	/**
	 * @param mixed $imageUrl
	 */
	public function setImageUrl($imageUrl)
	{
		$this->imageUrl = $imageUrl;
	}

	/**
	 * @return mixed
	 */
	public function getImageUrl()
	{
		return $this->imageUrl;
	}
}
```

表名 `posts_image` 对于 `ImagesPost` 实体很有用。我们也为 `VideoPost` 实体添加了相同风格的配置：

```php
<?php
namespace Entity;

/**
 * @Entity
 * @Table(name="posts_video")	
 */
class VideoPost extends Post
{
	/** @Column(type="string") */
	protected $videoUrl;

	/**
	 * @param mixed $videoUrl
	 */
	public function setVideoUrl($videoUrl)
	{
		$this->videoUrl = $videoUrl;
	}

	/**
	 * @return mixed
	 */
	public function getVideoUrl()
	{
		return $this->videoUrl;
	}
}
```

当让 Doctrine 2 创建数据库架构时，我们将为这个层次结构得到三个表，而 `posts` 表保存主要信息：

| Col | Type | Length | NULL? | KEY | Extras |
| --- | --- | --- | --- | --- | --- |
| id | INT | 11 | | PRI | auto\_increment |
| user\_id | INT | 11 | YES | MUL | |
| category\_id | INT | 11 | YES | MUL | |
| title | VARCHAR | 255 | | | |
| content | LONGTEXT | | | | |
| discr | VARCHAR | 255 | | | |

`posts_video` 表仅保存该类型的特定信息：

| Col | Type | Length | NULL? | KEY | Extras |
| --- | --- | --- | --- | --- | --- |
| id | INT | 11 | | PRI | |
| videoUrl | VARCHAR | 255 | YES | | |

`posts_image` 也是如此：

| Col | Type | Length | NULL? | KEY | Extras |
| --- | --- | --- | --- | --- | --- |
| id | INT | 11 | | PRI | |
| imageUrl | VARCHAR | 255 | YES | | |

通过评估外键引用，可以通过表连接重建 `ImagePost` 和 `VideoPost` 类型的实体。

#### 5.4.3 映射超类

最后，可以使用 *映射超类* 策略。与我们已经讨论的另外两种策略的主要区别在于，超类本身不能是实体。以上面的例子为例，这意味着类 `Post` 本身不能是实体。它只是将成员变量和关联继承给其子类。

要配置映射超类策略，需要将 `@MappedSuperclass` 注释添加到 `Post` 类：

```php
<?php
namespace Entity;

/** @MappedSuperclass */
class Post
{
	// member variables and associations shared between all types
}
```

两个子类 `ImagePost` 和 `VideoPost` 不需要更改。但是，应用映射超类策略后，我们无法再持久化 `Post` 类型的对象，这些对象主要由文本组成。我们可以通过添加另一个名为 `TextPost` 的新类型来解决这个问题：

```php
<?php
namespace Entity;

/**
 * @Entity
 * @Table(name="posts_text")	
 */
class TextPost extends Post
{
	/**
	 * @Id @Column(type="integer")
	 * @GeneratedValue
	 */
	protected $id;

} 
```

现在我们有三个具体的实体类型和一个不是实体的超类。这会导致数据库中有三个表：`posts_text`、`posts_images` 和 `posts_video`。

如上所示，重要的是每个实体都有其 ID 列指定，而映射超类没有。它只继承成员变量和关联，但不继承 ID 列定义。

当像上面所示继承属性或关联时，可能希望覆盖某些定义。

假设我们不想在 `VideoPost` 中谈论 `content`，而是称其为 `closed_caption`。这需要以下配置：

```php
<?php
namespace Entity;

/**
 * @Entity
 * @Table(name="posts_video")
 * @AttributeOverrides({
 *     @AttributeOverride(name="content",
 *         column=@Column(
 *             name = "closed_caption",
 *             type = "text"
 *         )
 *     )
 * })
 */
class VideoPost extends Post
{
	// [..]
}
```

虽然 Doctrine 2 要求成员变量必须是 `private` 或 `protected`，但重要的是要记住，这里成员变量需要是 `protected`。否则它们将在子类中不可用。像上面所示那样将属性 `content` 覆盖为 `closed_caption`，这会导致该类型实体的数据库中有一个 `closed_caption` 列。

