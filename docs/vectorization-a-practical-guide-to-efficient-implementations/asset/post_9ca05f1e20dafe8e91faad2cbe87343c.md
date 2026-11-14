
)
day = tf.strings.to_number(
    tf.strings.substr(timestamps_array, 8, 2),
    out_type=tf.int64
)
hour = tf.strings.to_number(
    tf.strings.substr(timestamps_array, 11, 2),
    out_type=tf.int64
)
minute = tf.strings.to_number(
    tf.strings.substr(timestamps_array, 14, 2),
    out_type=tf.int64
)
seconds = tf.strings.to_number(
    tf.strings.substr(timestamps_array, 17, 2),
    out_type=tf.int64
)
zone = tf.strings.to_number(
    tf.strings.substr(timestamps_array, 19, 3)
)
zone = tf.cast(zone, tf.int64)
# retroactively offset year/ month / day based on zone
if not utc:
    return year, month, day, hour, minute, seconds, zone

# offsets [-1, 0, +1] day
day += (hour - zone) // 24
num_days = tf.constant(
    [31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31],
    dtype=day.dtype
)
is_leap_year = tf.math.logical_and(
    year % 4 == 0, year % 400 != 0
)
# deals with month offsets
month_days = tf.gather(num_days, month - 1)
month_days = tf.where(
    tf.math.logical_and(month == 2, is_leap_year),
    month_days + 1,
    month_days
)
month -= (month_days - day) // month_days
# deals with year offset
year += (month - 1) // 12

# Go back to correct Month
month = (month - 1) % 12 + 1
# Correct day: day > max number of days for the month
day = tf.where(
    day > month_days, day % month_days, day
)
# month_days of the correct month
month_days = tf.gather(num_days, month - 1)
month_days = tf.where(
    tf.math.logical_and(month == 2, is_leap_year),
    month_days + 1,
    month_days
)

# Correct day: case when day = 0
day = tf.where(
    day < 1, month_days, day
)

# Correct hour
hour = (hour - zone) % 24

# make utc zone, which are 0s
zone = tf.zeros_like(seconds)

return year, month, day, hour, minute, seconds, zone

- Lines 9-36 extract the values of the year, month, date, hour, minute, seconds, and timezone information from the string using the substring method and convert each into an integer. A comment on zone: at the time of writing, tf.strings.to_number will throw an error if the string to be converted is prefixed by + and out_type=tf.int64 (confirmed in Tensorflow version 2.11, 2.13, and 2.14 on my MacBook Pro 2021). However, using the default out_type=tf.float32 has no problem. To ensure reproducibility, I have used tf.cast to convert the parsed number from float to integer.

- Lines 38 and 39 return the parsed time information if we want to retain the timestamp as is without converting back to UTC timestamp, by setting utc=True. The rest of the code implements the logic to convert from local timezone to the UTC timestamp.

- Line 42: We first offset the day based on the hour and timezone. (hour - zone) // 24 computes the offset value:
  - If hour - zone >= 24, then we need to add a day. In this case, it is possible we are exceeding the maximum number of days of the month, for example day = 32. We will handle it after computing all the offsets for month and year and come back to correct this later on.
  - If hour - zone < 0, we need to subtract a day. In this case, we may be going to get day = 0. Again, we will handle it after computing all the offsets for month and year and come back to correct this later on.
  - Otherwise, there is no need to offset the day.

- Lines 43–46 set up the `num_days` vector, which encodes the number of days of each month (for a non-leap year, we have additional logic to handle leap years below).

- Lines 47–49 determine if the timestamp occurs on a leap year.

- Lines 51–56 compute how many days the month is supposed to have, that is `month_days`. We use `tf.gather` to look up the expected number of days for a non-leap year first. We then use `tf.where` to replace any leap month with 29 days instead of 28 days instead of 28 days.

- Line 57 offsets the month.
  - If `month_days > day`, then we do not need to offset the `day`. However, if `day = 0`, then we need to offset the month backward by 1. For now, we may encounter cases where the `month = 0` after the offset. This is okay since we will correct it later on after first correcting the `year`.
  - If `month_days <= day`, then we need to add a month. For now, we may encounter cases where `month = 13` after the offset. Again, this is okay, since we will correct it later on after first correcting the `year`.

- Line 59 offsets the year.
  - If `month > 12` (i.e. `month = 13`), then we need to add a year.
  - If `month < 1` (i.e. `month = 0`), then we need to subtract a year.
  - Otherwise, the year does not change.

- Line 62 corrects the month
  - If `month = 13`, then we need to change it to `month = 1`.
  - If `month = 0`, then we need to change it to `month = 12`.

- Lines 64–78 handle the date correction.
  - Lines 64–66: If `day > month_days` exceeds the maximum number of days for the month, then we need to reset starting from the previous month and count the number of days exceeded.
  - Lines 68–73 compute `month_days` (which is the last day of the month) before handling the case where `day = 0`. Because we offset the `month` backward, sometimes to February which can potentially be a leap month, we need to compute which day we need to set back to (as the last day of the previous month) corresponding to the corrected `month` (in this case, a month is subtracted).
  - Lines 76–78 correct the `day` when `day = 0`, by setting the date to the previous month’s last day.

- Line 81 corrects the hour based on zone.
  - If `hour - zone > 24`, e.g. `hour - zone = 25`, then we need to reset the value to `(hour - zone) % 24 = 1`.
  - If `hour - zone < 0`, e.g. `hour - zone = -2`, then we need to reset the value to `(hour - zone) % 24 = 22`.

- Line 84 makes the UTC zone which is filled with zeros. This is just trying to be consistent with our return signature year, month, day, hour, minute, seconds, zone.

- Line 86 returns the outputs.

Let's write several test cases to ensure that the implementation above is indeed working as expected

```
import datetime
import numpy as np
import tensorflow as tf
timestamps_array = tf.constant(
    [
        "2023-05-07 05:32:25-08:00", # utc: same date
        "2023-05-07 17:32:25-08:00", # utc: next day
        "2023-05-07 05:32:25+11:00", # utc: previous day
        "2023-08-31 22:15:37-08:00", # utc: next month
        "2023-06-01 02:23:15+08:00", # utc: previous month
        "2023-12-31 23:32:15-04:00", # utc: next year
        "2023-01-01 02:25:10+04:00", # utc: last year
        "2024-02-28 23:59:11-02:00", # utc: leap year next day (29th)
        "2024-03-01 01:38:17+04:00", # utc: leap year last day (29th)
    ]
)
# parse with our function
year, month, day, hour, minute, seconds, zone = _parse_timestamps(
    timestamps_array, utc=True
)
output_tf = tf.stack(
    [year, month, day, hour, minute, seconds], axis=1
)
# parse each with datetime
output_dt = np.zeros((timestamps_array.shape[0], 6), dtype=int)
for ii, tstamp in enumerate(timestamps_array.numpy().astype(str)):
    datetime_local = datetime.datetime.strptime(
        tstamp, '%Y-%m-%d %H:%M:%S%z'
    )
    datetime_utc = datetime_local.astimezone(datetime.timezone.utc)
    output_dt[ii][0] = datetime_utc.year
    output_dt[ii][1] = datetime_utc.month
    output_dt[ii][2] = datetime_utc.day
    output_dt[ii][3] = datetime_utc.hour
    output_dt[ii][4] = datetime_utc.minute
    output_dt[ii][5] = datetime_utc.second
assert np.allclose(output_dt, output_tf)
```

| :- |
|---|
| **i Note** |
| Fingers crossed that this would no longer be needed in the future. |

## 6.4 Mapping Strings to Indices

When handling categorical features, there is a need to translate the string representations of the features into numerical representations. One-hot encoding and embedding techniques are commonly used to represent string features. To create these types of numerical representations, we first need to determine a list of **vocabulary** of the categorical feature (i.e. all valid values encountered during training time) and assign an ordinal number to each value of the feature. We call this the **index** of the categorical feature value. Much like the concept of indexing that we have seen in Chapter 3, we can use the vocabulary and the index to look up the corresponding category. From the index, we can then further create the one-hot encoding or look up a corresponding learned vector representation from an embedding table. Suppose we would like to look up integer values to some letters of the alphabet, we can do the following in Python:

```
# create a list to store all the alphabet
alphabet_lookup = [chr(ii+97) for ii in range(26)]
values = ["b", "a", "c", "d", "z"]
# using list.index to look
index = [alphabet_lookup.index(v) for v in values]
# [1, 0, 2, 3, 25]
# Look up letter based on index
retrieved_values = [alphabet_lookup[ii] for ii in index]
# the two values list should be the same
assert values == retrieved_values
```

Various libraries for machine learning implement a so-called “lookup” method (e.g. tensorflow.lookup, pandas.map), which allows the users to map from string values to integer indices via vectorization when processing a batch of categorical features.

### 6.4.1 NumPy np.unique

NumPy’s np.unique can determine the unique set of values from a given array of strings (as well as other dtypes). When specifying the argument return_inverse=True, the method can also return an integer value corresponding to the lookup index of the unique set. For instance,

```
import numpy as np
feature = ["a", "b", "c", "b", "a"]
```
