+   - Export an MDB from the storage with the Get() method, providing both the DMT_ID and the MDB_ID and returning the exact MDB.
+   - Add an up-to-date MDB version of a locally modified MDB in a DMT through the Add() method; this functionality requires the DMT_ID, the MDB_ID of the original MDB, and, specifying the action performed, returns a successful indicator and the MDB_ID chosen by the version control tool. The Action is related to what the user needs to do when uploading a new version of MDB in a DMT and can be of different types:
+     - Branch: if the new version of the MDB represents a parallel analysis, i.e. an alternative to the original one;
+     - Update: if the new version of the MDB is an evolution of the original one; and
+     - Merge: if the new MDB version is the result of a merge of multiple MDBs (for this reason the MDB_ID of the original MDB in the Add method can also be a list of MDBs).
+   - Remove an MDB version from a DMT through the Remove() method providing both the DMT_ID and the MDB_ID and returning a successful indicator.
+   - We do not enter the details of the Workspace handling system, and we just specify that its role is to manage the communications, advising the user when the MDB management tool is busy.

Figure 15.1b illustrates the specification regarding the users’ interactions with the MDB management tool, regulated following their access profile:

+   - The BA, AA and BM profiles can only perform the Get and Add methods, but only using the Update and Branch action; since those profiles can only act on existing models, they can only use the specimens already present in other existent MDBs to create new Specimen entities; also, if in some cases the merge action could not involve any consistency, when merging different works performed by multiple users, consistencies could appear. For this reason, those profiles need the supervision of an AM user to perform any merge.
+   - The AM can also create new MDBs from scratch using the New method and can perform the Add method with the Merge action.
+   - The MBM user has full authority; he/she can also use the Remove method, to remove an MDB from a DMT.

Overall, the specifications illustrated to show how to manage the MDB tool in working groups. Multiple users can work on different MDBs and also on different analyses, subject to the limits of their roles. The high-level users (BA, AA and BM in Figures 15.1b and 15.3) can work in parallel on different