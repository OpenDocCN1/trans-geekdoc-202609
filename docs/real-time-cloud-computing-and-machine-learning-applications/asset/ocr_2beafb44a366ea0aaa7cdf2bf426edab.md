# Chapter 5

SERVER AND SERVLET ARCHITECTURES FOR A CLOUD-BASED REAL-TIME NETWORK ANALYTICS SYSTEM

This chapter breaks down the implementation of a local server which acts as a centraliseded software for network analytics, capable of handling tasks involving the edge devices. This is detailed in Section 5.1. The server is run and tested in Section 5.2 before implementing the same functionalities on a hosted servlet, in Section 5.3. The latter also elaborates on the development of web pages for each edge device, that provide GUI interfaces.

# 5.1. LOCAL SERVER IMPLEMENTATION FOR NETWORK DATA CAPTURE AND FORECASTING

The wide array of information captured using the edge devices can be pushed to a running server using NetBeans using client-server paradigm with the Socket and ServerSocket classes. This server performs the following functions which are separately coded using Thread and Runnable objects to allow concurrent I/O operations:

+   - Launching the monitoring server which waits for a connection from either edge devices.
- Printing the received values upon connection, to a live monitoring graph.
- Launching a download and analytics server which returns values to the edge devices upon request.
- Downloading the last "N" number of values to .csv files from either a Cloudant database or a database hosted on localhost.
- Downloading by a specific date to .csv files from either a Cloudant database or a database hosted on localhost.