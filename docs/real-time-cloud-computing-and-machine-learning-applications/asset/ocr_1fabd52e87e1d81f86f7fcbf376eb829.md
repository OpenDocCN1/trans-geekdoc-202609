# Data Capture and Client Architecture for a Cloud-Based Real-Time ... 355

10. Before proceeding with saving the fetched values to a .csv file, a location first needs to be brows by mapping the launch of a JFileChooser component to a JButton component. This function is attached to the "Browse" button created, which prints the path selected by the user into the JTextField component next to. To add a destination-choosing property to the JButton button, a new JFrame needs to be created to accommodate the JFileChooser. This is performed by selecting the "Frame" component from the Swing Windows section of the palette and dropping it onto the main frame. From the navigator on the bottom left-side of the software, the newly added frame is automatically added under the "Other Components" tag as shown in Figure 4.61.

![](bbox=[0.266, 0.316, 0.673, 0.447])

Figure 4.61. Create a new frame for the file chooser.

11. It is renamed by being right-clicked, and selecting the "Choose Variable Name" option, after which it is called "exploreerframe." It is opened by being double-clicked, following by the dragging and dropping of the "File Cho" component from the Swing Windows section of the palette. The component is resized and the frame appears as in Figure 4.62.

![](bbox=[0.233, 0.613, 0.773, 0.853])

Figure 4.62. Add file chooser to created frame.