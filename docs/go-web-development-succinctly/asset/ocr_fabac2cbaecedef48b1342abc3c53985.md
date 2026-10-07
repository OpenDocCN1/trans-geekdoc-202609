os.O_RDWR|os.O_APPEND, 0660

```
defer warnFile.Close()
if err != nil {
	log.Fatal(err)
}
errorFile, err := os.OpenFile("error.log",
	os.O_RDWR|os.O_APPEND, 0660)
defer warnFile.Close()
if err != nil {
	log.Fatal(err)
}
```

Notice = log.New(noticeFile, "NOTICE: \ log.Date|log.Ltime)
Notice.SetOutput(noticeFile)
Notice.Println("This is basically F.Y.I.")

Warning = log.New(warnFile, "WARNING: \ log.Date|log.Ltime)
Warning.SetOutput(warnFile)
Warning.Println("Perhaps this needs your attention")

Error = log.New(errorFile, "ERROR: \ log.Date|log.Ltime)
Error.SetOutput(errorFile)
Error.Println("You REALLY should fix this!")

Note in the above code listing, 0660 is the file mode argument that enables reading and writing of the file to users and groups. For more information on file mode 0660 (and files in general), see http://www.filepermissions.com/file-permission/0660.

The output is as in Code List 39:

# Code List 39: Log File Output

| notice.log | | warnings.log | | error.log |
|---|---|---|---|---|n| 1 NOTICE: 2017/02/17 18:51:42 This is basically F.Y.I. | | 1 WARNING: 2017/02/17 18:51:42 Perhaps this needs your attention? | | 1 ERROR: 2017/02/17 18:51:42 You REALLY should fix! |

However, none of that is useful for logging web requests, which any decent web server can do. So, let's consider another approach for this.