Server and Servlet Architectures for a Cloud-Based Real-Time ... 689

The navigator tab in Figure 7.8 gives a tree view of the element placement in the JFrame. It also shows the GUI element type and variable name. Table 7.4 details about each GUI element's role.

# Table 7.4. GUI Elements

| Variable Name | Swing Element | Function |
| --- | --- | --- |
| window_s | JTextField | User enters the value of the window size for the algorithm |
| local_server | JButton | When pressed, a thread is started to respond to queries from mobile and desktop users for analytics or CSV file. |
| ptime | JTextField | User enters the value of the prediction time |
| predict | JButton | When pressed, the prediction process is started |
| monitor | JButton | When pressed, the monitoring Thread is started using the start ( ) method. |
| down_n | JTextField | The size of the last N records to fetch |
| result | JTextArea | Area to display the results of the forecast algorithms |
| w_var | JComboBox | Chooses the variable to display on the graph |
| window_label | JLabel | Label for window JTextField |
| prediction_label | JLabel | Label for prediction JTextField |
| download_label | JLabel | Label for the download button |
| result_label | JLabel | Label for result JTextArea |
| graph_label | JLabel | Label for graph |
| date_label | JLabel | Label for date JTextField |
| view_label | JLabel | Label for Data Fetch JTextArea |
| download_date | JButton | Button for downloading data for a specific date |
| down_date | JTextField | TextField to enter the date for the date to be fetched |
| data_view | JTextArea | Area to view the data fetched from the cloud |
| db_src | JComboBox | Presents the user with a choice to select the data source: Local Database – data from the local server Cloud Database – data from Cloudant database |

# 7.1.4. The MainFrame Class

The MainFrame class is the class of the application. This class is responsible for displaying the GUI window, updating the graph with weather information from the edge device in real-time, and downloading the latest weather parameters. The variables and methods present in the class are explained in the following sections.

# 7.1.4.1. Adding the Imports

For the program to work properly, the proper classes need to be imported from their respective package. Listing 7.1 shows the necessary imports in the program.