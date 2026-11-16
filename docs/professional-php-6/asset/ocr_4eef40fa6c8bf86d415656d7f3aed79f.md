```
```php
public function __get($nm) {
    $result = pg_query("SELECT variable_value FROM session_variable WHERE
        session_id = " . $this->native_session_id . " AND
        variable_name = '" . $nm . "'");
    if (pg_num_rows($result)>0) {
        $row = pg_fetch_array($result);
        return(unserialize($row["variable_value"]));
    } else {
        return(false);
    };
};

public function __set($nm, $val) {
    $strSer = serialize($val);
    $stmt = "INSERT INTO session_variable(session_id, variable_name,
        variable_value) VALUES(" . $this->native_session_id .
        ", '$nm', '$strSer')";
    $result = pg_query($stmt);
}

private function _session_open_method($save_path, $session_name) {
    # Do nothing
    return(true);
}

private function _session_close_method() {
    pg_close($this->dbhandle);
    return(true);
}

public function __session_read_method($id) {
    # We use this to determine whether or not our session actually exists.
    $strUserAgent = $_SERVER["HTTP_USER_AGENT"];
    $this->php_session_id = $id;
    # Set failed flag to 1 for now
    $failed = 1;
    # See if this exists in the database or not.
    $result = pg_query("select id, logged_in, user_id from \"http_session\"
        where ascii_session_id = '$id'");
    if (pg_num_rows($result)>0) {
        $row = pg_fetch_array($result);
        $this->native_session_id = $row["id"];
        if ($row["logged_in"]=="t") {
            $this->logged_in = true;
            $this->user_id = $row["user_id"];
        } else {
            $this->logged_in = false;
        };
    } else {
        $this->logged_in = false;
    }
}
```
```