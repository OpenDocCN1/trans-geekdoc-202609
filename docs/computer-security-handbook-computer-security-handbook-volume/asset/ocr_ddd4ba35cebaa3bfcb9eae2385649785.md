intrusion or interference from processes running on other virtual machines sharing the same physical resources.

# 24.4 FILE SHARING.

Multiuser systems almost always require that files can be shared among a number of users. Two issues arise: access rights and the management of simultaneous access.

# 24.4.1 Access Rights.

The file system should provide a flexible tool for allowing extensive file sharing among users. The file system should provide a number of options so that the way in which a particular file is accessed can be controlled. Typically, users or groups of users are granted certain access rights to a file. A wide range of access rights has been used. The next list indicates access rights that can be assigned to a particular user for a particular file.

+   - **None.** The user may not even learn of the existence of the file, much less access it. To enforce this restriction, the user would not be allowed to read the user directory that includes this file.
+   - **Knowledge.** The user can determine that the file exists and who its owner is. The user is then able to petition the owner for additional access rights.
+   - **Execution.** The user can load and execute a program but cannot copy it. Proprietary programs often are made accessible with this restriction.
+   - **Locking.** The user can change the status of a logical flag that indicates temporary restrictions on access to data. Database management systems provide for locking to control concurrent access to records so that different processes can avoid overwriting each other’s modifications.
+   - **Reading.** The user can read the file for any purpose, including copying and execution. Some systems are able to enforce a distinction between viewing and copying. In the former case, the contents of the file can be displayed to the user, but the user has no means for making a copy.
+   - **Appending.** The user can add data to the file, often only at the end, but cannot modify or delete any of the file’s contents. This right is useful in collecting data from a number of sources.
+   - **Updating.** The user can modify, delete, and add to the file’s data. This normally includes writing the file initially, rewriting it completely or in part, and removing all or a portion of the data. Some systems distinguish among different degrees of updating.
+   - **Changing protection.** The user can change the access rights granted to other users. Typically, only the owner of the file holds this right. In some systems, the owner can extend this right to others. To prevent abuse of this mechanism, the file owner typically is able to specify which rights can be changed by the holder of this extended right.
+   - **Deletion.** The user can delete the file from the file system.

These rights can be considered to constitute a hierarchy, with each right implying those that precede it. Thus, if a particular user is granted the updating right for a particular file, then that user also is granted these rights: knowledge, execution, reading, and appending.