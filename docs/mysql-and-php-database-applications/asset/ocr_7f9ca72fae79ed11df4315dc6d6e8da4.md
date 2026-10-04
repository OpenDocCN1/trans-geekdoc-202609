# 274 Part IV: Not So Simple Applications

METHOD CONSTRUCT() This method is expecting an associative array. Most often, in the course of the application, the associative array will be the result of mysqli_fetch_array(). Each of the keys in the array will become properties of the current object. Note that we have to run the set_thumb_src() property because the thumb_src is not stored in the database.

```
function Construct ($atts="")
{
    if (is_array($atts))
{
        while (list($name,$value) = each($atts))
        {
            if (!empty($value) && !is_array($value))
            {
                $this->$name = $value;
            }
        }
    }
    if (!empty($this->image_src))
    {
        $this->set_thumb_src();
    }
}
```

METHOD BASE() This is the constructor of the Base class. Its major job is to call the Construct() method. If it receives in the first argument, the properties of the object are turned into an associative array with the get_object_vars() function before it is sent to Construct. The thumb_width property is set here because a value of a default property cannot accompany the property’s declaration.

```
function Base ($parent="","atts="")
{
    $this->thumb_width = 50;
    if (is_object($parent))
    {
        $this->Construct(get_object_vars($parent));
    }
    $this->Construct($atts);
}
```

# PRODUCTS

Before we get started explaining this class, let us re-state that this class is very similar to the other classes in this application. If you understand how this works, the rest of the classes should be relatively easy to figure out.