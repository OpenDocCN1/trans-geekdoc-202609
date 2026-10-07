```
function get_first_name() : string
{ return $this->first_name; }
```

```
function get_last_name() : string
{ return $this->last_name; }
```

```
function get_address() : string
{ return $this->address; }
```

```
function get_city() : string
{ return $this->city; }
```

```
function get_state() : string
{ return $this->state; }
```

```
function get_zip_code()
{ return $this->zip_code; }

```

The class shown above provides a basic structure for storing the customer information. __construct(string $value1, string $value2, string $value3, string $value4, string $value5, int $value6)

A constructor method is shown which accepts all values when the object is created. The constructor passes the values to set methods to validate the data before it is stored. Using this structure an object array can be declared to hold all customer objects needed.

We can now pass all information for once customer with just one line of code. $customer_record[] = new Customer("Pete", "Smith", "123 Main Street", "Atlanta", "GA", 30001);

Position zero of the customer_record array would now point to an object