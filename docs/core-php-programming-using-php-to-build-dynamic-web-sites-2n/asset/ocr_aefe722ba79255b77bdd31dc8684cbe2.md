# Core PHP Programming

![](bbox=[0.198, 0.095, 0.558, 0.353])

```
<?php
// open file
if($myFile = fopen("data.csv", "r")) {
    print("<TABLE\n");

    while(!feof($myFile)) {
        print("<TR\n");

        $myField = fgetcsv($myFile, 1024);

        for($n=0; $n<count($myField); $n++) {
            print("\tTD\n");
            print($myField[$n]);
            print("</TD\n");
        }

        print("</TR\n");
    }

    fclose($myFile);
    print("</TABLE\n");
}
?>

string fgets(integer file_handle, integer length);
```