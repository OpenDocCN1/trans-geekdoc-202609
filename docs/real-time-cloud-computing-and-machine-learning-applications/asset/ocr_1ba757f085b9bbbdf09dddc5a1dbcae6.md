742 T. P. Fowdur, L. Babooram, M. N-D-Ibn Nazir Rosun and M. Indoonadon

```
JSONObject JSONObject = new JSONObject(data);
JSONArray analysis_val = new JSONArray[4];
for (int i = 0; i < keys.length; i++) {
  analysis_val[i] = (JSONArray) JSONObject.get(keys[i]);
}

for (int i = 0; i < keys.length; i++) {
  formatted.append(keys[i]).append("\n");
  for (int j = 0; j < analysis_val[i].length; j++) {
    formatted.append("Predicted ");
    .append(variables[j])
    .append(": ")
    .append(analysis_val[i].get(j))
    .append(units[j])
    .append("\n");
  }
  formatted.append("\n");
}
} catch (JSONException e) {
  e.printStackTrace();
}
return formatted.toString();
```

#  7.1.18. Saving Data from the Cloud in a CSV File to the Local Storage

The application can either download data for a specific date or download only the latest N records from the database. To save the latest record to a local device, first the number of records to fetch from the database needs to be entered in the JTextField labelled down_n. After entering an integer value in the box, the download button is clicked and the downloadActionPerformed() method is invoked. The codes for the method are given in Listing 7.23. To save all records for a specific date, the user first, needs to enter a String representation of the date in the "date-date" JTextField. Then, the date entered by the user is obtained using the getText() method. The download button is clicked and the download_dateActionPerformed() method is invoked. The codes for the method are given in Listing 7.24.

# Listing 7.23. downloadActionPerformed() method

```
private void download_dateActionPerformed(java.awt.event.ActionEvent event) {
  // Setfetchdate true since we require data for a specific date
  fetchdate = true;
  downloadThread.start();
}
```