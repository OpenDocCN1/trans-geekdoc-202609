# Unit Testing for Models

application/models/News_model.php

```
class News_model extends CI_Model
{
    public function __construct()
    {
        $this->load->database();
    }

    public function get_news($slug = false)
    {
        if ($slug === false) {
            $query = $this->db->get('news');
            return $query->result_array();
        }

        $query = $this->db->get_where('news', ['slug' => $slug]);
        return $query->row_array();
    }
n
```

The above code has three dependencies:

+   - $this->load (CI_Loader object)
- $this->db (CI_DB object)
- $query (CI_DB_result object)

> $this->load and $query will be an instance of different classes based on your database configuration. Using our sqlite configuration, $this->db will likely be an instance of CI_pdo_sqlite_driver and $query will be an instance of CI_DB_result. CodeIgniter's database library uses the CI_DB and CI_DB base classes to support drivers for multiple databases, so CI_pdo_sqlite_driver extends CI_DB_driver, which extends CI_DB and CI_pdo_result extends CI_DB_result. Similarly, the CI_Loader object could easily be an instance of MY_Loader or some other library which extends the CodeIgniter loader. With this in mind, our mocks target the base classes, rather than the more specific, configuration-dependent classes.

The _construct() method depends on $this->load (the CI_Loader object). As with most CodeIgniter classes, it is loaded into a property of the core CI_Controller object.

The get_news() method depends on $this->db (the CI_DB object, or CodeIgniter's database library) and $query (the CI_DB_result object, also part of CodeIgniter's database library).