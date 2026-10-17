
# 使用 Doctrine 2 与 Zend Framework 2

The easiest way to use to Doctrine 2 with Zend Framework 2 (ZF2) is a Composer based installation. The ZF2 module [doctrine-orm-module](https://github.com/doctrine/DoctrineORMModule) not only ships the glue code to make both libraries work together, but also ensure that the Doctrine 2 library itself is downloaded and installed in an existing ZF2 application. One simply needs to add the following line to the `require` block of the projects’ `composer.json`:

```
"doctrine/doctrine-orm-module": "dev-master"
```

Above the `require` block the following line must also be added:

```
"minimum-stability": "alpha"
```

If this configuration is missing, Composer might refuse to install the module. In fact, with this configuration, we tell Composer to install even non-stable modules.

The following commands start the download and the installation process:

```
$ php composer.phar update
```

As one can see, a whole bunch of other ZF2 modules and additional libraries are downloaded.

Last but not least two ZF2 modules must be activated via the `application.config.php`:

```
<?php
return array(
	'modules' => array(
		'Application',
		'DoctrineModule',
		'DoctrineORMModule'
	),
	'module_listener_options' => array(
		'config_glob_paths'    => array(
			'config/autoload/{,*.}{global,local}.php',
		),
		'module_paths' => array(
			'./module',
			'./vendor',
		),
	),
);
```

The modules register several services in Main Service Manager, all starting with the label “doctrine”, e.g. `doctrine.cache.apc` and `doctrine.sqlloggercollector.ormdefault`.

The entity manager can be obtained using a long-winded label:

```
<?php
// [..]
$this->getServiceLocator()->get('doctrine.entitymanager.orm_default');
```

But before this works, some additional configuration is need. Doctrine 2 needs to know where the entity classes are located and what the caching strategy looks like. The following example from the `module.php` tells Doctrine that the mappings are given as annotation, the entities are located in `__DIR__ . '/../src/Application/Entity'` and caching takes place via PHP arrays:

```
<?php
// [..]
'doctrine' => array(
	'driver' => array(
		'my_annotation_driver' => array(
			'class' => 'Doctrine\ORM\Mapping\Driver\AnnotationDriver',
			'cache' => 'array',
			'paths' => array(__DIR__ . '/../src/Application/Entity')
		)
	)
)
// [..]
```

To allow other ZF2 modules to provide entities to the application, a so-called “Driver Chain” allow to combine multiple entity sources even with different mapping formats and caching strategies:

```
<?php
// [..]
'doctrine' => array(
	'driver' => array(
		'my_annotation_driver' => array(
			'class' => 'Doctrine\ORM\Mapping\Driver\AnnotationDriver',
			'cache' => 'array',
			'paths' => array(__DIR__ . '/../src/Application/Entity')
		),
		'orm_default' => array(
			'drivers' => array(
                'Application\Entity' => 'my_annotation_driver'
            )
        )
	)
)
// [..]
```

Now the database connection must be configured. Usually, a dedicated config file in the `autoload` folder is used, e.g. `db.local.php`:

```
<?php
return array(
	'doctrine' => array(
		'connection' => array(
			'orm_default' => array(
				'driverClass' => 'Doctrine\DBAL\Driver\PDOMySql\Driver',
				'params' => array(
					'host'     => 'localhost',
					'port'     => '3306',
					'user'     => 'username',
					'password' => 'password',
					'dbname'   => 'database',
				)
			)
		)
	),
);
```

Once done, we can start dealing with entities (e.g. a `Product` entity) through Doctrine 2:

```
<?php
namespace Application\Entity;

use Doctrine\ORM\Mapping as ORM;

/**
 * @ORM\Entity
 * @ORM\Table(name="product")
 */
class Product
{
	/**
	* @ORM\Id @ORM\Column(type="integer")
	* @ORM\GeneratedValue
	*/
	protected $productId;

	/** @ORM\Column(type="string", nullable=true) */
	protected $name;

	/** @ORM\Column(type="integer") */
	protected $stock;

	/** @ORM\Column(type="string", nullable=true) */
	protected $description;

	/** @ORM\Column(type="string", nullable=true) */
	protected $features;

	public function setDescription($description)
	{
		$this->description = $description;
	}

	public function getDescription()
	{
		return $this->description;
	}

	public function setFeatures($features)
	{
		$this->features = $features;
	}

	public function getFeatures()
	{
		return $this->features;
	}

	public function setProductId($productId)
	{
		$this->productId = $productId;
	}

	public function getProductId()
	{
		return $this->productId;
	}

	public function setName($name)
	{
		$this->name = $name;
	}

	public function getName()
	{
		return $this->name;
	}

	public function setStock($stock)
	{
		$this->stock = $stock;
	}

	public function getStock()
	{
		return $this->stock;
	}
}
```

From a controller, a finder method provided by a repository can be accessed like this:

```
<?php
// [..]
$this->getServiceLocator()->get('doctrine.entitymanager.orm_default')
	->getRepository('Application\Entity\Product')
	->findOneByProductId($id);
// [..]
```

The Doctrine 2 command line tools are available as well. One needs to bring up a command line and change to the project’s root folder:

```
$ php vendor/bin/doctrine-module orm:validate-schema
```

## 11.2 Native SQL statements

Doctrine 2 ships with a special class called `NativeQuery` that allows to execute native SQL select statements and to map the results returned to entity objects. What usually works out-of-the-box with Doctrine 2, can be implemented by hand in cases where native queries are needed or where they are the better solution to a problem. `NativeQuery` allows to retrieve “raw data” and then work with entity objects in the following. The [official documentation](http://docs.doctrine-project.org/en/latest/reference/native-sql.html) holds further information about how to properly implement native SQL statements.

Lastly, in general, one needs to remember that it’s always possible to execute arbitrary SQL statements via the underlying database connection:

```
<?php
// [..]
$em->getConnection()->exec('DELETE FROM posts');
```

While it is possible, it should always be the last option. It bypasses the Entity Manager and might produce hard-to-debug issues and data inconsistencies.

## 11.3 Doctrine 2 Extensions

While Doctrine 2 already ships with tons and tons of features, there is even more. In the [Doctrine 2 extension repository](https://github.com/l3pp4rd/DoctrineExtensions) on GitHub, one will find several extensions with solutions to typical problems, which otherwise must be solved individually by each application developer again and again:

*   Tree: Automates the tree handling process and adds some tree specific functions on repositories.

*   Translatable: Gives a very handy solution for translating records into different languages.

*   Sluggable: Takes a specified field from an entity and makes it compatible for URLs.

*   Timestampable: Updates date fields on create, update and even property change.

*   Blameable: Updates string or reference fields on create, update and even property change with a string or object (e.g. user).

*   Loggable: Helps tracking changes and history of objects, also supports version management.

*   Sortable: Makes any entity sortable.

*   Translator: Supports handling translations.

*   Softdeleteable: Allows to mark entities as deleted, without physically deleting them.

*   Uploadable: Provides file upload handling to entity fields.

*   References: Supports linking entities in Documents and visa versa.
