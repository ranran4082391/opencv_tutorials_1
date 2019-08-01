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
