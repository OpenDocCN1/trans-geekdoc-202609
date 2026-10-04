382 T. P. Fowdur, L. Babooram, M. U-D-Ibn Nazir Rosun and M. Indoonondun

# 4.4.12. Downloading to .csv Files

The download operation can be broken down into the use of three buttons functionalities are as

+   - Browse: Opens the aforementioned explorerframe object from the JFrame class, which contains a File Chooser, the latter set to take as input, a specific file directory only. After obtaining the selection, the path to store the .csv file is obtained in a String object which is displayed on the GUI.
- Download last 'N' samples: Retrieves the parameters from the cloud and uses the OpenCSV library to output the specially-formatted characters to a .csv file. The retrieval of parameters is performed using the fetchRegressionValuesPC() method detailed in Section 5.1.12.3 for the local server. In the last JTextField is used to retrieve the last "N" number of parameters to be saved to the .csv file. A request code of "six" is used for downloading samples from locally stored databases such as XAMPP, accessed through the local server.
- Download by a specific date: For the "Cloudant", it takes an input with a particular date entered by the user and fetches the parameters using the fetchRegressionValuesPC() method itself. It compares the user-entered date with records bearing the same date and outputs the matching ones to both a .csv file and the resultArea component on the GUI. It uses a request code of "seven" for the "Local" option.

The codes for these functionalities are included in this section.

# 4.4.12.1. Browse Button

+   1. As mentioned before, "Browse" opens the explorerframe object.

Listing 4.68. Populating the browse button

```
private void browseButtonActionPerformed(java.awt.event.ActionEvent evt) {
    // Open explorer when button is pressed
    explorerframe.setVisible(true);
    // Manually set size of explorer
    explorerframe.setSize(700, 400);
}
```

+   2. To get the path of the directory selected by the user, an actionPerformed is called as shown in Figure 4.68.