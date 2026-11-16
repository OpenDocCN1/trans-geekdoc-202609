```
}

private function SetAccessor($strMember, $strNewValue) {
if (property_exists($this, $strMember)) {
if (is_numeric($strNewValue)) {
eval('$this->' . $strMember . ' = ' . $strNewValue . ';');
} else {
eval('$this->' . $strMember . ' = "' . $strNewValue . '";');
}
$this->arModifiedRelations[$strMember] = "1";
} else {
return(false);
}
}

private function GetAccessor($strMember) {
if ($this->blIsLoaded != true) {
$this->Load();
}
if (property_exists($this, $strMember)) {
eval('$strRetVal = $this->' . $strMember . ';');
return($strRetVal);
} else {
return(false);
}
}

}

?>
```

As you can see, the code has become somewhat longer, so take even more care than you did before when entering this into your editor to ensure that no errant line breaks make their way in.

# Example Implementation

Naturally, the abstract class isn’t of much use without a corresponding implementation that matches your original — namely, a new version of the `User` object. You can call the following code userv3.phpm:

```
<?php

class User extends DataBoundObject {

        protected $FirstName;
        protected $LastName;
        protected $Username;
        protected $Password;
        protected $EmailAddress;

        protected $DateLastLogin;
        protected $TimeLastLogin;
```