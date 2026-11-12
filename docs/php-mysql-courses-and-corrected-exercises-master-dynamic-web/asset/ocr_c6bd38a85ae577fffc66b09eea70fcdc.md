# Object-oriented PHP

# Exercise 24 (class without constructor)

Write a class representing a city. It must have the properties name, department, region and number of inhabitants and a method displaying "town X is in department Y of region Z and has N inhabitants".
Create city objects, assign their properties and use the display method.

# Correction

```
<?php
class City {
public $name;
public $department;
public $region;
public $inhabitants;

public function getInfos() {
```