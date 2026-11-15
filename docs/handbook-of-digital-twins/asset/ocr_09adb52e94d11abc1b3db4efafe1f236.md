analyses, but when all the analyses serve to take a decision, an – or a group of – AM will merge all of their work, inserting new specimens with new behaviours and/or identifying the consistencies if needed. As a consequence, the AMs that work to take different decisions on the same DMT would identify together if it is the case to add some consistency functions inside the constructed MDBs under the advice of an MBM.

It is evident that the whole unification works to replicate the PT cannot be a completely automatic process, it requires the collaboration of different professionals with more or less expertise in their field that must communicate and collaborate among themselves. The tool will support their work by checking if all the inserted models are consistent.

# 15.5.3 Complete Specification

Overall, we can say that each user has access to his/her workspace from which he/she can use methods to import, create, edit and save back to a DMT in the storage his/her work, i.e. new models in the form of MDB structure and simulation results. Figure 15.4 depicts the UML class diagram of the different workspaces in which the different profiles interact depending on their privileges.

All the profiles inherit the possibility to login(), and then, each profile is allowed to visualise a specific workspace with the privileges required by the class, as listed in the following (coherently with all the specifications described in this chapter).

+   The BA has the Workspace_BA class: he/she can import an MDB with the correspondent function Get() knowing the DMT_ID and the MDB_ID; he/she can open a specimen selecting the MDB_ID and simulate the said specimen respectively with the Open() and with the Simulate() functions. The user can also add a new specimen as a list of other specimens with the function NewSpecimen(), or add a specimen at a time to an existing one with AddSpecimen(). Finally, he/she can add the modified MDB to the storage through the use of the Add() function, but only using the actions branch or update.

+   The AA can add from its Workspace_AA a new set of parameters for a certain dataset with the function AddParData() indicating the DataSet_ID to which the parameters refer. Then, he/she can create a new specimen with the function AddSpecimen(), selecting an already existent specimen through the Specimen_ID and adding the new DataSet_ID that must be coherent with the said behaviour of the specimen.

+   The BM uses the Workspace_BM, which allows the BM profile to create new specimens as aggregates of other specimens, eventually adding a new interface and new behaviour placeholders, but always