# Goal
* 1. Access pixel values and modify them
* 2. Access image properties
* 3. Setting Region of Interest (ROI)
* 4. Splitting and Merging images
# A priori knowledge
Almost all the operations in this section is mainly related to `Numpy` rather than OpenCV. A good knowledge of Numpy is required to write better **ptimized code with OpenCV.**
# Accessing and Modifying pixel values
* Load Image
```python
import cv2
import numpy as np
img = cv2.imread('example.jpg')
```
    You can access a pixel value by its row and column coordinates. For BGR image, it returns an array of Blue, Green, Red values. For grayscale image, just corresponding intensity is returned.
```python
px = img[100,100]
print( px )
# accessing only blue pixel
blue = img[100,100,0]
print( blue )
```
    You can modify the pixel values the same way
```python
img[100,100] = [255,255,255]
print( img[100,100] )
```
# Accessing Image Properties
        Image properties include number of rows, columns and channels, type of image data, number of pixels etc.Shape of image is accessed by img.shape. It returns a tuple of number of rows, columns and channels (if image is color):
```python
print( img.shape )
for example : (342, 548, 3)
```
# Image ROI
ROI is again obtained using Numpy indexing. Here I am selecting the object and copying it to another region in the image:
```python
object = img[280:340, 330:390]
img[273:333, 100:160] = object
```
# Splitting and Merging Image Channels
        Sometimes you will need to work separately on B,G,R channels of image. Then you need to split the BGR images to single planes. Or another time, you may need to join these individual channels to BGR image. You can do it simply by:
```python
b,g,r = cv2.split(img)
img = cv2.merge((b,g,r))
```
# Making Borders for Images (Padding)
```python
import cv2
import numpy as np
from matplotlib import pyplot as plt
BLUE = [255,0,0]
img1 = cv2.imread('example.png')
replicate = cv2.copyMakeBorder(img1,10,10,10,10,cv2.BORDER_REPLICATE)
constant= cv2.copyMakeBorder(img1,10,10,10,10,cv2.BORDER_CONSTANT,value=BLUE)
plt.subplot(231),plt.imshow(img1,'gray'),plt.title('ORIGINAL')
plt.subplot(236),plt.imshow(constant,'gray'),plt.title('CONSTANT')
plt.show()
```
# Result
![]()
        
