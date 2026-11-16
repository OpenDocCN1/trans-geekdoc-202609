In the main part of the script, we begin by setting the Seaborn plot style and creating the Figure object in which the barplot will be displayed:

lick here to view code image

```
55 if __name__ == '__main__':
56     sns.set_style('whitegrid') # white  background with gray grid lines
57     figure = plt.figure('Stock Prices') # Figure for animation
58
```

# # Configuring the FuncAnimation and Displaying the Window

Next, we set up the FuncAnimation that calls function update, then call Matplotlib's show method to display the Figure. Normally, this method blocks the script from continuing until you close the Figure. Here, we pass the block=False keyword argument to allow the script to continue so we can configure the PubNub client and subscribe to a channel.

lick here to view code image

```
59 # configure and start animation that calls function  update
60 stock_animation = animation.FuncAnimation(
61     figure, update, repeat=False, interval=33)
62 plt.show(block=False) # display window
63
```

# # Configuring the PubNub Client

Next, we configure the PubNub subscription key, which the PubNub client uses in combination with the channel name to subscribe to the channel. The key is specified as an attribute of the PNConfiguration object (module pubnub.pnconfiguration), which line 69 passes to the new PubNub client object (module pubnub.pubnub). Lines 70–72 create the SensorSubscriberCallback object and pass it to the PubNub client's add_listener method to register it to receive messages from the channel. We use a command-line argument to specify the total number of messages to process.

lick here to view code image

```
64 # set up pubnub-market-orders sensor stream key
65 config = PNConfiguration()
66 config.subscribe_key = 'sub-c-4377ab04-f100-11e3-bffd-02ee2ddab7fe'
67
68 # create PubNub client and register a SubscribeCallback
69 pubnub = PubNub(config)
70 pubnub.add_listener(
71     SensorSubscriberCallback(df=companies_df,
72     limit=int(sys.argv[1] if len(sys.argv) > 1 else 1000))
73
```

# # Subscribing to the Channel

The following statement completes the subscription process, indicating that we wish to receive messages from the channel named 'pubnub-market-orders'. The execute method starts the stream.