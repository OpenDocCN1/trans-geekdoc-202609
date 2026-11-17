```
train_loader = torch.utils.data.DataLoader(train_dataset,
batch_size=64, shuffle=True)
test_loader = torch.utils.data.DataLoader(test_dataset,
batch_size=64, shuffle=False)
# Set number of epochs to train
number_of_epochs = 5
# Loop for each epoch
for epoch in range(number_of_epochs):
    running_loss = 0.0
    for i, data in enumerate(train_loader, 0):
        inputs, labels = data[0].to(device), data[1].to(device)
        optimizer.zero_grad()
        outputs = vgg16_pretrained(inputs)
        loss = criterion(outputs, labels)
        loss.backward()
        optimizer.step()
        running_loss += loss.item()
    print(f'Epoch {epoch + 1}: Loss: {running_loss /
len(train_loader)}')
# Save the model's state dictionary
torch.save(vgg16_pretrained.state_dict(),
'vgg16_cifar100.pth')
```