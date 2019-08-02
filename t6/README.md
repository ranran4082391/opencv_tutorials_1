# Goal
* Learn to apply different geometric transformation to images like `translation`, `rotation`, `affine transformation` etc.
* You will see these functions: `cv.getPerspectiveTransform`.
# Transformations
OpenCV provides two transformation functions, `cv.warpAffine` and `cv.warpPerspective`, with which you can have all kinds of transformations. **cv.warpAffine takes a 2x3 transformation matrix while cv.warpPerspective takes a 3x3 transformation matrix as input**.
## Scaling
Scaling is just resizing of the image. OpenCV comes with a function `cv.resize()` for this purpose. The size of the image can be specified manually, or you can specify the scaling factor. Different interpolation methods are used. Preferable interpolation methods are ***cv.INTER_AREA*** for shrinking and ***cv.INTER_CUBIC (slow) & cv.INTER_LINEAR for zooming***. By default, interpolation method used is cv.INTER_LINEAR for all resizing purposes. You can resize an input image either of following methods:
```python
import numpy as np
import cv2 as cv
img = cv.imread('example.jpg')
res = cv.resize(img,None,fx=2, fy=2, interpolation = cv.INTER_CUBIC)
#OR
height, width = img.shape[:2]
res = cv.resize(img,(2*width, 2*height), interpolation = cv.INTER_CUBIC)
```
## Translation (Translation is the shifting of object's location)
```python
import numpy as np
import cv2 as cv
img = cv.imread('example.jpg',0)
rows,cols = img.shape
M = np.float32([[1,0,100],[0,1,50]])
dst = cv.warpAffine(img,M,(cols,rows))
cv.imshow('img',dst)
cv.waitKey(0)
cv.destroyAllWindows()
```
![](https://github.com/ranran4082391/opencv_tutorials_1/blob/master/t6/warpAffine.png)
## Rotation
```python
img = cv.imread('example.jpg',0)
rows,cols = img.shape
# cols-1 and rows-1 are the coordinate limits.
M = cv.getRotationMatrix2D(((cols-1)/2.0,(rows-1)/2.0),90,1)
dst = cv.warpAffine(img,M,(cols,rows))
```
![](https://github.com/ranran4082391/opencv_tutorials_1/blob/master/t6/Rotation.png)
## Affine Transformation
## Perspective Transformation
