## Project: Build a Traffic Sign Recognition Program
[![Udacity - Self-Driving Car NanoDegree](https://s3.amazonaws.com/udacity-sdc/github/shield-carnd.svg)](http://www.udacity.com/drive)

### Dataset Exploration
#### Dataset Summary
 - Traffic sign image size: 32x32x3
 - Number of classes: 43
 
|              | Training | Validation |  Test    |
| ------------ |:--------:|:----------:|:--------:|
| dataset size |   34799  |     4410   |   12630  |
The distribution of class labels indicates that the training sample is not balanced, labels like 'End of No Passing', 'Dangerous curve to the left' etc. are less than 250.
<img src="./pictures/numClasses.png" alt="alt text" width="400" height="300">
The following plot shows 43 traffic signs, the contract and exposure of some images are very low.
<img src="./pictures/traffic_signs_original.png" alt="alt text" width="750" height="950">

#### Image Processing and Augmentation
- Convert RGB image to gray scale: Y = 0.299 R + 0.587 G + 0.114 B
- Apply local contrast enhancement using `skimage.exposure.equalize_adapthist`
- Normalize the image by image / 255

<img src="./pictures/preprocessed_sign.png" alt="alt text" width="500" height="250">
ImageDataGenerator of keras is used to generate batches of augmented tensor image in training. The images are 

 - randomly rotated with +/- 20deg range
 - randomly shifted in the x and y direction with +/- 6 pixels (20% of the image size)
 - randomly zoomed with a factor ranging from 0.8 to 1.2
 - randomly sheared within +/- 0.5 rad
<img src="./pictures/augumented_images.png" alt="alt text" width="500" height="250">
