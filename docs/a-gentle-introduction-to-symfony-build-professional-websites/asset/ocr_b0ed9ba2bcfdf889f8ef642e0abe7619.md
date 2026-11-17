to store any user attribute in it. This data will be available to other requests until the end of the user session, as shown in Listing 6-14. User attributes can store any type of data (strings, arrays, and associative arrays). They can be set for every individual user, even if that user is not identified.

# Listing 6-14 - The sfUser Object Can Hold Custom User Attributes Existing Across Requests

```
class mymoduleActions extends sfActions
{
  public function executeFirstPage($request)
  {
    $nickname = $request->getParameter('nickname');

    // Store data in the user session
    $this->getUser()->setAttribute('nickname', $nickname);
  }

  public function executeSecondPage()
  {
    // Retrieve data from the user session with a default value
    $nickname = $this->getUser()->getAttribute('nickname', 'Anonymous Coward');
  }
}
```

> You can store objects in the user session, but it is strongly discouraged. This is because the session object is serialized between requests. When the session is deserialized, the class of the stored objects must already be loaded, and that's not always the case. In addition, there can be “stalled” objects if you store Propel or Doctrine objects.

Like many getters in symfony, the getAttribute() method accepts a second argument, specifying the default value to be used when the attribute is not defined. To check whether an attribute has been defined for a user, use the hasAttribute() method. The attributes are stored in a parameter holder that can be accessed by the getAttributeHolder() method. It allows for easy cleanup of the user attributes with the usual parameter holder methods, as shown in Listing 6-15.

# Listing 6-15 - Removing Data from the User Session

```
class mymoduleActions extends sfActions
{
  public function executeRemoveNickname()
  {
    $this->getUser()->getAttributeHolder()->remove('nickname');
  }

  public function executeCleanup()
  {
    $this->getUser()->getAttributeHolder()->clear();
  }
}
```

The user session attributes are also available in the templates by default via the $sf_user variable, which stores the current sfUser object, as shown in Listing 6-16.

# Listing 6-16 - Templates Also Have Access to the User Session Attributes