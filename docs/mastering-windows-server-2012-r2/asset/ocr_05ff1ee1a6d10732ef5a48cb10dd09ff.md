Once the events are captured on the collector computer, you can manipulate and filter them just like any other events on the computer. You can also create custom views for forwarded events.

# Understanding Subscription Types

Subscriptions can be either collector initiated or source initiated. A collector-initiated subscription identifies all the computers that the collector will receive events from and normally pull events from these computers. In a computer-initiated subscription, source computers push to the collector.

# COLLECTOR-INITIATED SUBSCRIPTIONS

Collector-initiated subscriptions list all the computers that will forward events (event sources). This is the most common type of subscription used by server administrators.
Figure 30.14 shows the configuration page for a collector-initiated subscription named CollectSQLEvents.

FIGURE 30.14
Creating a collector-initiated subscription

![](bbox=[0.338, 0.409, 0.903, 0.748])

When clicking a collector-initiated subscription, you need to add the source computers by clicking the Select Computers button. If the source computers stay the same, the collector-initiated subscription is the best choice. You identify the list of computers once and you will need to reconfigure it only if you add or remove a computer/from the subscription.

Collector-initiated subscriptions also need to be configured with the credentials of an account that has Read permissions on the source logs. Since subscriptions will include events