# Modification: Query key value

![](bbox=[0.196, 0.065, 0.804, 0.631])

+   - Encoder outputs an explicit "key" and "value" at each input time

+   - Key is used to evaluate the importance of the input at that time, for a given output

+   - Decoder outputs an explicit "query" at each output time

+   - Query is used to evaluate which inputs to pay attention to

+   - The weight is a function of key and query

+   - The actual context is a weighted sum of value