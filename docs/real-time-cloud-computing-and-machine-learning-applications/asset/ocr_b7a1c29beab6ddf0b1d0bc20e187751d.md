268 T. P. Fowdur, L. Babooram, M. N-U-Dbn Nazir Rosun and M. Indoonondan

```
<Spinner
android:id="@id/spinner1"
android:layout_width="249dp"
android:layout_height="24dp"
android:layout_marginLeft="10dp"
android:layout_marginTop="8dp"
android:layout_marginBottom="5dp" />
```

6. The fields 얘가 for the printing of the parameters are added via a TextView component as shown in Listing 4.8. These fields are then replicated and edited to accommodate a total of seven parameters.

# Listing 4.8. XML codes for holding the network parameters

```
<TextView
android:id="@id/textView1"
android:layout_width="wrap_content"
android:layout_height="wrap_content"
android:layout_marginLeft="10dp"
android:text="WiFi Download Speed: "
android:textColor="#3F51B5"
android:textSize="18sp" />
```

```
<TextView
android:id="@id/textView2"
android:layout_width="wrap_content"
android:layout_height="wrap_content"
android:layout_marginLeft="10dp"
android:text="WiFi Upload Speed: "
android:textColor="#3F51B5"
android:textSize="18sp" />
```

```
<TextView
android:id="@id/textView6"
android:layout_width="match_parent"
android:layout_height="wrap_content"
android:layout_marginLeft="10dp"
android:text="LTE Download Speed: "
android:textColor="#3F51B5"
android:textSize="18sp" />
```

```
<TextView
android:id="@id/textView7"
```