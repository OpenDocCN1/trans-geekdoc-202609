
- combining related features,
- sampling data to obtain a representative subset (we’ll see in the data science case studies that random sampling is particularly effective for this and we’ll say why),
- standardizing data formats,
- grouping data,
- and more.

It's always wise to hold onto your original data. We’ll show simple examples of cleaning and transforming data in the context of Pandas `Series` and `DataFrame`s.

## Cleaning Your Data

Bad data values and missing values can significantly impact data analysis. Some data scientists advise against any attempts to insert “reasonable values.” Instead, they advocate clearly marking missing data and leaving it up to the data analytics package to handle the issue. Others offer strong cautions. ⁴

4 This footnote was abstracted from a comment sent to us July 20, 2018 by one of the book's reviewers, Dr. Alison Sanchez of the University of San Diego School of Business. She commented: Be cautious when mentioning 'substituting reasonable values' for missing or bad values. A stern warning: 'Substituting' values that increase statistical significance or give more 'reasonable' or 'better' results is not permitted. 'Substituting' data should not turn into 'fudging' data. The first rule readers should learn is not to eliminate or change values that contradict their hypotheses. 'Substituting reasonable values' does not mean readers should feel free to change values to get the results they want.

Let’s consider a hospital that records patients’ temperatures (and probably other vital signs) four times per day. Assume that the data consists of a name and four `float` values, such as

```
['Brown, Sue', 98.6, 98.4, 98.7, 0.0]
```

The preceding patient’s first three recorded temperatures are 99.7, 98.4 and 98.7. The last temperature was missing and recorded as 0.0, perhaps because the sensor malfunctioned. The average of the first three values is 98.57, which is close to normal. However, if you calculate the average temperature *including* the missing value for which 0.0 was substituted, the average is only 73.93, clearly a questionable result. Certainly, doctors would not want to take drastic remedial action on this patient—it’s crucial to “get the data right.”

One common way to clean the data is to substitute a *reasonable* value for the missing temperature, such as the average of the patient’s other readings. Had we done that above, then the patient’s average temperature would remain 98.57—a much more likely average temperature, based on the other readings.

## Data Validation

Let’s begin by creating a `Series` of five-digit ZIP Codes from a dictionary of city-name/five-digit-ZIP-Code key–value pairs. We intentionally entered an invalid ZIP Code for Miami:

Click here to view code image

```python
In [1]: import pandas as pd

In [2]: zips = pd.Series({'Boston': '02215', 'Miami': '3310'})

In [3]: zips
Out[3]:
Boston    02215
Miami     3310
dtype: object
```

Though *zips* looks like a two-dimensional array, it’s actually one-dimensional. The “second column” represents the `Series`’ ZIP Code *values* (from the dictionary’s values), and the “first column” represents their *indices* (from the dictionary’s keys).

We can use regular expressions with Pandas to validate data. The `str` attribute of a `Series` provides string-processing and various regular expression methods. Let’s use the `str` attribute’s `match` method to check whether each ZIP Code is valid:

Click here to view code image

```python
In [4]: zips.str.match(r'\d{5}')

Out[4]:
Boston    True
Miami     False
dtype: bool
```

Method match applies the regular expression \d{5} to each Series element, attempting to ensure that the element is comprised of exactly five digits. You do not need to loop explicitly through all the ZIP Codes—match does this for you. This is another example of functional-style programming with internal rather than external iteration. The method returns a new Series containing True for each valid element. In this case, the ZIP Code for Miami did not match, so its element is False.

There are several ways to deal with invalid data. One is to catch it at its source and interact with the source to correct the value. That’s not always possible. For example, the data could be coming from high-speed sensors in the Internet of Things. In that case, we would not be able to correct it at the source, so we could apply data cleaning techniques. In the case of the bad Miami ZIP Code of 3310, we might look for Miami ZIP Codes beginning with 3310. There are two—33101 and 33109—and we could pick one of those.

Sometimes, rather than matching an *entire* value to a pattern, you’ll want to know whether a value contains a *substring* that matches the pattern. In this case, use method `contains` instead of `match`. Let’s create a `Series` of strings, each containing a U.S. city, state and ZIP Code, then determine whether each string contains a substring matching the pattern ` [A-Z]{2} ` (a space, followed by two uppercase letters, followed by a space):

Click here to view code image

```python
In [5]: cities = pd.Series(['Boston, MA 02215', 'Miami, FL 33101'])

In [6]: cities
Out[6]:
0    Boston, MA 02215
1    Miami, FL 33101
dtype: object

In [7]: cities.str.contains(r' [A-Z]{2} ')
Out[7]:
0     True
1     True
dtype: bool

In [8]: cities.str.match(r' [A-Z]{2} ')
Out[8]:
0    False
1    False
dtype: bool
```

We did not specify the index values, so the `Series` uses zero-based indexes by default (snippet [6]). Snippet [7] uses `contains` to show that both `Series` elements contain substrings that match ' `[A-Z]{2}` '. Snippet [8] uses `match` to show that neither element’s value matches that pattern in its entirety, because each has other characters in its complete value.

## Reformatting Your Data

We’ve discussed data cleaning. Now let’s consider munging data into a different format. As a simple example, assume that an application requires U.S. phone numbers in the format ###-###-####, with hyphens separating each group of digits. The phone numbers have been provided to us as 10-digit strings without hyphens. Let’s create the `DataFrame`:

Click here to view code image

```python
In [9]: contacts = [['Mike Green',
 'demo1@deitel.com', '5555555555'],
...: ['Sue Brown', 'demo2@deitel.com', '5555551234']]
...:

In [10]: contactsdf = pd.DataFrame(contacts,
...: columns=['Name', 'Email', 'Phone'])
...:

In [11]: contactsdf
Out[11]:
 Name            Email              Phone
0 Mike Green  demo1@deitel.com  5555555555
1 Sue Brown   demo2@deitel.com  5555551234
```

In this `DataFrame`, we specified column indices via the `columns` keyword argument but did _not_ specify row indices, so the rows are indexed from `0`. Also, the output shows the column values right aligned by default. This differs from Python formatting in which numbers in a field are _right aligned_ by default but non-numeric values are _left aligned_ by default.

Now, let’s munge the data with a little more functional-style programming. We can `map` the phone numbers to the proper format by calling the `Series` method `map` on the `DataFrame`’s ' `Phone` ' column. Method `map`’s argument is a _function_ that receives a value and returns the _mapped_ value. The function `get_formatted_phone` maps 10 consecutive digits into the format ###-###-####:

Click here to view code image

```python
In [12]: import re
In [13]: def get_formatted_phone(value):
    ...:     result = re.fullmatch(r'(\d{3})(\d{3})(\d{4})', value)
    ...:     return '-'.join(result.groups()) if result else value
    ...:
    ...:
```

The regular expression in the block's first statement matches *only* 10 consecutive digits. It captures substrings containing the first three digits, the next three digits and the last four digits. The `return` statement operates as follows:

- If `result` is None, we simply return `value` unmodified.

- Otherwise, we call `result.groups()` to get a tuple containing the captured substrings and pass that tuple to string method `join` to concatenate the elements, separating each from the next with '-' to form the mapped phone number.

`Series` method `map` returns a new `Series` containing the results of calling its function argument for each value in the column. Snippet [15] displays the result, including the column's name and type:

Click here to view code image

```python
In [14]: formatted_phone = contactsdf['Phone'].map(get_formatted_phone)
In [15]: formatted_phone
0    555-555-5555
1    555-555-1234
Name: Phone, dtype: object
```

Once you've confirmed that the data is in the correct format, you can update it in the original `DataFrame` by assigning the new `Series` to the 'Phone' column:

Click here to view code image

```python
In [16]: contactsdf['Phone'] = formatted_phone
In [17]: contactsdf
Out[17]:
    Name           Email           Phone
0  Mike Green  demo1@deitel.com  555-555-5555
1   Sue Brown  demo2@deitel.com  555-555-1234
```
