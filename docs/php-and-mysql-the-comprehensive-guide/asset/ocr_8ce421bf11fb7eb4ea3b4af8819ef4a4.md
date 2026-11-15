![](bbox=[0.143, 0.101, 0.693, 0.399])

Figure 24.1 The MongoDB Installer for Windows

An important installation step is to specify the user under which MongoDB runs and the directory in which the databases are stored (see Figure 24.2). The installer grants the selected user write access to this folder, which is why you should carefully consider whether you really want to use the program directory for this purpose.

> **Tip**
> 
> The MongoDB Compass management software can also be installed as part of the installation, and it provides a useful graphical user interface for the MongoDB databases. However, you can also download it later from http://s.prs.co/v602235.

After installation, there are some executable files in the target directory (under Windows, these are .exe files; otherwise, they have no extension):

+   - mongod
+     The database service, and thus the most important component
+   - mongo
+     Interactive shell for managing and operating the database
+   - mongodump
+     Used to create a database dump (backup)
+   - mongorestore
+     Used to restore a dump
+   - mongoexport
+     Used to export database data (e.g., in JSON format)