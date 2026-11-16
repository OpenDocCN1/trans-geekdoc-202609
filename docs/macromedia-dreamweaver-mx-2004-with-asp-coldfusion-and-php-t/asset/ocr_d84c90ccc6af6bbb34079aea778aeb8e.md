![](bbox=[0.056, 0.064, 0.626, 0.346])

ColdFusion and PHP Users Only: In the Update Record dialog, choose newland as the Data Source and tbl_users as the Update Table. In the Columns area, make sure that the following two statements appear: 'userID' Selects Record Using 'FORM.userID' as 'Numeric'; 'userGroup' Gets Value From 'FORM.userGroup' as 'Text'; and the rest say Does Not Get a Value. Lower in the dialog, in the After Updating, Go To field, enter admin_addUser_master.cfm. ColdFusion users only: Make sure that Pass Original Query String is unchecked.

With this information, you are telling Dreamweaver to write a SQL query that will update tbl_users' userGroup column with the information stored in the userGroup form element, in the row whose primary key matches the one stored in the form's userID (hidden field) element.

Once users submit the form, they are redirected to admin_addUser_master.cfm, where, as you'll recall, the summary lists each user's current user group, enabling users to make sure that the change went through.

![](bbox=[0.056, 0.71, 0.545, 0.94])