# 610 T. P. Fowdur, L. Babooram, M. N-U-Dbn Nazir Rosun and M. Indoondom

server IP address. There is a TextView to display the results obtained from the servlet. There are two buttons present.

A button labelled "Cloud Analysis" is present and when the user clicks on this button, the following actions are performed:

+   - A connection to the servlet hosted on the cloud is made using JSOUP.
- The widow size & prediction time are sent together in the URL request.
- The servlet performs the analytics and the result is relayed back to the mobile client.
- The results are displayed in the TextView

A button labelled "Local Analysis" is also present and when the user clicks on this button, the following actions are performed:

+   - A connection to the local server is initiated via a socket connection on port 11111.
- The window size & prediction time is encapsulated in a JSONObject and sent to the server.
- The servlet performs the analytics and the result is relayed back to the mobile client.
- The results are displayed in the TextView

The Analyse Activity UI is shown in Figure 6.17.

![](bbox=[0.203, 0.572, 0.803, 0.907])

Figure 6.17. Analyse Activity Layout.