+   2. For the purposes of this illustration, let’s assume all entities will have two properties in common: $mapping (discussed later), and $id (with its corresponding getter and setter):

namespace Application\Entity;

class Base
{
protected $id = 0;
protected $mapping = ['id' => 'id'];

public function getId() : int
{
return $this->id;
}

public function setId($id)
{
$this->id = (int) $id;
}
}

+   3. It’s not a bad idea to define an arrayToEntity() method, which converts an array to an instance of the entity class, and vice versa (entityToArray()). These methods implement a process often referred to as hydration. As these methods should be generic, they are best placed in the Base class.

+   4. In the following methods, the $mapping property is used to translate between database column names and object property names. arrayToEntity() populates values of this object instance from an array. We can define this method as static in case we need to call it outside of an active instance:

public static function arrayToEntity($data, Base $instance)
{
if ($data && is_array($data)) {
foreach ($instance->mapping as $dbColumn => $propertyName) {
$method = 'set' . ucfirst($propertyName);
$instance->$method($data[$dbColumn]);
}
return $instance;
}
return FALSE;
}