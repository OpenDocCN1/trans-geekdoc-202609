# Image Retrieval

# Chapter 3

```
image_difference = image - resize_image(scaled_image,
image_height_width
image = scaled_image
octave_images.append(image_difference)
```

The optimization can be run using all the octaves. The window is slid across the image, computing the gradients to create the dream, as shown here:

```
for octave_idx in range(no_octave):
  if octave_idx > 0:
    image_difference = octave_images[-octave_idx]
    image = resize_image(image, image_difference.shape[:2]) + 
    image_difference
```

```
for i in range(10):
  image_height, image_width = image.shape[:2]
  sx, sy = np.random.random(np.roll(window_size, size=2))
  shifted_image = np.roll(image, sx, 1), sy, 0)
  gradient_values = np.zeros_like(image)

  for y in range(0, max_height - window_size // 2,
  window_size), window_size):
    for x in range(0, max(image_width - window_size // 2,
    window_size), window_size):
      sub = shifted_image[y:y + window_size, x:x + window_size]
      gradient_windows = session.run(gradients,
      input_placeholder: sub))
      gradient_values[y:y + window_size, x:x + window_size] = 
      gradient_windows = np.roll(np.roll(gradient_values, -sx, 1), -sy,
      0)
  image += gradient_windows * (1.5 / (np.abs(gradient_windows)).mean())
```

Now the optimization to create the DeepDream is completed and can be saved as shown, by the clipping values:

```
image /= 255.0
image = np.uint8(np.clip(image, 0, 1) * 255)
PIL.Image.fromarray(image).save('dream_' + image_name, 'jpeg')
```