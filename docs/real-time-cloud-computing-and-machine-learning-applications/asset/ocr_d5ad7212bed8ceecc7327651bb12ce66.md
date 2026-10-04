# Data Capture and Client Architecture for a Cloud-Based Real-Time ... 263

![](bbox=[0.373, 0.096, 0.626, 0.497])

Figure 4.12. Download Menu.

The three activities can be summarised as follows.

+   1. The first screen is the layout from the activity_main.xml file and has three buttons and a dropdown menu. The values fetched and calculated are printed in TextView fields.

+   2. When the “Monitor” button is clicked, the parameter-fetching process is started through the use of a thread. The latter is stopped if the “Stop” button is pressed.

+   3. The components placed in the GUI in Figure 4.10 accommodate for a live graph as well as TextView fields where the parameters can be viewed with respect to time. Additional features such as panning and zooming in and out of the chart are also implemented. The drop-down allows the choice between several parameters to be displayed on the graph in real-time.

+   4. When the user presses on the “Go to analysis” button, the 2nd menu, in Figure 4.11 pops up. This is the layout of another XML file created and labelled prediction.xml. In, it involves the interface that makes a call for specific analytics and displays the result from either client servlet or the local server running on NetBeans IDE.

+   5. Additionally, from the Network Monitoring Menu, the “Go to download” button can be pressed to trigger the 3rd menu in Figure 4.12. Using the three buttons namely, “Browse” and the two “Download” buttons, the user can select a