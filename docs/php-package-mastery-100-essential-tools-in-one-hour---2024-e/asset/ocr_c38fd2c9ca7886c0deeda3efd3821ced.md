# 22. Propel

Propel is an advanced open-source Object-Relational Mapping (ORM) library for PHP. It is designed for speed and flexibility, providing an active record implementation that allows developers to query and manipulate database data in an object-oriented way.

Ex:Propel

```
// Example: Querying a table using Propel
require 'vendor/autoload.php';
use Propel\Runtime\Propel;
use Propel\Runtime\ActiveQuery\Criteria;
use YourProject\Model\YourTableQuery;
// Assuming Propel is properly configured and YourTable is a model class
$results = YourTableQuery::create()
->filterBySomeColumn('value')
->orderByAnotherColumn(Criteria::DESC)
->find();
foreach ($results as $result) {
echo $result->getSomeColumn();
}
```