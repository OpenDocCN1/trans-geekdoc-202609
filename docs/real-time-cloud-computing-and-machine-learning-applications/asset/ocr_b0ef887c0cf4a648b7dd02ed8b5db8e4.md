# Server and Servlet Architectures for a Cloud-Based Real-Time .

![](bbox=[0.337, 0.095, 0.663, 0.471])

Figure 5.22. Selecting Android values with LTE.

The codes for the above process are as follows:

# Listing 5.33. Setting on or off certain fields through the LTE toggle

```
private void useMobileDataValuesActionPerformed(java.awt.event.ActionEvent
event) {
if (useMobileDataValues.isSelected()) {
    mobspeed.setEnabled(true);
    mobuspeed.setEnabled(true);
    tdspeed.setEnabled(false);
    tuspeed.setEnabled(false);
} else {
    mobspeed.setEnabled(false);
    mobuspeed.setEnabled(false);
    tdspeed.setEnabled(true);
    tuspeed.setEnabled(true);
}
}
```

+   2. Likewise, the analysisDeviceActionPerformed() method is shown in Listing 5.34.