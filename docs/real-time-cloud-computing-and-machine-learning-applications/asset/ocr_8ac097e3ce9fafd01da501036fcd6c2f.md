```
<Button
    android:id="@id/download_date"
    android:layout_width="match_parent"
    android:layout_height="wrap_content"
    android:layout_margin="3sp"
    android:layout_weight="0.3"
    android:padding="3sp"
    android:text="Download" />

</LinearLayout>
```

```
<!-- TextView to display the results from the cloud-->
<ScrollView>
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <TextView
        android:id="@id/results"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_margin="3sp"
        android:background="@android/color/holo_orange_light"
        android:inputType="textMultiLine"
        android:padding="10sp"
        android:scrollbars="vertical"
        android:text="Result appears here."
        android:textColor="@android/color/background_dark"
        android:verticalScrollBarPosition="right" />
</ScrollView>
</LinearLayout>
<android.constraintlayout.layout.widget.ConstraintLayout>
```

# 6.3.24. DownloadData class

This class is used to perform the followings functions:

+   - Displays the UI to the user using the activity_download_data XML layout file.
- Fetches data from the Cloudant database using an inner AsyncTask class, QueryDateCloud, to perform the networking on a background thread.
- Fetches data from a Local Java Server using an inner AsyncTask class, QueryDateLocal, to perform the networking on a background thread.
- After getting the data from the cloud, the data is converted into a CSV file and saved to the internal storage