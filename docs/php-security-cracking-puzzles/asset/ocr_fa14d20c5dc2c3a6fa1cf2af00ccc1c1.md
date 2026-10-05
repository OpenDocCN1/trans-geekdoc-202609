```
// authorization form
if (empty(\$_POST)) {
  <table>
    <form method=post>
      <tr>
        <td>Login:</td>
        <td><input type=text name=name></td>
      </tr>
      <tr>
        <td>Password:</td>
        <td><input type=password name=pass></td>
      </tr>
      <tr>
        <td>&nbsp;</td>
        <td><input type=submit value='Enter'></td>
      </tr>
    </form>
  </table>
}?>
<?php
// If the POST data were
// sent, processing them
else {
  // Verifying the input
  // user name and password
  $arr = file(\$filename);
  $i = 0;
  $temp = array();
  foreach($arr as $line) {
    // Breaking the line at the :: dividers
    $data = explode(":", $line);
    // Placing the names of the already
    // registered users into the $data array
    $temp['name'][\i] = \$data[0];
    $temp['password'][\i] = \$data[1];
    $temp['email'][\i] = \$data[2];
```