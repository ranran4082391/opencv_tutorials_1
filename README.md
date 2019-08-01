# opencv_tutorials_1
Interpretation and Implementation of Opencv3
--------------------------------------------
#GOALS
*Here, you will learn how to read an `image`, how to `display` it and how to `save` it back
*you will learn these functions : `cv2.imread(), cv2.imshow() , cv2.imwrite()`
*Optionally, you will learn how to display images with Matplotlib

#Using OpenCV
##Read an image

Use the function `cv2.imread()` to read an image. The image should be in the working directory or a full path of image should be given.

Second argument is a flag which specifies the way image should be read.

*cv2.IMREAD_COLOR : Loads a color image. Any transparency of image will be neglected. It is the default flag.
*cv2.IMREAD_GRAYSCALE : Loads image in grayscale mode
*cv2.IMREAD_UNCHANGED : Loads image as such including alpha channel

##for example
```python
import cv2

img = cv2.imread('example.jpg', cv2.IMREAD_COLOR)
```

##Display an image
Use the function `cv2.imshow()` to display an image in a window. The window automatically fits to the image size.

First argument is a window name which is a string. second argument is our image. You can create as many windows as you wish, but with different window names.
```python
import cv2

img = cv2.imread('example.jpg', cv2.IMREAD_COLOR)
cv2.imshow('image',img)
cv2.waitKey(0)
cv2.destroyAllWindows()
```
![](https://github.com/guodongxiaren/ImageCache/raw/master/Logo/foryou.gif)  

`cv2.waitKey()` is a keyboard binding function. Its argument is the time in milliseconds. The function waits for specified milliseconds for any keyboard event. If you press any key in that time, the program continues. If 0 is passed, it waits indefinitely for a key stroke. It can also be set to detect specific key strokes like, if key a is pressed etc which we will discuss below.

##Write an image
Use the function `cv2.imwrite()` to save an image.

First argument is the file name, second argument is the image you want to save.
```python
cv2.imwrite('example.png',img)
```




