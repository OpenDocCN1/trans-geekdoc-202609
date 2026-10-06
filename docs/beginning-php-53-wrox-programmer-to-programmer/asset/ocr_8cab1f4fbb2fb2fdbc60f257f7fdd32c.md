# Part III: Using PHP in Practice

![](bbox=[0.135, 0.075, 0.755, 0.535])

# Thank You

Thank you for registering. Here is the information you submitted:

| First name | Matt |
|---|---|
| Last name | Doyle |
| Password | secret |
| Retype password | secret |
| Gender | M |
| Favorite widgets | megaWidget,wonderWidget |
| You want to receive the following newsletters: | widgetTimes,funWithWidgets |
| Comments | I love widgets! |

# How It Works

The Web form, registration_multi.html, is largely similar to the previous registration.html page. However, this contains a multi-select list box (favoriteWidgets) and two checkboxes with the same name (newsletter). Because these controls are capable of sending multiple values, empty square brackets ([]) are appended to the field names:

```
<label for="favoriteWidgets">What are your favorite widgets?</label>
<select name="favoriteWidgets[]" id="favoriteWidgets" size="3">
  <option value="superWidget">The SuperWidget</option>
  <option value="megaWidget">The Megawidget</option>
  <option value="wonderWidget">The WonderWidget</option>
</select>
```

```
<label for="newsletterWidgetTimes">Do you want to receive our
'Widget Times'</label>
  <input type="checkbox" name="newsletter[]" id="newsletterTimes" value="widgetTimes" />
<label for="newsletterFunWithWidgets">Do you want to receive our
'Fun with Widgets' newsletter?</label>
  <input type="checkbox" name="newsletter[]" id="newsletterFunWithWidgets" value="funWithWidgets" />
```

240