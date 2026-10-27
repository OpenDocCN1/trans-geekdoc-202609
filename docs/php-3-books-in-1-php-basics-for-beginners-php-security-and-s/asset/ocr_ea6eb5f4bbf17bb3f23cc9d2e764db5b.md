```
```php
class Testing_Interpreter_Class {
    private $m_Interpreter_Controller;
    private $ m_Interpreter_Action;
    private $ m_Interpreter_Urlvalues;

    public function __construct($interpreterurlvalues)
    {
        $this->            m_Interpreter_Urlvalues     =
        $interpreterurlvalues;
        if ($this-> m_Interpreter_Urlvalues['controller']
            == "")
        {
            $this-> m_Interpreter_Controller = "show";
        }
        else
        {
            $this->  m_Interpreter_Controller  = $this->
            m_Interpreter_Urlvalues['controller'];
        }
        if ($this->  m_Interpreter_Urlvalues['action']  ==
        "")
        {
            $this-> m_Interpreter_Action = "index";
        }
        else
        {
            $this->      m_Interpreter_Action     =  $this->
            m_Interpreter_Urlvalues['action'];
        }
    }
}
```
```

URL commands will be parsed (with the help of .htaccess) to determine which specific controller is being requested and which action (method) in that controller class is being invoked by an object instantiated from this class. I'm hoping you recall some crucial concepts from the previous chapters, which might prompt you to post a question in the comments section. Unless we are using a static method from our controller class, we must build an instance of our controller object (which will not work if we are constructing numerous controllers that do different functions). As a result, we'll need to be able to generate a URL command-specific controller object. As a result, the Interpreter class requires the following method:

```
```php
// Create an object public function with the requested controller Testing_CreateController_Class ()
{
if (class_exists($this->controller))
{
$m_Controller_Parents = class_parents($this->m_m_Interpreter_Controller);
if (in_array("BaseController",$m_Controller_Parents))
{
if (method_exists($this->m_m_Interpreter_Controller,$this-> m_Interpreter_Action))
{
return new $this-> m_Interpreter_Controller($this->m_Interpreter_Action,$this->m_Interpreter_Urlvalues);
}
else
{
throw new Exception($this->m_Interpreter_Urlvalues);
}
```
```