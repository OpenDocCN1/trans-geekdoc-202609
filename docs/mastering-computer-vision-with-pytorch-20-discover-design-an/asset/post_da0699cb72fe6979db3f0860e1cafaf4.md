
Networks. We will use the following augmentations:

```
# Additional augmentations for CIFAR-10 training data
transform_augmented = transforms.Compose([
transforms.RandomCrop(32, padding=4),
transforms.RandomHorizontalFlip(),
transforms.ColorJitter(brightness=0.1, contrast=0.1,
saturation=0.1, hue=0.1),
transforms.ToTensor(),
transforms.Normalize((0.5, 0.5, 0.5), (0.5, 0.5, 0.5)),
])
```

```
# Use the augmented transform for the training dataset
trainset_augmented =
torchvision.datasets.CIFAR10(root='./data', train=True,
download=True, transform=transform_augmented)
trainloader_augmented =
torch.utils.data.DataLoader(trainset_augmented, batch_size=4,
shuffle=True)
```

# Rest of the training setup remains the same...

Here, we are not using augmentations like RandomErase;
the images in CIFAR-10 datasets are very small (32x32). It is
crucial to assess what augmentations will improve the
performance and which augmentations modify the images
to the extent that they lose valuable information required
for accurate training.

## Updated Code with Augmentations

```
# Updated code with new augmentations on the CIFAR-10 dataset
import torch
import torchvision
import torchvision.transforms as transforms
# Set up the transform to normalize the data
transform = transforms.Compose([
transforms.RandomCrop(32, padding=4),
transforms.RandomHorizontalFlip(),
transforms.ColorJitter(brightness=0.1, contrast=0.1,
saturation=0.1, hue=0.1),
transforms.ToTensor(),
transforms.Normalize((0.5, 0.5, 0.5), (0.5, 0.5, 0.5)),
])

# Load the CIFAR-10 dataset
trainset = torchvision.datasets.CIFAR10(root='./data',
train=True, download=True, transform=transform)
trainloader = torch.utils.data.DataLoader(trainset,
batch_size=4, shuffle=True)

testset = torchvision.datasets.CIFAR10(root='./data',
train=False, download=True, transform=transform)
testloader = torch.utils.data.DataLoader(testset,
batch_size=4, shuffle=False)

classes = ('plane', 'car', 'bird', 'cat', 'deer', 'dog',
'frog', 'horse', 'ship', 'truck')

# Define the neural network
import torch.nn as nn
import torch.nn.functional as F

class SimpleCNN(nn.Module):
def __init__(self):
super(SimpleCNN, self).__init__()
self.conv1 = nn.Conv2d(3, 6, 5)
self.pool = nn.MaxPool2d(2, 2)
self.conv2 = nn.Conv2d(6, 16, 5)
self.fc1 = nn.Linear(16 * 5 * 5, 120)
self.fc2 = nn.Linear(120, 84)
self.fc3 = nn.Linear(84, 10)

def forward(self, x):
x = self.pool(F.relu(self.conv1(x)))
x = self.pool(F.relu(self.conv2(x)))
x = x.view(-1, 16 * 5 * 5)
x = F.relu(self.fc1(x))
x = F.relu(self.fc2(x))
x = self.fc3(x)
return x

net = SimpleCNN()

# Compile the model with torch.compile for PyTorch 2.0
compiled_net = torch.compile(net)

# Set up the loss function and optimizer
import torch.optim as optim

criterion = nn.CrossEntropyLoss()
optimizer = optim.SGD(compiled_net.parameters(), lr=0.001,
momentum=0.9)

# Train the network
for epoch in range(5):  # Loop over the dataset multiple times
    running_loss = 0.0
    for i, data in enumerate(trainloader, 0):
        inputs, labels = data
        optimizer.zero_grad()
        outputs = compiled_net(inputs)
        loss = criterion(outputs, labels)
        loss.backward()
        optimizer.step()
        running_loss += loss.item()
        if i % 2000 == 1999:  # Print every 2000 mini-batches
            print('[%d, %5d] loss: %.3f' %
                (epoch + 1, i + 1, running_loss / 2000))
            running_loss = 0.0

print('Finished Training')

# Test the network on the test data
correct = 0
total = 0
with torch.no_grad():
    for data in testloader:
        images, labels = data
        outputs = compiled_net(images)
        _, predicted = torch.max(outputs.data, 1)
        total += labels.size(0)
        correct += (predicted == labels).sum().item()
print('Accuracy of the network on the 10000 test images: %d %%' % (100 * correct / total))
```

![](img/6d00092ab1eb61588b90a1b1f5390d1c_200_0.png)

Figure 6.14: Accuracy after training our SimpleCNN classifier on CIFAR-10 dataset with augmentations

We got an improvement of 6% from our previous version. Although the images in CIFAR-10 dataset are smaller for impact with data augmentations, in the next chapter we will see cases where it is much more impactful and also look at some limitations and risks.

## Best Practices for Data Augmentation and Preprocessing

Data augmentation is a powerful technique for improving the robustness and performance of machine learning models, particularly in the domain of computer vision. It involves generating new training samples from the existing ones by applying random jitters and perturbations, helping the model generalize better from limited training data. However, it’s essential to know when and how to use augmentation effectively.

### Scenarios and Use Cases

The following is the list of use cases and scenarios:

- **Insufficient Data:** When the dataset is too small, augmentations can artificially expand the diversity of the training set, helping to prevent overfitting and allowing the model to learn more general features.

- **Imbalanced Classes:** In scenarios where some classes are underrepresented, augmentation can help to balance the dataset by generating more examples of the minority class.

- **Model Generalization:** If a model performs well on the training data but poorly on the validation or test data, augmentation can introduce more variability, encouraging the model to learn more robust features.

- **Real-world Variability:** For tasks where the deployment environment will present data in various conditions (for example, different lighting or weather conditions in autonomous vehicle navigation), augmentation can simulate these conditions during training.

- **Domain-Specific Augmentations:** Certain tasks may benefit from custom augmentations that are specific to the domain. For instance, medical image analysis may use augmentations that mimic common artifacts found in medical scans.

### Incorporation Strategies

The incorporation strategies are listed as follows:

- **Incremental Complexity:** Start with simple augmentations, such as flips and rotations, and progressively introduce more complex ones based on the model's performance.

- **Pipeline Diversity:** Implement a diverse set of augmentations to cover a wide range of variations. However, ensure these augmentations are relevant to the problem at hand.

- **Consistency with Test Conditions:** Augmentations should reflect the types of variation expected during testing. Irrelevant augmentations might lead the model to learn features that are not useful.

- **Resource Constraints:** Consider the computational cost. More complex augmentations require additional processing power and time, which might not be justifiable in all scenarios.

### Limitations and Risks

While data augmentation can significantly enhance model training, it's not without limitations and potential pitfalls. The following are the limitations and risks associated with data augmentation:

- **Risk of Misleading the Model:** If augmentations don't accurately reflect the real-world scenarios or if they're applied too aggressively, they can introduce noise and misleading information, which can confuse the model and degrade the performance.

- **Quality Degradation:** Excessive augmentation can degrade the quality of the data. For instance, too much zooming, cropping, or warping might result in the loss of critical features necessary for the model to make accurate predictions.

- **Computational Overhead:** Augmentations increase the computational burden. Each new augmentation adds to the time required for training, which can be significant for large-scale or real-time systems.

- **Class Distortion:** Certain augmentations might distort class-specific features. For example, while flipping images might be beneficial for general object recognition, it can harm performance in tasks like reading text, where direction matters.

- **Bias Introduction:** Augmentations can inadvertently introduce or reinforce bias in the dataset. If not carefully
