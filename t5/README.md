# Goal
In image processing, since you are dealing with large number of operations per second, it is mandatory that your code is not only providing the correct solution, but also in the fastest manner. So in this chapter, you will learn
*  To measure the performance of your code.
*  Some tips to improve the performance of your code.
*  You will see these functions : `cv.getTickCount`, `cv.getTickFrequency` etc.
Apart from OpenCV, Python also provides a module **time** which is helpful in measuring the time of execution. Another module **profile** helps to get detailed report on the code, like how much time each function in the code took, how many times the function was called etc. But, if you are using IPython, all these features are integrated in an user-friendly manner. We will see some important ones, and for more details, check links in Additional Resources section.
# Measuring Performance with OpenCV
***cv.getTickCount*** function returns the number of clock-cycles after a reference event (like the moment machine was switched ON) to the moment this function is called. So if you call it before and after the function execution, you get number of clock-cycles used to execute a function.
***cv.getTickFrequency*** function returns the frequency of clock-cycles, or the number of clock-cycles per second. So to find the time of execution in seconds, you can do following:
```python
e1 = cv.getTickCount()
# your code execution
e2 = cv.getTickCount()
time = (e2 - e1)/ cv.getTickFrequency()
print(time)
```
# Default Optimization in OpenCV
Many of the OpenCV functions are optimized using `SSE2`, `AVX` etc. It contains unoptimized code also. So if our system support these features, we should exploit them (almost all modern day processors support them).It is enabled by default while compiling. So OpenCV runs the optimized code if it is enabled, else it runs the unoptimized code. You can use `cv.useOptimized()` to check if it is enabled/disabled and `cv.setUseOptimized()` to enable/disable it. Let's see a simple example.
```python
# check if optimization is enabled
In [5]: cv.useOptimized()
Out[5]: True
In [6]: %timeit res = cv.medianBlur(img,49)
10 loops, best of 3: 34.9 ms per loop
# Disable it
In [7]: cv.setUseOptimized(False)
In [8]: cv.useOptimized()
Out[8]: False
In [9]: %timeit res = cv.medianBlur(img,49)
10 loops, best of 3: 64.1 ms per loop
```
# Performance Optimization Techniques
There are several techniques and coding methods to exploit maximum performance of `Python and Numpy`. Only relevant ones are noted here and links are given to important sources. The main thing to be noted here is that, first try to implement the algorithm in a simple manner. Once it is working, profile it, find the bottlenecks and optimize them.

        1. Avoid using loops in Python as far as possible, especially double/triple loops etc. They are inherently slow.
        2. Vectorize the algorithm/code to the maximum possible extent because Numpy and OpenCV are optimized for vector operations.
        3. Exploit the cache coherence.
        4. Never make copies of array unless it is needed. Try to use views instead. Array copying is a costly operation.
# Additional Resources

[Python Optimization Techniques](https://wiki.python.org/moin/PythonSpeed/PerformanceTips)

