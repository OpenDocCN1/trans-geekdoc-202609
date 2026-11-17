```
// Date and time
$form->setWidget('end', new sfWidgetFormDateTime(array('default' => '01/01/2008 12:00')));
// symfony renders the widget in HTML as 5 dropdown lists for month, day,
year, hour, minute
```

Of course, you can customize the date format, to display it in European style instead of International style (%day%/%month%/%year% instead of %month%/%day%/%year%), you can switch to 2x12 hours per day instead of 24 hours, you can define custom values for the first option of each dropdown box, and you can define limits to the possible values. Once again, check the API documentation for more details about the options of the date and time widgets.

Date widgets are a good example of the power of widgets in symfony. A widget is not a simple form input. It can be a combination of several inputs, that symfony can render and read from in a transparent way.

# I18n Widgets

In multilingual applications, dates must be displayed in a format according to the user culture (see Chapter 13 for details about culture and localization). To facilitate this localization in forms, symfony provides an sfWidgetFormI18nDate widget, which expects a user culture to decide of the date formatting parameters. You can also specify a month_format to have the month drop-down display month names (in the user language) instead of numbers.

```
// Date
$years = range(1950, 1990);
$form->setWidget('dob', new sfWidgetFormI18nDate(array(
  'culture'     => $this->getUser()->getCulture(),
  'month_format' => 'name',    // Use any of 'name' (default),
  'short_name',  and 'number'
  'label'       => 'Date of birth',
  'default'     => '01/01/1950',
  'years'       => array_combine($years, $years)
)));
// For an English-speaking user, symfony renders the widget in HTML as
<label for="dob">Date of birth</label>
<select id="dob_month" name="dob[month]">
<option value=""/>
<option selected="selected" value="1">January</option>
<option value="2">February</option>
...
<option value="12">December</option>
</select>
<select id="dob_day" name="dob[day]">...</select>
<select id="dob_year" name="dob[year]">...</select>
// For an French-speaking user, symfony renders the widget in HTML as
<label for="dob">Date of birth</label>
<select id="dob_day" name="dob[day]">...</select>
<select id="dob_month" name="dob[month]">
<option value=""/>
<option selected="selected" value="1">Janvier</option>
<option value="2">Février</option>
...
<option value="12">Décembre</option>
</select>
<select id="dob_year" name="dob[year]">...</select>
```