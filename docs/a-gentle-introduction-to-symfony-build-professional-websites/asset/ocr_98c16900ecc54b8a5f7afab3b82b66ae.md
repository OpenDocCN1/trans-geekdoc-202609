# # The Delivery Strategy

One of the most useful feature of the Swift Mailer integration in symfony is the delivery strategy. The delivery strategy allows you to tell symfony how to deliver email messages and is configured via the `delivery_strategy` setting of `factories.yml`. The strategy changes the way the `send()` method behaves. Four strategies are available by default, which should suit all the common needs:

+   - realtime: Messages are sent in realtime.
+   - single_address: Messages are sent to a single address.
+   - spool: Messages are stored in a queue.
+   - none: Messages are simply ignored.

# ## The realtime Strategy

The realtime strategy is the default delivery strategy, and the easiest to setup as there is nothing special to do.

Email messages are sent via the transport configured in the `transport` section of the `factories.yml` configuration file (see the next section for more information about how to configure the mail transport).

# ## The single_address Strategy

With the `single_address` strategy, all messages are sent to a single address, configured via the `delivery_address` setting.

This strategy is really useful in the development environment to avoid sending messages to real users, but still allow the developer to check the rendered message in an email reader.

> > If you need to verify the original to, cc, and bcc recipients, they are available as values of the following headers: X-Swift-To, X-Swift-Cc, and X-Swift-Bcc respectively.

Email messages are sent via the same email transport as the one used for the realtime strategy.

# ## The spool Strategy

With the spool strategy, messages are stored in a queue.

This is the best strategy for the production environment, as web requests do not wait for the emails to be sent.

The spool class is configured with the `spool_class` setting. By default, symfony comes bundled with three of them:

+   - Swift_FileSpool: Messages are stored on the filesystem.
+   - Swift_DoctrineSpool: Messages are stored in a Doctrine model.
+   - Swift_PropelSpool: Messages are stored in a Propel model.

When the spool is instantiated, the `spool_arguments` setting is used as the constructor arguments. Here are the options available for the built-in queues classes:

+   - Swift_FileSpool:
+     - The absolute path of the queue directory (messages are stored in this directory)