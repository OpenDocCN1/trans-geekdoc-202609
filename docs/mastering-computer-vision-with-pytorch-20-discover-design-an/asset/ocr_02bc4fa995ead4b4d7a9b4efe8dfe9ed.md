# # Object Detection with Faster R-CNN

```
import torch
import torchvision.transforms as transforms
from PIL import Image, ImageDraw
import torchvision.models.detection as detection_models
# Load the pre-trained Faster R-CNN model
model_detection =
detection_models.fasterrcnn_resnet50_fpn(pretrained=True)
model_detection.eval()
# Load and preprocess the image
image = Image.open('test.png')
transform_detection =
transforms.Compose([transforms.ToTensor()])
input_tensor = transform_detection(image).unsqueeze(0)
# Inference
with torch.no_grad():
    predictions = model_detection(input_tensor)
# Draw the bounding boxes and labels on the image
draw = ImageDraw.Draw(image)
for element in range(len(predictions[0]['boxes'])):
    boxes = predictions[0]['boxes'][element].cpu().numpy()
    score = predictions[0]['scores'][element].cpu().numpy()
    label = predictions[0]['labels'][element].cpu().numpy()
# Draw the box with a threshold for scores to filter weak
detections
if score > 0.5:
    draw.rectangle([(boxes[0], boxes[1]), (boxes[2], boxes[3])],
    outline="red", width=3)
    draw.text((boxes[0], boxes[1]), f'Label: {label}',
    fill="red")
# Save the image with detections
image.save('detection_output.png')
print('Detection output saved as detection_output.png')
```