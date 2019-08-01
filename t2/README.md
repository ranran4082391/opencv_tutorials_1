# Goal
* Learn to draw different geometric shapes with OpenCV
* You will learn these functions : cv2.line(), cv2.circle() , cv2.rectangle(), cv2.ellipse(), cv2.putText() etc.
# Code
 * img: The image where you want to draw the shapes
 * color: Color of the shape. for BGR, pass it as a tuple, eg: (255,0,0) for blue. For grayscale, just pass the scalar value.
 * thickness: Thickness of the line or circle etc. If **-1** is passed for closed figures like circles, it will fill the shape. default thickness = 1
 * lineType: Type of line, whether 8-connected, anti-aliased line etc. By default, it is ***8-connected***. `cv2.LINE_AA` gives anti-aliased line which looks great for curves.
 # Drawing Line
 To draw a line, you need to pass starting and ending coordinates of line. We will create a black image and draw a blue line on it from `top-left to bottom-right` corners.
 
 ```python
img = cv2.imread('example.jpg', cv2.IMREAD_COLOR)
# Draw a diagonal blue line with thickness of 5 px
cv2.line(img, (0, 0), (511, 511), (255, 0, 0), 5)
cv2.imshow('image', img)
cv2.waitKey(0)
cv2.destroyAllWindows()
 ```
 # Adding Text to Images:
 To put texts in images, you need specify following things.
 
 * We will write OpenCV on our image in white color.
 ```python
font = cv2.FONT_HERSHEY_SIMPLEX
cv2.putText(img,'OpenCV',(10,500), font, 4,(255,255,255),2,cv2.LINE_AA)
 ```
 # Result
 ![](www.baidu.com)
