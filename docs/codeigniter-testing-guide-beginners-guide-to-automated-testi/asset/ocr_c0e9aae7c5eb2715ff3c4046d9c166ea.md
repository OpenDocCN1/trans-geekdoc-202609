Testing a Simple MVC Application

# News Section

Let's take a look at the source code for the News Section.

# News_model Model

The News_model class has two methods. One is to get news items from the database, the other is to insert a news item into the database.

application/models/News_model.php

```
<?php
class News_model extends CI_Model
{
    public function __construct()
    {
        # $this->load->database() method loads loads database class. After loading, you can
        # use it as "$this->db"
        $this->load->database();
    }

    public function get_news($slug = false)
    {
        if ($slug === false) {
            # $this->db->get() method runs the selection query and returns the result.
            $query = $this->db->get('news');
            # $result_array() method returns the query as an array of objects.
            return $query->result_array();
        }
    }

    # $this->db->get_where() method runs the selection with a "where" clause
    # in the second parameter.
    $query = $this->db->get_where('news', ['slug' => $slug]);
    # $row_array() method returns a single row as an array.
    return $query->row_array();
    }

    public function set_news()
    {
        # $this->load->helper() method loads CodeIgniter's helper function.
        $this->load->helper('url');
    }
```