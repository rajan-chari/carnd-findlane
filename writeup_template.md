# **Finding Lane Lines on the Road** 

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"
[image2]: ./examples/grayscale.jpg "Grayscale"


---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of the following steps:

* Convert the images to grayscale
* Perform Gaussian blur
* Detect edges using Canny edge detection
* Create a trepezoidal region of interest and mask the image
* Detect lines using Hough line detection
* Remove noise (bad lines) and draw a single line for left and right lanes

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by
* Seperating lines into ones with positive slopes and ones with negative slopes
* Remove lines with positive slopes from the left side of the image and viceversa
* Remove lines with abnormal slopes (two sigma) from each side
* Use linear regression to find a line that represents all the lines for each side

### 2. Identify potential shortcomings with your current pipeline

Potential shorcomings with current pipeline
* Does not handle high contrast shadows and light on the road
* Does not handle snow 
* Does not handle missing or extra lane markings
* Does not handle sharp curves

### 3. Suggest possible improvements to your pipeline

Possible improvements
* Detect changes in light conditions on different regions of the road and process each region with parameters for those light conditions
* Detect snow pixels and fill in those regions with information from non-snow regions
* Detect multiple parallel lines on the left and right sides and determine the likely lane marking
* Detect curve conditions and use higher order polynomial fit for curves
