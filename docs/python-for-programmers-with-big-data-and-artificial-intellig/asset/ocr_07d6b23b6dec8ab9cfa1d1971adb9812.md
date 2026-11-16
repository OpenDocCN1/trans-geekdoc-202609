# # Message Format

The simulated Market Orders stream returns JSON objects containing five key–value pairs with the keys 'bid_price', 'order_quantity', 'symbol', 'timestamp' and 'trade_type'. For this example, we'll use only the 'bid_price' and 'symbol'. The PubNub client returns the JSON data to you as a Python dictionary.

# # Importing the Libraries

Lines 3–13 import the libraries used in this example. We discuss the PubNub types imported in lines 10–13 as we encounter them below.

lick here to view code image

```
# stocklistener.py
"""Visualizing a PubNub live stream."""
from matplotlib import animation
import matplotlib.pyplot as plt
import pandas as pd
import random
import seaborn as sns
import sys

from pubnub.callbacks import SubscribeCallback
from pubnub.enums import PNStatusCategory
from pubnub.pnconfiguration import PNConfiguration
from pubnub.pubnub import PubNub
```

# # List and DataFrame Used for Storing Company Names and Prices

The list companies contains the names of the companies reported in the Market Orders stream, and the pandas DataFrame companies_df is where we'll store each company's last price. We'll use this DataFrame with Seaborn to display a bar chart.

lick here to view code image

```
companies = ['Apple', 'Bespin Gas', 'Elerium', 'Google', 'Linen Cloth'
# DataFrame to store last stock prices
companies_df = pd.DataFrame(
{'company': companies, 'price' : [0, 0, 0, 0, 0]})
```

# # Class SensorSubscriberCallback

When you subscribe to a PubNub stream, you must add a listener that receives status notifications and messages from the channel. This is similar to the Tweepy listeners you've defined previously. To create your listener, you must define a subclass of SubscribeCallback (module pubnub.callbacks), which we discuss after the code:

lick here to view code image

```
class SensorSubscriberCallback(SubscribeCallback):
"""SensorSubscriberCallback receives messages from PubNub."""
def __init__(self, df, limit=1000):
```