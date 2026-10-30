```
@click.option('--validation-target',
default="/mnt/validationtarget.data")
@click.option('--label', default="/mnt/labels.data")
@click.option('--image-size', default=224)

deftraining_data_processing(root,train_file,label,test_file,validation_file,
image_size,train_target,test_target,validation_target):
TRAIN_DIR = root + 'TRAIN/'
TEST_DIR = root + 'TEST/'
VAL_DIR = root + 'VAL/'
IMG_SIZE = (image_size,image_size)
X_train, y_train, labels = load_data_array(TRAIN_DIR, IMG_SIZE)
X_test, y_test, _ = load_data_array(TEST_DIR, IMG_SIZE)
X_val, y_val, _ = load_data_array(VAL_DIR, IMG_SIZE)

X_train_crop = crop_imgs(set_name=X_train)
X_val_crop = crop_imgs(set_name=X_val)
X_test_crop = crop_imgs(set_name=X_test)
directory=["TRAIN_CROP", "TEST_CROP", "VAL_CROP",
"TRAIN_CROP/YES", "TRAIN_CROP/NO", "TEST_CROP/YES",
"TEST_CROP/NO", "VAL_CROP/YES", "VAL_CROP/NO"]
for i in directory:
path = os.path.join(root, i)
try:
os.mkdir(path)
except OSError as error:
print(error)
save_new_images(X_train_crop, y_train,
folder_name='/mnt/TRAIN_CROP/')
```