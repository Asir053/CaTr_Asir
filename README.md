# CaTr_Asir
At first, I cloned the code from https://github.com/saahiluppal/catr

### Dataset Preparation:
The captions and images of the BanglaLekhaImageCaptions (https://data.mendeley.com/datasets/rxxch9vw59/2) dataset are separately split into training and validation without any shuffle or random state (seed) with a 80-20 ratio. The training set consists of 7323 images and the validation set consists of 1831 images.

### Preprocessing:
For preprocessing using keras I imported the preprocessing of the 	preprocess_input library of the Xception pretrained model 
```from tensorflow.keras.applications.xception import preprocess_input
``` 
because this preprocessing function has yielded decent results for RGB images in recent works.

*** Changes in the code:
In the 63 no. line of the file (```catr/datasets/coco.py```), it is modified from ```
self.annot = [(self._process(val['image_id']), val['caption'])



for val in ann['annotations']]``` 
to 
```
self.annot = [(self._process(val['filename']), val['caption'])



for val in ann]
``` 
to keep it consistent with our json data format (keys).

Line no. 75 of the same file, 
(```
val = str(image_id).zfill(12)



return val + '.jpg'```) 
is changed to ```val = image_id

return val``` 

to keep it consistent with the image names of our dataset.

### Training:
For training we follow the instructions given in README.md of (https://github.com/saahiluppal/catr) 
After 21 epochs the training and validation loss are 4.56*10^-9 and 2.79*10^-9 respectively.

