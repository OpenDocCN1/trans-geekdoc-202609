Objects in PHP are generally allocated and passed through reference. For instance:

```
Class CloneStaffClass
{
public $m_Staff_Name;
}

$firstStaff = new CloneStaffClass();
$firstStaff->m_Staff_Name="Joey";
$secondStaff = $firstStaff;

echo "first Staff = " . $firstStaff->m_Staff_Name . "<BR><BR>";

$secondStaff->m_Staff_Name="Tribbiani";

echo "first Staff = " . $firstStaff->m_Staff_Name . "<BR>";
echo "second Staff = " . $secondStaff->m_Staff_Name . "<BR>";
```

# OUTPUT:

first Staff = Joey
first Staff= Tribbiani
second Staff= Tribbiani

After I made a copy of the $first object named $secondStaff and set the value of $second->m_Staff_Name="Tribbiani," the value of the $firstStaff->m_Staff_Name property changed from "Joey" to "Tribbiani." This is because the $secondStaff object was assigned by reference, and both the $firstStaff and $secondStaff objects relate to the same object.

The __clone() magic-method can also be castoff to produce a duplicate of an object that does not relate to the original object but instead creates a new, fully different object. Instead of setting $secondStaff = $firstStaff, I'll use __clone() to explain how it works in the prior example.

```
Class CloneStaffClass
{
public $m_Staff_Name;
}
$firstStaff = new CloneStaffClass();
$firstStaff->m_Staff_Name="Joey";
$secondStaff = clone $firstStaff;
echo "first Staff = " . $first->m_Staff_Name . "<BR><BR>";

$secondStaff->m_Staff_Name="Tribbiani";

echo "first Staff= " . $firstStaff->m_Staff_Name . "<BR>";
echo "second Staff= " . $secondStaff->m_Staff_Name . "<BR>";
```

# OUTPUT:

First Staff = Joey
first Staff = Joey
second Staff = Tribbiani

The value of $firstStaff->m_Staff_Name did not change after we set a value for $secondStaff->m_Staff_Name. This is due to the fact that cloning allows us to create an object that is