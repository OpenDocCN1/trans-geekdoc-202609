```
$this->roleFactory = $roleFactory;
$this->accountFactory = $accountFactory;
}
```

```
public function create($userId)
{
  $role = $this->roleFactory->create($userId);
  $account = $this->accountFactory->create($userId);
  $userData = $this->db->query("SQL statement here");

  $user = new User($userData, $role, $account);
  return $user;
}
```

This is in, an illustration of the Inversion of Control principle. Rather than having our UserFactory reach out to the classes and objects upon which it depends, those dependencies are provided to the factory itself. The factory becomes dependent upon the abstractions declared by the type hinting in the constructor’s method signature.

A very desirable side effect of this is that our object factories have become unit testable too crucially, the database connection object can be mocked appropriately so that we no longer have to drag the database around us. Our full suite of automated tests can once again execute in a matter of seconds, rather than minutes.

This is fantastic news, isn't it? We should go out and celebrate immediately!

This is one particular statement that I could certainly get behind. After all, one of the key themes of this book has been to preserve all our important pub time.

In this particular case though, we need to hold our horses for just a little longer. You see, by turning our factories into objects we've dropped not one, but two problems onto our own doorstep.

The first of these problems is the matter of where and when do we put the new UserFactory() line of code? At what point do we create new instances of the UserFactory? In a bootstrap file that runs at the start of every request? The fact that the UserFactory has a declared dependency on the database connection seems to suggest that this would be prudent.