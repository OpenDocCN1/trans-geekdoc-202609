# Data Capture and Client Architecture for a Cloud-Based Real-Time ... 623

```
android:layout_height="wrap_content"
android:layout_margin="3sp"
android:layout_weight="0.3"
android:padding="3sp"
android:text="Download"/>
</LinearLayout>
```

```
<!-- Layout representing the 3rd Row --
<LinearLayout
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:layout_margin="3sp"
android:background="#E3F2FD2"
android:orientation="horizontal"
android:padding="3sp">
```

```
<!-- View label for prediction time --
<TextView
android:id="@+id/textView2"
android:layout_width="match_parent"
android:layout_height="40sp"
android:layout_gravity="center"
android:layout_margin="3sp"
android:layout_weight="0.3"
android:foregroundGravity="center_vertical"
android:gravity="center|end"
android:padding="2sp"
android:text="Download for Date :""
android:textColor="@android/color/background_dark"/>
```

```
<!-- EditText for the prediction time --
<EditText
android:id="@+id/date_text"
android:layout_width="match_parent"
android:layout_height="40sp"
android:layout_gravity="center"
android:layout_margin="3sp"
android:layout_weight="0.3"
android:ems="10"
android:foregroundGravity="center_vertical"
android:gravity="center"
android:inputType="text"
android:padding="2sp"
android:text="29/11/2020"
tools:ignore="Textfields"/>
```