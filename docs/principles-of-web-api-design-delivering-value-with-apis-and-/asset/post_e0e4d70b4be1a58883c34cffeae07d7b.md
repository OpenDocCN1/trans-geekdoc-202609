
```json
{
  "customerId": "330001003",
  "newBillingAddress": {
    "addressLine1": "...",
    "addressLine2": "...",
    "addressCity": "...",
    "addressState": "...",
    "addressRegionProvince": "...",
    "addressPostalCode": "..."
  }
}
```

An additional replyTo field could be provided with the URL for callback, or other subscribers listen for a customerAddress.updated event to react to the change, perhaps updating the billing address in a third-party system.

# Event Notifications

Event notifications, sometimes referred to as thin events, notify subscribers that a state change or business event has occurred. They seek to provide only the necessary information for the subscriber to determine if the event is of interest.

The event subscriber is responsible for fetching the latest representation of the details via an API to avoid using stale data. Providing hyperlinks as part of a thin event helps to integrate API operations for retrieving the latest resource representation(s) with async APIs such as events. This is shown in the following example event payload:

```json
{
  "eventType": "customerAddress.updated",
  "eventId": "123e4567",
  "updatedDate": "2020-01-14T03:56:45Z",
  "customerId": "330001003",
  "_links": [
    { "rel": "self", "href": "/events/123e4567" },
    { "rel": "customer", "href": "/customers/330001003" }
  ]
}
```

Thin events are used for events related to resources that change frequently, forcing the event subscriber to retrieve the latest resource representation to avoid working with stale data. While not necessary, thin events may also include details about the specific properties that changed when an update occurred to help consumers determine the event is of interest.

# Event-Carried State Transfer Events

Event-carried state transfer events contain all available information at the time of the event. This avoids the need to contact an API for the complete resource representation, though additional APIs may be used to augment the data required by the subscriber to perform any processing.

There are a few reasons why event-carried state transfer may be preferred over thin events:

- Subscribers watch a snapshot of the resource associated with the event rather than the few details and associated multimedia links offered by thin events.
- Data state changes using messaging streaming to support replaying message history, requiring a complete point-in-time snapshot of a resource.
- Messaging via async API is used for interservice communication, requiring publication of a full resource representation to avoid increased API traffic and tighter coupling between services.

It is common for this style of message design to mimic API representation structures whenever possible. Deviation is common when the event must offer the old and new values of any modified properties on an update event.

Finally, use nested rather flat structures to group related properties for medium-to-large payloads. This helps drive evolability, as property names are scoped to the parent property, avoiding property name collisions or long property names to clarify relationships. The following is a demonstration of a flat structure to event-carried state transfer message styles.

```json
{
  "eventType": "customerAddress.updated",
  "eventId": "123e4567",
  "updatedAt": "2020-01-14T03:56:45Z",
  "customerId": "330001003",
  "previousBillingAddressLine1": "...",
  "previousBillingAddressLine2": "...",
  "previousBillingAddressCity": "...",
  "previousBillingAddressState": "...",
  "previousBillingAddressRegionProvince": "...",
  "previousBillingAddressPostalCode": "...",
  "newBillingAddressLine1": "...",
  "newBillingAddressLine2": "...",
  "newBillingAddressCity": "...",
  "newBillingAddressState": "...",
  "newBillingAddressRegionProvince": "...",
  "newBillingAddressPostalCode": "..."
}
```

A structured approach is demonstrated in the following example:

```json
{
  "eventType": "customerAddress.updated",
  "eventId": "123e4567",
  "updatedAt": "2020-01-14T03:56:45Z",
  "customerId": "330001003",
  "previousBillingAddress": {
    "addressLine1": "...",
    "addressLine2": "...",
    "addressCity": "...",
    "addressState": "...",
    "addressRegionProvince": "...",
    "addressPostalCode": "..."
  },
  "newBillingAddress": {
    "addressLine1": "...",
    "addressLine2": "...",
    "addressCity": "...",
    "addressState": "...",
    "addressRegionProvince": "...",
    "addressPostalCode": "..."
  }
}
```

When applying structured composition to the event-carried state style, the consumer is able to reuse value objects to contain the details of each nested object and easily detect differences in fields or visualize the changes within a user interface at a later date. Without the pattern, a large value object plus additional coding effort are required to associate the flattened fields for performing things such as detecting a difference between the previous and new address.

# Event Batching

While most async APIs are designed to notify a subscriber when each message is available, some designs may benefit from grouping events into a batch. Event batching requires that subscribers handle multiple messages. A simple example is to wrap the notification with an array:

```json
{
  "eventType": "customerAddress.updated",
  "eventId": "123e4567",
  "updatedAt": "2020-01-14T03:56:45Z",
  "customerId": "330001003",
  "_links": [
    { "rel": "self", "href": "/events/123e4567" },
    { "rel": "customer", "href": "/customers/330001003" }
  ]
}
```

Another design option is to provide an envelope with additional metadata about the batch:

```json
{
  "meta": {
    "eventType": "customerAddress.updated",
    "eventId": "123e4567",
    "updatedAt": "2020-01-14T03:56:45Z",
    "customerId": "330001003",
    "_links": [
      { "rel": "self", "href": "/events/123e4567" },
      { "rel": "customer", "href": "/customers/330001003" }
    ]
  },
  "events": [
    {
      "eventType": "customerAddress.updated",
      ...
    }
  ]
}
```
