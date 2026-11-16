```
accomplishments text,
followup text,
literature_request text
);
CREATE UNIQUE INDEX cv_pk on contact_visits (emp_id,week_start,seq);
CREATE INDEX cv_emp_id ON contact_visits (emp_id);
CREATE INDEX cv_week_start ON contact_visits (week_start);
CREATE INDEX cv_seq ON contact_visits (seq);
```

The data is per week, is associated with the employee, and is unique when completed with the SEquence column. There may be a lot.

Note that state is 40 characters long in order to accommodate non-U.S. states, as well as provinces in Canada and Mexico. Also note that the Customer Contact Report contains the employee's department, which currently doesn't exist in the user table. Go ahead and add it:

```
CREATE TABLE "user" (
id serial PRIMARY KEY,
username varchar(32) default NULL,
md5_pw varchar(32) default NULL,
first_name varchar(64) default NULL,
last_name varchar(64) default NULL,
email varchar(255) default NULL,
role char(1) NOT NULL default 's',
department varchar(40) NOT NULL default 's'
);
```

# Customer Contact Tests

Think about how you intend to use the customer contacts. From this input screen, nearly all the form data is provided to you via the Web server, which means that when you prepare to persist it, you'll need the employee ID available from WidgetSession.

In addition, consider what minimum information you'll require before dumping into the table:
id, week_start, and sequence with this PHPUnit test:

```
function testValidContactVisit() {
$cv = new ContactVisit (
array ('emp_id'
=> "1",
'seq'
=> "1",
'week_start'
=> "1980-01-01",
'company_name'
=> "test one",
'contact_name'
=> "Big One",
'city'
=> "Columbus",
'state'
=> "OH",
'accomplishments'
=> "phone call",
'followup'
=> "",
'literature_request' => ""));
$this->assertEquals(true, $cv->isValid(), "valid log");
}
```