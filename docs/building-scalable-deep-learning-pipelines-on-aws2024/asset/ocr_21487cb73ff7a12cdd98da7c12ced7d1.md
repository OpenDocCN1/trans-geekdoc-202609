The first line, logging.basicConfig(level=logging.INFO), initializes the logging system and configures it to log messages with a level of INFO or higher. This means that only messages with a severity level of INFO, WARNING, ERROR, or CRITICAL will be logged, while messages with a DEBUG level will be ignored. The basicConfig() function allows us to configure the root logger, which is the main logger used by the Python logging module.

The second line, logger = logging.getLogger(__name__), creates a logger object named logger. The getLogger() function is used to obtain a logger instance, and __name__ is a special variable in Python that represents the name of the current module. By using __name__, the logger will have the same name as the current module in which it is defined. This helps in identifying the source of log messages, as the logger name will correspond to the module name.

# Step 3: Custom Callback

The code below defines a custom Keras callback named CustomCallback in Python:

```
[In] : class CustomCallback(Callback):
       """Custom Keras callback for printing epoch
       information."""
       def on_epoch_end(self, epoch, logs=None):
           """Prints epoch information every 10 epochs."""
           if (epoch + 1) % 10 == 0:
               logger.info(
                   f"Epoch [{(epoch + 1)}/{self.
                   params['epochs']}], "
                   f"Loss: {logs['loss']:.4f}")
```