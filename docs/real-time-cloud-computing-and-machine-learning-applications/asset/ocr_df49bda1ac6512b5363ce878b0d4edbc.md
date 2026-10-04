# 620 T. P. Fowdur, L. Babooram, M. N-U-D-Ibn Nazir Rosun and M. Indoondonon

# 6.3.23. DownloadDataActivity

This activity presents the user with an interface where the user chooses to download data for a specific date or only the last N rows from the database. This activity consists of an EditText to enter the IP Address of the local server, one to enter the number of samples to fetch, and the other to enter the sample size of data that is required. A switch is present to indicate whether to download data from the Cloudant or local server. There is also two Button, one for each scenario. A TextView is also inside a ScrollView to view the data fetched from the cloud. The UI of the activity is shown in Figure 6.20.

![](bbox=[0.238, 0.319, 0.762, 0.643])

Figure 6.20. DownloadData Activity UI.

The codes for the xml version="1.0" encoding="utf-8"?> download_data.xml file are given below.

```
<?xml version="1.0" encoding="utf-8"?>
<android.constraintlayout.widget.ConstraintLayout
xmlns:android="http://schemas.android.com/apk/res/android"
xmlns:app="http://schemas.android.com/apk/res-auto"
xmlns:tools="http://schemas.android.com/tools"
android:layout_width="match_parent"
android:layout_height="match_parent"
tools:context=".DownloadDataData>

  <LinearLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent">
```