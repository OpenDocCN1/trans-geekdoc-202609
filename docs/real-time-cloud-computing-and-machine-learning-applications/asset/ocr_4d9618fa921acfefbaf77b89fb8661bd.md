```
Runnable runnable = new Runnable() {
@Override
public void run() {
try {
```

```
client = ClientBuilder.url(new URL("https://913fa458-c60e-496a-b6b0-1cd3d57936a-bleumix.cloudant.com"))
.username("apikey-e79d3b976eb44cdb1a5671ae808c391")
.password("e8c0b073feb3c68823db7583e43bcca90b1ebebe")
.build();
```

```
 catch (IOException e) {
System.err.println(e.toString());
System.out.println("catch");
}
```

```
Database db = client.database("student_records", false);
Selector = eq("Id",id1);
```

```
try {
QueryResult<Object> newnewant = db.query(new
QueryBuilder(selector).build(),Object.class);
String all =newtenantant.getDocs().toString();
TV3.setText(all);
catch(Exception e){
}
};
```

```
Thread task = new Thread(runnable);
task.start();
}}
}
```

Figure 2.105 (a) shows a snapshot of the application when specific fields from a student record with ID 12 is retrieved and Figure 2.105(b) shows a snapshot of the application when all the fields from a student record with ID 11 are retrieved.