# 426 T. P. Fowdar, L. Babooram, M. N-U-D-ibn Naz Rosun and M. Indoonadon

```
// Enabling mouse wheel support for the panel
chartPanel.setMouseWheelEnabled(true);

// Adding the chart onto jPanel, which mounts onto the existing JFrame
JPanel jpanel = new JPanel();
// Setting the positioning of the panel onto the JFrame
jpanel.setBounds(288, 15, 563, 402);
// Adding the chart onto the jPanel
jpanel.add(chartPanel);
// Adding the jPanel onto the existing JFrame
add(jpanel);
```

# 5.1.7. Retrieving the Last Index from the Cloud

Since two different databases have been stored on IBM Cloud, for the Desktop application and the Android device respectively, this method bears the same principles as the one in Section 4.4.7. However, it is adapted so depending on the selection of the device by the user, the particular database, between PC or Android, is chosen for the index retrieval process. This is done by firstly identifying selection is made by the user on the parameterSelection JComboBox Using the getSelectedItemItem().toString(), the returned string object is created either selection, before updating the username, password and database objects which relate to the credentials of the respective databases.

After retrieving the index from the particular database, the threads defined in Listing 5.1, namely localServer or localSqlServer are started, again depending on the user device selection when the "Launch Monitor" button is pressed. This thread is as shown in Listing 5.4.

# Listing 5.4. Retrieving the last index of records from the cloud

```
// Retrieving the index of records on the cloud
private final Runnable getNumberOftems = new Runnable() {
public void run() {
// Setting the server selection between either PC or Android device
// Setting the credentials of the respective databases
if (localServerDevice.getSelectedItem().toString().equals("PC")) {
username = "apikey-5c23ef26874d4f6cab6a91ca350c71a5";
password = "a82ec2f648edef2fd997744070286bdcf96";
database = "laptopcloudparameters";
}}
```

![](bbox=[0.105, 0.945, 0.135, 0.965])