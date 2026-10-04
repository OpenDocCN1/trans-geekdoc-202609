# Data Capture and Client Architecture for a Cloud-Based Real-Time ... 269

```
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:layout_marginLeft="10dp"
android:text="LTE Upload Speed:"
android:textColor="#3F51B5"
android:textSize="18sp" /
```

```
<TextView
android:id="@id/textView3"
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:layout_marginLeft="10dp"
android:text="Packets received:"
android:textColor="#3F51B5"
android:textSize="18sp" /
```

```
<TextView
android:id="@id/textView4"
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:layout_marginLeft="10dp"
android:text="Packets Sent:"
android:textColor="#3F51B5"
android:textSize="18sp" /
```

```
<TextView
android:id="@id/textView5"
android:layout_width="230dp"
android:layout_height="wrap_content"
android:layout_marginLeft="10dp"
android:text="Wifi Signal Strength:"
android:textColor="#3F51B5"
android:textSize="18sp" /
```

7. Finally, the "Go to Analysis" and "Go to Download" buttons are added the same way as in Step 4, editing each of their gravity to centre the button horizontally. The codes are given in Listing 4.9.

# Listing 4.9. XML for adding buttons to network monitoring menu

```
<Button
android:id="@id/algoButton"
android:layout_width="250dp"
```