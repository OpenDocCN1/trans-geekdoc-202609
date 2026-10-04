# 374 T. P. Fowdur, L. Babooram, M. N-U-Dbn Nazir Rosun and M. Indoonondon

```
pRec.setText(""");
pSent.setText(""");

// Clearing the graph
series.clear();

// Clearing the graph
cloudSwitch.setEnabled(false);
}
```

#  4.4.10. Clearing Graph

When the JComboBox is used to switch between components so that an empty graph is shown. On the GUI, it is first selected and its "action performed" event is selected. The codes are as follows in Listing 4.65.

# Listing 4.65. Clearing the graph upon change of parameter

```
// If the selection is altered
private void parameterSelectionActionPerformed(java.awt.event.ActionEvent evt) {

// Clear the graph upon detecting a change in the parameter
series.clear();
}
```

#  4.4.11. Performing Analytics Using Servlet or Local Server

The servlet is first queried using a specifically constructed String object, passed into a URL object. The servlet is then used with the URLConnection class to make a connection to the servlet and accept data from it. The String object varies depending on inputs taken from the GUI, and so do the results. In simpler terms, inputs namely the prediction time, the window size and current network parameters are used in the hosted prediction and classification algorithms. For the local server, the "Local" radio button is enabled, while entering the IP address of the running local server on NetBeans IDE. This allows local analytics to be performed. The two buttons performing these functions are described in this section.

#  4.4.11. Predict Button

This button focuses on the building of two threads namely predictThread and predictThreadLocal, where the former caters for regression analytics using the