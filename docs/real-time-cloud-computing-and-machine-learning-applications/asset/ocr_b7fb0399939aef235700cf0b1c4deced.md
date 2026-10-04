# Server and Servlet Architectures for a Cloud-Based Real-Time . 483

detailed in Section 4.4.12. The only difference lies in the selection of the specific device for which the database is to be fetched from the local server caters for both edge devices. Databases can either be fetched from the IBM Cloud or databases stored on localhost. For this reason, the desired device for downloading purposes is selected using the downloadDevice dropdown. The code then detects which device is selected before executing the fetchRegressionValuesAndroid() or the fetchRegressionValuesPC() method.

The codes for these functionalities are included in this section.

# 5.1.13.1. Browse Button

+   1. As mentioned before, the browse button opens the explorerframe object.

Listing 5.20. Implementing the button actionPerformed(java.awt.ActionEvent evt) {

```
// Open explorerframe when button is pressed
explorerframe.setVisible(true);
// Manually set size of explorer
explorerframe.setSize(700, 400);
```

+   2. To get the path of the directory selected by the user, an actionPerformed event is best called as shown in Figure 5.19.

![](bbox=[0.125, 0.574, 0.873, 0.804])

Figure 5.19. Binding an actionPerformed() to the file chooser.

+   3. Next, the path is obtained using the getSelectedFile() method and printed on the GUI, in Listing 5.21.