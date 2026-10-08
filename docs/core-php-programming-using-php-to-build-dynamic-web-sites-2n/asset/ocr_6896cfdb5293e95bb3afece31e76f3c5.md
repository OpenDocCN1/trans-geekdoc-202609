# Core PHP Programming

![](bbox=[0.218, 0.097, 0.577, 0.473])

```
<?php
/*
** printEmployees
** send entire list of employees to browser
*/
function printEmployees($employee) {
    foreach ($employee as $value) {
        printf("%s (%s) %.2f/Hour <BR>\n",
            $value[0],
            $value[1],
            $value[2]);
    }
}

// Create some employees (Name, Title, Wage)
$employee[] = array(
    array("Smith, John", "Programmer", 20),
    array("Doe, Jane", "Programmer", 20),
    array("Mann, Joe", "Manager", 35),
    array("Smith, John", "CEO", 50),
    array("Leeds, Al", "President", 100)),
    array("Unsorted")
);

print(\<B>Unsorted</B><BR>\n");
printEmployees($employee);

print(\<B>Sorted by Name</<B><BR>\n");
```