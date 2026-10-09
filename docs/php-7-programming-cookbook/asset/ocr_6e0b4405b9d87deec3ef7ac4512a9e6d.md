# How to do it...

+   1.  In the child class, use the keyword extends to set up inheritance. In the example that follows, the Customer class extends the Base class. Any instance of Customer will inherit visible methods and properties, in this case, $id, getId() and setId():

```
class Base
{
    protected $id;
    public function getId()
    {
        return $this->id;
    }
    public function setId($id)
    {
        $this->id = $id;
    }
}

class Customer extends Base
{
    protected $name;
    public function getName()
    {
        return $this->name;
    }
    public function setName($name)
    {
        $this->name = $name;
    }
}
```

+   2.  You can force any developer using your class to define a method by marking it abstract. In this example, the Base class defines as abstract the validate() method. The reason why it must be abstract is because it would be impossible to determine exactly how a child class would be validated from the perspective of the parent Base class:

```
abstract class Base
{
    protected $id;
    public function getId()
    {
        return $this->id;
    }
}
```