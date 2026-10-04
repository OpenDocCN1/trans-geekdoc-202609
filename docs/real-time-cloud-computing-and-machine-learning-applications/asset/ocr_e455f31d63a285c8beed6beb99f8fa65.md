384 T. P. Fowdur, L. Babooram, M. U-D-Ibn Nazir Rosun and M. Indoondonon

# Listing 4.70. Creating a name for the .csv file for samples download

```
private void downloadButtonActionPerformed(java.awt.ActionEvent event) {
    // User should input the number of records as well as choose the
destination before downloading
    if (path.equals("") || lastN.getText().toString().equals("")) {
        System.out.println("Please browse for a destination first and enter
the number of records.");
    } else {
        // Making an automatic file name based on number of values to be
        printed, as well as the selected device
        filename = "Last_" + lastN.getText().toString() + "_" + "PC";
        // Adding the .csv extension to the filename
        finalpath = path + "\" + filename + ".csv";
        // Storing the full directory path into the finalpath
        System.out.println("File path: " + finalpath);
}
```

E.g., the name depicted in Figure 4.69 is constructed by the snippet
Listing 4.70 if 20 items are chosen for download. The first path refers to the directory
selection made by the user and the file path pertains to its String addition with the
built file name.

```
run:
The current set path is:
C:\Users\...Last_20_PC.csv
```

Figure 4.69. Example of making a filename for a downloaded .csv file.

The next step is to fetch the values from the Cloudant database and use the
OpenCSV library to prepare the data to be saved in the .csv file. This is performed
when the "Cloudant" radio button is clicked using the "download" Runnable thread.

+   - Fetch "N" from the GUI
- Fetch all the records on the cloud using fetchRegressionValuesPC().
- Create a List object bearing String variables
- Add a a header record bearing the parameter names
- Use the List object to store the variables to be sent via a for loop
encompassing the last "N" number of records by converting the variables of
type double to String