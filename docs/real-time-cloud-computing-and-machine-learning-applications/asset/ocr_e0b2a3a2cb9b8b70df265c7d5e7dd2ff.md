# Data Capture and Client Architecture for a Cloud-Based Real-Time ... 383

![](bbox=[0.146, 0.091, 0.658, 0.323])

Figure 4.68. Binding the actionPerformed(event) event to the file chooser.

+   1. Next, the path is obtained using the getSelectedFile() method and printed on the GUI through Listing 4.69.

# Listing 4.69. Getting the path using the explorer frame

```
private void explorererchooserActionPerformed(java.awt.event.ActionEvent evt) {
    // If the selection is made
    if (evt.getActionCommand().equals(FileChooser.APPROVE_SELECTION)) {
        // Getting the path of the directory
        File f = explorererchooser.getSelectedFile();
        path = f.toString();
        System.out.println("The current set path is:");
        System.out.println(path);
        // Closing the explorer
        explorerframe.setVisible(false);
        // Setting the path obtained in the Path JTextField
        destination.setText(path);
    }
    // If the selection is cancelled, the explorer is closed
    if (evt.getActionCommand().equals(FileChooser.CANCEL_SELECTION)) {
        explorerframe.setVisible(false);
    }
}
```

# 4.4.12.2. Download Last N Samples Button

+   1. With the directory obtained in the path variable, which is a String object, the latter is used to automatically create a proper name for the .csv file. This is the first task performed when clicking the "Download" button.