+   • Weight distributions and gradients (if histogram_freq=1 is enabled).
• Execution timelines and learning rate trends.

# Running TensorBoard

Launch TensorBoard in your terminal:
tensorboard --logdir=logs/fit
Then, open your browser and navigate to:
http://localhost:6006
To access the TensorBoard dashboard
If the link shows an error, it usually means one of the following:

+   • TensorBoard is not running or has failed to start.
• The log directory path is incorrect or empty.
• Another process is already using port 6006.
• Your firewall or browser is blocking local ports.

If needed, you can try:
tensorboard --logdir=logs/fit --port=6007
And then open http://localhost:6007.

# Importance of training visualizations

Visualizations help answer key questions during training:

+   • Is the model converging?
• Is validation loss plateauing or diverging?
• Are the layers learning effectively?

These insights help guide decisions about early stopping, regularization, or learning rate adjustments.

AI tip—Use ChatGPT to:

+   • Add TensorBoard logging to a custom training loop in PyTorch.