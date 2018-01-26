# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps: 
1. Gray Scale Transformation.
    This step transforms the image in RGB color space into gray-scale image preparing as the input for Canny Edge Detection.
2. Gaussian Smoothing 
    This steps applies Gaussian Filter to the image to reduce the noise and blur the image.
3. Canny Edge Detection 
    To produce the edge image, the low_threshold is set to 70 and high_threshold is set to 150.
4. ROI (Region of Interest) Based Edge Filtering 
    This step we add mask into to only demonstrate the edges in region of interest.
5. Hough Transformation
    Hough Transformation finds the line.
6. Lane Extrapolation 
    This helps draw a single line on the left and right lanes by connecting the line segments.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by the following steps:
    Step1: separating line segments by the sign of their slope ((y2-y1)/(x2-x1)) to decide which segments are part of the left line vs. the right line.  
    Step2: Find the mean of the slope of each of the lines, and filter out those who are above the tolerance threshold.
    Step3: Extrapolate to the top and bottom of the lane.


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the lane becomes bending in the image. 


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to after the edge image is produced, I need to investigate to use another algorithms or OpenCV library to find the bended line and using some regression algorithm to deteremine the line. 
