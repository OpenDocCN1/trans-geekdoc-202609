# Testing a Simple MVC Application

```
if (
    $this->db->dbdriver === 'sqlite3'
    || $this->db->subdriver === 'sqlite'
){
    $this->db->query(
        'DELETE FROM sql_sequence WHERE name=$this->table';
    );
}

$data = [
    'id' => 1,
    'title' => 'News test',
    'slug' => 'news-test',
    'text' => 'News text',
];
$this->db->insert($this->table, $data);
}
```

If seeded is called, it will truncate the news table and insert one record.

> **Testing Tip: Less More**
Insert as little data as possible. Include enough data to satisfy your tests, and no more, as the more data you insert, the longer it takes to run your tests.

# Test Case for the News Model

Now we can write tests for the model. Create the test case class.

application/tests/models/News_model_test.php

```
<?php
class News_model_test extends TestCase
{
}
```

# Fixtures

First, we need to call the database seeder. We'll add the setUpBeforeClass() method to the class.