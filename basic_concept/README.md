# Introduction to Computer Vision

## Image Representation and Classification

### General computer vision processing pipeline

![](https://github.com/runhaozhou/Car_Bicycle_SVM_Classifier/blob/master/basic_concept/Images/GeneralPipeline.JPG)

Images as numerical data, every pixel in an image is a numerical value. Therefore, the grayscale range is 0-255.

### Color Thresholds

Selecting an area of interest using a color threshold

### Color Spaces

RGB: Red, Green, Blue

HSV: Hue, Saturation, Value

HLS: Hue, Lightness, Saturation

Using Hue to build an image mask to choose the object under different light

### Dataset

Training dataset:  70%-80%

Test dataset: 20%-30%

## Convolutional Filters and Edge Detection

### Frequency in Images

frequency in images is a rate of change, images change in space, and a high frequency image is one where the intensity changes a lot. And the level of brightness changes quickly from one pixel to the next. A low frequency image may be one that is relatively uniform in brightness or changes very slowly.

**High-frequency components also correspond to the edges of objects in images**

### Fourier Transform

The output of an FT represents the image in the frequency domain, while the input image is the spatial domain (x, y) equivalent. In the frequency domain image, each point represents a particular frequency contained in the spatial domain image. So, for images with a lot of high-frequency components (edges, corners, and stripes), there will be a number of points in the frequency domain at high frequency values.

Smooth background: a lot of low frequency, edges: high frequency

OpenCV FFT: https://docs.opencv.org/3.0-beta/doc/py_tutorials/py_imgproc/py_transforms/py_fourier_transform/py_fourier_transform.html

Chinese explanation: https://www.cnblogs.com/wj-1314/p/11983496.html, https://zhuanlan.zhihu.com/p/19763358, https://zhuanlan.zhihu.com/p/99605178



Notice that this image has components of all frequencies. You can see a bright spot in the center of the transform image, which tells us that a large portion of the image is low-frequency; this makes sense since the body of the birds and background are solid colors. The transform image also tells us that there are **two** dominating directions for these frequencies; vertical edges (from the edges of birds) are represented by a horizontal line passing through the center of the frequency transform image, and horizontal edges (from the branch and tops of the birds' heads) are represented by a vertical line passing through the center.

### Edge Handling

Kernel convolution relies on centering a pixel and looking at it's surrounding neighbors. 

**Extend** The nearest border pixels are conceptually extended as far as necessary to provide values for the convolution. Corner pixels are extended in 90° wedges. Other edge pixels are extended in lines.

**Padding** The image is padded with a border of 0's, black pixels.

**Crop** Any pixel in the output image which would require values from beyond the edge is skipped. This method can result in the output image being slightly smaller, with the edges having been cropped.

