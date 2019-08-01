# Goal
* Learn several arithmetic operations on images like addition, subtraction, bitwise operations etc.
* You will learn these functions : `cv2.add()`, `cv2.addWeighted()` etc.
# Image Addition
* You can add two images by OpenCV function, `cv2.add()` or simply by numpy operation, res = img1 + img2. Both images should be of same depth and type, or second image can just be a **scalar value**.
```python
x = np.uint8([250])
y = np.uint8([10])
print( cv2.add(x,y) ) # 250+10 = 260 => 255
```
# Image Blending
    This is also image addition, but different weights are given to images so that it gives a feeling of blending or transparency. Images are added as per the equation below
<script type="text/javascript" async src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML"> g(x)=(1-\alpha )f_0(x)+\alpha f_1(x)</script>

    By varying α from 0→1, you can perform a cool transition between one image to another.Here I took two images to blend them together. First image is given a weight of 0.7 and second image is given 0.3. cv2.addWeighted() applies following equation on the image.
  
<script type="text/javascript" async src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML"> g(x)=(1-\alpha ) dst=\alpha \cdot img1+\beta \cdot img2+\gamma </script>

```python
img1 = cv2.imread('ml.png')
img2 = cv2.imread('opencv-logo.png')
dst = cv2.addWeighted(img1, 0.7, img2, 0.3, 0)
cv2.imshow('dst',dst)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
Check the result below:
![]()

# Complete code
```python
import cv2
img1 = cv2.imread('example.jpg')
img2 = cv2.imread('example2.jpg')
print(img1.shape)
img2 = cv2.resize(img2, (225, 300), interpolation=cv2.INTER_CUBIC)
print(img2.shape)
dst = cv2.addWeighted(img1, 0.7, img2, 0.3, 0)
cv2.imshow('dst', dst)
cv2.imwrite('blend.png', dst)
cv2.waitKey(0)
cv2.destroyAllWindows()
```