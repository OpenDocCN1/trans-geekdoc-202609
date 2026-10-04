# Data Capture and Client Architecture for a Cloud-Based Real-Time ... 275

# 4.3.3.4. Building the Visuals for csvddownload.xml

The steps used in the two previous sections are repeated and the codes for this layout are as shown in Listing 4.11.

# Listing 4.11. Layout for csvddownload.xml

```
<?XML version="1.0" encoding="utf-8" ?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context=".MainActivity">
    <!-- Field for entering IP Address of the local server -->
    <EditText
        android:id="@+id/EDT1"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:ems="10"
        android:hint="Enter IP address"
        android:inputType="textPersonName" />
    <!-- Button to browse to location to store the .csv file -->
    <Button
        android:id="@+id/browseButton"
        android:layout_width="140dp"
        android:layout_height="wrap_content"
        android:layout_marginLeft="10dp"
        android:layout_marginTop="12dp"
        android:fontFamily="sans-serif"
        android:text="Browse"
        android:layout_gravity="center_horizontal"
        android:textColor="#3F51B5"
        android:textSize="20sp" />
    <!-- Single row with which that components are aligned on the same line -->
    <TableRow
        android:id="@+id/tableRow3"
        android:layout_width="fill_parent"
        android:layout_height="wrap_content"
        android:layout_marginTop="3dp">
        <!-- Field for selecting the data -->
        <TextView
        android:id="@+id/dataSourceText"
```