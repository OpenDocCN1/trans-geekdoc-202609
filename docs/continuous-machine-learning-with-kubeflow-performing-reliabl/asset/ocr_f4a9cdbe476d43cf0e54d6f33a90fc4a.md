feature_spec

```
{'adr': FixedLenFeature(shape=(), dtype=tf.float32, default_value=None),
'adults': FixedLenFeature(shape=(), dtype=tf.int64, default_value=None),
'agent': FixedLenFeature(shape=(), dtype=tf.float32, default_value=None),
'arrival_date_day_of_month': FixedLenFeature(shape=(), dtype=tf.int64, default_value=None),
'arrival_date_month': FixedLenFeature(shape=(), dtype=tf.string, default_value=None),
'arrival_date_week_number': FixedLenFeature(shape=(), dtype=tf.int64, default_value=None),
'babies': FixedLenFeature(shape=(), dtype=tf.int64, default_value=None),
'children': FixedLenFeature(shape=(), dtype=tf.float32, default_value=None),
'company': FixedLenFeature(shape=(), dtype=tf.float32, default_value=None),
'customer_type': FixedLenFeature(shape=(), dtype=tf.string, default_value=None),
'deposit_type': FixedLenFeature(shape=(), dtype=tf.string, default_value=None),
'distribution_channel': FixedLenFeature(shape=(), dtype=tf.string, default_value=None),
'hotel': FixedLenFeature(shape=(), dtype=tf.string, default_value=None),
'is_canceled': FixedLenFeature(shape=(), dtype=tf.int64, default_value=None),
'is_repeated_guest': FixedLenFeature(shape=(), dtype=tf.int64, default_value=None),
'lead_time': FixedLenFeature(shape=(), dtype=tf.int64, default_value=None),
'market_segment': FixedLenFeature(shape=(), dtype=tf.string, default_value=None),
'meal': FixedLenFeature(shape=(), dtype=tf.string, default_value=None),
'previous_bookings_not_canceled': FixedLenFeature(shape=(), dtype=tf.int64, default_value=None),
'previous_cancellations': FixedLenFeature(shape=(), dtype=tf.int64, default_value=None),
'required_car_parking_spaces': FixedLenFeature(shape=(), dtype=tf.int64, default_value=None),
'reserved_room_type': FixedLenFeature(shape=(), dtype=tf.string, default_value=None),
'stays_in_week_nights': FixedLenFeature(shape=(), dtype=tf.int64, default_value=None),
'stays_in_weekend_nights': FixedLenFeature(shape=(), dtype=tf.int64, default_value=None),
'total_of_special_requests': FixedLenFeature(shape=(), dtype=tf.int64, default_value=None)}
```

Figure 5.16: Feature Columns Tensors and datatypes

```
train_inpf = functools.partial(tfexamples_input_fn, examples,
feature_spec, label_column)
```