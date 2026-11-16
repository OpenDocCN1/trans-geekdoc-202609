6) Save, upload, and test the file in a browser.
When you click the View All link, you’ll be taken to tours_detail.asp, which should
function as before. The important thing to remember for later is that when users
click this link, no additional variables are sent as URL or form variables.

![](bbox=[0.283, 0.155, 0.862, 0.495])

# SEARCHING BY REGION: BUILDING THE INTERFACES

You are ready to create the first of the remaining two search options: searching by
world region. When you are finished, you will have eight regions listed, each one
linking to tours_detail.asp with a unique querystring appended containing a unique
region ID. Back on tours_detail.asp, the SQL query that returns the tour descriptions
will be filtered so that only the tours with that regionID will be displayed. Once you
are finished, you will repeat the whole process in index.asp, to allow users to jump
straight to tours in their favorite regions from the homepage. When you go to repeat
the process in index.asp, I will encourage you to try to do so from memory; so as you
follow the steps in tours.asp, try to internalize them.

+   1) Create a new recordset on tours.asp with the following settings:
+   Name: rs_worldregions
+   Connection: conn_newland
+   Table: tbl_region
+   Columns: All
+   Filter: None
+   Sort: regionName, Ascending