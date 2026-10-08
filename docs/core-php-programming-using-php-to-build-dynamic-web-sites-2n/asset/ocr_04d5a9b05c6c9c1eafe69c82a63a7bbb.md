```
if($db)
{
    for($n=1; $n=10; $n++)
    {
        //insert row
        dba_insert($n, '', $db);

        //synchronize
        dba_sync($db);
    }

    // close database
    dba_close($db);
}
else
{
    print('Database does not exist');
}?
```

# # filePro

filePro is a relational database by fP Technologies. There are versions for win32 and SCO UNIX. PHP only supports reading from filePro databases. Further information can be found at the filePro Web site <http://www.fptechnologies.com/>. To enable filePro functions dynamically, use the dl function to load the appropriate extension. You can also compile filePro support into the PHP module. Chad Robinson wrote the filePro extension.

# # boolean filePro(string directory)

The filepro function starts a connection to a map file. Information about the database is stored in memory and used by the other FilePro functions.

```
<?
//get information about database
filepro("/fp/store");

print("TABLE");

//create headers that that contain
//field names, type, width
print("TR\n");
for($col=1; $col= filepro_fieldcount($col); $col++)
{
    print("TH");
    print(filepro_fieldname($col));
    print(" ");
    print(filepro_fieldtype($col));
    print(" ");
    print(filepro_fieldwidth($col));
```