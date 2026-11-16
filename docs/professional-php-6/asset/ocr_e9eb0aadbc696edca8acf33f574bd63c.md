```
public function getID() {
    return $this->_id;
}

private function _loadCourses(Collection $col) {
    $arCourses = StudentFactory::getCoursesForStudent($this->_id, $col);
}

public function __toString() {
    return $this->_name;
}
}
?>
```

Just as in the Course class, implement the $id and $name properties as private member variables and provide getID() and getName() functions. For now, leave the $courses member as a public member variable. Note the creation of a __toString() method for this class also. This makes it a little bit easier to display the most common string representation of any object (in this case, the name of the student).

In the constructor, call setLoadCallback() and pass in the name of the loading method __loadCourses() and a reference to the object where that method exists (namely, $this).

The _loadCourses() method takes a Collection as its only parameter, as required by the setLoadCallback() function, and uses a static method of the StudentFactory class (discussed next). This method requires the ID of the student and is passed a Collection object into which to load the courses.

The StudentFactory class contains two static methods that do all the work of loading the student and course information in the database. For this application, three tables must be created in your database: student, course, and studentcourse. The purpose of the first two tables should be fairly obvious — to store the basic information about the students and the courses. The third table has two fields: studentid and courseid. It creates the association between students and courses.

The following SQL statements are for PostgreSQL (the preferred database server for the examples in this book); but with only minor modifications, it would also work for most RDBMSs:

```
CREATE TABLE "student" (
    "studentid" SERIAL NOT NULL PRIMARY KEY,
    "name" varchar(255)
);

CREATE TABLE "course" (
    "courseid" SERIAL NOT NULL PRIMARY KEY,
    "coursecode" varchar(10),
    "name" varchar(255)
);

CREATE TABLE "studentcourse" (
    "studentid" integer,
```