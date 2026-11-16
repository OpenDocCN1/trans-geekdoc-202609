Testing twice in this way is important; PDO will complain rigorously if you attempt to bind a value to a non-existent parameter:

The methods that mark for deletion, destructor, and 'call' overload method (__call()) all remain unchanged from the original User class.

The two accessor methods have been slightly adapted:

```
private function SetAccessor($strMember, $strNewValue) {
    if (property_exists($this, $strMember)) {
        if (is_numeric($strNewValue)) {
            eval('$this->' . $strMember . ' = ' .
            $strNewValue . ';');
        } else {
            eval('$this->' . $strMember . ' = "' .
            $strNewValue . '"');
        };
        $this->arModifiedRelations[$strMember] = "1";
    } else {
        return(false);
    };
}
```

Notice now that the modified relations map is adjusted to indicate that the relation in question has been modified. This data is used by Save() to build a more concise UPDATE or INSERT statement as needed:

```
private function GetAccessor($strMember) {
    if ($this->blIsLoaded != true) {
        $this->Load();
    }
    if (property_exists($this, $strMember)) {
        eval('$strRetVal = $this->' . $strMember . '.;');
        return($strRetVal);
    } else {
        return(false);
    };
}
```

Finally, the 'get' accessor has had a small modification, as you can see from looking at the earlier code. The class is tested to determine whether the 'loaded' flag is set to true. If it is not, then the Load() method is called before attempting to evaluate and return the property.

What about the class itself? As shown in the code for userv3.phpm, it has become much smaller. Notice first that it subclasses from DataBoundObject:

```
class User extends DataBoundObject {
```

As a result, your application must ensure that not only is a require() statement present for the class itself, but also, equally important, that one is present for the DataBoundObject class.