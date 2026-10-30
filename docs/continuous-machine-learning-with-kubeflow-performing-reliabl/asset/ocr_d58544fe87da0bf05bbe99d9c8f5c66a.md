```
cnts = cv2.findContours(thresh.copy(), cv2.RETR_EXTERNAL,
 cv2.CHAIN_APPROX_SIMPLE)
cnts = imutils.grab_contours(cnts)
c = max(cnts, key=cv2.contourArea)

extLeft = tuple(c[c[:, :, 0].argmin()][0])
extRight = tuple(c[c[:, :, 0].argmax()][0])
extTop = tuple(c[c[:, :, 1].argmin()][0])
extBot = tuple(c[c[:, :, 1].argmax()][0])
ADD_PIXELS = add_pixels_value
new_img = img[extTop[1]-ADD_PIXELS:extBot[1]+ADD_PIXELS,
extLeft[0]-ADD_PIXELS:extRight[0]+ADD_PIXELS].copy()
set_new.append(new_img)
return np.array(set_new)

def preprocess_imgs(set_name, img_size):
set_new = []
for img in set_name:
img =
cv2.resize(img,dsize=img_size,interpolation=cv2.INTER_CUBIC)
set_new.append(tf.keras.applications.vgg16.preprocess_input(img))
return np.array(set_new)

def image_transform(instance):
logging.info("Inside Image Transform")
originalimage = base64.b64decode(instance)
jpg_as_np = np.frombuffer(originalimage, dtype=np.uint8)
img = cv2.imdecode(jpg_as_np, flags=1)
image_expanded = np.expand_dims(img, axis=0)
crop_image = crop_imgs(set_name=image_expanded)
IMG_SIZE=(224,224)
```