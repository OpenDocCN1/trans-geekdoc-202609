```
android:layout_height="0dp"
android:layout_margin="3sp"
android:layout_weight="1"
android:orientation="vertical"
android:padding="3sp">

<!-- Spinner to choose which value to display on the graph --
<Spinner
android:id="@+id/var_spinner"
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:layout_margin="3sp" />

<!-- Graph to display the values obtained --
<com.github.mikephil.charts.LineChart
android:id="@+id/livedata"
android:layout_width="match_parent"
android:layout_height="match_parent"
android:layout_margin="3sp" />
</LinearLayout>

<!-- Linear Layout to organize the elements horizontally (Row 3) --
<LinearLayout
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:layout_margin="3sp"
android:orientation="horizontal"
android:padding="3sp">

<!-- Button that Launches the 'Activity' Activity -->
<Button
android:id="@+id/analyse_btn"
android:layout_width="wrap_content"
android:layout_height="wrap_content"
android:layout_weight="0.5"
android:text="@string/analyse_button" />

<Button
android:id="@+id/download_data"
android:layout_width="wrap_content"
android:layout_height="wrap_content"
android:layout_weight="0.5"
android:text="Download Data" />
</LinearLayout>
</LinearLayout>
<androidx.constraintlayout.widget.ConstraintLayout>
```