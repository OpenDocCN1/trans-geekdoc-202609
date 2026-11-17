```
model_path = 'resnet50_cifar10.pth'
model = models.resnet50(pretrained=False)
num_ftrs = model.fc.in_features
model.fc = torch.nn.Linear(num_ftrs, 10) # CIFAR-10 has 10 classes
model = model.to(device)
model.load_state_dict(torch.load(model_path))
model.eval()

# CIFAR-10 validation dataset
transform = transforms.Compose([
    transforms.Resize(256),
    transforms.CenterCrop(224),
    transforms.ToTensor(),
    transforms.Normalize(mean=[0.485, 0.456, 0.406], std=[0.229, 0.224, 0.225]),
])

validation_set = torchvision.datasets.CIFAR10(root='./data',
train=False, download=True, transform=transform)
validation_loader = DataLoader(validation_set, batch_size=64,
shuffle=False)

# Function to get predictions and targets
def get_predictions_and_targets(loader, model):
    all_preds = []
    all_targets = []
    with torch.no_grad():
        for images, targets in loader:
            images, targets = images.to(device), targets.to(device)
            outputs = model(images)
            _, preds = torch.max(outputs, 1)
            all_preds.extend(preds.cpu().numpy())
            all_targets.extend(targets.cpu().numpy())
    return all_preds, all_targets

# Get predictions and targets from the model
predictions, targets =
get_predictions_and_targets(validation_loader, model)
```